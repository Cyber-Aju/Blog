+++
title= "Learnings of the Day 11/12"
date= '2023-12-11'
draft= 'false'
tags= ["learning", "cpp", "problem solving", "Leetcode"]
categories= ["leetcode" , "Days_Of_Cpp"]
+++

## Problem solving's 

-----

### 1. Repeated Substring Pattern

[leetcode](https://leetcode.com/problems/repeated-substring-pattern/?envType=study-plan-v2&envId=programming-skills)

#### Code:
```cpp
bool repeatedSubstringPattern(char s[]){
    char b[50];
    for(int i=0;i<50;i++)
    {
        b[i]=0;
    }
    for(int i=0;s[i];i++)
    {
        int k=s[i]-'a';
        b[k]++;
    }
    for(int i=0;i<50;i++)
    {
        if(b[i]!=0)
        {
          int a=b[1];
          while(b[i]==a)
          {
              return true;
          } 
        }
    }
    return false;
}
```

#### Modifications:
Then corrected version of code in a previous response.
```cpp
bool repeatedSubstringPattern(char s[]) {
    int len = strlen(s);
    
    for (int i = 1; i <= len / 2; i++) {
        if (len % i == 0) {
            int numRepeats = len / i;
            bool isRepeated = true;

            for (int j = i; j < len; j++) {
                if (s[j] != s[j - i]) {
                    isRepeated = false;
                    break;
                }
            }

            if (isRepeated) {
                return true;
            }
        }
    }
    
    return false;
}
```

#### Challenges Faced:
- The initial code had logic issues, particularly in the loop conditions and handling repeated substrings.

#### Learnings:
- Understanding the problem requirements and constraints is crucial for correct implementation.
- Correctly using loops and conditions is essential for solving substring-related problems.

-----

### 2. Move Zeros

[Leetcode](https://leetcode.com/problems/move-zeroes/?envType=study-plan-v2&envId=programming-skills)

#### Your Code:
```cpp
class Solution {
public:
    void moveZeroes(vector<int>& nums) {
        for(int i=0;i<nums;i++)
        {
            if(nums[i]==0)
            {
                int z=num[i];
                nums[i]=nums[i+1];
                nums[i+1]=z;
            }
        }

    }
};
```

#### Modifications:
A corrected version of code in a previous response.
```cpp
class Solution {
public:
    void moveZeroes(vector<int>& nums) {
        int nz=0;
        int n=nums.size();
        for(int i=0;i<n;i++)
        {
            if(nums[i]!=0)
            {
                nums[nz]=nums[i];
                nz++;
            }
        }
        for(int i=nz;i<n;i++)
        {
            nums[i]=0;
        }

    }
};
```

#### Challenges Faced:
- The initial code had a loop condition issue, and the logic was not correctly moving zeros to the end.

#### Learnings:
- Proper loop conditions are vital for avoiding array out-of-bounds issues.
- Efficiently handling zero movements requires careful consideration of array indices.

-----

### 3. Plus One

[Leetcode](https://leetcode.com/problems/plus-one/?envType=study-plan-v2&envId=programming-skills)

#### Your Code:
```cpp
int* plusOne(int* digits, int digitsSize, int* returnSize){
        long long sum=0;
        for(int i=0;i<digitsSize;i++)
        {
            sum=(sum*10LL)+digits[i];
        }
        sum+=1;
        long long temp = sum;
        int count=0;
        while(temp>0) {
        temp/=10;
        count++;
        }
        int res[count];
        for (int i=count-1;i>=0;i--) {
        res[i] = sum % 10;
        sum /= 10;
    }
    return res;
}
```

#### Modifications:
A corrected version of code in a previous response.
```cpp
class Solution {
public:
    vector<int> plusOne(vector<int>& digits) {
        int n=digits.size();
        vector<int>absk;
        for(int x:digits)
        {
            absk.push_back(x);
        }
        if(digits[n-1]!=9)
        {
            absk[n-1]++;
            return absk;
        }
        int i=n-1;
        for(;i>=0;i--)
        {
            if(digits[i]!=9)
            {
                break;
            }
        }
        if(i==-1)
        {
            absk[0]=1;
            for(int i=1;i<n;i++)
            {
                absk[i]=0;
            }
            absk.push_back(0);
            return absk;
        }
        else
        {
            absk[i]++;
            for(int k=i+1;k<n;k++)
            {
                absk[k]=0;
            }
        }
        return absk;
    }
};
```

#### Challenges Faced:
- The initial code needed to correctly handle the addition, carry propagation, and edge cases.

#### Learnings:
- Handling edge cases and efficiently propagating carries are crucial skills in numerical algorithm implementation.
- Understanding the structure of the problem is key to providing an elegant solution.

-----

### 4. Sign of the Product of an Array

[Leetcode](https://leetcode.com/problems/sign-of-the-product-of-an-array/?envType=study-plan-v2&envId=programming-skills)

#### Your Code:
```cpp
class Solution {
public:
    int arraySign(vector<int>& nums) {
        int product=1;
        for(int i=0;i<nums.size();i++)
        {
            product*=(nums[i])*(nums[i+1]);
        }
    int signFunc(product)
    {
        if(product<0)
        {
            return -1;
        }
        else if(product>0)
        {
            return 1;
        }
        else if(product==0)
        {
            return 0;
        }
    }
    }
};
```

#### Modifications:
A corrected version of code in a previous response.
```cpp
#include <vector>

class Solution {
public:
    int arraySign(std::vector<int>& nums) {
        int sign = 1;  // Initialize sign to positive
        for (int i = 0; i < nums.size(); i++) {
            if (nums[i] == 0) {
                return 0;  // If any element is 0, the product will be 0
            } else if (nums[i] < 0) {
                sign = -sign;  // Toggle sign for each negative number
            }
        }
        return sign;
    }
};
```

#### Challenges Faced:
- The initial code had an issue with overflow due to large product values.

#### Learnings:
- Understanding the limitations of data types and handling potential overflows is crucial in numerical computations.
- Efficiently toggling signs based on conditions simplifies code and reduces potential errors.

------

In navigating the solutions to the array manipulation challenges, we unveil the critical aspects that define proficient problem-solving in software development. Take, for instance, the Repeated Substring Pattern problem, where a meticulous understanding of string manipulation and careful implementation of loop conditions are paramount. The code intricacies teach us the value of dissecting problem requirements and employing precise logic, crucial skills in any developer's toolkit.

Moving on to the Move Zeros challenge, we delve into the significance of efficient array manipulation. Here, the correction involved a keen eye on loop conditions and index management, reinforcing the necessity of properly handling edge cases to avoid runtime errors. These skills are foundational, applicable not just in algorithmic problem-solving but also in optimizing real-world applications where data organization and preprocessing are routine tasks.

The Plus One problem provides a deeper insight into numerical algorithms and the importance of correctly handling arithmetic operations on arrays. With considerations for carry propagation and edge cases, the solution reflects the broader theme of understanding the intricacies of numerical computations, applicable in fields ranging from cryptography to simulations.

Finally, in the Sign of the Product of an Array challenge, the correction addressed potential overflow issues, highlighting the significance of understanding data types and efficiently toggling signs based on conditions. This exercise serves as a reminder of the broader lessons in numerical precision and the critical nature of managing computational complexities in various mathematical scenarios.

These exercises collectively underscore the value of clear problem understanding, precise logic implementation, and efficient handling of edge cases. As developers, these skills are not only essential in algorithmic problem-solving but also translate into building robust, optimized, and error-resistant software solutions across diverse domains. Regular practice in such problem-solving scenarios is not just an academic exercise; it's a cornerstone of continuous improvement for any software developer.

[github link : >>](https://github.com/Cyber-Aju/100_Days_of_Cpp/tree/main/Day%2028)