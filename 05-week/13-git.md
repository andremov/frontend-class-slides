---
theme: ../theme
transition: none
layout: cover
title: Git y Control de Versiones
exportFilename: 13-git
---

# Git
## Control de versiones

✏️ 2026-01 ➖ ⏱️ 60 min.

---
layout: cover
---

# Control de Versiones

---
layout: default-y-center
---

## El problema sin control de versiones

::contents::
```
proyecto-final.zip
proyecto-final-v2.zip
proyecto-final-ESTE.zip
proyecto-final-bueno.zip
proyecto-final-ahora-si.zip
proyecto-final-entrega-real.zip
```

¿Cuál es la versión correcta? ¿Qué cambió entre cada una?

::header::
Semana 5: Git

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Qué es el control de versiones

::contents::
Un sistema que **registra los cambios** de archivos a lo largo del tiempo.

Con Git puedes:
- Ver el historial completo de cambios
- Volver a cualquier versión anterior
- Trabajar en paralelo sin pisarte con otros
- Saber **quién** cambió **qué** y **cuándo**

::header::
Semana 5: Git

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: two-cols-centered
---

## Git vs GitHub

::left::
**Git**

Herramienta de control de versiones que corre en tu computador.

- Instalada localmente
- Gestiona el historial
- No necesita internet

::right::
**GitHub**

Plataforma en la nube para alojar repositorios Git.

- Repositorios remotos
- Colaboración en equipo
- Pull requests, issues

::header::
Semana 5: Git

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Repositorios y Primeros Pasos

---
layout: default-y-center
---

## Configuración inicial

::contents::
Lo primero: decirle a Git quién eres.

```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tu@email.com"
```

Solo se hace una vez por computador.

::header::
Semana 5: Git

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: two-cols-centered
---

## Crear vs Clonar un repositorio

::left::
**`git init`**

Convierte una carpeta existente en un repositorio Git.

```bash
mkdir mi-proyecto
cd mi-proyecto
git init
```

::right::
**`git clone`**

Descarga un repositorio remoto existente.

```bash
git clone https://github.com/usuario/repo.git
```

::header::
Semana 5: Git

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# El Flujo Básico

---
layout: default-y-center
---

## Área de staging

::contents::
Git tiene tres zonas:

```
Working Directory  →  Staging Area  →  Repository
  (tus archivos)      (git add)        (git commit)
```

- **Working Directory**: donde editas tus archivos
- **Staging Area**: cambios preparados para el próximo commit
- **Repository**: historial permanente de commits

::header::
Semana 5: Git

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## `git status`

::contents::
Muestra el estado actual del repositorio.

```bash
git status
```

```
On branch main

Changes not staged for commit:
  modified:   src/App.jsx

Untracked files:
  src/nuevo-componente.jsx
```

::header::
Semana 5: Git

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## `git add` y `git commit`

::contents::
```bash
# Agregar un archivo específico al staging
git add src/App.jsx

# Agregar todos los cambios
git add .

# Crear el commit con un mensaje
git commit -m "feat: add login button"
```

Un **commit** es un registro permanente del estado del proyecto en ese momento.

::header::
Semana 5: Git

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Mensajes de commit

::contents::
Un buen mensaje de commit describe **qué** se hizo y **por qué**.

```bash
# ❌
git commit -m "cambios"
git commit -m "arreglé cosas"
git commit -m "asdfg"

# ✅
git commit -m "fix: correct email validation regex"
git commit -m "feat: add user profile page"
git commit -m "style: fix button alignment on mobile"
```

Convención popular: `tipo: descripción breve en inglés`.

::header::
Semana 5: Git

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## `git log`

::contents::
Muestra el historial de commits.

```bash
git log
```

```
commit a3f8c21 (HEAD -> main)
Author: Ana García <ana@email.com>
Date:   Mon Feb 17 10:32:00 2026

    feat: add contact form

commit b1e4d09
Author: Ana García <ana@email.com>
Date:   Sun Feb 16 18:15:00 2026

    fix: correct navbar link
```

```bash
# Versión compacta
git log --oneline
```

::header::
Semana 5: Git

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Ramas (Branches)

---
layout: default-y-center
---

## Qué es una rama

::contents::
Una rama es una **línea de desarrollo independiente**.

```
main    ──●──●──────────────●──
               \           /
feature         ●──●──●──●
```

- `main` es la rama principal (código estable)
- Cada nueva funcionalidad se desarrolla en su propia rama
- Al terminar, se fusiona de vuelta a `main`

::header::
Semana 5: Git

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Trabajar con ramas

::contents::
```bash
# Ver todas las ramas
git branch

# Crear una rama nueva
git branch feature/login

# Cambiar a una rama
git checkout feature/login

# Crear y cambiar en un solo paso
git checkout -b feature/login

# Volver a main
git checkout main
```

::header::
Semana 5: Git

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## `git merge`

::contents::
Fusiona los cambios de una rama en la actual.

```bash
# Estando en main, fusionar feature/login
git checkout main
git merge feature/login
```

