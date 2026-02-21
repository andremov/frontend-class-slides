---
theme: ../theme
transition: none
layout: cover
title: Diseño Responsivo
exportFilename: 07-responsive-design
---

# Diseño Responsivo
## Media Queries y Mobile First

✏️ 2026-01 ➖ ⏱️ 25 min.

---
layout: cover
---

# Qué es Diseño Responsivo?

---
layout: default-y-center
---

## Diseño Responsivo

::contents::
El diseño responsivo permite que un sitio web se adapte a diferentes tamaños de pantalla y dispositivos.

**Beneficios:**
- ✅ Mejor experiencia de usuario
- ✅ Un solo código para todos los dispositivos
- ✅ Mejor SEO
- ✅ Mantenimiento más fácil

**Elementos clave:**
- Media Queries
- Unidades flexibles
- Layouts fluidos
- Imágenes responsivas

::header::
Semana 2: Diseño Responsivo

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Media Queries

---
layout: default-y-center
---

## Media Queries - Introducción

::contents::
Permiten aplicar estilos basados en características del dispositivo:

```css
/* Para pantallas de 768px o menos */
@media (max-width: 768px) {
    .container {
        flex-direction: column;
    }
}

/* Para pantallas de 769px o más */
@media (min-width: 769px) {
    .container {
        flex-direction: row;
    }
}
```

::header::
Semana 2: Diseño Responsivo

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Media Queries - Sintaxis

::contents::
```css
/* Sintaxis básica */
@media media-type and (condición) {
    /* Estilos */
}

/* Ejemplos */
@media screen and (min-width: 768px) { }
@media print { }
@media (orientation: landscape) { }

/* Múltiples condiciones */
@media (min-width: 768px) and (max-width: 1024px) { }

/* OR lógico */
@media (max-width: 768px), (orientation: portrait) { }
```

::header::
Semana 2: Diseño Responsivo

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Mobile First

---
layout: default-y-center
---

## Qué es Mobile First?

::contents::
**Mobile First** es un enfoque de diseño que comienza con la versión móvil y luego escala hacia arriba.

**Ventajas:**
- ✅ Prioriza el contenido esencial
- ✅ Mejor rendimiento en dispositivos móviles
- ✅ Progressive enhancement
- ✅ Más fácil escalar hacia arriba que hacia abajo

**Filosofía:** Diseñar para las restricciones del móvil primero, luego agregar complejidad para pantallas más grandes.

::header::
Semana 2: Diseño Responsivo

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Mobile First vs Desktop First

::contents::
**Mobile First (recomendado):**
```css
/* Base: Mobile */
.container { 
    padding: 10px;
    flex-direction: column;
}

/* Tablet y superior */
@media (min-width: 768px) {
    .container { 
        padding: 20px;
        flex-direction: row;
    }
}
```

**Desktop First:**
```css
/* Base: Desktop */
.container { 
    padding: 30px;
    flex-direction: row;
}

/* Móvil y inferior */
@media (max-width: 767px) {
    .container { 
        padding: 10px;
        flex-direction: column;
    }
}
```

::header::
Semana 2: Diseño Responsivo

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Breakpoints

---
layout: default-y-center
---

## Breakpoints Comunes

::contents::
```css
/* Mobile First approach */

/* Mobile (por defecto - 0px+) */
.container { padding: 10px; }

/* Tablet (768px+) */
@media (min-width: 768px) {
    .container { padding: 20px; }
}

/* Desktop (1024px+) */
@media (min-width: 1024px) {
    .container { padding: 30px; }
}

/* Large Desktop (1440px+) */
@media (min-width: 1440px) {
    .container { padding: 40px; }
}
```

::header::
Semana 2: Diseño Responsivo

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Breakpoints Estándar

::contents::
**Breakpoints comúnmente usados:**

- **Mobile**: 0 - 767px
- **Tablet**: 768px - 1023px
- **Desktop**: 1024px - 1439px
- **Large Desktop**: 1440px+

**Importante:** Los breakpoints deben basarse en tu contenido, no solo en dispositivos específicos.

