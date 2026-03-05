---
theme: ../theme
transition: none
layout: cover
title: Patrones UX - Overlays
exportFilename: 29-ux-overlays
---

# Patrones UX
## Overlays

✏️ 2026-01 ➖ ⏱️ 25 min.

---
layout: cover
---

# Modales

---
layout: default-y-center
---

## ¿Qué es un Modal?

::contents::
Un modal es una ventana que aparece sobre el contenido y **requiere una acción del usuario** antes de continuar.

**Cuándo usar modales:**
- Confirmación de acciones destructivas ("¿Eliminar este archivo?")
- Formularios cortos (login, newsletter, creación rápida)
- Alertas críticas que requieren atención inmediata
- Vista previa de contenido (lightbox de imágenes)

**Cuándo NO usar modales:**
- Para mostrar información que el usuario probablemente ignorará
- Para confirmaciones triviales que interrumpen el flujo
- En móvil para contenido largo — usa una página o drawer

❌ El abuso de modales es uno de los patrones más odiados por los usuarios.

::header::
Semana 8: Patrones UX

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Anatomía de un Modal Accesible

::contents::
```html
<!-- Backdrop (fondo oscuro) -->
<div class="modal-backdrop" aria-hidden="true"></div>

<!-- El modal -->
<dialog
  id="modal-confirmar"
  aria-labelledby="modal-titulo"
  aria-describedby="modal-descripcion"
>
  <h2 id="modal-titulo">Eliminar archivo</h2>
  <p id="modal-descripcion">
    Esta acción no se puede deshacer.
    ¿Estás seguro de que quieres eliminar "documento.pdf"?
  </p>
  <div class="modal__acciones">
    <button class="boton boton--secundario" autofocus>
      Cancelar
    </button>
    <button class="boton boton--peligro">
      Eliminar
    </button>
  </div>
  <button class="modal__cerrar" aria-label="Cerrar modal">✕</button>
</dialog>
```

`<dialog>` es el elemento HTML nativo para modales — úsalo siempre que puedas.

::header::
Semana 8: Patrones UX

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Focus Trap en Modales

::contents::
Cuando un modal está abierto, el foco de teclado **no debe salir del modal**.

```js
function abrirModal(modal) {
  modal.showModal(); // Método nativo de <dialog>

  // <dialog> maneja el focus trap automáticamente
  // y restaura el foco al elemento original al cerrarse
}

// Si no usas <dialog>, implementa focus trap manualmente:
function focusTrap(modal) {
  const focusables = modal.querySelectorAll(
    'button, [href], input, select, textarea, [tabindex]:not([tabindex="-1"])'
  );
  const primero = focusables[0];
  const ultimo = focusables[focusables.length - 1];

  modal.addEventListener('keydown', (e) => {
    if (e.key !== 'Tab') return;
    if (e.shiftKey && document.activeElement === primero) {
      e.preventDefault(); ultimo.focus();
    } else if (!e.shiftKey && document.activeElement === ultimo) {
      e.preventDefault(); primero.focus();
    }
  });
}
```

::header::
Semana 8: Patrones UX

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Drawers

---
layout: default-y-center
---

## Paneles Laterales (Drawers)

::contents::
Un drawer es un panel que desliza desde un lado de la pantalla.

**Cuándo usar drawers vs modales:**

| Modales | Drawers |
|---|---|
| Acciones críticas, confirmaciones | Formularios largos, configuración |
| Contenido corto y enfocado | Contenido que necesita más espacio |
| El usuario debe decidir algo | El usuario puede seguir viendo el contenido |
| Interacción bloqueante | Interacción no completamente bloqueante |

```css
.drawer {
  position: fixed;
  top: 0;
  right: -400px;  /* Fuera de pantalla por defecto */
  width: 400px;
  height: 100%;
  background: white;
  transition: right 0.3s ease;
  z-index: 200;
}

.drawer.abierto {
  right: 0;
}
```

::header::
Semana 8: Patrones UX

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Tooltips y Popovers

---
layout: default-y-center
---

## Tooltips

::contents::
Un tooltip muestra información adicional al pasar el cursor (o hacer foco) sobre un elemento.

**Reglas:**
- Solo texto breve (no interactivo)
- Aparece en hover Y en focus (accesibilidad)
- Desaparece al mover el cursor o perder el foco
- No es obligatorio para usar la interfaz

```html
<button
  aria-label="Ver más información sobre facturación"
  aria-describedby="tooltip-facturacion"
>
  ⓘ
</button>

<div
  role="tooltip"
  id="tooltip-facturacion"
>
  La factura se genera el primer día de cada mes.
</div>
```

```css
[role="tooltip"] {
  position: absolute;
  background: #111;
  color: #fff;
  padding: 6px 10px;
  border-radius: 4px;
  font-size: 0.875rem;
  pointer-events: none;
}
```

::header::
Semana 8: Patrones UX

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Popovers

::contents::
Un popover es como un tooltip pero puede contener contenido interactivo.

