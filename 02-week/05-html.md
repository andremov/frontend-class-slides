---
theme: ../theme
transition: none
layout: cover
title: HTML - HyperText Markup Language
exportFilename: 05-html
---

# HTML
## HyperText Markup Language

✏️ 2025-03 ➖ ⏱️ 45 min.

---
layout: cover
---

# Que es HTML?

---
layout: default-y-center
---

## HTML - HyperText Markup Language

::contents::
HTML es el lenguaje de marcado estándar para crear páginas web.

Define la **estructura** y el **contenido** de una página web.

No es un lenguaje de programación, es un lenguaje de marcado.

::header::
Semana 2: HTML

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## HTML - Historia Breve

::contents::
Creado por Tim Berners-Lee en 1991.

HTML5 es la versión actual (2014).

Es mantenido por el W3C y WHATWG.

::header::
Semana 2: HTML

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Estructura y Sintaxis

---
layout: default-y-center
---

## Estructura Básica de HTML

::contents::
```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mi Página</title>
</head>
<body>
    <!-- Contenido aquí -->
</body>
</html>
```

::header::
Semana 2: HTML

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Elementos HTML

::contents::
Un elemento HTML tiene:
- **Etiqueta de apertura**: `<p>`
- **Contenido**: El texto o elementos internos
- **Etiqueta de cierre**: `</p>`

```html
<p>Este es un párrafo</p>
```

Algunos elementos son auto-cerrados:
```html
<img src="imagen.jpg" alt="Descripción">
<br>
<input type="text">
```

::header::
Semana 2: HTML

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Atributos HTML

::contents::
Los atributos proporcionan información adicional sobre los elementos.

```html
<a href="https://example.com" target="_blank" class="link">
    Enlace
</a>
```

Atributos comunes:
- `id`: Identificador único
- `class`: Clase para estilos
- `style`: Estilos en línea
- `title`: Texto de ayuda
- `data-*`: Atributos personalizados

::header::
Semana 2: HTML

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Anidamiento de Elementos

::contents::
Los elementos pueden contener otros elementos:

```html
<div>
    <h1>Título</h1>
    <p>Este es un <strong>párrafo</strong> con texto en negrita.</p>
    <ul>
        <li>Item 1</li>
        <li>Item 2</li>
    </ul>
</div>
```

**Importante**: Los elementos deben cerrarse en el orden correcto.

::header::
Semana 2: HTML

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Elementos HTML Comunes

---
layout: default-y-center
---

## Encabezados (Headings)

::contents::
HTML tiene 6 niveles de encabezados:

```html
<h1>Encabezado 1 - El más importante</h1>
<h2>Encabezado 2</h2>
<h3>Encabezado 3</h3>
<h4>Encabezado 4</h4>
<h5>Encabezado 5</h5>
<h6>Encabezado 6 - El menos importante</h6>
```

**Nota**: Solo debe haber un `<h1>` por página.

::header::
Semana 2: HTML

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Texto y Párrafos

::contents::
```html
<p>Este es un párrafo de texto.</p>

<strong>Texto importante (negrita)</strong>
<em>Texto enfatizado (cursiva)</em>
<mark>Texto resaltado</mark>
<small>Texto pequeño</small>

<br> <!-- Salto de línea -->
<hr> <!-- Línea horizontal -->
```

::header::
Semana 2: HTML

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Enlaces (Links)

::contents::
```html
<!-- Enlace externo -->
<a href="https://example.com">Visitar Example</a>

<!-- Enlace que abre en nueva pestaña -->
<a href="https://example.com" target="_blank">
    Abrir en nueva pestaña
</a>

<!-- Enlace a otra página del mismo sitio -->
<a href="/about.html">Sobre Nosotros</a>

<!-- Enlace a una sección de la página -->
<a href="#seccion">Ir a Sección</a>
```

::header::
Semana 2: HTML

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Imágenes

