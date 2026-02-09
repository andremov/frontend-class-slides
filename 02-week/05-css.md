---
theme: ../theme
transition: none
layout: cover
title: CSS - Cascading Style Sheets
exportFilename: 05-css
---

# CSS
## Cascading Style Sheets

✏️ 2026-01 ➖ ⏱️ 60 min.

---
layout: cover
---

# Que es CSS?

---
layout: default-y-center
---

## CSS - Cascading Style Sheets

::contents::
CSS es el lenguaje que define el **estilo visual** de las páginas web.

Controla colores, fuentes, espaciado, layout, animaciones, y más.

Separa el contenido (HTML) de la presentación (CSS).

::header::
Semana 2: CSS

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Por qué usar CSS?

::contents::
✅ **Separación de responsabilidades**: Contenido vs Presentación

✅ **Reutilización**: Un archivo CSS para múltiples páginas

✅ **Mantenimiento**: Cambiar estilos en un solo lugar

✅ **Responsividad**: Adaptar diseño a diferentes dispositivos

::header::
Semana 2: CSS

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Sintaxis y Selectores

---
layout: default-y-center
---

## Sintaxis Básica de CSS

::contents::
```css
selector {
    propiedad: valor;
    otra-propiedad: otro-valor;
}
```

**Ejemplo:**
```css
p {
    color: blue;
    font-size: 16px;
    margin: 10px;
}
```

::header::
Semana 2: CSS

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Selectores Básicos

::contents::
**Selector de elemento:**
```css
p { color: blue; }
```

**Selector de clase:**
```css
.mi-clase { color: red; }
```

**Selector de ID:**
```css
#mi-id { color: green; }
```

**Selector universal:**
```css
* { margin: 0; }
```

::header::
Semana 2: CSS

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Pseudo-clases Comunes

::contents::
```css
/* Estados de interacción */
a:hover { color: red; }
button:hover { background: lightblue; }

/* Elementos de formulario */
input:focus { border-color: blue; }
input:disabled { opacity: 0.5; }
```

::header::
Semana 2: CSS

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Propiedades CSS Comunes

---
layout: default-y-center
---

## Colores

::contents::
```css
/* Nombres de color */
color: red;

/* Hexadecimal */
color: #ff0000;
color: #f00; /* Forma corta */

/* RGB */
color: rgb(255, 0, 0);

/* RGBA (con transparencia) */
color: rgba(255, 0, 0, 0.5);

/* HSL */
color: hsl(0, 100%, 50%);
```

::header::
Semana 2: CSS

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Tipografía

::contents::
```css
/* Familia de fuente */
font-family: Arial, Helvetica, sans-serif;

/* Tamaño */
font-size: 16px;
font-size: 1.2rem;

/* Peso */
font-weight: normal; /* 400 */
font-weight: bold;   /* 700 */

/* Estilo */
font-style: italic;

/* Altura de línea */
line-height: 1.5;
```

::header::
Semana 2: CSS

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Texto

::contents::
```css
/* Alineación */
text-align: left | center | right | justify;

/* Decoración */
text-decoration: none | underline | line-through;

/* Transformación */
text-transform: uppercase | lowercase | capitalize;

/* Espaciado */
letter-spacing: 2px;
word-spacing: 5px;

/* Sombra */
text-shadow: 2px 2px 4px rgba(0,0,0,0.5);
```

::header::
Semana 2: CSS

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Fondo

::contents::
```css
/* Color de fondo */
background-color: #f0f0f0;

/* Imagen de fondo */
background-image: url('imagen.jpg');

/* Repetición */
background-repeat: no-repeat | repeat | repeat-x | repeat-y;

/* Posición */
background-position: center;

/* Tamaño */
background-size: cover | contain | 100px 200px;

/* Forma corta */
background: url('img.jpg') no-repeat center/cover;
```

::header::
Semana 2: CSS

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Cascada y Especificidad

---
layout: default-y-center
---

## Qué es la Cascada?

::contents::
La **cascada** es el mecanismo que determina qué estilos se aplican cuando hay conflictos.

**Orden de prioridad:**

1. **Importancia**: `!important` (evitar)
2. **Especificidad**: IDs > Clases > Elementos
3. **Orden de código**: El último estilo gana

```css
/* Archivo styles.css */
p { color: blue; }
p { color: red; }  /* ✅ Este gana (último) */

.texto { color: green; }  /* ✅ Este gana (más específico) */
```

La cascada permite **heredar** y **sobreescribir** estilos de manera predecible.

::header::
Semana 2: CSS

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## La Cascada y Especificidad

::contents::
Los estilos se aplican en orden de especificidad:

