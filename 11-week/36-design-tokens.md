---
theme: ../theme
transition: none
layout: cover
title: Design Systems y Tokens
exportFilename: 36-design-tokens
---

# Design Systems
## y Tokens

✏️ 2026-01 ➖ ⏱️ 25 min.

---
layout: cover
---

# ¿Qué son los Design Tokens?

---
layout: default-y-center
---

## Tokens de Diseño

::contents::
Un **design token** es un valor de diseño (color, tamaño, espaciado) almacenado como una variable con nombre semántico.

```css
/* ❌ Sin tokens — valores hardcodeados en todas partes */
.boton { background: #2563eb; padding: 12px 24px; font-size: 1rem; }
.enlace { color: #2563eb; }
.icono-activo { fill: #2563eb; }

/* Si el azul principal cambia → hay que buscar y reemplazar en todos lados */

/* ✅ Con tokens — el valor vive en un solo lugar */
:root {
  --color-primario: #2563eb;
  --espacio-boton-v: 12px;
  --espacio-boton-h: 24px;
}

.boton { background: var(--color-primario); padding: var(--espacio-boton-v) var(--espacio-boton-h); }
.enlace { color: var(--color-primario); }
.icono-activo { fill: var(--color-primario); }
/* Si cambia el color → solo toco :root */
```

::header::
Semana 11: CSS Avanzado

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Tipos de Tokens

---
layout: default-y-center
---

## Tokens Primitivos vs Semánticos

::contents::
**Tokens primitivos** — el valor en bruto, sin contexto:
```css
:root {
  --azul-500: hsl(221, 83%, 53%);
  --azul-600: hsl(221, 83%, 45%);
  --gris-100: hsl(220, 14%, 96%);
  --rojo-500: hsl(0, 84%, 60%);
}
```

**Tokens semánticos** — el propósito del valor (referencian primitivos):
```css
:root {
  --color-accion:        var(--azul-500);
  --color-accion-hover:  var(--azul-600);
  --color-fondo-sutil:   var(--gris-100);
  --color-error:         var(--rojo-500);
}
```

**Por qué dos capas:**
- Los primitivos definen la paleta completa
- Los semánticos definen el significado → fácil de cambiar el tema sin tocar componentes

::header::
Semana 11: CSS Avanzado

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Tokens de Color, Espaciado y Tipografía

::contents::
```css
:root {
  /* === COLORES === */
  --color-texto:         hsl(222, 20%, 10%);
  --color-texto-sutil:   hsl(222, 10%, 50%);
  --color-fondo:         hsl(0, 0%, 100%);
  --color-fondo-sutil:   hsl(220, 14%, 97%);
  --color-borde:         hsl(220, 13%, 91%);
  --color-accion:        hsl(221, 83%, 53%);
  --color-exito:         hsl(142, 71%, 45%);
  --color-error:         hsl(0, 84%, 60%);

  /* === ESPACIADO (múltiplos de 4) === */
  --espacio-1: 4px;  --espacio-2: 8px;  --espacio-3: 12px;
  --espacio-4: 16px; --espacio-6: 24px; --espacio-8: 32px;

  /* === TIPOGRAFÍA === */
  --texto-sm:   0.875rem;
  --texto-base: 1rem;
  --texto-lg:   1.125rem;
  --texto-xl:   1.25rem;
  --texto-2xl:  1.5rem;
  --texto-4xl:  2.25rem;

  /* === BORDES === */
  --radio-sm: 4px; --radio-md: 8px; --radio-lg: 12px; --radio-full: 9999px;
}
```

::header::
Semana 11: CSS Avanzado

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Design Systems

---
layout: default-y-center
---

## ¿Qué es un Design System?

::contents::
Un **design system** es una colección de componentes reutilizables, tokens de diseño y directrices que mantienen la consistencia visual de un producto.

**Partes de un design system:**
1. **Tokens** — colores, tipografía, espaciado, sombras
2. **Componentes base** — Button, Input, Card, Modal, Badge...
3. **Patterns** — cómo combinar componentes (formularios, tablas, layouts)
4. **Documentación** — guías de uso, principios de diseño

**Ejemplos de design systems públicos:**
- **Material Design** (Google)
- **Carbon** (IBM)
- **Fluent** (Microsoft)
- **Ant Design** (Alibaba)
- **shadcn/ui** (popular en React — código que copias y controlas)

::header::
Semana 11: CSS Avanzado

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Component Libraries para React

::contents::
**shadcn/ui** — El más popular hoy (2025). No es una librería instalable, es código que copiás a tu proyecto.
```bash
npx shadcn@latest init
npx shadcn@latest add button
npx shadcn@latest add dialog
```

**Radix UI** — Primitivos sin estilos, ultra accesibles. shadcn está construido sobre Radix.
```bash
npm install @radix-ui/react-dialog
```

**MUI (Material UI)** — Implementación de Material Design. Muy popular en empresas.
```bash
npm install @mui/material @emotion/react @emotion/styled
```

**Mantine** — Rica en componentes, excelente DX, con hooks de utilidad incluidos.

**Headless UI** (Tailwind Labs) — Sin estilos, con Tailwind CSS.

::header::
Semana 11: CSS Avanzado

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Cuándo Usar una Librería vs Construir Propio

::contents::
| Escenario | Recomendación |
|---|---|
| MVP, startup, tiempo limitado | ✅ Usa una librería (shadcn, Mantine) |
| App interna / dashboard | ✅ Librería + tus tokens encima |
| Producto con identidad visual muy específica | Considera construir sobre Radix (sin estilos) |
| Aprender / portafolio personal | ✅ Construye desde cero — aprenderás más |
| Empresa grande con equipo de diseño | Design system propio a largo plazo |

**Consejo para principiantes:**
Usa shadcn/ui o Mantine en proyectos reales para avanzar rápido. Aprende los fundamentos (tokens, CSS) para no depender ciegamente de la librería.

::header::
Semana 11: CSS Avanzado

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Resumen — Design Tokens y Systems

::contents::
✅ Los design tokens son **variables CSS con nombres semánticos** — centraliza todos los valores de diseño

✅ Usa **dos capas**: tokens primitivos (paleta completa) + tokens semánticos (significado)

✅ Define tu sistema de tokens en `:root` antes de construir componentes

✅ shadcn/ui, Mantine y MUI son opciones sólidas para React — elige según el proyecto

✅ Radix UI para componentes accesibles sin estilos predefinidos

✅ Un design system bien definido hace que toda la app se vea consistente con menos esfuerzo

❌ No hardcodees colores o tamaños directamente en componentes

❌ No crees tokens por cada valor individual — define sistemas (escala de 8px, escala tipográfica)

::header::
Semana 11: CSS Avanzado

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# 🎉
