---
theme: ../theme
transition: none
layout: cover
title: Quick Start - React + Vite + Tailwind + Zustand
exportFilename: quick-start-01
---

# Quick Start
## React + Vite + Tailwind + Zustand

✏️ 2026-01 ➖ ⏱️ 10 min.

---
layout: cover
---

# 1. Crear el Proyecto

---
layout: default-y-center
---

## Crear proyecto React + Vite

::contents::

```bash
npm create vite@latest mi-app -- --template react
cd mi-app
git init
git add -A
git commit -m "init: vite + react"
```

Esto genera la estructura base:

```
mi-app/
├── public/
├── src/
│   ├── App.jsx
│   ├── main.jsx
│   └── index.css
├── index.html
├── vite.config.js
└── package.json
```

::header::
Quick Start

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# 2. Instalar Dependencias

---
layout: default-y-center
---

## Tailwind CSS + Zustand

::contents::

```bash
# Tailwind CSS v4
npm install tailwindcss @tailwindcss/vite

# Zustand
npm install zustand
```

```bash
git add -A
git commit -m "deps: tailwind y zustand"
```

::header::
Quick Start

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# 3. Configuración

---
layout: default-y-center
---

## vite.config.js

::contents::

```js
import { defineConfig } from "vite";
import react from "@vitejs/plugin-react";
import tailwindcss from "@tailwindcss/vite";

export default defineConfig({
  plugins: [
    react(),
    tailwindcss(),
  ],
});
```

::header::
Quick Start

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## src/index.css

::contents::

```css
@import "tailwindcss";
```

Solo eso. Tailwind v4 no necesita `tailwind.config.js`.

Asegúrate de que `main.jsx` importa este archivo:

```jsx
import "./index.css";
```

::header::
Quick Start

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## src/store/useCounterStore.js

::contents::

```js
import { create } from "zustand";

export const useCounterStore = create((set) => ({
  count: 0,
  increment: () => set((state) => ({ count: state.count + 1 })),
  decrement: () => set((state) => ({ count: state.count - 1 })),
  reset: () => set({ count: 0 }),
}));
```

Zustand no necesita providers ni contextos — se importa y se usa directamente.

::header::
Quick Start

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## src/App.jsx

::contents::

```jsx
import { useCounterStore } from "./store/useCounterStore";

function App() {
  const { count, increment, decrement, reset } = useCounterStore();

  return (
    <div className="min-h-screen flex flex-col items-center justify-center gap-4">
      <h1 className="text-4xl font-bold">Contador: {count}</h1>
      <div className="flex gap-2">
        <button onClick={decrement} className="px-4 py-2 bg-red-500 text-white rounded">
          -1
        </button>
        <button onClick={reset} className="px-4 py-2 bg-gray-500 text-white rounded">
          Reset
        </button>
        <button onClick={increment} className="px-4 py-2 bg-green-500 text-white rounded">
          +1
        </button>
      </div>
    </div>
  );
}

export default App;
```

::header::
Quick Start

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Correr y verificar

::contents::

```bash
npm run dev
```

Abre `http://localhost:5173` y verifica que:

- ✅ Los estilos de Tailwind se aplican
- ✅ El contador funciona con Zustand
- ✅ Hot reload funciona al editar

```bash
git add -A
git commit -m "feat: setup tailwind + zustand"
```

¡Listo! Proyecto configurado y funcionando. 🚀

::header::
Quick Start

::footer::
{{ $page }} / {{ $nav.total }}