::contents::
```html
<img 
    src="ruta/imagen.jpg" 
    alt="Descripción de la imagen"
    width="300"
    height="200"
>
```

**Importante**: El atributo `alt` es "obligatorio" para accesibilidad.

```html
<!-- Imagen como enlace -->
<a href="/destino.html">
    <img src="imagen.jpg" alt="Descripción">
</a>
```

::header::
Semana 2: HTML

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Listas

::contents::
**Lista desordenada:**
```html
<ul>
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
</ul>
```

**Lista ordenada:**
```html
<ol>
    <li>Primer paso</li>
    <li>Segundo paso</li>
    <li>Tercer paso</li>
</ol>
```

::header::
Semana 2: HTML

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Tablas

::contents::
```html
<table>
    <thead>
        <tr>
            <th>Nombre</th>
            <th>Edad</th>
            <th>Ciudad</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Juan</td>
            <td>25</td>
            <td>Madrid</td>
        </tr>
        <tr>
            <td>María</td>
            <td>30</td>
            <td>Barcelona</td>
        </tr>
    </tbody>
</table>
```

::header::
Semana 2: HTML

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Contenedores Genéricos

::contents::
**`<div>`**: Contenedor de bloque genérico
```html
<div class="container">
    <p>Contenido aquí</p>
</div>
```

**`<span>`**: Contenedor en línea genérico
```html
<p>Este es un <span class="highlight">texto destacado</span></p>
```

**Diferencia**: `<div>` ocupa toda la línea, `<span>` solo el espacio necesario.

::header::
Semana 2: HTML

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# HTML Semántico

---
layout: default-y-center
---

## Que es HTML Semántico?

::contents::
HTML semántico usa etiquetas que **describen su significado** en lugar de solo su apariencia.

**Beneficios**:
- Mejor accesibilidad
- Mejor SEO
- Código más legible
- Mejor para mantenimiento

::header::
Semana 2: HTML

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Elementos Semánticos de Estructura

::contents::
```html
<header>
    <nav>
        <!-- Menú de navegación -->
    </nav>
</header>

<main>
    <article>
        <section>
            <!-- Contenido de una sección -->
        </section>
    </article>
    
    <aside>
        <!-- Contenido relacionado/sidebar -->
    </aside>
</main>

<footer>
    <!-- Pie de página -->
</footer>
```

::header::
Semana 2: HTML

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Elementos Semánticos

::contents::
- **`<header>`**: Encabezado de página o sección
- **`<nav>`**: Navegación principal
- **`<main>`**: Contenido principal (uno por página)
- **`<article>`**: Contenido independiente
- **`<section>`**: Sección temática de contenido
- **`<aside>`**: Contenido relacionado/sidebar
- **`<footer>`**: Pie de página o sección
- **`<figure>`** y **`<figcaption>`**: Imagen con leyenda

::header::
Semana 2: HTML

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## No Semántico vs Semántico

::contents::
**No semántico (malo):**
```html
<div id="header">
    <div id="nav">...</div>
</div>
<div id="content">...</div>
<div id="footer">...</div>
```

**Semántico (bueno):**
```html
<header>
    <nav>...</nav>
</header>
<main>...</main>
<footer>...</footer>
```

::header::
Semana 2: HTML

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Formularios e Inputs

---
layout: default-y-center
---

## Formularios Básicos

::contents::
```html
<form action="/submit" method="POST">
    <label for="nombre">Nombre:</label>
    <input type="text" id="nombre" name="nombre" required>
    
    <label for="email">Email:</label>
    <input type="email" id="email" name="email" required>
    
    <button type="submit">Enviar</button>
</form>
```

**Atributos importantes**:
- `action`: URL donde se envía el formulario
- `method`: GET o POST

::header::
Semana 2: HTML

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Tipos de Input

::contents::
```html
<input type="text" placeholder="Texto">
<input type="email" placeholder="Email">
<input type="password" placeholder="Contraseña">
<input type="number" min="0" max="100">
<input type="date">
<input type="checkbox" id="acepto">
<input type="radio" name="genero" value="m">
<input type="file">
<input type="color">
<input type="range" min="0" max="100">
```

