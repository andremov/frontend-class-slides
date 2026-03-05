---
theme: ../theme
transition: none
layout: cover
title: Browser APIs
exportFilename: 27-browser-apis
---

# Browser APIs

✏️ 2026-01 ➖ ⏱️ 20 min.

---
layout: cover
---

# El Navegador Como Plataforma

---
layout: default-y-center
---

## Más Allá del DOM

::contents::
El navegador expone APIs que permiten acceder a capacidades del dispositivo y del sistema operativo.

**APIs útiles en el día a día:**

| API | Para qué sirve |
|---|---|
| **Clipboard API** | Copiar y pegar texto desde/hacia el portapapeles |
| **Geolocation API** | Coordenadas GPS del dispositivo |
| **Notifications API** | Notificaciones del sistema operativo |
| **Web Storage** | localStorage y sessionStorage |
| **Fetch API** | Peticiones HTTP (ya la conoces) |
| **Intersection Observer** | Detectar cuándo un elemento entra al viewport |
| **ResizeObserver** | Detectar cambios de tamaño en elementos |

Todas son asíncronas. Muchas requieren permiso explícito del usuario.

::header::
Semana 7: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Clipboard API

---
layout: default-y-center
---

## Copiar al Portapapeles

::contents::
```js
// Copiar texto al portapapeles
async function copiarTexto(texto) {
  try {
    await navigator.clipboard.writeText(texto);
  } catch (err) {
    console.error('No se pudo copiar:', err);
  }
}
```

```jsx
// Patrón completo — botón "Copiar código"
function BotonCopiar({ texto }) {
  const [copiado, setCopiado] = useState(false);

  async function handleCopiar() {
    await navigator.clipboard.writeText(texto);
    setCopiado(true);
    setTimeout(() => setCopiado(false), 2000);
  }

  return (
    <button onClick={handleCopiar}>
      {copiado ? '✅ Copiado' : 'Copiar'}
    </button>
  );
}
```

**Requiere:** HTTPS o localhost. En algunos navegadores pide permiso al usuario.

::header::
Semana 7: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Leer del Portapapeles

::contents::
```jsx
// Pegar desde el portapapeles — requiere permiso de lectura
function InputConPegar({ onChange }) {
  async function handlePegar() {
    try {
      const texto = await navigator.clipboard.readText();
      onChange(texto);
    } catch (err) {
      // El usuario puede denegar el permiso — diseña el fallback
      console.error('Permiso denegado:', err);
    }
  }

  return (
    <div>
      <input onChange={e => onChange(e.target.value)} />
      <button onClick={handlePegar}>Pegar</button>
    </div>
  );
}
```

`readText()` muestra un prompt de permiso en el navegador — el usuario puede denegarlo. Siempre diseña un fallback (el input sigue funcionando manualmente).

::header::
Semana 7: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Intersection Observer

---
layout: default-y-center
---

## Detectar Elementos Visibles

::contents::
`IntersectionObserver` detecta cuándo un elemento entra o sale del viewport — sin eventos de scroll costosos.

```jsx
// Animación al hacer scroll — el elemento aparece al entrar al viewport
useEffect(() => {
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          entry.target.classList.add('visible');
          observer.unobserve(entry.target); // observar solo una vez
        }
      });
    },
    { threshold: 0.1 } // visible cuando el 10% está en el viewport
  );

  document.querySelectorAll('.animar-al-entrar')
    .forEach(el => observer.observe(el));

  return () => observer.disconnect(); // limpieza en useEffect
}, []);
```

```css
.animar-al-entrar         { opacity: 0; transform: translateY(20px); transition: all 0.4s; }
.animar-al-entrar.visible { opacity: 1; transform: translateY(0); }
```

::header::
Semana 7: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Resumen — Browser APIs

::contents::
✅ El navegador expone APIs para acceder a capacidades del dispositivo — más allá del DOM

✅ **Clipboard API:** `navigator.clipboard.writeText()` para copiar, `readText()` para pegar

✅ Siempre usa `try/catch` — el usuario puede denegar permisos o el contexto puede no soportarlo

✅ **IntersectionObserver** para detectar visibilidad — mucho más eficiente que escuchar `scroll`

✅ Muchas APIs requieren **HTTPS** — no funcionan en HTTP (excepto localhost)

✅ Limpia observers y listeners en el `return` de `useEffect`

❌ No asumas que el usuario otorgará permisos — siempre diseña el caso en que los deniega

::header::
Semana 7: React

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# 🎉
