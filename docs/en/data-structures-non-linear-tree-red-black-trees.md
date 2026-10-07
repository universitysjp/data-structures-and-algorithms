---
title: "Red-Black Trees"
---

# Red-Black Trees

## Overview
Red-Black Trees are self-balancing binary search trees that guarantee O(log n) search times by maintaining balance during insertions and deletions.

## The Problem with Regular BST
- Suffer when data is inserted in sorted order
- Can become maximally unbalanced (like a linked list)
- Search speed degrades from O(log n) to O(n)

## Red-Black Tree Properties
Every Red-Black tree must satisfy these rules:

1. **Every node is either RED or BLACK**
2. **The root is always BLACK**
3. **Red Node Constraint**: If a node is red, its children must be black (no two red nodes in a row)
4. **Black Height Property**: Every path from root to leaf contains the same number of black nodes
5. **NIL nodes (null children) are considered BLACK**

## Balancing Operations

### Color Flips
- Change node from red to black or vice versa
- Used to maintain color properties

### Rotations
- **Left Rotation**: Moves right child up, node becomes left child
- **Right Rotation**: Moves left child up, node becomes right child
- Preserves BST property while rebalancing

## Insertion Process
1. Insert new node as in regular BST (colored RED)
2. Fix violations by:
   - Recoloring nodes
   - Performing rotations
3. Ensure root is BLACK

## Advantages
- **Guaranteed O(log n)** for all operations
- **Self-balancing**: Automatically maintains balance
- **Better worst-case than regular BST**
- Each node has roughly same number of descendants on left and right

## Applications
- Used in many libraries and systems:
  - C++ STL's map and set
  - Java's TreeMap and TreeSet
  - Linux kernel's completely fair scheduler
- Maintaining sorted data with frequent insertions/deletions
- Database indexing

## Comparison with Other Self-Balancing Trees
- **vs AVL Trees**: Less strictly balanced but faster insertion/deletion
- **vs 2-3-4 Trees**: Red-Black trees are isomorphic to 2-3-4 trees
- **vs B-Trees**: Better for in-memory structures

## Implementation
- RedBlackTree.java: Insert with rotations and fixup operations
