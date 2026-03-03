---
theme: ../theme
transition: none
layout: cover
title: TypeScript
exportFilename: 40-typescript
---

# TypeScript
## JavaScript con tipos estáticos

✏️ 2026-01 ➖ ⏱️ 60 min.

---
layout: cover
---

# ¿Por Qué TypeScript?

---
layout: default-y-center
---

## El Problema con JavaScript

::contents::
JavaScript es dinámico — los errores de tipo solo aparecen cuando el código se ejecuta.

```js
// JS — el error aparece cuando el usuario lo encuentra
function calcularTotal(precio, cantidad) {
  return precio * cantidad;
}

calcularTotal("100", 3); // → "100100100" — multiplicación de strings 🐛
```

```ts
// TS — el error aparece mientras escribís el código
function calcularTotal(precio: number, cantidad: number): number {
  return precio * cantidad;
}

calcularTotal("100", 3);
// ❌ Error: Argument of type 'string' is not assignable to type 'number'
```

**Beneficios:**
- Los errores se detectan antes de ejecutar el código
- El editor autocompleta propiedades y métodos con certeza
- El código se documenta a sí mismo — las firmas de funciones son contratos

::header::
Semana 11: TypeScript

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Tipos Básicos

---
layout: default-y-center
---

## Tipos Primitivos y Arrays

::contents::
```ts
// Tipos primitivos
let nombre: string  = "María";
let edad:   number  = 28;
let activo: boolean = true;

// Arrays
let precios:  number[] = [10, 25, 50];
let etiquetas: string[] = ["nuevo", "oferta"];

// Tuple — array con longitud y tipos fijos
let coordenada: [number, number] = [40.7, -74.0];
let entrada: [string, number]    = ["María", 28]; // [nombre, edad]

// TypeScript infiere el tipo automáticamente cuando hay un valor inicial
let ciudad   = "Buenos Aires"; // TS infiere: string
let cantidad = 5;              // TS infiere: number
// No es necesario anotar el tipo si TS puede inferirlo
```

::header::
Semana 11: TypeScript

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## any, unknown, never, void

::contents::
```ts
// any — desactiva el chequeo de tipos. Evitar siempre que sea posible
let dato: any = "texto";
dato = 42;       // OK
dato.metodo();   // OK — pero puede fallar en runtime sin error de TS

// unknown — tipo desconocido pero seguro: hay que verificar antes de usar
let respuesta: unknown = obtenerDatos();
if (typeof respuesta === 'string') {
  console.log(respuesta.toUpperCase()); // OK — ya verificamos el tipo
}

// void — función que no retorna ningún valor
function logMensaje(msg: string): void {
  console.log(msg);
  // sin return
}

// never — función que nunca termina normalmente
function lanzarError(mensaje: string): never {
  throw new Error(mensaje);
}
```

::header::
Semana 11: TypeScript

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Interfaces y Types

---
layout: default-y-center
---

## interface vs type

::contents::
```ts
// interface — describe la forma de un objeto
interface Usuario {
  id:     number;
  nombre: string;
  email:  string;
  rol?:   string; // opcional — puede estar o no
}

// type — más flexible, puede ser cualquier tipo
type EstadoCarga = 'cargando' | 'exito' | 'error'; // union type
type ID = string | number;                           // varios tipos posibles

// ¿Cuál usar?
// → interface para objetos y props de componentes React (más idiomático)
// → type para unions, aliases y tipos complejos

// Extender interfaces
interface Admin extends Usuario {
  permisos: string[];
}

// Función que recibe un objeto tipado
function mostrarUsuario(usuario: Usuario) {
  console.log(`${usuario.nombre} — ${usuario.email}`);
}
```

::header::
Semana 11: TypeScript

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Tipos Opcionales y Union Types

::contents::
```ts
// Propiedad opcional — puede ser string o undefined
interface Producto {
  id:          number;
  nombre:      string;
  descripcion?: string;     // opcional
  descuento?:  number;      // opcional
}

// Union type — puede ser uno u otro tipo
type Respuesta = 'si' | 'no' | 'tal-vez';
type ID = string | number;

// Null y undefined con strictNullChecks activado
let nombre: string = "Ana";
// nombre = null; // ❌ Error — no se puede asignar null

let nombreOpcional: string | null = null; // ✅ explicitamente nullable

// Optional chaining — acceder a propiedades que podrían no existir
const ciudad = usuario?.direccion?.ciudad;
// Equivale a: usuario && usuario.direccion && usuario.direccion.ciudad

// Nullish coalescing — valor por defecto si es null/undefined
const nombreMostrado = usuario.nombre ?? 'Anónimo';
```

::header::
Semana 11: TypeScript

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Generics Básicos

::contents::
Los generics permiten escribir código reutilizable que funciona con cualquier tipo.

```ts
// Función genérica — T es un parámetro de tipo
function primero<T>(array: T[]): T {
  return array[0];
}

primero([1, 2, 3]);        // TS infiere T = number → retorna number
primero(["a", "b", "c"]);  // TS infiere T = string → retorna string

// Promise con tipo de retorno
async function obtenerDatos<T>(url: string): Promise<T> {
  const res = await fetch(url);
  return res.json();
}

// Uso con tipo explícito:
interface Producto { id: number; nombre: string; precio: number; }

const producto = await obtenerDatos<Producto>('/api/productos/1');
// producto.nombre → TypeScript sabe que es string ✅
// producto.xyz    → ❌ Error — no existe esa propiedad
```

::header::
Semana 11: TypeScript

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# TypeScript en React