```css
/* Ejemplo basado en contenido */
@media (min-width: 600px) {
    /* El contenido se ve mejor en dos columnas */
    .grid { grid-template-columns: 1fr 1fr; }
}
```

::header::
Semana 2: Diseño Responsivo

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Unidades Responsivas

---
layout: default-y-center
---

## Unidades Relativas vs Absolutas

::contents::
**Unidades Absolutas** (evitar para diseño responsivo):
```css
width: 300px;  /* Siempre 300px */
font-size: 16px;
```

**Unidades Relativas** (preferir):
```css
width: 50%;           /* Relativo al padre */
width: 50vw;          /* Relativo al viewport */
font-size: 1.5rem;    /* Relativo al root */
padding: 2em;         /* Relativo al font-size del elemento */
```

::header::
Semana 2: Diseño Responsivo

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Unidades Responsivas Detalladas

::contents::
```css
/* Porcentaje - relativo al elemento padre */
width: 50%;

/* Viewport - relativo al tamaño de la pantalla */
width: 50vw;   /* 50% del ancho del viewport */
height: 100vh; /* 100% de la altura del viewport */
font-size: 5vw; /* Crece/decrece con el viewport */

/* REM - relativo al font-size del root (html) */
font-size: 1.5rem;
padding: 2rem;

/* EM - relativo al font-size del padre */
padding: 2em;
margin: 1.5em;
```

::header::
Semana 2: Diseño Responsivo

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Funciones CSS Modernas

::contents::
```css
/* MIN - el valor más pequeño */
width: min(500px, 100%);
/* Nunca más de 500px, pero puede ser menos */

/* MAX - el valor más grande */
width: max(300px, 50%);
/* Al menos 300px, pero puede ser más */

/* CLAMP - valor entre mín y máx */
width: clamp(300px, 50%, 800px);
/* Mínimo 300px, ideal 50%, máximo 800px */

font-size: clamp(1rem, 2.5vw, 2rem);
/* Fuente responsive entre 1rem y 2rem */
```

::header::
Semana 2: Diseño Responsivo

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Imágenes Responsivas

---
layout: default-y-center
---

## Imágenes Responsivas - CSS

::contents::
```css
/* Básico - imagen nunca sobresale del contenedor */
img {
    max-width: 100%;
    height: auto;
}

/* Control de ajuste con object-fit */
img {
    width: 300px;
    height: 200px;
    object-fit: cover;    /* Recorta para llenar */
    object-fit: contain;  /* Escala para caber */
    object-fit: fill;     /* Estira para llenar */
    object-position: center;
}
```

::header::
Semana 2: Diseño Responsivo

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Imágenes Responsivas - HTML

::contents::
```html
<!-- Picture element para diferentes imágenes -->
<picture>
    <source media="(min-width: 1024px)" srcset="large.jpg">
    <source media="(min-width: 768px)" srcset="medium.jpg">
    <img src="small.jpg" alt="Descripción">
</picture>

<!-- Srcset para diferentes resoluciones -->
<img 
    src="imagen-small.jpg"
    srcset="imagen-medium.jpg 768w, 
            imagen-large.jpg 1024w,
            imagen-xlarge.jpg 1440w"
    sizes="(max-width: 768px) 100vw, 
           (max-width: 1024px) 50vw, 
           33vw"
    alt="Descripción">
```

::header::
Semana 2: Diseño Responsivo

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Contenedores Responsivos

---
layout: default-y-center
---

## Container con Max-Width

::contents::
```css
/* Contenedor que crece hasta un máximo */
.container {
    width: 100%;
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 20px;
}

/* Con media queries para diferentes tamaños */
.container {
    width: 100%;
    margin: 0 auto;
    padding: 0 15px;
}

@media (min-width: 768px) {
    .container {
        max-width: 720px;
        padding: 0 20px;
    }
}

@media (min-width: 1024px) {
    .container {
        max-width: 960px;
    }
}
```

::header::
Semana 2: Diseño Responsivo

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Grid y Flexbox Responsivos

