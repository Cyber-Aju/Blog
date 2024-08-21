+++
title= "Array in PHP"
date= '2024-08-19'
draft= 'false'
tags= ["array"]
categories= ["php"]
+++

## Conversions:

### **1. Array to String**

**Where**: Use when you need a simple, readable format, such as displaying list items (implode). Example : Generating a URL query string.

```php
$params = ["name" => "Aja", "role" => "Developer"];
$queryString = http_build_query($params);
echo "https://example.com/?" . $queryString;
// Outputs: https://example.com/?name=Aja&role=Developer
```

[Query string](https://en.wikipedia.org/wiki/Query_string)

### **2. Array to Object**

**Where**: Use when you need to access elements as properties, particularly in object-oriented programming. Example : _Converting configuration arrays in an API response_.

```php
$config = ["api_key" => "123456", "timeout" => 30];
$configObject = (object) $config;
echo $configObject->api_key; // Outputs: 123456
```

[Array vs object](https://towardsdatascience.com/practical-javascript-arrays-vs-objects-3c1f895907bd)

### **3. Array to CSV**

**Where**: Use when exporting data for spreadsheets or for external data exchange.

```php
$data = ["Name" => "Aja", "Role" => "Developer"];
$handle = fopen('file.csv', 'w');
fputcsv($handle, array_keys($data));
fputcsv($handle, array_values($data));
fclose($handle);
// Creates file.csv with the content:
// Name,Role
// Aja,Developer
```

## Built-in functions:

### **1. Array Manipulation**

#### **array_pop()**

**Description**: Removes the last element from an array.

```php
$stack = array("orange", "banana", "apple");
$fruit = array_pop($stack);
print_r($stack);
```

**Output**:

```
Array
(
    [0] => orange
    [1] => banana
)
```

#### **array_push()**

**Description**: Pushes one or more elements onto the end of an array.

```php
$stack = array("orange", "banana");
array_push($stack, "apple", "raspberry");
print_r($stack);
```

**Output**:

```
Array
(
    [0] => orange
    [1] => banana
    [2] => apple
    [3] => raspberry
)
```

#### **array_shift()**

**Description**: Removes the first element from an array and returns it.

```php
$queue = array("orange", "banana", "apple");
$fruit = array_shift($queue);
print_r($queue);
```

**Output**:

```
Array
(
    [0] => banana
    [1] => apple
)
```

#### **array_unshift()**

**Description**: Prepends one or more elements to the beginning of an array.

```php
$queue = array("banana", "apple");
array_unshift($queue, "orange", "raspberry");
print_r($queue);
```

**Output**:

```
Array
(
    [0] => orange
    [1] => raspberry
    [2] => banana
    [3] => apple
)
```

---

### **2. Array Transformation**

#### **array_replace()**

**Description**: Replaces elements in the first array with values from the second array.

```php
$base = array("orange", "banana", "apple");
$replacements = array(0 => "pineapple", 2 => "cherry");
$basket = array_replace($base, $replacements);
print_r($basket);
```

**Output**:

```
Array
(
    [0] => pineapple
    [1] => banana
    [2] => cherry
)
```

#### **array_reverse()**

**Description**: Returns an array with elements in reverse order.

```php
$input = array("php", 4.0, array("green", "red"));
$reversed = array_reverse($input);
print_r($reversed);
```

**Output**:

```
Array
(
    [0] => Array
        (
            [0] => green
            [1] => red
        )
    [1] => 4
    [2] => php
)
```

#### **array_pad()**

**Description**: Pads an array to the specified length with a value.

```php
$input = array(12, 10, 9);
$result = array_pad($input, 5, 0);
print_r($result);
```

**Output**:

```
Array
(
    [0] => 12
    [1] => 10
    [2] => 9
    [3] => 0
    [4] => 0
)
```

#### **array_slice()**

**Description**: Extracts a slice of the array.

```php
$input = array("a", "b", "c", "d");
$slice = array_slice($input, 2);
print_r($slice);
```

**Output**:

```
Array
(
    [0] => c
    [1] => d
)
```

#### **array_splice()**

**Description**: Removes a portion of the array and replaces it with something else.

```php
$input = array("red", "green", "blue", "yellow");
array_splice($input, 2, 1, array("purple", "orange"));
print_r($input);
```

**Output**:

```
Array
(
    [0] => red
    [1] => green
    [2] => purple
    [3] => orange
    [4] => yellow
)
```

---

### **3. Array Search**

#### **array_search()**

**Description**: Searches the array for a given value and returns the corresponding key if successful.

```php
$array = array(0 => 'blue', 1 => 'red', 2 => 'green');
$key = array_search('green', $array);
echo $key;
```

**Output**:

```
2
```

#### **array_udiff()**

**Description**: Computes the difference of arrays by using a callback function for comparison.

```php
$array1 = array(0 => 1, 1 => 2, 2 => 3);
$array2 = array(0 => 1, 1 => 2, 2 => 4);
$diff = array_udiff($array1, $array2, "compare_func");

function compare_func($a, $b) {
    return ($a - $b);
}

print_r($diff);
```

**Output**:

```
Array
(
    [2] => 3
)
```

#### **array_uintersect()**

**Description**: Computes the intersection of arrays, compares data by a callback function.

```php
$array1 = array(0 => 'apple', 1 => 'orange');
$array2 = array(0 => 'banana', 1 => 'orange');
$intersect = array_uintersect($array1, $array2, "compare_func");

function compare_func($a, $b) {
    return strcmp($a, $b);
}

print_r($intersect);
```

**Output**:

```
Array
(
    [1] => orange
)
```

---

### **4. Array Aggregation**

#### **array_reduce()**

**Description**: Reduces an array to a single value using a callback function.

```php
$numbers = array(1, 2, 3, 4, 5);
$sum = array_reduce($numbers, function($carry, $item) {
    return $carry + $item;
});
echo $sum;
```

**Output**:

```
15
```

#### **array_sum()**

**Description**: Returns the sum of values in an array.

```php
$numbers = array(1, 2, 3, 4, 5);
$sum = array_sum($numbers);
echo $sum;
```

**Output**:

```
15
```

---

### **5. Array Utility**

#### **array_rand()**

**Description**: Picks one or more random entries out of an array.

```php
$input = array("apple", "banana", "cherry", "date");
$rand_keys = array_rand($input, 2);
echo $input[$rand_keys[0]] . "\n";
echo $input[$rand_keys[1]];
```

**Output**:

```
banana
date
```
