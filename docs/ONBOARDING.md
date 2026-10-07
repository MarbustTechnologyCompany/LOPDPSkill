# Tu primer día en la skill LOPDP Ecuador

Guía para quien empieza a mantener esta skill. Si algo no alcanza, es un error de la guía: dilo en un issue.

## 1. Qué es, en un minuto

Una **skill open-source** (plugin de Claude Code) para que un desarrollador en Ecuador incorpore bien la **LOPDP** (Ley Orgánica de Protección de Datos Personales, R.O. 459 de 2021) en sus proyectos: qué hacer, cuándo y cómo, a nivel de código y producto. El contenido vive en `skills/lopdp-ecuador-datos-personales/SKILL.md`, con el texto de la ley en `references/`.

- 🔴 **Es guía legal:** toda afirmación se respalda con el artículo de la ley (`references/`). Nada inventado.
- **Repo público:** sin datos personales reales ni secretos.

## 2. Qué leer, en este orden

1. [`README.md`](../README.md) — qué es e instalación.
2. Esta guía.
3. [`CONTRIBUTING.md`](../CONTRIBUTING.md) — el recorrido de cada cambio (incluye externos).
4. [`AGENTS.md`](../AGENTS.md) — estructura, precisión legal y skills.
5. [`skills/lopdp-ecuador-datos-personales/SKILL.md`](../skills/lopdp-ecuador-datos-personales/SKILL.md) — el contenido de la skill.
6. Las skills de colaboración en [`.claude/skills/`](../.claude/skills) (copia para colaboradores nuevos; los oficiales usan el directorio de la empresa).
7. [`SECURITY.md`](../SECURITY.md).

## 3. Accesos que debes pedir

Los concede Marco Antonio Bustillos (indica tu usuario de GitHub y correo):

| Acceso | Para qué |
|---|---|
| Colaborador del repo `MarbustTechnologyCompany/LOPDPSkill` (equipo Marbust) | Ramas y PRs (externos: fork + PR) |
| Tablero de Trello | Mover tus tarjetas |

## 4. Herramientas

- **git** y **GitHub CLI** (`gh`). Un editor. Claude Code para probar la skill instalada como plugin.

## 5. Tu primer issue

Sigue la skill [`trabajar-un-issue`](../.claude/skills/trabajar-un-issue/SKILL.md): elige uno chico, confirma en el issue, rama desde `main` (o fork), PR borrador, respalda cada afirmación legal con `references/`, revisa tu diff con `revisar-codigo`, pasa el QA, responde la revisión hasta el squash.

## 6. Cuentas en GitHub

`MarbustTechnologyCompany` crea los issues y aprueba los PRs. Quien implementa (`MarAntBQ`, el equipo o un externo desde un fork) hace ramas/forks y PRs. Nadie aprueba su propio PR. Merge por squash.

## 7. Lo que nunca se hace

- Afirmar algo legal sin respaldo en el texto de la ley.
- Presentar una buena práctica como obligación legal (o viceversa).
- Datos personales reales en ejemplos.
- Push directo a `main`; trabajar sin issue.
- Co-autoría de IA en commits o PRs.
