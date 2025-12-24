---
theme: ../theme
transition: none
layout: cover
title: JavaScript Extendido
exportFilename: 07b-javascript-extended
---

# JavaScript Extendido
## Conceptos Adicionales

✏️ 2025-03 ➖ ⏱️ 30 min.

---
layout: cover
---

# Loops Tradicionales

---
layout: default-y-center
---

## For Loop

::contents::
```js
// For básico
for (let i = 0; i < 5; i++) {
    console.log(i);  // 0, 1, 2, 3, 4
}

// Recorrer array
let frutas = ['manzana', 'banana', 'naranja'];

for (let i = 0; i < frutas.length; i++) {
    console.log(frutas[i]);
}

// For...of (más simple)
for (let fruta of frutas) {
    console.log(fruta);
}
```

::header::
Semana 3: JavaScript Extendido

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## While Loop

::contents::
```js
// While - mientras la condición sea verdadera
let contador = 0;

while (contador < 5) {
    console.log(contador);
    contador++;
}

// Do...while - ejecuta al menos una vez
let numero = 0;

do {
    console.log(numero);
    numero++;
} while (numero < 5);
```

::header::
Semana 3: JavaScript Extendido

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Break y Continue

::contents::
```js
// Break - salir del loop
for (let i = 0; i < 10; i++) {
    if (i === 5) break;
    console.log(i);  // 0, 1, 2, 3, 4
}

// Continue - saltar a la siguiente iteración
for (let i = 0; i < 5; i++) {
    if (i === 2) continue;
    console.log(i);  // 0, 1, 3, 4
}
```

::header::
Semana 3: JavaScript Extendido

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Manipulación del DOM

---
layout: default-y-center
---

## Que es el DOM?

::contents::
**DOM** = Document Object Model

Es la representación de la página HTML que JavaScript puede manipular.

Permite:
- Seleccionar elementos
- Modificar contenido
- Cambiar estilos
- Agregar/eliminar elementos
- Responder a eventos

::header::
Semana 3: JavaScript Extendido

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Seleccionar Elementos

::contents::
```js
// Por ID
const elemento = document.getElementById('mi-id');

// Por clase (devuelve el primero)
const elemento = document.querySelector('.mi-clase');

// Por clase (devuelve todos)
const elementos = document.querySelectorAll('.mi-clase');

// Por etiqueta
const parrafos = document.querySelectorAll('p');

// Combinaciones
const btn = document.querySelector('.btn-primary');
const items = document.querySelectorAll('#menu li');
```

::header::
Semana 3: JavaScript Extendido

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Modificar Contenido

::contents::
```js
const elemento = document.querySelector('#titulo');

// Cambiar texto
elemento.textContent = 'Nuevo texto';

// Cambiar HTML interno
elemento.innerHTML = '<strong>Texto en negrita</strong>';

// Cambiar atributos
const imagen = document.querySelector('img');
imagen.src = 'nueva-imagen.jpg';
imagen.alt = 'Nueva descripción';

// Cambiar clases
elemento.classList.add('activo');
elemento.classList.remove('inactivo');
elemento.classList.toggle('oculto');
```

::header::
Semana 3: JavaScript Extendido

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Modificar Estilos

::contents::
```js
const elemento = document.querySelector('.caja');

// Cambiar estilos individuales
elemento.style.color = 'red';
elemento.style.backgroundColor = 'blue';
elemento.style.fontSize = '20px';

// Mejor práctica: usar clases
elemento.classList.add('destacado');

// CSS
// .destacado {
//     color: red;
//     background-color: blue;
//     font-size: 20px;
// }
```

::header::
Semana 3: JavaScript Extendido

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Eventos

::contents::
```js
const boton = document.querySelector('#mi-boton');

// Click
boton.addEventListener('click', function() {
    console.log('Botón clickeado!');
});

// Con arrow function
boton.addEventListener('click', () => {
    console.log('Botón clickeado!');
});

// Otros eventos comunes
input.addEventListener('input', () => { /* ... */ });
form.addEventListener('submit', () => { /* ... */ });
elemento.addEventListener('mouseover', () => { /* ... */ });
elemento.addEventListener('mouseout', () => { /* ... */ });
```

::header::
Semana 3: JavaScript Extendido

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Event Object

::contents::
```js
// Acceder al evento
button.addEventListener('click', (event) => {
    console.log(event.target);  // Elemento clickeado
    console.log(event.type);    // 'click'
});

// Prevenir comportamiento por defecto
form.addEventListener('submit', (e) => {
    e.preventDefault();
    console.log('Formulario no se envió');
});

// Detener propagación
elemento.addEventListener('click', (e) => {
    e.stopPropagation();
});
```

::header::
Semana 3: JavaScript Extendido

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Crear y Agregar Elementos

::contents::
```js
// Crear elemento
const nuevoParrafo = document.createElement('p');
nuevoParrafo.textContent = 'Este es un nuevo párrafo';
nuevoParrafo.classList.add('destacado');

// Agregar al DOM
const contenedor = document.querySelector('#contenedor');
contenedor.appendChild(nuevoParrafo);

// Insertar antes de otro elemento
contenedor.insertBefore(nuevoParrafo, primerHijo);

// Eliminar elemento
const elemento = document.querySelector('.eliminar');
elemento.remove();
```

::header::
Semana 3: JavaScript Extendido

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Ejemplos Prácticos

---
layout: default-y-center
---

## Contador Simple

::contents::
```html
<div id="contador">
    <p>Contador: <span id="numero">0</span></p>
    <button id="incrementar">+</button>
    <button id="decrementar">-</button>
</div>
```

