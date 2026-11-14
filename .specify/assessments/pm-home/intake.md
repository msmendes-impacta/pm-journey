# Idea Intake: visão consolidada e alertas para Project Managers

- **Slug**: pm-home
- **Created**: 2026-11-08
- **Source**: o `README.md` original do repositório (2026-10-07, Matheus Mendes — escrito antes do bootcamp)
- **Type**: new-capability

> **Nota 2026-11-14:** o README original descrevia um protótipo do ambiente de trabalho do autor com termos, telas e integrações internas. O texto foi substituído e este intake passou a registrar **só a ideia em termos genéricos**, sem citações literais (AGENTS.md, regra 5).

## Idea (as captured)

O README original propunha, em resumo:

1. **Painel de projetos em andamento** do PM: visão consolidada dos projetos ativos, ordenação por prioridade, filtros "precisam de atenção" e "recursos com horas baixas".
2. **Monitoramento de horas e recursos**: % de horas lançadas × planejadas por recurso; alertas de horas críticas; detecção de lançamento acima do contratado.
3. **Painel de alertas** com situação por projeto (crítico / atenção / saudável), uma lista de eventos dos próximos dias e ações diretas (abrir pedido de recurso, avisar o recurso, revisar o contrato).
4. **Continuidade de recursos**: detalhe por recurso e aviso antes do fim de cada alocação.
5. **Experiência personalizada**: resumo do dia e atalho para o PM lançar as próprias horas.

Fluxos descritos: recurso com horas críticas → PM abre um pedido de recurso; lançamento acima do contratado → PM revisa a alocação; lançamento baixo perto do fim → PM avisa o recurso.

Stack proposta: LWC, Apex, objetos Salesforce, SLDS. Time: Matheus Mendes / Nicoli Ferreira.

## Restated

Uma tela única para o Project Manager de uma empresa de serviços que reúne seus projetos ativos e o consumo de horas de cada recurso, e o avisa antes que horas acabem, estourem o contratado ou deixem de ser lançadas, em vez de ele descobrir isso navegando entre sistemas.

## Origin & Context

- **Raised by**: Matheus Mendes (autor do README, integrante do POD), 2026-10-07. _Esclarecido em 2026-11-08 (entrevista):_ o autor constrói ferramentas para os PMs numa empresa de grande porte que usa uma plataforma PSA; não é PM.
- **Trigger**: _Esclarecido em 2026-11-08 (entrevista):_ observação das dificuldades dos PMs, não um pedido deles. Ponto de partida citado: uma experiência customizada de agenda usada pelo Resource Manager para achar quem pode atender um pedido de recurso.
- **Contexto do bootcamp**: a ideia foi trazida para o desafio do MBA (startup com IA na proposta de valor, MVP em URL pública). O README original é anterior ao bootcamp e não menciona IA.

## First-Glance Unknowns

- [NEEDS CLARIFICATION: o que é, na prática, a regra interna de governança de horas citada no README original — regra, sistema ou processo; quem a define; o que acontece quando ela "dispara"?]
- [NEEDS CLARIFICATION: qual é a dor real por trás das telas — o que acontece hoje quando horas acabam, estouram o contratado ou não são lançadas, e quanto isso custa (faturamento, cliente, compliance, tempo do PM)?]
- [NEEDS CLARIFICATION: como o PM evita essas surpresas hoje (relatórios, planilhas, rotina manual) e quanto tempo gasta nisso?]
- [NEEDS CLARIFICATION: quem sofre o problema — só o PM, ou também o recurso, o gestor de staffing, o financeiro, o cliente?]
- [NEEDS CLARIFICATION: é uma dor de uma empresa (ferramenta interna) ou de um mercado (empresas de serviços que usam PSA) — exigência do bootcamp de ser uma startup?]
- [NEEDS CLARIFICATION: onde a IA entra na proposta de valor — os alertas descritos (horas acima do contratado, % lançado) são regras fixas?]
- [NEEDS CLARIFICATION: os dados reais pertencem ao empregador; um MVP público exigiria dados fictícios?]
- [NEEDS CLARIFICATION: termos do domínio a definir — contrato (SOW), pedido de recurso (RR), alocação (assignment), lançamento de horas (timecard).]
