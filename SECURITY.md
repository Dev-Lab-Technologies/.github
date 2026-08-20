# Política de Seguridad — Dev Lab Technologies

## Reporte de vulnerabilidades

Si encuentras una vulnerabilidad de seguridad en cualquier repositorio de
**Dev-Lab-Technologies**, repórtala de forma privada:

- **No** abras un Issue público.
- Usa la pestaña **Security → Report a vulnerability** del repositorio afectado
  (GitHub Security Advisories), o escribe a `devlabtechnologies@gmail.com`.
- Incluye: descripción, pasos para reproducir, impacto estimado y, si es
  posible, una prueba de concepto.

## Tiempos de respuesta objetivo

| Severidad | Primera respuesta | Remediación objetivo |
|---|---|---|
| Crítica | 24 h | 7 días |
| Alta | 48 h | 15 días |
| Media | 5 días | 30 días |
| Baja | 10 días | Siguiente ciclo de release |

## Alcance

- Repositorios privados y públicos bajo la organización `Dev-Lab-Technologies`.
- Infraestructura de CI/CD (GitHub Actions) y dependencias declaradas
  (Dependabot).

## Fuera de alcance

- Ataques de ingeniería social.
- Vulnerabilidades en dependencias de terceros ya reportadas públicamente sin
  un vector de explotación específico a nuestro código.

## Buenas prácticas obligatorias

- Nunca subir API keys, tokens, contraseñas o credenciales al repositorio
  (usar GitHub Secrets / variables de entorno).
- Dependabot alerts y actualizaciones de seguridad activas por defecto en
  todos los repos de la organización.
- Revisión de dependencias antes de cada release.

---
*Este documento es una propuesta inicial de gobierno de seguridad, pendiente
de revisión por el equipo `Security`.*
