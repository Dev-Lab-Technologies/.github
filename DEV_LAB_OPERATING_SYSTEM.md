# Dev Lab Operating System

> **Dev Lab Technologies is a technology company building software, platforms
> and technological ventures.** No es una SaaS company: SaaS es, cuando
> aplica, la forma de entrega de *algunos* productos — no la identidad de la
> compañía. Esta identidad aplica a todo el contenido de este documento y de
> los repos que gobierna; cualquier texto que la contradiga (ej. lenguaje
> "SaaS company") es un error a corregir, no una variación válida.

El documento maestro de cómo opera Dev Lab Technologies dentro de GitHub:
los 10 pilares, qué documento gobierna cada uno, y su estado real hoy —no
aspiracional—. Cada pilar aquí es un resumen con enlace a su fuente
canónica; este archivo no duplica el contenido, lo **integra**.

## Los 10 pilares

| # | Pilar | Fuente canónica | Estado |
|---|---|---|---|
| 1 | Governance | [`README.md`](./README.md) (este repo) — equipos y permisos | ✅ Activo |
| 2 | Product Management | `docs/strategy/PRODUCT_OPERATING_MODEL.md` ([`documentation`](https://github.com/Dev-Lab-Technologies/documentation)) | 🟡 Propuesto (PR) |
| 3 | Software Factory | `docs/engineering/SOFTWARE_FACTORY.md` ([`documentation`](https://github.com/Dev-Lab-Technologies/documentation)) | 🟡 Propuesto (PR) |
| 4 | Engineering Standards | [`ARCHITECTURE_STANDARDS.md`](./ARCHITECTURE_STANDARDS.md), [`CONTRIBUTING.md`](./CONTRIBUTING.md) | 🟡 Propuesto (PR) |
| 5 | Architecture | `docs/architecture/` ([`documentation`](https://github.com/Dev-Lab-Technologies/documentation)) | 🔴 Reservado, sin contenido |
| 6 | Security | [`SECURITY.md`](./SECURITY.md) | 🟡 Propuesto (PR) + ver estado real de controles abajo |
| 7 | Infrastructure | Repo [`infrastructure`](https://github.com/Dev-Lab-Technologies/infrastructure) | ✅ Repo creado, sin contenido aún |
| 8 | Operations | `docs/operations/` ([`documentation`](https://github.com/Dev-Lab-Technologies/documentation)) | 🔴 Reservado, sin contenido |
| 9 | Innovation Lab | Repo [`innovation-lab`](https://github.com/Dev-Lab-Technologies/innovation-lab) | ✅ Repo creado, sin contenido aún |
| 10 | Portfolio Management | `docs/products/PRODUCT_PORTFOLIO.md` ([`documentation`](https://github.com/Dev-Lab-Technologies/documentation)) | 🟡 Propuesto (PR) |

`✅ Activo` = ya existe y no depende de ningún PR pendiente. `🟡 Propuesto` =
escrito, esperando revisión/merge de un Pull Request. `🔴 Reservado` = la
carpeta existe, el contenido todavía no se ha escrito (no se inventó para
llenar este documento).

## Cómo se conectan los pilares

```
                    ┌──────────────┐
                    │  Governance  │  equipos, permisos, quién decide
                    └──────┬───────┘
                           │
        ┌──────────────────┼──────────────────┐
        │                  │                  │
┌───────▼────────┐ ┌───────▼────────┐ ┌───────▼────────┐
│Product Management│ │ Software Factory│ │Portfolio Management│
│  cómo nace un    │→│ cómo se construye│→│  qué existe hoy,   │
│    producto      │ │  (8 estaciones) │ │  en qué estado     │
└───────┬────────┘ └───────┬────────┘ └────────────────┘
        │                  │
        │          ┌───────▼────────┐
        │          │ Engineering     │
        │          │ Standards       │  ramas, PRs, permisos mínimos
        │          └───────┬────────┘
        │                  │
┌───────▼────────┐ ┌───────▼────────┐ ┌────────────────┐
│  Innovation Lab  │ │  Architecture   │ │    Security     │
│ investigación que│ │ decisiones y    │ │ política, SLAs, │
│ puede graduar a  │ │ estándares      │ │ revisión de PRs │
│ producto         │ │ técnicos        │ │ sensibles       │
└─────────────────┘ └───────┬────────┘ └────────────────┘
                             │
                    ┌────────▼───────┐
                    │ Infrastructure  │  CI/CD, cloud, despliegues
                    └────────┬───────┘
                             │
                    ┌────────▼───────┐
                    │   Operations    │  runbooks, incidentes, on-call
                    └────────────────┘
```

**Governance** decide quién es dueño de cada pilar (equipos `Owners`,
`Engineering`, `DevOps`, `Security`, `Product`). **Product Management**
decide qué se construye. **Software Factory** decide cómo se construye,
apoyado en **Engineering Standards** y **Architecture**. **Security** y
**Infrastructure** sostienen todo el camino a producción. **Operations**
cierra el ciclo una vez algo está vivo. **Innovation Lab** alimenta
**Product Management** con ideas validadas técnicamente. **Portfolio
Management** es la vista de conjunto de todo lo anterior.

## Pilar por pilar

### 1. Governance
5 equipos (`Owners` admin, `Engineering` write, `DevOps` maintain,
`Security` triage, `Product` read), sin miembros todavía. Tu cuenta es el
único Organization Owner. Detalle: [`README.md`](./README.md).

### 2. Product Management
Cómo nace un producto, roles (Product Owner, Tech Lead, DevOps Lead,
Security Reviewer, Owner/CTO), RACI por etapa, 9 estados del ciclo de vida.
Detalle: `PRODUCT_OPERATING_MODEL.md`.

### 3. Software Factory
Las 8 estaciones: Discovery → Diseño → Arquitectura → Desarrollo → QA →
DevOps → Lanzamiento → Escalamiento. Detalle: `SOFTWARE_FACTORY.md`.

### 4. Engineering Standards
Estructura mínima de repo, ramas (`main`/`develop`/`feature`/`fix`/`hotfix`),
permisos mínimos en Actions (`contents: read`), flujo de PR con checklist.
Detalle: [`ARCHITECTURE_STANDARDS.md`](./ARCHITECTURE_STANDARDS.md),
[`CONTRIBUTING.md`](./CONTRIBUTING.md).

### 5. Architecture
ADRs, diagramas de sistema, modelos de datos por producto. Carpeta creada,
sin ADRs todavía porque no hay productos en construcción aún. Detalle:
`docs/architecture/`.

### 6. Security
Política de reporte de vulnerabilidades y SLAs por severidad en
[`SECURITY.md`](./SECURITY.md). **Estado real de los controles** (no solo
la política escrita): Dependabot alerts/dependency graph/security updates
activos; 2FA obligatorio y branch protection **bloqueados** hoy por
limitaciones de plan/cuenta — ver reporte CTO para el detalle y las
acciones pendientes de tu parte.

### 7. Infrastructure
Cloud, CI/CD, Cloudflare, seguridad de infraestructura. Repo
[`infrastructure`](https://github.com/Dev-Lab-Technologies/infrastructure)
creado con permisos de equipo aplicados; sin runbooks ni IaC todavía —
depende de que exista un primer producto que desplegar.

### 8. Operations
Runbooks, on-call, SLAs, rollback. Carpeta creada
(`docs/operations/`), vacía a propósito — se llena cuando haya algo en
`STAGING`/`PRODUCTION` que operar. Conectado con la plantilla de Issue
**Incidente técnico**.

### 9. Innovation Lab
IA, investigación, prototipos. Repo
[`innovation-lab`](https://github.com/Dev-Lab-Technologies/innovation-lab)
creado. Un spike que valida se gradúa a producto vía la plantilla **Nuevo
producto** y entra a `Software Factory` como cualquier otro producto.

### 10. Portfolio Management
Registro de productos propios, proyectos de cliente, plataformas internas,
investigación y **ventures** (categoría agregada para iniciativas de alto
riesgo/alto potencial más allá de un producto tradicional), mapeado a los
repos existentes. **BESTO** es la primera entrada real del portafolio,
categorizada como Producto propio. Detalle: `PRODUCT_PORTFOLIO.md`.
La fuente viva a futuro es el tablero **DLT OS Product Lifecycle**
(GitHub Projects) — pendiente de crear, bloqueado por el scope `project`
del token; cuando se cree, su campo "Tipo" debe incluir `Venture` como
cuarta opción, además de Producto / Proyecto Cliente / Investigación.

## Qué falta para que el Operating System esté completo

- Fusionar los Pull Requests abiertos en [`.github`](https://github.com/Dev-Lab-Technologies/.github/pulls) y [`documentation`](https://github.com/Dev-Lab-Technologies/documentation/pulls) (nada de esto está activo hasta el merge).
- Crear el tablero **DLT OS Product Lifecycle** (requiere `gh auth refresh -s project`).
- Resolver los riesgos de seguridad pendientes (2FA, branch protection) — ver reporte CTO.
- Registrar la primera entrada real en `PRODUCT_PORTFOLIO.md` cuando exista un producto/proyecto real.

---
*Propuesta — pendiente de aprobación. No modifica código existente; no
reemplaza ningún documento, los integra.*
