# Constituição do pm-journey

> **A fonte das regras deste projeto é o [`AGENTS.md`](../../AGENTS.md).** Esta constituição existe porque as skills do Spec Kit (`/speckit-plan`, `/speckit-analyze`) a leem para checar um plano. Ela não cria regra própria: resume as regras do `AGENTS.md` que um plano precisa respeitar. Se as duas divergirem, vale o `AGENTS.md`, e esta constituição é corrigida no mesmo PR. Decisão registrada no ADR-0003.

## Princípios

### I. Spec antes do código

Nada é implementado sem uma história em `docs/specs/` com critérios de aceite Dado / Quando / Então (`AGENTS.md`, regra 1). As specs do Spec Kit ficam em `docs/specs/NNN-nome/`, nunca em `specs/` na raiz.

### II. Rastreabilidade

Todo PR cita a(s) história(s) que atende, e todo teste aponta para a história de onde veio (regra 2). Qualquer membro do POD precisa conseguir explicar qualquer trecho: o que faz, de qual história veio e por que foi aceito.

### III. Humano decide (ciclo AI-DLC)

O agente propõe o plano, o POD aprova, o agente executa, e o POD revisa, testa e faz o merge (regra 3). Sem push direto na `main`; no máximo 2 PRs abertos (regra 4).

### IV. Decisão técnica não óbvia vira ADR

Toda decisão técnica não óbvia é registrada em `docs/adr/` (regra 6). Um plano que contraria um ADR aceito precisa de um ADR novo que o substitua.

### V. O repositório regenera o produto

Nenhum segredo no repositório (regra 5). Toda configuração feita no Setup da org volta para o repositório como metadado ou como passo a passo em `docs/` (regra 8). Código e nomes técnicos em inglês; documentação de produto em português (regra 7).

## Governança

Mudar uma regra é mudar o `AGENTS.md`, por PR revisado por outro membro do POD. Esta constituição só acompanha.

**Versão**: 1.0.0 | **Ratificada**: 2026-11-08 | **Última alteração**: 2026-11-08
