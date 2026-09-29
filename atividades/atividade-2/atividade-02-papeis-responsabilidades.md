# Atividade 2: Organização da Qualidade no LocalEats

**Unidade Curricular:** Qualidade de Software
**Projeto:** LocalEats
**Integrante:** Hernane Lemes (atividade individual)

---

## Tarefa 1: Diagnóstico da situação

| Problema identificado | Possível consequência para o produto ou para a equipe |
|---|---|
| Os critérios para considerar uma funcionalidade pronta não estão claros. | Cada pessoa entende "pronto" de um jeito: funcionalidades incompletas ou com defeitos chegam aos usuários e a equipe gasta tempo em retrabalho e discussões. |
| A equipe acredita que somente o QA deve testar. | O QA vira gargalo, os defeitos são descobertos tarde (quando corrigir é mais caro) e desenvolvedores deixam de testar o que produzem. |
| Defeitos são identificados, mas nem sempre registrados ou acompanhados. | Perde-se o histórico, o mesmo defeito reaparece, não há priorização e ninguém sabe se um problema foi corrigido ou não. |

**A qualidade do LocalEats deve ser responsabilidade exclusiva do profissional de QA? Justifiquem.**

Não. A qualidade é construída ao longo de todo o desenvolvimento: o responsável pelo produto define o que é valor e os critérios de aceitação, o desenvolvedor escreve código testável e testes unitários, e a liderança técnica cuida da revisão e da entrega. O QA coordena e aprofunda a estratégia de testes, mas não consegue "colocar qualidade" no produto sozinho no final. Concentrar tudo no QA repete o problema do LocalEats: defeitos tardios e responsabilidades sem dono.

---

## Tarefa 2: Papéis e competências

Papéis definidos para o LocalEats: Responsável pelo Produto, Desenvolvedor, QA (analista de qualidade) e Liderança Técnica (que também acumula as responsabilidades de DevOps, dado o tamanho da equipe).

| Integrante | Papel analisado | Responsabilidades relacionadas à qualidade | Competências técnicas | Competências comportamentais |
|---|---|---|---|---|
| Hernane Lemes | Responsável pelo Produto | Definir critérios de aceitação junto à equipe; garantir que os requisitos representem as necessidades dos usuários; priorizar a correção dos defeitos; aprovar a disponibilização da versão. | Escrita de histórias de usuário e critérios de aceitação; priorização de backlog; noções de métricas de produto. | Comunicação clara, visão de negócio, capacidade de decisão, negociação. |
| Hernane Lemes | Desenvolvedor | Implementar a funcionalidade conforme os critérios de aceitação; criar testes unitários; participar da revisão de código; corrigir defeitos e ajudar a registrá-los. | Linguagens e frameworks do projeto; testes unitários; controle de versão; depuração; boas práticas de código limpo. | Responsabilidade pelo próprio código, abertura a críticas, colaboração, atenção a detalhes. |
| Hernane Lemes | QA (analista de qualidade) | Revisar requisitos em busca de ambiguidades; planejar e executar testes do sistema; registrar e acompanhar defeitos; dar parecer de qualidade antes da liberação da versão. | Técnicas de teste (funcional, exploratório, regressão); ferramentas de gestão de defeitos; noções de automação; conhecimento da ISO/IEC 25010. Certificações (como as do ISTQB) podem apoiar o desenvolvimento profissional, mas não substituem a experiência. | Pensamento crítico, comunicação objetiva ao relatar defeitos, curiosidade, diplomacia ao apontar falhas. |
| Hernane Lemes | Liderança Técnica (com DevOps) | Revisar código e garantir padrões; apoiar a estratégia de testes automatizados; manter o processo de integração e entrega; executar a disponibilização da versão. | Arquitetura de software; revisão de código; integração e entrega contínuas (CI/CD); monitoramento; gestão de versões. | Liderança, mentoria, visão sistêmica, organização, colaboração entre os papéis. |

---

## Tarefa 3: Matriz de responsabilidades (RACI)

R = Responsável (executa) · A = Aprovador (decisão final, único por atividade) · C = Consultado · I = Informado

| Atividade de qualidade | Responsável pelo Produto | Desenvolvedor | QA | Liderança Técnica |
|---|---|---|---|---|
| Definir critérios de aceitação | A/R | C | C | I |
| Revisar requisitos | A | C | R | C |
| Implementar a funcionalidade | I | A/R | I | C |
| Revisar o código | — | R | I | A |
| Criar testes unitários | — | A/R | C | C |
| Planejar e executar testes do sistema | I | C | A/R | I |
| Registrar e acompanhar defeitos | I | R | A/R | I |
| Priorizar a correção dos defeitos | A/R | C | C | C |
| Aprovar a disponibilização da versão | A | I | C | R |

### Lacuna ou conflito encontrado

A atividade **"Aprovar a disponibilização da versão"** concentra a decisão (A) no Responsável pelo Produto, que pode não ter visão técnica sobre os riscos de uma liberação. Para evitar aprovações sem base, o QA é Consultado e deve emitir um parecer de qualidade (liberar ou não, com os defeitos abertos) antes da decisão, e a Liderança Técnica executa a liberação. Assim a decisão fica com um único aprovador, mas apoiada por informações de qualidade.

### Práticas recomendadas

| Prática recomendada | Problema que ajuda a resolver | Papéis envolvidos |
|---|---|---|
| **Definição de Pronto (Definition of Done) e critérios de aceitação combinados antes de implementar** (conversa entre produto, desenvolvimento e QA) | Critérios de "pronto" pouco claros e funcionalidades que chegam com defeitos | Responsável pelo Produto, Desenvolvedor, QA |
| **Registro de todos os defeitos em um quadro único, com triagem periódica** (todos podem registrar, o QA acompanha e o produto prioriza) | Defeitos não registrados ou sem acompanhamento e ausência de responsável pela priorização | QA, Desenvolvedor, Responsável pelo Produto |

---

## Uso de inteligência artificial

**Ferramenta utilizada:**
Claude (Anthropic).

**Como foi utilizada:**
Novamente solicitei que conferisse a ortografia e reescreve possíveis erros em minhas respostas, também solicitei que montasse o README de acordo com a estrutura solicitada.

**Como as respostas foram verificadas:**
