---
theme: ../theme
transition: none
layout: cover
title: Error Boundaries
exportFilename: 21-error-boundaries
---

# Error Boundaries
## Manejo de errores en React

✏️ 2026-01 ➖ ⏱️ 30 min.

---
layout: default-y-center
---

## Qué es un Error Boundary?

::contents::
Un **Error Boundary** es un componente que **captura errores en el árbol de componentes** y muestra una UI de respaldo en lugar de explotar toda la aplicación.

Sin error boundary → un error en un componente **derrumba toda la app**.

```
App
├── Navbar        ✅
├── Perfil        💥 Error aquí → toda la pantalla queda en blanco
└── Footer        ✅
```

Con error boundary → solo el componente afectado muestra el error:

```
App
├── Navbar                          ✅
├── <ErrorBoundary>
│    └── Perfil  💥 Error capturado → muestra fallback UI
└── Footer                          ✅
```

::header::
Semana 7: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Qué errores captura (y cuáles no)?

::contents::
**Captura:**
- Errores en `render()`
- Errores en métodos del ciclo de vida
- Errores en constructores de componentes hijo

**No captura:**
- Errores en event handlers (`onClick`, `onChange`, etc.) → usar `try/catch`
- Código asíncrono (`setTimeout`, `fetch`, `async/await`) → manejar con estado
- Errores en el propio Error Boundary
- Server-side rendering

::header::
Semana 7: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Implementación

::contents::
Los Error Boundaries **solo se pueden implementar como class components** — necesitan dos métodos de ciclo de vida especiales:

```jsx
class ErrorBoundary extends React.Component {
  constructor(props) {
    this.state = { hayError: false };
  }

  // Se ejecuta cuando un hijo lanza un error
  static getDerivedStateFromError(error) {
    return { hayError: true }; // Devuelve el nuevo estado → se usa para mostrar el fallback
  }

  // Se ejecuta después de capturar el error
  componentDidCatch(error, info) {
    console.error('Error capturado:', error, info.componentStack);
  }

  render() {
    if (this.state.hayError) return <h2>Algo salió mal.</h2>;
    return this.props.children;
  }
}
```

::header::
Semana 7: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: two-cols-header
---

## Cómo usarlo

::left::
**Envuelve los componentes que pueden fallar:**

```jsx
function App() {
  return (
    <>
      <Navbar />

      <ErrorBoundary>
        <Perfil />
      </ErrorBoundary>

      <ErrorBoundary>
        <ListaProductos />
      </ErrorBoundary>

      <Footer />
    </>
  );
}
```

::right::
**Con un fallback personalizado:**

```jsx
class ErrorBoundary extends React.Component {
  render() {
    if (this.state.hayError) {
      return (
        this.props.fallback ?? (
          <div className="error-box">
            <p>No se pudo cargar este contenido.</p>
          </div>
        )
      );
    }
    return this.props.children;
  }
}

// Uso:
<ErrorBoundary fallback={<p>Error al cargar el perfil.</p>}>
  <Perfil />
</ErrorBoundary>
```

::header::
Semana 7: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Buenas prácticas

::contents::
**Dónde colocar Error Boundaries?**

| Nivel | Cuándo usarlo |
|-------|--------------|
| Toda la app (`<App>`) | Último recurso — muestra un error global |
| Por sección (sidebar, feed, panel) | Aísla secciones independientes |
| Por componente de datos | Cuando el componente puede fallar por datos externos |

**Recomendaciones:**

- Granularidad media — ni uno solo por app ni uno por cada componente
- Siempre mostrar un mensaje útil al usuario (no solo "Error")
- Registrar el error con `componentDidCatch` → herramientas como **Sentry**
- Ofrecer una acción de recuperación: "Reintentar" o "Recargar"

::header::
Semana 7: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# 🎉
