---
theme: ../theme
transition: none
layout: cover
title: Estilos en React
exportFilename: 17-estilos
---

# Estilos en React

✏️ 2026-01 ➖ ⏱️ 45 min.

---
layout: cover
---

# Opciones de Estilos

---
layout: default-y-center
---

## Cómo se aplican estilos en React?

::contents::
Hay varias formas de darle estilo a los componentes. Cada una tiene sus ventajas:

1. **CSS Global** — archivos `.css` importados directamente
2. **CSS Modules** — CSS con scope automático por componente
3. **Estilos inline** — objetos de estilo dentro del JSX
4. **SCSS** — CSS con superpoderes (variables, nesting, mixins)
5. **CSS-in-JS / Styled Components** — CSS escrito en JavaScript
6. **Tailwind CSS** — clases de utilidad directamente en el HTML

> No hay una sola respuesta correcta — depende del proyecto y del equipo.

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## CSS Global

::contents::
La forma más simple: crear un archivo `.css` e importarlo.

```css
/* App.css */
.boton {
  background-color: #e94560;
  color: white;
  padding: 8px 16px;
  border-radius: 8px;
}
```

```jsx
// App.jsx
import './App.css';

function App() {
  return <button className="boton">Clic</button>;
}
```

**Problema:** los estilos son **globales**. Si dos componentes usan `.boton`, comparten el mismo CSS → conflictos de nombres.

> Usar para: reset, variables globales, estilos del `body`. No para componentes específicos.

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: two-cols-centered
---

## CSS Modules

::left::
```css
/* Button.module.css */
.boton {
  background-color: #e94560;
  color: white;
  padding: 8px 16px;
  border-radius: 8px;
}

.boton:hover {
  background-color: #c73652;
}

.botonGrande {
  padding: 12px 24px;
  font-size: 18px;
}
```

::right::
```jsx
// Button.jsx
import styles from './Button.module.css';

function Button({ grande, texto }) {
  return (
    <button
      className={grande ? styles.botonGrande : styles.boton}
    >
      {texto}
    </button>
  );
}
```

**Ventajas:**
- Los nombres de clase se vuelven únicos automáticamente: `.boton` → `.Button_boton__x7kR2`
- Sin conflictos entre componentes
- Mismo flujo que CSS normal

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Estilos Inline

::contents::
Pasar un **objeto** de estilos directamente al atributo `style`.

```jsx
// Las propiedades CSS van en camelCase
const estiloBoton = {
  backgroundColor: '#e94560',   // background-color
  color: 'white',
  padding: '8px 16px',
  borderRadius: '8px',           // border-radius
  fontSize: '16px',              // font-size
};

function Button() {
  return <button style={estiloBoton}>Clic</button>;
}

// También se puede pasar directamente (dobles llaves)
function Button2() {
  return <button style={{ color: 'white', padding: '8px' }}>Clic</button>;
}
```

**Útil para:** valores dinámicos basados en props o estado.

**No ideal para:** grandes cantidades de estilos, pseudo-clases (`:hover`), media queries.

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## SCSS

::contents::
SCSS es CSS con superpoderes: nesting, variables, mixins. Vite lo soporta con un solo paquete.

```bash
npm install sass
```

```scss
/* Button.module.scss */
$color-primario: #e94560;

.boton {
  background-color: $color-primario;
  color: white;
  padding: 8px 16px;
  border-radius: 8px;

  /* Nesting — equivale a .boton:hover */
  &:hover {
    background-color: darken($color-primario, 10%);
  }

  /* Variante — .boton--grande */
  &--grande {
    padding: 12px 24px;
    font-size: 18px;
  }
}
```

```jsx
import styles from './Button.module.scss'; // igual que CSS Modules
```

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# CSS-in-JS

---
layout: default-y-center
---

## Qué es CSS-in-JS?

::contents::
Escribir **CSS directamente en JavaScript**, co-ubicado con el componente.

- Los estilos se aplican solo al componente — sin conflictos
- Se pueden usar props y variables de JS en los estilos
- Ejemplos: **Styled Components**, **Emotion**

```bash
npm install styled-components
```

**Ventajas:**
- Estilos y componente en un solo archivo
- Dinámicos por naturaleza (usan props de JS)
- Sin nombres de clase manuales

**Desventajas:**
- Dependencia extra
- Ligero costo de rendimiento (genera CSS en runtime)
- Curva de aprendizaje diferente

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: two-cols-centered
---

## Styled Components

::left::
```jsx
// Button.jsx
import styled from 'styled-components';

// Creas un componente con estilos integrados
const Boton = styled.button`
  background-color: #e94560;
  color: white;
  padding: 8px 16px;
  border-radius: 8px;
  border: none;
  cursor: pointer;

  &:hover {
    background-color: #c73652;
  }
