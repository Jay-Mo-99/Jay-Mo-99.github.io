---
title: "⚡Container With Most Water"
layout: single
date: 2025-01-14
categories: ⚡LeetCode
tags: 
  - Array
  - Two Pointers
  - Python
excerpt: "Solutions for the 'Container With Most Water' problem using Python and Two Pointers."
author_profile: true
read_time: true
share: true
related: true
toc: true
---
# #11. Container With Most Water

- **Difficulty**: Medium
- **Company**: LeetCode75
- **Review**: January 14, 2025
- **Select**: Array, Stack, Two Pointers
- **Solved**: Yes
- **Tried**: 2

# My Solution: Brute Force - Unsolved

```python
class Solution(object):
    def maxArea(self, height):
        """
        :type height: List[int]
        :rtype: int
        """
        curr = 0
        for i in range(len(height)):
            for j in range(i+1,len(height)):
                curr = max(curr,((j+1)-(i+1))*min(height[i],height[j]))
        return curr
```

- Description:
    - Tried to calculate all possible cases using a nested loop.
    - Issue: This approach resulted in a time limit exceeded error for large inputs.
- Time: $O(n^2)$
- Space: O(1)

# Reflection

- [x]  Exploring various solutions and clearly communicating them
- [x]  Stating the runtime and space complexity (the pros and cons) of each solution)
- [x]  Translating ideas into code
- [ ]  Debugging your code

# Best Answer

## Using Two Pointers

```python
class Solution(object):
    def maxArea(self, height):
        """
        :type height: List[int]
        :rtype: int
        """
        max_area = 0 #Saving for answer
        s,e=0,len(height)-1 #Assign the first index and last index
        while s<e:
            area = (e-s) * min(height[s],height[e]) #Current area using e,s
            max_area = max(area, max_area) #Re-assing the max_area comparing with area
            if height[s]< height[e]:
                s+=1
            else:
                e -=1
        return max_area
```

- Complexity
    - $N$ : The number of elements in the `height` list.
- Time: $O(N)$
    - A single `while` loop ensures each pointer moves exactly once.
- Space: O(1)
    - No additional memory is used beyond a few variables.
