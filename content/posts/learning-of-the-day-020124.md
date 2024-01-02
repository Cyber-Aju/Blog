+++
title= "Day 02/01"
date= '2024-01-02'
draft= 'false'
tags= ["learning", "cpp", "Frequency Counting"]
categories= ["Days_Of_Cpp"]
+++

**Step 1: Frequency Counting**
   - An array `mp` of size 201 is created to store the frequency of each element in `nums`. This array's size is chosen based on the problem constraints.
   - Iterate through the array `nums` and update the frequency of each element in `mp`.
   - Keep track of the maximum frequency encountered (stored in `maxrow`).

**Step 2: Initialize 2D Vector**
   - Initialize a 2D vector `ans` with `maxrow` number of rows. This is based on the maximum frequency encountered.

**Step 3: Distribute Elements in Rows**
   - Iterate through the array `nums` again.
   - Distribute the elements in the rows of `ans` based on their frequencies. Decrease the frequency after placing the element in the row.

**Step 4: Return the Resulting 2D Array**
   - Return the resulting 2D array `ans`.

Now, let's analyze the code:

```cpp
class Solution {
public:
    vector<vector<int>> findMatrix(vector<int>& nums) {
        std::ios::sync_with_stdio(false);
        cin.tie(NULL);
        int n = nums.size(), maxrow = 0;
        array<int, 201> mp = {0};

        // Step 1: Frequency Counting
        for (int i = 0; i < n; i++) {
            mp[nums[i]]++;
            maxrow = max(maxrow, mp[nums[i]]);
        }

        // Step 2: Initialize 2D Vector
        vector<vector<int>> ans(maxrow);

        // Step 3: Distribute Elements in Rows
        for (int i = 0; i < n; i++) {
            ans[mp[nums[i]] - 1].push_back(nums[i]);
            mp[nums[i]]--;
        }

        // Step 4: Return the Resulting 2D Array
        return ans;
    }
};
```

**Time Complexity Analysis:**
   - The time complexity is O(N), where N is the length of the input array `nums`. The code iterates through the array twice, and each iteration takes linear time.

**Space Complexity Analysis:**
   - The space complexity is O(N), where N is the length of the input array `nums`. The space is used to store the frequency array `mp` and the resulting 2D array `ans`. The maximum size of `mp` is constant (201), so it doesn't contribute significantly to the overall space complexity.

**Pattern Used:**
   - The solution uses a frequency counting pattern to keep track of the occurrences of each element and then distributes them in rows based on their frequencies. The goal is to minimize the number of rows while ensuring that each row contains distinct integers.

This pattern is particularly useful when you need to organize elements based on their frequencies or occurrences in the input array.