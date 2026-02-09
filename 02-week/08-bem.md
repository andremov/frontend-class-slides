---
theme: ../theme
transition: none
layout: cover
title: BEM
exportFilename: 08-bem
---

# BEM
## Block Element Modifier

✏️ 2026-01 ➖ ⏱️ 20 min.

---
layout: cover
---

# ¿Qué es BEM?

---
layout: default-y-center
---

## BEM - Block Element Modifier

::contents::
**BEM** es una metodología de nombrado de clases CSS.

**Creado por:** Yandex (empresa rusa de tecnología)

**Objetivo:** Resolver problemas de:
- Colisión de nombres de clases
- Especificidad excesiva
- Código difícil de mantener
- Falta de estructura en proyectos grandes

**Resultado:** Código CSS más predecible y organizado.

::header::
Semana 2: BEM

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Estructura BEM

---
layout: default-y-center
---

## Los Tres Componentes

::contents::
**Block (Bloque):**
- Componente independiente y reutilizable
- Ejemplo: `.card`, `.menu`, `.button`

**Element (Elemento):**
- Parte de un bloque que no tiene sentido por sí sola
- Se separa con doble guion bajo: `__`
- Ejemplo: `.card__title`, `.menu__item`, `.button__icon`

**Modifier (Modificador):**
- Variación de un bloque o elemento
- Se separa con doble guion: `--`
- Ejemplo: `.card--featured`, `.button--primary`, `.menu__item--active`

::header::
Semana 2: BEM

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Sintaxis BEM

::contents::
```css
/* BLOCK */
.block { }

/* ELEMENT */
.block__element { }

/* MODIFIER de BLOCK */
.block--modifier { }

/* MODIFIER de ELEMENT */
.block__element--modifier { }
```

**Regla importante:** Los elementos NO se anidan en la nomenclatura.

❌ **Incorrecto:** `.block__element__subelement`

✅ **Correcto:** `.block__subelement`

::header::
Semana 2: BEM

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Block (Bloque)

---
layout: default-y-center
---

## Block - Componente Independiente

::contents::
Un **bloque** es un componente independiente que puede existir por sí solo.

**Características:**
- Nombre describe su **propósito**, no su apariencia
- Puede contener otros bloques
- No debe tener margin o position (para ser reutilizable)

**Ejemplos:**
```css
.card { }       /* Tarjeta */
.menu { }       /* Menú */
.button { }     /* Botón */
.header { }     /* Encabezado */
.sidebar { }    /* Barra lateral */
.form { }       /* Formulario */
```

::header::
Semana 2: BEM

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Block - Ejemplo

::contents::
```html
<div class="card">
    <!-- Contenido de la tarjeta -->
</div>
```

```css
.card {
    background: white;
    border-radius: 8px;
    padding: 20px;
    /* NO margin o position aquí */
}
```

**Reutilizable en cualquier lugar:**
```html
<div class="sidebar">
    <div class="card">...</div>
</div>

<main>
    <div class="card">...</div>
</main>
```

::header::
Semana 2: BEM

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Element (Elemento)

---
layout: default-y-center
---

## Element - Parte del Bloque

::contents::
Un **elemento** es una parte del bloque que no tiene sentido fuera de él.

**Características:**
- Separado por doble guion bajo: `__`
- No puede existir independientemente
- Describe una parte del bloque

**Ejemplos:**
```css
.card__header { }     /* Encabezado de la tarjeta */
.card__title { }      /* Título de la tarjeta */
.card__body { }       /* Cuerpo de la tarjeta */
.card__footer { }     /* Pie de la tarjeta */
.card__image { }      /* Imagen de la tarjeta */
.card__button { }     /* Botón de la tarjeta */
```

::header::
Semana 2: BEM

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Element - Ejemplo

::contents::
```html
<div class="card">
    <div class="card__header">
        <h2 class="card__title">Título</h2>
    </div>
    <div class="card__body">
        <p class="card__text">Contenido</p>
    </div>
    <div class="card__footer">
        <button class="card__button">Acción</button>
    </div>
</div>
```

