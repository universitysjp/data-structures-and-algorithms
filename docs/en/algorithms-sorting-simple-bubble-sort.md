---
title: "Bubble Sort"
---

# Bubble Sort

## Overview
Bubble sort is conceptually the simplest sorting algorithm but also very slow. It's rarely used in practice except for educational purposes. The algorithm gets its name because smaller elements "bubble" to the top of the array through successive comparisons and swaps.

## How It Works
The bubble sort algorithm works by repeatedly stepping through the array, comparing adjacent elements and swapping them if they're in the wrong order:

1. **Compare adjacent elements** starting from the first pair
2. **Swap if they're in wrong order** (left > right for ascending sort)
3. **Continue through the entire array** - this completes one pass
4. **Repeat passes** until no swaps are needed in a complete pass
5. **Each pass "bubbles" the largest unsorted element** to its correct position at the end

### Detailed Algorithm Steps:
- Pass 1: The largest element moves to the last position
- Pass 2: The second largest moves to the second-to-last position
- Continue until all elements are in their correct positions
- **Optimization**: If no swaps occur in a pass, the array is sorted

## Implementation

### 📁 [View Complete Implementation](https://github.com/universitysjp/data-structures-and-algorithms/blob/main/Algorithms/Sorting/Simple/Bubble%20Sort/BubbleSort.java)

```java
public static void sort(int[] a) {
    boolean swapped;
    for (int n = a.length; n > 1; n--) {
        swapped = false;
        for (int i = 1; i < n; i++) {
            if (a[i-1] > a[i]) {
                // Swap elements
                int temp = a[i-1];
                a[i-1] = a[i];
                a[i] = temp;
                swapped = true;
            }
        }
        if (!swapped) break; // Early termination optimization
    }
}
```

## Characteristics & Complexity Analysis

### Time Complexity
- **Best case: O(n)** - when array is already sorted (with optimization)
- **Average case: O(n²)** - typical unsorted data
- **Worst case: O(n²)** - when array is reverse sorted

### Space Complexity
- **O(1)** - sorts in place, only uses a constant amount of extra memory

### Other Properties
- **Stable**: Yes - maintains relative order of equal elements
- **Adaptive**: Yes - performs better on nearly sorted data
- **In-place**: Yes - requires only O(1) extra memory
- **Online**: No - needs the entire dataset before sorting

## Study Notes for Students

### Why Study Bubble Sort?
1. **Educational Foundation**: Helps understand sorting concepts and algorithm analysis
2. **Comparison Baseline**: Shows why more efficient algorithms are needed
3. **Algorithm Analysis Practice**: Good for learning Big-O notation

### Key Learning Points
- **Nested Loop Structure**: Outer loop for passes, inner loop for comparisons
- **Early Termination**: How optimizations can improve best-case performance
- **In-place Sorting**: Understanding memory-efficient algorithms
- **Stability Concept**: How equal elements maintain their relative order

## Advantages
- Simple to understand and implement
- No additional memory needed (in-place)
- Can detect if array is already sorted (with optimization)
- Stable sorting algorithm

## Disadvantages
- Very slow for large datasets O(n²)
- Many unnecessary comparisons in basic implementation
- Not practical for real-world applications
- Poor performance compared to other O(n²) algorithms

## When to Use
- **Educational purposes** to understand sorting fundamentals
- **Very small datasets** (< 10 elements) where simplicity matters
- **Nearly sorted data** with the optimized version
- **When stability is required** and dataset is tiny

## Related Algorithms
- [Selection Sort](./algorithms-sorting-simple-selection-sort) - Another O(n²) algorithm with fewer swaps
- [Insertion Sort](./algorithms-sorting-simple-insertion-sort) - More efficient O(n²) algorithm
- [Merge Sort](./algorithms-sorting-advanced-merge-sort) - O(n log n) stable sort
- [Quick Sort](./algorithms-sorting-advanced-quick-sort) - O(n log n) average case

## Implementation
- BubbleSort.java

