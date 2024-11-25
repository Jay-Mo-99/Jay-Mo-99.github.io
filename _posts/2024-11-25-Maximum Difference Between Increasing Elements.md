---
title: "⚡Maximum Difference Between Increasing Elements"
layout: single
date: 2024-11-25
categories: ⚡LeetCode
tags: 
  - Array
  - JavaScript
excerpt: "Solutions for the 'Maximum Difference Between Increasing Elements' problem using JavaScript and array."
author_profile: true
read_time: true
share: true
related: true
toc: true
---

# #2016. Maximum Difference Between Increasing Elements

- **Difficulty**: Easy
- **Company**: Cisco
- **Optimization**: Yes
- **Review**: November 25, 2024
- **Select**: Array
- **Solve**: No
- **Tried**: 2

# Understanding the Problem

- nums[j] - nums[i] = The maximum difference
- 0≤i<j<n

# My Answer

```jsx
/**
 * @param {number[]} nums
 * @return {number}
 */
var maximumDifference = function(nums) {

    const minVal = Math.min(...nums);
    const maxVal = Math.max(...nums);

    let minIndex = nums.indexOf(minVal);
    let maxIndex = nums.indexOf(maxVal);

    let cutArr = nums.slice(index);
    let maxCutVal = Math.max(...cutArr);
        //console.log(maxCutVal);
    if(maxCutVal<=minVal){
        return -1;
    }
    // let maxCutIndex = nums.indexOf(maxCutVal);
    // console.log(maxCutIndex);
    return (maxCutVal-cutArr[0]);

};
```

- The reason of Wrong
    - We can’t confirm that nums[i] is the minimum number of the array.
    - For example, [87,68,91,86,58,63,43,98,6,40], nums[j](98) minus nums[i](43) is the maximum difference ].

# Reflection

- [x]  Exploring various solutions and clearly communicating them
- [ ]  Stating the runtime and space complexity (the pros and cons) of each solution)
- [ ]  Translating ideas into code
- [x]  Debugging your code

# Best Answer

```jsx
/**
 * @param {number} n
 * @return {string[]}
 */

var maximumDifference = function(nums) {
   var min=Infinity
   var diff=-1
   for(i=0;i<nums.length;i++){
       min = Math.min(min,nums[i])//Update the min variable 
       diff=Math.max(diff,nums[i]-min)//Update the diff variable 
   }
   return diff===0 ? -1 : diff 
};

//nums=[9,8,7,6]
// (min,diff)
//(9,0)
//(8,0)
//(7,0)
//(6,0)
//i<j && num[j] - num[i] = The maximum -> In that case, there is no nums[j] 
//-1 return

```

- Description
    - The algorithm updates the `min` and `diff` variables for each element in the array without relying on fixed criteria like `min` or `max`.
        1. Use a loop to iterate through the array `nums`.
        2. For each `nums[i]`, compare it with the current `min` variable. Update `min` with the smallest value found so far.
        3. Subtract the current `min` from `nums[i]`. Then, compare the result with the current `diff` variable and update `diff` with the maximum value between them.
- Main Point
    - If the condition `i ≤ j && nums[j] - nums[i] = The maximum` cannot be satisfied, the value of `diff` will **always be 0**.
        - **Reason:** In cases like `[9, 8, 7, 6]` or `[5, 5, 5]`, where there is no valid `nums[j]` such that `nums[j] > nums[i]`:
            - The `min` variable will always track `nums[i]` at each step.
            - As a result, `nums[i] - min` will always equal `0`, and `diff` will remain `0`.
        - Therefore, the condition `diff === 0` indicates that the constraints were not met, and the algorithm will return `-1`. Otherwise, it will return the value of `diff`.

- Time: O(n)
    - The loop depends on the length of the nums(n).
- Space: O(1)
    - The variables min and diff don’t depend on the length of the nums. They are constant variables.
