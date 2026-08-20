# Dev-Lab-Technologies — `.github`

Repositorio especial de configuración a nivel de **organización**. GitHub usa el
contenido de este repositorio como valor por defecto para cualquier repo de
`Dev-Lab-Technologies` que no tenga su propia versión del archivo.

## Contenido

| Archivo | Propósito |
|---|---|
| [`CODEOWNERS`](./CODEOWNERS) | Dueños por defecto de revisión de código |
| [`SECURITY.md`](./SECURITY.md) | Política de reporte de vulnerabilidades |
| [`CONTRIBUTING.md`](./CONTRIBUTING.md) | Flujo de ramas, commits y Pull Requests |
| [`ARCHITECTURE_STANDARDS.md`](./ARCHITECTURE_STANDARDS.md) | Estándar de estructura para nuevos repositorios de producto |
| [`DEV_LAB_ENGINEERING_WORKFLOW.md`](./DEV_LAB_ENGINEERING_WORKFLOW.md) | Pipeline Idea → Producción y qué repo/equipo es dueño de cada etapa |
| [`.github/PULL_REQUEST_TEMPLATE.md`](./.github/PULL_REQUEST_TEMPLATE.md) | Plantilla por defecto de Pull Request |
| [`.github/ISSUE_TEMPLATE/`](./.github/ISSUE_TEMPLATE) | Idea de producto, Feature request, Bug report, Proyecto cliente, Investigación tecnológica |
| [`.github/workflows/`](./.github/workflows) | Workflows reutilizables (`workflow_call`) |

## Repositorios base de la organización

| Repo | Propósito |
|---|---|
| [`product-management`](https://github.com/Dev-Lab-Technologies/product-management) | Ideas, roadmap, discovery |
| [`software-factory`](https://github.com/Dev-Lab-Technologies/software-factory) | Proyectos de software para clientes |
| [`products`](https://github.com/Dev-Lab-Technologies/products) | Productos tecnológicos propios |
| [`infrastructure`](https://github.com/Dev-Lab-Technologies/infrastructure) | Cloud, CI/CD, DevOps, seguridad |
| [`innovation-lab`](https://github.com/Dev-Lab-Technologies/innovation-lab) | IA, investigación, prototipos |
| [`documentation`](https://github.com/Dev-Lab-Technologies/documentation) | Documentación empresarial y técnica |

## Equipos de la organización

| Equipo | Permiso | Responsabilidad |
|---|---|---|
| `Owners` | admin | Gobierno de GitHub, permisos, seguridad crítica |
| `Engineering` | write | Desarrollo frontend/backend, APIs, PRs |
| `DevOps` | maintain | CI/CD, GitHub Actions, infraestructura |
| `Security` | triage | Auditorías, vulnerabilidades, cumplimiento |
| `Product` | read | Documentación, roadmap, issues |

> Este archivo y el resto de este repositorio son una **propuesta** sujeta a
> revisión vía Pull Request antes de fusionarse a `main`.