::contents::
```css
/* Grid responsivo */
.grid {
    display: grid;
    grid-template-columns: 1fr; /* Mobile: 1 columna */
    gap: 20px;
}

@media (min-width: 768px) {
    .grid {
        grid-template-columns: repeat(2, 1fr); /* Tablet: 2 columnas */
    }
}

@media (min-width: 1024px) {
    .grid {
        grid-template-columns: repeat(3, 1fr); /* Desktop: 3 columnas */
    }
}

/* Auto-responsive con auto-fit */
.grid-auto {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 20px;
}
```

::header::
Semana 2: Diseño Responsivo

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Viewport Meta Tag

---
layout: default-y-center
---

## Viewport Meta Tag

::contents::
**Esencial para diseño responsivo:**

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

**Sin esta etiqueta**, los móviles renderizarán la página a ancho de escritorio y la escalarán.

**Parámetros:**
- `width=device-width`: Ancho igual al del dispositivo
- `initial-scale=1.0`: Escala inicial al 100%
- `maximum-scale=5.0`: Escala máxima permitida
- `user-scalable=yes`: Permitir zoom (recomendado)

**Siempre incluir en el `<head>` de tu HTML.**

::header::
Semana 2: Diseño Responsivo

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Mejores Prácticas

---
layout: default-y-center
---

## Mejores Prácticas - Diseño Responsivo

::contents::
✅ **Mobile First approach** - Comenzar desde móvil

✅ **Usar unidades relativas** (rem, em, %, vw/vh)

✅ **Breakpoints basados en contenido**, no en dispositivos específicos

✅ **Viewport meta tag** siempre presente

✅ **Imágenes responsivas** con max-width: 100%

✅ **Probar en dispositivos reales** y herramientas de desarrollo

✅ **Flexbox/Grid** para layouts flexibles

✅ **Touch-friendly** - botones y enlaces grandes en móvil (mínimo 44x44px)

::header::
Semana 2: Diseño Responsivo

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Herramientas de Desarrollo

::contents::
**Chrome DevTools:**
- Toggle Device Toolbar (Ctrl+Shift+M)
- Probar diferentes dispositivos
- Ver media queries activas

**Firefox Developer Tools:**
- Responsive Design Mode (Ctrl+Shift+M)
- Excelente para probar diferentes viewports

**Herramientas Online:**
- Responsive Design Checker
- BrowserStack
- LambdaTest

**Extensiones:**
- Window Resizer
- Responsive Viewer

::header::
Semana 2: Diseño Responsivo

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Ejemplo Completo - Mobile First

::contents::
```css
/* Base: Mobile (0px+) */
.header {
    padding: 15px;
    font-size: 1rem;
}

.nav {
    flex-direction: column;
}

.grid {
    grid-template-columns: 1fr;
    gap: 10px;
}

/* Tablet (768px+) */
@media (min-width: 768px) {
    .header {
        padding: 20px;
        font-size: 1.2rem;
    }
    
    .nav {
        flex-direction: row;
        justify-content: space-between;
    }
    
    .grid {
        grid-template-columns: repeat(2, 1fr);
        gap: 20px;
    }
}

/* Desktop (1024px+) */
@media (min-width: 1024px) {
    .header {
        padding: 30px;
        font-size: 1.5rem;
    }
    
    .grid {
        grid-template-columns: repeat(3, 1fr);
        gap: 30px;
    }
}
```

::header::
Semana 2: Diseño Responsivo

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Recursos Adicionales

::contents::
**Documentación:**
- MDN Media Queries: https://developer.mozilla.org/es/docs/Web/CSS/Media_Queries
- MDN Responsive Design: https://developer.mozilla.org/es/docs/Learn/CSS/CSS_layout/Responsive_Design

**Artículos:**
- A List Apart: Responsive Web Design
- Smashing Magazine: Responsive Design

**Herramientas:**
- Can I Use: Compatibilidad de browsers
- Am I Responsive?: Vista previa en múltiples dispositivos

::header::
Semana 2: Diseño Responsivo

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# 🎉