**IDs** (`#id`) > **Clases** (`.class`) > **Elementos** (`div`)

```css
/* Especificidad baja */
p { color: blue; }

/* Especificidad media */
.texto { color: red; }

/* Especificidad alta */
#principal { color: green; }
```

⚠️ **Evitar `!important`** - rompe la cascada natural.

::header::
Semana 2: CSS

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Combinando Selectores: Mayor Especificidad

::contents::
Combinar selectores aumenta la especificidad:

```css
/* Especificidad: 0,0,1 (1 elemento) */
p { color: blue; }

/* Especificidad: 0,1,0 (1 clase) */
.texto { color: red; }

/* Especificidad: 0,1,1 (1 clase + 1 elemento) */
p.texto { color: green; }

/* Especificidad: 0,2,1 (2 clases + 1 elemento) */
p.texto.destacado { color: purple; }

/* Especificidad: 1,0,0 (1 ID) */
#principal { color: orange; }

/* Especificidad: 1,1,1 (1 ID + 1 clase + 1 elemento) */
div#principal .texto { color: brown; }
```

::header::
Semana 2: CSS

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Animaciones y Transiciones

---
layout: default-y-center
---

## Transiciones

::contents::
Animan cambios de propiedades CSS:

```css
.button {
    background-color: blue;
    transition: background-color 0.3s ease;
}

.button:hover {
    background-color: red;
}

/* Múltiples propiedades */
.box {
    transition: all 0.3s ease-in-out;
}

/* Propiedades individuales */
.element {
    transition: 
        opacity 0.3s ease,
        transform 0.5s cubic-bezier(0.68, -0.55, 0.265, 1.55);
}
```

::header::
Semana 2: CSS

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Animaciones (Keyframes)

::contents::
```css
/* Definir animación */
@keyframes slide-in {
    0% {
        transform: translateX(-100%);
        opacity: 0;
    }
    100% {
        transform: translateX(0);
        opacity: 1;
    }
}

/* Usar animación */
.element {
    animation: slide-in 0.5s ease-out;
}

/* Con todas las propiedades */
.element {
    animation: slide-in 1s ease-in-out 0.5s infinite alternate;
    /*       nombre duración timing delay iteraciones dirección */
}
```

::header::
Semana 2: CSS

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Transform

::contents::
```css
/* Trasladar */
transform: translate(50px, 100px);
transform: translateX(50px);

/* Escalar */
transform: scale(1.5);
transform: scale(2, 0.5); /* x, y */

/* Rotar */
transform: rotate(45deg);

/* Sesgar */
transform: skew(10deg, 5deg);

/* Combinar */
transform: translate(50px) rotate(45deg) scale(1.2);
```

::header::
Semana 2: CSS

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# El Modelo de Caja (Box Model)

---
layout: default-y-center
---

## Box Model

::contents::
Cada elemento HTML es una caja rectangular con:

1. **Content**: El contenido (texto, imagen, etc.)
2. **Padding**: Espacio interno entre contenido y borde
3. **Border**: El borde de la caja
4. **Margin**: Espacio externo entre la caja y otros elementos

```css
div {
    width: 300px;
    padding: 20px;
    border: 2px solid black;
    margin: 10px;
}
```

::header::
Semana 2: CSS

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Box Model - Visualización

::contents::
```
┌─────────── margin ───────────┐
│ ┌───────── border ─────────┐ │
│ │ ┌─────── padding ──────┐ │ │
│ │ │                      │ │ │
│ │ │        CONTENT       │ │ │
│ │ │                      │ │ │
│ │ └──────────────────────┘ │ │
│ └──────────────────────────┘ │
└──────────────────────────────┘
```

**Ancho total** = width + padding + border + margin

::header::
Semana 2: CSS

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Box Sizing

::contents::
```css
/* Por defecto (content-box) */
div {
    box-sizing: content-box;
    width: 300px; /* Solo el contenido */
    padding: 20px; /* Se suma al width */
}

/* Border-box (recomendado) */
div {
    box-sizing: border-box;
    width: 300px; /* Incluye padding y border */
    padding: 20px; /* No se suma al width */
}
```

**Mejor práctica**: Usar `border-box` globalmente
```css
* { box-sizing: border-box; }
```

::header::
Semana 2: CSS

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Padding y Margin

::contents::
```css
/* Individual */
padding-top: 10px;
padding-right: 20px;
padding-bottom: 10px;
padding-left: 20px;

/* Forma corta - 4 valores (arriba, derecha, abajo, izquierda) */
padding: 10px 20px 10px 20px;

/* Forma corta - 2 valores (vertical, horizontal) */
padding: 10px 20px;

/* Forma corta - 1 valor (todos los lados) */
padding: 10px;
```

