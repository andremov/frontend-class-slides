---
theme: ../theme
transition: none
layout: cover
title: Formularios y Validación
exportFilename: 28-forms
---

# Formularios y Validación
## Manejo de formularios en React

✏️ 2026-01 ➖ ⏱️ 60 min.

---
layout: cover
---

# Formularios en React

---
layout: default-y-center
---

## Controlados vs No Controlados

::contents::
```jsx
// No controlado — el DOM guarda el valor, React no lo conoce
function FormNoControlado() {
  const inputRef = useRef();
  function handleSubmit(e) {
    e.preventDefault();
    console.log(inputRef.current.value); // leer solo al submit
  }
  return (
    <form onSubmit={handleSubmit}>
      <input ref={inputRef} />
    </form>
  );
}

// ✅ Controlado — React guarda el valor en estado (patrón estándar)
function FormControlado() {
  const [nombre, setNombre] = useState('');
  function handleSubmit(e) {
    e.preventDefault();
    console.log(nombre); // siempre disponible
  }
  return (
    <form onSubmit={handleSubmit}>
      <input value={nombre} onChange={e => setNombre(e.target.value)} />
    </form>
  );
}
```

Los formularios **controlados** son el patrón estándar en React — el estado de React es la fuente de verdad.

::header::
Semana 8: Formularios

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Formulario con Múltiples Campos

::contents::
```jsx
function FormularioRegistro() {
  const [form, setForm] = useState({
    nombre: '', email: '', password: ''
  });

  // Handler genérico — actualiza el campo por su atributo name
  function handleChange(e) {
    const { name, value } = e.target;
    setForm(prev => ({ ...prev, [name]: value }));
  }

  function handleSubmit(e) {
    e.preventDefault(); // evitar recarga de página
    console.log('Datos:', form);
    // llamar a la API aquí
  }

  return (
    <form onSubmit={handleSubmit}>
      <input name="nombre"   value={form.nombre}   onChange={handleChange} />
      <input name="email"    value={form.email}    onChange={handleChange} />
      <input name="password" value={form.password} onChange={handleChange} type="password" />
      <button type="submit">Registrarse</button>
    </form>
  );
}
```

::header::
Semana 8: Formularios

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Validación Manual

---
layout: default-y-center
---

## Validación Campo por Campo

::contents::
```jsx
function FormularioConValidacion() {
  const [form, setForm]     = useState({ email: '', password: '' });
  const [errores, setErrores] = useState({});

  function validar() {
    const nuevosErrores = {};
    if (!form.email.includes('@')) {
      nuevosErrores.email = 'El email no es válido';
    }
    if (form.password.length < 8) {
      nuevosErrores.password = 'La contraseña debe tener al menos 8 caracteres';
    }
    return nuevosErrores;
  }

  function handleSubmit(e) {
    e.preventDefault();
    const erroresEncontrados = validar();
    if (Object.keys(erroresEncontrados).length > 0) {
      setErrores(erroresEncontrados);
      return;
    }
    // sin errores → enviar datos
  }

  return (
    <form onSubmit={handleSubmit}>
      <input name="email" value={form.email} onChange={...} />
      {errores.email && <span className="error">{errores.email}</span>}
    </form>
  );
}
```

::header::
Semana 8: Formularios

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# React Hook Form

---
layout: default-y-center
---

## Introducción a React Hook Form

::contents::
Escribir validación manualmente escala mal. **React Hook Form** (RHF) es la solución estándar.

```bash
npm install react-hook-form
```

**Ventajas sobre la solución manual:**
- Menos código de boilerplate
- Validación declarativa junto al input
- Alto rendimiento — no re-renderiza en cada tecla
- Integración lista con librerías de schema (Zod)

```jsx
import { useForm } from 'react-hook-form';

function FormularioLogin() {
  const {
    register,              // conecta el input al formulario
    handleSubmit,          // wrapper del onSubmit con validación
    formState: { errors }  // errores de validación
  } = useForm();

  function onSubmit(datos) {
    console.log(datos); // { email: "...", password: "..." }
  }

  return <form onSubmit={handleSubmit(onSubmit)}>...</form>;
}
```

::header::
Semana 8: Formularios

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## register, handleSubmit y errors

::contents::
```jsx
function FormularioLogin() {
  const { register, handleSubmit, formState: { errors } } = useForm();

  return (
    <form onSubmit={handleSubmit(datos => console.log(datos))}>

      <label htmlFor="email">Email</label>
      <input
        id="email"
        {...register('email', {
          required: 'El email es obligatorio',
          pattern: { value: /^\S+@\S+$/, message: 'Email inválido' }
        })}
      />
      {errors.email && <span>{errors.email.message}</span>}

      <label htmlFor="password">Contraseña</label>
      <input
        id="password"
        type="password"
        {...register('password', {
          required: 'La contraseña es obligatoria',
          minLength: { value: 8, message: 'Mínimo 8 caracteres' }
        })}
      />
      {errors.password && <span>{errors.password.message}</span>}

      <button type="submit">Entrar</button>
    </form>
  );
}
```

