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
