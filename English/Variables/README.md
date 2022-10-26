# Variables

## Basics

Variables in JavaScript are kind of special compared to other languages like C++ or Java. First thing is that there aren't types. Every variable has a dynamic data type. This means that you can create a variable with a number, and change it to a string later on.

There are 2 ways to declare a variable in JavaScript:

* var
* let

Using the `var` keyword is not recommended nowadays because of the issues it can cause. So therefore, **do NOT use var**.

Using the `let` keyword is basically the way to go when you're declaring a new variable in JavaScript because of the scope.

Within the same context, you can't declare variable or constants with the same name.

Your variable names can start with:

* `$`
* `_`
* Any letter.

You can't start a variable/constant/function/class with a number, so `1name` just doesn't work.

We also have several keywords that can never be used as IDs:

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

---

```js
let name = "Elizabeth";
```

Here you can see how a variable is declared.

1. Keyword.
2. Variable name.
3. Assignment operator.
4. Value.

Also, something you should note is that variables are mostly written in _camelCase_. first character in lowercase, and if you have more than one word in the variable name, you write the first character in uppercase.

You could use *snake_case* too...

```js
let besto_king = "Jon Snow";
```

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
