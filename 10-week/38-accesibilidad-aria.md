---
theme: ../theme
transition: none
layout: cover
title: ARIA y Navegación por Teclado
exportFilename: 38-accesibilidad-aria
---

# ARIA y Navegación
## por Teclado

✏️ 2026-01 ➖ ⏱️ 25 min.

---
layout: cover
---

# ¿Qué es ARIA?

---
layout: default-y-center
---

## Accessible Rich Internet Applications

::contents::
**ARIA** es un conjunto de atributos HTML que añaden información de accesibilidad cuando el HTML semántico no es suficiente.

**Regla #1 de ARIA:**
> *"Ningún ARIA es mejor que ARIA malo"*

Antes de usar ARIA, pregunta: ¿existe un elemento HTML nativo que haga lo mismo?

```html
<!-- ❌ Usando ARIA innecesariamente -->
<div role="button" aria-pressed="false">Guardar</div>

<!-- ✅ Usando el elemento nativo correcto -->
<button>Guardar</button>
```

**Usa ARIA solo cuando:** estás construyendo componentes personalizados (tabs, dropdowns, modales) que no tienen equivalente HTML nativo.

::header::
Semana 10: Accesibilidad

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Roles ARIA

---
layout: default-y-center
---

## role=""

::contents::
Los roles definen **qué tipo de elemento es** para lectores de pantalla.

```html
<!-- Roles de estructura (ya existen como etiquetas HTML) -->
<div role="main">          → igual que <main>
<div role="navigation">    → igual que <nav>
<div role="banner">        → igual que <header>
<div role="contentinfo">   → igual que <footer>

<!-- Roles de widget — para componentes interactivos personalizados -->
<div role="tab">           → una pestaña
<div role="tabpanel">      → panel de una pestaña
<div role="dialog">        → un modal
<div role="tooltip">       → un tooltip
<div role="alert">         → mensaje de alerta (se anuncia automáticamente)
<div role="status">        → mensaje de estado (se anuncia sutilmente)
```

::header::
Semana 10: Accesibilidad

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Atributos ARIA

---
layout: default-y-center
---

## aria-label y aria-labelledby

::contents::
Proporcionan un nombre accesible cuando el texto visible no es suficiente.

```html
<!-- aria-label: nombre personalizado -->
<button aria-label="Cerrar modal">✕</button>
<button aria-label="Buscar">🔍</button>

<!-- Sin aria-label, el lector diría "✕ botón" o "emoji botón" -->

<!-- aria-labelledby: apunta a otro elemento como etiqueta -->
<h2 id="titulo-modal">Confirmar eliminación</h2>
<div role="dialog" aria-labelledby="titulo-modal">
  ...
</div>

<!-- aria-describedby: descripción adicional -->
<input
  type="password"
  aria-describedby="requisitos-password"
>
<p id="requisitos-password">
  Mínimo 8 caracteres, una mayúscula y un número.
</p>
```

::header::
Semana 10: Accesibilidad

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## aria-hidden, aria-expanded, aria-live

::contents::
```html
<!-- aria-hidden: oculta elementos decorativos del lector de pantalla -->
<span aria-hidden="true">🎉</span>
<svg aria-hidden="true">...</svg>  <!-- icono decorativo -->

<!-- aria-expanded: indica si un elemento está abierto/cerrado -->
<button aria-expanded="false" aria-controls="menu">
  Abrir menú
</button>
<ul id="menu" hidden>...</ul>

<!-- Se actualiza dinámicamente con JS -->
button.setAttribute('aria-expanded', 'true');

<!-- aria-live: anuncia cambios dinámicos sin recargar la página -->
<div aria-live="polite">
  <!-- Cuando el contenido cambie, el lector lo anunciará -->
  Los resultados se actualizarán aquí
</div>

<div aria-live="assertive" role="alert">
  <!-- Para errores urgentes — interrumpe lo que el lector esté diciendo -->
</div>
```

::header::
Semana 10: Accesibilidad

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Navegación por Teclado

---
layout: default-y-center
---

## Teclas de Navegación

::contents::
Los usuarios que no pueden usar mouse dependen del teclado para navegar.

| Tecla | Acción |
|---|---|
| `Tab` | Avanzar al siguiente elemento interactivo |
| `Shift + Tab` | Volver al elemento anterior |
| `Enter` | Activar botones, links, enviar formularios |
| `Espacio` | Activar checkboxes, botones, abrir selects |
| `Flechas ↑↓` | Navegar dentro de grupos (radios, listas, tabs) |
| `Escape` | Cerrar modales, dropdowns, tooltips |
| `Home / End` | Ir al primero / último elemento |

**Prueba básica:** cierra el mouse y navega toda tu página con solo Tab y Enter.

::header::
Semana 10: Accesibilidad

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Focus Visible

::contents::
El indicador de foco muestra qué elemento está activo con el teclado. Es obligatorio tenerlo visible.

```css
/* ❌ NUNCA hagas esto — elimina el foco para todos */
* {
  outline: none;
}

/* ✅ Estilo de foco personalizado y visible */
:focus-visible {
  outline: 2px solid var(--color-accion);
  outline-offset: 2px;
  border-radius: 4px;
}

/* ✅ Estilo diferente para botones */
button:focus-visible {
  box-shadow: 0 0 0 3px hsl(221, 83%, 53%, 0.4);
  outline: none;
}
```

