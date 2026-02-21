---
theme: ../theme
transition: none
layout: cover
title: Estado Avanzado y Gestión del Estado
exportFilename: 15-estado
---

# Estado Avanzado
## Gestión del Estado

✏️ 2026-01 ➖ ⏱️ 60 min.

---
layout: cover
---

# Diseño de Estado

---
layout: default-y-center
---

## Dónde poner el estado?

::contents::
**Regla:** el estado va en el componente más cercano que lo necesita.

Si **dos componentes** necesitan el mismo dato → subirlo al **padre común**.

```
App  ← 🏠 el estado vive aquí
├── Header  (lee el usuario)
└── Sidebar (lee el usuario)
```

> Esto se llama **lifting state up** (elevar el estado).

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Lifting State Up

::contents::
```jsx
function App() {
  // El estado vive en el padre
  const [texto, setTexto] = useState('');

  return (
    <>
      <CampoTexto valor={texto} onChange={setTexto} />
      <Vista texto={texto} />
    </>
  );
}

function CampoTexto({ valor, onChange }) {
  return <input value={valor} onChange={(e) => onChange(e.target.value)} />;
}

function Vista({ texto }) {
  return <p>Escribiste: {texto}</p>;
}
```

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Prop Drilling

---
layout: default-y-center
---

## Qué es el Prop Drilling?

::contents::
Pasar un prop **a través de múltiples niveles** de componentes para llegar a uno profundo.

```
App  (tiene el usuario)
 └── Sidebar  (no lo usa, pero lo pasa)
      └── Menu  (no lo usa, pero lo pasa)
           └── Avatar  ← solo este lo necesita
```

- `Sidebar` y `Menu` no usan el prop, pero **tienen que recibirlo y pasarlo**.
- A medida que la app crece, esto se vuelve inmanejable.

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: two-cols-centered
---

## En código

::left::
```jsx
function App() {
  const [usuario, setUsuario] = useState('Ana');
  return <Sidebar usuario={usuario} />;
}

function Sidebar({ usuario }) {
  // Sidebar no usa usuario, solo lo pasa
  return <Menu usuario={usuario} />;
}

function Menu({ usuario }) {
  // Menu tampoco lo usa
  return <Avatar usuario={usuario} />;
}

function Avatar({ usuario }) {
  // Solo Avatar lo necesita
  return <img src={usuario.foto} alt={usuario.nombre} />;
}
```

::right::
- `Sidebar` y `Menu` quedan **acoplados** a un dato que no les importa
- Los componentes intermedios **no son reutilizables** fácilmente

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Single Source of Truth

::contents::
**Un solo lugar** tiene el dato "real". Todos los que lo necesitan lo leen desde ahí.

- ✅ Cambiar el dato en un lugar actualiza **todos** los consumidores
- ✅ No hay versiones desincronizadas del mismo dato

**Problema con useState local:**

```
Componente A  [estado: usuario = "Ana"]
Componente B  [estado: usuario = "Ana"]   ← copia separada
```

**Con un estado global compartido:**

```
Store global  [usuario = "Ana"]
├── Componente A  ← lee del store
└── Componente B  ← lee del store
```

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Soluciones al Prop Drilling

---
layout: default-y-center
---

## Context API (nativo de React)

::contents::
React incluye una solución incorporada: el **Context API**.

```jsx
import { createContext, useContext, useState } from 'react';

// 1. Crear el contexto
const UsuarioContext = createContext(null);

// 2. Envolver el árbol con un Provider
function App() {
  const [usuario, setUsuario] = useState('Ana');
  return (
    <UsuarioContext.Provider value={usuario}>
      <Sidebar />  {/* ya no pasa props */}
    </UsuarioContext.Provider>
  );
}

// 3. Consumir en cualquier componente (sin prop drilling)
function Avatar() {
  const usuario = useContext(UsuarioContext);
  return <span>{usuario}</span>;
}
```

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Zustand

::contents::
**Zustand** es una librería ligera para estado global. Más simple que Context para la mayoría de casos.

```bash
npm install zustand
```

