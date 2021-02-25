# Estado
Hasta el momento todos nuestros componentes fueron simples y no necesitaban actualizarse a lo largo de la vida de nuestra aplicación. Podemos pensar al estado como una (o varias) variables que almacenan datos que podemos usar en nuestra aplicación, que pueden cambiar a lo largo del tiempo de ejecución de la aplicación.

## useState
React nos provee un `hook` llamado `useState` que nos permite usar estado en nuestros componentes.

```jsx
import React, { useState } from 'react'
import ReactDOM from 'react-dom'

const App = () => {
  const [ counter, setCounter ] = useState(0)

  setTimeout(() => setCounter(counter + 1), 1000)

  return (
    <div>{counter}</div>
  )
}

ReactDOM.render(<App />, document.getElementById('root'))
```

`useState`, al llamarlo como una función (que recibe el estado inicial como parametro), nos devuelve un array con dos elementos, el primero va a ser el dato o estado y el segundo es la función `setter`, que cada vez que la llamemos va a actualizar el valor del estado.

> Podés imaginarte que pasaría en esta aplicación?

## Re-rendering
En nuestros ejemplos anteriores, toda nuestra información era estática, por lo tanto no debíamos preocuparnos por como haríamos para actualizar la información que nuestra aplicación muestra en pantalla.

En realidad es bastante simple. Los únicos casos en los que un componente se volvería a renderizar (pintar su contenido en pantalla), es cuando las `props` o el `state` cambian.

### Actualizando el estado
Entonces, para actualizar el estado solo tengo que hacer `counter = counter + 1`?. NO.
Para actualizar el estado debemos usar la función `setter` que nos devuelve `useState`, eso va a hacer que nuestro componente se vuelva a renderizar con el nuevo estado. Vamos a volver al ejemplo de arriba y veamos que pasa.

Tenemos el siguiente componente:
```jsx
const App = () => {
  const [ counter, setCounter ] = useState(0)

  setTimeout(() => setCounter(counter + 1), 1000)

  return (
    <div>{counter}</div>
  )
}
```

Primer render (cuando la aplicación se monta):
```jsx
const App = () => {
  const [ counter, setCounter ] = useState(0)

  // Reemplazamos counter por lo que valdría en el primer render
  setTimeout(() => setCounter(0 + 1), 1000)

  // Reemplazamos counter por lo que valdría en el primer render
  return (
    <div>{0}</div>
  )
}
```

Después de 1 segundo (cuando se ejecuta el `setTimeout`), se llama a la función setter y se actualiza nuestro estado, por ende tenemos un segundo render:
Primer render (cuando la aplicación se monta):
```jsx
const App = () => {
  const [ counter, setCounter ] = useState(0)

  // Reemplazamos counter por lo que valdría en el segundo render
  setTimeout(() => setCounter(1 + 1), 1000)

  // Reemplazamos counter por lo que valdría en el segundo render
  return (
    <div>{1}</div>
  )
}
```

Nuestro componente se vuelve a renderizar, por ende el `setTimeout` se vuelve a setear! Vuelve a setear nuestro estado después de un segundo y esto se repite infinitamente.

[⏪ JSX](../01-jsx) | [Eventos ⏩](../03-events)
