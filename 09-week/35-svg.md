---
theme: ../theme
transition: none
layout: cover
title: SVG
exportFilename: 35-svg
---

# SVG

✏️ 2026-01 ➖ ⏱️ 20 min.

---
layout: cover
---

# Vector vs Raster

---
layout: default-y-center
---

## Dos Tipos de Imágenes

::contents::
**Raster (PNG, JPG, WebP):** cuadrícula de píxeles. Se pixela al escalar.

**Vector (SVG):** fórmulas matemáticas. Se ve perfecto a cualquier tamaño.

**SVG es ideal para:**
- Logos e iconos — necesitan verse bien en cualquier tamaño y resolución
- Ilustraciones con formas geométricas
- Gráficas e infografías interactivas

**PNG/JPG es mejor para:**
- Fotografías y imágenes complejas con muchos colores y gradientes
- Contenido generado por usuarios (fotos de perfil, capturas de pantalla)

**Regla práctica:** si lo creaste en Figma o Illustrator con formas → SVG. Si es una foto → JPG/WebP.

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Anatomía de un SVG

---
layout: default-y-center
---

## La Estructura Básica

::contents::
SVG (Scalable Vector Graphics) es XML. Se puede escribir a mano, editar como código y poner directo en HTML.

```html
<svg
  xmlns="http://www.w3.org/2000/svg"
  viewBox="0 0 24 24"
  width="24"
  height="24"
>
  <!-- Círculo -->
  <circle cx="12" cy="12" r="10" fill="blue" />

  <!-- Rectángulo con esquinas redondeadas -->
  <rect x="2" y="2" width="20" height="20" rx="4" fill="none" stroke="red" />

  <!-- Path — forma arbitraria (triángulo) -->
  <path d="M12 2 L22 20 L2 20 Z" fill="orange" />

  <!-- Texto -->
  <text x="12" y="16" text-anchor="middle" font-size="12">Hola</text>
</svg>
```

`viewBox="0 0 24 24"` define el sistema de coordenadas interno — independiente del tamaño real del SVG en pantalla.

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# SVG en la Web

---
layout: default-y-center
---

## Tres Formas de Usar SVG

::contents::
```html
<!-- 1. Como <img> — simple, no se puede estilizar con CSS -->
<img src="/logo.svg" alt="Logo de la empresa" width="120" />

<!-- 2. Como background CSS — decorativo, no accesible -->
<div style="background-image: url('/patron.svg')"></div>

<!-- 3. Inline — directo en el HTML (recomendado para íconos) -->
<svg viewBox="0 0 24 24" aria-hidden="true">
  <path d="M12 2..." />
</svg>
```

**Inline SVG es el más poderoso:**
- Se puede estilizar con CSS (`fill`, `stroke`, `color`)
- Responde a `:hover`, `:focus`, media queries
- Se puede animar con CSS o JS
- No hace una petición HTTP adicional

```css
/* Estilizar SVG inline */
.icono { width: 24px; height: 24px; }
.icono:hover path { fill: var(--color-accion); }
```

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## currentColor — SVG que Hereda el Color del Texto

::contents::
`currentColor` hace que el SVG tome el color `color` del elemento padre — fundamental para íconos en botones y links.

```css
/* ❌ Sin currentColor — hardcodear para cada contexto */
.boton-primario svg path { fill: white; }
.boton-secundario svg path { fill: #333; }
.boton-peligro svg path { fill: red; }
```

```css
/* ✅ Con currentColor — el ícono hereda automáticamente */
svg { fill: currentColor; }

.boton-primario   { color: white; }
.boton-secundario { color: #333; }
.boton-peligro    { color: red; }
/* los tres botones tienen el ícono del color correcto sin CSS extra */
```

```html
<!-- En React — patrón estándar para componentes de ícono -->
<svg viewBox="0 0 24 24" fill="currentColor" aria-hidden="true">
  <path d="..." />
</svg>
```

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Resumen — SVG

::contents::
✅ SVG es vectorial — se ve perfecto a cualquier tamaño y en pantallas de alta resolución

✅ Úsalo para logos, íconos e ilustraciones — PNG/WebP para fotografías

✅ Prefiere **SVG inline** para íconos — permite estilizar con CSS y no hace petición HTTP adicional

✅ Usa `fill="currentColor"` para que el ícono herede el color del elemento padre

✅ `viewBox` define el sistema de coordenadas interno — siempre inclúyelo

✅ `aria-hidden="true"` en íconos decorativos — el lector de pantalla los ignora

❌ No uses `<img src="icono.svg">` para íconos que deben cambiar de color — no se pueden estilizar con CSS

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# 🎉
