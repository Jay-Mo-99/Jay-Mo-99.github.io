---
title: "🚀 Linked List"
layout: single
date: 2024-10-09
categories: 🚀Data-Structure
tags: 
  - Algorithm
  - Array
excerpt: "Note for the 'Linked List' in data structure"
author_profile: true
read_time: true
share: true
related: true
toc: true
---

# Linked List

- **Number**: 1  
- **Presentation**: Yes
- **Review**: October 9, 2024  
- **Select**: Algorithm, Data Structure

# Difference of Array and Linked List on the Array

![image.png](image.png)

- Array List
    - Continuous Memory Allocation → **fast access** to specific indexes
    - Inefficient Memory Allocation → If we need to resize the array, a new block of memory must be allocated, and the existing data has to be copied
- Linked List
    - A Linked List stores each element (node) in ***different memory locations***
    - Each node contains a ***pointer*** to the next node, linking them together
    - Accessing a specific index requires **traversing from the beginning** (time complexity O(n))
        - Slower than an Array List, but **insertion and deletion** operations are more efficient

# Structure of Linked List

![image.png](image%201.png)

- **Node**(Vertex) = 마디(꼭짓점), Instead of element, Using Node
    - Data Field : Real Value of Node
    - Link Field(Next Pointer): Pointer for saving the information about next node
- **Head**: ***A pointer***  to the first node of the Linked List
- T**ail:** The Last Node of the Linked List***, Tail’s Link Field always points the null***

# Operation of Linked List

## Insert

### Insert new node to the first of the linked list

![image.png](image%202.png)

- Process
    1. Create the new object.
        - For example, vtx which has 51 value, were created
    2. Setting the New Object(51)’s Next Pointer points the head( A pointer to the first node)
        - Setting the vtx’s arrow point the head(-77).
    3. Update the new **head** to the new object 

- Time Complexity: O(1)

### Insert new node to the middle of the linked list

![image.png](image%203.png)

- Process
    1. **Approach the target index**:
        - Find the node (`pre`) that comes before the target insertion index. For example, if you want to insert a new node at index 5, locate the node at index 4 (`pre`).
        - Use a loop to traverse the linked list and set `pre` accordingly.
    2. **Create the new node**:
        - For instance, create a new node (`vtx`) with the value `1`.
    3. **Update the links**:
        - Set the `Next Pointer` of the new node (`vtx`) to point to the node that `pre.next` is currently pointing to.
        - Update `pre.next` to point to the new node (`vtx`).

## Delete

![image.png](image%204.png)

- Process
    1. **Approach the target index**:
        1. First, find the node (`pre`) that comes right before the node to be deleted. Use a loop to traverse the list so that `pre` reaches the node just before the target index.
        2. For example, if you want to delete the node at index 4, `pre` should point to the node at index 3.
    2. **Update the links**:
        1. Set a pointer (`del`) to the node to be deleted, for example, `del = pre.next`.
        2. Set another pointer (`aft`) to the node after the one to be deleted, for example, `aft = del.next`.
        3. Update `pre.next` to point to `aft`, effectively bypassing the node `del`. This removes the node from the list.
    3. **Delete the node**:
        1. Free the memory occupied by the node to be deleted, for example, using `delete del`.
        
- Time Complexity: O(n)
    - Loop to traverse the list to find the pre, So it depends on the number of the node(n)

# Single Linked List

- **Unidirectional:** We can only traverse the list in one direction, from the head to the tail
- **Non-Continuous memory allocation**: Nodes may not be stored in contiguous memory locations.
- Backward traversal is not possible
- **Memory Overhead**
    - There is some memory overhead because each node stores an additional pointer(next pointer). It consumes extra memory for storing value and pointers.

# Double Linked List

- Each node has both a next pointer and a previous pointer, allowing bidirectional traversal.
- Bidirectional traversal: We can freely move forward and backward
- Easier to node insertion and deletion
- Consumes more memory
- Complexity in managing pointers.

# **Queue**

### Abstract Data Type(ADT)

- Type of the Data Structure, Just several behaviours, this structure is, not existed code structure.

### Definition

![image.png](image%205.png)

![image.png](image%206.png)

- First in, First Out(FiFo), Such as the waiting line for the bus
- Enqueue: Add new element to the back of the queue
- Dequeue: Read and Delete the element to the front of the queue

### Usage: First Come, First Served feature, Handling input data in order

- Sending an email
- push alarm system
- Handling order information in Shopping mall
- Backend of Call Center service

### Operation

- **Enqueue**
- **Dequeue**
- **Peek/Front**: Return the first element of the queue without deleting.
- **isEmpty**
- **Size**: Return the num of the element in the queue

### Advantage

- Maintain order
- Efficient memory management: Not complexity of the calculation

### Disadvantage

- Difficult to Approach middle of the queue
- If the fixed-size queue is used, it might be waste the memory
- If the dynamic queue is used, we have to handle the assigning and deleting the memory

# Reference

[Linked list 개념 1 - 소개 - Data Structure](https://www.youtube.com/watch?v=sq49IpxBl2k)

[개발자라면 무조건 알아야하는 자료구조! 5분컷.](https://www.youtube.com/watch?v=Nk_dGScimz8&list=PL7jH19IHhOLMdHvl3KBfFI70r9P0lkJwL&index=7)

