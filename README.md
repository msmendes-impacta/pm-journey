# PM Home — IGC Experience

## Visão Geral

Este projeto visa implementar uma interface centralizada para Project Managers (PMs) gerenciarem suas jornadas de projetos, com foco especial em monitoramento de IGC (Internal Governance/Compliance), rastreamento de horas de recursos e alertas proativos.

## Objetivos Principais

### 1. Dashboard de Projetos em Andamento
- **Visualização consolidada** de todos os projetos ativos do PM
- **Ordenação inteligente** por prioridade e status IGC
- **Two layouts**: Enhanced (com métricas detalhadas) e Classic (simplificado)
- **Filtros rápidos**: Todos, Precisam de Atenção, Recursos com Horas Baixas

### 2. Monitoramento de Horas e Recursos
- **Resource Roster**: Visualização em tempo real de todos os recursos por projeto
- **Hours Forecast**: Barras de progresso mostrando % de horas submetidas vs planejadas
- **Alertas de horas críticas**: Indicadores visuais quando recursos estão esgotando horas
- **Detecção de over-submission**: Alertas quando horas submetidas excedem o SOW

### 3. Sistema de Alertas IGC
- **IGC Health Pulse**: Status visual (Critical/Warning/Healthy) para cada projeto
- **Painel de alertas em tempo real**: Notificações de exceções de schedule, over-submission, etc.
- **Predição de ações**: Seção "Next 7 Days" mostrando eventos futuros que requerem atenção
- **Ações contextuais**: Botões diretos para criar Resource Requests, notificar recursos, ajustar SOW

### 4. Gestão de Continuidade de Recursos
- **Accordion rows**: Detalhamento expandido de cada recurso no projeto
- **Indicadores individuais**: Status de horas por recurso com tooltips detalhados
- **Botões de ação rápida**: New RR, Notify, View Assignment para cada recurso
- **End date tracking**: Alertas proativos antes do fim de assignments

### 5. Experiência Personalizada
- **Today's Focus Banner**: Saudação personalizada com resumo de alertas do dia
- **Timesheet integration**: Botão direto para submissão de horas do próprio PM
- **Tabs de navegação**: Action Dashboard, First Customer Contact, On Hold Projects, Staffing Requests, Milestones, Approvals

## Componentes Chave

### Enhanced Table View
- Colunas: Project Name, Hours Alert, Status, Resources, Hours Forecast, Phase, Next Milestone, Action
- Badges de prioridade (! para crítico, ↓ para warning)
- Resource roster com dots coloridos por status
- Barras de progresso de horas com indicadores de gap (overflow, low, on track)

### Classic Table View
- Layout tradicional com colunas: Project Name, Overall Status, Project Tier, Project Age, Update Date, Update, Phase, Next Milestone, Link to EPS
- Ideal para usuários que preferem visualização simplificada

### IGC Alerts Panel
- Sidebar fixo com alertas categorizados por severidade (Red/Amber/Yellow)
- Cada alerta inclui: título, descrição detalhada, botões de ação
- Atualização em tempo real

### Next 7 Days
- Timeline de eventos futuros previstos
- Marcadores coloridos por severidade
- Botões de ação direta para cada evento

## Fluxos de Usuário

### Fluxo 1: Recurso com Horas Críticas
1. PM vê alerta vermelho no banner "Today's Focus"
2. Clica em summary card "Need Attention"
3. Expande accordion do projeto
4. Vê recurso com 4h restantes
5. Clica "New RR" para criar novo Resource Request pré-preenchido

### Fluxo 2: Over-submission Detectada
1. Sistema detecta horas submetidas > SOW planejado
2. Alerta aparece no painel IGC
3. PM clica "Review Assignment"
4. Sistema abre detalhes do assignment
5. PM ajusta SOW ou cria exceção

### Fluxo 3: Low Submission Near End Date
1. Alerta amarelo para recurso com 38% submetido
2. PM clica "Notify Resource"
3. Sistema envia notificação ao recurso
4. Resource submete horas pendentes
5. IGC trigger é ativado corretamente

## Integrações Planejadas

- **FinancialForce PSA**: Dados de projetos, assignments, timecards
- **IGC System**: Regras de compliance, exceções de schedule
- **Resource Request System**: Criação de RRs pré-preenchidos
- **Timesheet Entry**: Submissão de horas do PM
- **EPS (Enterprise Project System)**: Links para projetos externos
- **Notification System**: Alertas para recursos

## Stack Tecnológico (Proposto)

- **Frontend**: Lightning Web Components (LWC) - Salesforce
- **Backend**: Apex Classes - Salesforce
- **Data Source**: Salesforce Custom e Standard Objects
- **Logging**: Nebula Logger
- **UI Framework**: Salesforce Lightning Design System (SLDS)

## Próximos Passos

1. [ ] Definir estrutura de custom objects/metadata para IGC alerts
2. [ ] Criar Apex controllers para buscar dados de projetos e recursos
3. [ ] Implementar LWC principal (pmHome) com tabs e navegação
4. [ ] Desenvolver Enhanced Table View com accordion rows
5. [ ] Implementar Classic Table View como alternativa
6. [ ] Criar IGC Alerts Panel com atualização em tempo real
7. [ ] Desenvolver Next 7 Days prediction engine
8. [ ] Integrar com Resource Request system
9. [ ] Implementar filtros e sorting
10. [ ] Adicionar testes unitários e integração

## Benefícios Esperados

- **Redução de gaps de recursos**: Alertas proativos antes do fim de assignments
- **Compliance IGC**: Detecção automática de exceções e over-submissions
- **Eficiência do PM**: Visão consolidada reduz tempo de navegação entre sistemas
- **Melhor previsibilidade**: Next 7 Days permite planejamento antecipado
- **Ações contextuais**: Botões diretos reduzem cliques e tempo de execução

## Status do Projeto

- **Fase Atual**: Especificação e design
- **Próxima Milestone**: Definição de data model e Apex controllers

---

**Team**: Matheus Mendes / Nicoli Ferreira
**Repository**: msmendes-impacta/pm-journey
**Base**: Salesforce