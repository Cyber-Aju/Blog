+++
title= "Array in PHP"
date= '2024-08-19'
draft= 'false'
tags= ["array"]
categories= ["php"]
+++

### 1. **`array()`**

- **Example**:
  ```php
  $arr = array('1', '2', null, array('a', 'b')); // Mixing types
  ```
- **Output**:
  ```php
  // Output: ['1', '2', null, ['a', 'b']]
  ```
- **Explanation**: While PHP allows mixed types within an array, this can lead to unexpected results when manipulating or accessing elements, particularly if expecting uniform data types.

### 2. **`array_fill()`**

- **Example**:
  ```php
  $arr = array_fill(0, -3, 'A');
  ```
- **Output**:
  ```php
  // Output: Warning: array_fill(): Number of elements must be positive in ...
  // Result: []
  ```
- **Explanation**: The function expects `num` to be a positive integer. A negative value leads to a warning and results in an empty array.

- **Example**:
  ```php
  $arr = array_fill(-2, 3, 'B');
  ```
- **Output**:
  ```php
  // Output: [-2 => 'B', -1 => 'B', 0 => 'B']
  ```
- **Explanation**: While PHP accepts negative indices, it can make array handling unpredictable, particularly if your array is later combined with others or used in loops.

### 3. **`array_fill_keys()`**

- **Example**:
  ```php
  $keys = [1, 2, 2, 'a', 'b', []]; // Non-unique keys and an invalid array key
  $arr = array_fill_keys($keys, 'Y');
  ```
- **Output**:
  ```php
  // Output: Warning: Illegal offset type in ...
  // Result: ['1' => 'Y', '2' => 'Y', 'a' => 'Y', 'b' => 'Y']
  ```
- **Explanation**: PHP does not allow arrays as keys and expects keys to be unique. If an invalid type (like an array) is used as a key, it triggers a warning and skips that key.

---

---

### 1. **`array_push()`**

If you attempt to push elements onto a non-array variable.

- **Example**:
  ```php
  $arr = "not an array";
  array_push($arr, 3, 4);
  ```
- **Output**:
  ```php
  // Output: Warning: array_push() expects parameter 1 to be array, string given ...
  // Result: array_push() will not work; $arr remains "not an array"
  ```
- **Explanation**: `array_push()` expects the first argument to be an array. If it isn’t, it generates a warning and does not modify the variable.

### 2. **`array_pop()`**

If you pop from an empty array.

- **Example**:
  ```php
  $arr = [];
  $last = array_pop($arr);
  ```
- **Output**:
  ```php
  // Output: NULL
  // $arr Output: []
  ```
- **Explanation**: When `array_pop()` is used on an empty array, it returns `NULL` and does not produce any warnings or errors.

### 3. **`array_shift()`**

    If you shift from an empty array.

- **Example**:
  ```php
  $arr = [];
  $first = array_shift($arr);
  ```
- **Output**:
  ```php
  // Output: NULL
  // $arr Output: []
  ```
- **Explanation**: Similar to `array_pop()`, `array_shift()` on an empty array returns `NULL` without producing any warnings.

### 4. **`array_unshift()`**

If you unshift onto a non-array variable.

- **Example**:
  ```php
  $arr = "not an array";
  array_unshift($arr, 1);
  ```
- **Output**:
  ```php
  // Output: Warning: array_unshift() expects parameter 1 to be array, string given ...
  // Result: array_unshift() will not work; $arr remains "not an array"
  ```
- **Explanation**: `array_unshift()` expects the first argument to be an array. If it isn’t, it generates a warning and does not modify the variable.

### 5. **`array_combine()`**

If the `keys` and `values` arrays have different lengths.

- **Example**:
  ```php
  $keys = ['a', 'b'];
  $values = [1, 2, 3];
  $arr = array_combine($keys, $values);
  ```
- **Output**:
  ```php
  // Output: Warning: array_combine(): Both parameters should have an equal number of elements ...
  // Result: false
  ```
- **Explanation**: `array_combine()` requires that the `keys` and `values` arrays have the same number of elements. If not, it returns `false` and triggers a warning.

### 6. **`array_merge()`**

If you merge arrays with conflicting string keys.

- **Example**:
  ```php
  $arr1 = ['a' => 1, 'b' => 2];
  $arr2 = ['a' => 3, 'c' => 4];
  $merged = array_merge($arr1, $arr2);
  ```
- **Output**:
  ```php
  // Output: ['a' => 3, 'b' => 2, 'c' => 4]
  ```
- **Explanation**: When merging arrays with duplicate string keys, `array_merge()` overwrites the values from earlier arrays with values from later ones.

### 7. **`array_merge_recursive()`**

If you merge arrays with conflicting data types for the same key.

- **Example**:
  ```php
  $arr1 = ['a' => 1];
  $arr2 = ['a' => [2, 3]];
  $merged = array_merge_recursive($arr1, $arr2);
  ```
