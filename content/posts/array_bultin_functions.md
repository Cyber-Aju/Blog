+++
title= "Array in PHP"
date= '2024-08-19'
draft= 'false'
tags= ["array"]
categories= ["php"]
+++

# PHP Array Functions

## 1. Creation & Initialization

### `array()`

Creates an array. Use when you need to initialize an array with elements.

- **Syntax**: `array(value1, value2, ...)`
- **Example**:
  ```php
  $arr = array(1, 2, 3);
  or $arr = [];
  or $arr[] = 1;
  // Output: [1, 2, 3]
  ```

### `array_fill()`

Fills an array with values. Use when you need an array with \*repeated values.

- **Syntax**: `array_fill(start_index, num, value)`
- **Example**:
  ```php
  $arr = array_fill(0, 3, 'A');
  // Output: ['A', 'A', 'A']
  ```

### `array_fill_keys()`

Fills an array with values, using keys from another array. Use when you need an \*associative array with the same value.

- **Syntax**: `array_fill_keys(keys, value)`
- **Example**:
  ```php
  $keys = ['a', 'b', 'c'];
  $arr = array_fill_keys($keys, 'X');
  // Output: ['a' => 'X', 'b' => 'X', 'c' => 'X']
  ```

## 2. Modification

### Adding/Removing Elements

#### `array_push()`

Adds elements to the end of an array. Use when you want to \*append elements.

- **Syntax**: `array_push(array, value1, value2, ...)`
- **Example**:

  ```php
  $arr = [1, 2];
  array_push($arr, 3, 4);
  // Output: [1, 2, 3, 4]

  $assocArray = ["a" => 1, "b" => 2];
  array_push($assocArray, 3);
  // Result: ["a" => 1, "b" => 2, 0 => 3]

  $multiArray = [[1, 2], [3, 4]];
  array_push($multiArray[1], 5);
  // Result: [[1, 2], [3, 4, 5]]
  ```

#### `array_pop()`

Removes the last element from an array. Use when you need the \*last element removed.

- **Syntax**: `array_pop(array)`
- **Example**:

  ```php
  $arr = [1, 2, 3];
  $last = array_pop($arr);
  // $arr Output: [1, 2]
  // $last Output: 3

  $assocArray = ["a" => 1, "b" => 2];
  $lastElement = array_pop($assocArray);
  // $lastElement = 2, $assocArray = ["a" => 1]

  $multiArray = [[1, 2], [3, 4]];
  $lastElement = array_pop($multiArray[1]);
  // $lastElement = 4, $multiArray = [[1, 2], [3]]
  ```

#### `array_shift()`

Removes the first element from an array. Use when you need the \*first element removed.

- **Syntax**: `array_shift(array)`
- **Example**:

  ```php
  $arr = [1, 2, 3];
  $first = array_shift($arr);
  // $arr Output: [2, 3]
  // $first Output: 1

  $assocArray = ["a" => 1, "b" => 2];
  $firstElement = array_shift($assocArray);
  // $firstElement = 1, $assocArray = ["b" => 2]

  $multiArray = [[1, 2], [3, 4]];
  $firstElement = array_shift($multiArray[1]);
  // $firstElement = 3, $multiArray = [[1, 2], [4]]
  ```

#### `array_unshift()`

Adds elements to the beginning of an array. Use when you want to \*prepend elements.

- **Syntax**: `array_unshift(array, value1, value2, ...)`
- **Example**:

```php
$arr = [2, 3];
array_unshift($arr, 1);
// Output: [1, 2, 3]
```

### Merging/Replacing Arrays

#### `array_combine()`

Combines two arrays into an associative array - CREATE. Use when you need to pair up keys and values.

- **Syntax**: `array_combine(keys, values)`
- **Example**:
  ```php
  $keys = ['a', 'b', 'c'];
  $values = [1, 2, 3];
  $arr = array_combine($keys, $values);
  // Output: ['a' => 1, 'b' => 2, 'c' => 3]
  ```

#### `array_merge()`

Merges two or more arrays. Use when you want to combine \*multiple arrays into one.

- **Syntax**: `array_merge(array1, array2, ...)`
- **Example**:
  ```php
  $arr1 = [1, 2];
  $arr2 = [3, 4];
  $merged = array_merge($arr1, $arr2);
  // Output: [1, 2, 3, 4]
  ```

#### `array_merge_recursive()`

Merges arrays recursively. Use when merging \*multidimensional arrays.

- **Syntax**: `array_merge_recursive(array1, array2, ...)`
- **Example**:
  ```php
  $arr1 = ['a' => 1, 'b' => 2];
  $arr2 = ['a' => 3, 'c' => 4];
  $merged = array_merge_recursive($arr1, $arr2);
  // Output: ['a' => [1, 3], 'b' => 2, 'c' => 4]
  ```

