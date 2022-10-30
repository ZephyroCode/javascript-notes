# Clases

## Índice

* [Conceptos Básicos](#básicos)
* [Herencia](#herencia)
* [Operador Instanceof](#instanceof)

---

## Básicos

Las clases en JavaScript son básicamente _"moldes"_ o _"plantillas"_ desde las cuales crearemos objetos a partir de ellas, de modo que podemos tener muchos objetos con una serie de propiedades y/o métodos ya definidos gracias a la clase.

```js
class Operador {
	constructor(nombres, apellidos, dni, sexo, celular, correo) {
		this._nombres = nombres;
		this._apellidos = apellidos;
		this._dni = dni;
		this._sexo = sexo;
		this._celular = celular;
		this._correo = correo;
	}
	// Static props/methods
	static CARGO_PRINCIPAL = "Operador";

	// Getters
	get nombres() {
		return this._nombres;
	}
	get apellidos() {
		return this._apellidos;
	}
	get dni() {
		return this._dni;
	}
	get sexo() {
		return this._sexo;
	}
	get celular() {
		return this._celular;
	}
	get correo() {
		return this._correo;
	}

	// Setters
	set celular(nuevocelular) {
		this._celular = nuevocelular;
	}
	set correo(nuevocorreo) {
		this._correo = nuevocorreo;
	}

	// Métodos
	saludo() {
		return `Hola. Soy ${this.nombres} ${this.apellidos}.`;
	}
}
```

Como podemos ver, crear una clase es sencillo...

* Palabra reservada: `class`.
* El nombre de nuestra clase, usualmente escrito con la primera letra en mayúsculas. Abrimos llaves.
* Dentro de las llaves, usaremos la función `constructor` para definir qué propiedades tendrá nuestra clase por defecto.
* Fuera del constructor, crearemos los métodos que tendrá nuestra clase.

Además, podemos ver que dentro de la clase tenemos una sección de `Getters` y `Setters`. Los Getters te proporcionan el valor de una propiedad pero sin "tocar" la propiedad directamente. Lo Setters son similares, solo que no te proporcionan el valor, sino que lo modifican.

De igual forma, podemos tener propiedades y métodos estáticos dentro de nuestra clase. Estos no necesariamente son parte de los objetos creados a partir de nuestra clase, sino que son propiedades/métodos propios de la clase en sí. Como se puede ver en el ejemplo de arriba, los crearemos utilizando la palabra reservada `static`.

Aquí un ejemplo de cómo podemos crear un nuevo objeto basado en una clase.

```js
const elizabeth = new Operador("Elizabeth Alejandra", "Snow Blake", 1234567, "femenino", 123456789, "liz@correo.com");
```

[Volver arriba](#índice)

---

## Herencia

También tenemos en JavaScrit la herencia. Dicho de forma simple, es cuando una clase hereda propiedades y métodos de otra.

Tenemos la clase `Operador` como ejemplo. Esta clase tiene algunas propiedades y métodos que cada objeto basado en ella tendra, pero también puede haber algunas clases que hereden esas propiedades y métodos, además de tener los suyos. Para el caso de `Operador`, podemos ver que tiene algunos datos personales, y luego podemos tener algunas clases que hereden tales propiedades y añadan otras respecto a su cargo, deberes y responsabilidades.

```js
class Supervisor extends Operador { }
```

Este ejemplo muestra que la clase `Supervisor` hereda todas las propiedades de la clase `Operador`, por lo que si creamos un nuevo objeto basado en Supervisor, tendrá las mismas propiedades y métodos que un objeto de Operador tiene.

```js
class Gerente extends Operador {
	constructor(nombres, apellidos, dni, sexo, celular, correo) {
		super(nombres, apellidos, dni, sexo, celular, correo);

		this._responsabilidades = [];
	}
}
```

Aquí podemos apreciar que hemos usado la palabra reservada `super` para heredar propiedades de una clase padre, y luego podemos agregar nuevas propiedades o métodos a esta nueva clase.

Si intentamos copiar la clase padre usando `this`, tendremos un error que nos dirá que debemos llamar al constructor `super` para acceder al `this`.

También tenemos que considerar que cuando quieres agregar nuevas propiedades o métodos a una clase que hereda de otra, **debes** usar `super`.

[Volver arriba](#índice)

---

## Instanceof

Como una nota adicional, tenemos también el operador `instanceof`, el cual devuelve un booleano. Este operador es básicamente una pregunta sencilla: _"¿Este objeto es una instancia de esta clase?"_

```js
console.log(elizabeth instanceof Operador);
// This returns true.
```

[Volver arriba](#índice)