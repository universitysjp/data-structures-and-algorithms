---
title: "Computational Complexity Analysis"
---

## Overview
Complexity analysis evaluates algorithm efficiency in terms of time and space requirements. It helps answer:
- How much time/space does an algorithm need?
- How does performance scale with input size?
- Which algorithm is best for a given task?

## Big-O Notation
Classifies algorithms based on growth rate of running time or space requirements.
- Provides an **upper bound** on growth rate
- Ignores constant factors and lower-order terms
- `O` refers to the "order of the function"

### Common Complexities

#### O(1) - Constant Time
- Same time regardless of input size
- Example: Array element access by index

#### O(log n) - Logarithmic Time
- Time proportional to logarithm of input size
- Example: Binary Search
- Very efficient for large inputs

#### O(n) - Linear Time
- Time directly proportional to input size
- Example: Linear Search, finding maximum in array

#### O(n log n) - Linearithmic Time
- Combination of linear and logarithmic growth
- Example: Merge Sort, Quick Sort (average case)
- Efficient for sorting algorithms

#### O(n²) - Quadratic Time
- Time proportional to square of input size
- Example: Bubble Sort, nested loops
- Often from comparing all pairs of elements

#### O(n³) - Cubic Time
- Less common but appears in some algorithms
- Example: Matrix multiplication (naive approach)

#### O(2ⁿ) - Exponential Time
- Doubles with each additional input element
- Example: Tower of Hanoi, recursive Fibonacci (naive)
- Generally impractical for large inputs

## Other Notations

### Ω (Omega) Notation
- Expresses **lower bound** (best-case complexity)
- Minimum time an algorithm will take

### θ (Theta) Notation
- Expresses **tight bound** (both upper and lower)
- Algorithm always takes this time complexity

## Analyzing Algorithms

### Counting Primitive Operations
- Assignment: O(1)
- Arithmetic operation: O(1)
- Comparison: O(1)
- Array access: O(1)
- Method call/return: O(1)

### Worst-Case Analysis
- Focus on longest running time for any input
- Easier than average-case analysis
- Provides performance guarantee

### Asymptotic Analysis
- Focus on growth rate as n approaches infinity
- Disregards constant factors
- Compares algorithms at large scale

## Practical Examples

### Finding Maximum: O(n)
```java
for (int i = 0; i < n; i++)
    if (arr[i] > max) max = arr[i];
```

### Nested Loops: O(n²)
```java
for (int i = 0; i < n; i++)
    for (int j = 0; j < n; j++)
        // operation
```

### Binary Search: O(log n)
- Halves search space each iteration
- Much faster than linear search for large arrays

## Comparison Table
| Complexity | n=10 | n=100 | n=1000 | n=10000 |
|------------|------|-------|--------|---------|
| O(1)       | 1    | 1     | 1      | 1       |
| O(log n)   | 3    | 7     | 10     | 13      |
| O(n)       | 10   | 100   | 1000   | 10000   |
| O(n log n) | 30   | 700   | 10000  | 130000  |
| O(n²)      | 100  | 10000 | 10⁶    | 10⁸     |
| O(2ⁿ)      | 1024 | 10³⁰  | 10³⁰¹  | 10³⁰¹⁰  |
