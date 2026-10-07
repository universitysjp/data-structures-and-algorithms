---
title: "Binary Search"
---

## Overview
Binary search is a highly efficient searching algorithm that works on **sorted arrays**. It dramatically outperforms linear search for large datasets by using a divide-and-conquer approach that repeatedly halves the search space.

## How It Works
Binary search uses the "divide and conquer" strategy:

1. **Set bounds**: Initialize `lowerBound` (first index) and `upperBound` (last index)
2. **Calculate middle**: Find the middle index: `mid = lowerBound + (upperBound - lowerBound) / 2`
3. **Compare with target**: Compare the search key with the middle element
4. **Decision making**:
   - If `arr[mid] == key`: **Element found!** Return the index
   - If `arr[mid] < key`: Search right half (set `lowerBound = mid + 1`)
   - If `arr[mid] > key`: Search left half (set `upperBound = mid - 1`)
5. **Repeat** until element is found or bounds cross (`lowerBound > upperBound`)

### Why It's So Fast
Each comparison eliminates **half** of the remaining elements from consideration, leading to logarithmic time complexity.

## Implementation

### Complete implementation: `Algorithms/Searching/Binary Search/BinarySearch.java`

```java
package dsa.algorithms.searching;

public class BinarySearch {
    public static int iterative(int[] arr, int key) {
        int lo = 0, hi = arr.length - 1;
        while (lo <= hi) {
            int mid = lo + (hi - lo) / 2;
            if (arr[mid] == key) return mid;
            if (arr[mid] < key) lo = mid + 1;
            else hi = mid - 1;
        }
        return -1;
    }

    public static int recursive(int[] arr, int key) {
        return rec(arr, 0, arr.length - 1, key);
    }

    private static int rec(int[] arr, int lo, int hi, int key) {
        if (lo > hi) return -1;
        int mid = lo + (hi - lo) / 2;
        if (arr[mid] == key) return mid;
        if (arr[mid] < key) return rec(arr, mid + 1, hi, key);
        else return rec(arr, lo, mid - 1, key);
    }

    public static void main(String[] args) {
        int[] arr = {1,2,3,4,5,6,7,8,9};
        System.out.println(iterative(arr, 6)); // 5
        System.out.println(recursive(arr, 10)); // -1
    }
}
```

### Iterative Approach
```java
public static int iterative(int[] arr, int key) {
    int lo = 0, hi = arr.length - 1;
    while (lo <= hi) {
        int mid = lo + (hi - lo) / 2;  // Prevents integer overflow
        if (arr[mid] == key) return mid;
        if (arr[mid] < key) lo = mid + 1;
        else hi = mid - 1;
    }
    return -1;  // Element not found
}
```

### Recursive Approach
```java
public static int recursive(int[] arr, int key) {
    return rec(arr, 0, arr.length - 1, key);
}

private static int rec(int[] arr, int lo, int hi, int key) {
    if (lo > hi) return -1;  // Base case: not found
    int mid = lo + (hi - lo) / 2;
    if (arr[mid] == key) return mid;
    if (arr[mid] < key) return rec(arr, mid + 1, hi, key);
    else return rec(arr, lo, mid - 1, key);
}
```

## Characteristics & Complexity Analysis

### Time Complexity
- **Best case: O(1)** - element found at the middle on first try
- **Average case: O(log n)** - typical case requiring multiple divisions
- **Worst case: O(log n)** - element at the end or not present

### Space Complexity
- **Iterative version: O(1)** - uses constant extra space
- **Recursive version: O(log n)** - due to function call stack

### Prerequisites & Properties
- **Sorted array required**: Algorithm only works on pre-sorted data
- **Random access needed**: Requires array-like structure with O(1) indexing
- **Deterministic**: Always produces the same result for the same input

## Study Notes for Students

### Key Concepts to Understand
1. **Divide and Conquer**: How the problem size is reduced by half each iteration
2. **Loop Invariant**: The target element (if present) is always within [lo, hi]
3. **Integer Overflow Prevention**: Why we use `lo + (hi - lo) / 2` instead of `(lo + hi) / 2`
4. **Base Cases**: When to stop recursion or iteration

### Common Student Mistakes
- Forgetting that the array must be sorted first
- Using `(lo + hi) / 2` which can cause integer overflow
- Incorrect boundary updates (using `mid` instead of `mid ± 1`)
- Off-by-one errors in loop conditions

### Problem-Solving Patterns
Binary search is the foundation for many advanced algorithms:
- Finding insertion points
- Range queries (first/last occurrence)
- Peak finding in arrays
- Square root calculation
- Searching in rotated sorted arrays

## Comparison with Linear Search

| Aspect | Linear Search | Binary Search |
|--------|---------------|---------------|
| **Time Complexity** | O(n) | O(log n) |
| **Array Requirement** | Any order | Must be sorted |
| **Space Complexity** | O(1) | O(1) iterative, O(log n) recursive |
| **Best for** | Small or unsorted arrays | Large sorted arrays |

### When Each is Better
- **Linear Search**: Unsorted data, very small arrays (< 100 elements)
- **Binary Search**: Large sorted datasets, repeated searches on same data

## Variants and Extensions

### Modified Binary Search Problems
1. **Find First/Last Occurrence**: Handle duplicate elements
2. **Find Insertion Point**: Where to insert an element to maintain sorted order
3. **Search in Rotated Array**: Modified binary search for rotated sorted arrays
4. **Find Peak Element**: Local maximum in an array

### Real-World Applications
- **Database indexing**: B-trees use binary search principles
- **Dictionary lookups**: Word finding in sorted dictionaries
- **Library systems**: Book searching in cataloged systems
- **Memory management**: Finding free memory blocks

## Practice Problems

### Beginner Level
1. Implement both iterative and recursive versions
2. Find the insertion point for a new element
3. Count occurrences of an element in a sorted array

### Intermediate Level
1. Find first and last position of element in sorted array
2. Search in a rotated sorted array
3. Find peak element in an array
4. Search in a 2D sorted matrix

### Advanced Level
1. Median of two sorted arrays
2. Kth smallest element in sorted matrix
3. Binary search on answer (optimization problems)

## Related Topics
- [Linear Search](./algorithms-searching-linear-search) - Alternative searching method
- [Recursion](./algorithms-recursion) - Fundamental concept for recursive implementation
- [Divide and Conquer](./algorithms-divide-and-conquer) - Core algorithmic strategy
- [Sorting Algorithms](./algorithms) - Prerequisite for binary search
- **Much faster than linear search for large arrays**

## Recursive vs Iterative
- **Recursive**: Cleaner code, uses call stack, may cause stack overflow for very large arrays
- **Iterative**: More efficient space-wise, no stack overflow risk

## Implementation
- BinarySearch.java (both iterative and recursive versions)

