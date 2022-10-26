# Asincronismo

## Básicos

El código _"normal"_ en JavaScript es síncrono, por lo que se ejecuta **siempre** en el mismo orden, y dicho orden se puede predecir fácilmente solo siguiendo la ejecución del código.

Un ejemplo sencillo es un bucle; sabemos siempre qué iteración se ejecutará.

Sin embargo, hay algunas situaciones en que no depende de nosotros, sino que dependería de un "tercero" como una API.

Al realizar una llamada a una API, sabemos cuándo realizamos tal llamada, mas no sabemos cuándo el servidor nos dará la respuesta.

Planteemos un ejemplo de vida cotidiana:

Supongamos que tenemos hambre. En tal caso, disponemos de 2 opciones:

1. Cocinamos.
2. Ordenamos comida.

En el primer caso, todo lo que ello implica depende de nosotros. Desde tener los ingredientes hasta cocinarlo.

En el segundo caso, solo la llamada al lugar depende de nosotros. Cuánto tardará la comida en llegar no depende de nosotros.

