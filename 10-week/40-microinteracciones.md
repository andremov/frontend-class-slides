---
theme: ../theme
transition: none
layout: cover
title: Microinteracciones y Rendimiento Percibido
exportFilename: 40-microinteracciones
---

# Microinteracciones
## y Rendimiento Percibido

✏️ 2026-01 ➖ ⏱️ 25 min.

---
layout: cover
---

# Los 100ms

---
layout: default-y-center
---

## La Regla de los 100ms

::contents::
La investigación de Jakob Nielsen establece tres umbrales de tiempo de respuesta:

| Tiempo | Percepción |
|---|---|
| **< 100ms** | Instantáneo — el sistema reacciona de inmediato |
| **100ms – 1s** | El usuario nota el retraso pero sigue en la tarea |
| **> 1s** | El hilo mental se rompe |
| **> 10s** | El usuario abandona |

**Implicación práctica:** cada interacción visible (hover, click, focus, input) debe tener una respuesta visual en menos de 100ms.

El backend puede tardar más — el frontend decide cómo manejar esa espera con feedback, skeletons y UI optimista.

::header::
Semana 10: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Feedback Inmediato

---
layout: default-y-center
---

## Responder Antes de Tener la Respuesta del Servidor

::contents::
```css
/* Feedback visual inmediato en hover y active */
.boton {
  transition: background-color 80ms ease, transform 80ms ease;
}
.boton:hover  { background-color: var(--color-accion-hover); }
.boton:active { transform: scale(0.97); } /* sensación de click físico */
```

```jsx
// Optimistic UI — actualizar la UI antes de confirmar con el servidor
function BotonLike({ postId, likedInicial }) {
  const [liked, setLiked] = useState(likedInicial);

  async function handleLike() {
    setLiked(!liked); // actualizar de inmediato, sin esperar
    try {
      await api.toggleLike(postId);
    } catch {
      setLiked(liked); // revertir si falla
    }
  }

  return <button onClick={handleLike}>{liked ? '❤️' : '🤍'}</button>;
}
```

**Optimistic UI:** asumir que la acción tendrá éxito y revertir solo si falla.

::header::
Semana 10: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Debounce y Throttle

---
layout: default-y-center
---

## Controlar la Frecuencia de Eventos

::contents::
Algunos eventos disparan decenas de veces por segundo: `scroll`, `resize`, `input`. Ejecutar lógica pesada en cada disparo afecta el rendimiento.

**Debounce:** espera a que el usuario *termine* de hacer algo antes de ejecutar.

```js
// Búsqueda en tiempo real — esperar 300ms después del último keystroke
function useDebouncedValue(value, delay = 300) {
  const [debouncedValue, setDebouncedValue] = useState(value);

  useEffect(() => {
    const timer = setTimeout(() => setDebouncedValue(value), delay);
    return () => clearTimeout(timer); // cancelar si el valor cambia
  }, [value, delay]);

  return debouncedValue;
}

// Uso:
const query = useDebouncedValue(inputValue, 300);
useEffect(() => { buscar(query); }, [query]);
// solo busca cuando el usuario deja de escribir por 300ms
```

**Throttle:** ejecutar máximo una vez cada N milisegundos. Útil para eventos de scroll y resize.

::header::
Semana 10: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Microinteracciones

---
layout: default-y-center
---

## Animaciones que Comunican

::contents::
Una microinteracción es una animación pequeña que confirma una acción, muestra un cambio de estado o guía la atención.

**Duraciones recomendadas:**
```css
/* Feedback inmediato (hover, active, focus) */
transition-duration: 80ms–150ms;

/* Aparición de elementos (modales, toasts, dropdowns) */
transition-duration: 200ms–300ms;

/* Transiciones de página o cambios de contexto grandes */
transition-duration: 300ms–500ms;

/* Nunca más de 500ms — se siente lento */
```

**Easing:**
```css
/* Entradas: empieza rápido, frena al llegar */
transition-timing-function: ease-out;

/* Salidas: empieza despacio, termina rápido */
transition-timing-function: ease-in;

/* Movimientos naturales — la mayoría de los casos */
transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
```

::header::
Semana 10: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Resumen — Microinteracciones

::contents::
✅ Cada interacción visible debe tener respuesta visual en **menos de 100ms**

✅ Da **feedback visual inmediato** en `:hover`, `:active`, `:focus` — sin esperar al servidor

✅ Usa **Optimistic UI** para acciones comunes (likes, guardar, marcar) — revierte si falla

✅ **Debounce** para búsqueda en tiempo real — esperar a que el usuario deje de escribir

✅ **Throttle** para eventos de alta frecuencia (scroll, resize)

✅ Duraciones: 80–150ms para feedback inmediato, 200–300ms para transiciones

✅ Usa `ease-out` para entradas, `ease-in` para salidas

❌ Nunca más de 500ms para animaciones de UI — se siente lento

❌ No animes `width`, `height`, `top`, `left` — causan reflow. Usa `transform` y `opacity`

::header::
Semana 10: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# 🎉
