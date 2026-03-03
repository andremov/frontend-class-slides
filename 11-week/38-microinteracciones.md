---
theme: ../theme
transition: none
layout: cover
title: Microinteracciones y Animación
exportFilename: 38-microinteracciones
---

# Microinteracciones
## y Animación CSS

✏️ 2026-01 ➖ ⏱️ 25 min.

---
layout: cover
---

# ¿Qué son las Microinteracciones?

---
layout: default-y-center
---

## Definición

::contents::
Una **microinteracción** es una animación pequeña y específica que da **feedback** al usuario sobre una acción o estado.

**Ejemplos cotidianos:**
- El botón de "like" que rebota al hacer click
- El checkbox que hace un tick animado al marcar
- El menú hamburguesa que transforma sus líneas en una ✕
- El input que se sacude cuando la contraseña es incorrecta
- El botón de enviar que muestra un spinner mientras carga

**¿Por qué importan?**
- Confirman que el sistema recibió la acción
- Hacen la interfaz sentir viva y responsiva
- Comunican cambios de estado sin texto
- Mejoran la percepción de calidad del producto

::header::
Semana 11: CSS Avanzado

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# CSS Transitions

---
layout: default-y-center
---

## La Propiedad transition

::contents::
`transition` es la forma más simple de animación — interpola entre dos estados CSS.

```css
/* Sintaxis completa */
transition: [propiedad] [duración] [función-de-tiempo] [retraso];

/* Ejemplos */
.boton {
  background: var(--color-accion);
  transform: scale(1);
  transition: background 0.2s ease, transform 0.15s ease;
}

.boton:hover {
  background: var(--color-accion-hover);
  transform: scale(1.03);
}

/* Transicionar todas las propiedades (con cuidado) */
.card {
  transition: all 0.3s ease;
}

/* Mejor: ser específico — evita transicionar display, visibility, height:auto */
.card {
  transition: box-shadow 0.2s ease, transform 0.2s ease;
}
```

::header::
Semana 11: CSS Avanzado

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Propiedades que se pueden Transicionar

::contents::
```css
/* ✅ Propiedades de alto rendimiento (composited) — usan la GPU */
transform: translateX() translateY() scale() rotate();
opacity: 0 a 1;

/* Usar estas siempre que sea posible — no causan reflow ni repaint */
.menu-lateral {
  transform: translateX(-100%); /* fuera de pantalla */
  transition: transform 0.3s ease;
}
.menu-lateral.abierto {
  transform: translateX(0);
}

/* ⚠️ Propiedades que causan repaint — usar con moderación */
background-color, color, border-color, box-shadow, border-radius

/* ❌ Propiedades que causan reflow — evitar en transiciones */
width, height, padding, margin, top, left, font-size
/* Si necesitas animar height: usa max-height o grid-template-rows */
```

::header::
Semana 11: CSS Avanzado

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# CSS Animations

---
layout: default-y-center
---

## @keyframes

::contents::
`@keyframes` permite animaciones más complejas con múltiples pasos.

```css
/* Definir la animación */
@keyframes aparecer {
  from {
    opacity: 0;
    transform: translateY(8px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* Aplicar la animación */
.card-nueva {
  animation: aparecer 0.3s ease forwards;
}

/* Sintaxis completa */
animation: [nombre] [duración] [timing] [retraso] [iteraciones] [dirección] [fill-mode];

.pulsando {
  animation: pulso 1.5s ease-in-out infinite;
}
```

::header::
Semana 11: CSS Avanzado

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Keyframes con Múltiples Pasos

::contents::
```css
/* Animación de sacudida para error */
@keyframes sacudir {
  0%   { transform: translateX(0); }
  20%  { transform: translateX(-8px); }
  40%  { transform: translateX(8px); }
  60%  { transform: translateX(-6px); }
  80%  { transform: translateX(6px); }
  100% { transform: translateX(0); }
}

.input-error {
  animation: sacudir 0.4s ease;
}

/* Animación de entrada con rebote */
@keyframes entrada-rebote {
  0%   { transform: scale(0.8); opacity: 0; }
  60%  { transform: scale(1.05); opacity: 1; }
  100% { transform: scale(1); }
}

.modal {
  animation: entrada-rebote 0.35s cubic-bezier(0.34, 1.56, 0.64, 1);
}
```

