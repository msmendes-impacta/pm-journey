# src

Código do MVP.

- `force-app/` — metadados Salesforce (pacote padrão do `sfdx-project.json`). Deploy e retrieve com o Salesforce CLI apontam para cá.

Se o MVP ganhar um serviço fora da org (ex.: integração com um modelo de IA), ele entra como pasta irmã de `force-app/` e precisa aparecer no C2 em `/architecture/`.