```
Antes:
main    ──●──●──
               \
feature         ●──●──●

Después:
main    ──●──●──────────●
               \       /
feature         ●──●──●
```

::header::
Semana 5: Git

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# GitHub y Repositorios Remotos

---
layout: default-y-center
---

## Conectar con GitHub

::contents::
```bash
# Ver los remotos configurados
git remote -v

# Conectar un repositorio local con GitHub
git remote add origin https://github.com/usuario/repo.git

# Verificar
git remote -v
# origin  https://github.com/usuario/repo.git (fetch)
# origin  https://github.com/usuario/repo.git (push)
```

`origin` es el nombre convencional para el remoto principal.

::header::
Semana 5: Git

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: two-cols-centered
---

## `git push` y `git pull`

::left::
**`git push`**

Envía tus commits locales al repositorio remoto.

```bash
# Primera vez
git push -u origin main

# Las siguientes veces
git push
```

::right::
**`git pull`**

Descarga los commits remotos e integra los cambios.

```bash
git pull
```

Hacerlo antes de empezar a trabajar es un buen hábito.

::header::
Semana 5: Git

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Pull Requests

::contents::
Un **Pull Request (PR)** es una solicitud para fusionar una rama en otra, revisada por el equipo.

Flujo típico:
1. Crear una rama: `git checkout -b feature/nueva-funcionalidad`
2. Hacer commits con los cambios
3. Subir la rama: `git push -u origin feature/nueva-funcionalidad`
4. Abrir un Pull Request en GitHub
5. El equipo revisa, comenta, aprueba
6. Se fusiona en `main`

::header::
Semana 5: Git

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Flujo en Producción

---
layout: default-y-center
---

## Ambientes de despliegue

::contents::
En un proyecto real, el código pasa por varios **ambientes** antes de llegar a los usuarios.

| Ambiente | Rama | Descripción |
|---|---|---|
| **Production** | `main` | Lo que ven los usuarios. Solo código probado. |
| **QA / Staging** | `qa` o `staging` | Pruebas finales antes de producción. |
| **Development** | `dev` | Integración continua del trabajo del equipo. |
| **Feature** | `feature/xxx` | Desarrollo de una funcionalidad específica. |

::header::
Semana 5: Git

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## El flujo de una funcionalidad

::contents::
```
feature/login ──●──●──●─────────────────────────
                          \
dev           ──●──────────●──●──●───────────────
                                    \
qa            ──●────────────────────●──●────────
                                            \
main          ──●────────────────────────────●───
```

Cada merge representa una **revisión y aprobación** antes de avanzar al siguiente ambiente.

::header::
Semana 5: Git

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Por qué este flujo

::contents::
- **`main`** nunca recibe código directamente — solo desde `qa` tras aprobar pruebas
- **`qa`** replica producción: permite encontrar bugs antes de que lleguen a usuarios
- **`dev`** es donde se integra el trabajo de todo el equipo continuamente
- **`feature/*`** aíslan el trabajo: si una funcionalidad falla, no afecta a los demás

::header::
Semana 5: Git

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Flujo completo en equipo

::contents::
```bash
# 1. Partir siempre desde dev actualizado
git checkout dev && git pull

# 2. Crear rama de feature
git checkout -b feature/nueva-funcionalidad

# 3. Desarrollar y commitear
git add . && git commit -m "feat: implement X"

# 4. PR: feature → dev  (revisión de código)
git push -u origin feature/nueva-funcionalidad
# Abrir PR en GitHub hacia dev

# 5. PR: dev → qa  (pruebas de integración)
# 6. PR: qa → main  (aprobación final → producción)
```

::header::
Semana 5: Git

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# Buenas Prácticas

---
layout: default-y-center
---

## `.gitignore`

::contents::
Archivo que le dice a Git qué archivos **no** rastrear.

```bash
# .gitignore

# Dependencias
node_modules/

# Variables de entorno
.env
.env.local

# Archivos de build
dist/
build/

# Archivos del sistema
.DS_Store
Thumbs.db
```

::header::
Semana 5: Git

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Conflictos de merge

::contents::
Ocurren cuando dos ramas modificaron la misma línea del mismo archivo.

```html
<<
<h1>Hola Mundo</h1>
==
<h1>Bienvenido</h1>
>>
```

Resolución:
1. Abrir el archivo con conflicto
2. Elegir qué versión conservar (o combinar ambas)
3. Eliminar los marcadores `<<<`, `===` y `>>>`
4. Hacer `git add` y `git commit`

::header::
Semana 5: Git

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Flujo de trabajo completo

::contents::
```bash
# 1. Actualizar main
git checkout main
git pull

# 2. Crear rama para la nueva tarea
git checkout -b feature/mi-feature

# 3. Desarrollar: editar, agregar, commitear
git add .
git commit -m "feat: implement X"

# 4. Subir la rama
git push -u origin feature/mi-feature

# 5. Abrir Pull Request en GitHub
# 6. Fusionar y repetir
```

::header::
Semana 5: Git

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: cover
---

# 🎉
