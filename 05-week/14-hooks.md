---
theme: ../theme
transition: none
layout: cover
title: React Hooks
exportFilename: 14-hooks
---

# React Hooks

✏️ 2026-01 ➖ ⏱️ 60 min.

---
layout: default-y-center
---

## Qué son los Hooks?

::contents::
Los **Hooks** son funciones especiales de React que permiten usar características de React dentro de **function components**.

Antes de los hooks (React < 16.8), solo los class components podían tener estado, efectos, etc.

```jsx
// Sin hooks → necesitabas un class component para tener estado
class Contador extends React.Component { ... }

// Con hooks → los function components tienen las mismas capacidades
function Contador() {
  const [cuenta, setCuenta] = useState(0);

  return <button onClick={() => setCuenta(cuenta + 1)}>{cuenta}</button>;
}
```

Los hooks que empiezan con **`use`** son reconocidos por React como hooks.

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Reglas de los Hooks

::contents::
**1. Solo llamarlos en el nivel superior**

```jsx
// ✅ Nivel superior del componente
function MiComponente() {
  const [valor, setValor] = useState(0);
  useEffect(() => { ... }, []);
}

// ❌ Dentro de un if o loop
function MiComponente() {
  if (condicion) {
    const [valor, setValor] = useState(0); // ❌
  }
}
```

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Reglas de los Hooks

::contents::
**2. Solo llamarlos dentro de React function components**

```jsx
// ✅ Dentro de un componente o custom hook
function MiComponente() { const [x] = useState(0); }
function useMiHook() { const [x] = useState(0); }

// ❌ Fuera de un componente
const [x] = useState(0); // ❌ no funciona
```

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# State Hooks

---
layout: default-y-center
---

## useState

::contents::
**Guarda un valor** en un componente entre renders. Cuando el estado cambia, React vuelve a renderizar el componente.

```jsx
import { useState } from 'react';

function Contador() {
  const [cuenta, setCuenta] = useState(0); // valor inicial: 0

  return (
    <div>
      <p>Cuenta: {cuenta}</p>
      <button onClick={() => setCuenta(cuenta + 1)}>+</button>
      <button onClick={() => setCuenta(cuenta - 1)}>-</button>
      <button onClick={() => setCuenta(0)}>Reset</button>
    </div>
  );
}
```

- `cuenta` — el valor actual
- `setCuenta` — función para actualizar el valor
- `useState(0)` — valor inicial (solo se usa en el primer render)

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: two-cols-centered
---

## useReducer

::left::
```jsx
import { useReducer } from 'react';

function reducer(estado, accion) {
  switch (accion.type) {
    case 'incrementar':
      return { cuenta: estado.cuenta + 1 };
    case 'decrementar':
      return { cuenta: estado.cuenta - 1 };
    case 'reset':
      return { cuenta: 0 };
    default:
      return estado;
  }
}
```

::right::
```jsx
function Contador() {
  const [estado, dispatch] = useReducer(reducer, { cuenta: 0 });

  return (
    <div>
      <p>Cuenta: {estado.cuenta}</p>
      <button onClick={() => dispatch({ type: 'incrementar' })}>
        +
      </button>
      <button onClick={() => dispatch({ type: 'decrementar' })}>
        -
      </button>
      <button onClick={() => dispatch({ type: 'reset' })}>
        Reset
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
layout: cover
---

# Effect Hooks

---
layout: default-y-center
---

## useEffect

::contents::
Es el **ciclo de vida** de los function components.

| Array de dependencias | Equivale a |
|---|---|
| `[]` vacío | Corre una vez al montar |
| `[x, y]` con variables | Corre cuando `x` o `y` cambian |
| `return () => {}` | Limpieza al desmontar |

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## useEffect

::contents::
```jsx
function Reloj() {
  const [hora, setHora] = useState(new Date());

  useEffect(() => {
    // Inicia el timer
    const intervalo = setInterval(() => setHora(new Date()), 1000);

    // Limpia el timer
    return () => clearInterval(intervalo);
  }, []); // [] = solo al montar

  return <p>{hora.toLocaleTimeString()}</p>;
}
```

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Ref Hooks

---
layout: default-y-center
---

## useRef

::contents::
**Guarda entre renders** pero cuyo cambio **no hace re-render**.

**1. Referenciar un elemento del DOM**

```jsx
import { useRef } from 'react';

