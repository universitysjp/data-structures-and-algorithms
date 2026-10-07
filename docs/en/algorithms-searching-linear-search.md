---
title: "Linear Search"
---

# Linear Search

## Overview
Linear search is the default searching algorithm for **unordered arrays**. It's the simplest search algorithm but also the least efficient for large datasets.

## How It Works
1. Start from the first element
2. Compare each element with the search key
3. If found, return the index
4. If end is reached without finding, return -1

## Characteristics
- **Time Complexity**: O(n) - must check each element in worst case
- **Space Complexity**: O(1) - no extra space needed
- **Best for**: Small arrays or unsorted data
- **When to use**:
  - Data is unsorted
  - Dataset is small
  - Simplicity is more important than efficiency

## Implementation
- LinearSearch.java

