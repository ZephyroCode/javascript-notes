# Variables

## Índice

* [Conceptos Básicos](#básicos)
* [Constantes](#constantes)

---

## Básicos

Las variables en JavaScript son un poco especiales comparadas con otros lenguajes como C++ o Java. Lo primero sería que no tienen tipos; cada variable tiene un tipo de dato dinámico. Esto significa que puedes crear una variable con un número, y más tarde cambiarlo a un string, un boolean, o un objeto según se necesite.

Hay 2 formas de declarar una variable en JavaScript:

* `var`
* `let`

Usar la palabra reservada `var` no se recomienda hoy día dado que causa algunos problemas con el ámbito de las variables. Por lo tanto, **NO usar var**.

Usar `let` es básicamente el modo de declarar variables actualmente debido principalmente al ámbito.

Tener en cuenta que dentro del mismo contexto/ámbito, no podemos declarar variables con el mismo nombre.

Los nombres de las variables pueden comenzar con:

* `$`
* `_`
* Cualquier letra.

No se puede comenzar el nombre de una variable/constante/clase/función con un número, por lo que `1producto` simplemente no funciona.

Además, tenemos varias palabras reservadas que no pueden ser usadas como identificadores/nombres:

- **A**: `abstract`.

- **B**: `boolean`, `break`, `byte`.

- **C**: `case`, `catch`, `char`, `class`, `const`, `continue`.

- **D**: `debugger`, `default`, `delete`, `do`, `double`.

- **E**: `else`, `enum`, `export`, `extends`.

- **F**: `false`, `final`, `finally`, `float`, `for`, `function`.

- **G**: `goto`.

- **I**: `if`, `implements`, `import`, `in`, `instanceof`, `int`, `interface`.

- **L**: `long`.

- **N**: `native`, `new`, `null`.

- **P**: `package`, `private`, `protected`, `public`.

- **R**: `return`.

- **S**: `short`, `static`, `super`, `switch`, `synchronized`.

- **T**: `this`, `throw`, `throws`, `transient`, `true`, `try`, `typeof`.

- **V**: `var`, `volatile`, `void`.

- **W**: `while`, `with`.

```js
let nombre = "Elizabeth";
```

Aquí puede verse como una variable es declarada.

1. Palabra reservada.
2. Identificador de la variable.
3. Operador de asignación.
4. Valor.

También, algo que se ha de recordar es que las variables por convención se escriben en _camelCase_. Primera letra en minúsculas, y si tienes más de una palabra en el identificador, la primera letra de la segunda palabra en adelante, en mayúsculas.

También podría usarse *snake_case*...

```js
let el_rey_del_norte = "Jon Snow";
```

Ahora, algunos de los más nuevos podrían preguntarse _"¿Por qué necesito declarar variables?"_

Bueno, es simple: porque necesitas usar sus valores durante la ejecución del programa.

Un ejemplo rápido:

```js
let precio =  37;
let cantidad = 3;

let total = precio * cantidad;
console.log(total);
```

Sí, muy básico el ejemplo, pero con eso se hacen a la idea.

[Volver arriba](#índice)

---

## Constantes

Además de las variables, tenemos las constantes. Como el nombre indica, es una variable que **nunca** va a cambiar su valor.

Otro detalle es que los identificadores de las constantes se suelen escribir en mayúsculas separando las palabras con guión bajo.

Por supuesto, la palabra reservada a utilizar es `const`.

Ejemplo:

```js
const ZEPHYRO_BLOG = "https://zephyrocode.github.io";
```

[Volver arriba](#índice)