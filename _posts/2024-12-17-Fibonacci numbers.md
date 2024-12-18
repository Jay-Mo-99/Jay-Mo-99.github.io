---
title: "🧩 Fibonacci numbers"
layout: single
date: 2024-12-17
categories: 🧩Algorithm 
tags: 
  - Algorithm
excerpt: "Note for the 'Fibonacci numbers' in Algorithm"
author_profile: true
read_time: true
share: true
related: true
toc: true
---

# Fibonacci numbers

- **Repeated**: 1
- **Multi-select**: Dynamic Programming
- **Review**: December 17, 2024

# **Fibonacci Numbers/Sequence**

$Fn = Fn-1 + Fn-2$

- **Base Cas**
    - The initial values F(0) and F(1) must be clearly defined to generate the sequence.
    - F(0)=0
    - F(1)=1
- **Definition Range**
    - This recurrence relation is valid for n≥2.

---

### Fibonacci Sequence Example:

```python

0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, ...
```

---

# Python Implementation of Fibonacci Numbers/Sequence

```python
python
Copy code
def fibonacci_iterative(n):
    a, b = 0, 1 # Initial values: F(0)=0, F(1)=1
    for _ in range(n):
        a, b = b, a + b # Update a and b in each loop

    return a # a is the n-th Fibonacci number F(n)

```

---

### Explanation of the Iterative Process:

- **Initial State:** `a = 0`, `b = 1`
1. **First Loop:**
    - `a = b = 1` (current value of `b`)
    - `b = a + b = 0 + 1 = 1` (next Fibonacci number)
    - **Return Value:** `a = 1` (At this point, F(1)=1)
        
        
2. **Second Loop:**
    - `a = b = 1` (current value of `b`)
    - `b = a + b = 1 + 1 = 2` (next Fibonacci number)
    - **Return Value:** `a = 1` (At this point, F(2)=1)
        
        
3. **Third Loop:**
    - `a = b = 2` (current value of `b`)
    - `b = a + b = 1 + 2 = 3` (next Fibonacci number)
    - **Return Value:** `a = 2` (At this point, F(3)=2)
    
4. **Fourth Loop:**
    - `a = b = 3` (current value of `b`)
    - `b = a + b = 2 + 3 = 5` (next Fibonacci number)
    - **Return Value:** `a = 3` (At this point, F(4)=3)
    
5. **Fifth Loop:**
    - `a = b = 5` (current value of `b`)
    - `b = a + b = 3 + 5 = 8` (next Fibonacci number)
    - **Return Value:** `a = 5` (At this point, F(5)=5)
