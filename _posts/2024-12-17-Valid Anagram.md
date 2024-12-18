---
title: "⚡Valid Anagram"
layout: single
date: 2024-12-17
categories: ⚡LeetCode
tags: 
  - Sorting
  - String
  - Python
excerpt: "Solutions for the 'Valid Anagram' problem using Python and sorting."
author_profile: true
read_time: true
share: true
related: true
toc: true
---
# #242. Valid Anagram

- **Difficulty**: Easy
- **Company**: LeetCode75
- **Language**: Python
- **Optimization**: Yes
- **Review**: December 17, 2024
- **Select**: Hash Table, Sorting, String
- **Solved**: Yes
- **Tried**:1

# My Answer

```python
class Solution(object):
    def isAnagram(self, s, t):
        """
        :type s: str
        :type t: str
        :rtype: bool
        """
        s = list(s) #Convert string to list
        t = list(t)
        s.sort()    #Sort the list 
        t.sort()

        return s == t #If the s and t are same, return true(anagram)
        

```

- Time: NO(log N)
    - In `Python`,  `sort()`uses the Timsort method to divide and merge the object → NO(log N)
- Space: O(n)
    - list s and t depends on the length of the parameter s and t. → O(N)

# Reflection

- [x]  Exploring various solutions and clearly communicating them
- [x]  Stating the runtime and space complexity (the pros and cons) of each solution)
- [x]  Translating ideas into code
- [ ]  Debugging your code

# Best Answer

## 1. Fast Runtime

```python
class Solution(object):
    def isAnagram(self, s, t):
        # In case of different length of thpse two strings...
        if len(s) != len(t):
            return False
        for idx in set(s):
            # Compare s.count(l) and t.count(l) for every index i from 0 to 26...
            # If they are different, return false...
            if s.count(idx) != t.count(idx):
                return False
        return True     # Otherwise, return true...
```

- Time: O(n x k): n is the length of the s, k is the length of the set s
    - Compare the length of the string  s and t using `len()` → O(1)
    - Using set to delete duplicate using `set()`→ O(n)
    - Compare the length of each set  using `count()`→ O(n)
- Space: O(n)
    - `set` depends on the length of the string s and t → O(n)
    - `s.count` and `t.count` didn’t use any extra memory → O(1)

## 2. Optimize solution using Counter

```python
from collections import Counter

class Solution:
    def isAnagram(self, s, t):
        return Counter(s) == Counter(t)
```

- Time: O(n)
    - Counter(s) is utilized by the hash map. It depends on the length of the s → O(n)
- Space:  O(n)
    - Counter(s) save the length of the string and iteration of the character in the string. → O(n)
