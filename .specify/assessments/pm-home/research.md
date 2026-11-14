# Idea Research: PM Home — capacidade e risco de overbooking dos recursos

- **Slug**: pm-home
- **Created**: 2026-11-08
- **Evidence confidence (overall)**: low

> Por que _low_: toda evidência sobre a dor vem de **um observador** (o autor, que constrói ferramentas para os PMs e não é PM). Nenhum PM ou Resource Manager foi ouvido ainda. O único dado quantitativo (incidentes) é uma estimativa relativa, sem volume absoluto. As fontes externas são documentação de fornecedor e blogs de marketing.
>
> Convenção de fonte: **[E-n]** = entrevista com o autor, rodada n, 2026-11-08 (registrada no histórico desta sessão; o autor é engenheiro de software numa empresa de grande porte que usa uma plataforma PSA, e o repositório é público, então nenhum nome de empresa, cliente ou pessoa é registrado).

> **Atualização 2026-11-13:** uma conversa de discovery com um stakeholder interno da área de gestão ([C-1], 2026-11-11) mudou o recorte. A persona passou a ser o **PM**, o RM é só escalonamento reativo, e **overbooking e incidentes saíram do escopo**. O problema agora é a falta de uma visão única do status dos projetos do PM. Os achados abaixo ficam como histórico; o recorte vigente está em `problem.md`.

## Users & Demand

- O autor constrói ferramentas para PMs; **não é usuário** da rotina descrita. — [E-1] (confidence: high)
- A ideia **não veio de um pedido** dos usuários; nasceu da observação das dificuldades deles pelo autor. Sinal _observado_ (comportamento), não _declarado_ (demanda). — [E-1, pergunta 4] (confidence: high)
- Personas envolvidas: Project Manager, **Resource Manager** (usa a experiência customizada de agenda para achar quem pode atender um Resource Request), Technical Resource, Business Lead (provavelmente quem cobra o PM), recursos (registrados como Contacts no PSA). — [E-1, perguntas 4 e 6] (confidence: medium — "provavelmente" foi palavra do autor para o Business Lead)
- Perguntas recorrentes do usuário: "Qual recurso tem quantas horas disponíveis?" e "Qual recurso corre perigo de ficar com overbooking?". Para respondê-las, o usuário passa por várias telas (o planejador nativo da plataforma e uma experiência customizada). — [E-1, pergunta 5] (confidence: medium — relato do observador)
- Também citados: dificuldade de centralizar informação, muitos cliques, dependência de feedback de outras pessoas e comunicação assíncrona. — [E-1, pergunta 2] (confidence: low — formulação genérica, sem caso concreto)
- Frequência: Resource Requests surgem "constantemente"; o trabalho é "corriqueiro". — [E-2, pergunta 8] (confidence: medium — sem número)
- Persona principal declarada pelo autor: "principalmente PM". — [E-3, pergunta 13] (confidence: low — **em tensão** com a evidência de que a rotina de disponibilidade é do Resource Manager; ver Gaps)

## Prior Art

- **Interno — experiência customizada de agenda**: mostra ao Resource Manager quem tem horário livre para atender um pedido de recurso. O autor diz que operações feitas nela "poderiam ser resumidas" na nova experiência. — [E-1, pergunta 4] (confidence: high — o autor conhece o componente)
- **Mercado — fornecedores de PSA**: há fornecedores substituindo planejadores de recurso antigos por ferramentas novas que prometem equilibrar necessidade × disponibilidade, e lançando cálculo de disponibilidade por agenda; parceiros associam isso à redução de overbooking. — [pesquisa de mercado de 2026-11-08; fontes de fornecedor específico removidas em 2026-11-14 para não associar o ambiente do autor a um produto] (confidence: low — material de fornecedor e de parceiro)
- **Concorrente — Microsoft Dynamics 365 Project Operations**: a documentação diz que certos métodos de alocação (Full Capacity, Percentage Capacity, Evenly Distribute Hours) **levam a overbooking** se o recurso já está comprometido em outros projetos, **sem notificar** que houve overbooking. Mostra que o problema não é exclusivo de um fornecedor. — [learn.microsoft.com] (confidence: medium — documentação oficial, mas de outro produto)
- **Mercado — fluxo de Staffing Request**: Planview descreve o padrão PM solicita, Resource Manager revisa/aprova/atribui/rejeita — o mesmo desenho de papéis relatado pelo autor. — [success.planview.com] (confidence: medium)

## Market & Context

- Alternativa usada hoje: navegar entre telas nativas e customizadas e pedir informação a outras pessoas; quando dá errado, **abrir incidente para a TI**. — [E-1, E-2 perguntas 5 e 10] (confidence: medium)
- Custo de não fazer nada observado: **retrabalho manual** (ex.: cancelar um appointment) e intervenção manual após overbooking; o autor _acredita_ que os usuários realocam o recurso ou trocam quem atende o Resource Request, mas **não sabe** o que acontece depois. — [E-2, perguntas 9 e 10] (confidence: low para a consequência — "não sei, acredito")
- Fontes de mercado associam overbooking a **visibilidade fragmentada** e processos desconectados, e citam "reduzir o tempo para alocar (time to staff)" como benefício de uma boa gestão de recursos. Planilhas ainda são usadas por muitas empresas. — [birdviewpsa.com; tsia.com] (confidence: low — blogs de fornecedores, sem dado primário)
- Uma pesquisa com 154 executivos de empresas de serviços profissionais associa falta de visibilidade da demanda a mais dor com mudanças do cliente. — [blog.planview.com] (confidence: low — números não conferidos no relatório completo)

