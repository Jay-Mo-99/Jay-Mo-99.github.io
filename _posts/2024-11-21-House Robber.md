---
title: "⚡House Robber"
layout: single
date: 2024-11-21
categories: ⚡LeetCode
tags: 
  - Array
  - Dynamic Programming
  - JavaScript
excerpt: "Solutions for the 'House Robber' problem using JavaScript."
author_profile: true
read_time: true
share: true
related: true
toc: true
---

# #198. House Robber

- **Difficulty**: Medium
- **Company**: Cisco
- **Optimization**: Yes
- **Review**: November 21, 2024
- **Select**: Array, Dynamic Programming
- **Solve**: No
- **Tried**: 2

# My Answer: Wrong

```jsx
/**
 * @param {number[]} nums
 * @return {number}
 */
var rob = function(nums) {
    let evenSum = 0;
    let oddSum = 0;
    let maxSum =0;
    let restSum=0;
    for(let i =0;i<nums.length;i++){

        if(i%2===0||i===0){
            evenSum += nums[i]
        }else{
            oddSum += nums[i]
        }

        let maxNum = Math.max(...nums);
        let maxIndex = nums.indexOf(maxNum);
        if(i-maxIndex!==1&&i-maxIndex!==-1){
            restSum += nums[i]
        }else{
            maxSum += nums[i]
        }
    }

    return Math.max(maxSum, restSum,evenSum,oddSum);

};
```

- Time: O(n)
- Space: O(n)
- Opinion:
    - This code selects elements with a one-house gap
    - However, it fails to handle cases where elements with a two-house gap need to be selected.
        - For example, [2,1,1,2], where the optimal solution is to sum the first and last `2`
    - Instead of simply comparing individual `nums` elements or groups, the solution requires a **dynamic object or structure** that saves the maximum sum at each step

# Reflection

- [x]  Exploring various solutions and clearly communicating them
- [ ]  Stating the runtime and space complexity (the pros and cons) of each solution)
- [ ]  Translating ideas into code
- [ ]  Debugging your code

# Best Answer

```jsx

var rob = function(nums) {
    const dp = [...Array(nums.length)].fill(0);
    dp[0] = nums[0];
    dp[1] = Math.max(nums[0], nums[1]);
    
    for (let i=2; i<nums.length; i++) {
        dp[i] = Math.max((dp[i-2] + nums[i]), dp[i-1]);
    }
    return dp[nums.length-1];
};
```

**Description:**

1. `dp` is an array that stores the maximum sum that can be obtained by robbing houses up to the `i`th house, without robbing adjacent houses.
2. `dp[0]` represents the maximum sum when there is only the first house, so `dp[0] = nums[0]`.
3. `dp[1]` represents the maximum sum when considering only the first two houses, so `dp[1] = Math.max(nums[0], nums[1])`.
4. From `dp[2]` onwards, when considering up to the `i`th house, there are two cases:
    1. If the thief robs house `i`: `dp[i-2] + nums[i]`.
    2. If the thief does not rob house `i`: `dp[i-1]`.
    3. `dp[i] = Math.max(dp[i-2] + nums[i], dp[i-1])`.
5. Starting from `dp[3]`, the same logic applies: `dp[3] = Math.max(dp[1] + nums[3], dp[2])`.
    1. In general, `dp[i] = Math.max(dp[i-2] + nums[i], dp[i-1])`.
6. The last value in the `dp` array (`dp[nums.length-1]`) represents the maximum sum that can be obtained for the entire array.
- Time: O(n)
    - Creation of the `dp`/for loop  → Depends on the size of nums, resulting in O(n) time complexity
- Space: O(n)
    - For creating the dp → Depends on the size of nums, resulting in O(n)
    - Other variable is constant, so O(1)

## Optimization of Space

```jsx
var rob = function(nums) {
    if (nums.length === 1) return nums[0];

    let prev2 = nums[0]; //dp[0]
    let prev1 = Math.max(nums[0], nums[1]);//dp[1]
    
    for (let i = 2; i < nums.length; i++) {
        let current = Math.max(prev2 + nums[i], prev1);//dp[i] = Math.max((dp[i-2] + nums[i]), dp[i-1]);
        prev2 = prev1;//prev2 <- dp[i-2]
        prev1 = current;//prev1 <- dp[i-1]
    }
    return prev1;
};
```

- Description
    - No `dp` array depends on the length of `nums`. Instead, the solution uses two variables (`prev2` and `prev1`) to store intermediate results.
    - `prev2` acts as `dp[i-2]` and `prev1` acts as `dp[i-1]`. Since these variables are independent of the length of `nums`, the space complexity is O(1).
