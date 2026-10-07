# Reglas del repositorio — LOPDP Ecuador (skill)

Este archivo es para **todas las personas y agentes de IA** que trabajan en esta skill (Claude Code, Codex, Cursor, Copilot u otros). Si usas Claude Code, se carga solo a través de `CLAUDE.md`.

- Si es tu primer día: [`docs/ONBOARDING.md`](docs/ONBOARDING.md).
- Cómo colaborar paso a paso: [`CONTRIBUTING.md`](CONTRIBUTING.md).
- Qué es y cómo se instala: [`README.md`](README.md). El contenido de la skill: [`skills/lopdp-ecuador-datos-personales/SKILL.md`](skills/lopdp-ecuador-datos-personales/SKILL.md).
- El estándar común de todos los repos de Marbust: `MarbustTechnologyCompany/.github` → `ESTANDAR-REPOSITORIOS.md`.

**Clase del repo: producto de la empresa** (`.github/marbust.json`), **público y open-source (MIT)**, publicado como **plugin/skill de Claude Code** (`.claude-plugin/`). Puede publicar novedades; ver *Novedades* en `CONTRIBUTING.md`.

**Qué es:** una **skill open-source** para que un desarrollador en Ecuador incorpore correctamente la **Ley Orgánica de Protección de Datos Personales (LOPDP, R.O. 459 de 2021)** en sus proyectos: qué hacer, cuándo y cómo, a nivel de código y de producto. El contenido vive en `skills/lopdp-ecuador-datos-personales/` con el texto de la ley en `references/`.

> 🔴 **Da guía legal.** Una afirmación equivocada puede llevar a un desarrollador a **incumplir** la ley (multas sobre la facturación). Toda afirmación legal se **respalda con el texto de la ley** (cítalo desde `references/`). No se inventa ni se generaliza.

## Estructura

```
.claude-plugin/        — marketplace.json + plugin.json (publicación como plugin de Claude Code)
skills/lopdp-ecuador-datos-personales/
  SKILL.md             — la skill (qué hacer, cuándo, cómo)
  references/          — el texto de la ley (fuente de verdad legal)
README.md · LICENSE (MIT)
```

## Idiomas

- Contenido en **español** (Ecuador, tuteo), porque la ley es ecuatoriana.
- Issues, PRs y commits en español.

## Reglas duras

1. **Flujo:** tarjeta → issue (lo abre `MarbustTechnologyCompany`) → rama → PR en borrador → QA → aprobación de la empresa → squash. Nadie hace push directo a `main`. Detalle en [`CONTRIBUTING.md`](CONTRIBUTING.md). (Contribuciones externas: fork + PR.)
2. **El issue se autocontiene.** Skill `escribir-un-issue`.
3. **Revisión obligatoria.** Antes del PR, corre `revisar-codigo`. **Codex participa siempre.**
4. **Precisión legal (regla que manda):** toda afirmación sobre la LOPDP se respalda con el artículo correspondiente del texto en `references/`. Si no está en la ley, no se afirma como obligación legal (se puede sugerir como buena práctica, marcándolo como tal).
5. **Sin datos personales reales:** los ejemplos usan datos ficticios; es un repo público.
6. **El plugin sigue válido:** si se toca `.claude-plugin/`, `marketplace.json`/`plugin.json` quedan bien formados.
7. **Verificar:** el Markdown renderiza, los enlaces a `references/` resuelven, y las citas legales corresponden al texto. El output/evidencia va en el PR.
8. **Commits** con tipo (`feat`, `fix`, `docs`, `chore`, `refactor`, `test`, `perf`) y en español. **Prohibido** co-autoría de IA en commits y en PRs.
9. **Nada de estado escrito a mano** en el README (el avance vive en issues/releases).

## Seguridad (regla dura)

- **Público:** sin datos personales reales ni secretos en el repo.
- **No inducir incumplimiento:** la guía no recomienda prácticas que violen la LOPDP.
- Una vulnerabilidad o un error legal grave se reporta en privado: ver [`SECURITY.md`](SECURITY.md).

## Skills del repositorio (para contribuir)

Hay **dos rutas** (esto es aparte de la skill que **publica** este repo):

1. **Colaboradores nuevos o externos** usan las skills de colaboración en [`.claude/skills/`](.claude/skills). Son una **copia sincronizada** desde el directorio oficial por el Action `sync-skills`; **no se editan a mano aquí**.
2. **Colaboradores oficiales de Marbust** usan el **directorio oficial** (`MarbustTechnologyCompany/ClaudeSkills`, en `~/.claude/skills`). **Es la fuente de verdad.**

| Skill | Cuándo |
|---|---|
| `escribir-un-issue` | Al crear o corregir un issue |
| `trabajar-un-issue` | Al tomar un issue, de principio a fin |
| `revisar-codigo` | **Obligatoria** antes del PR y al revisar el de otro |