```css
.card { }
.card__header { }
.card__title { font-size: 1.5rem; }
.card__body { padding: 15px; }
.card__footer { border-top: 1px solid #ccc; }
.card__button { }
```

::header::
Semana 2: BEM

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Elements - NO Anidación en Nombres

::contents::
❌ **Incorrecto:**
```html
<div class="card">
    <div class="card__body">
        <p class="card__body__text">Texto</p>
    </div>
</div>
```

```css
.card__body__text { } /* ❌ Muy específico */
```

✅ **Correcto:**
```html
<div class="card">
    <div class="card__body">
        <p class="card__text">Texto</p>
    </div>
</div>
```

```css
.card__text { } /* ✅ Simple y claro */
```

::header::
Semana 2: BEM

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Modifier (Modificador)

---
layout: default-y-center
---

## Modifier - Variaciones

::contents::
Un **modificador** define una variación, estado o apariencia diferente de un bloque o elemento.

**Características:**
- Separado por doble guion: `--`
- Describe **cómo se ve**, **cómo se comporta**, o **qué estado tiene**
- Siempre se usa junto con la clase base

**Ejemplos:**
```css
.button--primary { }      /* Botón primario */
.button--large { }        /* Botón grande */
.button--disabled { }     /* Botón deshabilitado */
.card--featured { }       /* Tarjeta destacada */
.card--dark { }           /* Tarjeta oscura */
.menu__item--active { }   /* Item activo */
```

::header::
Semana 2: BEM

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Modifier - Ejemplo

::contents::
```html
<!-- Botón normal -->
<button class="button">Normal</button>

<!-- Botón primario (con modificador) -->
<button class="button button--primary">Primario</button>

<!-- Botón grande y primario (múltiples modificadores) -->
<button class="button button--primary button--large">Grande</button>
```

```css
.button {
    padding: 10px 20px;
    border: none;
    background: gray;
}

.button--primary {
    background: blue;
    color: white;
}

.button--large {
    padding: 15px 30px;
    font-size: 1.2rem;
}
```

::header::
Semana 2: BEM

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Modifier - Siempre con Clase Base

::contents::
❌ **Incorrecto (solo modificador):**
```html
<button class="button--primary">Botón</button>
```

✅ **Correcto (base + modificador):**
```html
<button class="button button--primary">Botón</button>
```

**Razón:** El modificador solo agrega cambios incrementales, la clase base proporciona los estilos fundamentales.

```css
.button {
    /* Estilos base comunes a todos los botones */
    padding: 10px 20px;
    border-radius: 4px;
}

.button--primary {
    /* Solo los cambios para la variante primaria */
    background: blue;
    color: white;
}
```

::header::
Semana 2: BEM

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Ejemplo Completo

---
layout: default-y-center
---

## Ejemplo Completo - Tarjeta de Producto

::contents::
```html
<article class="product-card product-card--featured">
    <div class="product-card__header">
        <img class="product-card__image" src="producto.jpg" alt="Producto">
        <span class="product-card__badge product-card__badge--new">Nuevo</span>
    </div>
    
    <div class="product-card__body">
        <h3 class="product-card__title">Nombre del Producto</h3>
        <p class="product-card__description">Descripción breve</p>
        <span class="product-card__price">$99.99</span>
    </div>
    
    <div class="product-card__footer">
        <button class="product-card__button product-card__button--primary">
            Comprar
        </button>
        <button class="product-card__button product-card__button--secondary">
            Ver más
        </button>
    </div>
</article>
```

::header::
Semana 2: BEM

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Ejemplo Completo - CSS

::contents::
```css
/* Block */
.product-card {
    border: 1px solid #ddd;
    border-radius: 8px;
    background: white;
}

.product-card--featured {
    border-color: gold;
    box-shadow: 0 4px 8px rgba(0,0,0,0.1);
}

```

::header::
Semana 2: BEM

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Ejemplo Completo - CSS

::contents::
```css
/* Elements */
.product-card__header { position: relative; }
.product-card__image { width: 100%; }
.product-card__badge { 
    position: absolute;
    top: 10px;
    right: 10px;
}
.product-card__badge--new { 
    background: green;
    color: white;
}
.product-card__title { font-size: 1.5rem; }
.product-card__description { color: #666; }
.product-card__price { 
    font-size: 1.25rem;
    font-weight: bold;
}
```

