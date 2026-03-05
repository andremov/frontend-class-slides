---
theme: ../theme
transition: none
layout: cover
title: Jerarquía Visual
exportFilename: 31-jerarquia-visual
---

# Jerarquía Visual

✏️ 2026-01 ➖ ⏱️ 25 min.

---
layout: cover
---

# ¿Qué es la Jerarquía Visual?

---
layout: default-y-center
---

## La Jerarquía Visual

::contents::
Es el principio de organizar elementos visuales para que el ojo del usuario sepa **qué mirar primero, después y al final**.

Sin jerarquía, todo compite por atención al mismo tiempo.

Con jerarquía, guiamos la mirada del usuario a través del contenido de forma intuitiva.

**Las 4 herramientas principales:**
- Tamaño y escala
- Contraste (claro/oscuro)
- Peso tipográfico
- Color

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Sin jerarquía vs Con jerarquía

::contents::
❌ **Sin jerarquía:** todo tiene el mismo peso visual
```css
h1 { font-size: 1rem; font-weight: normal; color: gray; }
h2 { font-size: 1rem; font-weight: normal; color: gray; }
p  { font-size: 1rem; font-weight: normal; color: gray; }
```

✅ **Con jerarquía:** cada nivel tiene un rol claro
```css
h1 { font-size: 2.5rem; font-weight: 700; color: #111; }
h2 { font-size: 1.5rem; font-weight: 600; color: #333; }
p  { font-size: 1rem;   font-weight: 400; color: #555; }
```

El cerebro humano detecta diferencias de tamaño, peso y color instantáneamente.

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Tamaño y Escala

---
layout: default-y-center
---

## Tamaño como Herramienta

::contents::
**Más grande = más importante.** Es la señal visual más fuerte.

```css
/* Escala tipográfica clara */
.titulo-principal { font-size: 3rem; }   /* Lo más importante */
.subtitulo        { font-size: 1.75rem; } /* Secundario */
.encabezado-card  { font-size: 1.25rem; } /* Terciario */
.texto-cuerpo     { font-size: 1rem; }    /* Base */
.nota-pie         { font-size: 0.875rem; }/* Menor importancia */
```

**Regla práctica:** usa al menos un **30% de diferencia** entre niveles para que se sienta como una jerarquía real, no una variación sutil.

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Contraste

---
layout: default-y-center
---

## Contraste Claro/Oscuro

::contents::
El contraste crea **énfasis**. El elemento con más contraste respecto al fondo atrae la mirada primero.

```css
/* Alto contraste = alta prioridad */
.cta-primario {
  background: #111;
  color: #fff;
}

/* Bajo contraste = baja prioridad */
.enlace-secundario {
  color: #888;
}

/* Sin contraste = invisible */
.texto-deshabilitado {
  color: #ccc;
  background: #eee;
}
```

**Uso intencional:** los elementos con menor importancia deben tener menor contraste.

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Peso Tipográfico

---
layout: default-y-center
---

## font-weight como Señal de Importancia

::contents::
El peso tipográfico es una de las herramientas más sutiles y efectivas.

```css
/* Escala de pesos útiles */
.etiqueta-sutil  { font-weight: 300; } /* Light — metadatos, pies de foto */
.cuerpo          { font-weight: 400; } /* Regular — texto normal */
.destacado       { font-weight: 500; } /* Medium — sutil énfasis */
.subtitulo       { font-weight: 600; } /* SemiBold — jerarquía secundaria */
.titulo          { font-weight: 700; } /* Bold — llamadas a la acción */
.hero            { font-weight: 800; } /* ExtraBold — titulares grandes */
```

**Consejo:** no necesitas usar todos los pesos. Elige 2–3 y úsalos consistentemente.

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Color como Herramienta de Jerarquía

---
layout: default-y-center
---

## Dirigir la Atención con Color

::contents::
El color llama la atención antes que el texto. Úsalo con intención.

