---
title: "⚡ Product of Array Except Self"
layout: single
date: 2024-10-21
categories: ⚡LeetCode
tags: 
  - Array
  - Prefix Sum
  - JavaScript
excerpt: "Solutions for the 'Product of Array Except Self' problem using JavaScript and array."
author_profile: true
read_time: true
share: true
related: true
toc: true
---

# #238. Product of Array Except Self

- **Difficulty**: Medium
- **Number**: 1  
- **Optimization**: Yes
- **Review**: October 21, 2024  
- **Select**: Array, Prefix Sum
- **Solve**: Yes

# My Solution: Wrong

```c
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var productExceptSelf = function(nums) {
    let result = []; //Push the result of multiple calc
    let cal=1;//Answer of Multiple calculation 
    let second;
    //Approach each element of the nums array
    for(let i=0;i<nums.length;i++){
        cal *= nums[i];
    }
    //We already multiply all element of nums input 
    for(let j=0;j<nums.length;j++){
        //Divide nums[j] to cal variable
        //Push the result of the division 
        second = cal/nums[j]; 
        result.push(second);                      
    }
    console.log(result);

};
```

- Time:
- Space:
- Reason for the wrong answer
    - If the input array has a 0 element, the cal’s result is always 0.
    - To solve the problem, We have to multiply all elements except specific elements. So Multiplying all elements and dividing specific elements is not a good approach because if the input element contains 0 elements, the Multiplying result always be 0.

# Reflection

- [ ]  Exploring various solutions and clearly communicating them
- [x]  Stating the runtime and space complexity (the pros and cons) of each solution)
- [ ]  Translating ideas into code
- [x]  Debugging your code

# Best Solution

1. Using 3 loops: Left Multiply, Right Multiply and Final Multiply calculation.

```c
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var productExceptSelf = function(nums) {
    let leftMulti = [];
    let tempLeft = 1;
    let tempRight = 1;
    let rightMulti = [];
    let result = [];

    for(let i = 0;i<nums.length;i++){
        leftMulti.push(tempLeft);
        tempLeft = tempLeft * nums[i];
    }

    for(let j = nums.length - 1;j>=0;j--){
        rightMulti[j] = tempRight;
        tempRight = tempRight * nums[j];
    }

    for(let k = 0;k<nums.length;k++){
        let temp = leftMulti[k]*rightMulti[k];
        result.push(temp);
    }
    return result;

};
```

1. Recycle the variable and array → Memory Beats 97.05%

```c
var productExceptSelf = function(nums) {
    var output = [];
    var leftMult = 1;
    var rightMult = 1;
    for (var i=nums.length - 1; i >= 0; i--) {
        output[i] = rightMult;
        rightMult *= nums[i];
    }
    for (var j=0; j < nums.length; j++) {
        output[j] *= leftMult;
        leftMult *= nums[j];
    }
    return output;
};
```

- Time: O(n)
    - Each for loop depends on the number of elements of the Input array
- Space: O(n)
    - The number of elements in Each array(leftMulti, rightMulti, result) depends on the Input array.

# Note

- Check the condition of the problem.
- Recycle the variable and array for saving the memory.
