# ADR-0003: Spec Kit como fluxo de discovery e de Spec-Driven Development

- **Status:** Aceito
- **Data:** 2026-11-08

## Contexto

O bootcamp exige rastreabilidade história → spec → PR → teste e avalia o "anti-vibecoding": qualquer membro do POD precisa explicar de qual história veio um trecho de código. A Aula 01 cita o Spec Kit como bem-vindo. O autor já usou o Spec Kit em outro projeto (Anchor), onde o `/speckit-clarify` achou ambiguidades que a entrevista livre não tinha pegado.

O POD ainda está formalizando o problema (checkpoint 01). O Spec Kit v1.3.2 traz, além do fluxo de SDD, a extensão oficial `assess` (intake → research → define → shape → decide), que organiza a discovery antes de existir qualquer feature.

Fatos verificados numa instalação de teste fora do repositório antes de instalar aqui:

- A instalação só cria `.specify/` e `.claude/skills/speckit-*`; não altera nenhum arquivo existente.
- As specs vão para `specs/` na raiz. O caminho é fixo no script `create-new-feature.ps1` e na skill `speckit-specify`; a documentação não oferece configuração para mudar a raiz. A única saída é a variável `SPECIFY_FEATURE_DIRECTORY`, por feature.
- O Spec Kit traz um `.specify/.gitignore` que ignora apenas o estado local de cada máquina, o que indica que o resto deve ser versionado.
- A criação automática de branch é uma extensão à parte (`git`), não instalada por padrão.

## Decisão

- Instalar o Spec Kit **v1.3.2** com a integração `claude` e scripts PowerShell (`specify init --here --integration claude --script ps`), mais a extensão `assess`.
- **Versionar** `.specify/` e `.claude/skills/speckit-*`: são ferramentas do POD, não preferências pessoais (diferente das skills `pmj-*`, que ficam fora do Git).
- **Specs em `docs/specs/NNN-nome/`**, como exige a estrutura do bootcamp. O agente define `SPECIFY_FEATURE_DIRECTORY` ao rodar `/speckit-specify`; a regra está no `AGENTS.md`. Os arquivos do Spec Kit **não** são editados para mudar o caminho.
- **O `AGENTS.md` é a fonte das regras.** A `constitution.md` do Spec Kit apenas resume e aponta para ele.
- A extensão `git` não é instalada: branches e PRs seguem as regras do `AGENTS.md`.

## Consequências

- **Bom:** um fluxo único e documentado do problema ao código, com artefatos por etapa que sustentam a rastreabilidade exigida.
- **Bom:** a extensão `assess` dá forma à discovery do checkpoint 01/02 e deixa evidência escrita do porquê de cada decisão de produto.
- **Custo:** o caminho das specs depende de o agente seguir uma regra, não de uma configuração. Se a regra for esquecida, a spec nasce em `specs/` na raiz e precisa ser movida. Mitigação: regra explícita no `AGENTS.md` e conferência na revisão do PR.
- **Custo:** o assessment fica em `.specify/assessments/`, pasta oculta que o professor não procura. Os entregáveis oficiais continuam em `docs/produto/`, com um ponteiro para o assessment.
- **Custo:** duas fontes de regra (`AGENTS.md` e constituição) podem divergir. Mitigação: a constituição declara que o `AGENTS.md` prevalece e é corrigida no mesmo PR.
- **Custo:** cerca de 40 arquivos gerados entram no repositório. Atualizar o Spec Kit (`specify integration upgrade claude`, `specify extension update`) gera diff nesses arquivos, que vai por PR como qualquer mudança.
- **Lição de instalação (Windows):** `specify self upgrade` falhou no meio por tentar substituir o próprio executável em uso, deixando a CLI quebrada. A recuperação foi rodar diretamente `uv tool install specify-cli --force --from git+https://github.com/github/spec-kit.git@v1.3.2`.
