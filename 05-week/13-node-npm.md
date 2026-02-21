---
theme: ../theme
transition: none
layout: cover
title: Node.js y NPM
exportFilename: 13-node-npm
---

# Node.js y NPM

✏️ 2026-01 ➖ ⏱️ 20 min.

---
layout: default-y-center
---

## Qué es Node.js?

::contents::
Normalmente, JavaScript solo corre en el **navegador**.

**Node.js** es un entorno que permite ejecutar JavaScript **fuera del navegador**. \
O sea, en nuestro computador o en un servidor.

```bash
# Verificar que está instalado
node --version
```

Lo usamos principalmente como **herramienta de desarrollo**: para correr Vite, instalar paquetes, y ejecutar scripts.

::header::
Semana 5: Node.js y NPM

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Qué es NPM?

::contents::
**NPM** (Node Package Manager) es el gestor de paquetes de Node.

- Viene instalado junto con Node.js
- Permite **instalar librerías** que otros desarrolladores crearon

```bash
# Verificar que está instalado
npm --version
```

Como `pip` de Python.

::header::
Semana 5: Node.js y NPM

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## `package.json`

::contents::
El `package.json` es el **archivo de configuración** de tu proyecto.

```json
{
  "name": "mi-app",
  "version": "1.0.0",
  "scripts": {
    "dev": "vite",
    "build": "vite build"
  },
  "dependencies": {
    "react": "^19.0.0",
    "react-dom": "^19.0.0"
  },
  "devDependencies": {
    "vite": "^6.0.0"
  }
}
```

::header::
Semana 5: Node.js y NPM

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: two-cols-centered
---

## dependencies vs devDependencies

::left::
**`dependencies`**

Paquetes que necesita tu app para **funcionar en producción**.

- `react`
- `react-dom`
- `axios`

```bash
npm install react
```

::right::
**`devDependencies`**

Paquetes que solo se usan durante el **desarrollo**.

- `vite`
- `eslint`
- `typescript`

```bash
npm install vite --save-dev
```

::header::
Semana 5: Node.js y NPM

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## `node_modules`

::contents::
Al correr `npm install`, NPM descarga todos los paquetes en una carpeta llamada `node_modules`.

```
mi-app/
├── node_modules/    ← ⚠️ No tocar, no subir a git
├── src/
├── package.json
└── .gitignore       ← node_modules va aquí
```

- Contiene los archivos de todas las dependencias del proyecto, y las dependencias de estas, y así...
- Nunca se sube a git (está en `.gitignore`)
- Se puede regenerar en cualquier momento con `npm install`

::header::
Semana 5: Node.js y NPM

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Comandos esenciales de NPM

::contents::
```bash
# Instala todas las dependencias del proyecto
npm install

# Instala un paquete nuevo
npm install nombre-paquete

# Corre un script definido en package.json
npm run [script]

# Desinstala un paquete
npm uninstall nombre-paquete
```

::header::
Semana 5: Node.js y NPM

::footer::
{{ $page }} / {{ $nav.total }}

---
layout: default-y-center
---

## Flujo de trabajo típico

::contents::
```bash
# 1. Clonar o crear el proyecto
git clone https://github.com/usuario/proyecto.git
cd proyecto

# 2. Instalar dependencias (solo la primera vez)
npm install

# 3. Iniciar el servidor de desarrollo
npm run dev

# 4. Cuando terminas, build para producción
npm run build
# Aunque, a menudo, esto lo hace automaticamente el servidor
```

::header::
Semana 5: Node.js y NPM

::footer::
{{ $page }} / {{ $nav.total }}
