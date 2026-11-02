# Frigus ❄️🌱

O **Frigus** é um projeto de tecnologia para ajudar famílias e pequenos negócios do setor alimentício a cuidar melhor dos alimentos que compram e armazenam. A plataforma reúne organização de estoque, acompanhamento de validade e recursos inteligentes para apoiar o consumo consciente e reduzir o desperdício.

Ao facilitar o controle dos alimentos na geladeira, no freezer e no estoque, o Frigus busca tornar a rotina mais prática e o uso dos recursos mais eficiente. A iniciativa está alinhada ao **Objetivo de Desenvolvimento Sustentável 12 (ODS 12) da ONU**, que promove padrões sustentáveis de consumo e produção.

---

## Objetivos do projeto

- Reduzir o desperdício de alimentos em residências e pequenos estabelecimentos.
- Facilitar a organização de produtos por categoria, local de armazenamento e prazo de validade.
- Apoiar o planejamento do consumo, das compras e da reposição de estoque.
- Usar tecnologia e Inteligência Artificial para automatizar tarefas de gestão de alimentos.
- Considerar privacidade e proteção de dados desde o desenvolvimento, em conformidade com os princípios da **LGPD**.

---

## Como funciona

O fluxo proposto começa com o cadastro dos alimentos. A pessoa usuária poderá ler o QR Code da Nota Fiscal Paulista para identificar os itens da compra; a Inteligência Artificial ajudará a reconhecer e filtrar alimentos refrigerados ou congelados, como carnes, laticínios, hortaliças e sobremesas. Como a nota fiscal não informa o prazo de validade, essa data será preenchida manualmente. Também será possível cadastrar refeições e preparações feitas em casa ou no estabelecimento.

Depois do cadastro, os itens poderão ser organizados por categoria e local de armazenamento. Uma visualização por cores ajudará a priorizar o consumo: **vermelho** para alimentos próximos do vencimento, **amarelo** para validade intermediária e **verde** para os de maior durabilidade. Notificações de validade e de estoque baixo ajudarão no planejamento do consumo e das compras.

O Frigus também prevê planos de uso adaptados às necessidades de residências e estabelecimentos comerciais.

---

## Funcionalidades em foco

- **Cadastro de alimentos:** leitura do QR Code da Nota Fiscal Paulista, identificação assistida por IA e inclusão manual de validade.
- **Organização de estoque:** acompanhamento dos alimentos por categoria e local, como geladeira, freezer ou estoque.
- **Sinalização de validade:** indicação visual da urgência de consumo.
- **Alertas e reposição:** notificações sobre vencimentos próximos e itens com estoque baixo.
- **Refeições e preparações:** cadastro de alimentos preparados em casa ou no comércio.
- **Experiência para diferentes públicos:** recursos e planos adequados a famílias e pequenos negócios.

---

## Tecnologias

O ecossistema Frigus é composto por aplicações e serviços em diferentes plataformas:

| Componente | Tecnologias principais |
|---|---|
| Aplicação web | React, TypeScript e Vite |
| Aplicativo Android | Kotlin e Android Jetpack |
| Aplicativo iOS | Swift |
| BFF (Backend for Frontend) | Node.js, TypeScript e Hono |
| API principal | Java e Spring Boot |
| Serviço de IA | Python, FastAPI e LangGraph |

### Repositórios

- [Aplicação web](https://github.com/Frigus-Interdisciplinar/frigus-react-web)
- [Aplicativo Android](https://github.com/Frigus-Interdisciplinar/frigus-mobile)
- [Aplicativo iOS](https://github.com/Frigus-Interdisciplinar/frigus-mobile-ios)
- [BFF](https://github.com/Frigus-Interdisciplinar/frigus-bff)
- [Core API](https://github.com/Frigus-Interdisciplinar/frigus-core-api)
- [Serviço de IA](https://github.com/Frigus-Interdisciplinar/frigus-ai)
- [Engenharia de software e documentação](https://github.com/Frigus-Interdisciplinar/frigus-software-engineering)

---

## Sustentabilidade, privacidade e segurança

O Frigus promove o consumo consciente ao ajudar as pessoas a visualizar o que já têm, priorizar alimentos próximos do vencimento e planejar compras e reposições. O projeto também considera a proteção de dados pessoais: a proposta é limitar a coleta ao necessário para as funcionalidades e seguir os princípios da **Lei Geral de Proteção de Dados (LGPD)**.

---

## Sobre a organização

O Frigus é desenvolvido pela organização **Frigus-Interdisciplinar**. Este repositório reúne materiais de engenharia de software, como apresentação da equipe, casos de uso, diagramas e requisitos.

## Documentação técnica

- [Levantamento de requisitos](requisitos/levantamento-de-requisitos.xlsx)
- [Diagrama de casos de uso](diagramas/casos-de-uso-frigus.png)
- [Diagrama de atividade: importação por nota fiscal](diagramas/atividade-importacao-por-nota-fiscal.png)
- [Diagrama de atividade: saída de estoque](diagramas/atividade-registro-saida-estoque.png)
- [Diagrama de sequência: requisições Web/Mobile](diagramas/sequencia-requisicoes-web-mobile.png)
- [Diagrama de sequência: fluxo de transação](diagramas/sequencia-fluxo-transacao.png)
- [Matriz de requisitos e casos de uso](matriz-requisitos-casos-de-uso.md): ligação dos requisitos funcionais aos casos de uso, com lacunas identificadas.
- [Padrões de projeto e TDD](padroes-de-projeto-e-tdd.md): explicações em linguagem direta, exemplos no código e caminhos dos testes.
