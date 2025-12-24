---
theme: ../theme
transition: none
layout: cover
title: JavaScript Básico
exportFilename: 07-javascript
---

# JavaScript Básico

✏️ 2025-03 ➖ ⏱️ 45 min.

---
layout: cover
---

# Que es JavaScript?

---
layout: default-y-center
---

## JavaScript

::contents::
JavaScript es el lenguaje de programación de la web.

Agrega **interactividad** y **comportamiento** a las páginas web.

Es el único lenguaje que funciona nativamente en todos los navegadores.

::header::
Semana 3: JavaScript

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## HTML, CSS, y JavaScript

::contents::
**HTML**: Estructura y contenido

**CSS**: Presentación y estilo

**JavaScript**: Comportamiento e interactividad

Juntos forman la base del desarrollo web front-end.

::header::
Semana 3: JavaScript

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Cómo Usar JavaScript

::contents::
**Inline** (en el HTML):
```html
<button onclick="alert('Hola!')">Click</button>
```

**Interno** (en el `<head>` o `<body>`):
```html
<script>
    console.log('Hola Mundo');
</script>
```

**Externo** (archivo separado - recomendado):
```html
<script src="script.js"></script>
```

::header::
Semana 3: JavaScript

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Variables

---
layout: default-y-center
---

## Declarar Variables

::contents::
```js
// let - puede cambiar
let nombre = 'Juan';
nombre = 'María'; // ✅ Permitido

// const - no puede cambiar
const edad = 25;
edad = 26; // ❌ Error

// var - evitar (antigua forma)
var ciudad = 'Madrid';
```

**Recomendación**: Usar `const` por defecto, `let` solo si necesitas reasignar.

::header::
Semana 3: JavaScript

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Nombres de Variables

::contents::
**Reglas**:
- Empezar con letra, `_`, o `$`
- Pueden contener letras, números, `_`, `$`
- No usar palabras reservadas (`if`, `let`, `function`, etc.)
- Case-sensitive (`nombre` ≠ `Nombre`)

**Convención (camelCase)**:
```js
let nombreCompleto = 'Juan Pérez';
let edadUsuario = 25;
let estaActivo = true;
```

::header::
Semana 3: JavaScript

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Tipos de Datos

---
layout: default-y-center
---

## Tipos de Datos Primitivos

::contents::
```js
// String (texto)
let nombre = 'Juan';
let apellido = "Pérez";

// Number (números)
let edad = 25;
let precio = 19.99;

// Boolean (verdadero/falso)
let estaActivo = true;
let estaLogueado = false;

// Undefined (sin valor asignado)
let sinValor;

// Null (valor vacío intencional)
let vacio = null;
```

::header::
Semana 3: JavaScript

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Strings (Cadenas de Texto)

::contents::
```js
let nombre = 'Juan';
let apellido = "Pérez";

// Concatenación
let nombreCompleto = nombre + ' ' + apellido;

// Template literals (comillas invertidas)
let saludo = `Hola, ${nombre}!`;

// Propiedades y métodos
nombre.length;              // 4
nombre.toUpperCase();       // 'JUAN'
nombre.toLowerCase();       // 'juan'
nombre.includes('Ju');      // true
```

::header::
Semana 3: JavaScript

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Numbers (Números)

::contents::
```js
let x = 10;
let y = 5;

// Operaciones
x + y;    // 15
x - y;    // 5
x * y;    // 50
x / y;    // 2
x % y;    // 0 (módulo/residuo)
x ** 2;   // 100 (potencia)

// Métodos útiles
Math.round(4.7);    // 5
Math.floor(4.7);    // 4
Math.ceil(4.3);     // 5
Math.random();      // número aleatorio entre 0 y 1
```

::header::
Semana 3: JavaScript

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Arrays (Arreglos)

::contents::
```js
// Crear array
let frutas = ['manzana', 'banana', 'naranja'];

// Acceder elementos
frutas[0];        // 'manzana'
frutas[1];        // 'banana'

// Propiedades
frutas.length;    // 3

// Métodos comunes
frutas.push('uva');           // Agregar al final
frutas.pop();                 // Eliminar del final
frutas.unshift('pera');       // Agregar al inicio
frutas.shift();               // Eliminar del inicio
frutas.includes('banana');    // true
```

::header::
Semana 3: JavaScript

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Objetos

::contents::
```js
// Crear objeto
let persona = {
    nombre: 'Juan',
    edad: 25,
    ciudad: 'Madrid'
};

// Acceder propiedades
persona.nombre;        // 'Juan'
persona['edad'];       // 25

// Modificar
persona.edad = 26;

// Agregar propiedad
persona.email = 'juan@email.com';
```

::header::
Semana 3: JavaScript

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Operadores

---
layout: default-y-center
---

## Operadores de Comparación

::contents::
```js
// Igualdad
5 == '5';     // true (compara valor)
5 === '5';    // false (compara valor y tipo)

// Desigualdad
5 != '5';     // false
5 !== '5';    // true

// Mayor/Menor
10 > 5;       // true
10 < 5;       // false
10 >= 10;     // true
10 <= 5;      // false
```

**Recomendación**: Usar `===` y `!==` siempre.

::header::
Semana 3: JavaScript

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Operadores Lógicos

