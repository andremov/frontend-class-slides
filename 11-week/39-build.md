---
theme: ../theme
transition: none
layout: cover
title: Build, Deploy y Optimización
exportFilename: 39-build
---

# Build, Deploy y Optimización
## Llevar una app React a producción

✏️ 2026-01 ➖ ⏱️ 60 min.

---
layout: cover
---

# El Proceso de Build

---
layout: default-y-center
---

## ¿Qué Hace el Build?

::contents::
Durante el desarrollo, Vite sirve los archivos como están. En producción, aplica varias transformaciones:

**Bundling** — agrupa todos los módulos JS en uno o pocos archivos.

**Tree shaking** — elimina el código importado que nunca se usa.

**Minificación** — elimina espacios, acorta nombres de variables, reduce el tamaño.

**Hashing** — agrega un hash al nombre de los archivos (`main.a3f9b2.js`) para cache busting.

```bash
# Desarrollo — servidor local con Hot Module Replacement
npm run dev

# Build de producción — genera la carpeta /dist
npm run build

# Preview local del build generado (simula producción)
npm run preview
```

El resultado en `/dist` son archivos estáticos listos para servir desde cualquier CDN o servidor.

::header::
Semana 11: Build

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## La Carpeta dist

::contents::
```bash
npm run build
```

```
dist/
├── index.html                   ← HTML con referencias actualizadas
└── assets/
    ├── index-a3f9b2.js         ← JS bundleado y minificado
    ├── index-7c4d1a.css        ← CSS bundleado y minificado
    └── logo-9e3f2b.svg         ← Assets copiados con hash
```

Vite muestra el tamaño de cada chunk al buildear:

```
dist/assets/index-abc123.js    142.3 kB │ gzip: 46.1 kB
dist/assets/index-def456.css   12.8 kB  │ gzip:  3.2 kB
```

**Regla práctica:** si un chunk supera los 500 kB, considerar code splitting.

::header::
Semana 11: Build

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Variables de Entorno

---
layout: default-y-center
---

## .env e import.meta.env

::contents::
Las variables de entorno permiten configurar la app por entorno sin tocar el código fuente.

```bash
# .env — valores por defecto (todos los entornos)
VITE_API_URL=https://api.ejemplo.com
VITE_APP_VERSION=1.0.0

# .env.development — solo en desarrollo
VITE_API_URL=http://localhost:3000

# .env.production — solo en build de producción
VITE_API_URL=https://api.produccion.com
```

```js
// En el código — acceder con import.meta.env
const apiUrl = import.meta.env.VITE_API_URL;

if (import.meta.env.DEV) {
  console.log('Modo desarrollo');
}
```

**Importante:**
- Las variables deben empezar con `VITE_` para ser expuestas al cliente
- Nunca pongas claves secretas (API keys privadas, contraseñas) en el frontend
- Agrega `.env.local` al `.gitignore`

::header::
Semana 11: Build

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Optimización

---
layout: default-y-center
---

## Code Splitting y Lazy Loading

::contents::
Por defecto, React bundlea toda la app en un archivo. Code splitting divide el bundle por rutas — el usuario solo descarga lo que visita.

```jsx
import { lazy, Suspense } from 'react';
import { Routes, Route } from 'react-router';

// lazy() — carga el componente solo cuando se navega a esa ruta
const Inicio     = lazy(() => import('./pages/Inicio'));
const Productos  = lazy(() => import('./pages/Productos'));
const AdminPanel = lazy(() => import('./pages/AdminPanel'));

function App() {
  return (
    // Suspense muestra el fallback mientras el chunk carga
    <Suspense fallback={<div>Cargando...</div>}>
      <Routes>
        <Route path="/"         element={<Inicio />} />
        <Route path="/productos" element={<Productos />} />
        <Route path="/admin"     element={<AdminPanel />} />
      </Routes>
    </Suspense>
  );
}
```

::header::
Semana 11: Build

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Lighthouse y Core Web Vitals

::contents::
**Core Web Vitals** — métricas de rendimiento de Google que afectan al SEO:

