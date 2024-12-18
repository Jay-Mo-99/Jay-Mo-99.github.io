---
title: "⚡Climbing Stairs"
layout: single
date: 2024-12-17
categories: ⚡LeetCode
tags: 
  - Dynamic Programming
  - Python
excerpt: "Solutions for the 'Climbing Stairs' problem using Python."
author_profile: true
read_time: true
share: true
related: true
toc: true
---


# #230. Climbing Stairs

- **Difficulty**: Easy
- **Company**: LeetCode75
- **Language**: Python
- **Optimization**: Yes
- **Review**: December 17, 2024
- **Select**: Dynamic Programming
- **Solved**: Yes
- **Tried**: 1

# My Answer and Best Solution

```python
class Solution(object):
    def climbStairs(self, n):
        """
        :type n: int
        :rtype: int
        """
        a,b = 1,2 #F(0) = 1, F(1) =2
        for i in range(1,n):
            a,b = b, a+b #Update a and b each iteration
            #Fn = Fn-1 + Fn-2

        return a
        

```

- Time: O(n)
    - for loop depends on the length of the n → O(n)
- Space: O(1)
    - variable a and b use a specific memory, constant → O(1)
- **Description**
    - The number of ways to reach the **N-th stair** = The number of ways to reach the N−1-th stair + The number of ways to reach the N−2-th stair.
- **Example:**
    - **Number of ways to reach the 1st stair:** 1 → (1)
    - **Number of ways to reach the 2nd stair:** 2 → (1,1), (2)
    - **Number of ways to reach the 3rd stair:** 3 = 1+2 → (1,1,1),(2,1), (1,2)
    - **Number of ways to reach the 4th stair:** 5 = 3+2 → [1,1,1,1], [1,2,1], [2,1,1], [1,1,2], [2,2]
    - The sequence continues as: **1, 2, 3, 5, 8, …**

# Reflection

- [x]  Exploring various solutions and clearly communicating them
- [x]  Stating the runtime and space complexity (the pros and cons) of each solution)
- [ ]  Translating ideas into code
- [x]  Debugging your code
