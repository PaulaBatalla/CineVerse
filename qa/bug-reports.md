# Bug Reports — CineVerse

Defectos detectados durante la Ronda 1 de testing (revisión de código + exploratoria), previos a la Ronda 2 documentada en `test-cases.md`. Todos fueron corregidos antes de dar por aprobado el sitio para portfolio.

---

### BUG-01 — Ordenamiento por defecto del catálogo falla silenciosamente

**Severidad:** Media
**Módulo:** Catálogo
**Estado:** Resuelto

**Pasos para reproducir:**
1. Ingresar a `catalogo.html` sin tener ninguna preferencia de orden guardada previamente en `localStorage` (por ejemplo, en una ventana de incógnito).
2. Observar el orden inicial de las cards.

**Resultado esperado:** Las cards se ordenan por título ascendente por defecto.

**Resultado obtenido:** El ordenamiento por defecto intentaba usar el campo `sortBy: "title"`, pero el dataset de cada card usa el atributo `data-titulo` (en español). Al no coincidir el nombre del campo, la comparación no ordenaba correctamente y el catálogo quedaba en el orden de inserción original sin que ningún botón de orden apareciera activo.

**Causa raíz:** Inconsistencia entre el nombre de campo en inglés (`title`) usado como valor por defecto en `init()`, y el nombre real del data-attribute (`titulo`) usado en el resto del código.

**Resolución:** Se corrigió el valor por defecto a `sortBy: "titulo"` en `catalogo.js`.

---

### BUG-02 — Reconstrucción innecesaria del DOM al generar estrenos

**Severidad:** Baja
**Módulo:** Estrenos
**Estado:** Resuelto

**Pasos para reproducir:**
1. Revisar el código de `generarEstrenos()` en `estrenos.js`.
2. Observar el uso de `contenedor.innerHTML += estrenoHTML` dentro de un loop `for`.

**Resultado esperado:** El contenedor se llena con los 5 estrenos en una sola operación de escritura al DOM.

**Resultado obtenido:** Cada iteración del loop leía y reescribía el `innerHTML` completo del contenedor, reconstruyendo todos los nodos ya insertados en cada vuelta. No producía un error visible con 5 elementos, pero es un antipatrón que degrada performance de forma proporcional a la cantidad de ítems y puede generar pérdida de listeners en escenarios más complejos.

**Causa raíz:** Uso de concatenación (`+=`) sobre `innerHTML` en vez de acumular el HTML en una variable/array y asignarlo una sola vez al final.

**Resolución:** Se refactorizó para construir un array de strings HTML con `.map()` y asignarlo al contenedor con `.join('')` en una sola operación.

---

### BUG-03 — Inconsistencia de patrón: `onclick` inline en vez de `addEventListener`

**Severidad:** Baja (deuda técnica / consistencia de código)
**Módulo:** Estrenos
**Estado:** Resuelto

**Pasos para reproducir:**
1. Comparar el manejo de eventos en `estrenos.js` (`onclick="toggleEstreno(${i})"` en el HTML generado) contra el resto del proyecto (`catalogo.js`, `merchandising.js`, `main.js`), que usa `addEventListener`.

**Resultado esperado:** Manejo de eventos consistente en todo el proyecto.

**Resultado obtenido:** `estrenos.js` era la única página que mezclaba JS con HTML mediante atributos `onclick`, rompiendo la separación de responsabilidades que el resto del código respeta.

**Resolución:** Se cambió el elemento `.estreno-toggle` de `<div>` a `<button>` con `data-index`, y se agregó `addEventListener` en una función `configurarEventosEstrenos()`. Se ajustó `estrenos.css` para resetear los estilos nativos del `<button>`.

---

### BUG-04 — Formulario de contacto sin funcionalidad

**Severidad:** Alta
**Módulo:** Home
**Estado:** Resuelto

**Pasos para reproducir:**
1. Ingresar a `index.html`.
2. Completar el formulario de contacto (nombre, email, mensaje).
3. Click en "Enviar".

**Resultado esperado:** Alguna confirmación visual de que el mensaje fue "enviado" (aunque sea simulado, al no haber backend), y limpieza del formulario.

**Resultado obtenido:** El formulario no tenía ningún listener asociado al evento `submit` en `main.js`. Al enviar, no pasaba nada visible para el usuario — ni confirmación ni error — dando la impresión de que el sitio no respondía.

**Causa raíz:** Falta de implementación; el HTML del formulario existía pero no estaba conectado a lógica en JavaScript.

**Resolución:** Se agregó `configurarFormularioContacto()` en `main.js`, con `preventDefault()`, validación de campos vacíos y un mensaje de confirmación simulado que limpia el formulario al finalizar.

---

### BUG-05 — Dependencia de un kit personal de Font Awesome

**Severidad:** Media (riesgo de disponibilidad, no funcional en el momento del testing)
**Módulo:** General (los 4 HTML)
**Estado:** Resuelto

**Pasos para reproducir:**
1. Revisar el `<script>` de Font Awesome en los 4 archivos HTML: `kit.fontawesome.com/a2e0d3c2c7.js`.

**Resultado esperado:** Los íconos (redes sociales en el footer, carrito) cargan de forma independiente de cuentas de terceros.

**Resultado obtenido:** El sitio dependía de un kit vinculado a una cuenta personal de Font Awesome. Si esa cuenta se desactiva o el kit se elimina, los íconos dejan de renderizar en todo el sitio sin aviso.

**Resolución:** Se reemplazó el script del kit por el CDN público de Font Awesome (`cdnjs.cloudflare.com`), moviendo el `<link>` de estilos al `<head>` de cada página (estaba antes ubicado al final del `<body>`, posición incorrecta para una hoja de estilos).

---

### BUG-06 — Inputs y selects sin `<label>` asociado

**Severidad:** Baja (accesibilidad)
**Módulo:** Home, Catálogo
**Estado:** Resuelto

**Pasos para reproducir:**
1. Inspeccionar los inputs de búsqueda (home, catálogo, header) y el select de género en `catalogo.html`.

**Resultado esperado:** Cada control de formulario tiene un `<label>` asociado (aunque sea oculto visualmente), para ser identificable por lectores de pantalla y cumplir con buenas prácticas de accesibilidad.

**Resultado obtenido:** Los inputs solo tenían `placeholder`, que no reemplaza a un `<label>` (desaparece al escribir y no todos los lectores de pantalla lo anuncian de forma confiable).

**Resolución:** Se agregaron `<label>` con clase `.sr-only` (oculta visualmente, accesible para lectores de pantalla) para: nombre, email y mensaje del formulario de contacto; buscador del catálogo; select de género; buscador del header.

---

## Resumen

| ID | Severidad | Estado |
|---|---|---|
| BUG-01 | Media | Resuelto |
| BUG-02 | Baja | Resuelto |
| BUG-03 | Baja | Resuelto |
| BUG-04 | Alta | Resuelto |
| BUG-05 | Media | Resuelto |
| BUG-06 | Baja | Resuelto |

**Defectos abiertos:** 0. Cumple el criterio de aceptación definido en `test-plan.md`.
