# Conceito: home do PM com triagem por IA

- **Slug**: pm-home
- **Created**: 2026-11-14
- **Inputs used**: problem.md, mocks internos mostrados pelo POD (2026-11-14), decisões do POD (2026-11-14)

> **Convenção de fonte** (além de [E-n], [C-1] e [D-1]):
> **[M-1]** = dois mocks de tela de um ambiente interno, mostrados pelo POD em fotografias em 2026-11-14. As fotos **não são versionadas**; deste registro constam só **conceitos**, reescritos em termos genéricos. Nenhum nome de empresa, cliente, parceiro, pessoa, ferramenta interna, layout ou valor de regra interna foi trazido.
> **[D-2]** = decisões do POD em 2026-11-14 (este registro).

## O papel da IA (proposta)

> **A IA cruza horas, pedidos de recurso e marcos de cada projeto do PM, decide quais precisam de atenção hoje e em que ordem, e explica o porquê com a próxima ação. O painel mostra os sinais; a IA faz a triagem.**

- "Precisa de atenção" é **julgamento**, não regra fixa [D-2]. As regras fixas (limiares de horas, prazos, SLA) são **entradas** da IA, não o produto.
- O que a IA faz e um painel sozinho não faz:
  1. **Priorizar** entre sinais de tipos diferentes (horas × pedido de recurso × marco) num mesmo projeto e entre projetos [M-1].
  2. **Combinar** sinais que, sozinhos, estão aceitáveis, mas juntos indicam risco (ex.: vários pedidos de recurso do mesmo projeto começando juntos, nenhum confirmado) [M-1].
  3. **Comparar com o normal** em vez de um limiar fixo (ex.: pedido parado há mais tempo que a média) [M-1].
  4. **Explicar** em uma frase o motivo e sugerir a próxima ação.
- **Onde entra:** dentro do fluxo, na própria home do PM (não é um chat) [D-2].
- **Limite:** a IA **sugere**; quem age é o PM. Nenhuma ação é executada sozinha [D-2].
- **Teste do bootcamp** ("tirando a IA, ainda resolve a dor?"): sem a IA sobra uma tabela consolidada — resolve os cliques, mas não diz ao PM **por onde começar**. A triagem é a parte que só a IA faz.

## Escopo do primeiro recorte [D-2]

- **Base:** a visão "meus projetos em andamento" do PM — uma linha por projeto, só os projetos dele.
- **Entram:**
  - horas por alocação (planejado × lançado × restante × dias até o fim);
  - **pedidos de recurso (RR)** do projeto: precisa de RR, RR parado, RR começando sem recurso confirmado — como sinais **dentro da linha do projeto**, não como uma central de RR separada;
  - **próximo marco** do projeto (tipo e data) [D-2];
  - **regra genérica de saldo de horas** (ver abaixo);
  - **horas do próprio PM a lançar na semana**.
- **Fica fora:** a central completa de pedidos de recurso (filas por "de quem é a vez", SLA de terceiros, aprovação de viagem, tarifas) [D-2].

## Regra genérica de saldo de horas [D-1; D-2]

Criada pelo POD; não reproduz nenhuma regra interna.

- Uma alocação tem horas planejadas, um período e horas lançadas.
- Se, a **N dias úteis** do fim, o lançado estiver abaixo de **P%** do esperado para a data, o saldo **não é remanejado** automaticamente e o PM precisa decidir (avisar o recurso, ajustar o plano ou liberar o saldo).
- Se as horas restantes **não cabem** na disponibilidade do recurso até o fim, o PM precisa de um novo pedido de recurso ou de um ajuste de plano.
- [NEEDS CLARIFICATION: valores padrão de N e P, escolhidos pelo POD.]
- Nome do conceito no produto: **"saldo de horas em risco"** [D-2].

## Sinais por projeto (modelo genérico)

| Conceito          | O que importa para a triagem                                                            |
| ----------------- | --------------------------------------------------------------------------------------- |
| Projeto           | PM responsável, fase, prioridade, próximo marco                                         |
| Alocação          | recurso, período, horas planejadas e lançadas                                           |
| Recurso           | interno ou externo (parceiro), disponibilidade no período                               |
| Pedido de recurso | papel, período, horas, prioridade, status, dias no status, tentativas, motivo de recusa |
| Marco             | tipo (fase, faturamento, entrega), data                                                 |

Nomes técnicos (objetos e campos) ficam para o `plan.md`, em inglês (AGENTS.md, regra 7).

## Casos de atenção (semente dos evals)

Dados **fictícios**, inspirados nos padrões de [M-1]. São hipóteses do POD: ainda **não foram validados por um PM**. Formato esperado da IA: classificação (_ação necessária / atenção / saudável_), posição relativa e motivo citando o sinal-chave.

| #   | Projeto | Sinais                                                                                                                   | Esperado                                                       | Por quê                                                                 |
| --- | ------- | ------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------- | ----------------------------------------------------------------------- |
| 1   | Alfa    | 3 RRs abertas, todas começando em 10–14 dias, nenhuma confirmada; horas no ritmo (40% lançado); marco de fase em 18 dias | **Atenção**, à frente de projetos com um único alerta de horas | Nenhum sinal isolado é vermelho; o risco é o conjunto                   |
| 2   | Beta    | Um recurso com 18h restantes e só 4h de disponibilidade até o fim da alocação; marco de faturamento em 3 dias            | **Ação necessária**, 1º lugar                                  | Trabalho para antes do marco; ação: novo pedido de recurso              |
| 3   | Gama    | 95% das horas lançadas; alocação termina em 2 dias; restante cabe; nenhum RR pendente                                    | **Saudável**                                                   | Consumo alto é esperado no fim — falso alarme de uma regra simples de % |
| 4   | Delta   | Um recurso lançou 38% e a alocação termina em 4 dias úteis                                                               | **Atenção**                                                    | Saldo de horas em risco; ação: avisar o recurso                         |
| 5   | Épsilon | RR "enviado" há 4 dias, quando o normal é ~1,5 dia; início em 9 dias                                                     | **Atenção**                                                    | Parado acima do normal, ainda com margem; ação: cobrar o andamento      |

## Open Questions

- [NEEDS CLARIFICATION: um PM confirmaria esses 5 casos? Hoje são hipóteses do POD a partir de [M-1] (ver checkpoint 03).]
- [NEEDS CLARIFICATION: quantos projetos um PM acompanha e quantos precisam de atenção por semana? Define se a IA destaca 1 ou vários.]
- [NEEDS CLARIFICATION: qual modelo de IA e onde roda (Agentforce/Einstein na org ou API externa via Named Credential)? Decisão para o spike do ADR-0002.]
- [NEEDS CLARIFICATION: o layout será desenhado do zero, moderno, com os componentes do Salesforce (SLDS/LWC) — nada do layout de [M-1]. Detalhe no ADR de design do checkpoint 03.]
