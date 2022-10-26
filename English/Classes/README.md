# Classes

## Basics

JavaScript Classes are basically bases for new objects which you will create from them, so we can have many objects with certain default properties and/or methods thanks to these classes.

```js
class Operator {
	constructor(names, surnames, dni, gender, phone, mail) {
		this._names = names;
		this._surnames = surnames;
		this._dni = dni;
		this._gender = gender;
		this._phone = phone;
		this._mail = mail;
	}
	// Static props/methods
	static MAIN_CHARGE = "Operator";

	// Getters
	get names() {
		return this._names;
	}
	get surnames() {
		return this._surnames;
	}
	get dni() {
		return this._dni;
	}
	get gender() {
		return this._gender;
	}
	get phone() {
		return this._phone;
	}
	get mail() {
		return this._mail;
	}

	// Setters
	set phone(newPhone) {
		this._phone = newPhone;
	}
	set mail(newMail) {
		this._mail = newMail;
	}

	// Methods
	greet() {
		return `Hello. I'm ${this.names} ${this.surnames}, DNI: ${this.dni}, gender ${this.gender}. My phone number is: ${this.phone}, my email is: ${this.mail} and my charge is ${Operator.MAIN_CHARGE}.`;
	}
}
```

As you can see, creating a class is easy.

* The keyword: `class`.
* The class name, usually writing the first character in uppercase. Open brackets.
* Inside the brackets, we'll use the `constructor` function to define which props our class will have by default.
* Out of the constructor, we'll create the methods our class will have.

We can also see that inside the class we have a `Getters` and `Setters` section. Getters gives you the value of a property so we don't "touch" the property directly. Setters are same as getters, but they don't get the value, they modify it.

We can have static properties and methods too inside the class. These are not necessarily part of the objects we create from our class, they're properties/methods that the class itself has. As you can see in the example above, we create them using the `static` keyword.

---

Here is an example of how you can create a new object based on a class.

```js
const elizabeth = new Operator("Elizabeth Alejandra", "Snow Blake", 1234567, "female", 123456789, "liz@mail.com");
```

---

## Inheritance

We have inheritance too. This is basically when a class inherits props and methods from another class.

We have the `Operator` class as example. This class has some props and methods that every object made from it will share, but there can also be some classes that inherits those props and methods, and also have its own props and methods. As for `Operator`, we can see that it has some personal information, and then we can have some classes that specify their responsibilities and duties depending on their charge.

```js
class Supervisor extends Operador { }
```

This example shows that the `Supervisor` class inherits all props and methods from the `Operator` class, so if we create a new object based on Supervisor, it'll have the same props and methods as Operator objects.

---

```js
class Manager extends Operador {
	constructor(names, surnames, dni, gender, phone, mail) {
		super(names, surnames, dni, gender, phone, mail);

		this._responsibilities = [];
	}
}
```

You can see here that we use the `super` keyword to inherit props from a parent class, and we then can add new props and/or methods to the new class.

If we try to copy the parent class using `this`, we'll get an error telling us that we must call the `super` constructor to use `this`.

You also have to consider that when you want to add new props or methods to a class that inherits from another one, you **must** use `super`.

---

## Instanceof Operator

As a side note, we also have the `instanceof` operator, which will return a boolean. This operator is basically a question: _"Is this object an instance of this class?"_

```js
console.log(elizabeth instanceof Operator);
// This returns true.
```
