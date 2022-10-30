# Asincronismo

## Índice

* [Conceptos Básicos](#básicos)
* [Callback Hell](#callback-hell)
* [Promesas](#promesas)
* [Async-Await](#async-await)

---

## Básicos

El código _"normal"_ en JavaScript es síncrono, por lo que se ejecuta **siempre** en el mismo orden, y dicho orden se puede predecir fácilmente solo siguiendo la ejecución del código.

Un ejemplo sencillo es un bucle; sabemos siempre qué iteración se ejecutará.

Sin embargo, hay algunas situaciones en que no depende de nosotros, sino que dependería de un "tercero" como una API.

Al realizar una llamada a una API, sabemos cuándo realizamos tal llamada, mas no sabemos cuándo el servidor nos dará la respuesta.

Planteemos un ejemplo de vida cotidiana:

Supongamos que tenemos hambre. En tal caso, disponemos de 2 opciones:

1. Cocinamos.
2. Ordenamos comida.

En el primer caso, todo lo que ello implica depende de nosotros. Desde tener los ingredientes hasta cocinar.

En el segundo caso, solo la llamada al lugar depende de nosotros. Cuánto tardará la comida en llegar no depende de nosotros.

Un ejemplo sería con la función `setTimeout`:

```js
console.log("Holi");
setTimeout(() => console.log("Timeout"), 5000);
console.log("Soy Elizabeth");
```

En este ejemplo vemos que tenemos 3 mensajes a imprimir por consola. Por sentido común podríamos decir que primero se ejecuta el que imprime _"Holi"_, luego el que imprime _"Timeout"_ pasados 5 segundos y por último el que imprime _"Soy Elizabeth"_, pero los 2 mensajes fuera del timeout serán impresos antes que el Timeout mientras que transcurren esos 5 segundos. Ese es un código asíncrono. El Timeout depende del reloj, y ese reloj no es propio de JavaScript, sino que está en nuestra PC.

Una vez que el código síncrono se ejecuta, "comienzan" las ejecuciones asíncronas.

[Volver arriba](#índice)

---

## Callback-Hell

Uno de los "problemas" en lo que podemos caer es el llamado Callback Hell. Esto dicho de forma simple sería tener muchas funciones las cuales consecutivamente se pasen como callback a otras, dando como resultado un código difícil de leer y engorroso.

Un ejemplo:

```js
pan.pourWater(() => {
	range.bringToBoil(() => {
		range.lowerHeat(() => {
			pan.addRice(() => {
				setTimeout(() => {
					range.turnOff();
					serve();
				}, 15 * 60 * 1000);
			});
		});
	});
});
```

Una de las principales causas del Callback Hell es cuando las personas intentan escribir su código JavaScript de modo que la ejecución sea visualmente de arriba a abajo. Eso podría llegar a ser bueno en lenguajes como C o Java, pero recordemos que JavaScript es un poco especial...

¿Cómo evitamos el Callback Hell?

Bueno, muchos se quedan atrapados ahí por malas prácticas y falta de estructura del código, por lo que no se dan cuenta de lo mal que está estructurado el código hasta que es tarde. En todo código, siempre hay que darse un momento para pensar si lo que haces puede estar más legible y simple antes, durante y después de escribirlo.

Algunos puntos que podrían tener en cuenta para evitar el Callback Hell serían:

* **Diseño Modular**: 
En muchos lenguajes de programación se puede reducir mucho la complejidad del código al tener un diseño modular, y eso también aplica para JavaScript. Cada vez que estemos escribiendo código, es bueno tomarse un tiempo para volver atrás y ver si se encuentra un patrón que se esté repitiendo a menudo. Sea que estemos escribiendo el mismo código varias veces en diferentes lugares, o que las diferentes partes del código sigan un tema en común, esas son oportunidades para limpiar las cosas, abstraer y reutilizar el código.

* **Nombrar las funciones**:
Cuando estamos leyendo código, en especial uno desordenado, es muy fácil perdernos en la lógica del mismo, y más cuando el código está lleno de callbacks anidados... Una forma de ayudar a que esto no suceda es nombrar las funciones. Así, todo lo que tendremos que hacer es leer el nombre y tendremos una idea de lo que hace.

Ejemplo:

```js
const fs = require('fs');
let myFile = 'tmp/test';

fs.readFile(myFile, 'utf8', function(err, txt) {
	if (err) return console.log(err);
	txt = txt + '\nAppended something!';
	fs.writeFile(myFile, txt, function(err) {
		if (err) return console.log(err);
		console.log('Appended text!');
	});
});
```

Viendo esto, puede tomar un poco darnos cuenta de dónde comienza cada callback y qué hace...

Agregar un nombre a las funciones puede hacer una gran diferencia para la interpretación del código, y más cuando tenemos múltiples niveles de profundidad en los callbacks...

```js
const fs = require('fs');
let myFile = 'tmp/test';

fs.readFile(myFile, 'utf8', function appendText(err, txt) {
	if (err) return console.log(err);
	txt = txt + '\nAppended something!';
	fs.writeFile(myFile, txt, function notifyUser(err) {
		if (err) return console.log(err);
		console.log('Appended text!');
	});
});
```

Ahora, un simple vistazo bastaría para saber qué hace cada función.

* **Declarar las funciones al principio**:
Una de las mejores formas de no tener un código desordenado es ser estructurado y separar las cosas. Si declaramos una función callback desde el principio y la llamamos más adelante, evitamos esas estructuras anidadas que nos llevan a un Callback Hell.

Con eso en mente, podríamos cambiar el primer código a esto:

```js
const fs = require('fs');

const notifyUser = err => {
	if err return console.log(err);
	console.log('Appended text!');
};

const appendedText = (err, txt) => {
	if err return console.log(err);
	txt = txt + '\nAppended something!';
	fs.writeFile(myFile, txt, notifyUser);
};

let myFile = 'tmp/test';
fs.readFile(myFile, 'utf8', appendText);
```

Aunque esta es una muy buena forma de ayudar a disminuir el problema, no lo resuelve por completo. Ahí es donde entran las promesas, o mejor aún: async/await.

[Volver arriba](#índice)

---

## Promesas

Si bien puede parecer que las promesas son algo complicadas de entender al principio, es algo muy importante en JavaScript. Una forma de explicarlo podría ser la siguiente:

Supongamos que somos niños y nuestra madre _promete_ que nos dará un juguete nuevo la próxima semana. Realmente no sabemos si lo tendremos hasta la próxima semana, por lo que nuestra madre podría darnos el juguete, o podría no hacerlo si no tenemos un comportamiento adecuado.

Eso es una promesa. También, las promesas tienen 3 estados:

1. Promesa **pendiente**: No sabemos sin tendremos el juguete hasta la próxima semana.
2. Promesa **resuelta**: Hemos recibido el juguete nuevo.
3. Promesa **rechazada**: No obtuvimos el juguete por tener un mal comportamiento.

Si bien es cierto que las promesas son muy útiles, no son la solución definitiva a nuestros problemas de programación asíncrona, por lo que no debemos asumir que por usar promesas tendremos un código limpio, rápido y libre de bugs. La cosa es saber cuándo serán útiles.

[Volver arriba](#índice)

---

## Async-Await

Esta característica vino con ES6, y está disponible en NodeJS a partir de la versión 7.10.1 _si la memoria no me falla..._

Esta forma de mejorar el código nos permite escribir código asíncrono que se parezca mucho a un código síncrono.

Ejemplo:

```js
async function getUser(id) {
	if (id) return await db.user.byId(id);
	else throw 'Invalid ID!';
}

try {
	let user = await getUser(123);
} catch (err) {
	console.log(err);
}
```

Aquí, la llamada a `db.user.byId(id)` regresa una promesa, que normalmene tenemos que usar con `.then()`, pero con `await` podemos devolver el valor resultante directamente.

También destacar que la función contiene la llamada a `await` está declarada con el prefijo `async`, el cual nos dice que contiene código asíncrono y que también debe ser llamado con un `await`.

Otra cosa buena que tiene este método es que podríamos usar `try/catch`, `for` y `while` con nuestras funciones asíncronas, lo cual es mucho más intuitivo que intentar seguir una serie de promesas anidadas.

[Volver arriba](#índice)