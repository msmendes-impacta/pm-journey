# Idea Intake: PM Home — visão consolidada e alertas para Project Managers

- **Slug**: pm-home
- **Created**: 2026-11-08
- **Source**: repo path `README.md` (commit `b98e6e2`, 2026-10-07, Matheus Mendes — escrito antes do bootcamp)
- **Type**: new-capability

## Idea (as captured)

Trechos literais do `README.md` (o texto completo está no arquivo, no commit citado):

> **PM Home — IGC Experience**
>
> Este projeto visa implementar uma interface centralizada para Project Managers (PMs) gerenciarem suas jornadas de projetos, com foco especial em monitoramento de IGC (Internal Governance/Compliance), rastreamento de horas de recursos e alertas proativos.

Objetivos principais, como listados:

> 1. Dashboard de Projetos em Andamento — visualização consolidada de todos os projetos ativos do PM; ordenação por prioridade e status IGC; filtros "Precisam de Atenção" e "Recursos com Horas Baixas".
> 2. Monitoramento de Horas e Recursos — Resource Roster; Hours Forecast (% de horas submetidas vs planejadas); alertas de horas críticas; detecção de over-submission ("quando horas submetidas excedem o SOW").
> 3. Sistema de Alertas IGC — IGC Health Pulse (Critical/Warning/Healthy); painel de alertas ("exceções de schedule, over-submission, etc."); "Next 7 Days"; ações contextuais (criar Resource Requests, notificar recursos, ajustar SOW).
> 4. Gestão de Continuidade de Recursos — detalhamento por recurso; "End date tracking: Alertas proativos antes do fim de assignments".
> 5. Experiência Personalizada — banner "Today's Focus"; integração com timesheet; abas (Action Dashboard, First Customer Contact, On Hold Projects, Staffing Requests, Milestones, Approvals).

Fluxos de usuário descritos:

> - Fluxo 1: Recurso com Horas Críticas — PM vê alerta, expande o projeto, "vê recurso com 4h restantes", cria um Resource Request pré-preenchido.
> - Fluxo 2: Over-submission Detectada — "Sistema detecta horas submetidas > SOW planejado"; PM revisa o assignment e "ajusta SOW ou cria exceção".
> - Fluxo 3: Low Submission Near End Date — "recurso com 38% submetido"; PM notifica o recurso; "IGC trigger é ativado corretamente".

Integrações planejadas: FinancialForce PSA (projetos, assignments, timecards), "IGC System", Resource Request System, Timesheet Entry, EPS (Enterprise Project System), Notification System.

Benefícios esperados, como escritos:

> Redução de gaps de recursos; Compliance IGC; Eficiência do PM ("visão consolidada reduz tempo de navegação entre sistemas"); Melhor previsibilidade; Ações contextuais ("reduzem cliques e tempo de execução").

Stack proposta no README: LWC, Apex, objetos Salesforce, Nebula Logger, SLDS. Time: Matheus Mendes / Nicoli Ferreira.

## Restated

Uma tela única para o Project Manager de uma empresa de serviços que reúne seus projetos ativos e o consumo de horas de cada recurso, e o avisa antes que horas acabem, estourem o contratado ou deixem de ser lançadas, em vez de ele descobrir isso navegando entre sistemas.

## Origin & Context

- **Raised by**: Matheus Mendes (autor do README, integrante do POD), 2026-10-07. *Esclarecido em 2026-11-08 (entrevista):* o autor constrói ferramentas para os PMs numa empresa de grande porte que usa o Certinia PSA; não é PM.
- **Trigger**: *Esclarecido em 2026-11-08 (entrevista):* observação das dificuldades dos PMs, não um pedido deles. Ponto de partida citado: uma experiência customizada (LWC) de agenda usada pelo Resource Manager para achar quem pode atender um Resource Request.
- **Contexto do bootcamp**: a ideia foi trazida para o desafio do MBA (startup com IA na proposta de valor, MVP em URL pública). O README é anterior ao bootcamp e não menciona IA.

## First-Glance Unknowns

- [NEEDS CLARIFICATION: o que é o "IGC" na prática — regra, sistema ou processo; quem o define e quem cobra; o que acontece quando ele "dispara"?]
- [NEEDS CLARIFICATION: qual é a dor real por trás das telas — o que acontece hoje quando horas acabam, estouram o SOW ou não são lançadas, e quanto isso custa (faturamento, cliente, compliance, tempo do PM)?]
- [NEEDS CLARIFICATION: como o PM evita essas surpresas hoje (relatórios, planilhas, rotina manual) e quanto tempo gasta nisso?]
- [NEEDS CLARIFICATION: quem sofre o problema — só o PM, ou também o recurso, o gestor de staffing, o financeiro, o cliente?]
- [NEEDS CLARIFICATION: é uma dor de uma empresa (ferramenta interna) ou de um mercado (empresas de serviços que usam PSA) — exigência do bootcamp de ser uma startup?]
- [NEEDS CLARIFICATION: onde a IA entra na proposta de valor — os alertas descritos (horas > SOW, % submetido) são regras fixas?]
- [NEEDS CLARIFICATION: dados reais pertencem ao empregador (FinancialForce/Certinia PSA); um MVP público exigiria dados fictícios?]
- [NEEDS CLARIFICATION: termos do domínio a definir — SOW, Resource Request (RR), assignment, timecard, over-submission, EPS.]