**`:focus-visible`** solo muestra el outline cuando se navega por teclado, no cuando se hace click con el mouse.

::header::
Semana 10: Accesibilidad

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## tabindex

::contents::
Controla si un elemento puede recibir foco por teclado.

```html
<!-- tabindex="0": añade el elemento al orden natural de tabulación -->
<div role="button" tabindex="0">Acción personalizada</div>

<!-- tabindex="-1": puede recibir foco programáticamente, pero no con Tab -->
<div id="primer-campo-modal" tabindex="-1">...</div>
<!-- Útil para mover el foco al abrir un modal -->
<script>
  document.getElementById('primer-campo-modal').focus();
</script>

<!-- ❌ tabindex positivo — evitar, rompe el orden natural de tabulación -->
<button tabindex="3">No hagas esto</button>
```

**Regla práctica:** usa `tabindex="0"` o `tabindex="-1"`. Nunca valores positivos.

::header::
Semana 10: Accesibilidad

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Skip Links

---
layout: default-y-center
---

## Saltar Contenido Repetitivo

::contents::
Los usuarios de teclado deben tabear por toda la navegación en cada página. Los skip links permiten saltar directo al contenido principal.

```html
<!-- Primer elemento del <body> -->
<a href="#contenido-principal" class="skip-link">
  Saltar al contenido principal
</a>

<header>
  <nav><!-- muchos links de navegación --></nav>
</header>

<main id="contenido-principal">
  <!-- El foco salta aquí -->
</main>
```

```css
.skip-link {
  position: absolute;
  top: -100%;    /* Oculto por defecto */
  left: 0;
}
.skip-link:focus {
  top: 0;        /* Visible al enfocar con teclado */
  background: #000;
  color: #fff;
  padding: 8px 16px;
  z-index: 9999;
}
```

::header::
Semana 10: Accesibilidad

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Atajos de Teclado

---
layout: default-y-center
---

## Cmd+K — La Paleta de Comandos

::contents::
La paleta de comandos (command palette) es un input de búsqueda global que agrupa todas las acciones de la app en un solo lugar.

Se activa con `Cmd+K` (Mac) o `Ctrl+K` (Windows/Linux). La usan Figma, Linear, Notion, Vercel, GitHub.

```js
// Escuchar el atajo globalmente
useEffect(() => {
  function handleKeyDown(e) {
    if ((e.metaKey || e.ctrlKey) && e.key === 'k') {
      e.preventDefault();
      abrirPaleta();
    }
  }
  window.addEventListener('keydown', handleKeyDown);
  return () => window.removeEventListener('keydown', handleKeyDown);
}, []);
```

```html
<!-- La paleta es un modal con un input de búsqueda -->
<dialog role="dialog" aria-label="Paleta de comandos">
  <input
    type="search"
    placeholder="Buscar acciones..."
    aria-controls="lista-comandos"
    aria-autocomplete="list"
  />
  <ul id="lista-comandos" role="listbox">
    <li role="option">Ir al Dashboard</li>
    <li role="option">Crear nuevo proyecto</li>
    <li role="option">Configuración</li>
  </ul>
</dialog>
```

::header::
Semana 10: Accesibilidad

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Por Qué Importa la Paleta de Comandos

::contents::
**Para usuarios de teclado:** acceso directo a cualquier acción sin navegar por menús.

**Para usuarios avanzados:** flujo más rápido que usar el mouse.

**Para accesibilidad:** centraliza la navegación en un solo componente bien construido.

```js
// Navegar la lista con flechas — patrón estándar
function handleKeyDown(e) {
  if (e.key === 'ArrowDown') {
    e.preventDefault();
    setSeleccionado(prev => Math.min(prev + 1, comandos.length - 1));
  }
  if (e.key === 'ArrowUp') {
    e.preventDefault();
    setSeleccionado(prev => Math.max(prev - 1, 0));
  }
  if (e.key === 'Enter') {
    ejecutar(comandos[seleccionado]);
  }
  if (e.key === 'Escape') {
    cerrarPaleta();
  }
}
```

**Librerías:** `cmdk` (React), `kbar` (React). No hay que construirlo desde cero.

::header::
Semana 10: Accesibilidad

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Resumen — ARIA y Teclado

::contents::
✅ Prefiere **HTML semántico** sobre ARIA. Úsalo solo cuando sea necesario.

✅ Usa `aria-label` para botones con solo iconos o texto poco descriptivo

✅ Usa `aria-live="polite"` para mensajes dinámicos (resultados de búsqueda, mensajes de éxito)

✅ **Nunca** elimines el outline de foco con `outline: none` sin reemplazarlo

✅ Usa `:focus-visible` para foco estilizado sin afectar la experiencia con mouse

✅ Implementa **skip links** al inicio de la página

✅ Prueba toda la interfaz navegando solo con `Tab` y `Enter`

❌ Evita `tabindex` con valores positivos — rompe el orden de navegación

::header::
Semana 10: Accesibilidad

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# 🎉
