+++
title= "Learnings of the Day 14/12"
date= '2023-12-14'
draft= 'false'
tags= ["learning", "cpp","JS", "problem solving", "Leetcode"]
categories= ["leetcode" , "Days_Of_Cpp"]
+++


##JavaScript:
### Day 3: Solving in 3 Different Ways
[Leetcode](https://leetcode.com/problems/counter-ii/description/?envType=study-plan-v2&envId=30-days-of-javascript)

From the question, we need to create three functions: `increment()`, `decrement()`, and `reset()`. Let's explore three different ways to implement these functions.

##### 1. Using Traditional Function
```javascript
var createCounter = function(init) {
  let presentCount = init;

  function increment() {
    return ++presentCount;
  }

  function decrement() {
    return --presentCount;
  }

  function reset() {
    return (presentCount = init);
  }

  return { increment, decrement, reset };
};
```

**Time and Space Complexity:** O(1)

##### 2. Using Arrow Function

```javascript
var createCounter = function(init) {
    let presentCount = init
    return {
        increment: () => ++presentCount,
        decrement: () => --presentCount,
        reset: () => presentCount = init,
    }
};
```

**Time and Space Complexity:** O(1)

#### 3. Using Class

```javascript
class Counter {
  constructor(init) {
    this.init = init;
    this.presentCount = init;
  }

  increment() {
    this.presentCount += 1;
    return this.presentCount;
  }

  decrement() {
    this.presentCount -= 1;
    return this.presentCount;
  }

  reset() {
    this.presentCount = this.init;
    return this.presentCount;
  }
}

var createCounter = function(init) {
  return new Counter(init);
};
```

**Time and Space Complexity:** O(1)

In conclusion, the choice depends on the specific use case:
- Classes are useful for creating objects with shared behavior.
- Traditional functions are suitable for reusable chunks of code.
- Arrow functions are handy for short, concise functions or when preserving the value of `this` is important.

I believe that classes are the best way to implement this type of problem in real life as they provide flexibility in scaling with shared behavioral properties.


### Day 4: Practicality and Efficiency are Two Sides of the Same Coin!
[Leetcode](https://leetcode.com/problems/apply-transform-over-each-element-in-array/?envType=study-plan-v2&envId=30-days-of-javascript)
##### Why Was Array.map() Restricted?
I can think of three reasons why the problem setter might have restricted the use of Array.map():
1. To encourage developers to think creatively and come up with alternative solutions using loops, functions, or recursion.
2. Using Array.map() may not always be the most efficient solution, especially for large arrays, and other techniques like loops or recursion may be more performant. So, it's good to know and be comfortable with different approaches to solving array manipulation problems.
3. It could have gotten too easy with Array.map()... 😉

#### Solutions:
##### 1. Using a For Loop with Operational Container:
```javascript
var map = function(arr, fn) {
  const transformedArr = [];
  for (let i = 0; i < arr.length; i++) {
    transformedArr[i] = fn(arr[i], i);
  }
  return transformedArr;
};
```
**Time and Space Complexity:** O(n)

##### 2. Using a For Loop Without Any Container (In-memory Transformations):
```javascript
var map = function(arr, fn) {
    for (let i = 0; i < arr.length; ++i) {
        arr[i] = fn(arr[i], i);
    }
    return arr;
};
```
**Time and Space Complexity:** O(n) and O(1) - *Note: This is not recommended as it alters the given data.*

##### 3. Using the forEach Method:
```javascript
var map = function(arr, fn) {
  const transformedArr = [];
  arr.forEach((element, index) => {
    transformedArr[index] = fn(element, index);
  });
  return transformedArr;
};
```
**Time and Space Complexity:** O(n)

##### 4. Using the Reduce Method:
```javascript
var map = function(arr, fn) {
  return arr.reduce((transformedArr, element, index) => {
    transformedArr[index] = fn(element, index);
    return transformedArr;
  }, []);
};
```
**Time and Space Complexity:** O(n)

##### 5. Using the For...of Loop:
```javascript
var map = function(arr, fn) {
  const transformedArr = [];
  let index = 0;
  for (const element of arr) {
    transformedArr[index] = fn(element, index);
    index++;
  }
  return transformedArr;
};
```
**Time and Space Complexity:** O(n)

##### Bonus: Using Array.map() (For Fun):
```javascript
var map = function(arr, fn) {
     return arr.map((element, index) => fn(element, index));
};
```
**Time and Space Complexity:** O(n)


### Day 5: Different Approaches With Beginner-Friendly Explanation
[Leetcode](https://leetcode.com/problems/filter-elements-from-array/description/?envType=study-plan-v2&envId=30-days-of-javascript)
#### Problem Summary
The problem requires us to return only the truthy values from an array, where truthy values are those that are considered true in JavaScript, and falsy values are considered false.

In JavaScript, the following values are considered falsy:
- false
- 0
- -0
- 0n (BigInt zero)
- '' (empty string)
- null
- undefined
- NaN

All other values are considered truthy, including:
- '0' (string containing a single zero)
- 'false' (string containing the word "false")
- [] (empty array)
- {} (empty object)
- function() {} (empty function)

#### Approaches
##### Approach 1: Using a for loop and Array.push
One way to solve this problem is to iterate through the input array using a for loop, and for each element, call the filtering function with two arguments - the element itself and its index. If the filtering function returns a truthy value, add the element to a result array using the push method.
```javascript
var filter = function(arr, fn) {
  const result = [];
  for (let i = 0; i < arr.length; i++) {
    if (fn(arr[i], i)) {
      result.push(arr[i]);
    }
  }
  return result;
};
```

##### Approach 2: Using Array.reduce
Another way to solve this problem is to use the Array.reduce method. We can use Array.reduce to accumulate the elements that satisfy the filtering function into a new array.
```javascript
var filter = function(arr, fn) {
  return arr.reduce((result, value, index) => {
    if (fn(value, index)) {
      result.push(value);
    }
    return result;
  }, []);
};
```

##### Approach 3: Using Array.forEach
We can also solve this problem using the Array.forEach method. We can use Array.forEach to iterate through the input array, and for each element, call the filtering function with two arguments - the element itself and its index. If the filtering function returns a truthy value, add the element to a result array using the push method.
```javascript
var filter = function(arr, fn) {
  const result = [];
  arr.forEach((value, index) => {
    if (fn(value, index)) {
      result.push(value);
    }
  });
  return result;
};
```

##### Approach 4: Using Array.map and Array.reduce
We can also use the Array.map method to create a new array containing only the elements that satisfy the filtering function, and then use Array.reduce to remove any undefined elements from the result array.
```javascript
var filter = function(arr, fn) {
  return arr.map((value, index) => {
    if (fn(value, index)) {
      return value;
    }
  }).reduce((result, value) => {
    if (value !== undefined) {
      result.push(value);
    }
    return result;
  }, []);
};
```

##### Approach 5: Using Array.flatMap()
The flatMap method applies a function to each element of an array and flattens the result into a new array. In this case, the function passed to flatMap takes two arguments, the current element i and its index j, and uses a ternary operator to check if fn(i, j) is truthy. If it is, the function returns an array containing i, otherwise it returns an empty array. The flatMap method flattens these arrays into a new array containing only the elements that satisfy our filtering function.

```javascript
var filter = function(arr, fn) {
    return arr.flatMap((i, j) => fn(i, j) ? [i] : []);
};
```


------------
## Cpp:
### Problem 1: Baseball Game

[Leetcode](https://leetcode.com/problems/baseball-game/?envType=study-plan-v2&envId=programming-skills)

#### Code:
```cpp
class Solution {
public:
    int calPoints(vector<string>& operations) {
        stack<int> s;
        for (int i=0;i<operations.size();i++)
        {
            if(operations[i]==isdigit(operations[i]))
            {
                s.push(operations[i]);
            }
            else if(operations[i]=='+')
            {
                int last=s.top();
                s.pop();
                int secLast=s.top();
                s.pop();
                s.push(last);
                s.push(last+secLast);
            }
            else if(operations[i]=='D')
            {
                int f=s.top();
                s.push(2*f);
            }
            else if(operation[i]=='C')
            {
                s.pop();
            }
        }
        int sum = 0;
        while (!s.empty()) {
            sum += s.top();
            s.pop();
        }
        return sum;
    }
};
```

#### Modifications:
```cpp
class Solution {
public:
    int calPoints(vector<string>& operations) {
        stack<int> s;
        for (int i=0;i<operations.size();i++)
        {
            if(isdigit(operations[i][0]) || (operations[i][0] == '-' && isdigit(operations[i][1])))
            {
                s.push(stoi(operations[i]));
            }
            else if(operations[i]=="+")
            {
                int last=s.top();
                s.pop();
                int secLast=s.top();
                s.push(last);;
                s.push(last+secLast);
            }
            else if(operations[i]=="D")
            {
                int f=s.top();
                s.push(2*f);
            }
            else if(operations[i]=="C")
            {
                s.pop();
            }
        }
        int sum = 0;
        while (!s.empty()) {
            sum += s.top();
            s.pop();
        }
        return sum;
    }
};
```

#### Time & Space Complexity:
- Time complexity: O(n)
- Space complexity: O(n)

#### Challenges Faced & Learnings:
- `operations[i]==isdigit(operations[i])` is corrected to `isdigit(operations[i][0])`. 
- `stoi(operations[i])` to convert the string to an integer when pushing onto the stack.
- The `isdigit function()` checks if a character is a decimal digit character (0-9). It can be used for positive integers. Regarding the use of `operations[i][0]`, it is because `operations[i]` is a string, and we are checking the first character of that string using [0].
- `(operations[i][0] == '-' && isdigit(operations[i][1]))` This modification allows for negative numbers by checking if the first character is '-' and the subsequent characters are digits. If this condition is true, it assumes a negative number.

#### Real-time Use Cases:
- Calculating scores in a game with certain rules.
- Managing a sequence of operations with cumulative effects.

### Problem 2: Robot Return to Origin

[Leetcode](https://leetcode.com/problems/robot-return-to-origin/?envType=study-plan-v2&envId=programming-skills)

#### Code:
```cpp
class Solution {
public:
    bool judgeCircle(string moves) {
        if(moves.length()%2!=0)
        {
            return false;
        }
        else 
        {
            char robArr=moves.toCharArray();
            int l=0;r=0;u=0;d=0;
            for(int i=0;i<robArr.length();i++)
            {
                if(robArr[i]=='L')
                {
                    l++;
                }
                else if(robArr[i]=='R')
                {
                    r++;
                }
                else if(robArr[i]=='U')
                {
                    u++;
                }
                else if(robArr[i]=='D')
                {
                    d++;
                }
            }
            if(l==r && u==d)
            {
                return true;
            }
            else
            {
                return false;
            }
        }
    }
};
```

#### Modifications:
```cpp
class Solution {
public:
    bool judgeCircle(string moves) {
        if(moves.length()%2!=0)
        {
            return false;
        }
        else 
        {
            int l=0,r=0,u=0,d=0;
            for(int i=0;i<moves.length();i++)
            {
                if(moves[i]=='L')
                {
                    l++;
                }
                else if(moves[i]=='R')
                {
                    r++;
                }
                else if(moves[i]=='U')
                {
                    u++;
                }
                else if(moves[i]=='D')
                {
                    d++;
                }
            }
            return (l==r && u==d);
        }
    }
};
```

#### Time & Space Complexity:
- Time complexity: O(n)
- Space complexity: O(1)

#### Challenges Faced & Learnings:
- Challenges: Properly counting movements in each direction.
- char robArr=moves.toCharArray(); was changed to int l = 0, r = 0, u = 0, d = 0; to declare the counting variables correctly.
- The loop condition was changed from robArr.length() to moves.length() to iterate through the characters in the string correctly.
- The typo int l=0;r=0;u=0;d=0; was corrected to declare each variable separately.
- Instead of using an if-else statement to return true or false, the code now directly returns the expression (l == r) && (u == d), which is the condition you want to check.
- Learnings: Importance of simplicity in counting problems and optimizing space usage.

#### Real-time Use Cases:
- Checking the validity of a robot's movement sequence.
- Validating movements in grid-based applications.

Then I done some OS && Cogita_read,it will post it new post.[link]()