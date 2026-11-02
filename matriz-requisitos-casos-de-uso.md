# Matriz de ligação entre requisitos e casos de uso

Esta matriz apresenta a rastreabilidade entre os requisitos funcionais da planilha [Levantamento de Requisitos](requisitos/levantamento-de-requisitos.xlsx) e os casos de uso do [diagrama de casos de uso](diagramas/casos-de-uso-frigus.png). Requisitos que definem campos ou regras de uma ação estão associados ao caso de uso correspondente.

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

## Requisitos que podem ser detalhados no diagrama

- **RF03 — Tipo de conta:** está associado ao cadastro. A escolha entre conta doméstica e comércio pode ser representada como `Selecionar tipo de conta`, ligada a `Cadastrar conta`.
- **RF24 — Indicador visual de validade:** está associado a `Controlar validade`. A apresentação visual das cores pode ser detalhada como `Visualizar indicador de validade`.
- **RF57 — Plano doméstico** e **RF58 — Plano comércio:** o diagrama distingue funcionalidades domésticas e comerciais, mas não representa a seleção ou gestão de planos. A inclusão desses casos depende de essas ações fazerem parte do escopo do sistema.

## Casos de uso complementares

O diagrama também apresenta `Filtrar por preferência alimentar` e `Salvar receita favorita`. A planilha atual não define requisitos funcionais próprios para essas ações. Caso façam parte do escopo, recomenda-se registrá-las na planilha de requisitos.

## Critério de associação

Cada requisito foi associado ao caso de uso que representa sua ação principal. Requisitos de campos, regras e critérios aparecem junto ao fluxo correspondente, em vez de como ações independentes.
