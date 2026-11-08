# pm-home — Pendências da discovery e roteiro de conversa com usuários

- **Slug**: pm-home
- **Atualizado**: 2026-11-08
- **Para quê**: o que falta para formalizar o problema (`/speckit-assess-define` → `problem.md`) e o roteiro das conversas com PMs e Resource Managers.

> O repositório é **público**. Nada de nome de empresa, cliente, pessoa, texto de chamado ou regra interna confidencial. Só números agregados e respostas anonimizadas.

## 1. Só o autor responde — bloqueia o `define`

| # | Pergunta | Fecha no `problem.md` | Status |
|---|---|---|---|
| 1 | **PM ou Resource Manager: de quem é a dor principal?** O autor disse "principalmente PM", mas a rotina relatada (achar quem atende um Resource Request, ver disponibilidade) é do Resource Manager. Qual o palpite, e por quê? | Usuários, enunciado | Aberta |
| 2 | **O que falta no Work Planner**, em termos de problema (não de tela)? Que pergunta o usuário ainda não consegue responder com ele? | Enunciado, evidência contra | Aberta |
| 3 | **Um caso real e concreto** de overbooking: o que aconteceu, quando foi percebido, o que foi refeito (pode ser um incidente investigado pelo time, sem dados identificáveis). | Enunciado, custo de não fazer | Aberta |
| 4 | **Ferramenta interna ou startup?** Se startup, quem é o cliente (ex.: empresas que usam o Certinia PSA)? | Usuários, stakeholders, metas | Aberta |

## 2. Números — o autor levanta depois

| # | Dado | Fecha | Status |
|---|---|---|---|
| 5 | **Volume absoluto** de incidentes da categoria por mês e o período considerado (hoje: ~5% da fila; ~60% mau uso, ~40% bug) | Linha de base | Aberta |
| 6 | **Tempo atual para atender um Resource Request**, se o sistema registra | Linha de base | Aberta |
| 7 | **Dá para contar** appointments cancelados ou reatribuídos por overbooking a partir dos dados? | Métrica mensurável? | Aberta |

## 3. Conversas com usuários — roteiro na seção 5

| # | O que esperamos descobrir | Fecha | Status |
|---|---|---|---|
| 8 | Com **pelo menos 1 PM e 1 Resource Manager**: quem sente mais a dor | Confirma ou derruba o item 1 | Aberta |
| 9 | **O que acontece depois** de um overbooking (realocação, cliente, faturamento) | Custo de não fazer | Aberta |
| 10 | **Frequência** e **tempo gasto** nas verificações | Peso da dor | Aberta |
| 11 | A palavra deles para a dor, **literalmente** | Evidência de discovery (checkpoint 02) | Aberta |

## 4. Já fechado — não perguntar de novo

- **Personas**: Project Manager, Resource Manager, Technical Resource, Business Lead (provavelmente quem cobra o PM), recursos (Contacts no PSA).
- **Perguntas-chave do usuário**: "qual recurso tem quantas horas disponíveis?" e "qual recurso corre risco de overbooking?".
- **Alternativa atual**: várias telas (Resource Planner, experiências customizadas) e outras pessoas; quando dá errado, incidente para a TI (~5% da fila; ~60% mau uso, ~40% bug).
- **Candidatas a métrica**: redução do retrabalho com appointments em overbooking; tempo para atender um Resource Request.
- **Fora de escopo**: IGC; aprovações de timecard (anotados para o futuro).
- **Contexto**: Resource Planner descontinuado pela Certinia (Spring 2025); Work Planner em teste na org e não atende por completo.

Detalhes e fontes em [`research.md`](research.md).

## 5. Roteiro de conversa (chat, em inglês)

### Como conduzir

- **Do not pitch the idea.** Never ask "would a dashboard that does X be useful?" — it only gets a polite "yes".
- **One question per message**, and wait for the answer.
- **When an answer is generic** ("it's hard", "too many screens"), follow up with: *"Could you give me an example from the last time that happened?"*
- **Copy answers verbatim** into section 6, without names, customers, or ticket text.
- Talk to **at least one PM and one Resource Manager**.

### Script

> **Opening:** "Hi [name]! I'm studying how PMs and Resource Managers keep track of resource hours and availability. I'm not selling or building anything specific yet — I just want to understand how it works today. Could I ask you about six quick questions here, whenever you have a moment?"
>
> 1. "What's your role, and roughly how many projects or resources are you responsible for right now?"
> 2. "Tell me about the **last time** you needed to know whether someone had hours or availability. What were you trying to decide?"
> 3. "How did you get to the answer? Which screens did you open, who did you ask? How long did it take until you were confident?"
> 4. "Has it ever happened that you found out **too late** that someone was out of hours, overbooked, or hadn't submitted time? What happened next?"
> 5. "How often do you do this kind of check? Do you keep your own spreadsheet, report, or reminder for it?"
> 6. "If you could change **one thing** about this routine, what would it be?"
>
> **Closing:** "Thanks a lot, this really helps! Would it be okay if I came back in a few weeks to show you an early draft?"

**Follow-ups (use only if the conversation opens the door):**

- "Who else gets involved when that happens?"
- "What would have been different if you had known earlier?"
- "Is there any tool you tried for this that didn't quite work? What was missing?"

## 6. Registro das respostas

Uma seção por conversa. Respostas literais, anonimizadas.

### Conversa 1

- **Data**:
- **Papel**: PM | Resource Manager | outro
- **Canal**: chat
- **Respostas**:
  1.
  2.
  3.
  4.
  5.
  6.
- **Observações do entrevistador**:
