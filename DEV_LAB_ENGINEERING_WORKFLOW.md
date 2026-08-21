# Dev Lab Engineering Workflow

Cómo se mueve el trabajo dentro de Dev Lab Technologies, de una idea a
producción, y qué repo/equipo es dueño de cada etapa.

```
Idea
 ↓
Producto
 ↓
Diseño
 ↓
Engineering
 ↓
Testing
 ↓
DevOps
 ↓
Producción
```

## Las etapas

| Etapa | Qué pasa | Dónde vive | Quién |
|---|---|---|---|
| **Idea** | Se captura una idea de producto, feature o proyecto de cliente. | Issue en `product-management` (plantilla *Idea de producto*) o `software-factory` (*Proyecto cliente*) | Cualquiera puede proponer; `Product` la triagea |
| **Producto** | Se valida el problema, se prioriza contra el roadmap, se define el alcance. | `product-management` | `Product` |
| **Diseño** | Se define la solución: UX, arquitectura técnica de alto nivel, contratos de API si aplica. | Issue/PR de diseño vinculado al repo destino (`products`, `software-factory`, `innovation-lab`) | `Product` + `Engineering` |
| **Engineering** | Se implementa en una rama `feature/*` (o `fix/*`), siguiendo `ARCHITECTURE_STANDARDS.md`. | `products`, `software-factory` o `innovation-lab` | `Engineering` |
| **Testing** | Tests automatizados + revisión de PR contra el checklist estándar. | Pull Request en el repo correspondiente (plantilla de PR) | `Engineering` (autor) + revisor |
| **DevOps** | Build, despliegue a `staging`, validación, despliegue a `production`. | `infrastructure` define el pipeline; se ejecuta vía GitHub Actions en el repo del producto | `DevOps` |
| **Producción** | Feature liberada. Se monitorea; incidentes vuelven como `hotfix/*`. | — | `DevOps` + `Engineering` |

## Reglas que atraviesan todas las etapas

- **Ninguna etapa se salta**: una idea no pasa a Engineering sin haber pasado por Producto y Diseño (al menos como Issue documentado), aunque sea de forma breve para cambios pequeños.
- **Todo cambio de código pasa por Pull Request** — nunca push directo a `main`. Ver `CONTRIBUTING.md` para la estrategia de ramas.
- **`innovation-lab` es la excepción de velocidad**: prototipos pueden saltar Diseño formal, pero para graduarse a `products` o `software-factory` sí deben pasar por el flujo completo.
- **Investigación tecnológica** (`innovation-lab`) alimenta la etapa de Diseño cuando valida una alternativa técnica.

## Relación con otros documentos del DLT OS

Este documento describe el flujo de **negocio/producto** (Idea → Producción)
a alto nivel. La ejecución técnica diaria de las etapas `Engineering` y
`Testing` — Issue → Branch → Pull Request → Review → Merge, convención de
ramas, criterios de aprobación — vive en
[`docs/ENGINEERING_WORKFLOW.md`](https://github.com/Dev-Lab-Technologies/documentation/blob/main/docs/ENGINEERING_WORKFLOW.md)
(repo `documentation`). No son dos procesos distintos: este documento es la
vista de producto, ese es la vista de ejecución del mismo flujo.

El mapeo a estados de GitHub Projects usa los 9 estados canónicos
declarados en `DEV_LAB_OPERATING_SYSTEM.md`, no un set de columnas propio —
ver [`docs/governance/GITHUB_PROJECT_MANAGEMENT.md`](https://github.com/Dev-Lab-Technologies/documentation/blob/main/docs/governance/GITHUB_PROJECT_MANAGEMENT.md)
para la especificación completa del Project oficial.

---
*Estándar activo en `main`, adoptado por `Owners`/`DevOps`.*
