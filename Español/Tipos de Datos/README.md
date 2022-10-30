# Tipos de Datos

## Índice

* [Conceptos Básicos](#básicos)
* [Strings](#strings)
* [Numbers](#numbers)
* [Booleans](#booleans)
* [Especiales](#especiales)
* [Object](#object)
* [Functions](#functions)
* [Operador typeof](#typeof)

---

## Básicos

En JavaScript disponemos de varios tipos de datos, como puede ser el string, number, boolean...

Todos esos tipos de datos son útiles dentro del lenguaje y pueden cumplir muchas tareas dependiendo del caso y la necesidad, teniendo en cuenta las consideradas _"buenas prácticas"_ dentro del lenguaje.

Echemos un vistazo.

[Volver arriba](#índice)

---

## Strings

Los strings, o _cadenas de texto_ se declaran utilizando comillas. Sean comillas dobles `""` o comillas simples `''`.

Ejemplo: 

```js
let stringComillaSimple = '¡Holi!';

let stringComillaDoble = "¡Hola!";
```

Ahora bien, si se preguntan cuándo se usaría una u otra, es muy sencillo: usaremos la que necesitemos. Personalmente tiendo a usar comillas dobles a menos que necesiten usarlas dentro del string.

Además, tenemos una tercera forma de declarar strings, que serían los llamados _template strings_. Estos son usados principalmente para añadir variables dentro de un string.

Ejemplo:

```js
let nombre = "Elizabeth";
let apellido = "Snow";

console.log(`¡Hola! Me llamo ${nombre} ${apellido}.`);
```

Como se puede ver, usamos esos strings que tenemos almacenados en las variables para imprimir un mensaje por consola usando un template string. Como habrán notado, usamos `${}` para incorporar las variables.

[Volver arriba](#índice)

---

## Numbers

Una cosa a tener en cuenta respecto a los números en JavaScript es que no hay un tipo `integer` ni un tipo `float`. Todos son números, indiferentemente de que sean enteros, decimales o negativos.

```js
let num1 = 21;
let num2 = -21;
let num3 = 135.7;
let num4 = -135.7;
let num5 = 21e25;
```

Como podemos ver, todos son números.

Por supuesto, todas las operaciones matemáticas están disponibles...

```js
let edad = 21;

console.log(edad + 13);
console.log(edad - 5);
console.log(edad * 7);
console.log(edad / 3);
console.log(edad % 5);
```

También tenemos algunos operadores de asignación que nos acortan algunas operaciones.

Por ejemplo:

```js
let num1 = 7;
num1  = num1 + 3;
console.log(num1);
// Esto imprime 10 en consola.

let num2 = 5;
num += 4;
console.log(num2);
// Esto imprime 9 en consola.
```

Se puede apreciar que es más corto y sencillo.

[Volver arriba](#índice)

---

## Booleans

Como en todo lenguaje de programación, tenemos los valores booleans. Estos solo son 2 posibles valores: `true` o `false`. Verdadero o falso, sí o no.

Estos valores son extremadamente útiles en muchas situaciones, y por ende los vamos a usar muy a menudo.

Un ejemplo muy rápido de uso de boolean sería algo como...

_"Si esto es **true**, entonces haz esto. De lo contrario, si es **false**, haz esto."_

[Volver arriba](#índice)

---

## Especiales

Tenemos otros 3 tipos, que serían `undefined`, `null` y `NaN`.

Estos tipos son un poco especiales...

- **Undefined** es el valor por defecto de toda variable, pero no de las constantes. Simplemente significa, como indica la palabra, que la variable _aún_ no tiene un valor definido, por lo que eso puede ser cambiado. Básicamente una variable vacía.

- **Null** es parecido a undefined, pero con la diferencia de que este no es un valor por defecto, sino que es intencional. El valor sera null porque así lo especificas.

- **NaN**, Not a Number, es el resultado de intentar realizar operaciones matemáticas con valores que no son números. Por ejemplo, si intentamos la operación `17 * "Holi"` devolverá NaN.

[Volver arriba](#índice)

---

## Object

Un objeto es, de forma simple, una variable con múltiples valores dentro.

Ejemplo:

```js
const nombres = ["Elizabeth", "Chloe", "Alex"];

const elizabeth = {
  nombres: "Elizabeth Alejandra",
  apellidos: "Snow Blake",
  edad: 21
}
```

**Ambos** son objetos para JavaScript.

Lo sé, algunos de ustedes podrán pensar _"Eso no es un objeto. ¡Es un array!"_

**Sí pero no.**

Aún cuando podemos crear un _"array"_ en JavaScript, sigue siendo un objeto. Más abajo verán a qué me refiero.

[Volver arriba](#índice)

---

## Functions

Síp, las funciones también son su propio tipo de dato.

```js
function saludo(nombre) {
  console.log(`¡Hola, ${nombre}!`);
}
```

[Volver arriba](#índice)

---

## Typeof

Disponemos también del operador `typeof` que nos servirá para saber el tipo de algún dato.

Ejemplo:

```js
console.log(typeof "¡Holi!");
// Imprime "string"

console.log(typeof 15);
// Imprime "number"

console.log(typeof true);
// Imprime "boolean"

console.log(typeof undefined);
// Imprime "undefined"

console.log(typeof null);
// Imprime "object"

console.log(typeof NaN);
// Imprime "number"

console.log(typeof [])
// Imprime "object"
// Les dije que es un objeto :P

console.log(typeof {})
// Imprime "object"

console.log(typeof function(){})
// Imprime "function"
```

[Volver arriba](#índice)