| Métrica | Descripción | Objetivo |
|---|---|---|
| **LCP** | Largest Contentful Paint — cuándo aparece el elemento más grande | < 2.5s |
| **INP** | Interaction to Next Paint — respuesta a interacciones del usuario | < 200ms |
| **CLS** | Cumulative Layout Shift — cuánto salta el layout mientras carga | < 0.1 |

**Lighthouse — herramienta integrada en Chrome DevTools:**
1. DevTools → pestaña Lighthouse
2. "Analyze page load"
3. Puntaje 0–100 en Performance, Accessibility, SEO y Best Practices

**Causas frecuentes de mal rendimiento:**
- Imágenes sin dimensiones definidas → CLS
- Bundle grande sin code splitting → LCP lento
- Fonts bloqueantes en el `<head>` → LCP lento

::header::
Semana 11: Build

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Deploy

---
layout: default-y-center
---

## Opciones de Deploy

::contents::
Una app React buildada es un conjunto de archivos estáticos — cualquier CDN puede servirlos.

| Plataforma | Plan gratuito | Mejor para |
|---|---|---|
| **Vercel** | Sí | React / Next.js — mejor experiencia de desarrollo |
| **Netlify** | Sí | Proyectos estáticos — buen sistema de plugins |
| **GitHub Pages** | Sí | Proyectos open source simples |
| **Cloudflare Pages** | Sí | Alta performance global, sin límites de build |
| **Railway / Render** | Sí (con límites) | Cuando también necesitas un backend |

**Para proyectos del curso:** Vercel es la recomendación — conecta con GitHub y deployea automáticamente en cada push a `main`.

::header::
Semana 11: Build

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Deploy en Vercel

::contents::
**Opción recomendada — conectar el repositorio:**
1. Ir a vercel.com → "Add New Project"
2. Importar el repositorio de GitHub
3. Vercel detecta Vite automáticamente — no requiere configuración
4. Cada `git push` a `main` dispara un nuevo deploy automáticamente

```bash
# Opción alternativa — desde la terminal
npm install -g vercel
vercel login
vercel        # deploy de preview
vercel --prod # deploy a producción
```

**Variables de entorno en Vercel:**
- Dashboard del proyecto → Settings → Environment Variables
- Agregar `VITE_API_URL` con su valor por cada entorno (Production / Preview / Development)

**Preview Deployments:** cada Pull Request recibe una URL propia para revisar antes de mergear a `main`.

::header::
Semana 11: Build

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## CI/CD Básico con GitHub Actions

::contents::
```yaml
# .github/workflows/ci.yml
name: CI

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - uses: actions/setup-node@v4
        with:
          node-version: 20
          cache: 'npm'

      - name: Instalar dependencias
        run: npm ci

      - name: Ejecutar tests
        run: npm test -- --run

      - name: Build
        run: npm run build
        env:
          VITE_API_URL: ${{ secrets.VITE_API_URL }}
```

Este workflow verifica que el build no rompe en cada PR — el deploy a producción lo maneja Vercel automáticamente.

::header::
Semana 11: Build

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Resumen — Build, Deploy y Optimización

::contents::
✅ `npm run build` genera `/dist` con JS/CSS bundleado, minificado y hasheado

✅ Las variables de entorno van en `.env` y se acceden con `import.meta.env.VITE_*`

✅ Usa `React.lazy()` + `<Suspense>` para code splitting por rutas — el usuario descarga solo lo que necesita

✅ Mide el rendimiento con Lighthouse — apunta a > 90 en Performance

✅ Vercel conecta con GitHub y deployea automáticamente en cada push

✅ Cada Pull Request obtiene un Preview Deployment propio para revisar antes de mergear

✅ GitHub Actions permite correr tests y verificar el build en cada PR

❌ No pongas API keys secretas en variables `VITE_*` — son visibles en el bundle del cliente

❌ No deployees sin ejecutar `npm run build` localmente — verifica que el build no tenga errores

::header::
Semana 11: Build

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# 🎉