```html
<!-- Usando el atributo popover nativo (HTML 2023) -->
<button popovertarget="pop-opciones">
  Opciones ▾
</button>

<div id="pop-opciones" popover>
  <ul>
    <li><button>Editar</button></li>
    <li><button>Duplicar</button></li>
    <li><button>Eliminar</button></li>
  </ul>
</div>
```

```css
/* El popover nativo se posiciona automáticamente */
#pop-opciones {
  border: 1px solid var(--color-borde);
  border-radius: 8px;
  padding: 8px;
  box-shadow: 0 4px 12px hsl(0, 0%, 0%, 0.1);
}
```

**`popover` nativo:** disponible en Chrome 114+, Firefox 125+, Safari 17+. Maneja foco y Escape automáticamente.

::header::
Semana 8: Patrones UX

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: two-cols-centered
---

## Tooltip vs Popover vs Modal

::left::
**Tooltip**
- Solo texto
- Se activa en hover/focus
- No interactivo
- No bloquea la página

**Popover**
- Puede tener botones, listas, formularios simples
- Se activa en click
- Interactivo
- No bloquea la página

::right::
**Modal**
- Contenido complejo, formularios
- Se activa en click
- Completamente interactivo
- **Bloquea el contenido** de fondo
- Requiere acción explícita para cerrar

**Regla:** usa el componente menos intrusivo que resuelva el problema.

::header::
Semana 8: Patrones UX

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Acciones Destructivas

---
layout: default-y-center
---

## Diseñar para la Pérdida de Datos

::contents::
Cuando el usuario puede perder trabajo, la interfaz debe **anticiparse y protegerlo**.

**Las 3 estrategias principales:**

**1. Confirmación antes de la acción**
```jsx
// Solo para acciones verdaderamente irreversibles
<dialog>
  <p>¿Eliminar "proyecto-final.zip"? Esta acción no se puede deshacer.</p>
  <button autofocus>Cancelar</button>   {/* foco por defecto en Cancelar */}
  <button className="peligro">Eliminar</button>
</dialog>
```

**2. Deshacer después de la acción** (preferible)
```jsx
// Más amigable — deja actuar y da opción de revertir
eliminarArchivo(id);
mostrarToast('Archivo eliminado', { accion: 'Deshacer', onClick: restaurar });
```

**3. Guardado automático**
```js
// Evita la pregunta completamente
useEffect(() => {
  const timer = setTimeout(() => guardar(contenido), 1000);
  return () => clearTimeout(timer);
}, [contenido]);
```

::header::
Semana 8: Patrones UX

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Dark Patterns

---
layout: default-y-center
---

## Patrones Oscuros — El Desarrollador es Cómplice

::contents::
Un **dark pattern** es una interfaz diseñada para engañar al usuario para que haga algo que no quiere.

**El problema:** alguien tiene que *escribir* ese código. Ese alguien eres tú.

```html
<!-- Confirm-shaming: hacer sentir mal al usuario por no aceptar -->
<button>Sí, quiero ahorrar dinero</button>
<button class="link-gris">No gracias, prefiero pagar más</button>

<!-- Pre-checked: suscribirlo sin que lo pida -->
<input type="checkbox" checked> Envíame ofertas y promociones

<!-- Roach motel: fácil entrar, difícil salir -->
<!-- Suscribirse: 1 click -->
<!-- Cancelar: buscar en FAQ → llamar a soporte → esperar 30 min -->

<!-- Misdirection: botón de acción visualmente escondido -->
<button class="btn-primario">Aceptar todos</button>
<button class="link-gris-minusculo">Rechazar</button>
```

::header::
Semana 8: Patrones UX

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Por Qué Importa

::contents::
Los dark patterns **funcionan a corto plazo** — aumentan conversiones, reducen cancelaciones.

Pero tienen costo real:
- El usuario eventualmente se da cuenta y pierde confianza
- Daño a la reputación del producto y la empresa
- En la Unión Europea, muchos son **ilegales** bajo GDPR y DSA

**Como desarrollador frontend:**
- Si el diseño que te llega usa un dark pattern, tienes la opción de señalarlo
- "Esto puede violar GDPR" es un argumento técnico, no solo moral
- Un cancel button honesto: **un click, sin fricción, sin culpa**

```html
<!-- ✅ Cancelación honesta -->
<button>Cancelar suscripción</button>
<!-- lleva directo al formulario de cancelación, no a una página de retención -->
```

::header::
Semana 8: Patrones UX

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Resumen — Overlays

::contents::
✅ Usa `<dialog>` HTML nativo para modales — maneja focus trap y Escape automáticamente

✅ Los modales deben poderse cerrar con la tecla **Escape**

✅ El foco debe ir al primer elemento focusable al abrir un modal

✅ Al cerrar el modal, el foco debe volver al **botón que lo abrió**

✅ Usa **drawers** para contenido lateral largo (configuración, filtros)

✅ Los tooltips deben funcionar en **hover y focus** — no solo hover

✅ Usa el componente menos intrusivo: tooltip < popover < drawer < modal

❌ No abuses de modales para información que el usuario no pidió ver

❌ No pongas contenido interactivo en un tooltip — usa popover o modal

::header::
Semana 8: Patrones UX

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# 🎉
