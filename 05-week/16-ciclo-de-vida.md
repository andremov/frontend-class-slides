---
theme: ../theme
transition: none
layout: cover
title: Ciclo de Vida de un Componente
exportFilename: 16-ciclo-de-vida
---

# Ciclo de Vida
## de un Componente

✏️ 2026-01 ➖ ⏱️ 45 min.

---
layout: default-y-center
---

## Qué es el ciclo de vida?

::contents::
Todo componente de React pasa por **tres fases** durante su existencia:

```
        ┌─────────────┐
        │   MOUNTING  │  ← el componente aparece en pantalla
        └──────┬──────┘
               │
        ┌──────▼──────┐
        │   UPDATING  │  ← cambian sus props o su estado
        └──────┬──────┘
               │
        ┌──────▼──────┐
        │  UNMOUNTING │  ← el componente desaparece de pantalla
        └─────────────┘
```

- **Mounting** — el componente se crea e inserta en el DOM
- **Updating** — el componente se re-renderiza por un cambio
- **Unmounting** — el componente se elimina del DOM

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Class Components
## (para entender el concepto)

---
layout: default-y-center
---

## Métodos del ciclo de vida

::contents::
Los **class components** tienen métodos explícitos para cada fase.

```jsx
class MiComponente extends React.Component {

  // ── MOUNTING ──────────────────────────────────────────
  constructor(props) {
    super(props);
    this.state = { datos: null }; // estado inicial
  }

  componentDidMount() {
    // Se ejecuta UNA VEZ después del primer render
    // Ideal para: llamadas a API, subscripciones, timers
  }

  render() {
    return <div>{this.state.datos}</div>;
  }
}
```

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}


---
layout: default-y-center
---

## Métodos del ciclo de vida

::contents::
```jsx
class MiComponente extends React.Component {

  // ── MOUNTING ──────────────────────────────────────────
  constructor(props) {
    super(props);
    this.state = { datos: null }; // estado inicial
  }
  
  // ── UPDATING ──────────────────────────────────────────
  componentDidUpdate(prevProps, prevState) {
    // Se ejecuta después de cada re-render
    // prevProps y prevState contienen los valores anteriores
  }

  render() {
    return <div>{this.state.datos}</div>;
  }
}
```

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}


---
layout: default-y-center
---

## Métodos del ciclo de vida

::contents::
```jsx
class MiComponente extends React.Component {

  // ── MOUNTING ──────────────────────────────────────────
  constructor(props) {
    super(props);
    this.state = { datos: null }; // estado inicial
  }

  // ── UNMOUNTING ────────────────────────────────────────
  componentWillUnmount() {
    // Se ejecuta justo antes de que el componente desaparezca
    // Ideal para: cancelar timers, cancelar fetches, desuscribirse
  }

  render() {
    return <div>{this.state.datos}</div>;
  }
}
```

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Mounting

::contents::
El componente **aparece en pantalla** por primera vez.

```jsx
class Reloj extends React.Component {
  constructor(props) {
    super(props);
    // 1. Se crea el componente, se inicializa el estado
    this.state = { hora: new Date() };
  }

  componentDidMount() {
    // 3. El componente ya está en el DOM
    this.intervalo = setInterval(() => {
      this.setState({ hora: new Date() });
    }, 1000);
  }

  render() {
    // 2. React llama a render() y pinta el JSX
    return <p>{this.state.hora.toLocaleTimeString()}</p>;
  }
}
```

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Updating

::contents::
El componente **se re-renderiza** porque cambiaron sus props o su estado.

```jsx
class Perfil extends React.Component {
  componentDidUpdate(prevProps, prevState) {
    // Se ejecuta después de cada actualización

    // Comparar con los valores anteriores para evitar loops infinitos
    if (prevProps.usuarioId !== this.props.usuarioId) {
      // El prop cambió → cargar nuevos datos
      this.cargarUsuario(this.props.usuarioId);
    }
  }

  cargarUsuario(id) {
    fetch(`/api/usuarios/${id}`)
      .then(r => r.json())
      .then(datos => this.setState({ datos }));
  }

  render() {
    return <div>{this.state.datos?.nombre}</div>;
  }
}
```

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Unmounting

::contents::
El componente **desaparece del DOM**. Último momento para hacer limpieza.

```jsx
class Reloj extends React.Component {
  componentDidMount() {
    // Inicia el timer al montar
    this.intervalo = setInterval(() => {
      this.setState({ hora: new Date() });
    }, 1000);
  }

  componentWillUnmount() {
    // Limpia el timer al desmontar ← MUY IMPORTANTE
    clearInterval(this.intervalo);
  }

  render() {
    return <p>{this.state.hora?.toLocaleTimeString()}</p>;
  }
}
```

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Unmounting

::contents::
**Por qué limpiar?**

Si no cancelas el timer cuando el componente se desmonta, el timer sigue corriendo en memoria e intenta actualizar el estado de un componente que ya no existe → **memory leak** y errores en consola.

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Function Components
## useEffect como ciclo de vida

---
layout: default-y-center
---

## useEffect reemplaza los tres métodos

