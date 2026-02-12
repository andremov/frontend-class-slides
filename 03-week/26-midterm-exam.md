---
theme: ../theme
transition: none
layout: cover
title: Examen de Medio Término
exportFilename: midterm-exam
---

# Examen de Medio Término

📝 Desarrollo Front-End ➖ 2026-01

---
layout: question
---

## Pregunta 1

¿Qué es Front-end?

- El servidor que maneja los datos de la aplicación
- Aquello que el usuario ve y manipula
- La base de datos de la aplicación
- El código que se ejecuta en el servidor

---
layout: question
---

## Pregunta 2

¿Qué es Back-end?

- La interfaz de usuario de la aplicación
- El diseño visual de la página web
- Aquello que NO está bajo control del usuario y maneja la lógica de negocio
- El navegador web del usuario

---
layout: question
---

## Pregunta 3

¿Cuál es la diferencia principal entre una librería y un framework?

- No hay diferencia, son lo mismo
- Una librería incluye todo lo necesario, un framework solo herramientas específicas
- Una librería solo proporciona herramientas específicas, un framework incluye todo
- Una librería es más grande que un framework

---
layout: question
---

## Pregunta 4

¿React es una librería o un framework?

- Framework, porque incluye routing y estado global
- Librería, porque solo maneja la UI
- Framework, porque es muy completo
- Librería, porque es pequeño

---
layout: question
---

## Pregunta 5

¿Qué significa HTML?

- Hyper Text Markup Language
- High Tech Modern Language
- Home Tool Markup Language
- Hyperlink and Text Markup Language

---
layout: question
---

## Pregunta 6

¿HTML es un lenguaje de programación?

- Sí, porque ejecuta código
- No, es un lenguaje de marcado
- Sí, porque tiene lógica
- Depende de la versión

---
layout: question-content
---

## Pregunta 7

¿Cuál es la estructura básica correcta de un documento HTML?

::content::
```html
<!DOCTYPE html>
<html>
  <head>
    <title>Mi Página</title>
  </head>
  <body>
    <h1>Contenido</h1>
  </body>
</html>
```

::options::
- `<html><body><head></head></body></html>`
- `<!DOCTYPE html><html><head></head><body></body></html>`
- `<html><head><body></body></head></html>`
- `<!DOCTYPE><head><body></body></head>`

---
layout: question
---

## Pregunta 8

¿Qué elemento HTML se usa para el contenido principal de la página?

- `<div>`
- `<content>`
- `<main>`
- `<body>`

---
layout: question
---

## Pregunta 9

¿Cuántos elementos `<h1>` debe tener una página HTML?

- Tantos como sea necesario
- Ninguno, no es obligatorio
- Solo uno por página
- Mínimo tres

---
layout: question
---

## Pregunta 10

¿Qué atributo es obligatorio en las imágenes para accesibilidad?

- src
- title
- alt
- width

---
layout: question
---

## Pregunta 11

¿Cuál es la diferencia entre `<div>` y `<span>`?

- No hay diferencia
- `<div>` es para texto, `<span>` para contenedores
- `<div>` es de bloque, `<span>` es en línea
- `<div>` es más moderno que `<span>`

---
layout: question
---

## Pregunta 12

¿Qué elemento HTML NO es semántico?

- `<header>`
- `<nav>`
- `<div>`
- `<article>`

---
layout: question
---

## Pregunta 13

¿Para qué sirve el elemento `<label>` en formularios?

- Para crear etiquetas visuales
- Para asociar texto descriptivo con inputs y mejorar accesibilidad
- Para agrupar inputs
- Para validar formularios

---
layout: question
---

## Pregunta 14

¿Qué atributo hace que un campo de formulario sea obligatorio?

- mandatory
- obligatory
- required
- necessary

---
layout: question
---

## Pregunta 15

¿Qué significa CSS?

- Computer Style Sheets
- Cascading Style Sheets
- Creative Style System
- Cascading System Styles

---
layout: question
---

## Pregunta 16

¿Cuál es el propósito principal de CSS?

- Crear la estructura de la página
- Agregar interactividad
- Definir el estilo visual de las páginas web
- Manejar bases de datos

---
layout: question-content
---

## Pregunta 17

¿Cuál es la sintaxis correcta de CSS?

::content::
```css
.mi-clase {
  color: blue;
  font-size: 16px;
}
```

::options::
- `selector { propiedad: valor; }`
- `selector [propiedad = valor]`
- `propiedad { selector: valor; }`
- `{ selector propiedad valor }`

---
layout: question
---

## Pregunta 18

¿Cuál selector tiene mayor especificidad?

- `.clase`
- `elemento`
- `#id`
- `*`

---
layout: question
---

## Pregunta 19

En la cascada CSS, ¿qué tiene mayor prioridad?

- El primer estilo en el código
- La especificidad
- El último estilo en el código
- El navegador decide

