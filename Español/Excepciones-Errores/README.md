# Excepciones / Errores

## Índice

* [Conceptos Básicos](#básicos)
* [Bloque Try-Catch](#try-catch)

---

## Básicos

Las excepciones son casos de funcionamiento anormal en nuestro código que nos obligan a desviar el funcionamiento de nuestro programa a uno diferente, por lo que se les da un tratamiento especial a estos escenarios.

Para declarar o lanzar una nueva excepción hacemos uso de la palabra reservada `throw` la cual funciona similar que el `return` en las funciones.

Así como el `return`, podemos lanzar cualquier cosa, por lo que podríamos usar `throw` para lanzar un número, o un string... Aunque claro, no es la mejor idea; no es recomendable por ser considerado una mala práctica dentro de JavaScript. Dicho de otra forma, el hecho de que podamos lanzar cualquier cosa _no significa_ que debamos hacerlo.

Una vez que la ejecución de nuestro código llega al `throw`, la ejecución se detendrá, por lo que el flujo de nuestro programa se verá afectado. Se rompe.

Un pequeño ejemplo práctico podría ser que estemos fabricando juguetes. Durante la producción de estos juguetes, pueden haber algunos defectuosos, que serían nuestras excepciones.

```js
const JUGUETES_A_FABRICAR = 10;
const PROBABILIDAD_ERROR = 0.10;

const comprobarSiEsDefectuosa = () => Math.random() < PROBABILIDAD_ERROR;

for (let i = 1; i <= JUGUETES_A_FABRICAR; i++) {
  defectuosa = comprobarSiEsDefectuosa();

  if (defectuosa) throw new Error(`Juguete número ${i} defectuoso.`);
  else console.log(`Juguete número ${i} fabricado.`);
}
```

Como podemos ver en el ejemplo, el programa irá produciendo 10 juguetes en total a menos que alguno sea defectuoso, en cuyo caso lanzará una excepción.

También podemos apreciar que no estamos lanzando un string o número, sino que estamos lanzando un error haciendo uso de la clase `Error`.

[Volver arriba](#índice)

---

## Try-Catch

El bloque try catch es sencillo.

* En el bloque `try` colocamos el código a ejecutar.
* En caso de que haya un error, lanzamos dicho error de modo que el bloque `catch` lo atrape y se le pueda dar su tratamiento correspondiente.

```js
const JUGUETES_A_FABRICAR = 10;
const PROBABILIDAD_ERROR = 0.10;
let juguetesCorrectos = 0;
let juguetesDefectuosos = 0;

const comprobarSiEsDefectuosa = () => Math.random() < PROBABILIDAD_ERROR;

for (let i = 1; i <= JUGUETES_A_FABRICAR; i++) {
  defectuosa = comprobarSiEsDefectuosa();

  try {
    if (defectuosa) throw new Error(`Juguete número ${i} defectuoso.`);
    juguetesCorrectos++;
  } catch (err) {
    juguetesDefectuosos++;
  }
}

console.log(`Juguetes fabricados: ${JUGUETES_A_FABRICAR}:`);
console.log(`- Juguetes correctos: ${juguetesCorrectos}`);
console.log(`- Juguetes defectuosos: ${juguetesDefectuosos}`);
```

De igual forma, tenemos el bloque `finally`, el cual quiere decir a grandes rasgos que el código contenido por este será ejecutado indiferentemente de que el código del `try` sea exitoso o no. Sin importar que haya error no no, el `finally` se ejecutará.


```js
const JUGUETES_A_FABRICAR = 10;
const PROBABILIDAD_ERROR = 0.10;
let juguetesCorrectos = 0;
let juguetesDefectuosos = 0;

const comprobarSiEsDefectuosa = () => Math.random() < PROBABILIDAD_ERROR;

for (let i = 1; i <= JUGUETES_A_FABRICAR; i++) {
  defectuosa = comprobarSiEsDefectuosa();

  try {
    if (defectuosa) throw new Error(`Juguete número ${i} defectuoso.`);
    juguetesCorrectos++;
  } catch (err) {
    juguetesDefectuosos++;
  } finally {
    console.log("Este código se ejecutará en todos los casos.");
  }
}

console.log(`Juguetes fabricados: ${JUGUETES_A_FABRICAR}:`);
console.log(`- Juguetes correctos: ${juguetesCorrectos}`);
console.log(`- Juguetes defectuosos: ${juguetesDefectuosos}`);
```

[Volver arriba](#índice)