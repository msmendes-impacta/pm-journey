# ADR-0002: Salesforce (Developer Edition) como plataforma do MVP

- **Status:** Proposto. Falta a confirmação do POD completo e do professor, e falta o spike de riscos descrito abaixo.
- **Data:** 2026-11-08

## Contexto

O bootcamp tem quatro regras inegociáveis: startup com IA na proposta de valor; MVP em **URL pública** com o fluxo principal de ponta a ponta; desenvolvimento agêntico pelo AI-DLC; C1 e C2 em LikeC4. A ferramenta é livre ("método fixo, ferramenta livre").

O POD quer construir o produto em Salesforce. A org disponível é a `org-impacta`. Fatos consultados nela em 2026-11-08 por SOQL e por `sf org list limits`:

| Item | Valor |
|---|---|
| Edição | Developer Edition, sem source tracking |
| Licenças Salesforce (usuários internos) | 4 no total, 3 em uso → 1 livre para o terceiro membro do POD |
| Licenças Salesforce Platform | 6 livres |
| Licenças de comunidade (usuários externos com login) | Customer Community, Customer Community Login, Customer Community Plus e Customer Community Plus Login: 5 de cada |
| Experience Cloud | ainda não ativado (o objeto `Network` não existe) |
| Agentforce | metadados presentes (`GenAiPlannerDefinition`), nenhum agente criado; 201 licenças Einstein Agent |
| Armazenamento | 5 MB de dados, 20 MB de arquivos |
| API | 15.000 chamadas por dia |

## Decisão (proposta)

Construir o MVP na plataforma Salesforce:

- **URL pública:** site do Experience Cloud com **usuário convidado** (sem login, sem licença). Se o produto precisar de identidade, usamos as licenças de comunidade (cerca de 5 usuários por tipo, o que basta para o teste com usuários e para a demo).
- **IA no produto:** Agentforce na org **ou** um LLM externo chamado por Apex via Named Credential/External Credential. A escolha vira um ADR próprio, depois do spike.
- **Design system:** **SLDS (Lightning Design System)**. As sugestões do bootcamp (shadcn/ui, Material/MUI, Carbon) são de React e não se aplicam a LWC. A escolha final é o ADR do checkpoint 03.
- **CI/CD:** GitHub Actions + Salesforce CLI com autenticação JWT (External Client App + certificado; segredo só nos secrets do GitHub). Validação (`--dry-run` com testes) no PR, deploy na org do MVP no merge.

## Consequências

**Ganhos**
- Banco, autenticação, permissões, hospedagem e site público vêm prontos: o walking skeleton depende mais de configuração do que de infraestrutura.
- Ecossistema de IA nativo (Agentforce) e um portfólio em Salesforce para o POD.

**Custos e riscos, do maior para o menor**
1. **Regeneração a partir do repositório (teste anti-vibecoding).** Parte da configuração do Salesforce é feita em telas do Setup: ativar Digital Experiences, site, permissões do convidado, agente. O que não for recuperado como metadado não existe no repo, e alguns passos não têm deploy. Mitigação: toda configuração feita em tela vira retrieve + commit; o que não tem deploy vai para um runbook em `docs/`.
2. **Uma org para 3 pessoas e para o MVP.** Sem source tracking, deploys paralelos se sobrescrevem sem aviso, e não há ambiente intermediário. Mitigação: só o CI faz deploy na org do MVP; cada membro desenvolve na própria Developer Edition ou numa scratch org (Dev Hub a avaliar).
3. **Eval da IA no CI.** Cada execução chama a IA de 10 a 20 vezes. Com Agentforce isso consome créditos (franquia da Developer Edition **não verificada**) e exige o CI autenticado na org. Com um LLM externo, a chave fica em External Credential, nunca no repo.
4. **Design system diferente do sugerido** (SLDS), e um C2 com os containers da plataforma (site Experience, LWC, Apex, banco da plataforma, IA) em vez de um front, um back e um banco separados.
5. **CI mais lento:** os testes Apex rodam dentro da org e consomem chamadas de API.
6. **Segurança do site público e LGPD:** o modelo do usuário convidado é restritivo, e Apex `without sharing` atrás de uma página pública expõe dados. Isso precisa entrar nos casos adversariais.
7. **Agentes de código conhecem menos Apex/LWC do que React:** maior risco de APIs inventadas e de limites da plataforma ignorados. Mitigação: regras de Apex no `AGENTS.md` e revisão mais atenta.
8. **Armazenamento de 5 MB:** o MVP não pode depender de volume de dados.

## Como esta proposta vira "Aceito"

Um spike, antes do checkpoint 04: (1) ativar Digital Experiences e publicar um site com um LWC "hello" acessível por URL pública; (2) deploy dessa página pelo GitHub Actions com JWT; (3) uma chamada de IA de teste (Agentforce ou LLM externo), medindo a franquia disponível. Se os três passarem, o status muda para Aceito. Se algum falhar, um novo ADR registra a alternativa.
