# JSX
Antes de adentrarnos en JSX vamos a hacer un pequeño resumen de que o cual es la idea de usar React.

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

## Componentes

```jsx
const App = () => {
  return (
    <div>
      <p>Hola Goncy</p>
    </div>
  )
}
```
Definimos una función `App` en `PascalCase` (mayúscula al principio de cada palabra) que retorna código `JSX` (ya vamos a hablar de esto después). A esto lo llamamos un componente.

## ReactDOM.render

```jsx
ReactDOM.render(<App />, document.getElementById('root'))
```
Llamamos a la funcion `render` de ReactDOM pasandole nuestro componente `App` como si fuera un tag de HTML y el elemento del DOM donde queremos que nuestra aplicación se monte.

Como resultado obtenemos un `div` con un `p` dentro con el contenido `Hola Goncy`.

## Interpolación

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

## JSX

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

## Diferencias

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

## Props

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

## Fragments

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

[⏪ Herramientas para crear un proyecto](../00-tools) | [Estado ⏩](../02-state)