function Formulario() {
  const inputRef = useRef(null);

  function enfocarInput() {
    inputRef.current.focus(); // acceso directo al elemento DOM
  }

  return (
    <>
      <input ref={inputRef} placeholder="Escribe algo..." />
      <button onClick={enfocarInput}>Enfocar</button>
    </>
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

## useRef

::contents::
**2. Guardar un valor sin re-renderizar**

```jsx
function Cronometro() {
  const intervalRef = useRef(null);

  function iniciar() {
    intervalRef.current = setInterval(() => console.log('tick'), 1000);
  }

  function detener() {
    clearInterval(intervalRef.current); // no causa re-render al cambiar
  }
}
```

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Performance Hooks

---
layout: default-y-center
---

## useMemo

::contents::
**Guarda el resultado de un cálculo** para no recalcular en cada render si las dependencias son iguales.

```jsx
import { useState, useMemo } from 'react';

function Lista({ productos, filtro }) {
  // const filtrados = productos.filter(p => p.nombre.includes(filtro));

  const filtrados = useMemo(() => {
    return productos.filter(p => p.nombre.includes(filtro));
  }, [productos, filtro]); // dependencias

  return (
    <ul>
      {filtrados.map(p => <li key={p.id}>{p.nombre}</li>)}
    </ul>
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

## useCallback

::contents::
**Guarda una función** para que no se cree una nueva instancia en cada render.

```jsx
import { useState, useCallback } from 'react';

function Padre() {
  const [cuenta, setCuenta] = useState(0);

  // const handleClick = () => setCuenta(c => c + 1);

  const handleClick = useCallback(() => {
    setCuenta(c => c + 1);
  }, []); // [] → la función nunca cambia

  return (
    <>
      <p>Cuenta: {cuenta}</p>
      <Boton onClick={handleClick} />
    </>
  );
}
```

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: two-cols-centered
---

## useMemo vs useCallback

::left::
**useMemo**

Guarda el **resultado** de una función.

```jsx
// Retorna el valor computado
const total = useMemo(() => {
  return carrito.reduce(
    (sum, item) => sum + item.precio,
    0
  );
}, [carrito]);

// total es un número
console.log(total); // 150
```

::right::
**useCallback**

Guarda la **función** en sí.

```jsx
// Retorna la función memorizada
const handleSubmit = useCallback((e) => {
  e.preventDefault();
  guardarDatos(formData);
}, [formData]);

// handleSubmit es una función
<form onSubmit={handleSubmit}>
```

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Context Hook

---
layout: default-y-center
---

## useContext

::contents::
Crea un **contexto** para tener un sitio donde queda guardado el estado **de la aplicación**.

```jsx
import { createContext, useContext, useState } from 'react';
const TemaContext = createContext('claro');

function App() {
  const [tema, setTema] = useState('claro');
  return (
    <TemaContext.Provider value={tema}>
      <button onClick={() => setTema(t => t === 'claro' ? 'oscuro' : 'claro')}>
        Cambiar tema
      </button>
      <Pagina />
    </TemaContext.Provider>
  );
}

function Tarjeta() {
  const tema = useContext(TemaContext);
  return (
    <div className={`tarjeta tarjeta--${tema}`}>
      Tema actual: {tema}
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

# Custom Hooks

---
layout: default-y-center
---

## Crear tus propios Hooks

::contents::
Un **custom hook** es una función que empieza con `use` y puede llamar otros hooks. Sirve para **reutilizar lógica con estado** entre componentes.

```jsx
// useContador.js — custom hook
import { useState } from 'react';

function useContador(inicial = 0, paso = 1) {
  const [cuenta, setCuenta] = useState(inicial);

  function incrementar() { setCuenta(c => c + paso); }
  function decrementar() { setCuenta(c => c - paso); }
  function reset()       { setCuenta(inicial); }

  return { cuenta, incrementar, decrementar, reset };
}
```

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Crear tus propios Hooks

::contents::
```jsx
// Uso en cualquier componente
function MiContador() {
  const { cuenta, incrementar, decrementar, reset } = useContador(10, 5);

  return (
    <>
      <p>{cuenta}</p>
      <button onClick={decrementar}>-5</button>
      <button onClick={incrementar}>+5</button>
      <button onClick={reset}>Reset</button>
    </>
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

## Resumen de Hooks

::contents::
| Hook | Categoría | Para qué sirve |
|------|-----------|----------------|
| `useState` | Estado | Guardar y actualizar un valor |
| `useReducer` | Estado | Estado complejo con múltiples acciones |
| `useEffect` | Ciclo de vida | Mounting, updating y unmounting del componente |
| `useRef` | Ref | Acceder al DOM / guardar valor sin re-render |
| `useMemo` | Rendimiento | Memorizar el resultado de un cálculo costoso |
| `useCallback` | Rendimiento | Memorizar una función (para props a hijos) |
| `useContext` | Contexto | Leer un contexto sin prop drilling |
| `useXxx` | Custom | Extraer y reutilizar lógica con estado |

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}
