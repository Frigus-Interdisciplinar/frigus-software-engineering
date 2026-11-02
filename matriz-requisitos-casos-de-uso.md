# Matriz de ligação entre requisitos e casos de uso

Esta matriz liga os requisitos funcionais da planilha [Levantamento de Requisitos](requisitos/levantamento-de-requisitos.xlsx) aos casos de uso que aparecem no [diagrama de casos de uso](diagramas/casos-de-uso-frigus.png). Ela ajuda a localizar no desenho quais requisitos cada ação atende.

Os IDs RF continuam sendo a referência principal. Quando um requisito descreve campos, regras ou comportamento transversal, ele aparece ligado ao caso de uso mais próximo e isso está explicado nas observações.

## Conta e grupo

| Caso de uso no diagrama | Requisito(s) relacionado(s) |
|---|---|
| Cadastrar conta | RF01 — Cadastro de usuário; RF03 — Tipo de conta |
| Fazer login | RF02 — Login de usuário |
| Criar família/equipe | RF04 — Criação de família ou equipe |
| Convidar membros | RF05 — Convite de membros |
| Gerenciar membros | RF06 — Gerenciamento de membros |

## Cadastro e gestão de estoque

| Caso de uso no diagrama | Requisito(s) relacionado(s) |
|---|---|
| Cadastrar produto manualmente | RF07 — Cadastro manual de produto; RF08 — Campos do produto doméstico; RF09 — Campos do produto comercial |
| Definir local de armazenamento | RF22 — Local de armazenamento |
| Importar via QR Code da nota fiscal | RF10 — Importação por QR Code da nota fiscal; RF11 — Importação de valor quando disponível |
| Conferir produtos importados | RF12 — Conferência antes de salvar |
| Padronizar nomes | RF13 — Padronização de nomes |
| Classificar categoria automaticamente | RF14 — Classificação automática |
| Corrigir dados sugeridos | RF15 — Correção manual |
| Listar produtos | RF16 — Listagem de produtos |
| Buscar produto | RF17 — Busca de produtos |
| Filtrar produtos | RF18 — Filtros de produtos |
| Editar produto | RF19 — Edição de produto |
| Excluir produto | RF20 — Exclusão de produto |
| Atualizar quantidade | RF21 — Atualização de quantidade |
| Registrar entrada | RF28 — Registro de entrada |
| Registrar saída | RF29 — Registro de saída; RF30 — Motivo de descarte |
| Consultar histórico | RF31 — Histórico de movimentações |

## Validade, alertas e notificações

| Caso de uso no diagrama | Requisito(s) relacionado(s) |
|---|---|
| Controlar validade | RF23 — Controle de validade; RF24 — Indicador visual de validade |
| Alertar vencimento próximo | RF25 — Alertas de vencimento próximo |
| Alertar produto vencido | RF26 — Alertas de produto vencido |
| Alertar estoque baixo | RF27 — Estoque baixo |
| Configurar alertas | RF60 — Configuração de alertas |
| Central de notificações | RF59 — Central de notificações |

## Lista de compras

| Caso de uso no diagrama | Requisito(s) relacionado(s) |
|---|---|
| Criar lista compartilhada | RF41 — Lista de compras compartilhada |
| Adicionar item à lista | RF42 — Adicionar item à lista |
| Alterar status do item | RF43 — Status de item da lista |
| Solicitar compra | RF44 — Solicitação de compra |
| Anexar foto à solicitação | RF45 — Solicitação com foto |
| Avisar item repetido | RF47 — Aviso de item repetido |
| Converter compra em entrada de estoque | RF46 — Adicionar solicitação ao estoque após compra |

## Conversa

| Caso de uso no diagrama | Requisito(s) relacionado(s) |
|---|---|
| Chat individual | RF48 — Chat individual |
| Chat em grupo | RF49 — Chat em grupo |
| Enviar mensagem | RF50 — Envio de mensagem de texto |
| Enviar foto | RF51 — Envio de fotos no chat |
| Solicitar compra pelo chat | RF52 — Pedido de compra pelo chat |
| Atualizações automáticas no chat | RF53 — Atualizações automáticas no chat |

## Receitas, visão comercial e administração

| Caso de uso no diagrama | Requisito(s) relacionado(s) |
|---|---|
| Sugerir receitas com base no estoque | RF38 — Sugestão de receitas domésticas |
| Priorizar ingredientes próximos do vencimento | RF39 — Priorização por validade nas receitas |
| Consultar itens próximos do vencimento (comercial) | RF40 — Consulta comercial de itens próximos do vencimento |
| Visualizar dashboard | RF32 — Dashboard comercial |
| Destacar produtos em risco | RF33 — Produtos em risco |
| Calcular perda financeira | RF34 — Estimativa de perda financeira |
| Exibir valor em risco | RF35 — Valor em risco |
| Perdas por categoria | RF36 — Perdas por categoria |
| Gerar relatório mensal | RF37 — Relatório mensal simples |
| Painel administrativo | RF54 — Dashboard administrativo web |
| Gerenciar banners de anunciantes | RF55 — Gerenciamento de banners |
| Bloquear links maliciosos | RF56 — Identificação de links maliciosos |
| Rastrear alterações por usuário | RF61 — Identificação de alterações |

## Ligações que precisam aparecer com mais clareza no diagrama

- **RF03 — Tipo de conta:** está associado ao cadastro, mas o diagrama não mostra explicitamente a escolha entre conta doméstica e comércio. Se essa distinção for importante para a avaliação, adicionar o caso de uso `Selecionar tipo de conta` ligado a `Cadastrar conta`.
- **RF24 — Indicador visual de validade:** foi ligado a `Controlar validade`, mas o desenho não mostra as cores ou a apresentação visual. Pode ser detalhado como `Visualizar indicador de validade`.
- **RF57 — Plano doméstico** e **RF58 — Plano comércio:** o desenho distingue funcionalidades domésticas e comerciais, mas não mostra seleção, contratação ou gestão de planos. Não há ligação direta com os casos de uso atuais.

## Casos do desenho sem RF correspondente na planilha

O diagrama também tem `Filtrar por preferência alimentar` e `Salvar receita favorita`. Esses casos não têm um requisito funcional próprio entre RF01 e RF61 na planilha atual. Para manter a documentação consistente, o grupo pode criar RFs para eles ou confirmar que são ideias fora do escopo desta versão.

## Como ler esta matriz

Esta matriz registra a relação entre as funções desenhadas e os IDs da planilha; ela não altera a imagem do diagrama. Se a professora pedir que os IDs apareçam no próprio desenho, use os códigos RF como etiquetas junto aos casos de uso correspondentes, mantendo esta matriz como referência detalhada.

Os diagramas de atividade detalham dois fluxos dessa mesma lista de requisitos: [importação por nota fiscal](diagramas/atividade-importacao-por-nota-fiscal.png) e [registro de saída do estoque](diagramas/atividade-registro-saida-estoque.png). O segundo destaca RF21, RF29, RF30, RF31 e RF61.
