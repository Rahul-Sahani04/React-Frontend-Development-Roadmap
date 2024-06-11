# Essential JavaScript Concepts for React 🚀

You don’t need to be a JavaScript expert to start your ReactJS journey, but just as knowledge of ingredients is a must for any chef hoping to master cooking, the same is true for learning ReactJS. It’s a modern JavaScript UI library, so you need to know some essential JavaScript for React.

## Essential JavaScript Concepts for React

- **Functions and Arrow Functions**
- **Objects**
- **Arrays and Array Methods**
- **Destructuring**
- **Template Literals**
- **Ternary Operators**
- **ES Modules and Import/Export Syntax**

## What to Learn in JavaScript Before React?

Before starting with React, it’s essential to master JavaScript basics like variables, functions, arrays, and objects. Familiarity with ES6 features such as arrow functions and template literals, along with asynchronous JavaScript concepts like promises and async/await, sets a strong groundwork for React development. Understanding scope, closures, and event handling further enriches your React learning experience.

---

### Functions and Arrow Functions 🔄

In JavaScript, there are two types of functions: normal functions and arrow functions. Let’s explore the difference between them.

#### Normal Function

```javascript
function multiply(num1, num2) {
  const result = num1 * num2;
  return result;
}
```

#### Arrow Function

```javascript
const multiply = (num1, num2) => {
  const result = num1 * num2;
  return result;
}
```

If the return statement is the only statement in the function, you can even have a shorter function expression:

```javascript
const multiply = (num1, num2) => num1 * num2;
```

### JavaScript Objects 🗂️

In JavaScript, an object is an unordered collection of key-value pairs. Each key-value pair is called a property.

#### Creating an Object

```javascript
let empty = {};
```

To create an object with properties:

```javascript
let person = {
  firstName: 'John',
  lastName: 'Doe'
};
```

### JavaScript Arrays and Array Methods 📚

An array is a special variable, which can hold more than one value.

```javascript
const cars = ["Volvo", "BMW", "Honda"];
```

#### Array Literal

```javascript
const array_name = [item1, item2, ...];
```

#### Array Constructor

```javascript
const cars = new Array("Volvo", "BMW", "Honda");
```

Array methods are functions built into JavaScript that we can apply to our arrays – each method has a unique function that performs a change or calculation to our array.

### Destructuring 🛠️

The destructuring assignment syntax is a JavaScript expression that makes it possible to unpack values from arrays, or properties from objects, into distinct variables.

#### Example:

```javascript
const vehicles = ['mustang', 'f-150', 'expedition'];
const [car, truck, suv] = vehicles;
```

### Template Literals 📜

Template literals are literals delimited with backtick (`) characters, allowing for multi-line strings, string interpolation with embedded expressions, and special constructs called tagged templates.

#### Example:

```javascript
const name = 'Jack';
console.log(`Hello ${name}!`); // Hello Jack!
```

### Ternary Operators ❓

The conditional (ternary) operator is the only JavaScript operator that takes three operands: a condition followed by a question mark (`?`), then an expression to execute if the condition is truthy followed by a colon (`:`), and finally the expression to execute if the condition is false.

#### Example:

```javascript
let age = 18;
let message = age >= 16 ? 'You can drive.' : 'You cannot drive.';
console.log(message);
```

### ES Modules and Import/Export Syntax 📦

With ES2015 (ES6), we get built-in support for modules in JavaScript. Each file is its own module.

#### Exporting:

```javascript
export const myNumbers = [1, 2, 3, 4];

export function myLogger() {
  console.log(myNumbers);
}

export class Alligator {
  constructor() {
    // ...
  }
}
```

#### Importing:

```javascript
import { myLogger, Alligator } from './app.js';
```

---

By mastering these JavaScript concepts, you'll be well-prepared to dive into React development. Happy coding! 😃