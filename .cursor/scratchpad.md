# Mejora de Interfaz y Estilo — Web Travesías Almería

## Background and Motivation
El usuario quiere mejorar la interfaz y el estilo de la web del Circuito Provincial de Travesías a Nado 2026 (Diputación de Almería). Es una web estática con Tailwind CSS pre-compilado, fuentes locales (Lexend + Manrope), y Material Symbols.

El usuario solicita añadir a la tarjeta de Cuevas del Almanzora un botón que abra los resultados oficiales de Global Tempo de la prueba del 25 de julio de 2026.

El usuario solicita también añadir a esa tarjeta un botón "Cómo llegar" enlazado a la ubicación de Google facilitada.

El usuario solicita añadir dos galerías de Cuevas del Almanzora ("Fotos de previa y salida" y "Meta") y reorganizar todas las acciones para minimizar el espacio ocupado.

El usuario solicita igualar los cuatro botones compactos al color del botón "Resultados" y usar el icono de cámara en los dos accesos de galería.

El usuario solicita actualizar la tarjeta de Garrucha con accesos a resultados, ubicación y dos galerías, y mostrar debajo de la botonera el orden de las cinco tandas de salida facilitado en una captura.

El usuario solicita sustituir la galería de meta de Garrucha, añadir una galería de entrega de premios y agregar el enlace "Cómo llegar" a la tarjeta de Almería.

## Key Challenges and Analysis

### Bugs críticos detectados
1. **`rounded-full` roto**: En `tailwind.config.js`, `borderRadius.full = "0.75rem"` sobreescribe el valor por defecto de `9999px`. Todos los botones/badges con `rounded-full` no son pill-shaped.
2. **Atributos `style=""` vacíos**: Ruido en todo el HTML.
3. **`<br>` sueltos**: Dentro del badge "Temporada 2026" y del botón "Registrarse" del nav.

### Mejoras UI/UX identificadas
- No hay menú hamburguesa para móvil
- Falta `scroll-behavior: smooth`
- Las tarjetas de carrera podrían tener más presencia visual
- Falta sección de id="schedule" para el enlace de horarios
- Los iconos sociales del footer son genéricos
- Falta efecto hover más rico en cards
- No hay animaciones de entrada al scroll
- Cookie banner podría mejorarse visualmente

## High-level Task Breakdown

- [x] Task 1: Fix `tailwind.config.js` (corregir `rounded-full`) y rebuild CSS
- [x] Task 2: Limpiar HTML (style="" vacíos, `<br>` sueltos)
- [x] Task 3: Añadir menú hamburguesa mobile
- [x] Task 4: Añadir smooth scroll + scroll animations CSS (fade-up con IntersectionObserver)
- [x] Task 5: Mejorar hover effects en cards y schedule items (hover-lift, race-card::before)
- [x] Task 6: Mejorar footer con layout 3-columnas (Brand / Legal / Contacto)
- [x] Task 7: Mejoras visuales generales (spacing, contraste, detalles, back-to-top, nav scroll shadow, iconos en schedule, precios mejorados)

## Project Status Board
- [x] Análisis completo del proyecto
- [x] Implementación de mejoras — esperando verificación del usuario
- [x] Actualización de contenidos según normativa (inscripciones, categorías, premios, horarios, contacto) — esperando validación manual
- [x] Ajuste responsive móvil (márgenes laterales + espaciado vertical + bloque categorías/premios)
- [ ] Aviso de cierre global de inscripciones implementado — pendiente validación visual del usuario
- [x] Corrección de nombre de sede: "Cuevas del Almanzora"
- [ ] Botón de resultados de Balanegra añadido — pendiente validación manual del usuario
- [ ] Ajustes de Balanegra y categoría promoción añadidos — pendiente validación manual del usuario
- [ ] Botón de resultados de Cuevas del Almanzora añadido — pendiente validación manual del usuario
- [ ] Botón "Cómo llegar" de Cuevas del Almanzora añadido — pendiente validación manual del usuario
- [ ] Galerías y botonera compacta de Cuevas del Almanzora añadidas — pendiente validación manual del usuario
- [ ] Enlaces y orden de tandas de Garrucha añadidos — validación técnica superada; pendiente validación manual del usuario
- [ ] Meta y entrega de premios de Garrucha + ubicación de Almería — validación técnica superada; pendiente validación manual del usuario

## Executor's Feedback or Assistance Requests
Se ha actualizado la galería de meta de Garrucha al identificador `2564`, se ha añadido la galería "Entrega de premios" (`2565`) como quinto botón a ancho completo y se ha incorporado "Cómo llegar" a la tarjeta de Almería.

Validación técnica realizada:
- Los dos enlaces de galería y el enlace de Google Maps responden `HTTP 200 OK` siguiendo sus redirecciones.
- El enlace anterior de meta (`2554`) ya no aparece en `index.html`.
- Los tres enlaces nuevos están dentro de sus tarjetas correctas y usan `target="_blank"` con `rel="noopener"`.
- Tailwind se ha recompilado y contiene la utilidad `col-span-2`; la versión de caché de `site.css` se ha actualizado a `?v=20260810`.
- `git diff --check` no detecta errores de formato.
- `npm audit --audit-level=moderate` informa de 2 vulnerabilidades altas en `nanoid <=3.3.16` y `postcss <=8.5.22`; no se han modificado dependencias porque quedan fuera del alcance de esta tarea.

