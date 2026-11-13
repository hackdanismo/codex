# JavaScript
`JavaScript` files usually end with the `.js` file extension.

To add a `JavaScript` file to `.html` document, use a `<script>` tag before the closing `</body>` tag.

```html
<script src="script.js"></script>

</body>
</html>
```

## Functions
`Functions` are reusable blocks of code. A `function` in `JavaScript` is usually declared with the `function` keyword followed by the name of the function, called the `identifier`.

```javascript
function boo() {
    // Code to be executed when the function is called.
}

// Call the function to execute the code block
boo();
```

Functions can also be writted using arrow function syntax:

```javascript
const boo = () => {
    // Code to be executed when the function is called.
}

// Call the function to execute the code block
boo();
```

A function can be written in shorthand, as with this `multiple` example, without the brackets:

```javascript
const multiply = (x, y) => x * y;

// Call the function to execute the code block
console.log(multiply(4, 3));    // Output: 12
```

Introduced in `ES6`, these are the most popular ways to write a function. They are commonly used for array methods like `.map()` or `.filter()`. 

### Parameters and Arguments
In `JavaScript`, `parameters` are variables that allow you to pass information into a function. Think of `parameters` as placeholders for values that a function will use when it runs. In this example, the `parameter` is `name`.

```javascript
const boo = (name) => {
    // Code to be executed when the function is called.
}
```

When the function is called, we can pass a value into the `parameter` using an `argument`. In this example, the `argument` is `"Dan"`.

```javascript
boo("Dan");
```

The full code:

```javascript
const boo = (name) => {
    console.log("Hello, " + name);    // Hello, Dan
}

// Call the function to execute the code block
boo("Dan");
```

Using a `template literal` and removing the braces around a single `parameter` in the function can make the syntax easier to read.

```javascript
const boo = name => {
    console.log(`Hello, ${name}`);    // Hello, Dan
}

// Call the function to execute the code block
boo("Dan");
```

A function can have multiple `arguments` and `parameters`. If a function has more than one `parameter`, braces are needed.

```javascript
const boo = (name, age) => {
    console.log(`Hello, ${name}. You are ${age} years old.`);    // Hello, Dan. You are 40 years old.
}

// Call the function to execute the code block
boo("Dan", 41);
```

#### Default Parameter Values
Default `parameter` values can be used in-place of values being passed as `arguments` so should a function be called without a value passed, the default value will be used.

```javascript
// Use the default parameter values
const boo = (name = "Peat", age = 9) => {
    console.log(`Hello, ${name}. You are ${age} years old.`);    // Hello, Peat. You are 9 years old.
}

// Call the function to execute the code block without values
boo();
```

### IIFE
An `IIFE (Immediately Invoked Function Expression)` is a `JavaScript` function that executes immediately after it is defined, without needing to call it separately. We don't need to call the function separately. It executes automatically.

```javascript
(() => {
    console.log("This is an IIFE.");
})();
```

This can also be writted with the `function` keyword instead of the arrow function syntax:

```javascript
(function () {
    console.log("This is an IIFE.");
})();
```

Just like regular functions, an `IIFE` can accept parameters.

```javascript
((name, age) => {
    console.log(`Hello, ${name}. You are ${age} years old.`);
})("Peat", 9);
```

One important reason to use an `IIFE` is to keep `variables` private to the function, so they don't interfere with variables outside it. The message `variable` only exists inside the `IIFE`.

```javascript
(() => {
    // This is a private variable and only available from inside the IIFE
    const message = "Hello, Peat!";
    console.log(message);
})();

console.log(message); // ReferenceError
```

In the context of a `JavaScript library`, it is used to create a `Private Scope`. Using an `IIFE` to create a library:

- To build a simple utility library, like a math helper or string formatter.
- To keep variables `"private"` so they don't leak into the global window object.
- Targetting a "Vanilla JS" environment where users just want to include a script tag.

For example:

```javascript
// IIFE function that runs as soon as it is defined
const MyLibrary = (function() {
    // Private variables, hidden from users
    const privateKey = "SECRET_123";

    // Public methods
    function sayHello() {
        return "Hello from the library.";
    }

    // Return what we want the public users to see
    return {
        sayHello: sayHello
    };
})();

console.log(MyLibrary.sayHello());    // Works
console.log(MyLibrary.privateKey);    // Undefined, as expected
```

### Return
The `return` statement is used to send a value back to the code that called the `function` and stopping the execution of the function immediately. The most common use of `return` is to output a result.

```javascript
function add(a, b) {
    return a + b;    // This sends the sum back to the caller
}

// The value is returned and stored in the sum variable
let sum = add(5, 10);
// Output the value stored in the variable, which is 15
console.log(sum);
```

If you are using `Arrow Functions` with a single line of code, we can use an `implicit return`. This means we don't need the word `return`.

```javascript
// Implicit return, no return statement needed
const multiply = (a, b) => a * b;
```

## Class
We can use a `class` to build a library that needs to `hold state`, such as a Video Player, Chat Widget, or a Game Engine. We can als use `Class` if we want users to be able to create multiple insances of the tool, or we want to use modern features like `async` and `await` inside of methods easily.

```javascript
class Counter {
    constructor(initialValue = 0) {
        this.count = initialValue;    // The library holds "state"
    }

    increment() {
        this.count++;
        return this.count;
    }

    decrement() {
        this.count--;
        return this.count;
    }
}

// The user creates an instance
const myCounter = new Counter(10);
console.log(myCounter.increment());    // 11
```

## ES Modules (ESM)
In modern development, `React`, `Vue`, `Node`, we actually rarely need to wrap the code in an `IIFE` anymore. Instead, we use `ES Modules` that allow `export` and `import`. If we are building a library to be published to `NPM`, we should write standard functions or classes and use `export`. Bundlers like `Webpack` or `Vite` will handle scoping so we don't need an `IIFE`.

```javascript
// library.js
export function add(a, b) {
    return a + b;
}

export class Calculator {
    constructor() {
        this.total = 0;
    }

    add(num) {
        this.total += num;
        return this.total;
    }
}
```

Because we use the `export` keyword, the library is now using `ES Modules (ESM)`. To use this, the way to import depends on whether we are working in a modern development environment like `React` or `Vite`, or just plain `HTML`.

If we are using two files in a browser without any specific tools, we must tell the browser that the script is a `module` in the `.html` file.

```html
<!-- You must include type="module" -->
<script type="module">
  import { add, Calculator } from './my-library.js';

  // Using the function
  console.log(add(5, 10)); // Output: 15

  // Using the class
  const myCalc = new Calculator();
  console.log(myCalc.add(5));  // Output: 5
  console.log(myCalc.add(5));  // Output: 10
</script>
```

If we are using a modern framework, like `React`, we don't need to worry about the `<script>` tag. The build tool handles this automatically. Example of `App.js` or another component.

```javascript
import { add, Calculator } from './my-library.js';

function App() {
  const result = add(10, 20);
  const calc = new Calculator();
  
  return (
    <div>
      <p>Sum: {result}</p>
      <p>Total: {calc.add(5)}</p>
    </div>
  );
}
```

If we want to share the library with the world, using `npm install my-library`, we would follow these steps:

- Initialize a project, run: `npm init` in the folder.
- File structure: `src/index.js` (where the code lives) and `dist/` where the compiles code goes.
- Build tools: use a tool like `Rollup` or `tsup` to take the export code and bundle it into a single file that other people can install.

Once published, a user would just do:

```javascript
import { add } from 'your-library';
```