```js
let contador = 0;
const numeroElemento = document.querySelector('#numero');
const btnIncrementar = document.querySelector('#incrementar');
const btnDecrementar = document.querySelector('#decrementar');

btnIncrementar.addEventListener('click', () => {
    contador++;
    numeroElemento.textContent = contador;
});

btnDecrementar.addEventListener('click', () => {
    contador--;
    numeroElemento.textContent = contador;
});
```

::header::
Semana 3: JavaScript Extendido

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Lista de Tareas

::contents::
```html
<input id="nueva-tarea" type="text" placeholder="Nueva tarea">
<button id="agregar">Agregar</button>
<ul id="lista"></ul>
```

```js
const input = document.querySelector('#nueva-tarea');
const btnAgregar = document.querySelector('#agregar');
const lista = document.querySelector('#lista');

btnAgregar.addEventListener('click', () => {
    const texto = input.value;
    
    if (texto) {
        const li = document.createElement('li');
        li.textContent = texto;
        lista.appendChild(li);
        input.value = '';
    }
});
```

::header::
Semana 3: JavaScript Extendido

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Toggle de Clase

::contents::
```html
<button id="toggle">Toggle Dark Mode</button>
<div class="content">
    <p>Contenido aquí</p>
</div>
```

```js
const toggleBtn = document.querySelector('#toggle');
const body = document.body;

toggleBtn.addEventListener('click', () => {
    body.classList.toggle('dark-mode');
});
```

```css
.dark-mode {
    background-color: #1a1a1a;
    color: white;
}
```

::header::
Semana 3: JavaScript Extendido

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Validación de Formulario

::contents::
```html
<form id="formulario">
    <input type="text" id="nombre" placeholder="Nombre">
    <span id="error"></span>
    <button type="submit">Enviar</button>
</form>
```

```js
const form = document.querySelector('#formulario');
const nombreInput = document.querySelector('#nombre');
const errorSpan = document.querySelector('#error');

form.addEventListener('submit', (e) => {
    e.preventDefault();
    
    if (nombreInput.value.length < 3) {
        errorSpan.textContent = 'El nombre debe tener al menos 3 caracteres';
    } else {
        errorSpan.textContent = '';
        console.log('Formulario válido:', nombreInput.value);
    }
});
```

::header::
Semana 3: JavaScript Extendido

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Conceptos Adicionales

---
layout: default-y-center
---

## Switch Statement

::contents::
```js
const dia = 'lunes';

switch (dia) {
    case 'lunes':
        console.log('Inicio de semana');
        break;
    case 'viernes':
        console.log('Fin de semana cerca!');
        break;
    case 'sabado':
    case 'domingo':
        console.log('Fin de semana!');
        break;
    default:
        console.log('Día de semana normal');
}
```

::header::
Semana 3: JavaScript Extendido

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Try...Catch (Manejo de Errores)

::contents::
```js
try {
    // Código que puede fallar
    const resultado = funcionQuePuedeFallar();
    console.log(resultado);
} catch (error) {
    // Manejar el error
    console.error('Ocurrió un error:', error.message);
} finally {
    // Siempre se ejecuta
    console.log('Limpieza');
}

// Lanzar errores personalizados
function dividir(a, b) {
    if (b === 0) {
        throw new Error('No se puede dividir por cero');
    }
    return a / b;
}
```

::header::
Semana 3: JavaScript Extendido

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Scope (Ámbito)

::contents::
```js
// Global scope
let global = 'Soy global';

function miFuncion() {
    // Function scope
    let local = 'Soy local';
    console.log(global);  // ✅ Accesible
    console.log(local);   // ✅ Accesible
}

console.log(global);  // ✅ Accesible
console.log(local);   // ❌ Error - no definido

// Block scope (let y const)
if (true) {
    let bloque = 'Soy de bloque';
    var noBloque = 'No respeto bloques';
}

console.log(noBloque);  // ✅ var ignora bloques
console.log(bloque);    // ❌ Error
```

::header::
Semana 3: JavaScript Extendido

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Métodos de String Adicionales

::contents::
```js
const texto = 'JavaScript es genial';

// Buscar
texto.indexOf('es');        // 11
texto.lastIndexOf('a');     // 18
texto.includes('genial');   // true
texto.startsWith('Java');   // true
texto.endsWith('genial');   // true

// Modificar
texto.replace('genial', 'increíble');
texto.replaceAll('a', 'o');
texto.trim();               // Elimina espacios
texto.padStart(30, '.');
texto.split(' ');           // ['JavaScript', 'es', 'genial']
```

::header::
Semana 3: JavaScript Extendido

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Métodos de Array Adicionales

::contents::
```js
const numeros = [1, 2, 3, 4, 5];

// Reducir a un solo valor
const suma = numeros.reduce((acc, num) => acc + num, 0);
// 15

// Verificar si todos cumplen
const todosMayores = numeros.every(num => num > 0);
// true

// Verificar si al menos uno cumple
const algunMayor = numeros.some(num => num > 4);
// true

// Encontrar índice
const indice = numeros.findIndex(num => num === 3);
// 2

// Aplanar arrays
const nested = [1, [2, 3], [4, [5]]];
nested.flat(2);  // [1, 2, 3, 4, 5]
```

::header::
Semana 3: JavaScript Extendido

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Consejos para Vanilla JS

::contents::
✅ **Usar `console.log()`** extensivamente para debugging

✅ **Cargar scripts al final** del `<body>` o usar `defer`

✅ **Cache de selectores** DOM para mejor performance

✅ **Delegar eventos** cuando sea posible

✅ **Usar DevTools** del navegador para debugging

::header::
Semana 3: JavaScript Extendido

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# 🎉
