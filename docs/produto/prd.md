# PRD — home do PM com triagem por IA (esqueleto, v0)

> Esqueleto do checkpoint 01: os 6 pilares com o que já se sabe. Vira **PRD v1** no checkpoint 02, com MoSCoW, AI Canvas e histórias em `docs/specs/`. Dona do documento: **PO**.

## 1. Visão e objetivo

Dar ao Project Manager um lugar único para saber **quais dos seus projetos precisam de atenção hoje, em que ordem e por quê**. A IA faz a triagem; o PM decide e age.

Objetivo do MVP: demonstrar esse valor à gestão patrocinadora com modelo genérico e dados fictícios. Ver [`hipotese.md`](hipotese.md).

## 2. Público-alvo

- **Usuário:** Project Manager, dono do ciclo do projeto depois do fechamento do contrato. Vê **só os próprios projetos**.
- **Fora:** Resource Manager como usuário principal (entra só de forma reativa).
- **Patrocinadora:** gestão da área.

## 3. Requisitos funcionais (rascunho)

- **RF-01** Listar os projetos em andamento do PM logado, um por linha, só os dele.
- **RF-02** Mostrar por projeto: horas planejadas × lançadas × restantes por alocação, sinais de pedidos de recurso e o próximo marco.
- **RF-03** Aplicar a regra genérica de **saldo de horas em risco** (parâmetros N dias úteis e P%, a definir).
- **RF-04** A IA classifica cada projeto (_ação necessária / atenção / saudável_), ordena e explica o motivo em uma frase.
- **RF-05** Sugerir a próxima ação por projeto; o PM executa (a IA nunca age sozinha).
- **RF-06** Mostrar as horas do próprio PM a lançar na semana.

## 4. Requisitos não funcionais (rascunho)

- **Privacidade:** dados fictícios; nada de dados, regras ou termos de empresa real.
- **Acesso:** escopo por PM aplicado no servidor, não só na tela.
- **IA mensurável:** casos de avaliação em `evals/` com taxa de acerto rodando no CI.
- **Plataforma:** Salesforce (Apex + LWC, layout moderno com SLDS), URL pública via Experience Cloud (ADR-0002).
- [a definir: tempo de resposta da triagem; custo por consulta à IA.]

## 5. Critérios de aceite

Escritos como Dado / Quando / Então em cada história de `docs/specs/` (checkpoint 02). Exemplo de formato, a partir do caso 3 do `concept.md`:

> **Dado** um projeto com 95% das horas lançadas, alocação terminando em 2 dias, saldo que cabe e nenhum pedido de recurso pendente,
> **Quando** o PM abre a home,
> **Então** o projeto aparece como _saudável_ e não fica à frente de projetos com alerta.

## 6. Métricas de sucesso

- Cliques até saber o que exige ação: de ≥ 10 (pior caso) para até 2.
- Concordância da triagem da IA com a de um PM: ≥ 80% dos casos de avaliação.
- Qualitativa: a gestão aprova levar a ideia adiante.

## Fora de escopo

Overbooking e incidentes; central completa de pedidos de recurso; substituir a ferramenta de planejamento em adoção; reproduzir regras ou termos internos de qualquer empresa.