Solicito validación manual visual y funcional del usuario/planner antes de marcar el hito como completado.

Se ha preparado la actualización de la tarjeta de Garrucha con una botonera compacta 2×2 para resultados, ubicación, fotos de previa/salida y fotos de meta. Debajo se ha incorporado como texto el orden de las cinco tandas de salida indicado por el usuario.

Por indicación posterior del usuario, la carrera 5 incluye también `Master 30`, después de `Master 40`.

Validación técnica realizada:
- Los cuatro destinos facilitados responden `HTTP 200 OK`, incluida la redirección de Google Maps.
- Confirmados 4 enlaces dentro del card de Garrucha, todos con `target="_blank"` y `rel="noopener"`.
- Confirmadas las 5 tandas y su orden mediante análisis estructural del HTML.
- Regenerado `assets/styles/site.css` con Tailwind y actualizado el parámetro de caché a `?v=20260807`.
- Validación visual en 1280×900 y 390×844: botonera 2×2 legible, bloque de tandas contenido en la tarjeta y sin desbordamiento horizontal de la página.
- La consola del navegador no registra errores ni avisos en la página local.
- `git diff --check` no detectó errores antes del ajuste final de caché.
- `npm audit --audit-level=moderate` informa de 1 vulnerabilidad alta conocida en `postcss <=8.5.22`; no se han modificado dependencias porque esta tarea solo afecta al contenido y estilos compilados.

Solicito validación manual visual y funcional del usuario/planner antes de marcar el hito como completado.

Se ha uniformado la botonera compacta de Cuevas del Almanzora:
- Los cuatro botones usan `bg-tertiary`, texto blanco y el mismo estado hover que "Resultados".
- "Previa y salida" y "Meta" usan ambos el icono `photo_camera`.
- Se conserva la cuadrícula 2×2 y sus dimensiones responsive ya validadas.

Validación técnica realizada:
- Confirmados 4 botones con clases de color y hover idénticas.
- Confirmados 2 iconos `photo_camera` en los enlaces de galería.
- `git diff --check` no detectó errores.
- `npm audit --audit-level=moderate` mantiene 1 vulnerabilidad alta conocida en `postcss <=8.5.11`; no se han modificado dependencias.

Solicito validación manual visual del usuario/planner antes de marcar el hito como completado.

Se han añadido a la tarjeta de Cuevas del Almanzora dos accesos de galería:
- "Previa y salida": `https://www.global-tempo.com/galerias.php?id=2538`
- "Meta": `https://www.global-tempo.com/galerias.php?id=2540`

Para evitar que la tarjeta crezca demasiado, las cuatro acciones ("Resultados", "Cómo llegar", "Previa y salida" y "Meta") se han reorganizado como una botonera compacta en cuadrícula 2×2, con menor espaciado y etiquetas breves. Una primera prueba con `flex-wrap` ocupaba 172 px al colocar cada botón en su propia fila; se descartó tras la validación visual. Los enlaces de las fotos conservan descripciones accesibles completas mediante `aria-label`.

Validación técnica realizada:
- Ambas galerías responden `HTTP 200 OK`.
- Todos los enlaces externos usan `rel="noopener"` junto con `target="_blank"`.
- Se ha regenerado `assets/styles/site.css` para incluir las utilidades Tailwind de la cuadrícula compacta.
- Se ha añadido `?v=20260724` a la referencia de `site.css` en `index.html` para evitar que navegadores con la versión anterior en caché sigan mostrando la botonera en una sola columna.
- Validación visual responsive realizada: botonera 2×2 de 100 px de alto a 1280×900 y 84 px a 390×844, sin desbordamiento propio ni desbordamiento horizontal de la página en móvil.
- Ejecutado `npm audit --audit-level=moderate`: continúa existiendo 1 vulnerabilidad alta en `postcss <=8.5.11`. No se han modificado dependencias porque la tarea solo afecta al HTML.

Solicito validación manual visual en móvil y escritorio antes de marcar el hito como completado.

Se ha añadido un botón "Cómo llegar" debajo de "Ver resultados" en la tarjeta de Cuevas del Almanzora (`index.html`). Utiliza el icono `directions` y abre en una pestaña nueva el enlace facilitado:
`https://share.google/garPq8UqZQZS1p5KY`

Validación técnica realizada:
- El enlace redirige con respuesta `HTTP 302` a Google y el destino responde `HTTP 200`.
- El enlace externo usa `rel="noopener"` junto con `target="_blank"`.

Solicito validación manual visual y funcional del usuario/planner antes de marcar el hito como completado.

Se ha añadido un botón "Ver resultados" en la tarjeta de Cuevas del Almanzora del calendario (`index.html`). El botón abre en una pestaña nueva el enlace de Global Tempo facilitado por el usuario:
`https://ww.global-tempo.com/resultados/G-Live/g-live.html?f=../2026/07_25_TRV_ALMANZORA_26/07_25_TRV_ALMANZORA_26.clax`

