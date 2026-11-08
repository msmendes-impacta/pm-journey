# AGENTS.md — harness do agente (v0)

> Regras, stack e limites que todo agente de código segue neste repositório.
> Evolui a cada encontro com o que o POD aprende. Seções marcadas **[a decidir pelo POD]** ainda não foram fechadas.

## Produto

**[a decidir pelo POD]** — nome da startup, problema, persona e o papel da IA (ver `docs/produto/`).

## Stack

- **Salesforce** (projeto Salesforce DX). Metadados em `src/force-app/` — o pacote padrão declarado em `sfdx-project.json`.
- Apex no backend, LWC no frontend, testes de LWC com Jest (`sfdx-lwc-jest`), testes Apex na org.
- Org de desenvolvimento: alias `org-impacta` (Developer Edition, **sem source tracking** → trabalhar com `--source-dir` / `--manifest`, não com push/pull).
- **[a decidir pelo POD]** — como o MVP fica numa URL pública (ex.: Experience Cloud / Site) e como a IA é chamada; vira ADR em `docs/adr/`.

## Estrutura do repositório

| Caminho | O que vai lá |
|---|---|
| `README.md` | Startup, POD, papéis e URL do MVP |
| `AGENTS.md` | Este arquivo |
| `docs/produto/` | Lean Canvas, AI Canvas, PRD, evidências de discovery |
| `docs/specs/` · `docs/adr/` | Histórias com critérios de aceite · decisões de arquitetura |
| `docs/diario/` | Diário agêntico, um arquivo por checkpoint |
| `docs/pitch/` | `pitch.md`, `pitch.pdf`, roteiro da demo |
| `architecture/` | Modelo LikeC4 (C1 e C2) |
| `prototype/` | Telas HTML do protótipo |
| `evals/` | Casos de avaliação da IA + script com a taxa de acerto |
| `src/` | Código do MVP (`src/force-app/` = metadados Salesforce) |
| `.github/` | CI com testes e eval |
| `manifest/` · `config/` · `scripts/` | Suporte do Salesforce DX: `package.xml`, definição de scratch org, Apex anônimo e SOQL de exemplo |

Metadado Salesforce novo **sempre** dentro de `src/force-app/main/default/`. Nada fora de `src/force-app/` é enviado para a org.

## Comandos

```bash
# deploy de tudo / validar sem gravar
sf project deploy start --source-dir src/force-app --target-org org-impacta
sf project deploy start --source-dir src/force-app --target-org org-impacta --dry-run

# deploy de um componente
sf project deploy start --metadata ApexClass:NomeDaClasse --target-org org-impacta

# retrieve do que está no manifest (cai em src/force-app)
sf project retrieve start --manifest manifest/package.xml --target-org org-impacta

# testes
sf apex run test --target-org org-impacta --code-coverage --result-format human --wait 10
npm run test:unit      # LWC (Jest)
npm run lint           # ESLint em aura/lwc
npm run prettier:verify
```

## Regras do agente

1. **Spec antes do código.** Nada é implementado sem uma história em `docs/specs/` com critérios Dado / Quando / Então.
2. **Rastreabilidade.** Todo PR cita a(s) história(s) que atende; todo teste aponta para a história de onde veio.
3. **Ciclo AI-DLC.** O agente propõe o plano → o POD aprova → o agente executa → o POD revisa, testa e faz o merge.
4. **Sem push direto na `main`.** Branch → PR → CI verde → revisão de outro membro do POD → merge. No máximo **2 PRs abertos**.
5. **Nenhum segredo no repositório** (tokens, chaves de API, senhas, `.env`). Credenciais ficam na org (Named Credentials / External Credentials) ou em variáveis de ambiente do CI.
6. **Decisão técnica não óbvia vira ADR** em `docs/adr/`.
7. **Código e nomes técnicos em inglês** (classes, campos, objetos, componentes); documentação de produto em português.
8. **[a decidir pelo POD]** — padrões de Apex (ex.: `with sharing`, bulkificação, cobertura mínima), design system (ADR do checkpoint 03) e limites do que o agente pode fazer sozinho.
