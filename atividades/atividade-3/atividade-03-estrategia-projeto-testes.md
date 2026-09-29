# Atividade 3: Estratégia e Projeto de Testes do LocalEats

**Unidade Curricular:** Qualidade de Software
**Projeto:** LocalEats
**Integrante:** Hernane Lemes (atividade individual)
**Funcionalidade escolhida:** Fazer pedido

---

## Tarefa 1: Planejamento dos testes

### 1.1 Objetivo dos testes

Verificar se o fluxo de fazer pedido do LocalEats só registra como realizado um pedido cuja finalização foi de fato concluída, se o sistema informa claramente o resultado (sucesso ou falha) e se impede a finalização de pedidos em condições inválidas (usuário não autenticado ou pedido sem itens).

### 1.2 Escopo

| Integrante | Funcionalidade incluída | O que será verificado |
|---|---|---|
| Hernane Lemes | Fazer pedido | Conclusão do pedido, consistência entre o resultado do pedido e o histórico exibido, e bloqueio de pedidos em condições inválidas |

| Funcionalidade não incluída | Justificativa |
|---|---|
| Favoritar e desfavoritar restaurantes | Não faz parte do fluxo de pedido escolhido para os testes |
| Pesquisar e filtrar restaurantes | Serve apenas para chegar ao restaurante; não é o foco dos riscos analisados |

### 1.3 Abordagem

| Item | Decisão da equipe | Justificativa |
|---|---|---|
| Níveis de teste | Sistema | O fluxo será analisado pela interface, do início ao fim, incluindo o histórico de pedidos. |
| Tipos de teste | Funcional | O objetivo é verificar as regras e o resultado do pedido. |
| Perspectiva caixa-preta ou caixa-branca | Caixa-preta | Serão consideradas entradas e resultados observáveis, sem acesso ao código. |
| Técnicas de teste | Transição de estados e tabela de decisão | O resultado do pedido depende do estado em que ele se encontra (risco R01) e da combinação entre autenticação e conteúdo do pedido (risco R02). |

### 1.4 Ambiente e responsabilidades

| Item | Definição |
|---|---|
| Ambiente necessário | Aplicação em https://local-eats-unisenac.vercel.app/; navegador atualizado em computador; conexão estável à internet; conta de teste com dados fictícios (e-mail e senha fictícios, sem dados pessoais reais); ao menos um restaurante com itens disponíveis para pedido. |
| Responsáveis pelo planejamento | Hernane Lemes |
| Responsáveis pela especificação dos casos | Hernane Lemes |
| Responsáveis pela futura execução | Hernane Lemes |

### 1.5 Critérios

| Critério | Definição da equipe |
|---|---|
| Entrada | Aplicação disponível, conta de teste criada e restaurante com itens disponível para pedido. |
| Saída | Todos os casos planejados executados e os resultados registrados. |
| Suspensão | Aplicação indisponível ou impossibilidade de acessar a conta de teste. |

---

## Tarefa 2: Riscos e técnicas de teste

### 2.1 Análise dos riscos

| ID | Integrante | Funcionalidade | Risco | Consequência | Probabilidade | Impacto | Prioridade | Justificativa |
|---|---|---|---|---|---|---|---|---|
| R01 | Hernane Lemes | Fazer pedido | Um pedido aparecer como realizado (no histórico ou na página de transações) sem que a finalização e o pagamento tenham sido concluídos. | O cliente pode acreditar que comprou algo que não comprou, e o restaurante e o negócio perdem credibilidade por exibir informações falsas. | Alta | Alto | Alta | Na exploração da Atividade 1, a "compra" levou a uma página de transações com registros mesmo sem nenhuma transação realizada. Afeta diretamente a confiança no sistema. |
| R02 | Hernane Lemes | Fazer pedido | O sistema permitir finalizar um pedido em condição inválida (usuário não autenticado ou pedido sem itens). | Pedidos sem dono ou vazios, que geram confusão para o cliente e para o restaurante. | Média | Médio | Média | Não foi observado durante a exploração, mas é uma regra básica de fluxos de compra, e a falha é menos grave que a de R01. |

### 2.2 Aplicação da técnica

#### Técnica 1: Transição de estados (risco R01)

**Integrante responsável:** Hernane Lemes
**Funcionalidade:** Fazer pedido
**Risco relacionado:** R01
**Técnica escolhida:** Transição de estados

**Por que a técnica foi escolhida?**
O risco R01 trata de um pedido "pular" para o estado de realizado sem passar pela conclusão do pagamento. A técnica de transição de estados é adequada porque verifica quais mudanças de estado são permitidas e quais devem ser bloqueadas.

**Aplicação da técnica**

Estados considerados para um pedido: **Em montagem → Aguardando pagamento → Confirmado** e, em caso de falha, **Aguardando pagamento → Não concluído**.

