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

## 2026-11-08 — discovery do pm-home e governança do repositório

**O que o agente fez**

- Leu as skills de discovery do Spec Kit (`assess`) antes de usá-las e mostrou ao POD que elas não entrevistam: registram o que a entrevista traz, sem inventar, marcando lacunas e exigindo uma seção de evidências contra a ideia. A entrevista seguiu as técnicas do guia de método (começar pelo problema, pedir um caso concreto, reformular e devolver).
- Registrou o README antigo como "ideia bruta" (`intake.md`), conduziu quatro rodadas de entrevista com o autor e escreveu o `research.md` com fonte para cada afirmação. A pesquisa externa achou fornecedores de PSA lançando ferramentas novas de planejamento que atacam o mesmo problema; isso entrou como evidência contra a ideia.
- Preparou o roteiro de conversa com PMs e Resource Managers em inglês e a lista do que falta para formalizar o problema (`pendencias-e-roteiro.md`).
- Adicionou a Nicoli como colaboradora e protegeu a `main` (PR com 1 aprovação, também para administradores, sem force-push).

**Onde o agente errou**

- A primeira formulação do problema veio carregada pelo README (alertas para o PM). A entrevista mostrou outro problema (visibilidade de capacidade, com o Resource Manager como possível usuário principal); o agente expôs a diferença em vez de seguir o README.
- Tentou ler a documentação de um fornecedor de PSA por fetch automático; o portal carrega por JavaScript e não devolveu conteúdo. O agente registrou a falha e usou trechos de busca, marcados como não abertos.

**Onde o POD interveio**

- Lembrou que ainda não era hora de desenhar funcionalidades: só problema, formalização e escopo.
- Pediu o roteiro em inglês, porque os PMs são americanos.
- Revisou e mesclou o PR #3 deixando só um comentário ("Revisado."), sem a aprovação formal do GitHub. O agente apontou que o repositório não registra revisão por comentário; o POD decidiu proteger a `main`, e a partir daqui o merge só libera com "Approve".

## 2026-11-13 — o problema muda de rumo com a conversa de discovery

**O que o agente fez**

- Recebeu a síntese de uma conversa de discovery do POD com um stakeholder interno da área de gestão e apontou os conflitos antes de formalizar: o enquadramento "dor interna, sem play de mercado" e a ausência de IA batiam com a regra nº 1 do bootcamp; a regra de horas que entraria no escopo era, ao mesmo tempo, regra interna da empresa (fora do escopo); "se estourar, dispara uma ação" lembrava o overbooking que acabara de sair; e a evidência vinha da patrocinadora, não de um PM.
- Com as respostas do POD, rodou o `/speckit-assess-define` e escreveu o `problem.md`: persona PM, baseline de pelo menos 10 cliques por resposta no pior caso, fora de escopo explícito e 8 perguntas em aberto. Marcou no `research.md` que o recorte anterior (capacidade e overbooking, visto pelo Resource Manager) virou histórico.
- Anonimizou tudo: sem nomes de pessoa ou empresa, e sem o termo interno da regra de horas.
- Abriu o PR #5 e começou a entrevista para achar o papel da IA.

**Onde o agente errou**

- Começou o `define` assim que o POD respondeu às perguntas, sem um "pode seguir" explícito para o plano que tinha proposto.
- Na primeira pergunta sobre a IA, falou em "tela-resumo" sem dizer que era a versão sem IA do próprio produto; o POD precisou perguntar.

**Onde o POD interveio**

- Trouxe a conversa com a gestão, que corrigiu o rumo: a discovery anterior, feita só com o autor, apontava para o Resource Manager e o overbooking.
- Decidiu: tratar o projeto como produto interno (intraempreendedorismo) até o próximo encontro; regra de negócio e modelo de dados genéricos, criados pelo POD; nada interno entra no repositório, nem anonimizado.
- Manteve os dois membros do POD como únicos testadores por enquanto. O agente registrou que isso não cumpre o "≥ 2 usuários reais" do checkpoint 03 e que vale levar a dúvida ao professor.

## 2026-11-14 — o papel da IA e os entregáveis do checkpoint 01

**O que o agente fez**

- Separou o que o PM pediu ("ver quais projetos precisam de atenção, de RR, de RR vencendo") em agregação, que um relatório resolve, e julgamento, onde cabe a IA. O POD escolheu "atenção = julgamento".
- Analisou fotos de dois mocks internos trazidos pelo POD. Registrou só conceitos, reescritos em termos genéricos (`concept.md`, fonte [M-1]); as fotos não foram versionadas. Mostrou que quase todos os alertas dos mocks são regra fixa e que só três elementos pedem julgamento: priorizar, comparar com o normal e combinar sinais do mesmo projeto. Daí saiu a frase da IA (triagem) e 5 casos fictícios que servem de semente dos evals.
- Achou termos internos de empresa no `README.md` público, vindos do commit inicial, e também no `intake.md`, no `research.md` e nas pendências. Reescreveu tudo em termos genéricos.
- Escreveu a hipótese, o Lean Canvas (versão intraempreendedorismo) e o esqueleto do PRD, e preencheu a seção "Produto" do `AGENTS.md`.

**Onde o agente errou**

- Usou "uns 8 projetos por PM" como fato na pergunta ao POD e no texto para a gestora. O número não tinha fonte, e o `problem.md` o marcava como desconhecido.
- Ao chamar os mocks de "tela A" e "tela B", não descreveu cada uma por um elemento visível. O POD confundiu as duas e chegou a pedir a troca de base antes de perceber.
- Não tinha notado, nas sessões anteriores, que o próprio agente havia citado termos internos ao registrar o README como "ideia bruta".

**Onde o POD interveio**

- Trouxe os mocks para destravar o entendimento do produto e fixou a regra: nada da empresa é exposto.
- Decidiu: a tela de projetos como base, com sinais de pedidos de recurso dentro da linha do projeto; regra genérica de horas e horas do próprio PM no escopo; marcos no primeiro recorte; IA no fluxo, só sugerindo; o nome "saldo de horas em risco"; sem nome de startup; papéis Matheus (Tech Lead e Quality & Ops) e Nicoli (Product Owner); POD de duas pessoas.
- Decidiu reescrever o histórico do git para apagar o README antigo, com o aval da Nicoli (pendente).

**Pendente: decidir com a Nicoli (levar ao próximo checkpoint)**

O texto antigo, com termos internos, saiu dos arquivos neste PR, mas continua nos commits anteriores. Reescrever a `main` não basta: o GitHub guarda cópias somente leitura dos PRs (`refs/pull/N`), e os links diretos de commit continuam abrindo o texto antigo. Opções:

| Opção                                                                                | O que apaga                | Custo                                                                                                                        |
| ------------------------------------------------------------------------------------ | -------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| (a) Reescrever o histórico + pedir ao suporte do GitHub a remoção dos dados em cache | Tudo, se o suporte atender | Force push na `main` protegida (desligar a proteção por alguns minutos); a Nicoli clona de novo; depende do prazo do suporte |
| (b) Repositório novo com histórico limpo; apagar o antigo                            | Tudo, na hora              | Perde os PRs #1 a #5 e as aprovações, que são evidência do ciclo AI-DLC; o professor precisa do link novo                    |
| (c) Tornar o repositório privado enquanto decidem                                    | Nada; só esconde           | Reversível em um clique; confirmar se o bootcamp aceita repo privado com o professor como colaborador                        |

Recomendação do agente: (c) já, como contenção; depois (a) ou (b) decididos pelo POD. Nada disso é feito sem o aval dos dois.
