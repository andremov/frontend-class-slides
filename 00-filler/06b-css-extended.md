---
theme: ../theme
transition: none
layout: cover
title: CSS Extendido
exportFilename: 06b-css-extended
---

# CSS Extendido
## Conceptos Adicionales

✏️ 2025-03 ➖ ⏱️ 30 min.

---
layout: cover
---

# Selectores Avanzados

---
layout: default-y-center
---

## Selectores Combinados

::contents::
**Descendiente** (espacio):
```css
div p { color: blue; } /* Todos los <p> dentro de <div> */
```

**Hijo directo** (>):
```css
div > p { color: red; } /* Solo <p> hijos directos de <div> */
```

**Hermano adyacente** (+):
```css
h1 + p { color: green; } /* <p> inmediatamente después de <h1> */
```

**Hermanos generales** (~):
```css
h1 ~ p { color: orange; } /* Todos los <p> después de <h1> */
```

::header::
Semana 2: CSS Extendido

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Selectores de Atributo

::contents::
```css
/* Tiene el atributo */
[disabled] { opacity: 0.5; }

/* Valor exacto */
[type="text"] { border: 1px solid gray; }

/* Contiene valor */
[class*="btn"] { padding: 10px; }

/* Empieza con */
[href^="https"] { color: green; }

/* Termina con */
[href$=".pdf"] { color: red; }
```

::header::
Semana 2: CSS Extendido

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Pseudo-clases Avanzadas

::contents::
```css
/* Estados de enlaces */
a:visited { color: purple; }
a:active { color: orange; }

/* Selección de hijos */
li:first-child { font-weight: bold; }
li:last-child { border-bottom: none; }
li:nth-child(2n) { background: #f0f0f0; }
li:nth-child(odd) { background: #fff; }
li:nth-child(3n+1) { color: red; }

/* Pseudo-clases estructurales */
p:first-of-type { margin-top: 0; }
p:last-of-type { margin-bottom: 0; }
div:only-child { width: 100%; }
```

::header::
Semana 2: CSS Extendido

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Pseudo-elementos

::contents::
```css
/* Primera letra y línea */
p::first-letter { font-size: 2em; }
p::first-line { font-weight: bold; }

/* Contenido antes y después */
.quote::before { content: '"'; }
.quote::after { content: '"'; }

/* Placeholder */
input::placeholder { color: gray; }

/* Selección de texto */
::selection { 
    background: yellow;
    color: black;
}
```

::header::
Semana 2: CSS Extendido

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Formas de Agregar CSS

---
layout: default-y-center
---

## 3 Formas de Agregar CSS

::contents::
**1. CSS Inline** (en el elemento):
```html
<p style="color: blue; font-size: 16px;">Texto</p>
```

**2. CSS Interno** (en el `<head>`):
```html
<style>
    p { color: blue; }
</style>
```

**3. CSS Externo** (archivo separado):
```html
<link rel="stylesheet" href="styles.css">
```

::header::
Semana 2: CSS Extendido

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Cuál Usar?

::contents::
❌ **CSS Inline**: Evitar (mezcla contenido y estilo)

⚠️ **CSS Interno**: Solo para páginas pequeñas o prototipos

✅ **CSS Externo**: Recomendado (reutilizable, cacheable, mantenible)

**Mejor práctica**: Usar archivos CSS externos.

::header::
Semana 2: CSS Extendido

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Especificidad Detallada

---
layout: default-y-center
---

## Cálculo de Especificidad

::contents::
Cálculo de especificidad (de mayor a menor):

1. **Inline styles**: `style=""` → 1000 puntos
2. **IDs**: `#id` → 100 puntos
3. **Clases, atributos, pseudo-clases**: `.class`, `[attr]`, `:hover` → 10 puntos
4. **Elementos, pseudo-elementos**: `div`, `::before` → 1 punto

```css
/* Especificidad: 1 */
p { color: blue; }

/* Especificidad: 10 */
.text { color: red; }

/* Especificidad: 100 */
#main { color: green; }

/* Especificidad: 111 */
#main p.text { color: orange; } /* Este gana */
```

::header::
Semana 2: CSS Extendido

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Herencia CSS

::contents::
Algunas propiedades se heredan automáticamente a los hijos:

**Se heredan**: `color`, `font-family`, `font-size`, `line-height`, `text-align`, etc.

**NO se heredan**: `margin`, `padding`, `border`, `background`, `width`, `height`, etc.

```css
body {
    font-family: Arial;
    color: #333;
}

/* Todos los elementos heredan la fuente y color */

div {
    /* NO hereda padding del body */
    padding: 20px;
}
```

