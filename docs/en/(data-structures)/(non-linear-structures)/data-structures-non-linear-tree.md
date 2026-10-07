---
title: "Tree Data Structures"
---

Trees are a foundational data structure in computer science, offering a blend of fast searchability, similar to ordered arrays, and efficient insertion/deletion, comparable to linked lists.

#### Key Concepts:
- **Binary Trees**: Each node has at most two children (left and right).
  - **Leaf Node**: A node with no children.
- **Binary Search Trees (BST)**: A binary tree where the left child’s key is less than its parent, and the right child’s key is greater than or equal to its parent. This organization facilitates fast searching and insertion.


### Tree Terminology:
- **Root**: The topmost node in a tree.
- **Parent**: A node that has at least one child.
- **Child**: A node that descends from another node.
- **Subtree**: Any tree formed from a node and its descendants.
- **Path**: A sequence of nodes connected by edges.
- **Level**: The depth of a node, where the root is at level 0.
- **Traversal**: Visiting all nodes in a specific order (Pre-order, In-order, Post-order).

## Binary Search Trees

### Insertion to a Binary Search Tree from left-to-right

Values:
65, 32, 44, 21, 78, 12, 87, 66, 5, 99, 35, 82, 71

1. Start with 65 as the root.
2. Insert 32, which is less than 65, so it goes to the left of 65.
3. Insert 44, which is greater than 32 but less than 65, so it goes to the right of 32.
4. Insert 21, which is less than 32, so it goes to the left of 32.
5. Insert 78, which is greater than 65, so it goes to the right of 65.
6. Insert 12, which is less than 21, so it goes to the left of 21.
7. Insert 87, which is greater than 78, so it goes to the right of 78.
8. Insert 66, which is less than 78 but greater than 65, so it goes to the left of 78.
9. Insert 5, which is less than 12, so it goes to the left of 12.
10. Insert 99, which is greater than 87, so it goes to the right of 87.
11. Insert 35, which is greater than 32 but less than 44, so it goes to the left of 44.
12. Insert 82, which is greater than 78 but less than 87, so it goes to the left of 87.
13. Insert 71, which is greater than 66 but less than 78, so it goes to the right of 66.

##### Resulting BST:

```
        65
       /   \
     32     78
    /  \    /   \
  21   44  66    87
 /     /      \   /  \
12    35      71 82  99
 /
5
```

### 1. **In-order Traversal (Left, Root, Right):**
In-order traversal visits the nodes in ascending order for a binary search tree.

Traversal steps:
1. Start from the leftmost node (smallest value), visit the left subtree, then the root, and then the right subtree.

**In-order Traversal:**
```
5, 12, 21, 32, 35, 44, 65, 66, 71, 78, 82, 87, 99
```

### 2. **Pre-order Traversal (Root, Left, Right):**
In pre-order traversal, we visit the root first, then the left subtree, followed by the right subtree.

Traversal steps:
1. Visit the root, then traverse the left subtree, and finally the right subtree.

**Pre-order Traversal:**
```
65, 32, 21, 12, 5, 44, 35, 78, 66, 71, 87, 82, 99
```

### 3. **Post-order Traversal (Left, Right, Root):**
In post-order traversal, we visit the left subtree first, then the right subtree, and finally the root.

Traversal steps:
1. Traverse the left subtree, then the right subtree, and finally visit the root.

**Post-order Traversal:**
```
5, 12, 21, 35, 44, 32, 71, 66, 82, 99, 87, 78, 65
```

These are the three traversals for the given binary search tree!

---

### Implementing a Tree in Java:

### [Full Code Example](https://github.com/universitysjp/data-structures-and-algorithms/blob/main/Data%20Structures/Non%20Linear/Tree/Tree.java)

#### Node Class:
A `Node` class represents each individual node in the tree.

```java
class Node {
    int iData; // Key or data
    Node leftChild; // Left child node
    Node rightChild; // Right child node
}
```

#### Tree Class:
A `Tree` class manages the root node and methods for operations like insertion, deletion, and searching.

```java
class Tree {
    private Node root;

    public Node find(int key) {
        // Find method implementation
    }

    public void insert(int id) {
        // Insert method implementation
    }

    public boolean delete(int key) {
        // Delete method implementation
    }
}
```

### Inserting a New Node:

```java
public void insert(int id) {
    Node newNode = new Node(); // Create a new node
    newNode.iData = id;

    if (root == null) {
        root = newNode; // Tree is empty
    } else {
        Node current = root;
        Node parent;

        while (true) {
            parent = current;
            if (id < current.iData) {
                current = current.leftChild;
                if (current == null) {
                    parent.leftChild = newNode;
                    return;
                }
            } else {
                current = current.rightChild;
                if (current == null) {
                    parent.rightChild = newNode;
                    return;
                }
            }
        }
    }
}
```

### Tree Traversal:
Traversal methods are used to visit each node in a specific order.

#### In-order Traversal:
Visits nodes in ascending order.

```java
private void inOrder(Node localRoot) {
    if (localRoot != null) {
        inOrder(localRoot.leftChild);
        System.out.print(localRoot.iData + " ");
        inOrder(localRoot.rightChild);
    }
}
```

#### Pre-order Traversal:
Visits the root node first, then left and right subtrees.

```java
private void preOrder(Node localRoot) {
    if (localRoot != null) {
        System.out.print(localRoot.iData + " ");
        preOrder(localRoot.leftChild);
        preOrder(localRoot.rightChild);
    }
}
```

#### Post-order Traversal:
Visits left and right subtrees first, then the root node.

```java
private void postOrder(Node localRoot) {
    if (localRoot != null) {
        postOrder(localRoot.leftChild);
        postOrder(localRoot.rightChild);
        System.out.print(localRoot.iData + " ");
    }
}
```

Here's the refined version of the section with **deleting a node, deleting a leaf, and deleting a node with one child**:

---

### Deleting a Node:
When deleting a node in a binary search tree, there are three main cases to consider:

1. **Deleting a Leaf Node**: The node has no children.
2. **Deleting a Node with One Child**: The node has either a left child or a right child, but not both.
3. **Deleting a Node with Two Children**: The node has both a left and a right child (covered below but more complex).

#### Deleting a Leaf:
If the node to be deleted is a leaf (no children), there are two possible cases:

- **If the node is the root**: The tree becomes empty after deleting it, so the root is set to `null`.
- **If the node is not the root**: Set the appropriate child reference of the parent node to `null`. If the node to be deleted is the left child, set the parent's left child to `null`; if it's the right child, set the parent's right child to `null`.

##### Example:
```java
if (current.leftChild == null && current.rightChild == null) {
    if (current == root) // If it's the root
        root = null;     // The tree is empty
    else if (isLeftChild)
        parent.leftChild = null; // Remove the left child
    else
        parent.rightChild = null; // Remove the right child
}
```

#### Deleting a Node with One Child:
If the node to be deleted has one child (either left or right), the child of the deleted node must take its place. This is done by updating the parent’s pointer to point to the node's child.

##### Example:
```java
// If the node has only a left child
if (current.rightChild == null) {
    if (current == root)
        root = current.leftChild;
    else if (isLeftChild)
        parent.leftChild = current.leftChild;
    else
        parent.rightChild = current.leftChild;
}

// If the node has only a right child
else if (current.leftChild == null) {
    if (current == root)
        root = current.rightChild;
    else if (isLeftChild)
        parent.leftChild = current.rightChild;
    else
        parent.rightChild = current.rightChild;
}
```

