# Data Types in JavaScript

In JavaScript, data types refer to the types of values that variables can hold. JavaScript is a dynamically typed language, meaning variables can hold any type of data and can change types at runtime. Data types are broadly categorized into two groups: `Primitive` and `Non-Primitive` (Reference) types.

## Primitive Data Types

Primitive data types are the most basic data types in JavaScript. They represent single values, not objects, and are immutable (cannot be changed). Here are the main primitive data types:

**a. Number**

-   Represents both integer and floating-point numbers.
-   Examples: `let age = 25;`, `let temperature = 98.6;`
-   Special values include Infinity, -Infinity, and NaN (Not a Number).

**b. String**

-   Used for text. A sequence of characters surrounded by single, double, or backticks (', ", or `).
-   Examples: `let name = "Alice";`, `let greeting = 'Hello, World!'`;

**c. Boolean**

-   Represents a logical entity with two values: true or false.
-   Examples: `let isAvailable = true;`, `let hasCompleted = false;`

**d. Undefined**

-   A variable that has been declared but not assigned a value is of type undefined.
-   Example

```
let test;
console.log(test); // undefined
```

**e. Null**

-   Represents the intentional absence of any object value.
-   Example: `let result = null;`

**f. Symbol (ES6)**

-   Represents a unique and immutable value, often used as identifiers for object properties.
-   Example: `let uniqueId = Symbol('id');`

**g. BigInt (ES2020)**

-   Used for numbers larger than those that can be represented by the Number type (greater than (2^{53} - 1) or less than (-2^{53} + 1)).
-   Example: `let bigNumber = 123456789012345678901234567890n;`

## Non-Primitive (Reference) Data Types

These types represent complex data structures and are mutable. The most common non-primitive type is Object, but there are also specialized types derived from it.

**a. Object**

-   Used to store collections of data and more complex entities.
-   An object is a collection of properties, and each property is associated with a key (name) and a value.
-   Example:

```
let person = {
    name: "John",
    age: 30,
    isStudent: false
};
```

**b. Array**

-   A type of object for storing an ordered collection of items.
-   Example:

```
let colors = ["red", "green", "blue"];
```

**c. Function**

-   A special type of object that represents a function.
-   Functions are objects in JavaScript, which means they can have properties and methods.
-   Example:

```
function greet() {
    console.log("Hello, World!");
}
```

**d. Date**

-   Used to handle dates and times.
-   Example:

```
let today = new Date();
```

**e. RegExp (Regular Expressions)**

-   Used to match patterns in strings.
-   Example:

```
let pattern = /hello/;
```

## Special Data Type: `typeof` Operator

The typeof operator is used to determine the type of a variable or a value in JavaScript.

Example

```
console.log(typeof 42);           // "number"
console.log(typeof "hello");      // "string"
console.log(typeof true);         // "boolean"
console.log(typeof undefined);    // "undefined"
console.log(typeof null);         // "object" (this is a historical bug in JavaScript)
console.log(typeof Symbol());     // "symbol"
console.log(typeof {});           // "object"
console.log(typeof []);           // "object"
console.log(typeof function(){}); // "function"
```

# Comprehensive Guide to JavaScript Functions

## Basic Concepts

### What is a Function?

Functions are the main "building blocks" of a program. They let you use the same code many times without repeating it.

### Function Syntax

```
function functionName(parameters) {
  // Code to execute
  return value; // (optional)
}
```

### Creating and Calling Functions

```
function sayHello() {
  console.log("Hello, world!");
}
sayHello(); // Outputs: "Hello, world!"
```

### Parameters and Arguments:

In JavaScript, parameters and arguments are terms often used interchangeably, but they refer to different aspects of functions.

#### Parameters

Parameters are the names listed in the function definition. They act as placeholders for the values that will be passed to the function when it is called.

For example:

```
function greet(name) {
    console.log("Hello, " + name + "!");
}
```

In this function, name is a parameter.

#### Arguments

Arguments are the actual values passed to the function when it is called. These values are assigned to the corresponding parameters.
For example:

```
greet("Alice");
```

In this function call, `"Alice"` is an argument.

### Key Points

-   Parameters are used when defining a function.
-   Arguments are used when calling a function.
-   A function can have multiple parameters, and you can pass multiple arguments to a function.

Here’s a complete example to illustrate the difference:

```
function add(a, b) { // a and b are parameters
    return a + b;
}

let sum = add(5, 10); // 5 and 10 are arguments
console.log(sum); // Outputs: 15
```

In this example, `a` and `b` are parameters, while `5` and `10` are arguments passed to the function `add`.

### Returning Values:

Functions can return values using the return statement.

```
function add(a, b) {
  return a + b;
}
let sum = add(5, 10); // sum is 15
```

### Function Declaration:

Functions are defined using the `function` keyword followed by a name, parameters in parentheses, and a block of code in curly braces.

```
function greet(name) {
    console.log("Hello, " + name + "!");
}
```

### Function Expression:

Functions can also be defined using expressions, which can be anonymous or named.

```
const greet = function(name) {
    console.log("Hello, " + name + "!");
};
```

### Arrow Functions:

Introduced in ES6, arrow functions provide a shorter syntax for writing functions.

```
const divide = (a, b) => a / b;
console.log(divide(10, 2)); // Outputs: 5
```

### Default Parameters:

You can set default values for parameters, which will be used if no argument is provided.

```
function greet(name = "Guest") {
  console.log("Hello, " + name + "!");
}
greet(); // Outputs: "Hello, Guest!"
```

### Rest Parameters:

Rest parameters allow you to pass an indefinite number of arguments as an array.

```
function sum(...numbers) {
  return numbers.reduce((total, num) => total + num, 0);
}
console.log(sum(1, 2, 3, 4)); // Outputs: 10
```

### Function Scope:

Variables defined inside a function are not accessible from outside the function. This is known as function scope.

```
function testScope() {
    let localVar = "I'm local";
    console.log(localVar);
}
testScope(); // Outputs: I'm local
console.log(localVar); // Error: localVar is not defined
```

### Closures:

A closure is a function that has access to its own scope, the scope of the outer function, and the global scope.

```
function outerFunction(outerVariable) {
    return function innerFunction(innerVariable) {
        console.log("Outer Variable: " + outerVariable);
        console.log("Inner Variable: " + innerVariable);
    };
}
const newFunction = outerFunction("outside");
newFunction("inside");
```

### Immediately Invoked Function Expressions (IIFE):

An IIFE is a function that runs as soon as it is defined.

```
(function() {
    console.log("This is an IIFE");
})();
```

### Higher-Order Functions:

Functions that operate on other functions, either by taking them as arguments or by returning them, are called higher-order functions.

```
function higherOrderFunction(callback) {
    callback();
}
higherOrderFunction(function() {
    console.log("Callback function executed");
});
```

### Function Methods:

Functions in JavaScript are objects and can have properties and methods such as call(), apply(), and bind().

```
function sayHello() {
    console.log("Hello, " + this.name);
}
const person = { name: "Alice" };
sayHello.call(person); // Outputs: Hello, Alice
```

## Advanced Concepts

### Recursion:

A recursive function is a function that calls itself somewhere within the body of the function. <a href="https://www.freecodecamp.org/news/recursion-in-javascript/">more info</a>

```
function recursiveFunc() {
  // some code here...
  recursiveFunc()
}
```

### Function Currying:

Currying is the process of transforming a function with multiple arguments into a sequence of functions each taking a single argument. <a href="https://javascript.info/currying-partials">more info</a>

```
function curry(f) {
    return function(a) {
        return function(b) {
            return f(a, b);
        };
    };
}
function sum(a, b) {
    return a + b;
}
let curriedSum = curry(sum);
console.log(curriedSum(1)(2)); // Outputs: 3
```

### Memoization:

Memoization is an optimization technique to speed up function calls by caching results.

```
function memoize(fn) {
    const cache = {};
    return function(...args) {
        const key = JSON.stringify(args);
        if (cache[key]) {
            return cache[key];
        }
        const result = fn(...args);
        cache[key] = result;
        return result;
    };
}
function slowFunction(num) {
    // Simulate a slow computation
    return num * 2;
}
const fastFunction = memoize(slowFunction);
console.log(fastFunction(5)); // Outputs: 10

```

### Asynchronous

Functions: Asynchronous functions allow you to write promise-based code as if it were synchronous.

```
async function fetchData() {
    let response = await fetch('https://api.example.com/data');
    let data = await response.json();
    console.log(data);
}
fetchData();
```

### Generators:

Generators are functions that can be paused and resumed, allowing you to work with asynchronous code more easily.

```
function* generatorFunction() {
    yield 'Hello';
    yield 'World';
}
const generator = generatorFunction();
console.log(generator.next().value); // Outputs: Hello
console.log(generator.next().value); // Outputs: World
```

### Function Composition:

Function composition is the process of combining two or more functions to produce a new function.

```
const compose = (f, g) => (x) => f(g(x));
const add1 = (x) => x + 1;
const multiply2 = (x) => x * 2;
const add1ThenMultiply2 = compose(multiply2, add1);
console.log(add1ThenMultiply2(5)); // Outputs: 12
```

### Partial Application:

Partial application is the process of fixing a number of arguments to a function, producing another function of smaller arity.

```
function partial(fn, ...fixedArgs) {
    return function(...remainingArgs) {
        return fn(...fixedArgs, ...remainingArgs);
    };
}
function add(a, b, c) {
    return a + b + c;
}
const add5 = partial(add, 5);
console.log(add5(3, 2)); // Outputs: 10
```

### Function as First-Class Citizens:

Functions in JavaScript are first-class citizens, meaning they can be assigned to variables, passed as arguments, and returned from other functions.

```
function executeFunction(fn) {
    fn();
}
executeFunction(() => console.log("Hello from a function!"));
```

### Function as Namespaces:

Functions can be used to create namespaces, helping to avoid polluting the global scope.

```
(function() {
    const privateVar = "I'm private";
    console.log(privateVar);
})();
// console.log(privateVar); // Error: privateVar is not defined
```

### Function Constructors:

Functions can be used as constructors to create objects.

```
function Person(name, age) {
    this.name = name;
    this.age = age;
}
const person1 = new Person("Alice", 25);
console.log(person1.name); // Outputs: Alice
```

### Decorators:

Decorators are a design pattern that allows behavior to be added to individual objects, functions, or classes.

```
function readonly(target, key, descriptor) {
    descriptor.writable = false;
    return descriptor;
}

class Example {
    @readonly
    name() {
        return 'example';
    }
}
```

### Function Binding:

Function binding ensures that a function retains its context (this) when called.

```
let obj = {
    x: 42,
    getX: function() {
        return this.x;
    }
};

let unboundGetX = obj.getX;
console.log(unboundGetX()); // The function gets invoked at the global scope

let boundGetX = unboundGetX.bind(obj);
console.log(boundGetX()); // 42
```

### Function Factories:

Function factories are functions that return other functions.

```
function createMultiplier(multiplier) {
    return function(x) {
        return x * multiplier;
    };
}

const double = createMultiplier(2);
console.log(double(5)); // Outputs: 10
```

### Function Overloading:

JavaScript does not support function overloading natively, but you can achieve similar behavior using conditional logic.

```
function example() {
    if (arguments.length === 0) {
        console.log("No arguments");
    } else if (arguments.length === 1) {
        console.log("One argument: " + arguments);
    } else {
        console.log("Multiple arguments: " + Array.from(arguments).join(", "));
    }
}

example(); // Outputs: No arguments
example(1); // Outputs: One argument: 1
example(1, 2, 3); // Outputs: Multiple arguments: 1, 2, 3
```

### Function Generators:

Function generators are functions that can be paused and resumed, allowing you to work with asynchronous code more easily.

```
function* generatorFunction() {
    yield 'Hello';
    yield 'World';
}
const generator = generatorFunction();
console.log(generator.next().value); // Outputs: Hello
console.log(generator.next().value); // Outputs: World
```

### Function Inheritance:

Functions can inherit properties and methods from other functions using prototypes.

```
function Animal(name) {
    this.name = name;
}

Animal.prototype.speak = function() {
    console.log(this.name + ' makes a noise.');
};

function Dog(name) {
    Animal.call(this, name);
}

Dog.prototype = Object.create(Animal.prototype);
Dog.prototype.constructor = Dog;

Dog.prototype.speak = function() {
    console.log(this.name + ' barks.');
};

let d = new Dog('Mitzie');
d.speak(); // Outputs: Mitzie barks.
```

### Function Context (this):

The value of this depends on how a function is called.

```
const obj = {
    value: 42,
    getValue: function() {
        return this.value;
    }
};

console.log(obj.getValue()); // Outputs: 42

const getValue = obj.getValue;
console.log(getValue()); // Outputs: undefined (or global object in non-strict mode)
```

### Function Callbacks:

Callbacks are functions passed as arguments to other functions.

```
function fetchData(callback) {
    setTimeout(() => {
        callback('Data fetched');
    }, 1000);
}

fetchData((message) => {
    console.log(message); // Outputs: Data fetched
});
```

### Function Promises:

Promises represent the eventual completion (or failure) of an asynchronous operation.

```
function fetchData() {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve('Data fetched');
        }, 1000);
    });
}

fetchData().then((message) => {
    console.log(message); // Outputs: Data fetched
});
```

### Async/Await:

Async/await is syntactic sugar built on top of promises, making asynchronous code look and behave more like synchronous code.

```
async function fetchData() {
    let response = await fetch('https://api.example.com/data');
    let data = await response.json();
    console.log(data);
}

fetchData();
```