```jsx
// store.js
import { create } from 'zustand';

const useStore = create((set) => ({
  usuario: 'Ana',
  setUsuario: (nombre) => set({ usuario: nombre }),

  cuenta: 0,
  incrementar: () => set((s) => ({ cuenta: s.cuenta + 1 })),
  decrementar: () => set((s) => ({ cuenta: s.cuenta - 1 })),
}));

export default useStore;
```

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: two-cols-centered
---

## Usando Zustand en componentes

::left::
```jsx
// store.js
import { create } from 'zustand';

const useStore = create((set) => ({
  cuenta: 0,
  incrementar: () =>
    set((s) => ({ cuenta: s.cuenta + 1 })),
  decrementar: () =>
    set((s) => ({ cuenta: s.cuenta - 1 })),
}));

export default useStore;
```

::right::
```jsx
// Botones.jsx
import useStore from './store';

function Botones() {
  const incrementar = useStore((s) => s.incrementar);
  const decrementar = useStore((s) => s.decrementar);

  return (
    <>
      <button onClick={decrementar}>-</button>
      <button onClick={incrementar}>+</button>
    </>
  );
}

// Display.jsx
function Display() {
  const cuenta = useStore((s) => s.cuenta);
  return <span>{cuenta}</span>;
}
```

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Redux y Redux Toolkit

::contents::
**Redux** es el estándar histórico para estado global. **Redux Toolkit (RTK)** es la forma moderna — mismo modelo (store → action → reducer), mucho menos boilerplate.

```bash
npm install @reduxjs/toolkit react-redux
```

```jsx
// store.js
import { configureStore } from '@reduxjs/toolkit';
import contadorReducer from './contadorSlice';

export const store = configureStore({
  reducer: { contador: contadorReducer },
});
```

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Redux y Redux Toolkit

::contents::
```jsx
// contadorSlice.js
import { createSlice } from '@reduxjs/toolkit';

const contadorSlice = createSlice({
  name: 'contador',
  initialState: { valor: 0 },
  reducers: {
    incrementar: (state) => { state.valor += 1; },
    decrementar: (state) => { state.valor -= 1; },
  },
});

export const { incrementar, decrementar } =
  contadorSlice.actions;
export default contadorSlice.reducer;
```


::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Redux y Redux Toolkit

::contents::
```jsx
// Componente
import { useSelector, useDispatch } from 'react-redux';
import { incrementar, decrementar } from './contadorSlice';

function Contador() {
  const valor = useSelector((s) => s.contador.valor);
  const dispatch = useDispatch();

  return (
    <>
      <p>{valor}</p>
      <button onClick={() => dispatch(decrementar())}>-</button>
      <button onClick={() => dispatch(incrementar())}>+</button>
    </>
  );
}
```

- **`createSlice`** — define estado, acciones y reducer juntos
- **`useSelector`** — leer del store (como `useStore` en Zustand)
- **`useDispatch`** — enviar acciones para modificar el estado

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: two-cols-centered
---

## Context API vs Zustand

::left::
**Context API**

- ✅ Incluido en React (sin instalar nada)
- ✅ Ideal para datos que cambian poco (tema, idioma, sesión)
- ⚠️ Re-renderiza **todos** los consumidores cuando cambia el valor
- ⚠️ Sintaxis más verbosa (createContext, Provider, useContext)

```jsx
// Hay que crear y exportar el contexto,
// envolver el árbol con Provider,
// y consumir con useContext
```

::right::
**Zustand**

- ✅ API muy simple — un solo hook
- ✅ Re-renders selectivos: solo el componente que usa el dato
- ✅ Funciona fuera de componentes (útil para lógica compleja)
- ✅ DevTools integradas
- ⚠️ Dependencia externa (~1KB)

```jsx
// Una línea para leer
const cuenta = useStore((s) => s.cuenta);

// Una línea para escribir
const incrementar = useStore((s) => s.incrementar);
```

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Qué usar y cuándo?

::contents::
| Situación | Solución recomendada |
|-----------|---------------------|
| Solo un componente lo necesita | `useState` local |
| Dos componentes hermanos | Lifting state up (subir al padre) |
| Árbol pequeño / dato que cambia poco | Context API |
| Estado global complejo / muchos consumidores | **Zustand** |
| App grande con múltiples stores | **Zustand** |
| Equipo grande / empresa / código ya usa Redux | **Redux Toolkit** |

<br>

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}
