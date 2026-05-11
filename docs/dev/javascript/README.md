# JavaScript Core Concepts

## Scope

- var - Function Scope ; can redeclare and access any where in the function regardless of where it is declared.
- let, const - block scope

<details>
<summary>Example</summary>

```javascript
function testVar() {
  if (true) {
    var a = 10;
    console.log(a); // 10
  }
  console.log(a); // 10
}

function testLetConst() {
  if (true) {
    let b = 20;
    const c = 30;
    console.log(b); // 20
    console.log(c); // 30
  }
  // console.log(b); // ReferenceError
  // console.log(c); // ReferenceError
}

testVar();
testLetConst();
```

</details>

## Hoisting

JavaScript moves declarations to the top of their scope during compilation.

- `var` is hoisted and initialized with `undefined`
- `let` and `const` are hoisted but stay in the temporal dead zone until declared
- function declarations are fully hoisted, so they can be called before declaration
- function expressions are not fully hoisted like function declarations

- Hoisting is the behavior of the JavaScript engine where declarations are registered before code execution starts
- Only the declaration is hoisted, not the actual assigned value

### Quick Understanding

- `var` gives `undefined` if accessed before assignment
- `let` and `const` throw `ReferenceError` before declaration because of the temporal dead zone
- function declarations can be called before they appear in the code

<details>
<summary>Example</summary>

```javascript
console.log(count); // undefined
var count = 5;

// console.log(total); // ReferenceError
let total = 10;

sayHello(); // works
function sayHello() {
  console.log("Hello");
}
```

</details>

## Temporal Dead Zone

- Temporal Dead Zone (TDZ) is the period where `let` and `const` variables are in scope but cannot be accessed before initialization.
- It starts from the beginning of the block and ends when the variable declaration is reached.
- If accessed inside this period, JavaScript throws a `ReferenceError`.

### Why it exists

- catches bugs early
- makes variable usage more predictable
- avoids accidental access before a variable is ready

<details>
<summary>Example</summary>

```javascript
{
  // console.log(score); // ReferenceError
  let score = 100;
  console.log(score); // 100
}
```

</details>


## Closure

- A closure happens when an inner function remembers and can access variables from its outer function even after the outer function has finished execution.
- In simple terms, a closure is a function bundled together with its lexical environment.

### Advantages

- data privacy
- function factory
- callbacks and event handlers
- memoization and caching

<details>
<summary>Example</summary>

```javascript
function counter() {
  let count = 0;

  return function () {
    count++;
    console.log(count);
  };
}

const increment = counter();
increment(); // 1
increment(); // 2
increment(); // 3
```

</details>


## Asynchronous JavaScript

Used for tasks like API calls, timers, and file operations.

- Callbacks
- Promises
- `async` / `await`

<details>
<summary>Example</summary>

```js
async function fetchUsers() {
  const response = await fetch("/api/users");
  return response.json();
}
```

</details>

## Equality

- `==` checks value with type conversion
- `===` checks value and type

Prefer `===` in most cases.

