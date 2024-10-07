---
layout: single
title:  "Validate Parentheses"
categories: coding
tags: [JavaScript,leetcode]
---


# Valid Parentheses

**Difficulty**: Easy

---

## Problem Statement

Write a function that takes a string `s` containing only the characters `(`, `)`, `{`, `}`, `[` and `]`, and returns whether the input string is valid.

---

## Solution 1: HashMap and Stack

```javascript
var isValid = function(s) {
    const stack = [];
    const mapping = {
        ')': '(',
        '}': '{',
        ']': '['
    };
    for (const c of s) {
        if (Object.values(mapping).includes(c)) {
            stack.push(c);
        } else if (mapping.hasOwnProperty(c)) {
            if (!stack.length || mapping[c] !== stack.pop())
                return false;
        }
    }
    return stack.length === 0;
};

Time Complexity: O(n)
The for-of loop iterates over each character c in the string s.
Each c performs a constant time operation such as pop and push.
Space Complexity: O(n)
The stack depends on the input string s.
The mapping object has a fixed size, unrelated to the input, making it O(1).
