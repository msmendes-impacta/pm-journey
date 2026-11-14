# Problem Definition: PM sem visão única do status dos próprios projetos

- **Slug**: pm-home
- **Created**: 2026-11-13
- **Inputs used**: intake.md, research.md, conversa de discovery com stakeholder interno (2026-11-11), decisões do POD (2026-11-13)

> **Convenção de fonte** (além de [E-n] do `research.md`):
> **[C-1]** = conversa de discovery com um stakeholder interno da área de gestão, 2026-11-11, registrada em anotações do POD e em transcrição automática com lacunas. Nenhum nome de pessoa ou empresa é registrado aqui.
> **[D-1]** = decisões do POD em 2026-11-13 (este registro).
>
> **Mudança de rumo em relação ao `research.md`:** a [C-1] substitui o recorte anterior (capacidade e overbooking do ponto de vista do Resource Manager). Overbooking e incidentes saíram do escopo; a persona passou a ser o PM. Os achados antigos continuam no `research.md` como histórico.

## Problem Statement

O Project Manager de uma empresa de serviços que usa uma plataforma PSA não tem um lugar onde veja, de uma vez, o status de recursos, horas e entregas dos **seus** projetos e o que vem a seguir. Para responder a uma pergunta simples ("como estão os recursos e as horas deste projeto?"), ele navega lista de projetos → projeto → assignment e repete o caminho para cada projeto, lendo informação demais e sem curadoria — no pior caso, **pelo menos 10 cliques** para uma única resposta [C-1; D-1].

## Affected Users & Stakeholders

- **Users**:
  - **Project Manager (PM)** — dono do ciclo do projeto depois do fechamento do contrato (recursos, entregas, planejamento, milestones); quem decide a alocação e quem consultaria a informação todo dia [C-1]. _Fonte indireta:_ a afirmação vem do stakeholder de gestão, não de um PM ouvido diretamente.
  - **Resource Manager (RM)** — entra de forma reativa, quando o PM não acha um recurso; **não é o usuário-alvo** [C-1].
- **Stakeholders**:
  - **Gestão da área (patrocinadora)** — decide se a ideia avança como próximo passo depois da plataforma de planejamento que está sendo adotada; o MVP serve para demonstrar valor a ela [C-1].
  - **POD do bootcamp** — constrói o MVP genérico e responde pela entrega acadêmica [D-1].
  - **Professor do bootcamp** — avalia; precisa aceitar o enquadramento como produto interno (intraempreendedorismo) [D-1].

## Goals

- O PM responde "como estão recursos, horas e entregas dos meus projetos?" sem percorrer projeto por projeto [C-1].
- O PM vê só os próprios projetos — o escopo de acesso por PM, que a ferramenta adotada hoje não respeita, vira regra [C-1].
- O PM enxerga não só o estado atual, mas o que vai acontecer (horas restantes distribuídas nos dias úteis que sobram e o que estoura) [C-1].
- Demonstrar esse valor à gestão com um MVP genérico e dados fictícios, a ponto de justificar adaptá-lo à realidade da empresa depois [C-1; D-1].

## Non-Goals

- Prevenir overbooking ou reduzir incidentes de TI [C-1].
- Competir com ou substituir a plataforma de planejamento que está sendo adotada [C-1].
- Atender o Resource Manager como usuário principal [C-1].
- Reproduzir regras de negócio, modelo de dados ou termos internos da empresa: o MVP usa regra e modelo **genéricos**, criados pelo POD; a especificidade só entra se a ideia for aprovada internamente, e fora deste repositório [D-1].
- Usar dados reais, ou trazer qualquer código, dado ou texto do ambiente da empresa para este repositório (e o inverso) [C-1; D-1].
- Play de mercado: até o próximo encontro o projeto é tratado como produto interno (opção "intraempreendedorismo") [D-1].

## Success Metrics

- **Cliques até a resposta** "status de recursos/horas de um projeto" (baseline: **≥ 10 cliques no pior caso**, informado pelo POD [D-1]; caminho medido e número médio: desconhecidos).
- **Tempo até a resposta** para a mesma pergunta (baseline: desconhecido).
- **Projetos verificados por sessão sem trocar de tela** (baseline: 1 — o caminho atual é por projeto [C-1]).
- _Qualitativa:_ a gestão aprova levar a ideia adiante como próximo passo (baseline: ideia ainda não apresentada) [C-1].

## Cost of Inaction

O PM continua montando a visão dos projetos à mão, tela a tela; o custo cresce com o número de projetos e recursos que ele acompanha [C-1]. A plataforma de planejamento adotada segue sem visão consolidada e sem escopo por PM, e a lacuna fica sem proposta concreta para a gestão avaliar [C-1].

## Open Questions

- ~~Onde entra a IA, em uma frase?~~ **Proposta em `concept.md` (2026-11-14):** a IA faz a triagem — decide quais projetos precisam de atenção, em que ordem e por quê. Também lá: pedidos de recurso, a regra genérica de saldo de horas e as horas do próprio PM entram no primeiro recorte.
- [NEEDS CLARIFICATION: o professor aceita o enquadramento como produto interno (intraempreendedorismo) em vez de startup de mercado? Quem do POD pergunta no próximo encontro?]
- [NEEDS CLARIFICATION: validação de usuário — os únicos testadores disponíveis são dois membros do POD, que não são PMs. O checkpoint 03 pede teste com ≥ 2 usuários reais; como cumprir sem acesso a PMs?]
- [NEEDS CLARIFICATION: como os "≥ 10 cliques" foram contados — qual pergunta, quantos projetos, qual caminho — e qual o número no caso típico?]
- [NEEDS CLARIFICATION: quantos projetos e recursos um PM acompanha, e com que frequência faz essa verificação? (perguntas 1 e 5 do roteiro, ainda sem resposta)]
- [NEEDS CLARIFICATION: regra genérica de horas — quando as horas restantes não cabem nos dias úteis que sobram ("estoura"), o que o PM precisa ver ou fazer? Isso não pode virar overbooking pela porta dos fundos.]
- ~~"Entregas" (milestones) entram no primeiro recorte?~~ **Sim, como "próximo marco" do projeto** — ver `concept.md`.
- [NEEDS CLARIFICATION: o termo interno usado para a regra de redistribuição não deve aparecer no produto; qual nome genérico o POD adota?]
