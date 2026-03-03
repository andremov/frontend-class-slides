---
theme: ../theme
transition: none
layout: cover
title: Patrones UX - Formularios
exportFilename: 28-ux-formularios
---

# Patrones UX
## Formularios

✏️ 2026-01 ➖ ⏱️ 25 min.

---
layout: cover
---

# Labels y Placeholders

---
layout: default-y-center
---

## Nunca Reemplaces el Label con Placeholder

::contents::
```html
<!-- ❌ Usando solo placeholder como label -->
<input type="email" placeholder="Correo electrónico">

<!-- Problema: el placeholder desaparece al escribir
     El usuario olvida qué datos tenía que poner -->
```

```html
<!-- ✅ Label siempre visible + placeholder de ejemplo -->
<div class="campo">
  <label for="email">Correo electrónico</label>
  <input
    type="email"
    id="email"
    name="email"
    placeholder="ejemplo@correo.com"
    autocomplete="email"
  >
</div>
```

**El placeholder** sirve para ejemplos o formato esperado — nunca para reemplazar el label.

**¿Por qué?** Los lectores de pantalla no siempre leen el placeholder. Y desaparece al escribir.

::header::
Semana 8: Patrones UX

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Floating Labels

::contents::
Un patrón donde el label comienza como placeholder y flota arriba al escribir.

```css
.campo-flotante {
  position: relative;
}

.campo-flotante input {
  padding: 20px 12px 8px;
  border: 1px solid var(--color-borde);
  border-radius: 6px;
}

.campo-flotante label {
  position: absolute;
  top: 14px;
  left: 12px;
  font-size: 1rem;
  color: var(--color-texto-secundario);
  transition: all 0.2s ease;
  pointer-events: none;
}

/* Cuando el input tiene contenido o está enfocado */
.campo-flotante input:focus + label,
.campo-flotante input:not(:placeholder-shown) + label {
  top: 6px;
  font-size: 0.75rem;
  color: var(--color-accion);
}
```

::header::
Semana 8: Patrones UX

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Validación

---
layout: default-y-center
---

## Cuándo Validar

::contents::
El momento de mostrar los errores importa tanto como el error en sí.

**Estrategias:**

| Cuándo | Cuándo usarla |
|---|---|
| **On submit** | Formularios simples. Valida todo al enviar. |
| **On blur** (al salir del campo) | Recomendado. Valida cuando el usuario termina de escribir en un campo. |
| **On change** (mientras escribe) | Solo para campos con formato estricto (contraseña, código). |
| **No validar en el primer blur** si el campo está vacío | El usuario no ha tenido chance de escribir aún. |

```jsx
const [tocado, setTocado] = useState(false);

<input
  onBlur={() => setTocado(true)}
  onChange={(e) => setValue(e.target.value)}
/>

{/* Solo mostrar el error si el campo fue tocado */}
{tocado && !esValido && <p className="error">{mensajeError}</p>}
```

::header::
Semana 8: Patrones UX

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Mensajes de Error Útiles

::contents::
```html
<!-- ❌ Mensajes genéricos e inútiles -->
<p class="error">Campo inválido</p>
<p class="error">Error en el email</p>
<p class="error">Contraseña incorrecta</p>

<!-- ✅ Mensajes específicos y accionables -->
<p class="error">El email debe incluir "@" y un dominio. Ej: nombre@correo.com</p>
<p class="error">La contraseña debe tener al menos 8 caracteres y un número.</p>
<p class="error">Este usuario ya existe. ¿Quieres iniciar sesión?</p>
```

**Buenas prácticas para errores:**
- Escrito en positivo cuando es posible: "Usa al menos 8 caracteres" mejor que "No puedes usar menos de 8"
- Sin tecnicismos: no pongas códigos de error al usuario
- Con solución: el usuario debe saber qué hacer para corregirlo
- Cercano al campo: justo debajo del input que tiene el error

::header::
Semana 8: Patrones UX

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Posicionamiento de Errores

::contents::
```html
<div class="campo" aria-invalid="true">
  <label for="email">Correo electrónico</label>
  <input
    type="email"
    id="email"
    aria-describedby="error-email"
    aria-invalid="true"
    class="input--error"
  >
  <!-- Error justo debajo del input, vinculado con aria-describedby -->
  <p id="error-email" class="campo__error" role="alert">
    ⚠️ Ingresa un email válido. Ej: nombre@correo.com
  </p>
</div>
```

```css
.input--error {
  border-color: var(--color-error);
  background: hsl(0, 100%, 99%);
}

.campo__error {
  color: var(--color-error);
  font-size: 0.875rem;
  margin-top: 4px;
  display: flex;
  align-items: center;
  gap: 4px;
}
```

::header::
Semana 8: Patrones UX

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Estados de los Campos

---
layout: default-y-center
---

## Los 5 Estados de un Input

::contents::
```css
/* 1. Default — estado normal, sin interacción */
.input { border: 1px solid var(--color-borde); }

/* 2. Focus — el usuario está escribiendo */
.input:focus {
  border-color: var(--color-accion);
  outline: none;
  box-shadow: 0 0 0 3px hsl(221, 83%, 53%, 0.2);
}

/* 3. Filled — tiene contenido pero no está enfocado */
.input:not(:placeholder-shown):not(:focus) {
  border-color: var(--color-borde);
  background: hsl(220, 14%, 98%);
}

/* 4. Error — validación falló */
.input[aria-invalid="true"] { border-color: var(--color-error); }
.input[aria-invalid="true"]:focus {
  box-shadow: 0 0 0 3px hsl(0, 84%, 60%, 0.2);
}

/* 5. Disabled — no interactuable */
.input:disabled {
  background: hsl(220, 14%, 96%);
  color: var(--color-texto-sutil);
  cursor: not-allowed;
}
```

::header::
Semana 8: Patrones UX

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Campos Requeridos

::contents::
```html
<!-- Convención estándar: asterisco (*) para campos requeridos -->
<label for="nombre">
  Nombre completo
  <span class="requerido" aria-hidden="true">*</span>
</label>
<input type="text" id="nombre" required>

<!-- Mejor: indicar los opcionales cuando son minoría -->
<label for="telefono">
  Teléfono
  <span class="opcional">(opcional)</span>
</label>
<input type="tel" id="telefono">
```

```css
.requerido {
  color: var(--color-error);
  margin-left: 2px;
}
.opcional {
  font-size: 0.8em;
  color: var(--color-texto-secundario);
}
```

**Agrega `required` en HTML para validación nativa del navegador como fallback.**

::header::
Semana 8: Patrones UX

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Resumen — Patrones de Formularios

::contents::
✅ **Siempre usa `<label>`** — nunca el placeholder como sustituto

✅ Vincula el label con el input usando `for` / `id`

✅ Valida **al perder el foco** (`onBlur`) — no mientras el usuario escribe

✅ Los mensajes de error deben ser **específicos y accionables**

✅ El error va **justo debajo del campo** que lo causó

✅ Usa `aria-invalid`, `aria-describedby` para conectar errores con el campo

✅ Diseña los **5 estados** del input: default, focus, filled, error, disabled

✅ `required` en el HTML como capa de validación nativa del navegador

❌ No muestres todos los errores al mismo tiempo antes de que el usuario interactúe

❌ No uses mensajes genéricos como "campo inválido"

::header::
Semana 8: Patrones UX

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# 🎉