::header::
Semana 2: BEM

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Ejemplo Completo - CSS

::contents::
```css
.product-card__footer { 
    display: flex;
    gap: 10px;
}
.product-card__button { padding: 10px 20px; }
.product-card__button--primary { 
    background: blue;
    color: white;
}
.product-card__button--secondary { 
    background: gray;
}
```

::header::
Semana 2: BEM

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Ventajas de BEM

---
layout: default-y-center
---

## Ventajas de Usar BEM

::contents::
✅ **Nombres descriptivos y específicos**
- Se entiende la estructura con solo leer las clases

✅ **Evita conflictos de nombres**
- Cada clase es única y específica

✅ **Especificidad baja y plana**
- No hay anidación profunda de selectores

✅ **Reutilización fácil**
- Los bloques son independientes y portables

✅ **Escalabilidad**
- Funciona bien en proyectos grandes

✅ **Trabajo en equipo**
- Convención clara que todos pueden seguir

✅ **Facilita encontrar y modificar estilos**
- Estructura clara y predecible

::header::
Semana 2: BEM

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Errores Comunes

---
layout: default-y-center
---

## Errores Comunes y Soluciones

::contents::
❌ **Anidar elementos en nombres:**
```css
.card__body__text { } /* MAL */
```
✅ `.card__text { }`

❌ **Usar solo modificadores:**
```html
<div class="card--featured"/> <!-- MAL -->
```
✅ `<div class="card card--featured"/>`

❌ **Modificadores que no describen variaciones:**
```css
.card__title--red { } /* MAL - describe apariencia */
```
✅ `.card__title--error { }` /* Describe propósito */

❌ **Crear bloques demasiado genéricos:**
```css
.text { } /* MAL - muy genérico */
```
✅ `.article__text { }` /* Específico al contexto */

::header::
Semana 2: BEM

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## BEM vs Utility-First

::contents::
**BEM:**
```html
<button class="button button--primary button--large">
    Comprar
</button>
```

**Utility-First (Tailwind):**
```html
<button class="bg-blue-500 text-white px-6 py-3 rounded-lg text-lg">
    Comprar
</button>
```

**BEM = Componentes semánticos**
**Utility = Utilidades atómicas**

::header::
Semana 2: BEM

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Mejores Prácticas

---
layout: default-y-center
---

## Mejores Prácticas con BEM

::contents::
✅ **Mantén los nombres descriptivos pero concisos**
- `.product-card__buy-button` ✅
- `.pc__bb` ❌ (demasiado corto)
- `.product-card__button-that-allows-user-to-buy` ❌ (demasiado largo)

✅ **Usa modificadores para estados**
```css
.menu__item--active { }
.button--disabled { }
.modal--open { }
```

✅ **Un bloque puede contener otros bloques**
```html
<div class="card">
    <button class="button button--primary">Acción</button>
</div>
```

✅ **Documenta tu convención**
- Crea una guía de estilo para tu equipo

::header::
Semana 2: BEM

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Recursos Adicionales

::contents::
**Documentación Oficial:**
- BEM Official: https://en.bem.info/
- BEM Methodology: https://en.bem.info/methodology/

**Artículos:**
- CSS Tricks: BEM 101
- Smashing Magazine: BEM Guide

**Herramientas:**
- BEM Linter (VS Code extension)
- PostCSS BEM Linter

**Ejemplos:**
- Yandex: Ejemplos de componentes BEM
- GitHub: Proyectos ejemplo con BEM

::header::
Semana 2: BEM

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Resumen - BEM en 60 Segundos

::contents::
**Block** → Componente independiente
```css
.card { }
```

**Element** → Parte del bloque (__)
```css
.card__title { }
.card__button { }
```

**Modifier** → Variación o estado (--)
```css
.card--featured { }
.card__button--primary { }
```

**Reglas de oro:**
1. Los elementos NO se anidan en nombres
2. Los modificadores siempre van con la clase base
3. Nombres descriptivos, no de apariencia
4. Especificidad plana

::header::
Semana 2: BEM

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# 🎉
