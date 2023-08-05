# Javascript Interview Preparation Q&A

This repository contains a set of common interview questions and their answers for JavaScript developers.

## Q1. Difference between `==` and `===` operator

The `==` operator compares values after performing type conversion, while `===` compares values without type conversion.

Example:
```javascript
console.log(5 == "5");   // true
console.log(5 === "5");  // false
```

## Q. What is Prototypical Inheritance?

Prototypical inheritance is a fundamental concept in JavaScript that deals with how objects can inherit properties and methods from other objects. Unlike traditional class-based inheritance, JavaScript uses prototype chains to achieve inheritance.

In JavaScript, every object has an internal property called `[[Prototype]]` (commonly accessed using the `__proto__` property). When you access a property or method on an object, JavaScript first checks if the object itself has that property. If not, it looks at its prototype (`[[Prototype]]`), and if the property is found there, it's used.

This linking of objects through their prototypes creates a chain, commonly referred to as the prototype chain. If a property or method is not found even in the prototype, the search continues up the chain until the property is found or until the end of the chain (where the last object's prototype is `null`).

### Example

```javascript
// Constructor function
function Animal(name) {
    this.name = name;
}


// Adding a method to the prototype
Animal.prototype.sound = function() {
    return "Animal sound";
};

// Creating an instance of Animal
const cat = new Animal("Cat");

// The cat object inherits the sound method from its prototype
console.log(cat.sound());  // Output: Animal sound
```
## Q. What is the purpose of strict mode?

Strict mode (`"use strict"`) is a feature introduced in ECMAScript 5 (ES5) that helps developers write more robust and error-free JavaScript code by catching common mistakes and preventing certain unsafe actions.

### Purpose and Benefits

1. **Error Reporting**: Strict mode helps catch silent errors and subtle bugs in your code. In non-strict mode, some mistakes may go unnoticed, potentially leading to unexpected behavior. Strict mode ensures that these mistakes trigger errors.

2. **Prevents Global Variables**: In non-strict mode, omitting the `var`, `let`, or `const` keywords when declaring a variable creates a global variable. This can cause unintended side effects and make the code harder to maintain. In strict mode, omitting these keywords leads to an error, preventing accidental global variable creation.

3. **Prevents Octal Interpretation**: In non-strict mode, numbers starting with a leading zero are treated as octal (base 8). This can lead to confusion and unintended results. Strict mode disables octal interpretation, helping to avoid such issues.

4. **No Use of Deprecated Features**: Strict mode disables the usage of certain features and syntax that are considered deprecated or error-prone. This encourages developers to adopt modern and recommended coding practices.

5. **Catches Assignment to Non-Writable Globals**: In strict mode, attempts to modify non-writable global variables or built-in objects (such as `undefined`, `null`, `Infinity`, etc.) result in errors. This helps prevent unintentional modifications to these values.

### Example

```javascript
"use strict";

x = 10;  // Throws an error because 'x' is not declared
```

## Q. What is a Module and how to work with them?

A module is a self-contained piece of code that encapsulates functionality, variables, and functions. It allows you to organize your code into reusable, maintainable, and well-structured components.

In JavaScript, there are different module systems, including CommonJS and ES6 modules.

### Working with CommonJS Modules

CommonJS is a module system used in Node.js and is suitable for server-side development.

To create a module:
```javascript
// module.js
const greet = name => {
    return `Hello, ${name}!`;
};

module.exports = greet;
```
To use the module in another file:

```js
// main.js
const greet = require('./module');
console.log(greet('Alice'));  // Output: Hello, Alice!
```
### Working with ES6 Modules
ES6 introduced a more standardized module system that works both in browsers and Node.js.

To create a module:
```js
// module.js
export const greet = name => {
    return `Hello, ${name}!`;
};
```
To use the module in another file:
```js
// main.js
import { greet } from './module.js';
console.log(greet('Bob'));  // Output: Hello, Bob!
```

## Q. State the difference between high order function and a callback function
    A higher-order function and a callback function are related concepts in programming, often used together, but they have distinct meanings:

### Higher-Order Function:
    A higher-order function is a function that either takes one or more functions as arguments (callbacks), or it returns a function as its result. In other words, a higher-order function treats functions as values, allowing them to be manipulated and passed around like any other data type. Higher-order functions enable powerful functional programming techniques.

    Example of a higher-order function that takes a callback function as an argument:
```js
    function higherOrderFunction(callback) {
    // Do something before calling the callback
    callback();
    // Do something after calling the callback
}
```
### Callback function:
    Callback Function:
    A callback function is a function that is passed as an argument to another function and is intended to be executed after some specific task is completed or an event occurs. Callbacks are often used for asynchronous operations or to customize the behavior of a higher-order function.

    Example of using a callback function:
```js
function performOperation(value, callback) {
    // Perform the operation on the value
    const result = value * 2;
    // Call the callback with the result
    callback(result);
}

function displayResult(output) {
    console.log(`The result is: ${output}`);
}

performOperation(5, displayResult); // Output: The result is: 10
```
In this example, displayResult is a callback function passed to the performOperation higher-order function. After the operation is performed, the callback is invoked with the result.

To summarize:

    A higher-order function is a function that can accept other functions as arguments or return functions as results.
    A callback function is a function passed as an argument to another function, to be executed later when a specific condition is met or task is completed.

Callback functions are commonly used within higher-order functions to enable dynamic behavior and enhance the flexibility of your code, especially when dealing with asynchronous operations or customizing the behavior of functions.
