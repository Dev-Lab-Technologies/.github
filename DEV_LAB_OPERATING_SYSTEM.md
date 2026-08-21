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
| 1 | Governance | [`README.md`](./README.md) (este repo) — equipos y permisos; `docs/governance/GITHUB_PROJECT_MANAGEMENT.md` ([`documentation`](https://github.com/Dev-Lab-Technologies/documentation)) — especificación del Project oficial | ✅ Activo (equipos) + 🟡 Project especificado, sin crear |
| 2 | Product Management | `docs/strategy/PRODUCT_OPERATING_MODEL.md`, `docs/strategy/PRODUCT_CRITERIA.md` ([`documentation`](https://github.com/Dev-Lab-Technologies/documentation)) | ✅ Activo en `main` |
| 3 | Software Factory | `docs/engineering/SOFTWARE_FACTORY.md`, `docs/ENGINEERING_WORKFLOW.md` ([`documentation`](https://github.com/Dev-Lab-Technologies/documentation)) | ✅ Activo en `main` |
| 4 | Engineering Standards | [`ARCHITECTURE_STANDARDS.md`](./ARCHITECTURE_STANDARDS.md), [`CONTRIBUTING.md`](./CONTRIBUTING.md) | ✅ Activo en `main` |
| 5 | Architecture | `docs/architecture/PORTFOLIO_ARCHITECTURE.md` ([`documentation`](https://github.com/Dev-Lab-Technologies/documentation)) | 🟡 Modelo de portafolio activo; ADRs por producto siguen reservados, sin contenido |
| 6 | Security | [`SECURITY.md`](./SECURITY.md), [`SECURITY_CONTROLS.md`](./SECURITY_CONTROLS.md) | ✅ Activo (Dependabot en los 8 repos) + 🔴 2 bloqueos raíz (2FA de cuenta, plan de GitHub) — ver detalle abajo |
| 7 | Infrastructure | Repo [`infrastructure`](https://github.com/Dev-Lab-Technologies/infrastructure) | ✅ Repo creado, sin contenido aún |
| 8 | Operations | `docs/operations/` ([`documentation`](https://github.com/Dev-Lab-Technologies/documentation)) | 🔴 Reservado, sin contenido |
| 9 | Innovation Lab | Repo [`innovation-lab`](https://github.com/Dev-Lab-Technologies/innovation-lab) | ✅ Repo creado, sin contenido aún |
| 10 | Portfolio Management | `docs/products/PRODUCT_PORTFOLIO.md` ([`documentation`](https://github.com/Dev-Lab-Technologies/documentation)) | ✅ Activo en `main` — BESTO registrado |

`✅ Activo` = fusionado en `main`, no depende de ningún PR abierto. `🟡` =
parcialmente activo (una parte en `main`, otra parte real todavía sin
escribir). `🔴 Reservado` = la carpeta existe, el contenido todavía no se ha
escrito (no se inventó para llenar este documento). Última sincronización:
Fase 5 — antes de esta fase, 5 de estas 10 filas llevaban desde Fase 1/3/4
diciendo "Propuesto (PR)" o "Reservado" pese a que sus PR ya estaban
fusionados (o, en el caso de Security, se fusionó recién en esta misma
fase — ver §"Qué falta").

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
único Organization Owner. Detalle: [`README.md`](./README.md). Especificación
del futuro GitHub Project oficial (campos, reglas de uso — propuesta, sin
crear aún): `docs/governance/GITHUB_PROJECT_MANAGEMENT.md` (repo `documentation`).

### 2. Product Management
Cómo nace un producto, roles (Product Owner, Tech Lead, DevOps Lead,
Security Reviewer, Owner/CTO), RACI por etapa, 9 estados del ciclo de vida.
Detalle: `PRODUCT_OPERATING_MODEL.md`. Criterios objetivos de entrada al
portafolio (cuándo aprobar algo nuevo): `PRODUCT_CRITERIA.md`.

### 3. Software Factory
Las 8 estaciones: Discovery → Diseño → Arquitectura → Desarrollo → QA →
DevOps → Lanzamiento → Escalamiento. Detalle: `SOFTWARE_FACTORY.md`. Flujo
diario de ejecución (Issue → Branch → PR → Review → Merge, convención de
ramas, roles): `ENGINEERING_WORKFLOW.md`.

### 4. Engineering Standards
Estructura mínima de repo, ramas (`main`/`develop`/`feature`/`fix`/`hotfix`),
permisos mínimos en Actions (`contents: read`), flujo de PR con checklist.
Detalle: [`ARCHITECTURE_STANDARDS.md`](./ARCHITECTURE_STANDARDS.md),
[`CONTRIBUTING.md`](./CONTRIBUTING.md).

### 5. Architecture
Modelo de portafolio, clasificación productos/plataformas/ventures, y
relación entre Dev Lab Technologies S.A.S. y sus productos (ej. BESTO):
`PORTFOLIO_ARCHITECTURE.md`. ADRs y diagramas *por producto* siguen
reservados, sin contenido — no hay productos en construcción aún.

### 6. Security
Política de reporte de vulnerabilidades y SLAs por severidad en
[`SECURITY.md`](./SECURITY.md). **Matriz de controles real** (Fase 3) en
[`SECURITY_CONTROLS.md`](./SECURITY_CONTROLS.md): Dependabot alerts +
automated security fixes activos en los **8 repos** de la org (verificado
individualmente, no solo el flag de org); 2FA obligatorio y branch
protection **bloqueados** por dos causas raíz que requieren acción tuya
directamente en GitHub (2FA en tu cuenta personal; decisión de upgrade de
plan) — ninguna resoluble por API.

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

## Ciclo de vida canónico (Fase 6)

Los 9 estados de este documento (§ arriba, pilar Product Management /
Portfolio Management) son la **fuente de verdad** del ciclo de vida de
cualquier entrada del portafolio:

```
IDEA → DISCOVERY → RESEARCH → DESIGN → DEVELOPMENT →
TESTING → STAGING → PRODUCTION → ITERATION
```

`PRODUCT_LIFECYCLE.md` (repo `documentation`) usa una nomenclatura de 7
nombres más simple, pensada para conversación de negocio — no es una
fuente de verdad alterna, es una **vista** de estos mismos 9 estados con un
crosswalk explícito. Cuando se cree el tablero de GitHub Projects, su campo
Status usa estos 9 nombres directamente (no el set de `PRODUCT_LIFECYCLE.md`).

## Qué falta para que el Operating System esté completo

Actualizado en Fase 5 — lo ya resuelto (fusión de PRs de Fase 1–4, alta de
BESTO) se retiró de esta lista; solo quedan los pendientes reales de hoy:

- **GitHub Project "DLT OS Product Lifecycle" + sus 7 campos personalizados
  + labels organizacionales** — bloqueados por el scope `project` del
  token (`gh auth refresh -s project`); los labels esperan expresamente a
  esto por instrucción explícita, no por límite técnico propio.
- **2FA obligatorio a nivel de organización** — bloqueado porque la cuenta
  Owner no tiene 2FA activo; requiere acción tuya en
  `github.com/settings/security`, ninguna llamada de API lo resuelve.
- **Branch protection / Rulesets** — bloqueados por el plan Free de GitHub
  en repos privados (probado con ambas APIs, mismo `403`); requiere
  decisión de upgrade de plan.
- **Campos "Por definir" en la entrada de BESTO** (`PRODUCT_PORTFOLIO.md`):
  Prioridad, Equipo responsable, Fecha objetivo — pendientes del triage
  formal de `Product`.
- **Campo "Lifecycle Stage" del futuro tablero de Projects**: al crearlo,
  usar los 9 estados canónicos de este documento como su set de valores en
  vez del set separado especificado originalmente — evita una cuarta
  nomenclatura antes de que llegue a existir.

---
*Activo en `main`. Última sincronización de estado: Fase 6 — ciclo de vida
declarado canónico. No modifica código existente; no reemplaza ningún
documento, los integra.*
