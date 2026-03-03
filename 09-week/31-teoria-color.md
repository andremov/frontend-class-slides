---
theme: ../theme
transition: none
layout: cover
title: Teoría del Color
exportFilename: 31-teoria-color
---

# Teoría del Color

✏️ 2026-01 ➖ ⏱️ 25 min.

---
layout: cover
---

# La Rueda de Color

---
layout: default-y-center
---

## Colores Primarios, Secundarios y Terciarios

::contents::
**Primarios:** rojo, amarillo, azul — no se pueden mezclar para obtenerlos

**Secundarios:** naranja (rojo + amarillo), verde (amarillo + azul), violeta (azul + rojo)

**Terciarios:** mezcla de primario + secundario adyacente

En diseño digital trabajamos con el modelo **RGB** (pantallas emiten luz):
- Rojo + Verde = Amarillo
- Verde + Azul = Cian
- Rojo + Azul = Magenta
- Rojo + Verde + Azul = Blanco

**Herramienta útil:** coolors.co, paletton.com, Adobe Color

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Relaciones de Color

---
layout: default-y-center
---

## Combinaciones Clásicas

::contents::
**Complementarios** — colores opuestos en la rueda. Alto contraste, energía:
```
Azul ↔ Naranja
Rojo ↔ Verde
Amarillo ↔ Violeta
```

**Análogos** — 3 colores adyacentes en la rueda. Armonioso, tranquilo:
```
Azul → Azul-violeta → Violeta
```

**Triádico** — 3 colores equidistantes. Vibrante pero equilibrado:
```
Rojo + Amarillo + Azul
```

**Monocromático** — un solo color en diferentes saturaciones y luminosidades. Elegante y consistente.

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# El Modelo HSL

---
layout: default-y-center
---

## HSL: La Mejor Forma de Trabajar con Color en CSS

::contents::
HSL = **H**ue (tono) + **S**aturation (saturación) + **L**ightness (luminosidad)

```css
color: hsl(220, 90%, 56%);
/*         ^    ^     ^
           |    |     └── Luminosidad: 0% negro → 100% blanco
           |    └──────── Saturación: 0% gris → 100% color puro
           └───────────── Tono: 0-360° en la rueda de color
                          (0=rojo, 120=verde, 240=azul)        */
```

**Por qué HSL es mejor que HEX o RGB para UI:**

```css
/* Crear variantes de un color es intuitivo */
--azul-base:  hsl(220, 90%, 56%);
--azul-claro: hsl(220, 90%, 75%); /* solo cambia L */
--azul-oscuro:hsl(220, 90%, 35%); /* solo cambia L */
--azul-sutil: hsl(220, 30%, 95%); /* solo cambia S y L */
```

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## HSL en la Práctica

::contents::
```css
:root {
  /* Paleta de un solo tono — solo variamos S y L */
  --primary-50:  hsl(221, 100%, 96%); /* fondo sutil */
  --primary-100: hsl(221, 100%, 90%);
  --primary-500: hsl(221, 83%, 53%);  /* color base */
  --primary-600: hsl(221, 83%, 45%);  /* hover */
  --primary-700: hsl(221, 83%, 37%);  /* activo/presionado */
  --primary-900: hsl(221, 83%, 20%);  /* texto oscuro */
}

.boton {
  background: var(--primary-500);
}
.boton:hover {
  background: var(--primary-600);
}
.boton:active {
  background: var(--primary-700);
}
```

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Psicología del Color

---
layout: default-y-center
---

## Asociaciones Culturales del Color

::contents::
| Color | Asociaciones comunes en UI occidental |
|---|---|
| **Azul** | Confianza, tecnología, calma — el más usado en apps |
| **Verde** | Éxito, dinero, salud, naturaleza — ideal para confirmaciones |
| **Rojo** | Peligro, error, urgencia — errores y alertas |
| **Amarillo/Naranja** | Advertencia, energía, acción — warnings y CTAs secundarios |
| **Morado** | Creatividad, lujo, misterio |
| **Negro** | Elegancia, premium, poder |
| **Gris** | Neutral, sutil, deshabilitado |

⚠️ **Importante:** estas asociaciones son culturales y contextuales. No son absolutas.

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# La Regla 60-30-10

---
layout: default-y-center
---

## Distribuyendo los Colores

::contents::
Una fórmula clásica del diseño de interiores que funciona perfectamente en UI:

**60%** — Color dominante (fondo, áreas grandes)
```css
body, .fondo { background: hsl(0, 0%, 98%); } /* casi blanco */
```

**30%** — Color secundario (tarjetas, sidebars, secciones)
```css
.card, .sidebar { background: hsl(220, 15%, 94%); } /* gris azulado */
```

**10%** — Color de acento (botones, links, iconos activos)
```css
.boton-cta, a, .activo { color: hsl(221, 83%, 53%); } /* azul */
```

El 10% de acento es lo que le da vida y personalidad al diseño. Si lo usas más, pierde impacto.

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Paletas con CSS Custom Properties

---
layout: default-y-center
---

## Estructura de una Paleta Completa

::contents::
```css
:root {
  /* Colores semánticos — se usan en componentes */
  --color-texto-principal: hsl(222, 20%, 10%);
  --color-texto-secundario: hsl(222, 10%, 45%);
  --color-texto-sutil: hsl(222, 8%, 65%);

  --color-fondo: hsl(0, 0%, 100%);
  --color-fondo-sutil: hsl(220, 14%, 96%);

  --color-borde: hsl(220, 13%, 91%);

  --color-accion: hsl(221, 83%, 53%);
  --color-accion-hover: hsl(221, 83%, 45%);

  --color-exito: hsl(142, 71%, 45%);
  --color-error: hsl(0, 84%, 60%);
  --color-advertencia: hsl(38, 92%, 50%);
  --color-info: hsl(199, 89%, 48%);
}
```

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Resumen — Color en UI

::contents::
✅ Usa **HSL** para definir colores — es más fácil de ajustar

✅ Define la paleta como **CSS Custom Properties** en `:root`

✅ Aplica la **regla 60-30-10**: dominante, secundario, acento

✅ Usa colores semánticos: `--color-error`, `--color-exito`, `--color-accion`

✅ Elige colores complementarios para crear contraste visual

❌ No uses colores sin un sistema — decide la paleta antes de diseñar

❌ No uses más de 3–4 colores principales

❌ No relies en color como la única forma de comunicar información (accesibilidad)

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# 🎉