::header::
Semana 11: CSS Avanzado

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Timing Functions

---
layout: default-y-center
---

## Funciones de Tiempo

::contents::
La timing function controla la **velocidad de la animación** a lo largo del tiempo.

```css
/* Funciones predefinidas */
transition: transform 0.3s linear;       /* velocidad constante — mecánico */
transition: transform 0.3s ease;         /* lento → rápido → lento — natural */
transition: transform 0.3s ease-in;      /* lento inicio → rápido final */
transition: transform 0.3s ease-out;     /* rápido inicio → lento final — más natural */
transition: transform 0.3s ease-in-out;  /* lento en ambos extremos */

/* cubic-bezier — control total */
transition: transform 0.3s cubic-bezier(0.4, 0, 0.2, 1); /* Material Design */

/* spring-like (rebote) — solo para entradas */
animation: entrada 0.5s cubic-bezier(0.34, 1.56, 0.64, 1);
/*                                          ^ > 1 crea el efecto de rebote */
```

**Regla práctica:**
- `ease-out` para elementos que **entran** a escena
- `ease-in` para elementos que **salen** de escena
- `ease` para hover y estados interactivos

::header::
Semana 11: CSS Avanzado

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# prefers-reduced-motion

---
layout: default-y-center
---

## Respetar las Preferencias del Usuario

::contents::
Algunos usuarios tienen condiciones vestibulares o sensibilidad a las animaciones. Los OS permiten "Reducir movimiento".

```css
/* Define las animaciones normalmente */
.modal { animation: entrada-rebote 0.35s ease; }
.boton { transition: transform 0.15s ease; }

/* Desactiva o reduce para usuarios que lo piden */
@media (prefers-reduced-motion: reduce) {
  /* Opción 1: eliminar todas las animaciones */
  *,
  *::before,
  *::after {
    animation-duration: 0.01ms !important;
    transition-duration: 0.01ms !important;
  }

  /* Opción 2: reemplazar por algo aceptable */
  .modal {
    animation: aparecer-simple 0.1s ease; /* solo fade, sin movimiento */
  }
}

@keyframes aparecer-simple {
  from { opacity: 0; }
  to   { opacity: 1; }
}
```

::header::
Semana 11: CSS Avanzado

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Rendimiento de Animaciones

::contents::
**Propiedades baratas (GPU) — úsalas sin miedo:**
```css
transform: translate, scale, rotate, skew
opacity
```

**Propiedades costosas (CPU) — evitar en animaciones en loop:**
```css
width, height, padding, margin  /* → reflow (recalcula layout) */
background, color, box-shadow   /* → repaint (redibuja pixels) */
```

**Herramienta para verificar:** Chrome DevTools → Performance → graba una animación y busca "Layout" y "Paint" en exceso.

```css
/* Truco: forzar la GPU para un elemento */
.elemento-animado {
  will-change: transform, opacity;
  /* Úsalo con moderación — consume memoria de GPU */
}
```

::header::
Semana 11: CSS Avanzado

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Resumen — Microinteracciones y Animación

::contents::
✅ Usa `transition` para cambios de estado simples (hover, focus, active)

✅ Usa `@keyframes` para animaciones de entrada, salida o secuencias complejas

✅ Prefiere `transform` y `opacity` — son las propiedades más baratas de animar

✅ Usa `ease-out` para entradas, `ease-in` para salidas

✅ **Siempre** implementa `prefers-reduced-motion: reduce`

✅ Mantén las animaciones cortas: 150–350ms para UI. Solo secuencias narrativas llevan más.

❌ No animes `width`, `height`, `margin`, `padding` en loops — usa `transform: scale` o `max-height`

❌ No uses `will-change` en todos los elementos — solo en los que realmente lo necesitan

❌ Las animaciones deben tener un propósito — no animes por decorar

::header::
Semana 11: CSS Avanzado

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# 🎉