::header::
Semana 2: HTML

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Otros Elementos de Formulario

::contents::
**Área de texto:**
```html
<textarea rows="4" cols="50">Texto aquí</textarea>
```

**Select (dropdown):**
```html
<select name="pais">
    <option value="es">España</option>
    <option value="mx">México</option>
    <option value="ar">Argentina</option>
</select>
```

**Botones:**
```html
<button type="submit">Enviar</button>
<button type="reset">Limpiar</button>
<button type="button">Click</button>
```

::header::
Semana 2: HTML

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Validación de Formularios

::contents::
HTML5 incluye validación nativa:

```html
<input type="email" required>
<input type="url" required>
<input type="number" min="1" max="10" required>
<input type="text" pattern="[A-Za-z]{3,}" required>
<input type="text" minlength="3" maxlength="20">
```

**Atributos de validación**:
- `required`: Campo obligatorio
- `pattern`: Expresión regular
- `min/max`: Valores mínimo/máximo
- `minlength/maxlength`: Longitud

::header::
Semana 2: HTML

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Labels y Accesibilidad

::contents::
**Siempre usa `<label>` con inputs:**

```html
<!-- Opción 1: Con 'for' -->
<label for="username">Usuario:</label>
<input type="text" id="username" name="username">

<!-- Opción 2: Anidado -->
<label>
    Usuario:
    <input type="text" name="username">
</label>
```

Esto mejora la accesibilidad y UX (se puede hacer clic en el label).

::header::
Semana 2: HTML

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Mejores Prácticas

---
layout: default-y-center
---

## Mejores Prácticas - Estructura

::contents::
✅ **Usar HTML semántico** en lugar de `<div>` y `<span>` genéricos

✅ **Un solo `<h1>` por página**

✅ **Estructura jerárquica** de encabezados (h1 → h2 → h3)

✅ **Indentar correctamente** para legibilidad

✅ **Cerrar todas las etiquetas** en el orden correcto

::header::
Semana 2: HTML

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Mejores Prácticas - Accesibilidad

::contents::
✅ **Usar atributo `alt`** en todas las imágenes

✅ **Usar `<label>` con todos los inputs**

✅ **Usar atributo `lang`** en la etiqueta `<html>`

✅ **Usar ARIA** cuando sea necesario

✅ **Asegurar contraste** y tamaño de texto adecuado

::header::
Semana 2: HTML

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Mejores Prácticas - SEO

::contents::
✅ **Meta tags apropiados** (description, keywords, viewport)

✅ **Títulos descriptivos** y únicos por página

✅ **URLs semánticas** y limpias

✅ **Estructura de encabezados clara**

✅ **Atributos `alt` descriptivos** en imágenes

::header::
Semana 2: HTML

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Mejores Prácticas - Performance

::contents::
✅ **Minimizar HTML** en producción

✅ **Lazy loading** para imágenes: `<img loading="lazy">`

✅ **Evitar HTML inline excesivo**

✅ **Usar formatos modernos** de imagen (WebP, AVIF)

✅ **Cargar scripts** al final del body o con `defer`

::header::
Semana 2: HTML

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Validación de HTML

::contents::
Es importante validar tu HTML:

**W3C Validator**: https://validator.w3.org/

Ayuda a encontrar:
- Etiquetas sin cerrar
- Atributos inválidos
- Anidamiento incorrecto
- Problemas de accesibilidad

::header::
Semana 2: HTML

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Recursos Adicionales

::contents::
**Documentación**:
- MDN Web Docs: https://developer.mozilla.org/es/docs/Web/HTML
- HTML Standard: https://html.spec.whatwg.org/

**Herramientas**:
- W3C Validator
- HTML5 Boilerplate
- Can I Use (compatibilidad)

::header::
Semana 2: HTML

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# 🎉