#### `array_replace()`

Replaces elements of the first array with elements from subsequent arrays. Use when you want to replace existing array values.

- **Syntax**: `array_replace(array1, array2, ...)`
- **Example**:
  ```php
  $arr1 = ['a' => 1, 'b' => 2];
  $arr2 = ['b' => 3, 'c' => 4];
  $replaced = array_replace($arr1, $arr2);
  // Output: ['a' => 1, 'b' => 3, 'c' => 4]
  ```

#### `array_replace_recursive()`

Replaces elements recursively. Use for multidimensional arrays.

- **Syntax**: `array_replace_recursive(array1, array2, ...)`
- **Example**:
  ```php
  $arr1 = ['a' => ['b' => 1]];
  $arr2 = ['a' => ['b' => 2, 'c' => 3]];
  $replaced = array_replace_recursive($arr1, $arr2);
  // Output: ['a' => ['b' => 2, 'c' => 3]]
  ```

### Manipulation

#### `array_chunk()`

Splits an array into chunks. Use when you want to \*split an array into smaller arrays.

- **Syntax**: `array_chunk(array, size, preserve_keys = false)`
- **Example**:
  ```php
  $arr = [1, 2, 3, 4, 5];
  $chunks = array_chunk($arr, 2);
  // Output: [[1, 2], [3, 4], [5]]
  ```

#### `array_slice()`

Extracts a portion of an array. Use when you need a \*part of an array.

- **Syntax**: `array_slice(array, offset, length = null, preserve_keys = false)`
- **Example**:
  ```php
  $arr = [1, 2, 3, 4, 5];
  $slice = array_slice($arr, 1, 3);
  // Output: [2, 3, 4]
  ```

#### `array_splice()`

Removes and replaces elements in an array. Use when modifying the array in-place.

- **Syntax**: `array_splice(array, offset, length = 0, replacement = [])`
- **Example**:
  ```php
  $arr = [1, 2, 3, 4, 5];
  array_splice($arr, 2, 2, ['a', 'b']);
  // Output: [1, 2, 'a', 'b', 5]
  ```

#### `array_pad()`

Pads an array to a specified length. Use when you need an array of a specific length.

- **Syntax**: `array_pad(array, size, value)`
- **Example**:
  ```php
  $arr = [1, 2];
  $padded = array_pad($arr, 5, 'X');
  // Output: [1, 2, 'X', 'X', 'X']
  ```

#### `array_reverse()`

Reverses the order of an array. Use when you need the elements in reverse order.

- **Syntax**: `array_reverse(array, preserve_keys = false)`
- **Example**:
  ```php
  $arr = [1, 2, 3];
  $reversed = array_reverse($arr);
  // Output: [3, 2, 1]
  ```

## 3. Searching & Access

### `array_key_exists()`

Checks if a key exists in an array. Use when verifying if an array contains a specific key.

- **Syntax**: `array_key_exists(key, array)`
- **Example**:
  ```php
  $arr = ['a' => 1, 'b' => 2];
  $exists = array_key_exists('a', $arr);
  // Output: true
  ```

### `array_keys()`

Returns all the keys of an array. Use when you need to retrieve keys.

- **Syntax**: `array_keys(array, search_value = null, strict = false)`
- **Example**:
  ```php
  $arr = ['a' => 1, 'b' => 2];
  $keys = array_keys($arr);
  // Output: ['a', 'b']
  ```

### `array_column()`

Returns values from a single column in a multidimensional array. Use when extracting a column of values.

- **Syntax**: `array_column(array, column_key, index_key = null)`
- **Example**:
  ```php
  $records = [
    ['id' => 1, 'name' => 'John'],
    ['id' => 2, 'name' => 'Jane'],
  ];
  $names = array_column($records, 'name');
  // Output: ['John', 'Jane']
  ```

### `array_search()`

Searches for a value in an array and returns its key. Use when locating the position of a value.

- **Syntax**: `array_search(value, array, strict = false)`
- **Example**:
  ```php
  $arr = [1, 2, 3];
  $key = array_search(2, $arr);
  // Output: 1
  ```

### `in_array()`

Checks if a value exists in an array. Use when verifying if an array contains a value.

- **Syntax**: `in_array(value, array, strict = false)`
- **Example**:
  ```php
  $arr = [1, 2, 3];
  $exists = in_array(2, $arr);
  // Output: true
  ```

### `array_rand()`

Picks one or more random keys from an array. Use when selecting random elements.

- **Syntax**: `array_rand(array, num = 1)`
- **Example**:
  ```php
  $arr = [1, 2, 3, 4, 5];
  $randomKey = array_rand($arr);
  // Output: (random key from the array)
  ```

