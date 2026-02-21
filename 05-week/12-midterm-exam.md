---
theme: ../theme
transition: none
layout: cover
title: Examen de Medio Término
exportFilename: 12-midterm-exam
---

# Examen de Medio Término

📝 Desarrollo Front-End ➖ 2026-01

---
layout: question
---

## Pregunta 1

Qué es Front-end?

- El servidor que maneja los datos de la aplicación
- Aquello que el usuario ve y manipula
- La base de datos de la aplicación
- El código que se ejecuta en el servidor

---
layout: question
---

## Pregunta 2

Cuál es la diferencia principal entre una librería y un framework?

- No hay diferencia, son lo mismo
- Una librería incluye todo lo necesario, un framework solo herramientas específicas
- Una librería solo proporciona herramientas específicas, un framework incluye todo
- Una librería es más grande que un framework

---
layout: question
---

## Pregunta 3

React es una librería o un framework?

- Framework, porque incluye routing y estado global
- Librería, porque solo maneja la UI
- Framework, porque es muy completo
- Librería, porque es pequeño

---
layout: question
---

## Pregunta 4

Qué elemento HTML NO es semántico?

- `<header>`
- `<nav>`
- `<div>`
- `<article>`

---
layout: question
---

## Pregunta 5

Por qué es importante usar HTML semántico?

- Solo para hacer el código más bonito
- Para mejorar la accesibilidad, SEO y mantenibilidad del código
- Para que la página cargue más rápido
- No es importante, es solo una preferencia de estilo

---
layout: question
---

## Pregunta 6

Para qué sirve el elemento `<label>` en formularios?

- Para crear etiquetas visuales
- Para asociar texto descriptivo con inputs y mejorar accesibilidad
- Para agrupar inputs
- Para validar formularios

---
layout: question
---

## Pregunta 7

Qué significa CSS?

- Computer Style Sheets
- Cascading Style Sheets
- Creative Style System
- Cascading System Styles

---
layout: question
---

## Pregunta 8

Cuál es el propósito principal de CSS?

- Crear la estructura de la página
- Agregar interactividad
- Definir el estilo visual de las páginas web
- Manejar bases de datos

---
layout: question
---

## Pregunta 9

Cuál es la sintaxis correcta de CSS?

- `selector { propiedad: valor; }`
- `selector [propiedad = valor]`
- `propiedad { selector: valor; }`
- `{ selector propiedad valor }`

---
layout: question
---

## Pregunta 10

Cuál selector tiene mayor especificidad?

- `.clase`
- `elemento`
- `#id`
- `*`

---
layout: question
---

## Pregunta 11

En la cascada CSS, qué tiene mayor prioridad?

- El primer estilo en el código
- La especificidad
- El último estilo en el código
- El navegador decide

---
layout: question
---

## Pregunta 12

Qué NO es parte del Box Model?

- Content
- Padding
- Margin
- Color

---
layout: question
---

## Pregunta 13

Dado el siguiente HTML y CSS, de qué color será el texto?

HTML: `<div id="box" class="container">Texto</div>`

CSS:
```css
div { color: blue; }
.container { color: green; }
#box { color: red; }
```

- blue
- green
- red
- negro (valor por defecto)

---
layout: question
---

## Pregunta 14

Qué hace `display: none`?

- Hace el elemento transparente
- Oculta el elemento completamente
- Hace el elemento pequeño
- Quita solo el color del elemento

---
layout: question
---

## Pregunta 15

Dado el siguiente CSS, de qué color será el fondo?

```css
.box { background: blue; }
.box { background: green; }
.box { background: red; }
```

- blue
- green
- red
- Ninguno, hay un conflicto

---
layout: question
---

## Pregunta 16

Dado el siguiente CSS, de qué color será el borde?

```css
div.item { border-color: blue; }
.item { border-color: green; }
```

- blue
- green
- negro (valor por defecto)
- Ambos colores se mezclan

---
layout: question
---

## Pregunta 17

Dado el siguiente CSS, qué tamaño de fuente se aplicará?

```css
p { font-size: 14px; }
p { font-size: 16px; }
#texto { font-size: 18px; }
```

HTML: `<p id="texto">Hola</p>`

- 14px
- 16px
- 18px
- 16px y 18px se combinan

---
layout: question
---

## Pregunta 18

Cuál es la diferencia entre Flexbox y Grid?

- Flexbox es unidimensional (fila o columna), Grid es bidimensional (filas y columnas)
- Flexbox es bidimensional, Grid es unidimensional
- Ambos son unidimensionales
- Ambos son bidimensionales

---
layout: question
---

## Pregunta 19

Para qué se usan las media queries?

- Para consultar bases de datos
- Para aplicar estilos según características del dispositivo
- Para cargar imágenes
- Para crear animaciones

---
layout: question
---

## Pregunta 20

Qué es el enfoque "Mobile First"?

- Diseñar solo para móviles
- Diseñar primero para móvil y luego escalar hacia arriba
- Diseñar primero para desktop y luego para móvil
- Diseñar igual para todos los dispositivos

---
layout: question
---

## Pregunta 21

Qué significa `vw` en CSS?

- Very wide
- Viewport width (ancho del viewport)
- Variable width
- Visible width

---
layout: question
---

## Pregunta 22

Qué es BEM?

- Un framework de CSS
- Una metodología de nombrado de clases CSS
- Un preprocesador de CSS
- Un lenguaje de programación

---
layout: question
---

## Pregunta 23

En BEM, qué significa el "Block"?

- Un elemento bloqueado
- Un componente independiente
- Un modificador de estilo
- Una clase prohibida

---
layout: question
---

## Pregunta 24

En BEM, cómo se separan los elementos del bloque?

- Con un guion: `block-element`
- Con doble guion bajo: `block__element`
- Con punto: `block.element`
- Con slash: `block/element`

---
layout: question
---

## Pregunta 25

En BEM, cómo se separan los modificadores?

- Con doble guion: `block--modifier`
- Con guion bajo: `block_modifier`
- Con punto: `block.modifier`
- Con dos puntos: `block:modifier`

---
layout: question
---

## Pregunta 26

Cómo se definen variables CSS?

- `var-name: value;`
- `$name: value;`
- `--name: value;`
- `@name: value;`

---
layout: question
---

## Pregunta 27

Cómo se usan las variables CSS?

- `value(--name)`
- `var(--name)`
- `use(--name)`
- `get(--name)`

---
layout: question
---

## Pregunta 28

Qué unidad CSS es relativa al tamaño de fuente del root?

- em
- px
- rem
- %

---
layout: question
---

## Pregunta 29

Cuál es el breakpoint común para tablets?

- 320px
- 768px
- 1024px
- 1440px

---
layout: question
---

## Pregunta 30

Qué propiedad grid se usa para definir el espacio entre items?

- space
- margin
- gap
- padding

---
layout: cover
---

# Fin del Examen

¡Buena suerte! 🍀
