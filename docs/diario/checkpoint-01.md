# Diário agêntico — checkpoint 01

> O que o agente fez, onde errou e onde o POD interveio. Uma entrada por sessão de trabalho, a mais nova no final.
> Agente: Claude Code (VS Code). Operador: Matheus Mendes.

## 2026-11-08 — setup do repositório e da forma de trabalho

**O que o agente fez**
- Separou as identidades Git/GitHub por pasta: commits deste repositório saem com o e-mail da Impacta e o push sai pela conta `msmendes-impacta`. Reescreveu os 4 commits antigos para o mesmo autor e enviou com force-push protegido, depois de mostrar o plano e receber o "sim".
- Leu a Aula 01 e montou o checklist dos 6 checkpoints.
- Reorganizou o repositório para a estrutura do bootcamp, mantendo o Salesforce DX funcional (ADR-0001). Verificou contra a org: retrieve com sucesso e deploy em `--dry-run` validado.
- Criou o `AGENTS.md` v0. As seções que dependem do POD ficaram marcadas como "a decidir".
- Consultou a org (licenças, limites, recursos) e levantou o que fica mais difícil num MVP em Salesforce (ADR-0002, proposto).

**Onde o agente errou**
- Rodou uma consulta SOQL com `> 0` pelo Git Bash: o shell tratou o `>` como redirecionamento e criou um arquivo vazio chamado `0` na raiz. O agente percebeu no `git status`, conferiu que estava vazio, apagou e passou a rodar SOQL pelo PowerShell.
- Tentou um retrieve com a pasta de saída fora do projeto; o CLI recusou (`OutputDirOutsideProjectError`). O agente refez numa pasta temporária dentro do repo e apagou a pasta depois.
- Afirmou de primeira que o Salesforce "atende" sem ter medido os pontos críticos. Ao ser perguntado, consultou a org e separou o que estava verificado (licenças, limites) do que não estava (créditos de IA na Developer Edition).

**Onde o POD interveio**
- Recusou versionar as skills pessoais de mentoria e o PDF da aula: os dois foram para o `.gitignore`, contrariando a recomendação inicial do agente.
- Pediu que nada fosse commitado antes de ver o resultado. Os commits só foram feitos depois, numa branch, agrupados por assunto.
- Pediu que o agente fosse além da resposta "a Developer Edition atende" e explorasse as limitações. Disso saíram a consulta à org e a lista de riscos do ADR-0002.
- Confirmou que um dos usuários administradores da org (Nicoli Ferreira) é a segunda integrante do POD. Com isso, a única licença Salesforce livre fica reservada ao terceiro membro.

## 2026-11-08 — Spec Kit no repositório

**O que o agente fez**
- Comparou o que tinha testado com o README e a documentação oficial do Spec Kit, a pedido do POD, e encontrou a CLI desatualizada (1.0.5 instalada, 1.3.2 publicada).
- Antes de instalar no repositório, testou a instalação numa pasta descartável, nas duas versões, e listou cada arquivo criado. Confirmou que nada existente seria sobrescrito e que o caminho das specs (`specs/`) é fixo.
- Instalou o Spec Kit v1.3.2 e a extensão `assess` numa branch, trocou a constituição genérica por um resumo que aponta para o `AGENTS.md`, adicionou o fluxo ao `AGENTS.md` e registrou a decisão no ADR-0003.

**Onde o agente errou**
- Recomendou instalar sem antes conferir a versão publicada. Foi o POD que pediu para comparar com a página do projeto, e a diferença de versão mudou o plano.
- A atualização da CLI (`specify self upgrade`) quebrou a instalação no Windows, porque o executável tentou se substituir enquanto rodava. O agente diagnosticou pelo estado da pasta e passou o comando de reinstalação, que resolveu.

**Onde o POD interveio**
- Pediu para instalar o Spec Kit agora, e não só no checkpoint 02 como o agente tinha sugerido, para conhecer as skills disponíveis.
- Pediu a conferência com a documentação oficial antes de seguir.
