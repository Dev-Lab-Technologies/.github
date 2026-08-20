# Workflows compartidos (reservado)

Esta carpeta queda reservada para **reusable workflows** de organización
(`workflow_call`) que otros repos de `Dev-Lab-Technologies` puedan invocar
(ej. un job estándar de lint+test, o un template de deploy).

No se agrega ningún workflow activo todavía a propósito: un workflow en este
repositorio se ejecutaría igual que en cualquier otro, y no hay código de
producto aquí que compilar o testear. Cuando exista un caso de uso concreto
(ej. un workflow común para todos los repos `devlab-*`), se propondrá vía PR
siguiendo el estándar de permisos mínimos:

```yaml
permissions:
  contents: read
```

y aumentando permisos solo cuando sea estrictamente necesario (ver
`ARCHITECTURE_STANDARDS.md`).
