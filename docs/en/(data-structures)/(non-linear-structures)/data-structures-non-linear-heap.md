---
title: "Heaps"
---

## Overview
Heaps are complete binary trees that satisfy the heap property. They're primarily used to implement priority queues efficiently.

## Characteristics
- **Complete Binary Tree**: Completely filled from left to right
- **Usually implemented as an array** for efficiency
- **Heap Property**:
  - Max-heap: Every node's key ≥ its children's keys
  - Min-heap: Every node's key ≤ its children's keys
- **Weakly ordered** compared to BST (no left-right ordering)
- **Root always contains max (or min) element**

## Operations

### Insertion - O(log n)
1. Place new node at first open position (end of array)
2. Trickle up: Swap with parent if larger (max-heap)
3. Continue until heap property restored

### Removal - O(log n)
1. Remove root (max/min element)
2. Move last node to root
3. Trickle down: Swap with larger child
4. Continue until heap property restored

## Array Representation
- Parent of node at index i: (i-1)/2
- Left child of node at index i: 2*i + 1
- Right child of node at index i: 2*i + 2

## Applications
- **Priority Queues**: Efficient access to highest priority item
- **Heap Sort**: O(n log n) sorting algorithm
- **Dijkstra's Algorithm**: For shortest path
- **Task Scheduling**: In operating systems
- **Huffman Coding**: For data compression

## Heap Sort
1. Build heap from unsorted array
2. Repeatedly remove max element
3. Place removed elements at end of array
- Time Complexity: O(n log n)
- In-place sorting algorithm

## Implementation
- BinaryHeap.java: Max-heap with trickle up/down operations