```css
:root {
  --color-accion:    #2563eb; /* Azul — acciones principales */
  --color-texto:     #111827; /* Casi negro — contenido principal */
  --color-secundario:#6b7280; /* Gris — texto de apoyo */
  --color-sutil:     #d1d5db; /* Gris claro — bordes, separadores */
}

.boton-primario { background: var(--color-accion); }
.texto-apoyo    { color: var(--color-secundario); }
.borde-sutil    { border-color: var(--color-sutil); }
```

**Regla:** un solo color de acción por página. Si todo es azul, nada llama la atención.

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Alineación Óptica

---
layout: default-y-center
---

## Alineación Geométrica vs Óptica

::contents::
**Alineación geométrica:** centrado matemático, calculado por el navegador.

**Alineación óptica:** ajustado manualmente para que *se vea* centrado al ojo humano.

```css
/* Un ícono dentro de un botón — geométricamente centrado */
.boton-icono {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 12px; /* igual en todos los lados */
}

/* Muchos íconos tienen más espacio visual arriba que abajo.
   Compensar con padding asimétrico: */
.boton-icono {
  padding: 11px 12px 13px; /* top menor, bottom mayor */
}
```

El cerebro evalúa el peso visual, no las coordenadas. Un triángulo geométricamente centrado parece estar más abajo de lo que está.

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Casos Comunes de Ajuste Óptico

::contents::
```css
/* 1. Texto en botón — las mayúsculas necesitan más espacio arriba */
.boton {
  padding: 10px 16px 12px; /* fondo ligeramente mayor */
}

/* 2. Ícono junto a texto — los íconos SVG suelen necesitar 1-2px de ajuste */
.icono-con-texto {
  display: flex;
  align-items: center;
  gap: 8px;
}
.icono-con-texto svg {
  position: relative;
  top: 1px; /* corrección óptica frecuente */
}

/* 3. Número dentro de un círculo — el número parece estar alto */
.badge {
  display: flex;
  align-items: center;
  justify-content: center;
  padding-top: 2px; /* compensa el peso visual de la tipografía */
}
```

**Regla:** si algo se ve mal aunque sea matemáticamente correcto, confía en el ojo y ajusta.

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Patrones de Lectura

---
layout: default-y-center
---

## El Patrón F y el Patrón Z

::contents::
Los estudios de seguimiento ocular muestran que los usuarios no leen, **escanean**.

**Patrón F** (páginas de texto denso como noticias o resultados de búsqueda):
```
█████████████████   ← Lee la primera línea completa
█████████           ← Lee parcialmente la segunda
███                 ← Solo el inicio de las líneas siguientes
```

**Patrón Z** (páginas con poco texto como landing pages):
```
█━━━━━━━━━━━━━━░    ← Lee de izquierda a derecha arriba
           ↗         ← Diagonal hacia la izquierda
░━━━━━━━━━━━━━━█    ← Lee de izquierda a derecha abajo
```

**Conclusión:** pon los elementos más importantes en las zonas de mayor atención.

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Aplicando los Patrones

::contents::
**Landing page (Patrón Z):**
- Logo → arriba izquierda
- CTA principal → arriba derecha
- Mensaje clave → centro diagonal
- CTA secundario → abajo derecha

**Artículo / listado (Patrón F):**
- Título → primera línea (se lee completa)
- Información clave → inicio de cada párrafo
- Detalles menos importantes → resto de la línea

```html
<!-- Buen orden de elementos en una card con patrón F -->
<article>
  <h2>Título llamativo</h2>        <!-- línea 1 — se lee completa -->
  <p><strong>Dato clave</strong> y más contexto aquí...</p>  <!-- inicio de línea -->
</article>
```

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Resumen — Las 4 Herramientas

::contents::
| Herramienta | Cómo usarla |
|---|---|
| **Tamaño** | Más grande = más importante. Diferencia mínima 30% entre niveles |
| **Contraste** | Mayor contraste con el fondo = mayor prioridad visual |
| **Peso** | Bold para títulos y acciones, Regular para cuerpo, Light para notas |
| **Color** | Un solo color de acción; gris para contenido secundario |

**Regla de oro:** si todo es grande, negrita y de color → nada tiene jerarquía.

La jerarquía funciona por **contraste entre elementos**, no por el valor absoluto de cada uno.

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# 🎉
