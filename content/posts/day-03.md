+++
title= "Day 03"
date= '2025-03-13'
draft= 'false'
tags= ["", "Expressions", "Operations", "Numbers","Strings"]
categories= ["Days_of_Back"]
+++

# Under the pressure

## 1. Coding of the day : **None**

## 2. JS of the day : **Expressions / Operations and Numbers / Strings**

### Expressions and Operations :

- An expression is a valid unit of code that resolves to a value. There are two types of expressions: those that have side effects (such as assigning values) and those that purely evaluate.
- `Nullish coalescing assignment (??=)`, also known as the logical nullish assignment operator, only evaluates the right operand and assigns to the left if the left operand is nullish (null or undefined).
- **Destructuring,** a JavaScript expression that makes it possible to extract data from arrays or objects using a syntax that mirrors the construction of array and object literals.

  - Without destructuring, it takes multiple statements to extract values from arrays and objects:

  ```js
  const foo = ["one", "two", "three"];

  const one = foo[0];
  const two = foo[1];
  const three = foo[2];
  ```

  - With destructuring, you can extract multiple values into distinct variables using a single statement:

  ```js
  const [one, two, three] = foo;
  ```

- **Optional chaining**, (?.) performs the chained operation on an object if it is defined and non-null, and otherwise short-circuits the operation and returns undefined. This allows you to operate on a value that may be null or undefined without causing a TypeError.

```js
maybeObject?.property;
maybeObject?.[property];
maybeFunction?.();
```

### Numbers and Strings :

- **Number object**, The built-in Number object has properties for numerical constants, such as maximum value, not-a-number, and infinity. You cannot change the values of these properties and you use them as follows:

```js
const biggestNum = Number.MAX_VALUE;
const smallestNum = Number.MIN_VALUE;
const infiniteNum = Number.POSITIVE_INFINITY;
const negInfiniteNum = Number.NEGATIVE_INFINITY;
const notANum = Number.NaN;
```

- **Template literals**, `${expression}` are string literals allowing embedded expressions. You can use multi-line strings and string interpolation features with them.

Queries : [Send mail](ajmalakram152@gmail.com)
