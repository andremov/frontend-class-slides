---
theme: ../theme
transition: none
layout: cover
title: Espaciado y Espacio Negativo
exportFilename: 32-espaciado
---

# Espaciado
## y Espacio Negativo

✏️ 2026-01 ➖ ⏱️ 20 min.

---
layout: cover
---

# Por Qué Importa el Espacio

---
layout: default-y-center
---

## El Espacio No es "Vacío"

::contents::
Un error muy común en diseñadores novatos: intentar **llenar** todo el espacio disponible.

El espacio en blanco (whitespace o espacio negativo) hace que el contenido respire y sea más fácil de procesar.

❌ **Sin espaciado:**
- Los elementos se sienten amontonados
- El usuario no sabe dónde mirar primero
- Se ve amateur y difícil de leer

✅ **Con espaciado correcto:**
- El contenido respira
- Los grupos de información son claros
- Parece más profesional y confiable
- Facilita la lectura y la comprensión

> *"El espacio en blanco en el diseño es como el silencio en la música."*

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# El Sistema de 8px

---
layout: default-y-center
---

## ¿Por Qué 8?

::contents::
La mayoría de pantallas modernas tienen densidades que son múltiplos de 8 pixels. Además, 8 divide bien en 2 y 4.

**La regla:** todo el espaciado debe ser múltiplo de 8 (o de 4 para valores pequeños).

```
4px  — espaciado mínimo, entre iconos e ícono+texto
8px  — espaciado pequeño, padding interno de chips
12px — entre elementos relacionados
16px — espaciado base, padding de componentes
24px — separación entre componentes
32px — secciones relacionadas
48px — separación entre secciones distintas
64px — secciones de página
96px — espaciado hero/landing
```

**Resultado:** consistencia visual en toda la interfaz.

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Escala de Espaciado en CSS

::contents::
```css
:root {
  --space-1:  4px;
  --space-2:  8px;
  --space-3:  12px;
  --space-4:  16px;
  --space-5:  20px;
  --space-6:  24px;
  --space-8:  32px;
  --space-10: 40px;
  --space-12: 48px;
  --space-16: 64px;
  --space-20: 80px;
  --space-24: 96px;
}

.card { padding: var(--space-6); }
.card + .card { margin-top: var(--space-4); }
.seccion { padding-block: var(--space-16); }
```

**Tip:** Tailwind CSS sigue exactamente este sistema (p-4, p-6, p-8...).

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Padding vs Margin

---
layout: default-y-center
---

## Cuándo Usar Cada Uno

::contents::
```
┌─────────────────────────┐
│  margin (externo)       │
│  ┌───────────────────┐  │
│  │  border           │  │
│  │  ┌─────────────┐  │  │
│  │  │  padding    │  │  │
│  │  │  ┌───────┐  │  │  │
│  │  │  │       │  │  │  │
│  │  │  │content│  │  │  │
│  │  │  └───────┘  │  │  │
│  │  └─────────────┘  │  │
│  └───────────────────┘  │
└─────────────────────────┘
```

**Padding:** espacio *dentro* del componente (afecta el área clicable)

**Margin:** espacio *fuera* del componente (separa de otros elementos)

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: two-cols-centered
---

## Padding vs Margin — Cuándo Usar Cada Uno

::left::
**Usa `padding` para:**
- Espacio interior de botones, cards, inputs
- Separar el contenido del borde del componente
- Hacer el área clicable más grande

```css
.boton {
  padding: 12px 24px;
  /* El click funciona
     en toda esa área */
}

.card {
  padding: 24px;
}
```

::right::
**Usa `margin` para:**
- Separar componentes entre sí
- Empujar un elemento de su contenedor

```css
.card + .card {
  margin-top: 16px;
}

.titulo {
  margin-bottom: 8px;
}

/* Evita margin-top en el
   primer hijo — usa gap
   en el padre con flex/grid */
```

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Espacio y Proximidad

---
layout: default-y-center
---

## La Ley de Proximidad (Gestalt)

::contents::
Los elementos con menos espacio entre ellos se perciben como un grupo.

```css
/* ❌ Espacio uniforme — los grupos no son claros */
.campo { margin: 16px; }

/* ✅ Menos espacio dentro del grupo, más entre grupos */
.grupo-campo {
  margin-bottom: 24px; /* Entre grupos: más espacio */
}

.etiqueta {
  margin-bottom: 4px;  /* Entre label e input: poco espacio */
}

.campo-error {
  margin-top: 4px;     /* Error pegado al input */
  color: var(--color-error);
}
```

**Regla:** el espacio *entre* grupos debe ser mayor que el espacio *dentro* de un grupo.

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Espacio en Tipografía

::contents::
El espaciado en texto también sigue el sistema de 8px.

```css
h1 {
  font-size: 2.25rem;
  line-height: 1.1;
  margin-bottom: 16px; /* --space-4 */
}

h2 {
  font-size: 1.5rem;
  line-height: 1.2;
  margin-top: 40px;    /* --space-10 — sección nueva */
  margin-bottom: 8px;  /* --space-2 — pegado al párrafo */
}

p {
  font-size: 1rem;
  line-height: 1.6;
  margin-bottom: 16px; /* --space-4 */
}

p + p { margin-top: 0; } /* gap ya está en margin-bottom */
```

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Gap en Flexbox y Grid

::contents::
`gap` es la forma moderna de espaciar hijos en flex y grid — sin margin hacks.

```css
/* Antes (con margins en hijos) — frágil */
.lista > * + * { margin-left: 16px; }

/* Ahora (con gap en el padre) — limpio */
.lista {
  display: flex;
  gap: 16px;
}

/* Grid con espaciado diferente en filas y columnas */
.grilla {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 24px 16px; /* row-gap column-gap */
}
```

**Ventaja:** `gap` no aplica en los bordes — no hay margin extra en el primero ni en el último hijo.

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Resumen — Reglas de Espaciado

::contents::
✅ Usa múltiplos de **8px** (o 4px para valores pequeños)

✅ Define tu escala de espaciado como **CSS Custom Properties**

✅ Usa `padding` para espacio interno, `margin` para separar elementos

✅ Usa `gap` en flex/grid en lugar de margins en los hijos

✅ Más espacio *entre* grupos que *dentro* de grupos (ley de proximidad)

✅ Los diseños con más espacio del que parecen necesitar generalmente se ven mejor

❌ No mezcles valores aleatorios (13px, 17px, 22px) — rompe la consistencia

❌ No tengas miedo del espacio en blanco — no es espacio desperdiciado

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# 🎉
