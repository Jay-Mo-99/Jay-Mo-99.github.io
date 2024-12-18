---
title: "🧩 Timsort Algorithm"
layout: single
date: 2024-12-17
categories: 🧩Algorithm 
tags: 
  - Algorithm
excerpt: "Note for the 'Timsort Algorithm' in Algorithm"
author_profile: true
read_time: true
share: true
related: true
toc: true
---
# Timsort Algorithm

- **Repeated**: 1
- **Multi-select**: Merge Sort, Insertion Sort
- **Review**: December 17, 2024

## **Why is the Time Complexity of `sort()` and `sorted()` O(N log N)?**

### **Python uses the *Tim-Sort* algorithm in `sort()`**

---

### **1. Divide Phase**

1. **Splitting the list in half → O(log N):** The list is repeatedly split into halves.
2. **Example:**
    
    ```csharp
    
    [8, 3, 7, 4, 2, 6, 5, 1]
    
    ```
    
    - **Step 1:** `[8, 3, 7, 4]` | `[2, 6, 5, 1]` (split into two halves).
    - **Step 2:** `[8, 3]` | `[7, 4]` | `[2, 6]` | `[5, 1]` (split further).
    - **Step 3:** `[8] | [3] | [7] | [4] | [2] | [6] | [5] | [1]` (cannot be split further).

---

### **2. Merge Phase**

1. **Merging lists at each step → O(N):**
    
    Once the lists cannot be split further, **merging and sorting** begin.
    
2. **During merging:**
    - Smaller sorted lists are combined to form larger sorted lists.
3. **Merge Example:**
    - Step 1 (small lists):
        - `[8]` and `[3]` → `[3, 8]`
        - `[7]` and `[4]` → `[4, 7]`
        - `[2]` and `[6]` → `[2, 6]`
        - `[5]` and `[1]` → `[1, 5]`
    - Step 2 (merging larger lists):
        - `[3, 8]` and `[4, 7]` → `[3, 4, 7, 8]`
        - `[2, 6]` and `[1, 5]` → `[1, 2, 5, 6]`
    - Final merge:
        - `[3, 4, 7, 8]` and `[1, 2, 5, 6]` → `[1, 2, 3, 4, 5, 6, 7, 8]`

---

### **3. Overall Time Complexity Calculation:**

- **Merging all the lists** at each level takes **O(N)** time.
- The number of levels in the splitting process is **O(log N)**.

Thus, the total time complexity is: **O(N) × O(log N) = O(N log N)**