::contents::
Los function components no tienen `componentDidMount`, `componentDidUpdate` ni `componentWillUnmount`. En su lugar, **`useEffect` los unifica a todos**:

```jsx
useEffect(() => {
  // Equivale a componentDidMount + componentDidUpdate
  // (cuerpo del efecto)

  return () => {
    // Equivale a componentWillUnmount
    // (función de cleanup)
  };
}, [dependencias]); // controla cuándo se ejecuta
```

El **array de dependencias** es el que determina a cuál método equivale:

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## useEffect reemplaza los tres métodos

::contents::
El **array de dependencias** es el que determina a cuál método equivale:

| Array | Equivale a |
|-------|------------|
| `[]` vacío | `componentDidMount` |
| `[x, y]` con variables | `componentDidUpdate` (cuando x o y cambian) |
| Sin array | Después de **cada** render |
| Con cleanup `return () => {}` | `componentWillUnmount` |

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: two-cols-centered
---

## componentDidMount → useEffect con `[]`

::left::
**Class Component**

```jsx
class Ejemplo extends React.Component {
  componentDidMount() {
    // Se ejecuta UNA SOLA VEZ
    // después del primer render
    console.log('Componente montado');
    fetch('/api/datos')
      .then(r => r.json())
      .then(d => this.setState({ datos: d }));
  }

  render() { ... }
}
```

::right::
**Function Component**

```jsx
function Ejemplo() {
  useEffect(() => {
    // Se ejecuta UNA SOLA VEZ
    // después del primer render
    console.log('Componente montado');
    fetch('/api/datos')
      .then(r => r.json())
      .then(d => setDatos(d));
  }, []); // ← [] vacío = solo al montar

  return ...;
}
```

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: two-cols-centered
---

## componentDidUpdate → useEffect con dependencias

::left::
**Class Component**

```jsx
class Perfil extends React.Component {
  componentDidUpdate(prevProps) {
    // Comparar manualmente con el valor anterior
    if (prevProps.id !== this.props.id) {
      this.cargarPerfil(this.props.id);
    }
  }

  cargarPerfil(id) {
    fetch(`/api/perfil/${id}`)
      .then(r => r.json())
      .then(d => this.setState({ perfil: d }));
  }

  render() { ... }
}
```

::right::
**Function Component**

```jsx
function Perfil({ id }) {
  useEffect(() => {
    // React compara automáticamente
    // y corre cuando id cambia
    fetch(`/api/perfil/${id}`)
      .then(r => r.json())
      .then(d => setPerfil(d));
  }, [id]); // ← corre cuando `id` cambia

  return ...;
}
```

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: two-cols-centered
---

## componentWillUnmount → cleanup de useEffect

::left::
**Class Component**

```jsx
class Reloj extends React.Component {
  componentDidMount() {
    this.timer = setInterval(() => {
      this.setState({ hora: new Date() });
    }, 1000);
  }

  componentWillUnmount() {
    // Limpieza al desmontar
    clearInterval(this.timer);
  }

  render() { ... }
}
```

::right::
**Function Component**

```jsx
function Reloj() {
  const [hora, setHora] = useState(new Date());

  useEffect(() => {
    const timer = setInterval(() => {
      setHora(new Date());
    }, 1000);

    // La función que retorna = cleanup
    // Se ejecuta al desmontar (o antes de re-ejecutar el efecto)
    return () => clearInterval(timer);
  }, []);

  return <p>{hora.toLocaleTimeString()}</p>;
}
```

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Ejemplo completo: los tres en uno

::contents::
```jsx
function Perfil({ id }) {
  const [perfil, setPerfil] = useState(null);

  useEffect(() => {
    // 1. Corre al montar Y cuando id cambia (componentDidMount + componentDidUpdate)
    const controller = new AbortController();

    fetch(`/api/perfil/${id}`, { signal: controller.signal })
      .then(r => r.json())
      .then(d => setPerfil(d))
      .catch(err => { if (err.name !== 'AbortError') console.error(err); });

    // 2. Cleanup: cancela el fetch si el componente se desmonta
    //    o si id cambia antes de que termine (componentWillUnmount)
    return () => controller.abort();

  }, [id]); // 3. Dependencia: se re-ejecuta cuando id cambia

  if (!perfil) return <p>Cargando...</p>;
  return <h1>{perfil.nombre}</h1>;
}
```

Un solo `useEffect` reemplaza los tres métodos del class component.

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Resumen: Class vs Function

::contents::
| Fase | Class Component | Function Component |
|------|----------------|-------------------|
| Al montar | `componentDidMount()` | `useEffect(() => { }, [])` |
| Al actualizar | `componentDidUpdate(prev)` | `useEffect(() => { }, [dep])` |
| Al desmontar | `componentWillUnmount()` | `return () => { }` dentro del efecto |
| Estado | `this.state` + `this.setState()` | `useState()` |
| Sintaxis | Clase con `extends React.Component` | Función normal |

<br>

> Los **class components** siguen funcionando, pero los **function components con hooks** son el estándar moderno. La ventaja de los class components es que el ciclo de vida queda explícito y es más fácil de aprender conceptualmente.

::header::
Semana 5: React

::footer::
{{ $page }} / {{ $nav.total }}
