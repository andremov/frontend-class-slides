---
theme: ../../theme
transition: none
layout: cover
title: Taller 03 - React Router y UX
exportFilename: 23-taller-03
---

# Taller 03
## React — Routing, Vistas y Login (UI)

✏️ 2026-01

---
layout: default-y-center
---

## Qué hay que hacer?

::contents::
Deben tomar la **misma referencia visual del Taller 02** y convertirla en una SPA con **múltiples vistas** usando **React Router**.

No deben implementar autenticación real. Solo deben construir la **UI y navegación** de las rutas `/login`, `/cursos`, y `/nosotros`.

Cada seccion original ahora tiene su propia ruta, y `/login` es una nueva ruta.

::header::
Taller 03

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Paso 1 — Crear el proyecto

::contents::
```bash
# Crear el proyecto con Vite
npm create vite@latest taller-03 -- --template react

# Entrar e instalar dependencias
cd taller-03
npm install

# Instalar React Router v7
npm install react-router

# Iniciar el servidor
npm run dev
```

::header::
Taller 03

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Paso 2 — Estructura mínima

::contents::
Crear archivos separados para **views**, **componentes** y **rutas**:

::header::
Taller 03

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Paso 3 — Rutas obligatorias

::contents::
Configurar React Router con estas rutas mínimas:

- `/` → vista principal
- `/cursos`
- `/nosotros`
- `/login` (solo UI)
- `*` → 404

La navegación interna debe usar **`Link` o `NavLink`** (no `<a href>` para rutas internas).

::header::
Taller 03

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Ruta /login (sin lógica real)

::contents::
La vista `/login` debe incluir:

- Título claro
- Formulario visual con email y password
- Botón de "Ingresar"
- Mensaje de ayuda/microcopy (ej: "Solo interfaz, no valida credenciales")

No deben conectar backend ni validar usuario real.

::header::
Taller 03

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## UX/UI esperada (Semana 7)

::contents::
Aplicar criterios de diseño vistos en Semana 7.

::header::
Taller 03

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Requisitos técnicos

::contents::
✅ Proyecto creado con **Vite + React**

✅ Instalación y uso de **`react-router`**

✅ `BrowserRouter` en `main.jsx`

✅ `Routes` + `Route` para cada vista requerida

✅ Ruta `/login` implementada como interfaz (sin auth real)

✅ Ruta `*` para 404

✅ Componentes y vistas en archivos separados `.jsx`

❌ No se acepta todo en un solo componente

❌ No se acepta navegación interna con `<a href>`

::header::
Taller 03

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Entrega

::contents::
📁 **Formato:** Carpeta del proyecto comprimida en `.zip`
*(sin incluir `node_modules`)*

📅 **Fecha límite:** según lo indicado en el aula virtual

📤 **Cómo entregar:** subir el `.zip` al aula virtual

**Criterios de evaluación:**
- Similitud visual con la referencia base (Taller 02)
- Configuración correcta de rutas y navegación
- Ruta `/login` completa a nivel de UI
- Calidad de estructura de componentes/vistas
- Aplicación de criterios UX de Semana 7

::header::
Taller 03

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# 🎉
