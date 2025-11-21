# JavaScript Variables

## What is a variable?
A variable is a named container that holds a value. In JavaScript, variables store data (numbers, strings, objects, functions, etc.) so your program can read and change that data.

## Declaring variables
You can declare variables using `var`, `let`, or `const`.

- `let` — block-scoped, can be reassigned.
- `const` — block-scoped, cannot be reassigned (but object contents can mutate).
- `var` — function-scoped, legacy behavior; has hoisting quirks.

## Block scoped
This applies to variables that only exist inside a pair of curly braces {}.
You step outside those braces, and boom, they vanish like your motivation during exams.

## Function scoped:
These variables live inside a function. As long as you’re inside the function body, the variable exists. Outside? It’s gone.

```js
let count = 1;
const name = "Alice";
var legacy = true;
```

## Naming rules
- Must start with a letter, `$`, or `_`.
- Subsequent characters can include digits.
- Case-sensitive: `myVar` ≠ `myvar`.
- Avoid reserved words (e.g., `class`, `function`).

## Initialization and reassignment
- A variable can be declared without a value (undefined):
    ```js
    let x;
    console.log(x); // undefined
    x = 10;
    ```
- `const` requires an initializer:
    ```js
    const PI = 3.14; // must initialize
    ```

## Hoisting
- Declarations are hoisted; behavior differs:
    - `var` is hoisted and initialized to `undefined`.
    - `let`/`const` are hoisted but in Temporal Dead Zone until initialized.

```js
console.log(a); // undefined (var)
var a = 5;

console.log(b); // ReferenceError (let)
let b = 6;
```

## Scope
- Global scope — accessible everywhere.
- Function scope (`var`) — inside a function.
- Block scope (`let`, `const`) — inside `{ ... }`.

## Types commonly stored
- Primitives: `number`, `string`, `boolean`, `null`, `undefined`, `bigint`, `symbol`.
- Objects: arrays, plain objects, functions, dates, etc.

## Examples
```js
let age = 30;
age = age + 1;

const user = { name: "Sam" };
user.name = "Samira"; // allowed (mutation)

function demo() {
    var insideFn = "I am function-scoped";
}
```

## Best practices
- Prefer `const` by default; use `let` when reassignment is needed.
- Avoid `var` in modern code.
- Use descriptive, camelCase names.
- Minimize global variables.

## This is the some imp to interview Perpose
1. var is hoised but stupid:
You can use it before declaration, but it gives undefined.

console.log(a)  // undefined (not error)
var a = 10


2. let and const are hoisted but strict:
You CANNOT use them before declaration.

console.log(x)  // error
let x = 5


3. Functions? They’re show-offs.
Function declarations work even before they appear in code.

hello()  // works
function hello() { console.log("Hi") }