## Data & Constraints

- Incidentes de TI: o autor relatou que parte da fila de incidentes é sobre esta categoria (agenda, overbooking, pedido de recurso), em sua maioria mau uso e não bug. Os números são internos e não são registrados aqui. — [E-3, pergunta 11] (confidence: medium — estimativa do autor)
- Fora de escopo declarado pelo autor em 2026-11-08: uma **regra interna de governança de horas** (que o próprio autor não domina) e **aprovações de timecard**. _Revisto em 2026-11-14:_ uma regra **genérica** de saldo de horas entrou no escopo (ver `concept.md`). — [E-3, pergunta 14] (confidence: high)
- **Restrição de dados**: os dados reais pertencem ao empregador; o repositório e o MVP do bootcamp são públicos. — [README do repositório; regras do bootcamp] (confidence: high)
- **Restrição do bootcamp**: o produto precisa ser uma startup com IA na proposta de valor e rodar numa URL pública. — [Aula 01] (confidence: high)

## Evidence Against the Idea

- **Os fornecedores de PSA estão atacando o mesmo problema.** Ferramentas novas de planejamento prometem exatamente equilibrar necessidade × disponibilidade. Uma solução própria pode ficar redundante com uma atualização da plataforma. — [pesquisa de mercado, ver Prior Art]
- _Esclarecido em 2026-11-08 [E-4]:_ o ambiente do autor **está adotando uma ferramenta de planejamento**, que "não atende por completo os usuários"; o time já desenha uma solução customizada que vai além dele. Isso enfraquece a hipótese "é só migração/treinamento", mas a lacuna exata dessa ferramenta (o que falta) ainda não foi descrita. (confidence: medium — relato do construtor, testes em andamento)
- **A maior parte dos incidentes relatados é mau uso, não bug.** Isso é compatível com "falta de visibilidade", mas também com "falta de treinamento" — que se resolve sem software novo. — [E-3, pergunta 11]
- **Nenhum usuário pediu.** A demanda é inferida pelo construtor; o risco de resolver um problema que o usuário não prioriza é real. — [E-1, pergunta 4]
- **A métrica de sucesso é, nas palavras do autor, "um pouco subjetiva"** ("facilitar a vida"); só "redução do retrabalho de appointments com overbooking" e "tempo para atender o Resource Request" são mensuráveis, e nenhuma tem linha de base. — [E-3, pergunta 13]
- **Para o bootcamp:** o problema é de uma empresa (ferramenta interna) e não mostra ainda um mercado nem um papel para a IA; o README não menciona IA. — [intake.md; Aula 01]

## Gaps & Open Questions

- [NEEDS CLARIFICATION: quem sofre mais — PM ou Resource Manager? O autor diz "principalmente PM", mas a rotina de disponibilidade relatada é do Resource Manager. Resolver nas conversas com usuários.]
- [NEEDS CLARIFICATION: o que acontece de fato depois de um overbooking (realocação, troca de quem atende, impacto no cliente ou no faturamento)?]
- [NEEDS CLARIFICATION: tempo atual para atender um Resource Request (linha de base) e se o sistema registra isso.]
- [NEEDS CLARIFICATION: dá para contar appointments cancelados ou reatribuídos por overbooking a partir dos dados do PSA?]
- [NEEDS CLARIFICATION: o que falta na ferramenta de planejamento que está sendo adotada?]
- [NEEDS CLARIFICATION: o problema existe em outras empresas que usam PSA (mercado para a startup do bootcamp)?]
- Conversas por chat com PMs e Resource Managers: roteiro entregue ao autor em 2026-11-08; respostas pendentes.

## Sources

- Entrevista com o autor, rodadas 1–3, 2026-11-08 (histórico da sessão; sem dados identificáveis).
- `.specify/assessments/pm-home/intake.md` e `README.md` (repositório).
- https://learn.microsoft.com/en-us/dynamics365/project-operations/psa/faq-allocation-methods (host: learn.microsoft.com, policy: not fetched — trecho de resultado de busca)
- https://success.planview.com/capabilities/Professional_Services_Resource_Management/Process_flows (host: success.planview.com, policy: not fetched — trecho de resultado de busca)
- https://birdviewpsa.com/blog/prevent-resource-overbooking/ (host: birdviewpsa.com, policy: not fetched — trecho de resultado de busca)
- https://www.tsia.com/blog/professional-services-resource-management (host: www.tsia.com, policy: not fetched — trecho de resultado de busca)
- https://blog.planview.com/se/optimize-resource-productivity-profitability/ (host: blog.planview.com, policy: not fetched — trecho de resultado de busca)