`;

// Variante con props
const BotonGrande = styled(Boton)`
  padding: 12px 24px;
  font-size: 18px;
`;
```

::right::
```jsx
// Uso — igual que cualquier componente
function App() {
  return (
    <>
      <Boton>Normal</Boton>
      <BotonGrande>Grande</BotonGrande>
    </>
  );
}
```

**Estilos dinámicos con props:**

```jsx
const Boton = styled.button`
  background-color: ${(props) =>
    props.primario ? '#e94560' : '#ccc'};
`;

// Uso
<Boton primario>Guardar</Boton>
<Boton>Cancelar</Boton>
```

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Tailwind CSS

---
layout: default-y-center
---

## Qué es Tailwind CSS?

::contents::
Un framework **utility-first**: en lugar de escribir CSS personalizado, usas clases predefinidas directamente en el HTML/JSX.

```jsx
// Sin Tailwind
<button className="boton">Clic</button>
// + archivo CSS separado con .boton { ... }

// Con Tailwind — todo en un lugar
<button className="bg-red-500 text-white px-4 py-2 rounded-lg hover:bg-red-700">
  Clic
</button>
```

**Clases comunes:**
- Colores: `bg-red-500`, `text-white`, `border-gray-200`
- Espaciado: `p-4`, `px-4 py-2`, `m-4`, `gap-4`
- Layout: `flex`, `grid`, `items-center`, `justify-between`
- Tipografía: `text-lg`, `font-bold`, `text-center`
- Bordes: `rounded`, `rounded-lg`, `rounded-full`

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: two-cols-centered
---

## Tailwind en práctica

::left::
**CSS Tradicional**

```css
/* Card.css */
.card {
  background-color: white;
  border-radius: 12px;
  padding: 24px;
  box-shadow: 0 4px 16px rgba(0,0,0,0.08);
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.card-title {
  font-size: 20px;
  font-weight: bold;
  color: #1a1a2e;
}
```

```jsx
import './Card.css';
<div className="card">
  <h3 className="card-title">Hola</h3>
</div>
```

::right::
**Con Tailwind**

```jsx
// No hay archivo CSS separado
<div className="bg-white rounded-xl p-6 shadow-md flex flex-col gap-3">
  <h3 className="text-xl font-bold text-gray-900">
    Hola
  </h3>
</div>
```

**Ventajas:**
- Todo en un lugar
- Sin inventar nombres de clase
- Sin cambiar entre archivos
- Sistema de diseño consistente

**Desventaja:**
- El JSX puede volverse largo con muchas clases

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Instalación de Tailwind (Vite + React)

::contents::
```bash
npm install tailwindcss @tailwindcss/vite
```

Agregar el plugin en **`vite.config.js`**:

```js
import { defineConfig } from 'vite';
import react from '@vitejs/plugin-react';
import tailwindcss from '@tailwindcss/vite';

export default defineConfig({
  plugins: [
    react(),
    tailwindcss(), // 👈 agregar aquí
  ],
});
```

Agregar la directiva en **`src/index.css`** (o el archivo CSS principal):

```css
@import "tailwindcss";
```

¡Listo! Las clases de Tailwind ya están disponibles en todos los componentes.

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Comparativa

::contents::
| Opción | Scope | Configuración | Mejor para |
|--------|-------|--------------|------------|
| CSS Global | Global ⚠️ | Ninguna | Reset / variables base |
| CSS Modules | Por componente ✅ | Ninguna (Vite lo soporta) | Componentes tradicionales |
| Inline styles | Por elemento ✅ | Ninguna | Valores dinámicos puntuales |
| SCSS | Global o módulo | `npm install sass` | Proyectos con diseño complejo |
| Styled Components | Por componente ✅ | `npm install styled-components` | Temas dinámicos con JS |
| **Tailwind CSS** | Por elemento ✅ | Plugin de Vite | **Mayoría de proyectos modernos** |

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Recomendación

::contents::
Para este curso y proyectos nuevos:

**Tailwind CSS** — si quieres velocidad de desarrollo y un sistema de diseño consistente

**CSS Modules** — si prefieres escribir CSS "normal" sin dependencias extra

<br>

**Considera Styled Components** cuando necesites estilos fuertemente dinámicos controlados por JavaScript.

**Usa SCSS** si ya dominas CSS y quieres nesting y variables sin cambiar de paradigma.

**Evita CSS global** para estilos de componentes — reservalo solo para el `body`, fuentes y variables CSS.

<br>

> En la industria: Tailwind es el más adoptado en proyectos nuevos de React (2024–2026).

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}