---
layout: question
---

## Pregunta 20

¿Qué NO es parte del Box Model?

- Content
- Padding
- Margin
- Color

---
layout: question
---

## Pregunta 21

¿Cuál es el valor recomendado de box-sizing?

- content-box
- border-box
- padding-box
- margin-box

---
layout: question
---

## Pregunta 22

¿Qué hace `display: none`?

- Hace el elemento transparente
- Oculta el elemento completamente
- Hace el elemento pequeño
- Quita solo el color del elemento

---
layout: question
---

## Pregunta 23

¿Qué hace `position: fixed`?

- Fija el elemento en su posición original
- Posiciona el elemento relativo al ancestro
- Posiciona el elemento relativo al viewport
- No hace nada

---
layout: question
---

## Pregunta 24

¿Flexbox es un modelo de layout...?

- Bidimensional (filas y columnas)
- Tridimensional
- Unidimensional (fila o columna)
- Sin dimensiones

---
layout: question
---

## Pregunta 25

¿Qué propiedad de flexbox se usa para centrar items en el eje principal?

- align-items
- justify-content
- text-align
- center-items

---
layout: question
---

## Pregunta 26

¿CSS Grid es un modelo de layout...?

- Unidimensional (fila o columna)
- Solo para texto
- Bidimensional (filas y columnas)
- Solo para imágenes

---
layout: question
---

## Pregunta 27

¿Para qué se usan las media queries?

- Para consultar bases de datos
- Para aplicar estilos según características del dispositivo
- Para cargar imágenes
- Para crear animaciones

---
layout: question
---

## Pregunta 28

¿Qué es el enfoque "Mobile First"?

- Diseñar solo para móviles
- Diseñar primero para móvil y luego escalar hacia arriba
- Diseñar primero para desktop y luego para móvil
- Diseñar igual para todos los dispositivos

---
layout: question
---

## Pregunta 29

¿Qué significa `vw` en CSS?

- Very wide
- Viewport width (ancho del viewport)
- Variable width
- Visible width

---
layout: question
---

## Pregunta 30

¿Qué es BEM?

- Un framework de CSS
- Una metodología de nombrado de clases CSS
- Un preprocesador de CSS
- Un lenguaje de programación

---
layout: question
---

## Pregunta 31

En BEM, ¿qué significa el "Block"?

- Un elemento bloqueado
- Un componente independiente
- Un modificador de estilo
- Una clase prohibida

---
layout: question-content
---

## Pregunta 32

En BEM, ¿cómo se separan los elementos del bloque?

::content::
```css
.card { }
.card__title { }
.card__body { }
.card__footer { }
```

::options::
- Con un guion: `block-element`
- Con doble guion bajo: `block__element`
- Con punto: `block.element`
- Con slash: `block/element`

---
layout: question-content
---

## Pregunta 33

En BEM, ¿cómo se separan los modificadores?

::content::
```css
.button { }
.button--primary { }
.button--large { }
.button--disabled { }
```

::options::
- Con doble guion: `block--modifier`
- Con guion bajo: `block_modifier`
- Con punto: `block.modifier`
- Con dos puntos: `block:modifier`

---
layout: question-content
---

## Pregunta 34

¿Cómo se definen variables CSS?

::content::
```css
:root {
  --primary-color: #007bff;
  --font-size: 16px;
}
```

::options::
- `var-name: value;`
- `$name: value;`
- `--name: value;`
- `@name: value;`

---
layout: question-content
---

## Pregunta 35

¿Cómo se usan las variables CSS?

::content::
```css
.button {
  background: var(--primary-color);
  font-size: var(--font-size);
}
```

::options::
- `value(--name)`
- `var(--name)`
- `use(--name)`
- `get(--name)`

---
layout: question
---

## Pregunta 36

¿Qué unidad CSS es relativa al tamaño de fuente del root?

- em
- px
- rem
- %

---
layout: question
---

## Pregunta 37

¿Cuál es el breakpoint común para tablets?

- 320px
- 768px
- 1024px
- 1440px

---
layout: question
---

## Pregunta 38

¿Qué propiedad grid se usa para definir el espacio entre items?

- space
- margin
- gap
- padding

---
layout: question
---

## Pregunta 39

¿Cuándo deberías usar Flexbox en lugar de Grid?

- Para layouts complejos bidimensionales
- Para alinear elementos en una dirección
- Para crear galerías de imágenes
- Siempre se debe usar Grid

---
layout: question
---

## Pregunta 40

¿Qué meta tag es esencial para diseño responsivo?

- `<meta name="responsive">`
- `<meta name="viewport" content="width=device-width, initial-scale=1.0">`
- `<meta name="mobile">`
- `<meta name="device">`

---
layout: cover
---

# Fin del Examen

¡Buena suerte! 🍀
