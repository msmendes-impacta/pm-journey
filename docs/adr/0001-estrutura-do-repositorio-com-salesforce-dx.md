# ADR-0001: Estrutura do repositório do bootcamp com o projeto Salesforce DX em `src/force-app`

- **Status:** Aceito
- **Data:** 2026-11-08

## Contexto

O bootcamp exige o mesmo esqueleto de pastas para todos os PODs (`README.md`, `AGENTS.md`, `docs/produto`, `docs/specs`, `docs/adr`, `docs/diario`, `docs/pitch`, `architecture/`, `prototype/`, `evals/`, `src/`, `.github/`), com o código do MVP em `/src/`.

O repositório nasceu como um projeto Salesforce DX padrão, com os metadados em `force-app/` na raiz. Precisamos cumprir a estrutura do bootcamp **e** continuar fazendo deploy e retrieve na org Salesforce pelo Salesforce CLI e pelas extensões do VS Code.

## Decisão

- Os metadados Salesforce ficam em **`src/force-app/`**, declarado como pacote padrão no `sfdx-project.json` (`"path": "src/force-app"`). Todo metadado novo entra em `src/force-app/main/default/`.
- As pastas de suporte do Salesforce DX ficam na raiz, onde a ferramenta e as extensões as esperam: `manifest/` (`package.xml`), `config/` (definição de scratch org), `scripts/` (Apex anônimo e SOQL de exemplo).
- Cada pasta exigida pelo bootcamp ganha um `README.md` curto dizendo o que vai nela e em qual checkpoint. Isso também garante que a pasta exista no Git, que não versiona pasta vazia.
- Um serviço fora da org (por exemplo, uma integração com um modelo de IA), se existir, entra como pasta irmã de `src/force-app/` e precisa aparecer no C2.

## Consequências

- **Bom:** cumpre o esqueleto do bootcamp sem quebrar o Salesforce DX. Verificado em 2026-11-08 contra a org `org-impacta`: retrieve pelo `manifest/package.xml` concluído com sucesso, e deploy em `--dry-run` de uma classe de teste a partir de `src/force-app` validado (nada foi gravado na org).
- **Bom:** ESLint, Prettier e Jest de LWC não precisaram de ajuste: os filtros deles valem para qualquer pasta, e o Jest lê o caminho do `sfdx-project.json`.
- **Custo:** `manifest/`, `config/` e `scripts/` ficam fora da lista do bootcamp, como pastas extras na raiz. Estão documentadas no `AGENTS.md`.
- **Limite já existente, não causado por esta decisão:** a org de desenvolvimento é uma Developer Edition sem source tracking. Trabalhamos com `--source-dir` e `--manifest`, não com push/pull nem com `deploy preview`.
