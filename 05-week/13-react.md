---
theme: ../theme
transition: none
layout: cover
title: Fundamentos de React
exportFilename: 13-react
---

# React
## Fundamentos

✏️ 2026-01 ➖ ⏱️ 60 min.

---
layout: default-y-center
---

## Qué es React?

::contents::
- Una **librería** de JavaScript para construir interfaces de usuario
- Desarrollada por **Meta** (Facebook) en 2013
- Basada en **componentes** reutilizables
- La librería de frontend más popular del mundo

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Crear un Proyecto

---
layout: default-y-center
---

## Crear un proyecto con Vite

::contents::
```bash
# Crear el proyecto
npm create vite@latest mi-app -- --template react

# Entrar a la carpeta e instalar dependencias
cd mi-app
npm install

# Iniciar el servidor de desarrollo
npm run dev
```

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Estructura de archivos

::contents::
```
mi-app/
├── index.html          ← Punto de entrada HTML
├── src/
│   ├── main.jsx        ← Monta la app en el DOM
│   ├── App.jsx         ← Componente raíz
│   └── App.css         ← Estilos CSS
└── package.json
```

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Components

---
layout: default-y-center
---

## Qué es un Component?

::contents::
Un componente es una **función o clase de JavaScript** que retorna **JSX** (interfaz de usuario).

- Reutilizables y combinables
- Cada componente maneja su propia lógica y apariencia

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: two-cols-centered
---

## Tipos de componentes

::left::
**Class Components** (antiguo)
```jsx
class Saludo extends React.Component {
  render() {
    return <h1>¡Hola!</h1>;
  }
}
```

- Sintaxis más verbosa
- Se usaban antes de React 16.8

::right::
**Function Components** (moderno)
```jsx
function Saludo() {
  return <h1>¡Hola!</h1>;
}
```

- Más simples y concisos
- La forma estándar hoy en día

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Component sencillo

::contents::
```jsx
// Saludo.jsx
function Saludo() {
  return (
    <div>
      <h1>¡Hola, mundo!</h1>
      <p>Mi primer componente de React.</p>
    </div>
  );
}

export default Saludo;
```

El nombre del componente **siempre empieza con mayúscula**.

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Usando componentes

::contents::
```jsx
// App.jsx
import Saludo from './Saludo';

function App() {
  return (
    <div>
      <Saludo />
      <Saludo />
      <Saludo />
    </div>
  );
}

export default App;
```

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# JSX

---
layout: default-y-center
---

## Qué es JSX?

::contents::
JSX es una sintaxis que permite escribir **HTML dentro de JavaScript**.

```jsx
// Nuestro JSX
const elemento = <h1>¡Hola!</h1>;

// Lo que hace React
const elemento = React.createElement('h1', null, '¡Hola!');
```

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Reglas de JSX

::contents::
**1. Un solo elemento raíz**
```jsx
// ❌ Dos elementos raíz
return <h1>Título</h1><p>Texto</p>

// ✅ Un div los envuelve
return <div><h1>Título</h1><p>Texto</p></div>
```

**2. `className` en vez de `class`**
```jsx
<div className="tarjeta">...</div>
```

**3. Etiquetas siempre cerradas**
```jsx
<img src="foto.jpg" />   <input type="text" />
```

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Expresiones en JSX

::contents::
Usa `{}` para insertar cualquier expresión de JavaScript:

```jsx
function Perfil() {
  const nombre = 'Ana';
  const edad = 25;

  return (
    <div>
      <h2>{nombre}</h2>
      <p>Edad: {edad}</p>
      <p>Nacida en: {2026 - edad}</p>
      <p>{edad >= 18 ? 'Mayor de edad' : 'Menor de edad'}</p>
    </div>
  );
}
```

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Props

---
layout: default-y-center
---

## Qué son los Props?

::contents::
Los **props** son los argumentos que le pasamos a un componente.

- Permiten el flujo de datos de un padre a su hijo
- Son de **solo lectura**
- Permiten hacer componentes **reutilizables y dinámicos**

```jsx
// Padre pasa props → Hijo las recibe
<Tarjeta titulo="React" descripcion="Una librería de JS" version={1} />
```

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: two-cols-centered
---

## Usando Props

::left::
**Padre**:
```jsx
// App.jsx
function App() {
  return (
    <div>
      <Tarjeta
        titulo="React"
        descripcion="Librería de UI"
      />
      <Tarjeta
        titulo="Vite"
        descripcion="Bundler moderno"
      />
    </div>
  );
}
```

::right::
**Hijo**:
```jsx
// Tarjeta.jsx
function Tarjeta(props) {
  const { titulo, descripcion } = props;
  return (
    <div className="tarjeta">
      <h2>{titulo}</h2>
      <p>{descripcion}</p>
    </div>
  );
}

function Tarjeta({ titulo, descripcion }) {
  return (
    <div className="tarjeta">
      <h2>{titulo}</h2>
      <p>{descripcion}</p>
    </div>
  );
}
```

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Props con valores por defecto

::contents::
Se pueden definir valores por defecto usando la sintaxis de parámetros de JavaScript:

```jsx
function Boton({ texto = 'Aceptar', color = 'azul' }) {
  return (
    <button className={color}>
      {texto}
    </button>
  );
}

// Usa los valores por defecto
<Boton />

// Sobreescribe los valores por defecto
<Boton texto="Cancelar" color="rojo" />
```

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# State

---
layout: default-y-center
---

## Qué es el State?

::contents::
El **state** o **estado** es información guardada que puede cambiar con el tiempo.

- Cuando el state cambia → React **vuelve a renderizar** el componente
- Se maneja con el hook `useState`
- Cada componente tiene su **propio state** independiente

```jsx
import { useState } from 'react';
```

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Hook `useState`

::contents::
```jsx
const [valor, setValor] = useState(valorInicial);
//     ↑          ↑                    ↑
//  el dato   función para         valor con el
//  actual    actualizarlo         que empieza
```

```jsx
function Contador() {
  const [cuenta, setCuenta] = useState(0);

  return (
    <div>
      <p>Cuenta: {cuenta}</p>
      <button onClick={() => setCuenta(cuenta + 1)}>
        Incrementar
      </button>
    </div>
  );
}
```

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Actualizando el Estado

::contents::
**Siempre** usa la función setter:

```jsx
const [cuenta, setCuenta] = useState(0);

// ❌ React no detecta el cambio
cuenta = cuenta + 1;

// ✅ React detecta el cambio y re-renderiza el componente
setCuenta(cuenta + 1);
```

React necesita saber que el estado cambió para actualizar lo visual.

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Eventos

---
layout: default-y-center
---

## Manejando Eventos

::contents::
Los eventos en React funcionan igual que en HTML, pero en **camelCase**:

| HTML | React |
|------|-------|
| `onclick` | `onClick` |
| `onchange` | `onChange` |
| `onsubmit` | `onSubmit` |

```jsx
// ✅ Pasas la función como prop
<button onClick={handleClick}>Click</button>

// ❌ Llamas la función inmediatamente al renderizar
<button onClick={handleClick()}>Click</button>
```

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Contador completo

::contents::
```jsx
import { useState } from 'react';

function Contador() {
  const [cuenta, setCuenta] = useState(0);

  function incrementar() {
    setCuenta(cuenta + 1);
  }

  function decrementar() {
    setCuenta(cuenta - 1);
  }

  return (
    <div>
      <button onClick={decrementar}>-</button>
      <span>{cuenta}</span>
      <button onClick={incrementar}>+</button>
    </div>
  );
}
```

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

