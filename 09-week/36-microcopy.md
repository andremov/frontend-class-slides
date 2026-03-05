---
theme: ../theme
transition: none
layout: cover
title: Microcopy y UX Writing
exportFilename: 36-microcopy
---

# Microcopy
## Escritura para Interfaces

✏️ 2026-01 ➖ ⏱️ 20 min.

---
layout: cover
---

# ¿Qué es el Microcopy?

---
layout: default-y-center
---

## Las Palabras que Nadie Nota (Hasta que Están Mal)

::contents::
**Microcopy** es todo el texto de una interfaz que no es contenido principal:
- Etiquetas de botones y links
- Placeholders en inputs
- Mensajes de error y confirmación
- Texto de estados vacíos
- Tooltips y ayudas contextuales

```
❌ Microcopy genérico:        ✅ Microcopy efectivo:
"Submit"                      "Crear cuenta"
"Error"                       "El email ya está registrado"
"Are you sure?"               "¿Eliminar 'proyecto-final'? No se puede deshacer."
"No data"                     "Aún no tienes proyectos. Crea el primero."
"Click here"                  "Ver tutorial de 2 minutos"
```

El microcopy bueno es **invisible**. El malo detiene al usuario.

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Voz Activa

---
layout: default-y-center
---

## Activa vs Pasiva

::contents::
La **voz activa** es directa, corta y más fácil de procesar. La **voz pasiva** suena burocrática y distante.

```
❌ Pasiva:                                ✅ Activa:
"Tu cuenta ha sido creada"               "Cuenta creada"
"El archivo fue eliminado"               "Eliminaste el archivo"
"Los datos serán guardados"              "Guardamos tus datos"
"El formulario debe ser completado"      "Completa el formulario"
"Ha ocurrido un error"                   "Algo salió mal"
```

**Fórmula:** Sujeto → Verbo → Objeto

```
❌ "La imagen no pudo ser cargada por el sistema"
✅ "No pudimos cargar la imagen"

❌ "Se requiere confirmación del correo electrónico"
✅ "Confirma tu correo"
```

Máximo **7 palabras por oración** en mensajes de interfaz. Si necesitas más, divide en dos oraciones.

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Botones y Etiquetas

---
layout: default-y-center
---

## El Botón Dice Qué Pasa al Hacer Click

::contents::
La etiqueta de un botón debe describir la **acción**, no el estado. Usa verbos, no sustantivos.

```
❌ Botones vagos:     ✅ Botones descriptivos:
"OK"                 "Entendido" / "Confirmar" / "Continuar"
"Submit"             "Crear cuenta" / "Enviar mensaje" / "Guardar"
"Cancel"             "Descartar cambios" / "Volver" / "No, mantener"
"Yes" / "No"         "Sí, eliminar" / "No, cancelar"
"Next"               "Siguiente: Método de pago"
```

**Botones destructivos:** describir exactamente qué se destruye.

```html
<!-- ❌ Ambiguo — ¿qué se elimina? -->
<button class="peligro">Eliminar</button>

<!-- ✅ Claro — el usuario sabe exactamente qué pasa -->
<button class="peligro">Eliminar cuenta permanentemente</button>
<button class="peligro">Borrar "proyecto-final.zip"</button>
```

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Placeholders, Errores y Estados Vacíos

::contents::
**Placeholders:** ejemplo de formato, no instrucción — desaparecen al escribir

```html
❌ <input placeholder="Ingrese su correo electrónico aquí">
✅ <input placeholder="nombre@empresa.com">
```

**Errores:** qué pasó + qué hacer

```
❌ "Email inválido"
✅ "Este email no tiene un formato válido. Ejemplo: nombre@empresa.com"

❌ "Contraseña incorrecta"
✅ "La contraseña no coincide. ¿Olvidaste tu contraseña?"
```

**Estados vacíos:** contexto + llamada a la acción

```
❌ "No hay resultados"

✅ "No encontramos proyectos con ese nombre.
    Prueba con otro término o crea un proyecto nuevo."
```

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Resumen — Microcopy

::contents::
✅ Usa **voz activa**: sujeto → verbo → objeto. Máximo 7 palabras por oración.

✅ Los botones describen la **acción** que ocurre al hacer click — usa verbos

✅ Los botones destructivos dicen exactamente **qué se destruye**

✅ Los **placeholders** muestran un ejemplo de formato — no instrucciones, no etiquetas

✅ Los **errores** dicen qué pasó y qué hacer — sin tecnicismos, sin culpar al usuario

✅ Los **estados vacíos** dan contexto y ofrecen un siguiente paso útil

❌ Evita "Submit", "OK", "Cancel", "Click here" — son genéricos y no informan al usuario

❌ No uses el placeholder como reemplazo de `<label>` — desaparece al escribir

::header::
Semana 9: Diseño Web

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# 🎉
