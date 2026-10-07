# Cómo colaborar — LOPDP Ecuador (skill)

Esta guía es el recorrido de cada cambio. Las reglas están en [`AGENTS.md`](AGENTS.md); si es tu primer día, parte de [`docs/ONBOARDING.md`](docs/ONBOARDING.md).

Este repo es **público y open-source**. Las contribuciones externas son bienvenidas: abre un issue o un PR desde un fork. El mantenedor (Marbust Technology Company) revisa y mergea.

## El flujo (equipo Marbust)

1. **Tarjeta en Trello** — marca Marbust Dev, severidad, ejecutor, cómo probar.
2. **Issue** — lo abre `MarbustTechnologyCompany` con la plantilla. Se autocontiene. Skill `escribir-un-issue`.
3. **Rama** — desde `main`, nunca push directo a `main`.
4. **PR en borrador** — con la plantilla (`Refs #N`); al terminar, `Closes #N` y listo.
5. **Verificación real** — respalda las afirmaciones legales y **pega la evidencia** en el PR.
6. **Revisión / QA** — antes del PR corre `revisar-codigo`. **Codex participa siempre.** Si el QA encuentra errores (legales o de forma), la empresa comenta **solicitando cambios**; se corrige, se responde, y recién si pasa se aprueba.
7. **Aprobación** — la da `MarbustTechnologyCompany` (el autor no se auto-aprueba).
8. **Squash** — un issue, un PR, un commit.

## Verificación (antes de pedir revisión)

| Qué | Para qué |
|---|---|
| Respaldo legal | cada afirmación nueva/cambiada cita el artículo en `references/` |
| Render del Markdown | `SKILL.md` renderiza, enlaces a `references/` válidos |
| Plugin válido | `.claude-plugin/` bien formado si se tocó |
| Sin datos reales | ejemplos ficticios únicamente |

## Novedades (producto público)

Cada PR declara su **Novedad** (pública / interna / hito). La línea pública la puede leer cualquiera: **no** afirma algo legal sin respaldo ni incluye datos personales. El check "Checks del PR" exige las tres líneas.

## Reglas que no se discuten dentro de un PR

- **Precisión legal:** respaldada por el texto de la LOPDP (`references/`). Lo que no está en la ley se marca como buena práctica, no como obligación.
- **Sin datos personales reales** ni secretos (repo público).
- La guía no induce a incumplir la LOPDP.
- Commits con tipo, en español. **Prohibida la co-autoría de IA** en commits y PRs.
