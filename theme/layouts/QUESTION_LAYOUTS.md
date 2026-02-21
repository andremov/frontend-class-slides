# Question Layouts

This document describes the custom question layouts available for creating exam slides.

## question.vue

A clean question format with a centered title and 4 options displayed in a 2x2 grid.

**Usage:**

```md
---
layout: question
---

## Question Title

- Option A
- Option B
- Option C
- Option D
```

**Features:**
- Centered question title
- 4 options in a 2x2 grid layout
- Hover effects on options
- Responsive design
- Clean borders and spacing

**Best for:**
- Standard multiple choice questions
- Questions without code examples
- Questions with short option text

---

## question-content.vue

A split-layout question format with content (code/image) on the left and options in a vertical column on the right.

**Usage:**

```md
---
layout: question-content
---

## Question Title

::content::
```js
// Your code example here
const answer = 42;
```
// Or an image
![Description](./path/to/image.png)

::options::
- Option A
- Option B
- Option C
- Option D
```

**Features:**
- Centered question title at the top
- Left side: Code block or image with styled container
- Right side: 4 options in a vertical list
- Hover effects with slide-right animation
- Equal width columns (50/50 split)
- Scrollable code blocks if content is long

**Best for:**
- Questions about code syntax or structure
- Questions with visual examples
- Questions comparing code patterns
- Questions where context is needed

---

## Examples

### Example 1: Simple Question

```md
---
layout: question
---

## Qué es Front-end?

- El servidor que maneja los datos
- Aquello que el usuario ve y manipula
- La base de datos de la aplicación
- El código del servidor
```

### Example 2: Question with Code

```md
---
layout: question-content
---

## Cuál es la sintaxis correcta de CSS?

::content::
```css
.clase {
  propiedad: valor;
}
```

::options::
- `selector { propiedad: valor; }`
- `selector [propiedad = valor]`
- `propiedad { selector: valor; }`
- `{ selector propiedad valor }`
```

### Example 3: Question with HTML Structure

```md
---
layout: question-content
---

## Cuál es la estructura básica de HTML?

::content::
```html
<!DOCTYPE html>
<html>
  <head>
    <title>Título</title>
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
```

---

## Styling Notes

Both layouts include:
- Semi-transparent backgrounds for options
- Border highlighting on hover
- Smooth transitions
- Responsive padding and spacing
- Code formatting inside options with inline `code` styling
- Mobile-friendly responsive design

The layouts use Tailwind CSS classes and scoped styles for consistent appearance across slides.
