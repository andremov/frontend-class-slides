---
theme: ../theme
transition: none
layout: cover
title: Persistencia de Estado
exportFilename: 22-persistencia-estado
---

# Persistencia de Estado

✏️ 2026-01 ➖ ⏱️ 20 min.

---
layout: cover
---

# ¿Por qué persistir el estado?

---
layout: default-y-center
---

## El Problema

::contents::
Por defecto, el estado de React **desaparece** cuando el usuario recarga la página o cierra el navegador.

```jsx
// Este estado se pierde al recargar
const [tema, setTema] = useState('claro');
const [filtros, setFiltros] = useState([]);
const [borradorTexto, setBorradorTexto] = useState('');
```

**¿Qué estado vale la pena guardar?**
- Preferencias del usuario (tema, idioma, configuración)
- Borradores de formularios (para no perder trabajo)
- Filtros y posición de scroll activos

**¿Qué no guardar?**
- Estado de UI temporal (modal abierto, hover, focus)
- Datos del servidor que se pueden volver a pedir

::header::
Semana 6: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# localStorage

---
layout: default-y-center
---

## localStorage — Datos que Persisten Siempre

::contents::
`localStorage` guarda datos en el navegador **sin fecha de expiración**. Sobrevive al cierre del navegador.

```js
// Guardar
localStorage.setItem('tema', 'oscuro');
localStorage.setItem('usuario', JSON.stringify({ nombre: 'Ana', rol: 'admin' }));

// Leer
const tema = localStorage.getItem('tema'); // "oscuro"
const usuario = JSON.parse(localStorage.getItem('usuario'));

// Eliminar
localStorage.removeItem('tema');
localStorage.clear(); // elimina TODO — usar con cuidado
```

**Limitaciones:**
- Solo almacena strings — usa `JSON.stringify` / `JSON.parse` para objetos
- Capacidad: ~5MB por dominio
- No se sincroniza entre pestañas automáticamente

::header::
Semana 6: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## useEffect + localStorage — El Patrón

::contents::
```jsx
function App() {
  // 1. Leer el valor guardado al inicializar
  const [tema, setTema] = useState(() => {
    return localStorage.getItem('tema') ?? 'claro';
  });

  // 2. Guardar cada vez que cambia
  useEffect(() => {
    localStorage.setItem('tema', tema);
  }, [tema]);

  return (
    <div data-tema={tema}>
      <button onClick={() => setTema(t => t === 'claro' ? 'oscuro' : 'claro')}>
        Cambiar tema
      </button>
    </div>
  );
}
```

El inicializador de `useState` acepta una función — se ejecuta **solo una vez** al montar, no en cada render. Ideal para leer de localStorage.

::header::
Semana 6: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# sessionStorage y URL

---
layout: default-y-center
---

## sessionStorage vs localStorage vs URL

::contents::
| | localStorage | sessionStorage | URL / Query Params |
|---|---|---|---|
| Duración | Permanente | Hasta cerrar pestaña | Mientras esté en la URL |
| Compartible | No | No | ✅ Sí |
| Tamaño | ~5MB | ~5MB | ~2000 caracteres |

**Regla:** si el usuario debería poder compartir o bookmarkear ese estado → URL. Si es una preferencia personal → localStorage.

::header::
Semana 6: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Estado en la URL — useSearchParams

::contents::
```jsx
// Los filtros de búsqueda deben vivir en la URL — se pueden compartir
// ❌ Estado local — no se puede compartir ni bookmarkear
const [filtro, setFiltro] = useState('activo');

// ✅ En la URL — /usuarios?estado=activo&rol=admin
const [searchParams, setSearchParams] = useSearchParams();
const filtro = searchParams.get('estado') ?? 'todos';
```

Si el usuario debería poder **compartir un link** con ese estado, o **guardar un bookmark** → ponlo en la URL con `useSearchParams`.

::header::
Semana 6: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Resumen — Persistencia de Estado

::contents::
✅ El estado de React **se pierde** al recargar — usa `localStorage` para preservarlo

✅ Inicializa el estado desde `localStorage` usando la forma de función en `useState`

✅ Guarda a `localStorage` en un `useEffect` con el estado como dependencia

✅ Usa `JSON.stringify` / `JSON.parse` para objetos y arrays

✅ Usa **URL state** (`useSearchParams`) para filtros y datos que el usuario quiera compartir

✅ Usa **sessionStorage** para datos temporales de sesión (formularios en múltiples pasos)

❌ No guardes contraseñas ni tokens en localStorage — son accesibles desde JavaScript

❌ No guardes estado de UI efímero (modal abierto, focus) — no tiene sentido persistirlo

::header::
Semana 6: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# 🎉
