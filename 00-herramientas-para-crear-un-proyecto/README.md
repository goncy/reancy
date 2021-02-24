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

## Que es React?
* React es una librería para crear interfaces de usuario.
* Su sintaxis es parecida a `HTML` (o `XML`) y se llama `JSX`.
* React propone dividir nuestra aplicación en componentes que podamos reutilizar.

## Analizando una aplicación React
Veamos el código de una aplicación web en React:
```jsx
import ReactDOM from 'react-dom'

const App = () => {
  return (
    <div>
      <p>Hola Goncy</p>
    </div>
  )
}

ReactDOM.render(<App />, document.getElementById('root'))
```
> Asumimos que este archivo es importado desde un index.html y previamente compilado por create-react-app o vite.

Vamos a dividir esto en 3 partes:
```js
import ReactDOM from 'react-dom'
```
Importamos `ReactDOM`, una librería que sabe como convertir código React a vanilla js para ser comprendido por un navegador web.

```jsx
const App = () => {
  return (
    <div>
      <p>Hola Goncy</p>
    </div>
  )
}
```
Definimos una función `App` en `PascalCase` (mayúscula al principio de cada palabra) que retorna código `JSX` (ya vamos a hablar de esto después).

```jsx
ReactDOM.render(<App />, document.getElementById('root'))
```
Llamamos a la funcion `render` de ReactDOM pasandole nuestro componente `App` como si fuera un tag de HTML y el elemento del DOM donde queremos que nuestra aplicación se monte.

Como resultado obtenemos un `div` con un `p` dentro con el contenido `Hola Goncy`.

Volviendo a la definición de nuestro componente, también podemos usar código JavaScript dentro de el para luego usarlo en nuestra interfaz.

```jsx
const App = () => {
  const name = "Goncy";

  return (
    <div>
      <p>Hola {name}</p>
    </div>
  )
}
```
> Para usar código JavaScript dentro de le interfaz que devuelve nuestro componente, tenemos que envolverlo entre llaves.

Esta sintaxis que parece HTML / XML (lo que está entre parentesis luego del `return`) se llama `JSX`. En el proceso de compilación de nuestro código, realizado por vite, create-react-app o cual sea la herramienta que usemos, nuestro código JSX va a ser transformado a JavaScript vanilla para luego ser entendido por el navegador.

Y por que no usamos directamente JavaScript?

```js
var App = function App() {
  return React.createElement(
    'div',
    null,
    React.createElement(
      'p',
      null,
      'Hola Goncy'
    )
  );
};
```
Así se ve el código compilado y si bien no se ve "tan mal", cuando nuestros componentes empiezan a crecer, creeme que vas a agradecer estar escribiendo JSX.

Algunas diferencias con HTML / XML son:
* Los atributos de los elementos se escriben en camelCase (onClick en vez de onclick).
* class se escribe className (ya que class es una palabra reservada de JavaScript).

## Multiples componentes
React propone crear componentes que puedan ser reutilizados en nuestra aplicación, por ende podemos usar componentes dentro de componentes.

```jsx
import ReactDOM from 'react-dom'

const Hello = () => <h2>Holissss</h2>

const App = () => {
  const name = "Goncy";

  return (
    <div>
      <Hello />
      <Hello />
    </div>
  )
}

ReactDOM.render(<App />, document.getElementById('root'))
```
> Esto devolvería un div con dos h2 dentro que dicen Holissss

También podemos pasarle parametros a nuestros componentes (llamadas `props`) para agregar funcionalidad externa.

```jsx
import ReactDOM from 'react-dom'

const Hello = (props) => <h2>Holissss {props.name}</h2>

const App = () => {
  return (
    <div>
      <Hello name="Goncy" />
      <Hello name="Reancy" />
    </div>
  )
}

ReactDOM.render(<App />, document.getElementById('root'))
```
> Esto devolvería un div con dos h2 dentro que dicen Holissss Goncy y Holissss Reancy

Siempre que debamos pasar variables o código JavaScript debemos recordar que tiene que ser entre llaves, nuestras props no son la excepción.

```jsx
<Persona name="Goncy" edad={27 + 1} />
```

Una cosa a notar es que cada componente de React puede devolver un solo elemento, así que si debemos devolver mas de uno debemos crear un `fragment` (elemento vacío) para contenerlos.

```jsx
const App = () => {
  return (
    <>
      <Hello name="Goncy" />
      <Hello name="Reancy" />
    </>
  )
}
```

[⏪ Inicio](../) | [JSX ⏩](../01-JSX)