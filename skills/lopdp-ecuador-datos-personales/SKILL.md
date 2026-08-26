---
name: lopdp-ecuador-datos-personales
description: Cumplir la Ley Orgánica de Protección de Datos Personales de Ecuador (LOPDP, R.O. 459 del 26-V-2021) en CUALQUIER desarrollo que recoja datos de personas — formularios de contacto/cotización, registro de usuarios, newsletter, chatbots que guardan conversaciones, analítica, CRM, apps móviles. Úsalo SIEMPRE que vayas a crear o modificar un formulario, una tabla que guarde datos de personas, o una política de privacidad, en cualquier proyecto o sitio en Ecuador. Cubre qué informar antes de recoger el dato (art. 12), cuándo hace falta consentimiento y cómo debe ser (arts. 7 y 8), los derechos ARCO+ y cómo atenderlos, retención, datos sensibles, brechas de seguridad y las sanciones reales.
license: MIT
---

# LOPDP Ecuador — cumplir al desarrollar

Ley Orgánica de Protección de Datos Personales, Quinto Suplemento del Registro Oficial 459, 26 de mayo de 2021. Texto completo en `references/ley-lopdp-registro-oficial-459-2021.txt` — **consúltalo cuando necesites la letra exacta de un artículo**, no cites de memoria.

Aplica a **cualquier proyecto en Ecuador**, propio o de un cliente: si el sistema recoge un nombre, un correo o un teléfono de una persona, esta ley aplica.

> **Descargo legal.** Esta skill es una guía técnica para desarrolladores, no asesoría jurídica. Para casos concretos, decisiones de negocio o dudas legales, consulta a un profesional del derecho y la fuente oficial: la **Superintendencia de Protección de Datos Personales del Ecuador** y el texto de la ley en `references/`.

---

## 0. Lo que NUNCA se hace

- **Recoger un dato sin decir para qué.** El art. 12 obliga a informar **antes** de recoger, no después.
- **Casilla de consentimiento premarcada.** El art. 8 exige consentimiento *inequívoco*: premarcada no lo es.
- **Un solo "acepto" para varias finalidades.** Si vas a usar el correo para responder Y para marketing, son dos consentimientos separados. El art. 8 lo dice literal: *"será preciso que conste que dicho consentimiento se otorga para todas ellas"*.
- **Guardar datos "por si acaso", sin plazo.** Sin política de retención no hay cumplimiento.
- **Pedir datos que no necesitas.** Principio de minimización: si el formulario no necesita la cédula, no la pidas.
- **Tratar datos sensibles sin base legal.** Salud, biometría, origen étnico, ideología, orientación sexual, datos de menores: prohibidos salvo las excepciones del art. 26, y con consentimiento **explícito**.

---

## 1. Antes de escribir el formulario: dos preguntas

### ¿Cuál es la base de licitud? (art. 7)

No todo tratamiento necesita consentimiento. Hay 8 bases; en desarrollo web casi siempre es una de estas tres:

| Base | Cuándo aplica | ¿Casilla? |
|---|---|---|
| **Consentimiento** (7.1) | Newsletter, marketing, cookies no esenciales, guardar el historial de un chatbot | Sí, explícita |
| **Medidas precontractuales** (7.5) | Formulario de **cotización** o de contacto comercial: el titular pide el contacto | No hace falta casilla para responderle, pero **sí hay que informar** |
| **Interés legítimo** (7.8) | Seguridad del sitio, antifraude, logs | No, pero debe poder oponerse |

**El error típico:** poner casilla obligatoria de consentimiento en un formulario de cotización. Si el visitante te escribe pidiendo precio, responderle es una medida precontractual — no necesitas su permiso para hacer lo que te está pidiendo. La casilla obligatoria de más puede invalidar el consentimiento por no ser *libre*.

Lo que **sí** necesita casilla aparte y opcional: usar ese correo para enviarle promociones después.

### ¿Qué datos necesito de verdad?

Recorta hasta lo mínimo. Cada campo extra es riesgo y obligación.

---

## 2. Lo que hay que informar (art. 12) — 17 puntos

El art. 12 lista 17 puntos. **No caben todos junto al formulario**; el patrón correcto es:

- **Junto al formulario**: un aviso corto con lo esencial (quién trata, para qué, base legal, derechos, enlace).
- **En la política completa**: los 17 puntos.

