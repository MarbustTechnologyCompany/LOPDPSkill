# 🇪🇨 LOPDP Ecuador — Skill de Protección de Datos Personales

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](./LICENSE)
[![Claude Code Skill](https://img.shields.io/badge/Claude%20Code-Skill-8A63D2.svg)](https://code.claude.com)
[![Ley](https://img.shields.io/badge/LOPDP-R.O.%20459%20(2021)-blue.svg)](./skills/lopdp-ecuador-datos-personales/references/ley-lopdp-registro-oficial-459-2021.txt)

Una **skill open source** para que cualquier desarrollador en Ecuador incorpore correctamente la
**Ley Orgánica de Protección de Datos Personales (LOPDP)** en sus proyectos — sin adivinar, sin
copiar políticas genéricas que no cumplen, y sin dejarlo "para después".

Si tu sistema recoge un **nombre, un correo o un teléfono** de una persona, esta ley te aplica.
Esta skill te dice **qué hacer, cuándo y cómo**, a nivel de código y de producto.

---

## ¿Por qué existe?

En Ecuador, la mayoría de sitios y apps recogen datos personales (formularios de contacto,
registros, newsletters, chatbots) **sin cumplir la LOPDP**: sin informar antes de recoger, con
casillas premarcadas, sin plazo de retención, sin forma real de ejercer derechos. Las multas se
calculan sobre la **facturación** del negocio, no sobre la utilidad — es dinero real.

Esta skill convierte la ley en **decisiones concretas de desarrollo**: qué base legal aplica, qué
aviso poner junto al formulario, cuándo hace falta consentimiento (y cómo debe ser), cómo modelar
el consentimiento y la retención en la base de datos, y qué trampas evitar.

## ¿Qué cubre?

- **Base de licitud** (art. 7): consentimiento vs. medidas precontractuales vs. interés legítimo.
- **Qué informar antes de recoger** (art. 12): los 17 puntos y el patrón aviso corto + política completa.
- **Consentimiento válido** (art. 8): libre, específico, informado, inequívoco y **revocable** — con el modelo de tabla `consents`.
- **Derechos ARCO+** (arts. 12–22): acceso, rectificación, eliminación, oposición, portabilidad, decisiones automatizadas.
- **Retención** (art. 12.4): plazos razonables **y** la purga que hay que implementar.
- **Seguridad desde el diseño** (arts. 38–42) y **brechas** (arts. 43, 46): notificar en 5 días.
- **Sanciones** reales, checklist de cierre y **trampas verificadas** (reCAPTCHA = transferencia internacional, el chatbot es tratamiento, el aviso solo en el footer no vale, etc.).
- El **texto completo de la ley** en [`references/`](./skills/lopdp-ecuador-datos-personales/references/) para citar el artículo exacto.

---

## Instalación

### Opción A — como plugin de Claude Code (recomendado)

```bash
/plugin marketplace add MarbustTechnologyCompany/LOPDPSkill
/plugin install lopdp-ecuador@marbust-lopdp
```

### Opción B — copiando la skill a mano

Clona el repo y copia la carpeta de la skill a tu directorio de skills de Claude Code:

```bash
git clone https://github.com/MarbustTechnologyCompany/LOPDPSkill.git
cp -r LOPDPSkill/skills/lopdp-ecuador-datos-personales ~/.claude/skills/
```

(En Windows: copia `skills\lopdp-ecuador-datos-personales` a `%USERPROFILE%\.claude\skills\`.)

## Cómo se usa

Con la skill instalada, Claude Code la invoca **automáticamente** cuando detecta que vas a crear o
modificar un formulario, una tabla que guarde datos de personas o una política de privacidad.
También puedes pedirla explícitamente:

> "Aplica la LOPDP a este formulario de contacto"
> "Revisa si este registro de usuarios cumple la ley de datos de Ecuador"

Aunque está empaquetada como skill de Claude Code, el contenido de
[`SKILL.md`](./skills/lopdp-ecuador-datos-personales/SKILL.md) es **agnóstico de herramienta**:
sirve como guía de referencia para cualquier desarrollador o asistente de IA.

---

## ⚖️ Descargo de responsabilidad

Esta skill es una **guía técnica para desarrolladores**, **no** asesoría jurídica. El texto de la
ley en `references/` es un documento público del Estado ecuatoriano, reproducido con fines
informativos. Para decisiones legales, casos concretos o dudas, consulta a un profesional del
derecho y a la **Superintendencia de Protección de Datos Personales del Ecuador**.

## Contribuir

Las contribuciones son bienvenidas: correcciones, nuevas trampas verificadas, ejemplos en otros
stacks (Laravel, Django, Rails, .NET), mejoras de redacción. Abre un *issue* o un *pull request*.
Si la Autoridad emite reglamentos o reformas, los PR que actualicen el contenido son muy valiosos.

## Licencia

[MIT](./LICENSE) — úsala, adáptala y compártela libremente.

## Créditos

Creada por **[Marco Antonio Bustillos Quiroz (@MarAntBQ)](https://marantbq.dev)** ·
**Marbust Technology Company**.
