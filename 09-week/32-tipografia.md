---
theme: ../theme
transition: none
layout: cover
title: Tipografía para Web
exportFilename: 32-tipografia
---

# Tipografía para Web

✏️ 2026-01 ➖ ⏱️ 25 min.

---
layout: cover
---

# Conceptos Básicos

---
layout: default-y-center
---

## Typeface vs Font

::contents::
- **Typeface** (familia tipográfica): el diseño completo de un conjunto de letras. Ej: *Inter*, *Georgia*, *Roboto*
- **Font** (fuente): una variante específica dentro de esa familia. Ej: *Inter Bold 700*, *Inter Light 300*

**Categorías principales:**
- **Serif** — remates decorativos en las letras (Georgia, Times New Roman). Clásica, lectura larga en papel.
- **Sans-serif** — sin remates (Inter, Roboto, System UI). Moderna, mejor en pantalla.
- **Monospace** — caracteres de ancho fijo (JetBrains Mono, Courier). Código.
- **Display** — fuentes decorativas para titulares grandes. No usar para texto de cuerpo.

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Escala Tipográfica

---
layout: default-y-center
---

## La Escala Tipográfica

::contents::
Una escala tipográfica es un conjunto de tamaños que siguen una proporción matemática.

**Escala modular (ratio 1.25 — "Major Third"):**
```
xs:  0.64rem  (~10px)
sm:  0.8rem   (~13px)
base:1rem     (16px)   ← siempre el punto de partida
lg:  1.25rem  (~20px)
xl:  1.563rem (~25px)
2xl: 1.953rem (~31px)
3xl: 2.441rem (~39px)
4xl: 3.052rem (~49px)
```

**Regla:** usa siempre `rem`, no `px`, para respetar la configuración de fuente del usuario.

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Escala en CSS Custom Properties

::contents::
```css
:root {
  --text-xs:   0.75rem;
  --text-sm:   0.875rem;
  --text-base: 1rem;
  --text-lg:   1.125rem;
  --text-xl:   1.25rem;
  --text-2xl:  1.5rem;
  --text-3xl:  1.875rem;
  --text-4xl:  2.25rem;
}

h1 { font-size: var(--text-4xl); }
h2 { font-size: var(--text-2xl); }
h3 { font-size: var(--text-xl); }
p  { font-size: var(--text-base); }
small { font-size: var(--text-sm); }
```

Definir la escala una vez y reutilizarla en todo el proyecto.

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Legibilidad

---
layout: default-y-center
---

## Line-height: El Espaciado Entre Líneas

::contents::
El `line-height` afecta directamente la legibilidad del texto.

```css
/* Demasiado apretado — difícil de leer */
p { line-height: 1; }

/* Correcto para cuerpo de texto */
p { line-height: 1.6; }

/* Correcto para titulares grandes */
h1 { line-height: 1.1; }
h2 { line-height: 1.2; }

/* Demasiado espaciado — se pierde continuidad */
p { line-height: 2.5; }
```

**Reglas prácticas:**
- Texto de cuerpo: `line-height: 1.5` a `1.7`
- Títulos grandes: `line-height: 1.1` a `1.2`
- Nunca uses `px` para line-height — usa valores sin unidad

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Letter-spacing y Ancho de Línea

::contents::
**Letter-spacing (`letter-spacing`):**
```css
/* Títulos grandes en mayúsculas — más espaciado */
.titulo-caps {
  text-transform: uppercase;
  letter-spacing: 0.1em;
}

/* Texto de cuerpo — casi nunca modifiques este */
p { letter-spacing: normal; }
```

**Ancho máximo de línea (`max-width`):**

Una línea con más de ~75 caracteres es difícil de leer.
```css
/* La regla de los 65ch */
p, li, blockquote {
  max-width: 65ch; /* "ch" = ancho del carácter "0" */
}
```

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Fuentes Web

---
layout: default-y-center
---

## Google Fonts

::contents::
La forma más fácil de usar fuentes no-sistema en web.

```html
<!-- En el <head> del HTML -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;700&display=swap" rel="stylesheet">
```

```css
body {
  font-family: 'Inter', sans-serif;
}
```

**O con CSS @import:**
```css
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap');
```

⚠️ Carga solo los pesos que vas a usar. Cada peso extra = más bytes descargados.

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## System Font Stack

::contents::
La opción más rápida: usar las fuentes del sistema operativo.

```css
body {
  font-family:
    -apple-system,       /* macOS/iOS: San Francisco */
    BlinkMacSystemFont,  /* Chrome en macOS */
    'Segoe UI',          /* Windows */
    Roboto,              /* Android/Chrome OS */
    Oxygen,              /* KDE Linux */
    Ubuntu,              /* Ubuntu Linux */
    sans-serif;          /* Fallback genérico */
}
```

✅ **Ventajas:** cero tiempo de descarga, nativa del sistema, legible por diseño

⚠️ **Desventaja:** cada sistema se ve diferente

**Cuándo usar:** apps de productividad, dashboards, proyectos que priorizan velocidad.

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Pairing de Fuentes

---
layout: default-y-center
---

## Combinar Fuentes

::contents::
**Regla #1:** usa máximo 2 fuentes en un proyecto.

**Pairing que funciona bien:** una fuente para títulos + otra para cuerpo.

```css
/* Clásico: serif para títulos, sans-serif para cuerpo */
h1, h2, h3 {
  font-family: 'Playfair Display', serif;
}
body {
  font-family: 'Source Sans 3', sans-serif;
}

/* Moderno: dos sans-serif con personalidades distintas */
h1, h2, h3 {
  font-family: 'Space Grotesk', sans-serif; /* geométrica */
}
body {
  font-family: 'Inter', sans-serif; /* neutral */
}
```

**Tip:** Google Fonts tiene sugerencias de pairing en cada fuente.

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Resumen — Buenas Prácticas

::contents::
✅ Usa `rem` para tamaños — nunca `px` en `font-size`

✅ `line-height: 1.5`–`1.7` para texto de cuerpo

✅ `max-width: 65ch` para párrafos largos

✅ Máximo 2 fuentes en un mismo proyecto

✅ Carga solo los pesos que usas en Google Fonts

✅ Usa variables CSS para tu escala tipográfica

❌ No uses `px` fijos en `font-size` — rompe el zoom del usuario

❌ No uses más de 3 pesos tipográficos diferentes

❌ No pongas texto claro sobre fondo claro (contraste insuficiente)

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# 🎉
