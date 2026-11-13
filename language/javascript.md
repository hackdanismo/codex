# JavaScript

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