- **Output**:
  ```php
  // Output: ['a' => [1, 2, 3]]
  ```
- **Explanation**: `array_merge_recursive()` attempts to merge arrays and values together. If an element in one array is a scalar and the corresponding element in another array is an array, it merges them into a single array, which can lead to unexpected results.

### 8. **`array_replace()`**

If the keys don’t match between arrays.

- **Example**:
  ```php
  $arr1 = ['a' => 1, 'b' => 2];
  $arr2 = ['c' => 3];
  $replaced = array_replace($arr1, $arr2);
  ```
- **Output**:
  ```php
  // Output: ['a' => 1, 'b' => 2, 'c' => 3]
  ```
- **Explanation**: `array_replace()` will only replace existing keys; if the keys do not match, it simply adds the new key-value pairs to the array, which may not be the intended outcome.

### 9. **`array_replace_recursive()`**

If there are conflicting data types in nested arrays.

- **Example**:
  ```php
  $arr1 = ['a' => ['b' => 1]];
  $arr2 = ['a' => 2];
  $replaced = array_replace_recursive($arr1, $arr2);
  ```
- **Output**:
  ```php
  // Output: ['a' => 2]
  ```
- **Explanation**: If a nested array in `array1` is replaced by a scalar value in `array2`, the entire nested array is replaced, which might lead to loss of data.

### 10. **`array_chunk()`**

**Negative Scenario**: If the chunk size is larger than the array size.

- **Example**:
  ```php
  $arr = [1, 2, 3];
  $chunks = array_chunk($arr, 5);
  ```
- **Output**:
  ```php
  // Output: [[1, 2, 3]]
  ```
- **Explanation**: If the chunk size is greater than the number of elements in the array, `array_chunk()` returns the entire array as a single chunk.

---

## chunck()

In the `array_chunk()` function, the `true` parameter is a flag that determines whether the original array's keys should be preserved when the array is chunked into smaller arrays.

1. **Without `true` (default)**: Keys are re-indexed in the resulting chunks.
2. **With `true`**: Original keys are preserved in the resulting chunks.

(chucnk)[https://www.php.net/manual/en/function.array-chunk.php]

### with Associative Array:

```php
$input_array = array('key1' => 'a', 'key2' => 'b', 'key3' => 'c', 'key4' => 'd', 'key5' => 'e');
print_r(array_chunk($input_array, 2));
print_r(array_chunk($input_array, 2, true));
```

**Without `true`:**

```php
Array
(
    [0] => Array
        (
            [0] => a
            [1] => b
        )
    [1] => Array
        (
            [0] => c
            [1] => d
        )
    [2] => Array
        (
            [0] => e
        )
)
```

Here, the original keys (`key1`, `key2`, etc.) are lost because the chunks are re-indexed starting from `0`.

**With `true`:**

```php
Array
(
    [0] => Array
        (
            [key1] => a
            [key2] => b
        )
    [1] => Array
        (
            [key3] => c
            [key4] => d
        )
    [2] => Array
        (
            [key5] => e
        )
)
```

Here, the original keys are preserved (`key1`, `key2`, etc.).

## slice

(slice)[https://www.php.net/manual/en/function.array-slice.php]

---

### 11. **`array_slice()`**

**Negative Scenario**: If the offset is out of bounds.

- **Example**:
  ```php
  $arr = [1, 2, 3];
  $slice = array_slice($arr, 5);
  ```
- **Output**:
  ```php
  // Output: []
  ```
- **Explanation**: If the offset exceeds the array length, `array_slice()` returns an empty array.

### 12. **`array_splice()`**

**Negative Scenario**: If the length parameter is negative.

- **Example**:
  ```php
  $arr = [1, 2, 3, 4];
  array_splice($arr, 1, -2);
  ```
- **Output**:
  ```php
  // Output: [1, 4]
  ```
- **Explanation**: A negative length in `array_splice()` removes elements up to the last element specified by the negative length, which can result in unexpected array truncation.

### 13. **`array_pad()`**

**Negative Scenario**: If the size is smaller than the array size.

- **Example**:
  ```php
  $arr = [1, 2, 3];
  $padded = array_pad($arr, 2, 'X');
  ```
- **Output**:
  ```php
  // Output: [1, 2, 3]
  ```
- **Explanation**: If the specified size is smaller than or equal to the array length, `array_pad()` returns the original array without adding any elements.

### 14. **`array_reverse()`**

**Negative Scenario**: If you reverse an associative array and expect keys to be preserved.

- **Example**:
  ```php
  $arr = ['a' => 1, 'b' => 2];
  $reversed = array_reverse($arr);
  ```
- **Output**:
  ```php
  // Output: ['b' => 2, 'a' => 1]
  ```
- **Explanation**: By default, `array_reverse()` preserves keys, which can result in unexpected outcomes if you expect the keys to be reindexed.