### `array_flip()`

Exchanges all keys with their corresponding values in an array. Use when you need to invert keys and values.

- **Syntax**: `array_flip(array)`
- **Example**:
  ```php
  $arr = ['a' => 1, 'b' => 2];
  $flipped = array_flip($arr);
  // Output: [1 => 'a', 2 => 'b']
  ```

### `array_values()`

Returns all the values of an array. Use when you need just the values of an array.

- **Syntax**: `array_values(array)`
- **Example**:
  ```php
  $arr = ['a' => 1, 'b' => 2];
  $values = array_values($arr);
  // Output: [1, 2]
  ```

### `each()`, `current()`, `pos()`, `end()`, `next()`, `prev()`

Functions to iterate over an array. Use for sequential access to array elements.

- **Syntax**:
  ```php
  $arr = [1, 2, 3];
  $current = current($arr); // Output: 1
  $next = next($arr);       // Output: 2
  $prev = prev($arr);       // Output: 1
  $end = end($arr);         // Output: 3
  $current = pos($arr); // Output: 3
  ```

## 4. Filter & Map

### `array_filter()`

Filters elements of an array using a callback function. Use when you need to filter array elements based on a condition.

- **Syntax**: `array_filter(array, callback, mode = 0)`
- **Example**:
  ```php
  $arr = [1, 2, 3, 4];
  $filtered = array_filter($arr, fn($val) => $val > 2);
  // Output: [3, 4]
  ```

### `array_map()`

Applies a callback to the elements of an array. Use when transforming array elements.

- **Syntax**: `array_map(callback, array1, array2, ...)`
- **Example**:
  ```php
  $arr = [1, 2, 3];
  $mapped = array_map(fn($val) => $val * 2, $arr);
  // Output: [2, 4, 6]
  ```

### `array_reduce()`

Reduces an array to a single value using a callback. Use for accumulating or summarizing data.

- **Syntax**: `array_reduce(array, callback, initial = null)`
- **Example**:
  ```php
  $arr = [1, 2, 3];
  $sum = array_reduce($arr, fn($carry, $val) => $carry + $val, 0);
  // Output: 6
  ```

### `array_walk()`

Applies a callback to every element of an array. Use for applying changes in-place.

- **Syntax**: `array_walk(array, callback, userdata = null)`
- **Example**:
  ```php
  $arr = [1, 2, 3];
  array_walk($arr, fn(&$val) => $val *= 2);
  // Output: [2, 4, 6]
  ```

### `array_walk_recursive()`

Applies a callback to every element of a multidimensional array. Use for nested arrays.

- **Syntax**: `array_walk_recursive(array, callback, userdata = null)`
- **Example**:
  ```php
  $arr = ['a' => 1, 'b' => ['c' => 2, 'd' => 3]];
  array_walk_recursive($arr, fn(&$val) => $val *= 2);
  // Output: ['a' => 2, 'b' => ['c' => 4, 'd' => 6]]
  ```

## 5. Sorting

### Indexed Arrays

#### `sort()`

**What**: Sorts an array in ascending order.
**When & Where**: Use when sorting numerically or alphabetically.
**How**:

- **Syntax**: `sort(array, sort_flags = SORT_REGULAR)`
- **Example**:
  ```php
  $arr = [3, 1, 2];
  sort($arr);
  // Output: [1, 2, 3]
  ```

#### `rsort()`

**What**: Sorts an array in descending order.
**When & Where**: Use when sorting in reverse order.
**How**:

- **Syntax**: `rsort(array, sort_flags = SORT_REGULAR)`
- **Example**:
  ```php
  $arr = [3, 1, 2];
  rsort($arr);
  // Output: [3, 2, 1]
  ```

#### `shuffle()`

**What**: Randomly shuffles the elements of an array.
**When & Where**: Use when randomizing array order.
**How**:

- **Syntax**: `shuffle(array)`
- **Example**:
  ```php
  $arr = [1, 2, 3];
  shuffle($arr);
  // Output: (random order of [1, 2, 3])
  ```

### Associative Arrays

#### `asort()`

**What**: Sorts an associative array in ascending order by value.
**When & Where**: Use when sorting associative arrays by values.
**How**:

- **Syntax**: `asort(array, sort_flags = SORT_REGULAR)`
- **Example**:
  ```php
  $arr = ['a' => 3, 'b' => 1, 'c' => 2];
  asort($arr);
  // Output: ['b' => 1, 'c' => 2, 'a' => 3]
  ```

#### `arsort()`

**What**: Sorts an associative array in descending order by value.
**When & Where**: Use when sorting in reverse

```

```
