---
title: "⚡Group Anagrams"
layout: single
date: 2025-01-07
categories: ⚡LeetCode
tags: 
  - Array
  - Python
excerpt: "Solutions for the 'Group Anagrams' problem using Python and array."
author_profile: true
read_time: true
share: true
related: true
toc: true
---
# #49. Group Anagrams

- **Difficulty**: Medium
- **Company**: LeetCode75
- **Optimization**:  Yes
- **Review**: January 7, 2025
- **Select**: Hash Table
- **Solved**: No
- **Tried**: 1

# My Answer

```python

```

- Why I can’t solve this problem?
    - First, I tried to convert each string in the `strs` list into a list of sorted characters, such as ['a', 'e', 't'] for "eat".
    - Then, I stored these sorted results in a 2D list, such as [['a', 'e', 't'], ['a', 'b', 't']].
    - However, I didn’t know how to compare and group elements in this 2D list.
    - To solve this, I realized I could use a dictionary to store the sorted characters as a tuple (key) and group the original strings (value), like: {('a', 'e', 't'): ['eat', 'tea', 'ate']}.
    

# Reflection

- [x]  Exploring various solutions and clearly communicating them
- [x]  Stating the runtime and space complexity (the pros and cons) of each solution)
- [ ]  Translating ideas into code
- [x]   Debugging your code

# Best Answer

## 1. Using Hash Table(In python, Dictionary)

```python
class Solution(object):
    def groupAnagrams(self, strs):
        """
        :type strs: List[str]
        :rtype: List[List[str]]
        """
        answerDict = defaultdict(list) 
        #Create the empty dict where the default value for each eky is an empty list
        #defaultdict(<class 'list'>, {}) 
        
        for s in strs:
            key = tuple(sorted(s)) #Create a key by sorting s and converting to tuple. 
            #If s is "eat", the key is ('a','e','t') 
            answerDict[key].append(s) #Add the string s as a value for the corresponding key. 
            #If strs has a 'eat' and 'tea', the key is ('a','e','t') 
            #So the 'eat' and 'tea' is the value of the ('a','e','t') key.
            #answerDict = {('a','e','t'):['eat','tea']}     
        return list(answerDict.values())
        
#1.
#key = ('a','e','t')
#answerDict[key].append(s) 
#answerDict = {('a','e','t'):['eat']}
#2.
#key = ('a','e','t')
#answerDict[key].append(s) 
#answerDict = {('a','e','t'):['eat','tea']}
#3.
#key = ('a','n','t')
#answerDict[key].append(s) 
#answerDict = {('a','e','t'):['eat','tea'],('a','n','t'):['tan']}
#4.
#key = ('a','e','t')
#answerDict[key].append(s) 
#answerDict = {('a','e','t'):['eat','tea','ate'],('a','n','t'):['tan']}
#5.
#key = ('a','n','t')
#answerDict[key].append(s) 
#answerDict = {('a','e','t'):['eat','tea','ate'],('a','n','t'):['tan','nat']}
#6.
#key = ('a','b','t')
#answerDict[key].append(s) 
#answerDict = {('a','e','t'):['eat','tea','ate'],('a','n','t'):['tan','nat'],('a','b','t'):['bat']}
#
#answerDict.keys() = dict_keys([('a', 'e', 't'), ('a', 'n', 't'), ('a', 'b', 't')])
#answerDict.values() = dict_values([['eat', 'tea', 'ate'], ['tan', 'nat'], ['bat']])ea
```

- Complexity
    - $N$ : The number of elements in the `strs` list (i.e., the number of strings).
    - $K$ : The number of characters in each element of the `strs` list .
    
- Time: $O(N∗K∗Log(K)) = O(N) * O(K*Log(K))$
    - **Sorting each string**:
        - For each string in the `strs` list, we sort its characters. Sorting a string with k characters takes $O(K*Log(K))$
        - Since there are n strings, this step contributes:
        $O(N∗K∗Log(K))$
            
            
    - **Appending to the dictionary**:
        - For each string, we append it to the dictionary. In Python, dictionary operations (like adding or retrieving a value) take O(1) on average. Since this happens n times, this step contributes: $O(N)$
        
    
- Space: $O(N∗K) = O(N) * O(N)$
    - `answerDict` = {key, value pairs}
        - The key depends on the K, as the key is sorted tuple of string → $O(K)$
        - The value depends on the N, as all strings are stored in the dictionary. → $O(N)$
    - **Temporary storage for sorting**:
        - During the sorting process, temporary space is used to hold the sorted characters for each string. This requires O(k) space per string. However, since this space is reused for each string, it doesn’t add to the total complexity.
