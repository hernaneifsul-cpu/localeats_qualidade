# LocalEats: Qualidade de Software

Repositório das atividades da unidade curricular **Qualidade de Software** (metodologia Problem-Based Learning, PBL), com foco na análise, organização e testes de qualidade do projeto **LocalEats**.

**Integrante:** Hernane Lemes

## Sobre o LocalEats

O LocalEats é uma aplicação que conecta usuários a restaurantes locais.

- Aplicação: https://local-eats-unisenac.vercel.app/
- Funcionalidades da versão analisada: criar conta, entrar no sistema, explorar restaurantes, filtrar por especialidade, pesquisar por especialidade ou localização, favoritar e desfavoritar restaurantes, fazer pedido e consultar pedidos.

## Atividades

| Atividade | Tema | Elemento de competência | Arquivo |
|---|---|---|---|
| 01 | Fundamentos e características da qualidade | EC1 | [atividade-01-fundamentos-qualidade.md](atividades/atividade-01/atividade-01-fundamentos-qualidade.md) |
| 02 | Organização da qualidade: papéis e responsabilidades | EC2 | [atividade-02-papeis-responsabilidades.md](atividades/atividade-02/atividade-02-papeis-responsabilidades.md) |
| 03 | Estratégia e projeto de testes | EC4 | [atividade-03-estrategia-projeto-testes.md](atividades/atividade-03/atividade-03-estrategia-projeto-testes.md) |

## Resumo do trabalho

- **Atividade 01:** análise do LocalEats com base nas necessidades explícitas e implícitas dos usuários. Na exploração da funcionalidade *fazer pedido*, foram observados o registro de conta com e-mail falso, a impossibilidade de realizar o pagamento, uma página de transações com registros sem transação realizada e a ausência de opção para cancelar pedido. O requisito de qualidade proposto foi relacionado à **Corretude funcional** (ISO/IEC 25010).
- **Atividade 02:** proposta de organização da qualidade, com quatro papéis (Responsável pelo Produto, Desenvolvedor, QA e Liderança Técnica), matriz RACI, uma lacuna identificada e duas práticas de QA.
- **Atividade 03:** plano de testes simplificado para *fazer pedido*, com dois riscos priorizados, duas técnicas (transição de estados e tabela de decisão), três casos de teste e matriz de rastreabilidade.

## Estrutura do repositório

```
localeats-qualidade/
├── README.md
└── atividades/
    ├── atividade-01/
    │   ├── atividade-01-fundamentos-qualidade.md
    │   └── evidencias/
    ├── atividade-02/
    │   └── atividade-02-papeis-responsabilidades.md
    └── atividade-03/
        └── atividade-03-estrategia-projeto-testes.md
```

## Evidências

As capturas de tela e gravações da exploração da aplicação (Atividade 01) ficam em `atividades/atividade-01/evidencias/`, com nomes descritivos, sem espaços ou acentos. As Atividades 02 e 03 são predominantemente textuais e não possuem pasta de evidências.

## Uso de inteligência artificial

O uso de IA como apoio está registrado ao final de cada atividade, conforme solicitado nos enunciados.
