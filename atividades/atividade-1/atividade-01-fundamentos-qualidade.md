# Atividade 1: Fundamentos e Características da Qualidade no LocalEats

**Unidade Curricular:** Qualidade de Software
**Projeto:** LocalEats
**Integrante:** Hernane Lemes (atividade individual)

---

## Tarefa 1: Fundamentos da qualidade

| Tipo | Necessidade | Interessado | Consequência se não for atendida |
|---|---|---|---|
| Explícita | O usuário deve poder fazer um pedido e consultar seus pedidos depois. | Cliente e restaurante | O cliente não consegue comprar nem acompanhar o que pediu, e o restaurante não recebe pedidos. |
| Explícita | O usuário deve poder pesquisar e filtrar restaurantes por especialidade ou localização. | Cliente | O cliente não encontra o restaurante que procura e abandona a aplicação. |
| Implícita | As informações exibidas sobre pedidos e transações devem corresponder ao que realmente aconteceu, com indicação clara de sucesso ou falha. | Cliente e negócio | O cliente perde a confiança, pode acreditar que comprou algo que não comprou (ou o contrário) e o negócio perde credibilidade. |
| Implícita | O cadastro deve garantir que a conta pertence a uma pessoa real (por exemplo, validando o e-mail). | Negócio e cliente | Contas falsas, dados de baixa confiabilidade e maior risco de abuso ou fraude. |

**Um sistema que implementa todas as funcionalidades explicitamente solicitadas pode, ainda assim, apresentar baixa qualidade?**

Sim. No LocalEats a função "fazer pedido" existe, mas ao tentar finalizar a compra fui levado a uma página de transações que exibia registros sem que eu tivesse realizado nenhuma transação. Isso fere a necessidade implícita de informações verdadeiras e de resultado claro. A funcionalidade está presente, mas não atende à expectativa real do usuário, portanto a qualidade é baixa.

---

## Tarefa 2: Exploração da aplicação

| Integrante | Funcionalidade | O que foi realizado | O que foi observado | Evidência |
|---|---|---|---|---|
| Hernane Lemes | Fazer pedido | (1) Utilização esperada: escolhi um restaurante, adicionei itens e tentei finalizar a compra com dados fictícios. (2) Utilização alternativa:  Não consegui realizar o pagamento. A "compra" me levou direto a uma página que registra "transações", que exibia registros mesmo sem eu ter realizado nenhuma transação. Não encontrei opção de cancelar pedido. | `evidencias/hernanelemes-pedido-redireciona-transacoes.png` |

---

## Tarefa 3: Requisitos e características de qualidade

| Integrante | Requisito de Qualidade | Característica ou subcaracterística | Justificativa | Como avaliar |
|---|---|---|---|---|
| Hernane Lemes | Ao finalizar um pedido, o sistema deve informar claramente se ele foi concluído ou falhou, e o histórico deve listar apenas pedidos efetivamente realizados. | Adequação funcional → Corretude funcional | No LocalEats, a compra levou a uma tela de transações sem que houvesse transação: o resultado apresentado não corresponde ao que de fato aconteceu. O problema está na precisão do resultado, e não na existência da função. | Executar o fluxo de pedido várias vezes (com sucesso e com falha) e comparar o que o histórico exibe com o que realmente foi concluído, contando as divergências encontradas. |

---

## Uso de inteligência artificial

**Ferramenta utilizada:**
Claude (Anthropic).

**Como foi utilizada:**
Solicitei que conferisse a ortografia e reescreve possíveis erros em minhas respostas, também solicitei que montasse o README de acordo com a estrutura solicitada.

**Como as respostas foram verificadas:**
Só li se as respostas reescritas batiam com o que escrevi anteriormente.