| Transição | Situação | Resultado esperado |
|---|---|---|
| Em montagem → Aguardando pagamento | Permitida | O usuário inicia a finalização do pedido. |
| Aguardando pagamento → Confirmado | Permitida (somente com pagamento concluído) | O pedido passa a constar como realizado no histórico. |
| Aguardando pagamento → Não concluído | Permitida | O sistema informa a falha e não registra o pedido como realizado. |
| Em montagem → Confirmado | **Inválida** | Um pedido não pode constar como realizado sem passar pela conclusão do pagamento. |
| Aguardando pagamento → Confirmado (sem pagamento concluído) | **Inválida** | O pedido não pode constar como realizado. |

**Casos derivados:** CT01

#### Técnica 2: Tabela de decisão (risco R02)

**Integrante responsável:** Hernane Lemes
**Funcionalidade:** Fazer pedido
**Risco relacionado:** R02
**Técnica escolhida:** Tabela de decisão

**Por que a técnica foi escolhida?**
O resultado de tentar finalizar um pedido depende da combinação de duas condições (usuário autenticado e pedido com itens). A tabela de decisão permite enumerar todas as combinações e definir o resultado esperado de cada uma.

**Aplicação da técnica**

| Regra | Usuário autenticado? | Pedido possui itens? | Resultado esperado |
|---|---|---|---|
| 1 | Sim | Sim | Permitir seguir com a finalização do pedido |
| 2 | Sim | Não | Impedir a finalização e informar que não há itens |
| 3 | Não | Sim | Solicitar autenticação e não finalizar o pedido |
| 4 | Não | Não | Solicitar autenticação e não finalizar o pedido |

**Casos derivados:** CT02 (regra 3) e CT03 (regra 2)

---

## Tarefa 3: Casos de teste e rastreabilidade

### 3.1 Especificação dos casos de teste

#### CT01: Não registrar como realizado um pedido sem pagamento concluído

**Integrante responsável:** Hernane Lemes
**Funcionalidade:** Fazer pedido
**Risco ou requisito relacionado:** R01
**Técnica utilizada:** Transição de estados

**Pré-condição:**
O usuário está autenticado com a conta de teste, e existe um restaurante com itens disponíveis.

**Dados de entrada:**
Restaurante: qualquer restaurante com itens disponíveis
Item: um item qualquer
Pagamento: nenhum dado de pagamento concluído (etapa de pagamento não finalizada)

**Passos:**
1. Acessar a consulta de pedidos e anotar a quantidade de registros exibidos.
2. Escolher um restaurante e adicionar um item ao pedido.
3. Iniciar a finalização do pedido sem concluir o pagamento.
4. Acessar novamente a consulta de pedidos (ou a página de transações).

**Resultado esperado:**
O sistema não registra o pedido como realizado: a quantidade de registros permanece a mesma e é informado que o pagamento não foi concluído.

#### CT02: Exigir autenticação para finalizar um pedido

**Integrante responsável:** Hernane Lemes
**Funcionalidade:** Fazer pedido
**Risco ou requisito relacionado:** R02
**Técnica utilizada:** Tabela de decisão (regra 3)

**Pré-condição:**
O usuário não está autenticado (sessão encerrada) e existe um restaurante com itens disponíveis.

**Dados de entrada:**
Restaurante: qualquer restaurante com itens disponíveis
Item: um item qualquer

**Passos:**
1. Acessar o LocalEats sem entrar na conta.
2. Escolher um restaurante e adicionar um item ao pedido.
3. Tentar finalizar o pedido.

**Resultado esperado:**
O sistema solicita autenticação e não finaliza o pedido.

#### CT03: Impedir a finalização de um pedido sem itens

**Integrante responsável:** Hernane Lemes
**Funcionalidade:** Fazer pedido
**Risco ou requisito relacionado:** R02
**Técnica utilizada:** Tabela de decisão (regra 2)

**Pré-condição:**
O usuário está autenticado com a conta de teste e o pedido não possui nenhum item.

**Dados de entrada:**
Nenhum item selecionado

**Passos:**
1. Entrar na conta de teste.
2. Acessar a área de pedido sem adicionar nenhum item.
3. Tentar finalizar o pedido.

**Resultado esperado:**
O sistema impede a finalização e informa que o pedido não possui itens, sem gerar registro no histórico.

### 3.2 Matriz de rastreabilidade

| Integrante | Funcionalidade | Risco ou requisito | Técnica utilizada | Casos de teste |
|---|---|---|---|---|
| Hernane Lemes | Fazer pedido | R01: pedido registrado como realizado sem conclusão | Transição de estados | CT01 |
| Hernane Lemes | Fazer pedido | R02: finalização em condição inválida | Tabela de decisão | CT02 e CT03 |

Todos os riscos identificados (R01 e R02) possuem ao menos um caso de teste.

---

## Uso de inteligência artificial

**Ferramenta utilizada:**
Claude (Anthropic).

**Como foi utilizada:**
Novamente solicitei que conferisse a ortografia e reescreve possíveis erros em minhas respostas, também solicitei que montasse o README de acordo com a estrutura solicitada.

**Uma sugestão que precisou ser alterada ou rejeitada:**
Nada foi ajustado.

**Como as respostas foram verificadas:**