::header::
Semana 2: CSS Extendido

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## La Cascada

::contents::
"Cascading" significa que los estilos se aplican en orden:

1. **Importancia**: `!important` > estilos normales
2. **Especificidad**: Qué tan específico es el selector
3. **Orden**: El último definido gana

```css
p { color: blue; }
p { color: red; } /* Este gana */

p { color: blue !important; } /* Este gana sobre todo */
```

⚠️ **Evitar `!important`** excepto en casos muy específicos.

::header::
Semana 2: CSS Extendido

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Metodologías CSS

---
layout: default-y-center
---

## BEM (Block Element Modifier)

::contents::
**BEM** = Block Element Modifier

```css
/* Block */
.card { }

/* Element (hijo del block) */
.card__title { }
.card__content { }

/* Modifier (variación del block o element) */
.card--featured { }
.card__title--large { }
```

```html
<div class="card card--featured">
    <h2 class="card__title card__title--large">Título</h2>
    <p class="card__content">Contenido</p>
</div>
```

::header::
Semana 2: CSS Extendido

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Ventajas de BEM

::contents::
✅ **Modular**: Componentes independientes y reutilizables

✅ **Legible**: Nombres descriptivos y predecibles

✅ **Escalable**: Fácil de mantener en proyectos grandes

✅ **Sin conflictos**: Evita colisiones de nombres

**Ideal para**: Proyectos grandes, equipos grandes, CSS vanilla

::header::
Semana 2: CSS Extendido

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Mejores Prácticas Detalladas

---
layout: default-y-center
---

## Organización del Código

::contents::
✅ **Agrupar por componentes o secciones**

✅ **Ordenar propiedades lógicamente**:
1. Posicionamiento (position, top, left)
2. Box model (display, width, margin, padding)
3. Tipografía (font, text)
4. Visual (background, border, color)
5. Otros (cursor, transform)

✅ **Comentar secciones complejas**

✅ **Usar nombres descriptivos** de clases

::header::
Semana 2: CSS Extendido

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Performance CSS

::contents::
✅ **Minimizar CSS** en producción

✅ **Evitar selectores complejos** y anidamiento excesivo

✅ **Usar `will-change`** con moderación:
```css
.animated {
    will-change: transform;
}
```

✅ **Evitar `@import`** en CSS (usa `<link>` en HTML)

✅ **Cargar CSS crítico** inline, resto asíncrono

::header::
Semana 2: CSS Extendido

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Código Limpio

::contents::
✅ **Evitar `!important`** - indica problemas de especificidad

✅ **Preferir clases sobre IDs** para estilos

✅ **No usar selectores de etiqueta** para estilos (excepto reset)

✅ **Usar shorthand properties** cuando sea apropiado

✅ **Validar CSS** con herramientas como CSS Validator

✅ **Mantener consistencia** en el formato

::header::
Semana 2: CSS Extendido

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Preprocesadores y Herramientas

---
layout: default-y-center
---

## Preprocesadores CSS

::contents::
**Sass/SCSS**:
```scss
$primary-color: #007bff;

.button {
    background: $primary-color;
    
    &:hover {
        background: darken($primary-color, 10%);
    }
}
```

**Less**:
```less
@primary-color: #007bff;

.button {
    background: @primary-color;
    
    &:hover {
        background: darken(@primary-color, 10%);
    }
}
```

::header::
Semana 2: CSS Extendido

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## PostCSS

::contents::
PostCSS es una herramienta para transformar CSS con plugins:

**Autoprefixer**: Agrega prefijos de navegador automáticamente
```css
/* Tu escribes */
display: flex;

/* Autoprefixer genera */
display: -webkit-box;
display: -ms-flexbox;
display: flex;
```

**PurgeCSS**: Elimina CSS no usado

**CSSNano**: Minimiza CSS

::header::
Semana 2: CSS Extendido

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Frameworks CSS

::contents::
**Bootstrap**:
- Completo y popular
- Componentes prediseñados
- Grid system responsive

**Tailwind CSS**:
- Utility-first
- Altamente personalizable
- No componentes prediseñados

**Bulma**:
- Basado en Flexbox
- Modular y ligero
- Sintaxis simple

::header::
Semana 2: CSS Extendido

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Herramientas Útiles

::contents::
**Desarrollo**:
- DevTools del navegador
- CSS Validator (W3C)
- Can I Use (compatibilidad)

**Generadores**:
- CSS Grid Generator
- Gradient Generator
- Box Shadow Generator

**Optimización**:
- PurgeCSS
- CSSNano
- Critical CSS

::header::
Semana 2: CSS Extendido

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# 🎉