::contents::
```js
// AND (&&) - ambos deben ser verdaderos
true && true;     // true
true && false;    // false

// OR (||) - al menos uno debe ser verdadero
true || false;    // true
false || false;   // false

// NOT (!) - invierte el valor
!true;            // false
!false;           // true

// Ejemplos
let edad = 18;
let tienePermiso = true;

edad >= 18 && tienePermiso;  // true
```

::header::
Semana 3: JavaScript

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Control de Flujo

---
layout: default-y-center
---

## If / Else

::contents::
```js
let edad = 18;

if (edad >= 18) {
    console.log('Eres mayor de edad');
} else {
    console.log('Eres menor de edad');
}

// Con else if
let nota = 85;

if (nota >= 90) {
    console.log('Excelente');
} else if (nota >= 70) {
    console.log('Bien');
} else {
    console.log('Necesitas mejorar');
}
```

::header::
Semana 3: JavaScript

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Operador Ternario

::contents::
Forma corta de if/else para asignaciones simples:

```js
// Sintaxis: condición ? siVerdadero : siFalso

let edad = 18;
let mensaje = edad >= 18 ? 'Mayor' : 'Menor';

// Equivalente a:
let mensaje;
if (edad >= 18) {
    mensaje = 'Mayor';
} else {
    mensaje = 'Menor';
}
```

::header::
Semana 3: JavaScript

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Métodos de Array

::contents::
```js
const numeros = [1, 2, 3, 4, 5];

// map - transformar cada elemento
const duplicados = numeros.map(num => num * 2);
// [2, 4, 6, 8, 10]

// filter - filtrar elementos
const mayores = numeros.filter(num => num > 3);
// [4, 5]

// find - encontrar un elemento
const encontrado = numeros.find(num => num === 3);
// 3
```

::header::
Semana 3: JavaScript

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Funciones

---
layout: default-y-center
---

## Arrow Functions

::contents::
Las arrow functions son la forma moderna y más común en React:

```js
// Función normal
function sumar(a, b) {
    return a + b;
}

// Arrow function
const sumar = (a, b) => {
    return a + b;
};

// Arrow function corta (return implícito)
const sumar = (a, b) => a + b;

// Un solo parámetro (sin paréntesis)
const duplicar = x => x * 2;
```

::header::
Semana 3: JavaScript

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Destructuring (Objetos)

::contents::
Extraer propiedades de objetos de forma simple:

```js
const persona = {
    nombre: 'Juan',
    edad: 25,
    ciudad: 'Madrid'
};

// Sin destructuring
const nombre = persona.nombre;
const edad = persona.edad;

// Con destructuring
const { nombre, edad } = persona;

// Con nombres diferentes
const { nombre: n, edad: e } = persona;
```

::header::
Semana 3: JavaScript

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Destructuring (Arrays)

::contents::
```js
const colores = ['rojo', 'verde', 'azul'];

// Sin destructuring
const primero = colores[0];
const segundo = colores[1];

// Con destructuring
const [primero, segundo] = colores;

// Saltar elementos
const [primero, , tercero] = colores;

// Con valores por defecto
const [a, b, c, d = 'amarillo'] = colores;
```

::header::
Semana 3: JavaScript

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Spread Operator (...)

::contents::
```js
// Con arrays
const numeros = [1, 2, 3];
const masNumeros = [...numeros, 4, 5];
// [1, 2, 3, 4, 5]

// Con objetos
const persona = { nombre: 'Juan', edad: 25 };
const personaActualizada = { ...persona, edad: 26 };
// { nombre: 'Juan', edad: 26 }

// Copiar array
const copia = [...numeros];

// Combinar arrays
const todos = [...numeros, ...masNumeros];
```

::header::
Semana 3: JavaScript

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Trabajando con Arrays

---
layout: default-y-center
---

## Ejemplo: Transformar Datos

::contents::
```js
const productos = [
    { id: 1, nombre: 'Laptop', precio: 999 },
    { id: 2, nombre: 'Mouse', precio: 25 },
    { id: 3, nombre: 'Teclado', precio: 75 }
];

// Crear un array de nombres
const nombres = productos.map(producto => producto.nombre);
// ['Laptop', 'Mouse', 'Teclado']

// Crear descripciones
const descripciones = productos.map(producto => 
    `${producto.nombre} - $${producto.precio}`
);
```

::header::
Semana 3: JavaScript

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Filtrar y Mapear

::contents::
Combinar métodos de array:

```js
const productos = [
    { id: 1, nombre: 'Laptop', precio: 999 },
    { id: 2, nombre: 'Mouse', precio: 25 },
    { id: 3, nombre: 'Teclado', precio: 75 }
];

// Filtrar productos caros y obtener nombres
const caros = productos
    .filter(p => p.precio > 50)
    .map(p => p.nombre);
// ['Laptop', 'Teclado']
```

::header::
Semana 3: JavaScript

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Consejos Importantes

::contents::
✅ **Usar `console.log()`** para debugging

✅ **Usar nombres descriptivos** de variables y funciones

✅ **Comentar código complejo**

✅ **Practicar regularmente** - la práctica hace al maestro

::header::
Semana 3: JavaScript

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Recursos de Aprendizaje

::contents::
**Documentación**:
- MDN Web Docs: https://developer.mozilla.org/es/docs/Web/JavaScript
- JavaScript.info: https://javascript.info

**Práctica**:
- freeCodeCamp
- Codecademy
- LeetCode (algoritmos)

**Herramientas**:
- Console del navegador (F12)
- VS Code

::header::
Semana 3: JavaScript

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# 🎉