---
layout: default-y-center
---

## Tipado de Props

::contents::
```tsx
// Definir el tipo de las props con interface
interface TarjetaProductoProps {
  nombre:    string;
  precio:    number;
  imagen:    string;
  enOferta?: boolean;              // prop opcional
  onClick:   () => void;           // función sin argumentos ni retorno
  onAgregar: (id: number) => void; // función con argumento
}

// Componente con props tipadas
function TarjetaProducto({
  nombre, precio, enOferta = false, onClick
}: TarjetaProductoProps) {
  return (
    <div onClick={onClick}>
      <h2>{nombre}</h2>
      <p>{enOferta ? `¡Oferta! $${precio}` : `$${precio}`}</p>
    </div>
  );
}

// ReactNode — para props que reciben JSX
interface ContenedorProps {
  children: React.ReactNode;
  titulo:   string;
}
```

::header::
Semana 11: TypeScript

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Tipado de Hooks y Eventos

::contents::
```tsx
import { useState, useRef } from 'react';

// useState<T> — tipo del estado
const [contador, setContador] = useState<number>(0);
const [usuario, setUsuario]   = useState<Usuario | null>(null);

// Si el valor inicial clarifica el tipo, TS lo infiere:
const [nombre, setNombre] = useState('');  // TS infiere: string

// useRef<T> — tipo del elemento DOM
const inputRef = useRef<HTMLInputElement>(null);
const divRef   = useRef<HTMLDivElement>(null);

// Tipado de eventos
function handleClick(e: React.MouseEvent<HTMLButtonElement>) {
  console.log(e.currentTarget.textContent);
}

function handleChange(e: React.ChangeEvent<HTMLInputElement>) {
  setNombre(e.target.value);
}

function handleSubmit(e: React.FormEvent<HTMLFormElement>) {
  e.preventDefault();
}
```

::header::
Semana 11: TypeScript

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Tipado de Respuestas de API

::contents::
```ts
// Definir la forma esperada de los datos
interface Producto {
  id:        number;
  nombre:    string;
  precio:    number;
  categoria: string;
  imagen:    string;
}

// Hook con estado tipado
function useProductos() {
  const [productos, setProductos] = useState<Producto[]>([]);
  const [cargando, setCargando]   = useState(true);
  const [error, setError]         = useState<string | null>(null);

  useEffect(() => {
    fetch('/api/productos')
      .then(res => res.json())
      .then((datos: Producto[]) => {   // ← tipo explícito en .then()
        setProductos(datos);
        setCargando(false);
      })
      .catch(() => setError('Error al cargar productos'));
  }, []);

  return { productos, cargando, error };
}
```

::header::
Semana 11: TypeScript

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Configuración y Migración

---
layout: default-y-center
---

## tsconfig.json Básico

::contents::
Vite crea el `tsconfig.json` automáticamente. Los valores más importantes:

```json
{
  "compilerOptions": {
    "target": "ES2020",          // versión de JS a generar
    "lib": ["ES2020", "DOM"],    // APIs disponibles (DOM para browser)
    "jsx": "react-jsx",          // transformación JSX
    "module": "ESNext",          // sistema de módulos
    "strict": true,              // ← activar siempre
    "noUnusedLocals": true,      // error si hay variables sin usar
    "noUnusedParameters": true   // error si hay parámetros sin usar
  }
}
```

**`"strict": true`** activa varios chequeos importantes:
- `strictNullChecks` — `null` y `undefined` no son valores por defecto
- `noImplicitAny` — prohíbe el tipo `any` implícito
- `strictFunctionTypes` — verifica la compatibilidad de funciones

::header::
Semana 11: TypeScript

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Migrar un Componente de JS a TS

::contents::
```jsx
// ANTES — Tarjeta.jsx
function Tarjeta({ titulo, descripcion, fecha, onClick }) {
  return (
    <div onClick={onClick}>
      <h3>{titulo}</h3>
      <p>{descripcion}</p>
      <small>{fecha}</small>
    </div>
  );
}
```

```tsx
// DESPUÉS — Tarjeta.tsx
interface TarjetaProps {
  titulo:       string;
  descripcion:  string;
  fecha:        string;
  onClick?:     () => void;
}

function Tarjeta({ titulo, descripcion, fecha, onClick }: TarjetaProps) {
  return (
    <div onClick={onClick}>
      <h3>{titulo}</h3>
      <p>{descripcion}</p>
      <small>{fecha}</small>
    </div>
  );
}
```

**Pasos:** renombrar `.jsx` → `.tsx`, agregar `interface` para las props, corregir los errores que TS señale.

::header::
Semana 11: TypeScript

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Resumen — TypeScript

::contents::
✅ TypeScript detecta errores de tipo **antes** de ejecutar el código

✅ Usa `interface` para describir la forma de objetos y props de componentes React

✅ Usa `type` para unions (`'cargando' | 'exito' | 'error'`) y aliases de tipo

✅ Tipa siempre las props de tus componentes con una `interface`

✅ `useState<T>`, `useRef<HTMLElement>` — pasa el tipo como genérico

✅ Activa `"strict": true` en `tsconfig.json` desde el inicio del proyecto

✅ Para migrar: renombra `.jsx` → `.tsx` y agrega las interfaces de props

❌ No uses `any` para escapar del sistema de tipos — usa `unknown` si el tipo es realmente desconocido

❌ No tipees todo manualmente — deja que TS infiera cuando el tipo es obvio por el valor inicial

::header::
Semana 11: TypeScript

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# 🎉
