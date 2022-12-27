---
layout: post
title: Basic ES6 features you should know before diving into Javascript frameworks
tags: [javascript]
cover-img: /assets/img/javascript-es6/js-es6-banner.jpg
comments: true
---

Javascript is undeniably very popular as it has mostly been utilized in a variety of development projects, including mobile, desktop, and, of course, web applications.

Javascript is currently the most highly recommended programming language by developers due to the growing popularity of its frameworks. You can become a full-stack developer by learning Javascript because there are many frameworks available for backend and frontend development, allowing you to create full-stack applications.

However, you should first gain a better understanding of Javascript in general. One of the most important features was ES6 or ECMAScript 2015 or ECMAScript 6, which you should know before diving into Javascript Frameworks.

Before choosing your preferred javascript frameworks, you should be aware of the ES6 features we'll be covering in this blog.

### let and const keyword

- Variables were previously declared using `var` which had function scope and where hoisted to the top within
  its scope. It means that a variable can be used before declaration.
- But the `let` variables and constants have block scope which is surrounded by curly-braces `{}`, they are not
  hoisted and cannot be used before declaration.
- Thew new `const` keyword makes it possible to define constants. Constants are read-only, you cannot reassign new
  values to them.

#### let example

```javascript
let num = 100; // num is equals 100 here
{
  let num = 300; // num is equals 300 here
}
console.log(num); // Output here is 100
```

#### const example

```javascript
var num = 100; // num is equals 100 here
{
  const num = 300; // num is equals 300 here
}
console.log(num); // Output here is 100
```

<hr>

### Arrow Functions

- It provides a more concise syntax for writing function expressions by removing the `function` and `return`
  keywords.
- Arrow functions are defined using fat arrow `=>` notation.
- Unlike ordinary functions, arrow functions do not have their own `this` keyword.
- The value of `this` inside an arrow function is always bound to the value of this in the closest
  non-arrow function.
- `Arrow functions are not hoisted.` They must be defined before they are used.

#### ES5 Function Expression

```javascript
var sum = function (a, b) {
  return a + b;
};
console.log(sum(6, 9)); // Output: 15
```

#### ES6 Arrow function

```javascript
const sum = (a, b) => a + b;
console.log(sum(6, 9)); // Output: 15
```

<hr>

### Multi-line Strings

- Users can create multi-line strings by using back-ticks **(`)**. In ES5 we needed to use **(\n)** for multi-line statements.

#### ES5 syntax

```javascript
var message =
  "O Holy Night!\n" +
  "The stars are brightly shining\n" +
  "It is the night of the dear Savior's birth!";
```

#### ES6 syntax

```javascript
var message = `O Holy Night!
  The stars are brightly shining
  It is the night of the dear Savior's birth!`;
```

<hr>

### Template Literals

- ES6 introduces very simple string templates along with placeholders for the variables.
  The syntax for using the string template is `${PARAMETER}` and is used inside of the back-ticked string.

#### ES5 syntax

```javascript
var firstName = "Mark Anthony";
var lastName = "Estopace";

var message = "Hello! " + firstName + " " + lastName + ".";
// Output: Hello! Mark Anthony Estopace.
```

#### ES6 syntax

```javascript
const firstName = "Mark Anthony";
const lastName = "Estopace";

const message = `Hello! ${firstName} ${lastName}.`;
// Output: Hello! Mark Anthony Estopace.
```

<hr>

### Default Parameters

- ES6 allows function parameters to have default values but in ES5, `OR` operator had to be used.

#### ES5 syntax

```javascript
var calcArea = function (height, width) {
  height = height || 50;
  width = width || 80;
  // logic here
};
```

#### ES5 syntax

```javascript
const calcArea = (height = 100, width = 50) => {
  // logic here
};
```

<hr>

### Destructuring Assignment

- The destructuring assignment is an expression that makes it easy to extract values from arrays, or properties from
  objects into distinct variables.
- There are two types of destructuring assignment expressions, namely, `Array Destructuring` and `Object Destructuring`.

#### Array Destructuring

```javascript
const cars = ["Honda", "Toyota", "Ford", "Audi"];
const [honda, toyota, ford, audi] = cars;
console.log(honda, toyota, ford, audi);
// Output: Honda Toyota Ford Audi
```

#### Object Destructuring

```javascript
const user = { firstName: "Mark", lastName: "Estopace", age: 23 };
const { firstName, lastName, age } = user;
console.log(firstName, lastName, age);
// Output: Mark Estopace 23
```

<hr>

### Function Rest Parameter

- The rest parameter `...` allows a function to treat an indefinite number of arguments as an array.

```javascript
const sum = (...args) => {
  let sum = 0;
  for (let arg of args) sum += arg;
  return sum;
};

console.log(sum(1, 2, 3, 4, 5)); // Output: 15
```

<hr>

### Spread syntax

- The spread `...` syntax allows an iterable, such as an array or string, to be expanded in places where zero or more
  arguments (for function calls) or elements (for array literals) are expected.
- Spread syntax looks like rest syntax. In a way, spread syntax is the opposite of rest syntax.
- Spread syntax `expands` an array into its elements, while rest syntax collects multiple elements and `condenses`
  them into a single element.

```javascript
const sum = (a, b, c) => {
  return a + b + c;
};

const numbers = [2, 4, 6];

console.log(sum(...numbers)); // Output: 12
```

### Summary

We learned about the basic ES6 features:

- let and const keyword
- Arrow functions
- Multi-line strings
- Template literals
- Default parameters
- Destructuring assigment
- Function rest parameter
- Spread syntax

There are more ES6 features we didn't cover in this blog but you can learn them along the way if you're
using Javascript daily or if you're started using Javascript frameworks.