Lo mismo aplica para `margin`.

::header::
Semana 2: CSS

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Bordes

::contents::
```css
/* Forma individual */
border-width: 2px;
border-style: solid;
border-color: black;

/* Forma corta */
border: 2px solid black;

/* Bordes específicos */
border-top: 1px solid red;
border-right: 2px dashed blue;

/* Bordes redondeados */
border-radius: 5px;
border-radius: 50%; /* Círculo */
```

::header::
Semana 2: CSS

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Display y Position

---
layout: default-y-center
---

## Display

::contents::
```css
/* Bloque (ocupa toda la línea) */
display: block;

/* En línea (solo el espacio necesario) */
display: inline;

/* En línea-bloque (híbrido) */
display: inline-block;

/* Ocultar elemento */
display: none;

/* Flexbox */
display: flex;

/* Grid */
display: grid;
```

::header::
Semana 2: CSS

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Position

::contents::
```css
/* Estático (por defecto) */
position: static;

/* Relativo (relativo a su posición original) */
position: relative;
top: 10px;
left: 20px;

/* Absoluto (relativo al ancestro posicionado) */
position: absolute;

/* Fijo (relativo al viewport) */
position: fixed;

/* Sticky (híbrido relativo-fijo) */
position: sticky;
top: 0;
```

::header::
Semana 2: CSS

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Z-Index

::contents::
Controla el orden de apilamiento de elementos posicionados:

```css
.modal {
    position: fixed;
    z-index: 1000; /* Encima */
}

.overlay {
    position: fixed;
    z-index: 999; /* Debajo del modal */
}

.content {
    position: relative;
    z-index: 1; /* Nivel normal */
}
```

Valores más altos = más cerca del usuario.

::header::
Semana 2: CSS

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# CSS Variables (Custom Properties)

---
layout: default-y-center
---

## CSS Variables

::contents::
```css
/* Definir variables en :root */
:root {
    --primary-color: #007bff;
    --secondary-color: #6c757d;
    --spacing-unit: 8px;
    --font-main: 'Arial', sans-serif;
}

/* Usar variables */
.button {
    background-color: var(--primary-color);
    padding: var(--spacing-unit);
    font-family: var(--font-main);
}

/* Con valor por defecto */
.element {
    color: var(--undefined-color, black);
}
```

::header::
Semana 2: CSS

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Variables - Ámbito y Herencia

::contents::
```css
:root {
    --spacing: 10px;
}

.container {
    /* Redefinir para este ámbito */
    --spacing: 20px;
    padding: var(--spacing); /* 20px */
}

.container .child {
    padding: var(--spacing); /* 20px (heredado) */
}

.other {
    padding: var(--spacing); /* 10px (del :root) */
}
```

::header::
Semana 2: CSS

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Variables - Uso Común: Temas

::contents::
```css
:root {
    --bg-color: white;
    --text-color: black;
}

[data-theme="dark"] {
    --bg-color: #1a1a1a;
    --text-color: white;
}

body {
    background-color: var(--bg-color);
    color: var(--text-color);
}
```

```js
// Cambiar tema con JavaScript
document.body.setAttribute('data-theme', 'dark');
```

::header::
Semana 2: CSS

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Mejores Prácticas

---
layout: default-y-center
---

## Mejores Prácticas

::contents::
✅ **Usar nombres de clase descriptivos**

✅ **Usar variables CSS** para valores reutilizables

✅ **Evitar `!important`**

✅ **Mobile First** approach con media queries

✅ **Preferir Flexbox y Grid** para layouts

::header::
Semana 2: CSS

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## CSS Moderno: Características Útiles

::contents::
```css
/* Clamp - tamaño responsive */
font-size: clamp(1rem, 2.5vw, 2rem);

/* Aspect Ratio */
.video {
    aspect-ratio: 16 / 9;
}

/* Gap en Flexbox */
.flex-container {
    display: flex;
    gap: 20px;
}

/* Logical Properties */
margin-inline: 20px; /* margin-left + margin-right */
padding-block: 10px; /* padding-top + padding-bottom */
```

::header::
Semana 2: CSS

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Recursos de Aprendizaje

::contents::
**Documentación**:
- MDN Web Docs: https://developer.mozilla.org/es/docs/Web/CSS
- CSS Tricks: https://css-tricks.com

**Práctica Interactiva**:
- Flexbox Froggy: https://flexboxfroggy.com
- Grid Garden: https://cssgridgarden.com

**Herramientas**:
- Can I Use: https://caniuse.com

::header::
Semana 2: CSS

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# 🎉
