# Security Controls & Compliance

Estado real (no aspiracional) de los controles de seguridad de
Dev Lab Technologies en GitHub, verificado contra la API — no contra lo que
se propuso. Complementa a [`SECURITY.md`](./SECURITY.md) (política de
reporte de vulnerabilidades): este documento cubre los controles operativos,
`SECURITY.md` cubre el proceso de divulgación.

## Matriz de controles

| Control | Alcance | Estado | Verificado |
|---|---|---|---|
| Dependabot alerts | Los 8 repos de la org | ✅ Activo | `GET /repos/{repo}/vulnerability-alerts` → `204` en los 8 |
| Dependabot automated security fixes | Los 8 repos de la org | ✅ Activo | `GET /repos/{repo}/automated-security-fixes` → `enabled:true` en los 8 |
| Dependency graph | Org (repos nuevos) | ✅ Activo | `orgs/{org}.dependency_graph_enabled_for_new_repositories` |
| Secret scanning + push protection | Org (repos nuevos) | 🟡 Configurado, alcance limitado | Flag activo en la org, pero `security_and_analysis` devuelve `null` por repo — GitHub Advanced Security no está disponible en repos privados del plan Free |
| 2FA obligatorio para toda la org | Org | ❌ Bloqueado | `two_factor_requirement_enabled` sigue `false` tras reintentarlo — la API lo ignora en silencio (`200 OK` sin aplicar el cambio) mientras la cuenta Owner no tenga 2FA propio activo |
| Branch protection en `main` | Todos los repos privados | ❌ Bloqueado | `403 Upgrade to GitHub Pro or make this repository public` |
| Rulesets (alternativa moderna a branch protection) | Todos los repos privados | ❌ Bloqueado | Probado directamente: mismo `403`, misma limitación de plan — no es un camino alterno |
| Permisos de equipo (least privilege) | Los 8 repos de la org | ✅ Activo | 5 equipos con `admin`/`write`/`maintain`/`triage`/`read` verificados por repo (ver `DEV_LAB_OPERATING_SYSTEM.md`) |
| Revisión de PR obligatoria | Todos los repos | 🟡 Solo por proceso | `PULL_REQUEST_TEMPLATE.md` y `docs/ENGINEERING_WORKFLOW.md` lo exigen, pero sin branch protection nada lo obliga técnicamente |

## Los 2 bloqueos raíz

Todo lo marcado ❌ se reduce a dos causas raíz, ninguna resoluble por API:

1. **2FA de la cuenta Owner** — GitHub exige que el dueño de la organización
   tenga 2FA activo en su cuenta *personal* antes de poder exigirlo a nivel
   de organización. Se activa en `github.com/settings/security`. Ninguna
   llamada de API puede hacerlo por ti — requiere confirmar un segundo
   factor (app autenticadora, SMS, llave de seguridad) de forma interactiva.
2. **Plan Free de GitHub** — branch protection, rulesets y GitHub Advanced
   Security (secret scanning completo) en repositorios **privados**
   requieren GitHub Team o superior. Es una decisión de facturación, no
   técnica.

Nada más en este documento depende de terceros — el resto de los controles
(Dependabot, permisos de equipo, proceso de revisión) ya están activos o son
100% gobierno/documentación.

## Qué pasa mientras estos dos siguen bloqueados

- **Sin branch protection**: el checklist de seguridad del PR template y el
  proceso de `ENGINEERING_WORKFLOW.md` son la única barrera — dependen de
  disciplina del equipo, no de una regla técnica. Con 0 miembros en los
  equipos hoy, el riesgo real es bajo; crece en cuanto se invite al primer
  colaborador externo.
- **Sin 2FA obligatorio**: mismo razonamiento — hoy solo hay 1 cuenta con
  acceso (el Owner), así que el riesgo práctico es bajo, pero la política
  debe estar activa *antes* de invitar a alguien más, no después.

## Cumplimiento — manejo de secretos

- Ningún secreto, token o credencial debe subirse a ningún repo (política en
  `SECURITY.md`, checklist de seguridad en `PULL_REQUEST_TEMPLATE.md`).
- Secretos de CI/CD van en GitHub Actions Secrets (por repo o por
  organización), nunca en archivos versionados — aplica igual una vez
  `infrastructure` tenga pipelines reales.
- Push protection de secretos está configurada a nivel de org para repos
  nuevos, pero su cobertura real en repos privados depende del mismo
  bloqueo de plan que el resto de GitHub Advanced Security.

## Respuesta a incidentes

- Vulnerabilidad explotable → proceso privado de `SECURITY.md` (Security
  Advisory o `devlabtechnologies@gmail.com`).
- Hallazgo de menor severidad / postura de seguridad → Issue
  `security-report.md`.
- Incidente operativo (staging/producción caídos o degradados) → Issue
  `incidente_tecnico.md`, alimenta `docs/operations/` (repo `documentation`)
  una vez haya algo real desplegado que operar.

## Checklist para cuando se resuelvan los 2 bloqueos raíz

- [ ] Activar 2FA en la cuenta Owner → activar `two_factor_requirement_enabled` en la org.
- [ ] Decidir sobre upgrade a GitHub Team → activar branch protection (o rulesets) exigiendo PR + revisión en `main` de los 8 repos → habilitar GitHub Advanced Security completo.
- [ ] Una vez ambos activos, marcar "Revisión de PR obligatoria" como ✅ técnico, no solo de proceso, en la matriz de arriba.

---
*Propuesta — pendiente de aprobación. No modifica código de producto; los
controles ✅ ya descritos aquí fueron aplicados directamente (son
configuración, no código) y verificados contra la API antes de escribir
este documento.*
