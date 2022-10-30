# Document Object Model

## Índice

* [Conceptos Básicos](#básicos)
* [Selectores](#selectores)
* [Manipulación del DOM](#manipulación)
* [Eventos](#eventos)
* [Event Bubbling](#bubbling)

---

## Básicos

El DOM (Document Object Model, Modelo del Objeto Document) es esa "interfaz" que permite interactuar con HTML y CSS mediante JavaScript, de modo que le podamos dar funcionalidad a nuestra web.

En JavaScript disponemos del objeto `document` que contiene todos los elementos y propiedades HTML, y también contamos con una serie de métodos que nos facilitarán la interacción/manipulación con tal objeto.

Por ejemplo, si vamos a la consola del navegador y simplemente escribimos `document`, la consola nos daría una representación del HTML. De igual forma, tenemos por encima del DOM al BOM, Browser Object Model, que es el objeto `window` el cual tiene funcionalidades propias del navegador y que no necesariamente tendrán relación con `document`. Un ejemplo del objeto `window` es el típico `alert()` o el `console.log()` que al llamarlos, sería lo mismo que llamar a `window.console.log()`

El DOM podría verse como un árbol. El objeto `document` es la base de la que sale la etiqueta `html`, y desde esta salen las etiquetas `head` y `body`. Así sucesivamente con cada elemento.

Todos los elementos del DOM son nodos. Desde el propio objeto `document` hasta los elementos en sí. Un nodo es un tipo de objeto en JavaScript que posee una serie de propiedades.

Entre las propiedades comunes de los nodos, tenemos 2 que se tienen muy en cuenta:

- parentElement
- children

Y de igual forma, el document es su propio objeto como ya se había comentado, y a partir de ahí, cada elemento es de tipo element.

[Volver arriba](#índice)

---

## Selectores

Dentro del DOM tenemos varios selectores para poder obtener los elementos de nuestro HTML y poder manipularlos.

* Selector por ID: `getElementById()` es el selector que permite obtener un elemento de nuestro HTML mediante su atributo `id=""` como por ejemplo: `document.getElementById('navbar-button');` Y si la ID que le damos no la encuentra o no existe, nos devuelve `null`.
* Selector por clase: `getElementsByClassName()` nos devuelve una lista/objeto/colección de HTML de todos los elementos que compartan la clase que le damos al selector. 
* Selector por Etiqueta: `getElementsByTagName()` nos selecciona todos los elementos del mismo tipo que el seleccionado, como `getElementsByTagName('li');` y nos devuelve un listado de estos.
* Selector por Propiedad Name: `getElementsByName()` nos devolverá el listado de elementos que en el HTML tengan el mismo valor de la propiedad `name=""`.

Estos 4 selectores son muy útiles, pero también podrían usarse otros 2 en su lugar:

* Query Selector: `querySelector()` nos devuelve el primer elemento encontrado que coincida con el selector de CSS que le damos, como en `querySelector('.nav__link');`.
* Query Selector All: `querySelectorAll()` nos devuelve un listado de todos los elementos que coincidan con el selector de CSS que le damos. `querySelectorAll('.nav__link')`.

Una cosa a tener en cuenta es que todos estos selectores que devuelven listados pueden devolver un tipo de listado diferente.

Algunos devuelven un listado de tipo `HTMLCollection` y otros devuelven uno de tipo `NodeList`.  La principal diferencia es que una es estática y la otra es dinámica.

El listado `HTMLCollection` es dinámico, por lo que si añadimos o quitamos un elemento de tal listado, se actualizará de forma dinámica.

El listado `NodeList` es estático, por lo que una vez definida la lista, ya no se actualizará.

Otra cosa a considerar es que estos listados **no son arrays**, por lo que los métodos habituales de arrays no están disponibles, como el método `forEach()`.

Una forma de transformar estos listados en arrays sería usando el spread operator:

```js
const lista = document.getElementsByClassName('nav__link');

const arrayElementos = [...lista];
```

[Volver arriba](#índice)

---

## Manipulación

JavaScript nos proporciona una serie de métodos que podemos utilizar para poder alterar nuestro DOM, ya sea creando elementos, insertarlos, editarlos o removerlos.

Veamos algunos:

* `document.createElement()`: Este método recibe 2 parámetros; la etiqueta del elemento a crear y un objeto de propiedades, siendo este parámetro opcional. Un ejemplo podría ser el siguiente: `const titulo = document.createElement('h1');`
* `document.createTextNode()`: Este método nos permite crear un nodo de texto el cual podremos insertar en un elemento del DOM. `const textoTitulo = document.createTextNode('Título Potente');`
* `.cloneNode()`: Este método permite seleccionar un elemento existente del DOM y clonarlo para poder editarlo o duplicarlo posteriormente. Este método se aplica al elemento a duplicar, y admite un parámetro que recibe true o false. False si no le damos algo, true si se lo especificamos, y la utilidad de este parámetro es indicar al método si queremos que se copie el elemento completo incluyendo hijos o si queremos clonarlo individual. `const clonTitulo = titulo.cloneNode();`
* `.isConnected`: Esto nos será de utilidad ara saber si un elemento se encuentra existente en nuestro DOM o si solo está en memoria de JavaScript. Esto nos devuelve true o false.
* `.appendChild()`: Este método se ha de aplicar al elemento padre del elemento que querems insertar en nuestro DOM. Por ejemplo, si tenemos un section y queremos añadir un article dentro de él, primero seleccionamos tal section y usamos este método en él, y el parámetro que el método admite es el nodo a insertar. Tener en cuenta también que este método añade el elemento como último hijo del elemento padre.
* `insertAdjacentElement()`: Este método nos permite añadir un elemento como primer hijo de un elemento, como último hijo, como hermano superior, o como hermano inferior. Este método admite 2 parámetros; el string que indica la posición y el elemento a insertar. Tenemos 4 posibles posiciones: `beforebegin` lo coloca como hermano superior, `beforeend` lo coloca como último hijo, `afterbegin` lo coloca como primer hijo y `afterend` lo coloca como hermano inferior.
* `insertAdjacentText()`: Esto nos permite insertar texto sin la necesidad de crear un nodo de texto, y funciona exactamente igual que el método `insertAdjacentElement()`.
* `insertAdjacentHTML()`: Permite insertar código HTML directamente sin crear los elementos, y también funciona igual que `insertAdjacentElement()`.
* `.remove()`: Este método nos permite remover un elemento del DOM, mas no lo elimina de la memoria, por lo que podemos tenerlo almacenado en una variable y removerlo o recolocarlo según sea necesario.
* `.innerHTML`: Esta propiedad puede servir para saber el HTML que tiene contenido el elemento, sino también para alterarlo.
* `.outerHTML`: Esta propiedad nos permite saber el HTML del elemento seleccionado o bien alterarlo por completo.
* `.innerText`: Esta propiedad nos permite saber o editar el contenido _de texto_ que tenga el elemento seleccionado.
* `.getAttribute()`: Este método nos permite obtener el valor del atributo que le damos como parámetro, como podría ser `navLink.getAttribute('href');`
* `.setAttribute()`: Este método admite 2 parámetros; el atributo a modificar y el nuevo valor de este, como puede ser `navLogo.setAttribute('src', 'michi.jpg');`
* `.classList`: Esta propiedad nos devuelve un listado de todas las clases que tiene el elemento seleccionado. Además, podemos usar los métodos `.add()`, `.remove()`, `.toggle()` para añadir y remover clases.
* `.className`: Esta propiedad no da la capacidad de saber o alterar la clase del elemento seleccionado.

[Volver arriba](#índice)

---

## Eventos

Los eventos son sucesos o acciones que ocurren en algún momento. En JavaScript, estos eventos suceden cuando el usuario interactúa con los elementos del DOM. Esto nos permite tomar ventaja de tales eventos para ejecutar ciertas acciones en función del evento en cuestión.

La forma de poder "escuchar" los eventos es con el método `addEventListener()` el cual se aplica al elemento en el cual vayamos a escuchar los eventos. Este método admite 2 parámetros; el evento a esuchar como string, y el callback/función que vamos a ejecutar cuando el evento suceda. Esta forma es la más recomendada y la que _siempre_ recomendaría utilizar. Esta manera dspone de muchos más eventos que otras formas, además de ser más flexible. Además, contamos con una ventaja extra para mayor interactividad y que da más juego a los eventos, y es el método `removeEventListener()` el cual admite los mismos parámetros y su utilidad es remover la función a ejecutar una vez que se produzca el evento, por lo que podríamos deshabilitar ciertos eventos en un elemento y habilitarlos usando otro.

Aquí tenemos una pequeña lista de _algunos_ de los eventos disponibles:

- `click`: Se activa al hacer click en el elemento como dice el nombre.
- `dbclick`: Se activa con un doble click.
- `mouseover`: Se activa cuando el puntero se mueve sobre un elemento o sobre uno de sus hijos.
- `mouseout`: Se activa cuando el puntero deja de estar sobre un elemento o uno de sus hijos.
- `contextmenu`: Se activa al hacer click drecho en un elemento para abrir el menú contextual.
- `mouseenter`: Se activa al pasar el puntero sobre un elemento.
- `mouseleave`: Se activa cuando el puntero deja de estar sobre un elemento.
- `mousedown`: Se activa cuando se presiona el click sobre un elemento.
- `mouseup`: Se activa cuando el click se levanta de un elemento.
- `mousemove`: Se activa cuando el puntero se mueve en un elemento.
- `keydown`: Se activa cuando una tecla se presiona. 
- `keyup`: Se activa cuando una tecla se deja de presionar.
- `DOMContentLoaded`: Se activa cuando el contenido del DOM se ha cargado por completo. Es decir, cuando nuestro HTML ha sido cargado.
- ``

De igual forma, tenemos en la función a ejecutar en el evento, el parámetro del propio evento para poder utilizarlo dentro de la función.

Un ejemplo:

```js
const titulo = document.querySelector('#titulo');
const clickTitulo = event => console.log(event);

titulo.addEventListener('click', clickTitulo);
```

También tenemos la posibilidad de escuchar los eventos directamente desde nuestro HTML, aunque no es lo más recomendado en muchos casos... Para hacerlo, se añade el atributo `onclick="conquistarElMundo()"` de modo que se usa `on` y el evento. Esta forma no se recomienda mucho pues se ensucia el código HTML con algo que _tendría_ que estar en el fichero de JavaScript. Si bien es cierto que puede ser práctico, no es lo mejor. Hay también quienes lo consideramos mala práctica.

También tenemos el método `onclick()` que funciona igual que hacerlo en el HTML, y aún sigue sin ser la mejor opción. `boton.onclick = conquistarElMundo;`. Esta forma a pesar de tener la ventaja de que lo estamos haciendo directamente desde el código JavaScript, es poco práctica considerando que tenemos una mejor forma, la cual sería con el método `addEventListener()` comentado antes.

Uno de los ejemplos más comunes de manejo de eventos es con un formulario.

```js
const formulario = document.getElementById('formulario');
const enviarFormulario = event => console.log(event);

formulario.addEventListener('submit', enviarFormulario);
```

Si intentamos ejecutar ese código tal cual está, la página se refrescará, o mejor dicho, se enviará al presionar el botón de submit, por lo que no podremos apreciar el `console.log` del evento submit, pues hay algunos eventos que tienen unos ciertos comportamientos ya predefinidos. Por tal motivo, se maneja el evento submit de un modo "especial", así que el código continúa de la siguiente forma:

```js
const formulario = document.getElementById('formulario');
const enviarFormulario = event => {
	event.preventDefault();
	console.log(event);
};

formulario.addEventListener('submit', enviarFormulario);
```

Ahora hemos añadido el método `.preventDefault()` al evento, por lo que el comportamiento predefinido del mismo será "anulado" de modo que le indicamos al evento que queremos tener total control sobre lo que sucede al ejecutarse.

Ahora, supongamos que tenemos un formulario sencillo con 3 input y un botón. Un input para nombre, otro para correo y otro para contraseña. Esos 3 input con un atributo `name=""`. Podríamos tomar el valor introducido en esos input al presionar el botón.

```js
const formulario = document.getElementById('formulario');
const enviarFormulario = event => {
	event.preventDefault();
	const {nombre, email, contra} = event.target;
	
	console.log(name.value, email.value, contra.value);
};

formulario.addEventListener('submit', enviarFormulario);
```

Aquí podemos ver que al hacer un submit, se imprimirá por consola lo introducido en los inputs.

[Volver arriba](#índice)

---

## Bubbling

Para comprender esto tenemos que saber que al escuchar un evento hay 3 fases:

1. Captura. Esta fase empieza en la etiqueta HTML y va bajando en sus hijos hasta localizar el elemento en el que se produce el evento.
2. Target. Esta fase es donde se identifica que el elemento tiene un event listener asociado al evento que ha ocurrido.
3. Bubbling. Esta fase no siempre está presente, pero se trata de cuando tenemos el mismo evento en 2 elementos padre e hijo y hará que se ejecute en ambos. Es decir, supongamos que tenemos un `h1` que tiene como uno un `em` y en ese `em` tenemos un `addEventListener('click', conquistarElMundo)` y en el h1 tenemos `addEventListener('click', conquistarElUniverso)`, pues al dar click en el `em` no solo activaremos la función `conquistarElMundo`, sino que también activaremos la función `conquistarElUniverso` debido a esta fase. Podría verse como la fase de capturing al revés.

Veamos un ejemplo:

```js
const articulo = document.querySelector('#articulo');
const titulo = document.querySelector('#titulo');

titulo.addEventListener('click', () => console.log('Click en el título'));
articulo.addEventListener('click', () => console.log('Click en el artículo'));
```

Al hacer click en el articulo, solo se ejecutará su respectiva función, pero si hacemos click en el título, ambas funciones serán ejecutadas puesto que el título es un hijo del artículo y se produce el Event Bubbling. Esto irá en el orden de primero el elemento específico en el que se produjo el evento (en este caso el título) y luego los elementos padres.

Una forma que tenemos para saber si un evento tiene bubbling por defecto es utilizando la propiedad `.bubbles` la cual devuelve true si el evento tiene bubbling o false en caso contrario.

De igual manera, tenemos una manera de evitar que el bubbling se produzca con un método el cual sería `.stopPropagation()` la cual hará que no se produzca el Event Bubbling.

También, para comprobar si hemos cancelado el bubbling tenemos la propiedad `.cancelBubble` la cual devuelve true si hemos anulado el bubbling o false en caso contrario.

Tengamos en cuenta también que el Event Bubbling no necesariamente es algo malo, pues también podemos sacarle provecho. Uno de sus usos más interesantes sería ejecutar una función de un listener para varios elementos.

Una pequeña muestra para darse una idea de la posible utilidad del bubbling:

```js
const articulo = document.querySelector('#articulo');

articulo.addEventListener('click', event => console.log(event.target, event.currentTarget));
```

En este código solo tenemos el evento de click en el articulo, pero dentro de dicho articulo, podríamos hacer click en cualquer elemento hijo y podríamos usar el `event.target` para realizar una acción según sea el caso.

También tenemos una forma de invertir el orden en el que se ejecutarán las funciones de los eventos, de modo que se ejecuten durante la fase de Captura. La forma de hacerlo es agregar como tercer parámetro al listener un objeto con la key `capture` y su valor en `true`.

Tomemos el código de antes como ejemplo:

```js
const articulo = document.querySelector('#articulo');
const titulo = document.querySelector('#titulo');

titulo.addEventListener('click', () => console.log('Click en el título'));
articulo.addEventListener('click', () => console.log('Click en el artículo'), {capture: true});
```

Con ese parámetro en el listener del artículo, primero se ejecutará la función de ese listener y luego la función del título, por lo que habremos ejecutado ese código en orden "inverso".

[Volver arriba](#índice)