Los 17: fines; base legal; tipos de tratamiento; **tiempo de conservación**; existencia de la base de datos; origen de los datos si no vienen del titular; finalidades ulteriores; identidad y contacto del responsable (**domicilio legal, teléfono y correo**); delegado de protección de datos si aplica; transferencias nacionales o internacionales con destinatarios y garantías; consecuencias de entregar o negarse; efecto de dar datos erróneos; **posibilidad de revocar el consentimiento**; cómo ejercer acceso, eliminación, rectificación, actualización, oposición, anulación y limitación; cómo ejercer portabilidad; dónde reclamar ante el responsable **y ante la Autoridad**; existencia de decisiones automatizadas y perfilado.

> Si los datos se obtienen directamente del titular, la información debe darse **en el momento mismo de la recogida**.

### Aviso corto, listo para usar

```
Tus datos se tratan para atender tu solicitud. Responsable: {EMPRESA}
({correo}, {teléfono}). Base legal: medidas precontractuales a tu
petición. Se conservan {N} meses. Puedes acceder, rectificar, eliminar
u oponerte escribiendo a {correo}. Más información en la
{Política de Protección de Datos Personales}.
```

---

## 3. Consentimiento válido (art. 8)

Cuatro requisitos, los cuatro obligatorios:

1. **Libre** — sin condicionar el servicio a aceptar tratamientos que no hacen falta.
2. **Específico** — una finalidad concreta por consentimiento.
3. **Informado** — con la información del art. 12 disponible antes de aceptar.
4. **Inequívoco** — acción afirmativa clara. Casilla **sin** premarcar. Seguir navegando NO es consentir.

**Revocable en cualquier momento**, sin justificación, por un procedimiento **igual de sencillo** que el usado para recogerlo y **gratuito**. Si lo recogiste con un clic, debe poder revocarse con un clic — no con una carta notariada.

En código, esto significa que si guardas consentimiento, guardas también **cuándo, para qué y cómo** lo obtuviste:

```sql
CREATE TABLE consents (
  id           INT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
  subjectEmail VARCHAR(190) NOT NULL,
  purpose      VARCHAR(60)  NOT NULL,  -- 'marketing', 'chat_history'
  granted      TINYINT(1)   NOT NULL,
  policyVersion VARCHAR(20) NOT NULL,  -- qué texto aceptó
  ipAddress    VARCHAR(45)  NULL,
  createdAt    DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,
  revokedAt    DATETIME NULL,
  KEY idx_subject (subjectEmail, purpose)
);
```

Sin `policyVersion` no puedes demostrar **qué** aceptó la persona. Sin `revokedAt` no puedes demostrar que respetaste la revocación.

---

## 4. Derechos del titular (arts. 12 a 22)

Información, acceso, rectificación y actualización, eliminación, oposición, portabilidad, suspensión del tratamiento, y a no ser objeto de decisiones únicamente automatizadas.

**Qué implica en el desarrollo:**

- Un **canal de contacto real** publicado (correo basta para un sitio pequeño).
- Que los datos se puedan **localizar por titular** — de ahí el índice por email en las tablas.
- Que se puedan **exportar** en formato legible (portabilidad).
- Que se puedan **borrar de verdad**, incluidos respaldos y logs. Un borrado lógico que deja el dato visible no cumple.
- Si hay decisiones automatizadas o perfilado, **decirlo** y permitir intervención humana.

---

## 5. Retención — el punto que más se olvida

El art. 12.4 obliga a informar el **tiempo de conservación**. Eso implica definirlo y **cumplirlo**.

Criterios razonables para un sitio de servicios:

| Dato | Plazo sugerido | Motivo |
|---|---|---|
| Consulta de contacto no convertida | 12 meses | Seguimiento comercial |
| Solicitud de cotización | 24 meses | Puede reactivarse |
| Conversación de chatbot | 6 meses | Mejora del servicio |
| Cliente con contrato | Mientras dure + plazo legal tributario | Obligación legal (base 7.2) |

Implementa la purga, no solo la documentes. Un cron mensual:

