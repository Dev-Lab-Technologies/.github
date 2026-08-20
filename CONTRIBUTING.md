# Guía de Contribución — Dev Lab Technologies

## Estrategia de ramas

| Rama | Propósito | Reglas |
|---|---|---|
| `main` | Producción | Sin push directo. Solo vía Pull Request, con revisión y checks obligatorios (branch protection pendiente de activar — ver `SECURITY.md`/reporte CTO). |
| `develop` | Integración | Base para `feature/*`, `fix/*`. Se mergea a `main` por release. |
| `feature/*` | Nuevas funcionalidades | Sale de `develop`, vuelve a `develop` vía PR. |
| `fix/*` | Correcciones no urgentes | Sale de `develop`, vuelve a `develop` vía PR. |
| `hotfix/*` | Errores críticos en producción | Sale de `main`, vuelve a `main` **y** a `develop` vía PR. |

## Flujo de Pull Request

1. Crear rama desde `develop` (o `main` para `hotfix/*`) con prefijo correspondiente.
2. Commits descriptivos (convención sugerida: `tipo: descripción corta`, ej. `fix: corrige validación de login`).
3. Abrir Pull Request usando la plantilla del repositorio.
4. Pasar CI (tests, build) y al menos 1 revisión aprobada antes de mergear.
5. Ningún merge automático — lo aprueba y ejecuta una persona.

## Checklist antes de abrir un PR

- [ ] Código revisado por al menos un compañero.
- [ ] Tests ejecutados localmente / en CI.
- [ ] Sin secretos, tokens ni credenciales en el diff.
- [ ] Documentación (README/CHANGELOG) actualizada si aplica.

## Issues

- **Bug report**: usar la plantilla `bug_report.md`.
- **Feature request**: usar la plantilla `feature_request.md`.

---
*Propuesta inicial de gobierno de contribución, pendiente de revisión por
`Engineering` y `DevOps`.*
