---
title: Happy Path
theme: ../theme
transition: none
layout: cover
exportFilename: 13b-happy-path
---

# Happy Path

✏️ 2025-03 ➖ ⏱️ 7 min.

---
layout: center
---

## Como visualizan un algoritmo?

::header::
Relleno: Happy Path

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Como visualizan un algoritmo?

::contents::
![img](./assets/happy-path-01.png)

::header::
Relleno: Happy Path

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## "Early Return"

::contents::
![img](./assets/happy-path-02.png)

::header::
Relleno: Happy Path

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Early Return

::contents::
Un *Early Return* es un **guard clause** que, como el nombre lo indica, es un retorno temprano, antes de siquiera iniciar el procesamiento.

::header::
Relleno: Happy Path

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## "Early Return"

::contents::
![img](./assets/happy-path-02.png)

::header::
Relleno: Happy Path

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## "Guard Clause"

::contents::
![img](./assets/happy-path-03.png)

::header::
Relleno: Happy Path

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Guard Clause

::contents::
Un guard clause es como un early return, pero en medio del procesamiento.

::header::
Relleno: Happy Path

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## "Guard Clause"

::contents::
![img](./assets/happy-path-03.png)

::header::
Relleno: Happy Path

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## "if" Branch

::contents::
![img](./assets/happy-path-04.png)

::header::
Relleno: Happy Path

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## "if-else" Branch

::contents::
![img](./assets/happy-path-05.png)

::header::
Relleno: Happy Path

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Guard Clause 2

::contents::
![img](./assets/happy-path-06.png)

::header::
Relleno: Happy Path

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Guard Clause 3

::contents::
![img](./assets/happy-path-07.png)

::header::
Relleno: Happy Path

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Happy Path

::contents::
![img](./assets/happy-path-07.png)

Lo que llamamos el "happy path" es el camino verde.

Es cuando todo va bien, todos los datos son correctos y el algoritmo va de inicio a fin de la manera mas directa.

::header::
Relleno: Happy Path

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Happy Path

::contents::
![img](./assets/happy-path-07.png)

::header::
Relleno: Happy Path

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Happy Path & Fail-fast System

::contents::
Un sistema "fail-fast" (falla rapido) es un sistema que detiene o cancela la operación en vez de intentar continuar con la operación de manera posiblemente incorrecta.

::header::
Relleno: Happy Path

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-center
---

## Fail-fast System

::contents::
"Si algo anda mal, cancela todo."

::header::
Relleno: Happy Path

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Fail-fast System

::contents::
Entonces, un sistema con **Early Returns** y **Guard Clauses** es un sistema "Fail-fast".

::header::
Relleno: Happy Path

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Bouncer Pattern

::contents::
Patrón de diseño donde se implementan **Early Returns** y **Guard Clauses** para evitar que se realice un proceso de manera incorrecta o datos incorrectos.

Saca su nombre de los "bouncers", el guardia de seguridad presente en las entradas a discotecas o clubs VIP, que solo permite la entrada a cierta gente.

::header::
Relleno: Happy Path

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Fail-fast System & Bouncer Pattern

::contents::
Entonces un _fail-fast system_ está usando el _bouncer pattern_.

Comúnmente en backend se utiliza el _bouncer pattern_, se construye un _fail-fast system_.

::header::
Relleno: Happy Path

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Ejemplo Muy Básico

::contents::
```js
function attemptLogin(username, password) {

// **espacio 1**

// codigo que busca el usuario en la base de datos

// **espacio 2**

// codigo que verifica la contraseña ingresada con la contraseña de la base de datos

// **espacio 3**

// codigo que responde con OK o Error si el login es exitoso o fallido.

// **espacio 4**

}
```

1. Donde validamos que el usuario y contraseña pasados por parametro son validos? (Por ejemplo, no vacios.)
2. Donde validamos que el usuario existe en la base de datos?

::header::
Relleno: Happy Path

::footer::
{{ $page }} / {{ $nav.total }}
