# Padrões de projeto e testes no Frigus

Este documento explica, sem complicar, algumas decisões que já aparecem no código do Frigus: como a API organiza o acesso ao banco, como transforma dados para a web, como processa transações em segundo plano e como escolhe o modelo de IA. No fim, mostramos onde os testes entram e o que eles cobrem.

Os exemplos da Core API apontam para a branch `dev`; os exemplos do serviço de IA apontam para `main`.

## Repository: cada coisa no seu lugar

Quando uma tela ou serviço precisa salvar ou buscar dados, ele não precisa conhecer os detalhes de cada consulta ao banco. Essa parte fica nos repositórios.

Na Core API, [`BaseRepository`](https://github.com/Frigus-Interdisciplinar/frigus-core-api/blob/dev/src/main/java/com/frigus/coreapi/repository/BaseRepository.java) reaproveita as operações do Spring Data JPA. Repositórios específicos, como [`TransactionRepository`](https://github.com/Frigus-Interdisciplinar/frigus-core-api/blob/dev/src/main/java/com/frigus/coreapi/repository/TransactionRepository.java), herdam essa base e acrescentam consultas próprias quando necessário. O [`BaseService`](https://github.com/Frigus-Interdisciplinar/frigus-core-api/blob/dev/src/main/java/com/frigus/coreapi/service/BaseService.java) usa o repositório para buscar, listar e excluir registros.

Na prática, isso mantém o serviço focado na regra da aplicação. Ele pede os dados ao repositório sem precisar montar consultas de banco em cada operação.

## DTO e Mapper: separar a API do banco

Uma entidade do banco pode ter campos internos que não devem ser enviados pela API. Por isso, a Core API usa DTOs para definir os dados que entram e saem, e mappers para converter entre esses DTOs e as entidades.

O contrato comum está em [`BaseMapper`](https://github.com/Frigus-Interdisciplinar/frigus-core-api/blob/dev/src/main/java/com/frigus/coreapi/mapper/BaseMapper.java), com conversões nos dois sentidos. Mappers específicos, como [`ProductMapper`](https://github.com/Frigus-Interdisciplinar/frigus-core-api/blob/dev/src/main/java/com/frigus/coreapi/mapper/ProductMapper.java) e [`TransactionMapper`](https://github.com/Frigus-Interdisciplinar/frigus-core-api/blob/dev/src/main/java/com/frigus/coreapi/mapper/TransactionMapper.java), cuidam dos campos de cada recurso. O `BaseService` chama o mapper ao transformar resultados do banco em respostas da API.

O `pom.xml` inclui MapStruct, mas os mappers citados implementam as conversões no próprio código. Então a evidência aqui é o padrão **DTO + Mapper**; não estamos dizendo que essas conversões são geradas pelo MapStruct.

## Producer/Consumer: processar transações pela fila

Cobrar ou processar uma transação pode levar mais tempo que uma resposta normal da API. A Core API coloca esse trabalho numa fila Redis: o produtor registra a mensagem e um worker a consome depois.

O [`TransactionQueueProducer`](https://github.com/Frigus-Interdisciplinar/frigus-core-api/blob/dev/src/main/java/com/frigus/coreapi/service/TransactionQueueProducer.java) adiciona o payload à fila `queue:transactions`. O [`TransactionWorkerService`](https://github.com/Frigus-Interdisciplinar/frigus-core-api/blob/dev/src/main/java/com/frigus/coreapi/service/TransactionWorkerService.java) retira a mensagem e entrega o processamento ao `TransactionProcessorService`. Se o processamento falha, o worker consulta a regra de falha e pode devolver a mensagem à fila para uma nova tentativa.

Essa divisão evita prender a requisição da pessoa usuária enquanto o processamento acontece e deixa explícito quem envia e quem consome o trabalho.

## Registry e Factory: escolher um modelo de IA

O Frigus.AI pode usar provedores diferentes. A escolha não fica espalhada por vários `if`s: um registro relaciona cada modelo ao provedor e outro relaciona cada provedor à classe LangChain que o cria.

Em [`registry.py`](https://github.com/Frigus-Interdisciplinar/frigus-ai/blob/main/src/frigus_ai/infra/llm/registry.py), `PROVIDER_MAP` faz o primeiro mapeamento e `BUILDERS` guarda os construtores, como `ChatGroq`, `ChatAnthropic` e `ChatOpenAI`. A função [`build_llm`](https://github.com/Frigus-Interdisciplinar/frigus-ai/blob/main/src/frigus_ai/infra/llm/builder.py) consulta esses registros, aplica as configurações do provedor e constrói o modelo. Se uma chave opcional não estiver configurada, ela retorna `None` para que esse provedor possa ficar fora da cadeia de alternativas.

Aqui aparecem duas ideias próximas: **Registry**, que centraliza as associações, e **Factory**, que usa essas associações para criar o objeto certo.

## TDD e testes: transformar regras em exemplos verificáveis

TDD é uma forma de desenvolver em ciclos curtos:

1. Escrever um teste que descreve o comportamento esperado.
2. Rodar o teste e confirmar que ele falha pelo motivo esperado.
3. Implementar o necessário para fazê-lo passar.
4. Melhorar o código mantendo os testes passando.

Esse ciclo é conhecido como **Red, Green, Refactor**. No Frigus, os testes automatizados ajudam a manter as regras visíveis e a encontrar regressões quando o código muda.

### Exemplos na Core API

- [`TransactionQueueProducerTest`](https://github.com/Frigus-Interdisciplinar/frigus-core-api/blob/dev/src/test/java/com/frigus/coreapi/service/TransactionQueueProducerTest.java) verifica se o payload é enviado à fila correta do Redis.
- [`TransactionWorkerServiceTest`](https://github.com/Frigus-Interdisciplinar/frigus-core-api/blob/dev/src/test/java/com/frigus/coreapi/service/TransactionWorkerServiceTest.java) verifica o processamento de uma mensagem, o comportamento com a fila vazia e as duas saídas em caso de falha: reenfileirar quando uma nova tentativa é permitida ou parar quando não é.
- Os testes de integração, como [`MoneySavingHttpIntegrationTest`](https://github.com/Frigus-Interdisciplinar/frigus-core-api/blob/dev/src/test/java/com/frigus/coreapi/integration/MoneySavingHttpIntegrationTest.java), usam Testcontainers para verificar a aplicação com dependências reais em contêiner, em vez de testar apenas objetos isolados.

### Exemplos no Frigus.AI

- [`test_llm.py`](https://github.com/Frigus-Interdisciplinar/frigus-ai/blob/main/tests/graph/test_llm.py) verifica a associação entre modelo e provedor, a criação do modelo, o tratamento de chave ausente e opções como timeout e tentativas.
- A pasta [`tests/`](https://github.com/Frigus-Interdisciplinar/frigus-ai/tree/main/tests) acompanha a organização de `src/frigus_ai/`, com testes para API, serviços, nós do grafo, repositórios e ferramentas.

Esses arquivos mostram quais comportamentos estão cobertos. O histórico dos arquivos, por si só, não prova que cada teste foi escrito antes da implementação. Por isso, apresentamos a suíte como apoio ao TDD e à regressão, sem afirmar que todo o código do projeto seguiu Red, Green, Refactor em cada mudança.

Para executar os testes, use `./mvnw test` na Core API e `just test` no Frigus.AI.
