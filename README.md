# pm-journey

Projeto do bootcamp **Software Engineering Project** (MBA em Engenharia de Software, Faculdade Impacta).

## O que é

Não é uma startup de mercado: é uma **iniciativa interna (intraempreendedorismo)**. Somos profissionais de uma empresa de serviços que viram uma necessidade da área de negócio e estão construindo uma proposta para melhorá-la. _O enquadramento ainda será confirmado com o professor._

**O problema.** O Project Manager (PM) não tem um lugar único para ver o andamento dos **seus** projetos — horas dos recursos, pedidos de recurso, próximos marcos. Hoje ele navega projeto a projeto para montar essa visão: no pior caso, 10 cliques ou mais para uma única resposta.

**A proposta.** Uma home do PM que reúne esses sinais por projeto e usa **IA para fazer a triagem**: decide quais projetos precisam de atenção hoje, em que ordem, e explica o porquê com a próxima ação sugerida. O painel mostra os sinais; a IA diz por onde começar. Quem age é sempre o PM.

**Dados.** O MVP usa **modelo de dados e regras genéricos e dados fictícios**, criados pelo POD. Nada do ambiente, dos dados ou das regras de qualquer empresa entra neste repositório (ver `AGENTS.md`, regra 5).

## POD

| Pessoa          | Papel no bootcamp         |
| --------------- | ------------------------- |
| Matheus Mendes  | Tech Lead · Quality & Ops |
| Nicoli Ferreira | Product Owner             |

O POD tem duas pessoas.

## Onde está cada coisa

| Caminho                                                          | Conteúdo                                      |
| ---------------------------------------------------------------- | --------------------------------------------- |
| [`AGENTS.md`](AGENTS.md)                                         | Regras do agente de código (harness)          |
| [`docs/produto/`](docs/produto/)                                 | Hipótese, Lean Canvas, PRD                    |
| [`.specify/assessments/pm-home/`](.specify/assessments/pm-home/) | Discovery: problema, pesquisa, conceito da IA |
| [`docs/adr/`](docs/adr/)                                         | Decisões de arquitetura                       |
| [`docs/diario/`](docs/diario/)                                   | Diário agêntico por checkpoint                |

## MVP

**URL pública:** ainda não publicada (checkpoint 05). Stack proposta: Salesforce (Apex + LWC), ver [ADR-0002](docs/adr/0002-salesforce-como-plataforma-do-mvp.md).
