---
theme: ../theme
transition: none
layout: cover
title: Dark Mode
exportFilename: 37-dark-mode
---

# Dark Mode

✏️ 2026-01 ➖ ⏱️ 20 min.

---
layout: cover
---

# ¿Cómo Funciona el Dark Mode?

---
layout: default-y-center
---

## Dos Enfoques

::contents::
**1. Basado en preferencia del sistema (`prefers-color-scheme`)**
- Detecta si el OS del usuario tiene dark mode activado
- No requiere interacción del usuario
- Se actualiza automáticamente si el usuario cambia el tema del sistema

**2. Basado en elección del usuario (toggle manual)**
- El usuario elige el tema en la app
- Se guarda la preferencia en `localStorage`
- Puede anular la preferencia del sistema

**Estrategia recomendada:**
1. Detectar la preferencia del sistema como valor por defecto
2. Ofrecer un toggle manual que lo anule
3. Recordar la elección del usuario en `localStorage`

::header::
Semana 11: CSS Avanzado

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# prefers-color-scheme

---
layout: default-y-center
---

## Media Query de Preferencia de Color

::contents::
```css
/* Definir tokens para el tema claro (por defecto) */
:root {
  --color-fondo:  hsl(0, 0%, 100%);
  --color-texto:  hsl(222, 20%, 10%);
  --color-borde:  hsl(220, 13%, 91%);
  --color-accion: hsl(221, 83%, 53%);
}

/* Sobreescribir tokens para el tema oscuro */
@media (prefers-color-scheme: dark) {
  :root {
    --color-fondo:  hsl(222, 20%, 10%);
    --color-texto:  hsl(210, 40%, 96%);
    --color-borde:  hsl(215, 20%, 25%);
    --color-accion: hsl(221, 83%, 65%); /* un poco más claro en oscuro */
  }
}

/* Los componentes usan los tokens — se actualizan automáticamente */
body {
  background: var(--color-fondo);
  color: var(--color-texto);
}
```

::header::
Semana 11: CSS Avanzado

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Toggle Manual con data-theme

---
layout: default-y-center
---

## Atributo data-theme

::contents::
Para permitir que el usuario cambie el tema manualmente, usamos un atributo en `<html>`.

```css
/* Tema claro por defecto */
:root,
[data-theme="claro"] {
  --color-fondo: hsl(0, 0%, 100%);
  --color-texto: hsl(222, 20%, 10%);
  --color-borde: hsl(220, 13%, 91%);
}

/* Tema oscuro */
[data-theme="oscuro"] {
  --color-fondo: hsl(222, 20%, 10%);
  --color-texto: hsl(210, 40%, 96%);
  --color-borde: hsl(215, 20%, 25%);
}

/* Seguir la preferencia del sistema si no hay elección manual */
@media (prefers-color-scheme: dark) {
  :root:not([data-theme]) {
    --color-fondo: hsl(222, 20%, 10%);
    --color-texto: hsl(210, 40%, 96%);
  }
}
```

::header::
Semana 11: CSS Avanzado

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## El Toggle en JavaScript

::contents::
```js
// Leer preferencia guardada o detectar preferencia del sistema
function getTemaInicial() {
  const guardado = localStorage.getItem('tema');
  if (guardado) return guardado;

  return window.matchMedia('(prefers-color-scheme: dark)').matches
    ? 'oscuro'
    : 'claro';
}

// Aplicar el tema al cargar la página
document.documentElement.setAttribute('data-theme', getTemaInicial());

// Toggle del botón
function toggleTema() {
  const actual = document.documentElement.getAttribute('data-theme');
  const nuevo = actual === 'oscuro' ? 'claro' : 'oscuro';

  document.documentElement.setAttribute('data-theme', nuevo);
  localStorage.setItem('tema', nuevo);

  // Actualizar el botón
  botonTema.setAttribute('aria-label',
    nuevo === 'oscuro' ? 'Cambiar a modo claro' : 'Cambiar a modo oscuro'
  );
}
```

::header::
Semana 11: CSS Avanzado

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Dark Mode en React

---
layout: default-y-center
---

## Implementación con useState y useEffect

::contents::
```jsx
function useTema() {
  const [tema, setTema] = useState(() => {
    // Inicializar desde localStorage o preferencia del sistema
    const guardado = localStorage.getItem('tema');
    if (guardado) return guardado;
    return window.matchMedia('(prefers-color-scheme: dark)').matches
      ? 'oscuro' : 'claro';
  });

  useEffect(() => {
    document.documentElement.setAttribute('data-theme', tema);
    localStorage.setItem('tema', tema);
  }, [tema]);

  const toggleTema = () =>
    setTema(t => t === 'oscuro' ? 'claro' : 'oscuro');

  return { tema, toggleTema };
}

// En el componente
function BotonTema() {
  const { tema, toggleTema } = useTema();
  return (
    <button
      onClick={toggleTema}
      aria-label={tema === 'oscuro' ? 'Cambiar a modo claro' : 'Cambiar a modo oscuro'}
    >
      {tema === 'oscuro' ? '☀️' : '🌙'}
    </button>
  );
}
```

::header::
Semana 11: CSS Avanzado

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Colores para Dark Mode

::contents::
El dark mode no es simplemente invertir colores. Hay principios específicos.

```css
/* ❌ Incorrecto: simplemente invertir */
[data-theme="oscuro"] {
  --color-fondo: black;
  --color-texto: white;
}

/* ✅ Correcto: usar gris muy oscuro, no negro puro */
[data-theme="oscuro"] {
  /* Negro puro (#000) cansa la vista — usa gris oscuro */
  --color-fondo:       hsl(222, 20%, 10%);  /* casi negro */
  --color-fondo-sutil: hsl(222, 20%, 14%);  /* un nivel más claro */
  --color-superficie:  hsl(222, 20%, 18%);  /* cards, paneles */

  /* El blanco puro (#fff) también cansa — usa blanco suave */
  --color-texto:       hsl(210, 40%, 96%);
  --color-texto-sutil: hsl(215, 20%, 65%);

  /* El color de acción puede necesitar ajuste de luminosidad */
  --color-accion:      hsl(221, 83%, 65%); /* más claro para mantener contraste */
}
```

::header::
Semana 11: CSS Avanzado

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Resumen — Dark Mode

::contents::
✅ Usa **CSS Custom Properties** para todos los colores — el dark mode solo cambia los tokens

✅ Usa `prefers-color-scheme` como punto de partida automático

✅ Añade soporte de toggle manual con `data-theme` en `<html>`

✅ Persiste la elección del usuario en `localStorage`

✅ En React, encapsula la lógica en un **custom hook** (`useTema`)

✅ Usa **gris oscuro** (no negro puro) para fondos en dark mode

✅ El color de acción puede necesitar ajustarse para mantener el contraste en dark mode

❌ No uses valores hardcodeados como `color: black` — siempre usa variables

❌ No apliques dark mode solo invirtiendo los colores — el resultado es incómodo

::header::
Semana 11: CSS Avanzado

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# 🎉
