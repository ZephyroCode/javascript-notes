# Variables

## Basics

Variables in JavaScript are kind of special compared to other languages like C++ or Java. First thing is that there aren't types. Every variable has a dynamic data type. This means that you can create a variable with a number, and change it to a string later on.

There are 2 ways to declare a variable in JavaScript:

* var
* let

Using the `var` keyword is not recommended nowadays because of the issues it can cause. So therefore, **do NOT use var**.

Using the `let` keyword is basically the way to go when you're declaring a new variable in JavaScript because of the scope.

```js
let name = "Elizabeth";
```

Here you can see how a variable is declared.

* Keyword.
* Variable name.
* Assignment operator.
* Value.

Also, something you should note is that variables are mostly written in camelCase. first character in lowercase, and if you have more than one word in the variable name, you write the first character in uppercase.

---

Now, some of the new ones may be asking _"Why do I need to declare variables?"_ 

Well, that's easy. Because you need to use their values during the execution of your program/script.

Let's make a quick example:

```js
let price =  37;
let amount = 3;

let total = price * amount;
console.log(total);
```

Yes, it's a super basic example, but you get the idea.

---

## Constants

Besides the variables, we have constants. A constant, as the name says, is a variable that will **never** change it's value.

Another thing is that constant names are written in uppercase and you separate each word with an underscore.

And of course, the keyword you'll use is `const`.

Example:

```js
const ZEPHYRO_BLOG = "https://zephyrocode.github.io";
```

---

Also note that you can't declare variables or constants with the same name _when you're in the same context_. That's when the `let` keyword shines.

---

## Data Types

Now we'll talk about the data types.

We have several data types in JavaScript, such as strings, numbers, booleans...

Let's get an overview.

---

### Strings

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

### Numbers

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

### Booleans

We also have booleans, and there are only 2 possible values: `true` or `false`.

These values are very useful in a lot of situations, and you'll use them quite often.

A quick example of using a boolean value would be something like...

_"If this thing is **true**, then do this. Otherwise, if it's **false**, do this."_

---

### Undefined, Null & NaN

We have 3 more primitive types, which are `undefined`, `null` and `NaN`.

These types are kinda special.

Undefined is the default value for any variable, but not for a constant. It just means that the variable doesn't have a defined value, so you can change that. Basically an empty variable.

Null is basically the same as undefined, but this one is not a default value. It's null when you _want_ it to be.

NaN is the result you get when you try to make maths with values that are not numbers. For example, if you try to do `17 * "hello"` it will return NaN.

---

### Object

This data type is not primitive.

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

Even if you can create an "array" in JavaScript, it's still an object.

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

console.log(typeof {})
// Prints "object"

console.log(typeof function(){})
// Prints "function"
```
