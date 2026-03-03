---
theme: ../theme
transition: none
layout: cover
title: Accesibilidad Visual
exportFilename: 35-accesibilidad-visual
---

# Accesibilidad Visual

✏️ 2026-01 ➖ ⏱️ 20 min.

---
layout: cover
---

# Contraste de Color

---
layout: default-y-center
---

## ¿Qué es el Ratio de Contraste?

::contents::
El **ratio de contraste** mide la diferencia de luminosidad entre el color del texto y el color del fondo.

**Escala:** 1:1 (sin contraste — idénticos) hasta 21:1 (contraste máximo — negro sobre blanco)

**Requisitos WCAG AA (mínimo recomendado):**

| Tipo de texto | Ratio mínimo |
|---|---|
| Texto normal (< 18pt o 14pt bold) | **4.5:1** |
| Texto grande (≥ 18pt o 14pt bold) | **3:1** |
| Componentes UI e imágenes | **3:1** |

**Requisitos WCAG AAA (óptimo):**
- Texto normal: **7:1**
- Texto grande: **4.5:1**

::header::
Semana 10: Accesibilidad

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Ejemplos de Contraste

::contents::
```css
/* ✅ Contraste 21:1 — máximo */
color: #000000; background: #ffffff;

/* ✅ Contraste ~7:1 — AAA para texto normal */
color: #1a1a1a; background: #f5f5f5;

/* ✅ Contraste ~4.5:1 — AA para texto normal */
color: #595959; background: #ffffff;

/* ⚠️ Contraste ~3:1 — solo válido para texto grande */
color: #767676; background: #ffffff;

/* ❌ Contraste ~2:1 — insuficiente */
color: #aaaaaa; background: #ffffff;

/* ❌ Trampas comunes */
color: #fff; background: #f0f0f0;  /* blanco sobre gris muy claro */
color: #555; background: #888;     /* dos grises similares */
```

::header::
Semana 10: Accesibilidad

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Herramientas para Verificar Contraste

::contents::
**Online:**
- **WebAIM Contrast Checker** — webaim.org/resources/contrastchecker
- **Accessible Colors** — accessible-colors.com

**En el navegador:**
- Chrome DevTools → Inspector → coloca el cursor sobre el color en CSS → aparece el ratio de contraste

**En VS Code:**
- La extensión **axe Accessibility Linter** marca colores con contraste insuficiente

**Tip de flujo de trabajo:**
```css
/* Usa HSL para ajustar el contraste fácilmente */
/* Si el ratio es insuficiente, baja la L del texto o sube la L del fondo */
color: hsl(0, 0%, 40%);   /* ratio insuficiente */
color: hsl(0, 0%, 25%);   /* baja L → más oscuro → más contraste ✅ */
```

::header::
Semana 10: Accesibilidad

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# No Depender Solo del Color

---
layout: default-y-center
---

## Color No es el Único Indicador

::contents::
Aproximadamente el **8% de los hombres** tienen algún tipo de daltonismo (principalmente rojo-verde).

**Regla WCAG:** la información nunca debe transmitirse **solo** mediante color.

```html
<!-- ❌ Solo color para indicar error -->
<input style="border-color: red">

<!-- ✅ Color + icono + texto -->
<div class="campo-error">
  <input aria-invalid="true" aria-describedby="error-email">
  <span id="error-email">
    ⚠️ El email no tiene un formato válido
  </span>
</div>
```

```css
/* ✅ Formulario: usa borde + color + texto de error */
.campo-error input {
  border: 2px solid var(--color-error);
}
.campo-error .mensaje-error {
  color: var(--color-error);
  font-size: 0.875rem;
  margin-top: 4px;
}
```

::header::
Semana 10: Accesibilidad

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Daltonismo — Tipos Principales

::contents::
**Deuteranopia/Deuteranomalía** (más común) — dificultad con el verde

**Protanopia/Protanomalía** — dificultad con el rojo

**Tritanopia** — dificultad con el azul (muy rara)

**Achromatopsia** — no percibe ningún color (extremadamente rara)

**Cómo probar tu diseño:**
- Chrome DevTools → Rendering → Emulate vision deficiencies
- Extensión **Colorblinding** para Chrome

**Diseño seguro para daltonismo:**
- Combina diferencias de color + forma + texto
- Usa iconos junto con el color en gráficas (no solo líneas de colores)
- Evita solo rojo/verde para comunicar éxito/error — agrega un ✅ o ❌

::header::
Semana 10: Accesibilidad

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Tamaño y Zoom

---
layout: default-y-center
---

## Tamaño Mínimo de Texto y Áreas de Click

::contents::
```css
/* ❌ Texto demasiado pequeño */
.nota { font-size: 10px; }

/* ✅ Tamaño base mínimo recomendado */
body { font-size: 1rem; }  /* 16px por defecto del navegador */

/* ✅ Áreas de click/tap mínimas (WCAG 2.5.5) */
button, a, input[type="checkbox"] {
  min-height: 44px;
  min-width: 44px;
  /* O al menos el área de toque debe ser 44x44px */
}
```

**El navegador por defecto usa 16px.** Si defines `font-size: 62.5%` en html para hacer `1rem = 10px`, asegúrate de que el texto de cuerpo sea al menos `1.6rem`.

**Soporte de zoom:**
- Usa `rem` y `em` — se escalan con el zoom del usuario
- Nunca bloquees el zoom con `user-scalable=no` en el viewport

::header::
Semana 10: Accesibilidad

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
Algunos usuarios tienen vestibular disorders u otras condiciones que hacen las animaciones incómodas o peligrosas.

Los sistemas operativos permiten activar "Reducir movimiento" — CSS puede detectarlo.

```css
/* Definir animaciones normalmente */
.boton {
  transition: transform 0.2s ease;
}
.boton:hover {
  transform: scale(1.05);
}

/* Desactivar o reducir para usuarios que lo piden */
@media (prefers-reduced-motion: reduce) {
  .boton {
    transition: none;
  }

  /* O como regla global */
  *,
  *::before,
  *::after {
    animation-duration: 0.01ms !important;
    transition-duration: 0.01ms !important;
  }
}
```

::header::
Semana 10: Accesibilidad

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Resumen — Accesibilidad Visual

::contents::
✅ Contraste mínimo **4.5:1** para texto normal, **3:1** para texto grande

✅ Usa WebAIM Contrast Checker o Chrome DevTools para verificar

✅ **Nunca** uses color como **único** indicador de información

✅ Añade iconos + texto junto al color en estados de error, éxito, advertencia

✅ Respeta `prefers-reduced-motion` para usuarios sensibles a animaciones

✅ Áreas de click mínimas de **44×44px** en móvil

✅ Usa `rem` para que el texto respete el zoom del usuario

❌ Nunca pongas `user-scalable=no` en la meta viewport

❌ No confíes solo en rojo/verde para error/éxito — el 8% de los hombres no los distingue

::header::
Semana 10: Accesibilidad

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# 🎉
