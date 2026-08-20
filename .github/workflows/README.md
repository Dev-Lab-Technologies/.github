# Workflows compartidos

Esta carpeta guarda **reusable workflows** de organización (`workflow_call`)
que los repos de `Dev-Lab-Technologies` pueden invocar en vez de duplicar su
propio CI.

- `reusable-standard-checks.yml` — lint + test estándar (Node.js), pensado
  como punto de partida para `products` y `software-factory`.

Ninguno de estos workflows se dispara solo: solo corren cuando otro repo los
invoca explícitamente con `uses: Dev-Lab-Technologies/.github/.github/workflows/<archivo>@main`,
así que agregarlos aquí no ejecuta nada en este repo.

Todo workflow, reutilizable o no, declara permisos mínimos por defecto:

```yaml
permissions:
  contents: read
```

y amplía solo cuando sea estrictamente necesario (ver `ARCHITECTURE_STANDARDS.md`).
