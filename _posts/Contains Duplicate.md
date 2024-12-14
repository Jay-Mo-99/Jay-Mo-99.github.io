---
title: "⚡Contains Duplicate"
layout: single
date: 2024-12-12
categories: ⚡LeetCode
tags: 
  - Array
  - Python
excerpt: "Solutions for the 'Contains Duplicate' problem using Python and array."
author_profile: true
read_time: true
share: true
related: true
toc: true
---

# #217. Contains Duplicate

- **Difficulty**: Easy
- **Company**: LeetCode75
- **Optimization**: Yes
- **Review**: December 12, 2024
- **Select**: Array
- **Solved**: Yes
- **Tried**:1

# My Answer

```python

class Solution(object):
    def isPalindrome(self, s):
        """
        :type s: str
        :rtype: bool
        """

        #removes all non alpha numeric(only accept alphabet and number) items from the s
        temp = lower(s)
        temp = " ".join(re.split("[^a-zA-Z0-9]*",temp)).replace(" ","")
        #Compare with temp and reverse temp 
        #If they are same, it is palindrome
        return temp == temp[::-1]

```

- Time: O(n)
    - `temp` depends on the characters of `s` string (n) → O(n)
    - `temp[::-1]` reverse the `temp.`In this progress, it checks and copies each character of string s. It depends on n → O(n)
- Space: O(n)
    - `temp` created depending on the number of characters in string s → O(n)
- Description
    1. Convert parameter s to lower classes (lower(s))
    2. Delete non-alphanumeric characters and space
    3. If the temp and temp[::-1](reverse ver.) are same, they are palindrome. 
    

# Reflection

- [x]  Exploring various solutions and clearly communicating them
- [x]  Stating the runtime and space complexity (the pros and cons) of each solution)
- [x]  Translating ideas into code
- [ ]  Debugging your code

# Best Answer

## 1. Short version

```python
﻿class Solution(object):
    def containsDuplicate(self, nums):
        """
        :type nums: List[int]
        :rtype: bool
        """
       return len(list(set(nums))) != len(nums)
 
```

- Time: O(n)
    - `set(nums)` traverses all characters of the `s`  → `O(n)`
    - `len(nums)` bring the stored information in memory → O(1)
        - The length of the list `nums` is stored as a property of the list object in Python. Accessing this stored value takes constant time
- Space: O(n)
    - When converting data types like `set()` or `list()`, all elements in `s` are traversed, creating a new data structure. It requires additional memory proportional to the number of elements in `s` → O(n)

# Note

- Converting data types such as `list()`, `set()`, or `dict()` requires memory proportional to the size of the original data.
