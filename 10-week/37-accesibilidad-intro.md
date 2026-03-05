---
theme: ../theme
transition: none
layout: cover
title: Accesibilidad Web
exportFilename: 37-accesibilidad-intro
---

# Accesibilidad Web
## Introducción

✏️ 2026-01 ➖ ⏱️ 25 min.

---
layout: cover
---

# ¿Qué es la Accesibilidad?

---
layout: default-y-center
---

## Accesibilidad Web (a11y)

::contents::
La accesibilidad web significa que los sitios y aplicaciones web pueden ser **usados por todas las personas**, incluyendo aquellas con discapacidades.

**Tipos de discapacidades que afectan el uso de la web:**
- **Visual:** ceguera, baja visión, daltonismo
- **Motora:** dificultad para usar el teclado o mouse, temblores
- **Auditiva:** sordera, baja audición (afecta videos sin subtítulos)
- **Cognitiva:** dislexia, TDAH, autismo, deterioro cognitivo

**"a11y"** = abreviatura de "accessibility" (11 letras entre la a y la y)

El objetivo no es solo cumplir reglas — es construir productos que funcionen para todos.

::header::
Semana 10: Accesibilidad

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## ¿Por Qué Importa?

::contents::
**Estadísticas:**
- ~15% de la población mundial tiene alguna discapacidad (OMS)
- ~8% de los hombres tienen daltonismo
- Millones usan tecnologías de asistencia (lectores de pantalla, teclados especiales)

**Razones para implementar accesibilidad:**

✅ **Ética:** todos merecen acceso a la información y los servicios

✅ **Legal:** muchos países exigen accesibilidad (Ley ADA en EE.UU., directivas de la UE)

✅ **SEO:** el HTML semántico mejora el posicionamiento en buscadores

✅ **Usabilidad:** lo que beneficia a personas con discapacidades beneficia a todos (subtítulos, buen contraste, teclado funcional)

::header::
Semana 10: Accesibilidad

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# WCAG

---
layout: default-y-center
---

## Web Content Accessibility Guidelines

::contents::
**WCAG** es el estándar internacional de accesibilidad web, publicado por el W3C.

**Versiones:** WCAG 2.1 (vigente) y WCAG 2.2 (2023)

**Los 4 principios (POUR):**

| Principio | Significado |
|---|---|
| **P**erceptible | La información debe ser presentable para todos los sentidos |
| **O**perable | La interfaz debe poder navegarse de distintas formas |
| **U**nderstandable | La información y operación deben ser comprensibles |
| **R**obust | El contenido debe interpretarse por tecnologías asistivas |

::header::
Semana 10: Accesibilidad

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Niveles de Conformidad

::contents::
**Nivel A** — Mínimo obligatorio. Sin esto, el contenido es inutilizable para algunos.
- Ejemplos: imágenes con alt text, videos con transcripción, sin contenido que cause convulsiones

**Nivel AA** — Estándar recomendado (requerido legalmente en muchos países).
- Ejemplos: contraste mínimo 4.5:1, navegación por teclado, etiquetas en formularios

**Nivel AAA** — Óptimo. Difícil de cumplir en todo el sitio.
- Ejemplos: contraste 7:1, lenguaje de señas en videos, 3 formas de navegación

**En la práctica:** apunta a **Nivel AA**. Es el estándar razonable para proyectos profesionales.

::header::
Semana 10: Accesibilidad

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# HTML Semántico

---
layout: default-y-center
---

## Usar los Elementos Correctos

::contents::
El HTML semántico es la base de la accesibilidad. Los lectores de pantalla usan la estructura del HTML para interpretar la página.

```html
<!-- ❌ Sin semántica — un lector de pantalla no entiende la estructura -->
<div class="header">
  <div class="nav">
    <div class="link">Inicio</div>
  </div>
</div>
<div class="main-content">
  <div class="title">Bienvenido</div>
  <div class="text">Contenido aquí</div>
</div>

<!-- ✅ Con semántica — estructura clara y navegable -->
<header>
  <nav>
    <a href="/">Inicio</a>
  </nav>
</header>
<main>
  <h1>Bienvenido</h1>
  <p>Contenido aquí</p>
</main>
```

::header::
Semana 10: Accesibilidad

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Elementos Semánticos Clave

::contents::
```html
<!-- Estructura de página -->
<header>   — encabezado del sitio o sección
<nav>      — bloque de navegación
<main>     — contenido principal (solo uno por página)
<aside>    — contenido relacionado/sidebar
<footer>   — pie del sitio o sección
<section>  — sección temática (con h2/h3 propio)
<article>  — contenido independiente (un post, una tarjeta)

<!-- Contenido -->
<h1>–<h6>  — jerarquía de títulos (no saltar niveles)
<p>        — párrafos
<ul>, <ol>, <li> — listas
<button>   — acción interactiva (no <div>!)
<a href>   — navegación/enlace (no <div>!)
<label>    — etiqueta de formulario
<figure> + <figcaption> — imágenes con descripción
```

::header::
Semana 10: Accesibilidad

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Alt Text en Imágenes

::contents::
```html
<!-- ✅ Imagen informativa — describe el contenido -->
<img src="grafico-ventas.png" alt="Gráfico de barras mostrando ventas de enero a marzo 2025">

<!-- ✅ Imagen decorativa — alt vacío (el lector la ignora) -->
<img src="patron-decorativo.png" alt="">

<!-- ❌ Sin alt — el lector lee la ruta del archivo -->
<img src="grafico-ventas.png">

<!-- ❌ Alt genérico — no aporta información -->
<img src="grafico-ventas.png" alt="imagen">
<img src="logo.png" alt="logo">

<!-- ✅ Logo con enlace — describe la acción -->
<a href="/">
  <img src="logo.png" alt="Volver a la página de inicio">
</a>
```

::header::
Semana 10: Accesibilidad

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Herramientas de Testing

---
layout: default-y-center
---

## Cómo Probar la Accesibilidad

::contents::
**Herramientas automáticas (detectan ~30-40% de los problemas):**
- **Lighthouse** — integrado en Chrome DevTools (F12 → Lighthouse → Accessibility)
- **axe DevTools** — extensión de Chrome con análisis detallado
- **WAVE** — extensión visual que resalta problemas in situ

**Prueba manual imprescindible:**
- Navega toda la página **solo con el teclado** (Tab, Shift+Tab, Enter, Espacio, flechas)
- Verifica que todos los elementos interactivos tienen un **indicador de foco visible**
- Prueba con zoom al 200% — ¿sigue siendo usable?

**Lectores de pantalla gratuitos:**
- **NVDA** (Windows, gratis) — el más usado
- **VoiceOver** (macOS/iOS, incluido)
- **TalkBack** (Android, incluido)

::header::
Semana 10: Accesibilidad

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Resumen — Fundamentos de A11y

::contents::
✅ Accesibilidad beneficia al **15% de la población** y mejora la experiencia de todos

✅ Apunta a **WCAG 2.1 Nivel AA** — el estándar profesional

✅ Usa **HTML semántico**: `<header>`, `<nav>`, `<main>`, `<button>`, `<h1>`–`<h6>`

✅ Pon **alt text descriptivo** en imágenes informativas; `alt=""` en decorativas

✅ Prueba con **Lighthouse** y con navegación por **teclado**

❌ No uses `<div>` y `<span>` para todo — los elementos semánticos tienen comportamiento de accesibilidad incorporado

❌ No saltes niveles de heading (`<h1>` → `<h3>` directo)

::header::
Semana 10: Accesibilidad

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# 🎉
