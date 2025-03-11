+++
title= "Day 02"
date= '2025-03-11'
draft= 'false'
tags= ["MergeSort", "Loops", "Iterations","Functions"]
categories= ["Days_of_Back"]
+++

# Thought Hard Day

## 1. Coding of the day : **Merge Sort**

- Can't understand the code, but i tried to learn the logic.
- Merge sort is Divide and Conquer method algorithm.
- Advantage is in performs well even on large datasets. But it takes large space and it is slower than quick sort because of Not in-place.
- Not in-place is it requires additional memory to store the sorted data.

## 2. JS of the day : **Loops and Functions**

### Loops and Iterations :

- **Labeled statements** are an identifier that lets you refer to it elsewhere in your program. It works only in Loops.
- **`break` statements** breaks the loops
- **`continue` statements** skips next part and if there any labeled it continues from there.
- When you use continue with a label, it applies to the looping statement identified with that label.
- `for...in` iterates over the property names.
- `for...of` iterates over the property values.

```js
const arr = [3, 5, 7];
arr.foo = "hello";

for (const i in arr) {
  console.log(i);
}
// "0" "1" "2" "foo"

for (const i of arr) {
  console.log(i);
}
// Logs: 3 5 7
```

### Functions :

- Function hoisting only works with function declarations — not with function expressions. The following code will not work:

```js
console.log(square(5)); // ReferenceError: Cannot access 'square' before initialization
const square = function (n) {
  return n * n;
};
```

- **Immediately Invoked Function Expressions (IIFE)**, is a code pattern that directly calls a function defined as an expression. It looks like this:

```js
(function () {
  // Do something
})();

const value = (function () {
  // Do something
  return someValue;
})();
```

- IIFE advantage : Instead of saving the function in a variable, the function is immediately invoked. This is almost equivalent to just writing the function body, but there are a few unique benefits:

  1. It creates an extra scope of variables, which helps to confine variables to the place where they are useful.
  2. It is now an expression instead of a sequence of statements. This allows you to write complex computation logic when initializing variables.

- Scopes and closures:

  1. Functions form a scope for variables—this means variables defined inside a function cannot be accessed from anywhere outside the function.
  2. The function scope inherits from all the upper scopes. For example, a function defined in the global scope can access all variables defined in the global scope.
  3. A function defined inside another function can also access all variables defined in its parent function, and any other variables to which the parent function has access.
  4. On the other hand, the parent function (and any other parent scope) does not have access to the variables and functions defined inside the inner function. This provides a sort of encapsulation for the variables in the inner function.
  5. Closures : The function body as a closure. A closure is any piece of source code (most commonly, a function) that refers to some variables, and the closure "remembers" these variables even when the scope in which these variables were declared has exited.

- The **rest parameter** syntax allows us to represent an indefinite number of arguments as an array.
- **Arrow functions** does not have its own this, arguments, super, or new.target. Arrow functions are always anonymous.

```js
function Person() {
  this.age = 0;

  setInterval(() => {
    this.age++; // `this` properly refers to the person object
  }, 1000);
}

const p = new Person();
```

Queries : [Send mail](ajmalakram152@gmail.com)
