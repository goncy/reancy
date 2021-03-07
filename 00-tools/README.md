# Herramientas para crear un proyecto
Tenemos varias maneras de crear un proyecto en React, vamos a repasar algunas de las que más me gustan.

### CodeSandbox
[CodeSandbox](https://codesandbox.io/) es un entorno de desarrollo para distintas tecnologías, que nos permite crear proyectos basados en plantillas previamente creadas. Por lo que con solo un click podemos tener un proyecto de React + TypeScript corriendo en la nube sin bajar nada previamente.

### Create React App
[Create React App](https://create-react-app.dev/) es una herramienta creada y mantenida por el equipo de React, que nos permite con un solo comando, crear un proyecto React. También posee plantillas que nos permiten extender sus funcionalidades (como la integración con TypeScript) y está pensada para ser `zero config`, esto significa, que si bien podemos extender sus funcionalidades mediante configuraciónes e instalación de dependencias, no necesitamos configurar nada para empezar a usarla.

Para crear un proyecto React + TypeScript podemos correr:
```bash
# NPM
npx create-react-app mi-app --template typescript

# Yarn
yarn create react-app mi-app --template typescript
```
> Esto crearía una carpeta `mi-app` en donde estemos parado con nuestra terminal.

### Vite
[Vite](https://vitejs.dev/) es una herramienta de desarrollo (de similar uso a `create-react-app`) que nos permite crear aplicaciónes en diversas tecnologías con solo un comando. Su velocidad y performance es mayor actualmente a `create-react-app`.

Para crear un proyecto React + TypeScript podemos correr:
```bash
# NPM
npx @vitejs/app mi-app --template react-ts

# Yarn
yarn create @vitejs/app mi-app --template react-ts
```
> Esto crearía una carpeta `mi-app` en donde estemos parado con nuestra terminal.

[⏪ Inicio](../) | [JSX ⏩](../01-jsx)