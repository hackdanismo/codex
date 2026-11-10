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

## Parameters and Arguments
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
