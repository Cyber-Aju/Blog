+++
title= "Learnings of the Day 12/12"
date= '2023-12-12'
draft= 'false'
tags= ["learning", "cpp","JS", "problem solving", "Leetcode"]
categories= ["leetcode" , "Days_Of_Cpp"]
+++

### 1. Problem: Can Make Arithmetic Progression From Sequence

[Leetcode](https://leetcode.com/problems/can-make-arithmetic-progression-from-sequence/?envType=study-plan-v2&envId=programming-skills)

#### Original Code:
```cpp
class Solution {
public:
    bool canMakeArithmeticProgression(vector<int>& arr) {
        for(int i=0;i<arr.size();i++)
        {
            int z=arr[0]-arr[1];
            if(z!=(arr[i]-arr[i+1]))
            {
                return false;
            }
        }
        return true;
    }
};
```

#### Modifications:
```cpp
class Solution {
public:
    bool canMakeArithmeticProgression(vector<int>& arr) {
        sort(arr.begin(),arr.end());
        int z=arr[1]-arr[0];
        for(int i=0;i<(arr.size()-1);i++)
        {
            if(z!=(arr[i+1]-arr[i]))
            {
                return false;
            }
        }
        return true;
    }
};
```
caused of 'outbound errors'.

#### Complexity:
- Time Complexity: O(n)
- Space Complexity: O(1)

#### Challenges Faced:
- Ensuring correct handling of edge cases and optimizing the code for efficiency and Outbounds Error

#### Learnings:
- Importance of not always relying on sorting and exploring alternative approaches.
- Paying attention to edge cases.
- "Out of bounds" refers to attempting to access an element of an array or a container at an index that is not within the valid range of indices for that container. In most programming languages, array indices start from 0, so the valid range is typically from 0 to `size - 1`.

When you try to access an element at an index that is equal to or greater than the size of the array, you are going beyond the bounds of the array. This can lead to undefined behavior, and it often results in runtime errors, crashes, or unexpected behavior in your program.

Here's how to recognize and rectify the "out of bounds" issue:

##### Recognizing "Out of Bounds" Issues:

1. **Index Range in the Loop Condition:**
   - When using a loop to iterate through an array, the loop condition should be `i < arr.size()` to ensure that `i` stays within the bounds of the array.
   - If `i` becomes equal to `arr.size()`, the loop should terminate to avoid accessing an element beyond the array's valid indices.

2. **Accessing Elements:**
   - Be cautious when accessing elements at indices calculated within the loop. Ensure that the index is within the valid range before attempting to access the element.

##### Rectifying "Out of Bounds" Issues:

1. **Loop Condition Adjustment:**
   - When iterating through an array, ensure that the loop condition prevents `i` from exceeding `arr.size() - 1`.
   - For example, use `i < arr.size()` instead of `i <= arr.size()`.

2. **Check Bounds Before Accessing:**
   - Before accessing an element at index `i`, check if `i` is within the valid range using an `if` statement.
   - For example:
     ```cpp
     if (i < arr.size()) {
         // Access arr[i] safely
     }
     ```

3. **Loop Until `arr.size() - 1`:**
   - If your loop is designed to compare consecutive elements, loop until `arr.size() - 1` to avoid accessing `arr[i + 1]` when `i` is equal to `arr.size() - 1`.

4. **Use Range-Based For Loops:**
   - In languages that support range-based for loops (e.g., C++ with C++11 and later), consider using them to simplify the loop and reduce the risk of index-related errors.
   - Example:
     ```cpp
     for (const auto& element : arr) {
         // Process each element
     }
     ```

#### Use Cases:
- Checking if a sequence of numbers follows an arithmetic progression.

------------------------

### 2. Problem: Monotonic Array

[Leetcode](https://leetcode.com/problems/monotonic-array/?envType=study-plan-v2&envId=programming-skills)

#### Original Code:
```cpp
class Solution {
public:
    bool isMonotonic(vector<int>& nums) {
        for (int i=0;i<nums.size();i++)
        {
            int temp=nums[0];
            if(temp>=nums[i])
            {
                int s=nums[i];
                if(s>=nums[i++])
                {
                    return true;
                }      
            }
            else if(temp<=nums[i])
            {
                int s=nums[i];
                if(s<=nums[i++])
                {
                    return true;
                }    
                return true;
            }
        }
        return false;
    }
};
```

#### Modifications:
```cpp
class Solution {
public:
    bool isMonotonic(vector<int>& nums) {
        bool inc=true;
        bool dec=true;

        for (int i=1;i<(nums.size());i++)
        {
            if(nums[i]>nums[i-1])
            {
                dec=false;
            }
            if (nums[i]<nums[i-1])
            {
                inc=false;
            }
        }
        return (inc || dec);
    }
};
```
It seems like there's a logical issue in your code. The approach you've taken doesn't cover all cases properly. You're returning true when encountering certain conditions, which might not be correct for determining if the array is monotonic. Also, the usage of i++ inside the loop might cause unexpected behavior. And also problem lies in the loop condition and how you are accessing array elements. Specifically, the condition nums[i] > nums[i - 1] and nums[i] < nums[i - 1] can lead to an out-of-bounds access.

#### Complexity:
- Time Complexity: O(n)
- Space Complexity: O(1)

#### Challenges Faced:
- Ensuring correct handling of edge cases.
- Optimizing code for simplicity.
- logical issues
- Out of bounds 

#### Learnings:
- Recognizing patterns in the problem to simplify the solution.
- Efficient use of variables.

#### Use Cases:
- Verifying if an array is monotonic.

--------------------

### 3. Problem: Roman to Integer

[Leetcode](https://leetcode.com/problems/monotonic-array/?envType=study-plan-v2&envId=programming-skills)

#### Original Code:
```cpp
class Solution {
public:
    int romanToInt(string s) {
        unordered_map<char , int>m;
        m['I']=1;
        m['V']=5;
        m['X']=10;
        m['L']=50;
        m['C']=100;
        m['D']=500;
        m['M']=1000;
        int ans=0;
        for(int i=0;i<s.size();i++)
        {
            if(m[s[i]]<m[s[i+1]])
            {
                ans-=m[s[i]];
            }
            else
            ans+=m[s[i]];
        }
        return ans;
    }
};
```

#### Modifications:
The original code is correct. This problem is efficiently solved using a map to store the values of Roman numerals. However, you can experiment with other approaches, such as using a switch statement.

#### Complexity:
- Time Complexity: O(n)
- Space Complexity: O(1) (assuming the map is constant in size)

#### Challenges Faced:
- Decoding the Roman numerals correctly.
- Handling the subtraction cases.

#### Learnings:
- Efficiently using a map for constant lookup time.
- Handling special cases in the algorithm.

#### Use Cases:
- Converting Roman numerals to integers.

-------------------

### 4. Problem: Length of Last Word

[Leetcode](https://leetcode.com/problems/length-of-last-word/?envType=study-plan-v2&envId=programming-skills)

#### Original Code:
```cpp
class Solution {
public:
    int lengthOfLastWord(string s) {
        int l=s.len();
        inr count=0;
        for(int i=l;i>0;i--)
        {
            if(s[i]==' ')
            {
                int j=s[i];
                while(j>=l)
                {
                    count++;
                }
            }
        }
        return count;
    }
};
```

#### Modifications:
```cpp
class Solution {
public:
    int lengthOfLastWord(string s) {
        int l=s.length();
        int count=0;
        int i=l-1;
        while(i>=0 && s[i]==' ')
        {
            i--;
        }
        while(i>=0 && s[i]!=' ')
        {
        count++;
        i--;
        }
        return count;
    }
};

```
* code has a few issues. Let's correct them:

- The loop condition should be i >= 0 instead of i > 0 to avoid going out of bounds.
- The comparison if (s[i] == ' ') should be if (s[i - 1] == ' ') because you want to check the character before the current position i.
- The variable j is assigned the ASCII value of the space character (' '), and the loop condition while (j >= l) is not correct. Instead, you should use while (j < l) to iterate through the characters in the string.

#### Complexity:
- Time Complexity: O(n)
- Space Complexity: O(1)

#### Challenges Faced:
- Correctly handling edge cases.
- Optimizing the code

#### Learnings:
The `for` loop is not used in this specific implementation because the problem requires finding the length of the last word in the string, and the conditions for counting the length are more naturally expressed using a `while` loop.

Here's the reasoning:

1. **Finding the Index of the Last Non-Space Character:** We use a `while` loop to iterate from the end of the string towards the beginning until we find the last non-space character. This is more intuitive with a `while` loop because we don't have a fixed number of iterations; we are moving backward until we reach a condition.

    ```cpp
    while (i >= 0 && s[i] == ' ') {
        i--;
    }
    ```

2. **Counting the Length of the Last Word:** After finding the index of the last non-space character, we again use a `while` loop to iterate backward and count the length of the last word. We continue until we encounter a space or reach the beginning of the string.

    ```cpp
    while (i >= 0 && s[i] != ' ') {
        count++;
        i--;
    }
    ```

Using `while` loops in this scenario allows for a more natural expression of the conditions, as we are not iterating through a fixed range. The conditions are based on the content of the string and the position of non-space characters.
-------------
### 5. To Lower Case

[Leetcode](https://leetcode.com/problems/to-lower-case/?envType=study-plan-v2&envId=programming-skills)

Original code:
```cpp
class Solution {
public:
    string toLowerCase(string s) {
        int l=s.length();
        for(int i=0;i<l;i++)
        {
            if (s[i]=='A'-256)
            {
                s[i]= 'a'-256;
            }
        }
    }
    return s;
};
```
#### Modifications:
```cpp
class Solution {
public:
    string toLowerCase(string s) {
        int l=s.length();
        for(int i=0;i<l;i++)
        {
            if (s[i]>='A' && s[i]<='Z')
            {
                s[i]= s[i]-'A'+'a';
            }
        }
            return s;
    }
};
//on line ans : transform(s.begin(), s.end(), s.begin(), ::tolower);
```
It looks like there's a small issue with your code. Instead of comparing the character directly with 'A' - 256, you should compare it with the actual uppercase letters. Also, you need to make sure to handle all uppercase letters, not just 'A'. Here's the corrected version of your code.

#### Complexity:
- Time Complexity: O(n)
- Space Complexity: O(1)

#### Challenges Faced:
- Ensuring correct handling of edge cases.
- Optimizing code for simplicity.
- logical issues

#### Learnings:
-transform STL

-------------------
## JS:
[link](https://leetcode.com/problems/counter/solutions/3491300/day2-o-1-understanding-closure-in-easy-way-and-its-practical-uses/?envType=study-plan-v2&envId=30-days-of-javascript)
### When, Where, What, and How to use closure!!!
* First of all closure is not something you create it's something that the language has created for itself for appropriate development and we need to crack this code that how the language uses it.

* "To be honest, a good developer's greatest fear is discovering that something is working but not knowing how it works."

### What is Closure ?
* A closure is created when a function is defined inside another function, and the inner function references variables in the outer function's scope. When the inner function is returned from the outer function, it retains a reference to the outer function's scope, and can continue to access those variables even after the outer function has finished executing. Vice-Versa is not true!!
* In simple terms a closure can "remember" values from its outer function's scope and use them later, even if the outer function has returned and those values would normally be out of scope.

### When to use closure concept ?
* First let's summarize the definition as usually the definition gives the answer for when to use..

* From definition you can see that it's used for retrival of values from outer parent function so we can understand that closure can be used for retrival of dead values which have become out of scope. also we can comprehend that it can used for privating some varibles or function.

* Thus closures are useful for creating private variables and functions, implementing partial function application, and preserving state in asynchronous code.

* While writing the code whenever there is a need for these types of thing try to incorporate this closure concept i.e. In a programmer languge it's called lexical environment

### Where and How to use closure concept ?
```JavaScript
///Private variables and functions:
const makeCounter = () => {
  let count = 0;
  
  return () => {
    count++;
    console.log(count);
  }
}

let counter = makeCounter();
counter(); // logs 1
counter(); // logs 2
counter(); // logs 3
```
- In this example, makeCounter is an arrow function that returns another arrow function. The returned function increments a count variable each time it is called, and logs the new value of count to the console.
- When makeCounter is called, it creates a new scope with a count variable initialized to 0. It then returns a new arrow function that "closes over" this scope and increments the count variable each time it is called.
- When we assign the returned arrow function to the counter variable, we create a closure that retains a reference to the count variable.
- Each time we call counter(), it increments the count variable and logs the new value to the console, because it is still "closing over" the original count variable in the outer function's scope.
- Thus because the count variable is not exposed outside of the returned object, it is effectively a private variable that can only be accessed or modified through the makeCounter() methods.

#### Partial function:
- I was introduced to this concept name during development phase but was shocked that unknowingly I have used it many times. I'm sure that you all also must have use this:
```JavaScript
function add(x) {
  return function(y) {
    return x + y;
  }
}

let add5 = add(5);
console.log(add5(3)); // 8
```
- In this example, the add() function returns another function that takes a single argument and returns the sum of that argument and the x value from the outer function's scope.
- This allows us to "partially apply" the add() function by passing in an x value and getting back a new function that always adds that value to its argument.
- Thuse we can then use the new function like any other function, passing in different y values as needed.
For preserving states in asynchronous code:
The below snippet is from my personal project:)
```JavaScript
const animate = (element, from, to, duration) => {
  let start = performance.now();
  
  const update = () => {
    let time = performance.now() - start;
    let progress = time / duration;
    let value = from + (to - from) * progress;
    
    element.style.left = value + 'px';
    
    if (progress < 1) {
      requestAnimationFrame(update);
    }
  }
  
  requestAnimationFrame(update);
}

let element = document.getElementById('my-element');
animate(element, 0, 100, 1000);
```
- In this example, the animate() function creates a closure over the start variable, which is used to calculate the elapsed time since the animation started.
- The update() function also "closes over" the element, from, to, and duration arguments, so that it can use them to update the element's position over time.
- Thus by creating a closure over these values, we can preserve their state between animation frames, even though the update() function is called asynchronously by requestAnimationFrame().

#### Answer to todays(#2) JS challenge:
```JS
var createCounter = function(n) {
    return ()=> n++
};
```
Time and Space : O(1).


Then I done some Cogita_read will post it new post.[link]()