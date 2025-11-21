# Block vs Function Scope in JavaScript

Short overview of how variables are scoped in JS and common pitfalls.

## Function scope (var)
- `var` is function-scoped: a `var` declared anywhere inside a function is visible throughout that function.
- `var` is hoisted: the declaration is moved to the top of the function, initialization remains in place.

Example:
```js
function f() {
    console.log(a); // undefined (declaration hoisted)
    if (true) {
        var a = 1;
    }
    console.log(a); // 1 (accessible anywhere in f)
}
f();
```

## Block scope (let, const)
- `let` and `const` are block-scoped: limited to the nearest `{ ... }`.
- They are not accessible before their declaration (Temporal Dead Zone - TDZ).
- `const` must be initialized at declaration.

Example:
```js
{
    let x = 10;
    const y = 20;
}
// x and y are not accessible here (ReferenceError if accessed)
```

TDZ example:
```js
{
    // console.log(a); // ReferenceError: can't access 'a' before initialization
    let a = 5;
}
```

## Functions and blocks
- Function declarations inside blocks behave differently across environments; prefer declaring functions at function scope or using `const fn = () => {}` inside blocks to avoid portability issues.

Example (recommended pattern):
```js
if (cond) {
    const handler = () => { /* ... */ };
    handler();
}
// handler not visible here
```

## Practical tips
- Prefer `const` for values that shouldn't change, `let` for reassignable bindings.
- Avoid `var` to prevent unexpected function-scoped leaks/hoisting bugs.
- Use block-scoped declarations for loop variables to avoid closure pitfalls:
```js
for (let i = 0; i < 3; i++) {
    setTimeout(() => console.log(i), 0); // logs 0,1,2
}
```

That's a concise summary of block vs function scope behavior.