```sql
DELETE FROM contact_messages WHERE createdAt < DATE_SUB(NOW(), INTERVAL 12 MONTH);
DELETE FROM quote_requests   WHERE createdAt < DATE_SUB(NOW(), INTERVAL 24 MONTH) AND status IN ('lost','new');
DELETE FROM chat_messages    WHERE createdAt < DATE_SUB(NOW(), INTERVAL 6 MONTH);
```

---

## 6. Seguridad y protección desde el diseño (arts. 38 a 42)

El art. 39 obliga a tener en cuenta la protección de datos **en las primeras fases de concepción y diseño**, no al final. En la práctica:

- **Cifrado en tránsito** — HTTPS obligatorio, sin excepción.
- **Credenciales fuera del repositorio y fuera del docroot**.
- **Consultas parametrizadas siempre** — una inyección SQL sobre una tabla de titulares es una vulneración notificable.
- **Mínimo privilegio** en el usuario de base de datos.
- **No registrar datos personales en logs** ni en mensajes de error.
- **Rate limiting** en formularios públicos.

---

## 7. Brechas de seguridad (arts. 43 y 46)

Si hay vulneración con riesgo para los derechos de las personas:

- **Notificar a la Autoridad de Protección de Datos en término de 5 días.** Pasado ese plazo, hay que justificar la demora.
- **Notificar a los titulares afectados** cuando el riesgo sea alto.
- El encargado debe notificar al responsable **cualquier** vulneración.

Para poder cumplirlo hace falta **detectarlo**: logs de acceso, alertas y un contacto responsable definido.

---

## 8. Lo que arriesga el responsable

Multas calculadas sobre el **volumen de negocio del ejercicio anterior**:

- Infracciones leves: **0,1 % a 0,7 %**
- Infracciones graves: **0,7 % a 1 %**

Es sobre facturación, no sobre utilidad. Para un negocio pequeño es dinero real. Cuando alguien diga que "eso no hace falta", este es el dato que lo cambia.

---

## 9. Checklist antes de dar por terminado un formulario

- [ ] Base de licitud identificada y **escrita** (art. 7).
- [ ] Aviso corto **junto al formulario**, visible antes de enviar (art. 12).
- [ ] Política de Protección de Datos completa publicada y enlazada, con los 17 puntos.
- [ ] Casilla de consentimiento **solo** donde hace falta, **sin premarcar**, y **separada** por finalidad (art. 8).
- [ ] Responsable identificado con **domicilio legal, teléfono y correo**.
- [ ] Canal para ejercer derechos, publicado y funcionando.
- [ ] Plazo de conservación definido **y** purga implementada.
- [ ] HTTPS, consultas parametrizadas, credenciales fuera del repo.
- [ ] Sin datos personales en logs.
- [ ] Si hay chatbot que guarda conversaciones: consentimiento y plazo propios.
- [ ] Si el sitio es bilingüe, aviso y política **en los dos idiomas**.

---

## 10. Trampas verificadas

**El aviso solo en el pie de página no vale.** El art. 12 exige informar *en el momento mismo de la recogida*. Tiene que estar junto al formulario.

**Traducir el aviso no basta si la política solo existe en un idioma.** Si el sitio es bilingüe, el enlace tiene que llevar a una política que la persona entienda.

**El chatbot es tratamiento de datos.** Si guardas la conversación —y normalmente conviene guardarla— estás tratando datos personales: la persona escribe su nombre, su teléfono o su problema. Necesita su propio aviso y su propio plazo.

**reCAPTCHA transfiere datos a Google.** Es una transferencia internacional (art. 12.10): debe constar en la política, nombrando a Google como destinatario.

**Analítica y píxeles publicitarios necesitan consentimiento**, no solo aviso — no son cookies esenciales.

**Un correo de aviso a la empresa también es tratamiento.** El formulario que reenvía a `info@` está comunicando datos: la política debe decir quién los recibe.

---

## Fuente y créditos

- **Fuente legal:** Ley Orgánica de Protección de Datos Personales del Ecuador, R.O. 459 (26-V-2021). Texto en `references/`. Autoridad de control: Superintendencia de Protección de Datos Personales.
- **Autor:** Marco Antonio Bustillos Quiroz ([@MarAntBQ](https://marantbq.dev)) · Marbust Technology Company.
- **Licencia:** MIT. Úsala, adáptala y compártela libremente. Contribuciones bienvenidas.