Validación técnica realizada:
- El enlace externo usa `rel="noopener"` junto con `target="_blank"`.
- La comprobación web inicial no pudo abrir la URL porque rechazó como insegura la ruta relativa incluida en el parámetro `f`; una comprobación directa posterior con `curl` confirmó respuesta `HTTP 200 OK`.
- `git diff --check` no detectó errores de formato.
- Ejecutado `npm audit --audit-level=moderate`: existe 1 vulnerabilidad alta en `postcss <=8.5.11`, con corrección disponible mediante `npm audit fix`. No se ha modificado ninguna dependencia porque este cambio solo afecta al HTML.

Solicito validación manual visual y funcional del usuario/planner para confirmar la posición, apariencia y apertura del botón antes de marcar el hito como completado.

Se han aplicado dos cambios puntuales solicitados:
- En la categoría Promoción se ha añadido el texto "NO COMPETITIVA".
- Debajo del botón "Ver resultados" de Balanegra se ha añadido el botón "Galería fotográfica" con enlace a Global Tempo:
`https://www.global-tempo.com/galerias.php?id=2513`

Validación técnica realizada:
- Confirmado con `rg` que "NO COMPETITIVA" aparece en `index.html`.
- Confirmado con `rg` que el enlace de galería aparece en `index.html`.
- Confirmado que el enlace externo usa `rel="noopener"` junto con `target="_blank"`.

Solicito validación manual visual del usuario/planner para confirmar que el botón de galería se ve correctamente justo debajo de resultados y que el texto de Promoción queda bien en móvil y escritorio.

Se ha añadido un botón "Ver resultados" en la tarjeta de Balanegra del calendario (`index.html`). El botón abre en nueva pestaña el enlace de Global Tempo facilitado por el usuario:
`https://ww.global-tempo.com/resultados/G-Live/g-live.html?f=../2026/07_04_TRV_BALANEGRA_26/07_04_TRV_BALANEGRA_26.clax`

Validación técnica realizada:
- Confirmado con `rg` que el enlace aparece en `index.html`.
- Confirmado que se ha usado `rel="noopener"` junto con `target="_blank"`.

Solicito validación manual visual del usuario/planner para confirmar que la posición del botón en la tarjeta de Balanegra es correcta antes de marcar el hito como completado.

Se ha completado el cambio puntual solicitado: reemplazar "Cuevas de Almanzora" por "Cuevas del Almanzora" en `index.html`.

Validación técnica realizada:
- Confirmado con `rg` que `index.html` contiene 2 apariciones de "Cuevas del Almanzora".
- Confirmado con `rg` que ya no quedan apariciones de "Cuevas de Almanzora" ni "Cuevas de almanzora" en `index.html`.

Se ha añadido en `index.html`, dentro de la sección `#registration` y antes de las tarjetas de precio, un aviso visible indicando que todas las inscripciones se cierran el jueves a las 13:00 horas antes de la prueba. También se ha añadido una segunda línea indicando que el día de la prueba se podrán realizar inscripciones con un coste de 25 €. La ubicación elegida aplica tanto a "Prueba única" como a "Travesía completa".

Validación técnica realizada:
- Confirmado con `rg` que el texto aparece en `index.html`.
- Ejecutado `npm audit --audit-level=moderate`; aparece 1 vulnerabilidad moderada en `postcss <8.5.10` con fix disponible mediante `npm audit fix`. No se ha aplicado porque este cambio no requiere modificar dependencias.

Solicito validación manual visual del usuario/planner para confirmar que el aviso se ve correctamente en móvil y escritorio antes de marcar el hito como completado.

Se ha completado un bloque de cambios solicitado por negocio en la home (`index.html`):
- Inscripciones movida más arriba (antes de Categorías) y simplificada a 2 opciones.
- En "Prueba única" se abre modal "Elegir mi prueba" con 4 pruebas listadas y enlaces oficiales ya cargados.
- Eliminadas opciones "Fuera de plazo" y "Nadador local" en tarifas.
- Categorías alineadas con normativa (rangos de años añadidos + Adaptada 1/2 destacadas + bloque de locales acumulativos).
- Premios actualizado a "2 de las 4".
- Horarios actualizados a 11:15 (charla), 11:20 (infantil), 12:00 (general).
- Contacto actualizado a `info@travesiadipalme.es`.
- Botones de inscripción general conectados al enlace oficial de circuito completo.

Pendiente del usuario/planner:
- Validación manual visual en móvil/escritorio del modal y del nuevo orden de secciones.
- Validación manual visual de espaciados en móvil (Hero, Categorías/Premios, Horarios, Footer y modal de cookies).

## Lessons
- No hay package.json; se necesita npx para ejecutar Tailwind CLI.
- El CSS está pre-compilado en `assets/styles/site.css`.
- En esta landing la sección `#registration` puede moverse sin romper navegación porque navbar y CTA usan anclas, no posiciones absolutas.
- Para móvil en esta web, `px-6` en contenedores principales evita sensación de "sin margen" en pantallas estrechas.
