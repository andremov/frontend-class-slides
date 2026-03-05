---
theme: ../theme
transition: none
layout: cover
title: Patrones UX - Navegación
exportFilename: 25-ux-navegacion
---

# Patrones UX
## Navegación

✏️ 2026-01 ➖ ⏱️ 25 min.

---
layout: cover
---

# Navegación Principal

---
layout: default-y-center
---

## La Navbar

::contents::
La barra de navegación principal es el punto de partida de todo el sitio.

**Tipos:**
- **Static** — se queda en su lugar al hacer scroll
- **Sticky/Fixed** — se queda pegada al top al hacer scroll
- **Hidden on scroll down / visible on scroll up** — patrón moderno para móvil

```css
/* Sticky navbar */
.navbar {
  position: sticky;
  top: 0;
  z-index: 100;
  background: white;
  /* Sombra sutil para separar del contenido */
  box-shadow: 0 1px 3px hsl(0, 0%, 0%, 0.1);
}
```

**Qué incluir:** logo, links principales, CTA, búsqueda, menú usuario

**Regla:** máximo 5–7 items en la navbar principal.

::header::
Semana 7: Patrones UX

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Menú Hamburguesa (Mobile)

::contents::
```html
<nav class="navbar">
  <a href="/" class="navbar__logo">Mi Sitio</a>

  <!-- Botón hamburguesa — visible solo en móvil -->
  <button
    class="navbar__hamburger"
    aria-expanded="false"
    aria-controls="menu-principal"
    aria-label="Abrir menú de navegación"
  >
    ☰
  </button>

  <!-- Menú — oculto en móvil, visible en desktop -->
  <ul id="menu-principal" class="navbar__menu">
    <li><a href="/sobre-nosotros">Nosotros</a></li>
    <li><a href="/servicios">Servicios</a></li>
    <li><a href="/contacto">Contacto</a></li>
  </ul>
</nav>
```

```css
@media (max-width: 768px) {
  .navbar__menu { display: none; }
  .navbar__menu.abierto { display: flex; flex-direction: column; }
}
```

::header::
Semana 7: Patrones UX

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Breadcrumbs

---
layout: default-y-center
---

## Migas de Pan

::contents::
Los breadcrumbs muestran la ubicación del usuario dentro de la jerarquía del sitio.

```
Inicio > Categoría > Subcategoría > Página actual
```

**Cuándo usar:**
- Sitios con más de 2 niveles de profundidad
- E-commerce, documentación, blogs con categorías

**Cuándo NO usar:**
- Sitios de una sola página o con estructura plana

```html
<nav aria-label="Migas de pan">
  <ol>
    <li><a href="/">Inicio</a></li>
    <li><a href="/productos">Productos</a></li>
    <li><a href="/productos/ropa">Ropa</a></li>
    <li aria-current="page">Camisetas</li>
  </ol>
</nav>
```

`aria-current="page"` indica al lector de pantalla cuál es la página actual.

::header::
Semana 7: Patrones UX

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Tabs

---
layout: default-y-center
---

## Pestañas de Navegación

::contents::
Las tabs organizan contenido relacionado en el mismo espacio.

```html
<div class="tabs" role="tablist" aria-label="Secciones del perfil">
  <button
    role="tab"
    aria-selected="true"
    aria-controls="panel-info"
    id="tab-info"
  >
    Información
  </button>
  <button
    role="tab"
    aria-selected="false"
    aria-controls="panel-actividad"
    id="tab-actividad"
    tabindex="-1"
  >
    Actividad
  </button>
</div>

<div role="tabpanel" id="panel-info" aria-labelledby="tab-info">
  <!-- Contenido de Información -->
</div>
<div role="tabpanel" id="panel-actividad" aria-labelledby="tab-actividad" hidden>
  <!-- Contenido de Actividad -->
</div>
```

::header::
Semana 7: Patrones UX

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Tabs vs Nav Links vs Accordion

::contents::
| Patrón | Cuándo usar |
|---|---|
| **Tabs** | Contenido alternativo en el mismo espacio. Usuario cambia entre vistas |
| **Nav links** | Navegación entre páginas distintas |
| **Accordion** | Lista de secciones colapsables. Útil cuando el usuario quiere leer varias |
| **Steps / Wizard** | Proceso secuencial (checkout, registro multi-paso) |

**Regla de tabs:** usa tabs cuando el usuario solo necesita ver una sección a la vez y el contenido es comparable (ej: info personal / configuración / historial).

❌ No uses tabs para contenido que el usuario probablemente querrá ver todo junto.

✅ Usa accordion en ese caso.

::header::
Semana 7: Patrones UX

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Paginación

---
layout: default-y-center
---

## Tipos de Paginación

::contents::
**Paginación clásica** — páginas numeradas

```html
<nav aria-label="Paginación">
  <a href="?page=1" aria-label="Página anterior">← Anterior</a>
  <a href="?page=1">1</a>
  <span aria-current="page">2</span>
  <a href="?page=3">3</a>
  <a href="?page=3" aria-label="Página siguiente">Siguiente →</a>
</nav>
```

**Infinite scroll** — carga automática al llegar al final
- ✅ Ideal para feeds sociales y exploración
- ❌ Difícil llegar al footer, sin forma de volver a un punto exacto

**"Cargar más" (Load more)** — botón explícito para cargar más
- ✅ El usuario controla cuándo cargar
- ✅ El footer es accesible
- ✅ Se puede compartir la posición exacta con URL

::header::
Semana 7: Patrones UX

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Cuándo Usar Cada Tipo

::contents::
| Tipo | Ideal para | Evitar en |
|---|---|---|
| **Paginación clásica** | Resultados de búsqueda, tablas de datos, e-commerce | Feeds infinitos |
| **Infinite scroll** | Redes sociales, feeds de noticias, exploración casual | Datos con los que el usuario trabaja |
| **Load more** | Blogs, listados de productos, portafolios | Tablas de datos (usa paginación) |

**Tip de accesibilidad para infinite scroll:**

Agrega un botón "Cargar más" como fallback para usuarios que navegan por teclado — el scroll infinito puede ser difícil de usar sin mouse.

::header::
Semana 7: Patrones UX

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Resumen — Patrones de Navegación

::contents::
✅ **Navbar sticky** para sitios con contenido largo — el usuario siempre puede navegar

✅ Usa `aria-expanded` en el botón hamburguesa y actualízalo con JS

✅ **Breadcrumbs** en sitios con más de 2 niveles de profundidad

✅ Usa roles ARIA (`role="tablist"`, `role="tab"`, `role="tabpanel"`) en tabs

✅ **Paginación clásica** para datos estructurados; **infinite scroll** para feeds

✅ El link/botón activo debe estar visualmente diferenciado y usar `aria-current`

❌ No pongas más de 7 items en la navbar principal

❌ No uses infinite scroll en contenido donde el usuario necesita orientarse

::header::
Semana 7: Patrones UX

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# 🎉
