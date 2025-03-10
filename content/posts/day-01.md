+++
title= "Day 01"
date= '2025-03-10'
draft= 'false'
tags= ["SelectionSort", "GrammarTypes", "ControlFlow","ErrorHandling"]
categories= ["Days_of_Back"]
+++

# A Starting Journey of 2025 Goals

## 1. Coding of the day : **Selection Sort**

```c++
function selectionSort(array)
{
    int n = array.size();
    for(int i = 0; i<n-1;++i)
    {
        int minVal = i;
        for(int j=i+j;j<n;++j)
        {
            if(array[j]<array[minVal])
            {
                minVal = j;
            }
        }
        swap(array[i],array[minVal]);
    }
}
```

- Advantage of Selection sort is the **Memory writes** which is better than the Insertion sort and Bubble sort, It makes at most N-1 swaps.
- Memory Writes is a value overwritten in memory, and Swap operation changes the positions of the elements.

## 2. JS of the day : **Grammar Types and Control Flow/Error Handling**

### Grammar Types :

- `const` only prevents re-assignments, but doesn't prevent mutations. The properties of Objects/Arrays assigned to constants are not protected, so the following statement is executed without problems.
- `parseInt()` to convert the string to numbers.
- **Literals** are actual values (e.g., 10, "Aja!", true).
- **Variables** store values and can change (e.g., $name = "Aja!";).
- **Identifiers** are names given to variables, functions, or classes.

### Error Handling :

- Use `try`, `catch` as much possible.
- Property names that are not valid identifiers cannot be accessed as a dot (.) property.

```js
const unusualPropertyNames = {
  '': 'An empty string',
  '!': 'Bang!'
}
console.log(unusualPropertyNames.'');   // SyntaxError: Unexpected string
console.log(unusualPropertyNames.!);    // SyntaxError: Unexpected token !
```
