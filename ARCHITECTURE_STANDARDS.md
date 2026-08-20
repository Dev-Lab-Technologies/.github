# Estándar de repositorios — Dev Lab Technologies

Aplica a todo repositorio nuevo que se cree bajo `Dev-Lab-Technologies`
(propuesto para: `devlab-besto`, `devlab-besto-frontend`,
`devlab-besto-backend`, `devlab-infrastructure`, `devlab-documentation`,
`devlab-web`, `devlab-tools` — ver reporte CTO para el detalle de cada uno).

## Separación por repositorio

Cada producto separa responsabilidades en repos independientes en vez de un
monorepo:

- **Código de aplicación** (frontend / backend) — repos `*-frontend`, `*-backend`.
- **Documentación** — `devlab-documentation` (o `docs/` dentro del propio repo para docs técnicas específicas).
- **Infraestructura** (IaC, Cloudflare, configuración de despliegue) — `devlab-infrastructure`.
- **Testing** — vive junto al código que prueba (`tests/` o `__tests__/` en cada repo), no en un repo aparte.
- **Deploy** — definido en `.github/workflows/` de cada repo; el repo `devlab-infrastructure` guarda la configuración de los entornos.

## Estructura mínima esperada por repo

```
repo/
├── README.md              # Descripción, arquitectura, instalación, tecnologías,
│                           # variables de entorno, deploy, contribución
├── .github/
│   └── workflows/          # CI/CD del repo (permissions mínimos, ver abajo)
├── CODEOWNERS               # si difiere del default de la organización
├── src/ (o equivalente)
└── tests/ (o equivalente)
```

## Ramas

Ver `CONTRIBUTING.md` — `main` / `develop` / `feature/*` / `fix/*` / `hotfix/*`.
`main` sin push directo, solo Pull Request (branch protection pendiente de
activación — ver reporte CTO, bloqueada hoy por el plan Free de GitHub en
repos privados).

## GitHub Actions

- Todo workflow declara `permissions:` explícitos, mínimos por defecto:
  ```yaml
  permissions:
    contents: read
  ```
  y solo se amplían (`pull-requests: write`, `id-token: write`, etc.) cuando
  el job específico lo necesita.
- Usar acciones de fuentes confiables, ancladas a versión o SHA, evitando
  tags mutables (`@main`, `@master`).

## Ambientes

`development` → `staging` → `production`, cada uno con sus propios secrets
de GitHub Actions y, si aplica, su propio entorno protegido (`environments`
de GitHub).

## Pipeline estándar

```
Developer → Branch → Pull Request → GitHub Actions (tests + build) → Review → Deploy
```

---
*Estándar propuesto por el equipo `DevOps`/`Owners`, pendiente de aplicarse
al crear cada repo de producto.*
