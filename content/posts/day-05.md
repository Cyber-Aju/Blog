+++
title= "Day 05"
date= '2025-03-16'
draft= 'false'
tags= ["", "IndexedCollections", "KeyedCollections","ErrorHandling"]
categories= ["Days_of_Back"]
+++

# Cover up the best on this week

## 1. Coding of the day : **None**

## 2. JS of the day : ** Indexed collections and Keyed Collections**

### Indexed Collections :

- JavaScript does not have an explicit array data type.
- `const arr = [45]` creates array with one element, Where `const arr = Array(45)` creates array with no elements but the length of the array.
- At the implementation level, JavaScript's arrays actually store their elements as **standard object properties**, using the array index as the property name.
- JavaScript arrays using for...in loops, because normal elements and all enumerable properties will be listed.
- **Array methods :**

  - `push()` => Pushes element at the last element.
  - `pop()` => Removes the last element of the array.
  - `shift()` => Removes the first element in the array.
  - `unshift()` => Adds one or more element in the starting posititon.
  - `slice()` => Extracts the section of array and return a new array.
  - `at()` => Method returns the element at the specified index in the array.
  - `splice()` => Removes the element from the array and optionally replaces them
  - `reverse()` => reverse the elements in the array.
  - `sort()` => sorts the element of array in place, and returns aa reference to the array.
  - `indexOf()` => method searches the array for searchElement and returns the index of the first match.
  - `lastIndexOf()` => method works like indexOf, but starts at the end and searches backwards.
  - `forEach()` => method executes _callback_ on every array item and returns undefined.
  - `find()` => method returns the first item of the which the _callback_ returned _true_.
  - `findLast()` => method returns the last item for which the _callback_ returns _true_.
  - `findIndex()` => method returns the index of the first item for which the _callback_ returned _true_.
  - `findLastIndex()` => method returns the index of the last item for which _callback_ returned _true_.
  - `every()` => method returns true if callback returns true for every item in the array.
  - `some()` => method returns true if callback returns true for at least one item in the array.
  - `concat()` => joins two or more arrays and returns a new array.

  ```js
  let myArray = ["1", "2", "3"];
  myArray = myArray.concat("a", "b", "c");
  // myArray is now ["1", "2", "3", "a", "b", "c"]
  ```

  - `join()` => method joins all elements of an array into a string.

  ```js
  const myArray = ["Wind", "Rain", "Fire"];
  const list = myArray.join(" - "); // list is "Wind - Rain - Fire"
  ```

  - `flat()` => This method return a new array with all sub-array elements concatenated into it recursively up to specified depth. The paramenters defines the _Depth_.

  ```js
  const arr4 = [1, 2, [3, 4, [5, 6, [7, 8, [9, 10]]]]];
  arr4.flat(Infinity);
  // [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
  ```

  - `map()` => methods returns a new array of the return value from executing the _callback_ on every array item.

  ```js
  const a1 = ["a", "b", "c"];
  const a2 = a1.map((item) => item.toUpperCase());
  console.log(a2); // ['A', 'B', 'C']
  ```

  - `flatMap()` => method runs `map()` followed by a `flat()` of depth 1.

  ```js
  const a1 = ["a", "b", "c"];
  const a2 = a1.flatMap((item) => [item.toUpperCase(), item.toLowerCase()]);
  console.log(a2); // ['A', 'a', 'B', 'b', 'C', 'c']
  ```

  - `filter()` => method returns a new array containing the items for which callback returned _true_.

  ```js
  const a1 = ["a", 10, "b", 20, "c", 30];
  const a2 = a1.filter((item) => typeof item === "number");
  console.log(a2); // [10, 20, 30]
  ```

  - `reduce()` => method applies callback(accumulator, currentValue, currentIndex, array) for each value in the array for the purpose of reducing the list of items down to a single value. The reduce function returns the final value returned by callback function.

  ```js
  const a = [10, 20, 30];
  const total = a.reduce(
    (accumulator, currentValue) => accumulator + currentValue,
    0
  );
  console.log(total); // 60
  ```

- **Grouping the elements of an array**, The `Object.groupBy()` method can be used to group the elements of an array, using a test function that returns a string indicating the group of the current element.

```js
const inventory = [
  { name: "asparagus", type: "vegetables" },
  { name: "bananas", type: "fruit" },
  { name: "goat", type: "meat" },
  { name: "cherries", type: "fruit" },
  { name: "fish", type: "meat" },
];

const result = Object.groupBy(inventory, ({ type }) => type);
console.log(result);
// Logs
// {
//   vegetables: [{ name: 'asparagus', type: 'vegetables' }],
//   fruit: [
//     { name: 'bananas', type: 'fruit' },
//     { name: 'cherries', type: 'fruit' }
//   ],
//   meat: [
//     { name: 'goat', type: 'meat' },
//     { name: 'fish', type: 'meat' }
//   ]
// }
```

##### Note that the returned object references the same elements as the original array (not deep copies). Changing the internal structure of these elements will be reflected in both the original array and the returned object.

- **Sparse arrays**, Arrays can contain "empty slots", which are not the same as slots filled with the value `undefined`.
- Arrays can also be used like objects, to store related information.

```js
const arr = [1, 2, 3];
arr.property = "value";
console.log(arr.property); // "value"
```

### Keyed Collections :

- `Map` and `Set` objects contain elements which are iterable in the order of insertion.
- A `Map` object is a key/value map that can iterate its elements in insertion order.

  - use a `for...of` loop to return an array of `[key, value]` for each iteration.

  ```js
  const sayings = new Map();
  sayings.set("dog", "woof");
  sayings.set("cat", "meow");
  sayings.set("elephant", "toot");
  sayings.size; // 3
  sayings.get("dog"); // woof
  sayings.get("fox"); // undefined
  sayings.has("bird"); // false
  sayings.delete("dog");
  sayings.has("dog"); // false

  for (const [key, value] of sayings) {
    console.log(`${key} goes ${value}`);
  }
  // "cat goes meow"
  // "elephant goes toot"

  sayings.clear();
  sayings.size; // 0
  ```

  - We can get the size of a `Map` easily, while you have to manually keep track of size for an Object.
  - These three tips can help you to decide whether to use a Map or an Object:
    - Use maps over objects when keys are unknown until run time, and when all keys are the same type and all values are the same type.
    - Use maps if there is a need to store primitive values as keys because object treats each key as a string whether it's a number value, boolean value or any other primitive value.
    - Use objects when there is logic that operates on individual elements.

- `Sets`, objects are collections of **unique values**. You can iterate its elements in insertion order. A value in a Set may only occur once; it is unique in the Set's collection.

```js
const mySet = new Set();
mySet.add(1);
mySet.add("some text");
mySet.add("foo");

mySet.has(1); // true
mySet.delete("foo");
mySet.size; // 2

for (const item of mySet) {
  console.log(item);
}
// 1
// "some text"
```

- `Set` objects let you delete elements by their value. With an `array`, you would have to `splice` based on an element's index.
- `Set` objects store unique values. You don't have to manually keep track of duplicates.
- Both the key equality of `Map` objects and the value equality of `Set` objects are based on the **SameValueZero algorithm**:
  - Equality works like the identity comparison operator `===`.
  - `-0` and `+0` are considered equal.
  - `NaN` is considered equal to itself (contrary to `===`).

Queries : [Send mail](ajmalakram152@gmail.com)
