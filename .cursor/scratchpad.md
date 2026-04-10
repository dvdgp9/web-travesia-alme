# Mejora de Interfaz y Estilo — Web Travesías Almería

## Background and Motivation
El usuario quiere mejorar la interfaz y el estilo de la web del Circuito Provincial de Travesías a Nado 2026 (Diputación de Almería). Es una web estática con Tailwind CSS pre-compilado, fuentes locales (Lexend + Manrope), y Material Symbols.

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

## Executor's Feedback or Assistance Requests
Ninguno por ahora.

## Lessons
- No hay package.json; se necesita npx para ejecutar Tailwind CLI.
- El CSS está pre-compilado en `assets/styles/site.css`.
