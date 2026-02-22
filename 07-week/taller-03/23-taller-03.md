---
theme: ../../theme
transition: none
layout: cover
title: Taller 03 - React y Data Fetching
exportFilename: 21-taller-03
---

# Taller 03
## React — Data Fetching

✏️ 2026-01

---
layout: default-y-center
---

## Qué hay que hacer?

::contents::
A partir de la **imagen de referencia** que se les suministra, deben recrear la página como una aplicación de **React** usando Vite.

La app debe **consumir una API pública gratuita** para obtener los datos que se muestran en las tarjetas — no se aceptan datos hardcodeados.

::header::
Taller 03

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## La API

::contents::
Deben usar una **API pública gratuita** (sin API key, sin registro).

Algunas opciones sugeridas:

| API | URL | Datos disponibles |
|-----|-----|-------------------|
| REST Countries | `https://restcountries.com/v3.1/all` | Países, banderas, capitales, población |
| PokeAPI | `https://pokeapi.co/api/v2/pokemon?limit=20` | Pokémon, sprites, tipos |
| Open Library | `https://openlibrary.org/search.json?q=programacion` | Libros, autores, portadas |

Pueden proponer cualquier otra API gratuita — con aprobación del profesor.

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

# Iniciar el servidor
npm run dev
```

Limpiar el contenido de `App.jsx` y `App.css` antes de empezar.

::header::
Taller 03

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Paso 2 — Estructura de componentes

::contents::
Crear un archivo `.jsx` por cada componente en la carpeta `src/`:

```
src/
├── App.jsx          ← fetch, estados, filtrado
├── Navbar.jsx
├── SearchBar.jsx    ← input controlado (busqueda)
└── ItemCard.jsx     ← props: imagen, nombre, detalle1, detalle2
```

`App.jsx` ensambla todo y le pasa los datos a los demás componentes.

::header::
Taller 03

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Paso 3 — Fetch y estados

::contents::
Tres estados obligatorios en `App.jsx`:

```jsx
const [datos, setDatos] = useState([]);
const [cargando, setCargando] = useState(true);
const [error, setError] = useState(null);
```

El fetch va dentro de `useEffect` al montar el componente:

```jsx
useEffect(() => {
  async function cargar() {
    try {
      const res = await fetch('https://...');
      const data = await res.json();
      setDatos(data);
    } catch (e) {
      setError('No se pudo cargar la información.');
    } finally {
      setCargando(false);
    }
  }
  cargar();
}, []);
```

Mostrar un mensaje de carga y uno de error en la UI.

::header::
Taller 03

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Paso 4 — Filtrado

::contents::
Agregar un estado `busqueda` y filtrar el array antes de renderizar:

```jsx
const [busqueda, setBusqueda] = useState('');

const datosFiltrados = datos.filter((item) =>
  item.nombre.toLowerCase().includes(busqueda.toLowerCase())
);
```

Pasar `busqueda` y `setBusqueda` como props al componente `<SearchBar />`.

Renderizar `datosFiltrados` en lugar de `datos`.

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

✅ **API pública gratuita** (sin API key)

✅ `useEffect` para el fetch al montar el componente

✅ Estados: `cargando`, `error`, `datos`

✅ UI visible de **loading** y **error**

✅ **Búsqueda/filtrado** funcional en tiempo real

✅ Componentes separados en archivos `.jsx`

❌ No se aceptan datos hardcodeados

❌ No se acepta todo en un solo componente

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
- Similitud visual con la referencia
- Fetch correcto con `useEffect`
- Manejo de estados: loading, error, datos
- Componentes separados en `.jsx`
- Filtrado funcional

::header::
Taller 03

::footer::
{{ $page }} / {{ $nav.total }}