::header::
Semana 8: Formularios

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Validación con Zod

---
layout: default-y-center
---

## Schema Validation con Zod

::contents::
Zod define las reglas de validación como un esquema reutilizable, separado del componente.

```bash
npm install zod @hookform/resolvers
```

```ts
import { z } from 'zod';

// Definir el esquema de validación
const esquemaLogin = z.object({
  email: z.string()
    .min(1, 'El email es obligatorio')
    .email('Email inválido'),
  password: z.string()
    .min(8, 'Mínimo 8 caracteres')
    .max(64, 'Máximo 64 caracteres'),
});

// Inferir el tipo TypeScript desde el esquema
type DatosLogin = z.infer<typeof esquemaLogin>;
// equivalente a: { email: string; password: string; }
```

**Ventaja clave:** el esquema es independiente del formulario — se puede reutilizar en el backend o para validar datos de la API.

::header::
Semana 8: Formularios

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Integración React Hook Form + Zod

::contents::
```tsx
import { useForm } from 'react-hook-form';
import { zodResolver } from '@hookform/resolvers/zod';
import { z } from 'zod';

const esquema = z.object({
  email:    z.string().min(1, 'Requerido').email('Email inválido'),
  password: z.string().min(8, 'Mínimo 8 caracteres'),
});

type FormData = z.infer<typeof esquema>;

function FormularioLogin() {
  const { register, handleSubmit, formState: { errors } } = useForm<FormData>({
    resolver: zodResolver(esquema), // ← conectar Zod con RHF
  });

  return (
    <form onSubmit={handleSubmit(datos => console.log(datos))}>
      <input {...register('email')} />
      {errors.email && <span>{errors.email.message}</span>}

      <input type="password" {...register('password')} />
      {errors.password && <span>{errors.password.message}</span>}

      <button type="submit">Entrar</button>
    </form>
  );
}
```

::header::
Semana 8: Formularios

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Casos de Uso Reales

---
layout: default-y-center
---

## Manejo de Errores del Servidor

::contents::
```tsx
function FormularioRegistro() {
  const { register, handleSubmit, setError, formState: { errors } } = useForm<FormData>();

  async function onSubmit(datos: FormData) {
    try {
      await api.registrar(datos);
      navigate('/bienvenido');
    } catch (error) {
      if (error.status === 409) {
        // El servidor indica que el email ya está en uso
        setError('email', {
          type: 'server',
          message: 'Este email ya está registrado'
        });
      } else {
        // Error genérico
        setError('root', {
          message: 'Error al registrarse. Intenta de nuevo.'
        });
      }
    }
  }

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <input {...register('email')} />
      {errors.email && <span>{errors.email.message}</span>}
      {errors.root  && <div className="error-global">{errors.root.message}</div>}
      <button type="submit">Registrarse</button>
    </form>
  );
}
```

::header::
Semana 8: Formularios

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Accesibilidad en Formularios

::contents::
```jsx
{/* ❌ Sin accesibilidad — el usuario de screen reader no sabe qué es este input */}
<input type="text" placeholder="Nombre" />

{/* ✅ Con label asociado — el label es leído en voz alta al enfocar el input */}
<label htmlFor="nombre">Nombre completo</label>
<input id="nombre" type="text" />

{/* ✅ Con aria-describedby — asocia el error al input para screen readers */}
<label htmlFor="email">Email</label>
<input
  id="email"
  type="email"
  aria-describedby={errors.email ? 'error-email' : undefined}
  aria-invalid={!!errors.email}
/>
{errors.email && (
  <span id="error-email" role="alert">
    {errors.email.message}
  </span>
)}

{/* ✅ Campo requerido — indicar visualmente Y con aria */}
<label htmlFor="password">
  Contraseña <span aria-hidden="true">*</span>
</label>
<input id="password" type="password" required aria-required="true" />
```

::header::
Semana 8: Formularios

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Resumen — Formularios y Validación

::contents::
✅ Usa formularios **controlados** en React — el estado es la fuente de verdad

✅ Un handler `handleChange` genérico con `e.target.name` maneja todos los campos

✅ `React Hook Form` reduce el boilerplate y mejora el rendimiento

✅ `register` conecta el input, `handleSubmit` envuelve el submit, `errors` muestra mensajes

✅ **Zod** define las reglas como un esquema reutilizable y tipado — úsalo con `zodResolver`

✅ Usa `setError('campo', {...})` para mostrar errores devueltos por el servidor

✅ Siempre usa `<label htmlFor>` + `id` — obligatorio para accesibilidad

❌ No valides manualmente con `if/else` para cada campo — usa un esquema de validación

❌ No muestres solo un error global — muestra el error junto al campo que lo causó

::header::
Semana 8: Formularios

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# 🎉
