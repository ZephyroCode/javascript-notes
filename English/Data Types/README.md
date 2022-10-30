# Data Types

## Basics

We have several data types in JavaScript, such as strings, numbers, booleans...

Let's get an overview.

---

## Strings

Strings are declared using quotes. You can either use double quotes `""` or single quotes `''`.

Example: 

```js
let singleQuoteString = 'Hiya!';

let doubleQuoteString = "Here!";
```

Now, if you're wondering when you should use one or another, it's pretty easy. Use the one you need. I mostly use double quotes unless I need to use them inside the string.

We also have a third way to declare string, which are the _template strings_. These are mostly used to concatenate variables inside a string.

Example:

```js
let name = "Elizabeth";
let surname = "Snow";

console.log(`Hi! I'm ${name} ${surname}!`);
```

As you can see, we're using the strings that we have in those variables to print a message in the console by using a template string. You can see too that we're using `${}` to concatenate the variable values.

---

## Numbers

One thing to know about the numbers in JavaScript is that there's not a `integer` or `float` types. They all are numbers.

```js
let num1 = 21;
let num2 = -21;
let num3 = 135.7;
let num4 = -135.7;
let num5 = 21e25;
```

As you see, they all are numbers.

Of course, all mathemical operations are available.

```js
let age = 21;

console.log(age + 13);
console.log(age - 5);
console.log(age * 7);
console.log(age / 3);
console.log(age % 5);
```

We also have special operators to make these operations a bit shorter.

For example:

```js
let num1 = 7;
num1  = num1 + 3;
console.log(num1);
// This will print 10 in the console.

let num2 = 5;
num += 4;
console.log(num2);
// This will print 9 in the console.
```

You can see that it's shorter and easier.

---

## Booleans

We also have booleans, and there are only 2 possible values: `true` or `false`.

These values are very useful in a lot of situations, and you'll use them quite often.

A quick example of using a boolean value would be something like...

_"If this thing is **true**, then do this. Otherwise, if it's **false**, do this."_

---

## Undefined, Null & NaN

We have 3 more primitive types, which are `undefined`, `null` and `NaN`.

These types are kinda special.

- **Undefined** is the default value for any variable, but not for a constant. It just means that the variable doesn't have a defined value _yet_, so you can change that. Basically an empty variable.

- **Null** is basically the same as undefined, but this one is not a default value. It's null when you _want_ it to be.

- **NaN** is the result you get when you try to make maths with values that are not numbers. For example, if you try to do `17 * "hello"` it will return NaN.

---

## Object

An object has multiple values inside of it.

Example:

```js
const names = ["Elizabeth", "Chloe", "Alex"];

const elizabeth = {
  names: "Elizabeth Alejandra",
  surnames: "Snow Blake",
  age: 21
}
```

Both of those are objects for JavaScript.

I know, some of you may think _"That's not an object, that's an array!"_

**Yesn't.**

Even if you can create an _"array"_ in JavaScript, it's still an object.

---

## Functions

Yes. Functions are their own data type too.

```js
function greet(name) {
  console.log(`Hi, ${name}!`);
}
```

---

## Typeof Operator

We also have the `typeof` operator to know the data type of certain value.

Example:

```js
console.log(typeof "Hi!");
// Prints "string"

console.log(typeof 15);
// Prints "number"

console.log(typeof true);
// Prints "boolean"

console.log(typeof undefined);
// Prints "undefined"

console.log(typeof null);
// Prints "object"

console.log(typeof NaN);
// Prints "number"

console.log(typeof [])
// Prints "object"
// Told ya :P

console.log(typeof {})
// Prints "object"

console.log(typeof function(){})
// Prints "function"
```
