![BlackBox Vision](./assets/logo.png "BlackBox Vision")

QuizBox Vision es un juego de preguntas y respuestas, como tantos otros. Sin embargo, en este juego, se ponen muchas más cosas en juego!! Bueno, en realidad no, pero quedaba bien para el resúmen.

## Definición funcional
El juego consiste en 10 preguntas las cuales pueden ser verdadero/falso o multiple choice y se obtienen de [la siguiente API](https://opentdb.com/api.php?amount=10).

Por cada pregunta, es necesario mostrar los siguientes campos:
* Pregunta
* Categoría
* Dificultad
* Posibles respuestas

Al finalizar el juego, se muestra el puntaje obtenido. El mismo se calcula de la
siguiente manera:
* Respuesta correcta: *5 puntos*
* Respuesta incorrecta: *0 puntos*

## Modalidad de entrega
* Repositorio público subido a GitHub, Gitlab, Bitbucket.
* Link a la aplicación funcionando.

## Estrellas extra
* Usar TypeScript y tipar todos los elementos que usa la aplicación. ⭐️
* Cada pregunta se muestra en una pantalla separada. ⭐️
* Las preguntas de multiple choice suman 10 puntos y las de verdadero o falso suman 5 puntos. ⭐️