---
title: "Linked List"
---

# Linked List

A **Linked List** is a linear data structure where elements are stored in nodes, and each node contains two parts:
1. **Data**: The value stored in the node.
2. **Next Pointer**: A reference (or pointer) to the next node in the sequence.

#### Types of Linked Lists:
1. **Singly Linked List**: Each node has one pointer that points to the next node in the list.
2. **Doubly Linked List**: Each node has two pointers, one pointing to the next node and one to the previous node.
3. **Circular Linked List**: The last node points back to the first node instead of pointing to `null`.

---

### Operations in Linked Lists

#### 1. **Insertion**
You can insert a node at the beginning, middle, or end of the list.
- **Insert at the head**: This involves pointing the new node to the current head of the list and updating the head.
- **Insert at the tail**: Traverse the entire list to find the last node and update its `next` pointer to the new node.
- **Insert at a specific position**: Traverse to the desired position and adjust pointers accordingly.

#### 2. **Deletion**
- **Delete at the head**: Simply move the head pointer to the second node.
- **Delete at the tail**: Traverse to the second last node and set its `next` pointer to `null`.
- **Delete at a specific position**: Traverse to the node before the one to be deleted and adjust the pointers to bypass the node.

#### 3. **Traversal**
This operation involves visiting each node, typically to access or modify its data. Traversal can be performed from the head to the tail.

#### 4. **Searching**
You can search for a specific value by traversing the list node by node until you find the target value or reach the end of the list.

---

### Linked List Implementation in Java

Let's start by implementing the **Node** class and the **Singly Linked List** structure. We'll break this into smaller pieces for clarity.

#### Step 1: Node Class

```java
class Node {
    int data;
    Node next;

    // Constructor to initialize node data
    public Node(int data) {
        this.data = data;
        this.next = null;
    }
}
```

This is the basic structure of a `Node` in a singly linked list:
- **data** stores the value.
- **next** is a reference to the next node.

#### Step 2: Linked List Class (Skeleton)

```java
class LinkedList {
    Node head;

    // Constructor to initialize the linked list
    public LinkedList() {
        head = null;
    }

    // Method to insert a node at the head
    public void insertAtHead(int data) {
        Node newNode = new Node(data);
        newNode.next = head;  // Point new node to the current head
        head = newNode;       // Update head to new node
    }
}
```

Here, we initialize the `LinkedList` class with an empty list (i.e., the head is `null`).

---

### Insertion Operation: Breakdown

#### Insert at the Head

```java
public void insertAtHead(int data) {
    Node newNode = new Node(data);
    newNode.next = head;  // Point the new node to the current head
    head = newNode;       // Update head to new node
}
```
- **Time Complexity**: O(1), since inserting at the head does not require traversing the list.

#### Insert at the Tail

```java
public void insertAtTail(int data) {
    Node newNode = new Node(data);
    if (head == null) {
        head = newNode;
    } else {
        Node temp = head;
        while (temp.next != null) {
            temp = temp.next;  // Traverse to the last node
        }
        temp.next = newNode;  // Point the last node to the new node
    }
}
```
- **Time Complexity**: O(n), because you need to traverse the list to find the last node.

#### Insert at a Specific Position

```java
public void insertAtPosition(int data, int position) {
    Node newNode = new Node(data);
    if (position == 1) {
        newNode.next = head;
        head = newNode;
    } else {
        Node temp = head;
        for (int i = 1; i < position - 1 && temp != null; i++) {
            temp = temp.next;
        }
        if (temp != null) {
            newNode.next = temp.next;
            temp.next = newNode;
        }
    }
}
```
- **Time Complexity**: O(n), as you may need to traverse up to the specified position.

---

### Deletion Operation: Breakdown

#### Delete at the Head

```java
public void deleteAtHead() {
    if (head != null) {
        head = head.next;  // Move the head to the next node
    }
}
```
- **Time Complexity**: O(1), because you just update the head.

#### Delete at the Tail

```java
public void deleteAtTail() {
    if (head == null) return;
    if (head.next == null) {
        head = null;
    } else {
        Node temp = head;
        while (temp.next.next != null) {
            temp = temp.next;  // Traverse to the second last node
        }
        temp.next = null;  // Set the next pointer of second last node to null
    }
}
```
- **Time Complexity**: O(n), as you need to traverse to the second last node.

#### Delete at a Specific Position

```java
public void deleteAtPosition(int position) {
    if (position == 1) {
        deleteAtHead();
    } else {
        Node temp = head;
        for (int i = 1; i < position - 1 && temp != null; i++) {
            temp = temp.next;
        }
        if (temp != null && temp.next != null) {
            temp.next = temp.next.next;
        }
    }
}
```
- **Time Complexity**: O(n), because you may need to traverse to the specific position.

---

### Traversal Operation: Breakdown

```java
public void traverse() {
    Node temp = head;
    while (temp != null) {
        System.out.print(temp.data + " -> ");
        temp = temp.next;  // Move to the next node
    }
    System.out.println("null");
}
```
- **Time Complexity**: O(n), since every node must be visited.

---

### Comparison: Linked List vs. Stack vs. Queue

- **Stack**: A Last-In-First-Out (LIFO) structure, where insertion and removal happen at the top. Operations in a stack are O(1) for both insertion and removal (push/pop).
- **Queue**: A First-In-First-Out (FIFO) structure, where insertion happens at the back, and removal happens from the front. Like a linked list, a queue requires O(1) for insertion and removal.
- **Linked List**: More flexible than both stacks and queues because you can insert or remove elements from any position. However, accessing elements (random access) in linked lists requires O(n) time, while stacks and queues limit access to specific ends.

---

### Doubly Linked List Documentation

A **Doubly Linked List** is an extension of the singly linked list where each node contains two pointers:
1. **Next Pointer**: Points to the next node in the sequence.
2. **Previous Pointer**: Points to the previous node in the sequence.

This allows traversal of the list in both directions, enhancing flexibility for various operations.

#### Advantages of Doubly Linked Lists:
- **Bidirectional Traversal**: Ability to traverse forwards and backwards.
- **Efficient Deletion**: Easier to delete a node when you have a reference to it, without needing to traverse from the head.

#### Disadvantages:
- **Extra Memory**: Requires additional memory for the previous pointer in each node.
- **Complexity**: More complex to implement compared to singly linked lists.

---

### Operations in Doubly Linked Lists

#### 1. **Insertion**
Insertion operations are similar to singly linked lists but involve updating both `next` and `prev` pointers.

- **Insert at the Head**
- **Insert at the Tail**
- **Insert at a Specific Position**

#### 2. **Deletion**
Deletion also requires updating both `next` and `prev` pointers.

- **Delete at the Head**
- **Delete at the Tail**
- **Delete at a Specific Position**

#### 3. **Traversal**
Can be performed in both forward and backward directions.

- **Forward Traversal**
- **Backward Traversal**

#### 4. **Searching**
Similar to singly linked lists but can optimize in some cases due to bidirectional access.

---

### Doubly Linked List Implementation in Java

We'll implement a **Doubly Linked List** by defining the `Node` class and the `DoublyLinkedList` class with various operations.

#### Step 1: Node Class

```java
class DoublyNode {
    int data;
    DoublyNode next;
    DoublyNode prev;

    // Constructor to initialize node data
    public DoublyNode(int data) {
        this.data = data;
        this.next = null;
        this.prev = null;
    }
}
```

**Explanation:**
- **data**: Stores the value.
- **next**: Reference to the next node.
- **prev**: Reference to the previous node.

#### Step 2: Doubly Linked List Class (Skeleton)

```java
class DoublyLinkedList {
    DoublyNode head;

    // Constructor to initialize the doubly linked list
    public DoublyLinkedList() {
        head = null;
    }

    // Method to insert a node at the head
    public void insertAtHead(int data) {
        DoublyNode newNode = new DoublyNode(data);
        if (head != null) {
            head.prev = newNode;
            newNode.next = head;
        }
        head = newNode;
    }

    // Other methods will be added here
}
```

---

#### Insertion Operation: Breakdown

##### Insert at the Head

```java
public void insertAtHead(int data) {
    DoublyNode newNode = new DoublyNode(data);
    if (head != null) {
        head.prev = newNode;    // Set current head's previous to new node
        newNode.next = head;    // Set new node's next to current head
    }
    head = newNode;             // Update head to new node
}
```
- **Time Complexity**: O(1)

##### Insert at the Tail

```java
public void insertAtTail(int data) {
    DoublyNode newNode = new DoublyNode(data);
    if (head == null) {
        head = newNode;
        return;
    }
    DoublyNode temp = head;
    while (temp.next != null) {
        temp = temp.next;      // Traverse to the last node
    }
    temp.next = newNode;        // Link last node to new node
    newNode.prev = temp;        // Link new node back to last node
}
```
- **Time Complexity**: O(n)

##### Insert at a Specific Position

```java
public void insertAtPosition(int data, int position) {
    DoublyNode newNode = new DoublyNode(data);
    if (position == 1) {
        insertAtHead(data);
        return;
    }
    DoublyNode temp = head;
    for (int i = 1; i < position - 1 && temp != null; i++) {
        temp = temp.next;
    }
    if (temp != null) {
        newNode.next = temp.next;
        newNode.prev = temp;
        if (temp.next != null) {
            temp.next.prev = newNode;
        }
        temp.next = newNode;
    }
}
```
- **Time Complexity**: O(n)

---

#### Deletion Operation: Breakdown

##### Delete at the Head

```java
public void deleteAtHead() {
    if (head == null) return;
    if (head.next != null) {
        head.next.prev = null;   // Remove reference to the current head
    }
    head = head.next;            // Update head to the next node
}
```
- **Time Complexity**: O(1)

##### Delete at the Tail

```java
public void deleteAtTail() {
    if (head == null) return;
    if (head.next == null) {
        head = null;
        return;
    }
    DoublyNode temp = head;
    while (temp.next != null) {
        temp = temp.next;      // Traverse to the last node
    }
    temp.prev.next = null;      // Remove the last node
}
```
- **Time Complexity**: O(n)

##### Delete at a Specific Position

```java
public void deleteAtPosition(int position) {
    if (head == null) return;
    if (position == 1) {
        deleteAtHead();
        return;
    }
    DoublyNode temp = head;
    for (int i = 1; i < position && temp != null; i++) {
        temp = temp.next;
    }
    if (temp == null) return;
    if (temp.next != null) {
        temp.next.prev = temp.prev;
    }
    if (temp.prev != null) {
        temp.prev.next = temp.next;
    }
}
```
- **Time Complexity**: O(n)

---

#### Traversal Operation: Breakdown

##### Forward Traversal

```java
public void traverseForward() {
    DoublyNode temp = head;
    while (temp != null) {
        System.out.print(temp.data + " <-> ");
        temp = temp.next;         // Move to the next node
    }
    System.out.println("null");
}
```
- **Time Complexity**: O(n)

##### Backward Traversal

To perform backward traversal, we first need to reach the last node.

```java
public void traverseBackward() {
    if (head == null) return;
    DoublyNode temp = head;
    while (temp.next != null) {
        temp = temp.next;         // Traverse to the last node
    }
    while (temp != null) {
        System.out.print(temp.data + " <-> ");
        temp = temp.prev;         // Move to the previous node
    }
    System.out.println("null");
}
```
- **Time Complexity**: O(n)

---

#### Searching Operation: Breakdown

```java
public boolean search(int key) {
    DoublyNode temp = head;
    while (temp != null) {
        if (temp.data == key) {
            return true;            // Key found
        }
        temp = temp.next;          // Move to the next node
    }
    return false;                   // Key not found
}
```
- **Time Complexity**: O(n)

---

### Sorted Linked List Documentation

A **Sorted Linked List** maintains its elements in a sorted order (ascending or descending). This can be implemented using either singly or doubly linked lists. For simplicity, we'll focus on a **Singly Sorted Linked List**.

#### Advantages:
- **Always Sorted**: Eliminates the need for sorting after each insertion.
- **Efficient Search**: Can potentially terminate early during search operations.

#### Disadvantages:
- **Insertion Overhead**: Inserting elements requires traversal to find the correct position.

---

### Operations in Sorted Linked Lists

#### 1. **Insertion**
Insert elements while maintaining the sorted order.

#### 2. **Deletion**
Remove elements while maintaining the sorted order.

#### 3. **Traversal**
Access elements in sorted order.

#### 4. **Searching**
Efficiently locate elements due to the sorted nature.

---

### Sorted Linked List Implementation in Java

We'll implement a **Singly Sorted Linked List** with essential operations.

#### Step 1: Node Class

```java
class SortedNode {
    int data;
    SortedNode next;

    // Constructor to initialize node data
    public SortedNode(int data) {
        this.data = data;
        this.next = null;
    }
}
```

#### Step 2: Sorted Linked List Class (Skeleton)

```java
class SortedLinkedList {
    SortedNode head;

    // Constructor to initialize the sorted linked list
    public SortedLinkedList() {
        head = null;
    }

    // Method to insert a node while maintaining sorted order
    public void insertSorted(int data) {
        SortedNode newNode = new SortedNode(data);
        if (head == null || head.data >= newNode.data) {
            newNode.next = head;
            head = newNode;
        } else {
            SortedNode current = head;
            while (current.next != null && current.next.data < newNode.data) {
                current = current.next;
            }
            newNode.next = current.next;
            current.next = newNode;
        }
    }

    // Other methods will be added here
}
```

---

#### Insertion Operation: Breakdown

##### Insert in Sorted Order

```java
public void insertSorted(int data) {
    SortedNode newNode = new SortedNode(data);
    // Case 1: Empty list or new node should be new head
    if (head == null || head.data >= newNode.data) {
        newNode.next = head;
        head = newNode;
    } else {
        // Case 2: Find the position to insert
        SortedNode current = head;
        while (current.next != null && current.next.data < newNode.data) {
            current = current.next;          // Traverse to find insertion point
        }
        newNode.next = current.next;         // Link new node to next node
        current.next = newNode;              // Link previous node to new node
    }
}
```
- **Time Complexity**: O(n)

---

#### Deletion Operation: Breakdown

##### Delete a Node by Value

```java
public void deleteNode(int key) {
    if (head == null) return;

    // If the head needs to be deleted
    if (head.data == key) {
        head = head.next;
        return;
    }

    // Search for the node to be deleted
    SortedNode current = head;
    while (current.next != null && current.next.data != key) {
        current = current.next;
    }

    // If the node was not found
    if (current.next == null) return;

    // Delete the node
    current.next = current.next.next;
}
```
- **Time Complexity**: O(n)

---

#### Traversal Operation: Breakdown

```java
public void traverse() {
    SortedNode temp = head;
    while (temp != null) {
        System.out.print(temp.data + " -> ");
        temp = temp.next;           // Move to the next node
    }
    System.out.println("null");
}
```
- **Time Complexity**: O(n)

---

#### Searching Operation: Breakdown

```java
public boolean search(int key) {
    SortedNode temp = head;
    while (temp != null && temp.data <= key) {
        if (temp.data == key) {
            return true;            // Key found
        }
        temp = temp.next;          // Move to the next node
    }
    return false;                   // Key not found
}
```
- **Time Complexity**: O(n) (Can be optimized to stop early due to sorted order)

---

### Comparison: Sorted Linked List vs. Regular Linked List vs. Stack vs. Queue

- **Sorted Linked List**: Maintains elements in a sorted order, making search operations potentially faster. Insertion requires traversal to maintain order (O(n)).
- **Regular Linked List**: Does not maintain any specific order. Offers flexibility in insertion and deletion at any position.
- **Stack**: Last-In-First-Out (LIFO) structure. Operations are limited to the top of the stack with O(1) time complexity.
- **Queue**: First-In-First-Out (FIFO) structure. Operations are limited to the front and rear with O(1) time complexity for insertion and removal.

**Key Differences:**
- **Order Maintenance**: Sorted linked lists maintain order automatically, unlike regular linked lists, stacks, and queues.
- **Access Patterns**: Stacks and queues restrict access to specific ends, whereas linked lists allow access to any part of the list.
- **Use Cases**: Sorted linked lists are ideal for applications requiring ordered data, such as priority queues.

---

### Big O Notation and Uses

Understanding the **Big O Notation** is crucial for analyzing the efficiency of data structures and algorithms.

#### Big O Notation for Linked Lists Operations

| Operation            | Singly Linked List | Doubly Linked List | Sorted Linked List |
|----------------------|--------------------|--------------------|--------------------|
| Insertion at Head    | O(1)               | O(1)               | O(1)               |
| Insertion at Tail    | O(n)               | O(n)               | O(n)               |
| Insertion at Position| O(n)               | O(n)               | O(n)               |
| Deletion at Head     | O(1)               | O(1)               | O(1)               |
| Deletion at Tail     | O(n)               | O(n)               | O(n)               |
| Deletion at Position | O(n)               | O(n)               | O(n)               |
| Search               | O(n)               | O(n)               | O(n)               |
| Traversal            | O(n)               | O(n)               | O(n)               |

**Use Cases Based on Big O:**
- **Frequent Insertions/Deletions at Head**: Use linked lists for O(1) operations.
- **Need for Bidirectional Traversal**: Use doubly linked lists despite extra memory overhead.
- **Maintaining Sorted Order**: Use sorted linked lists for applications like priority queues.

---

### Uses of Linked Lists

- **Dynamic Memory Allocation**: Efficient memory usage when the size of data structures changes frequently.
- **Implementing Other Data Structures**: Stacks, queues, and graphs can be efficiently implemented using linked lists.
- **Real-Time Applications**: Systems that require frequent insertions and deletions, such as operating systems and dynamic memory management.
- **Music Players**: Managing playlists where songs can be added or removed dynamically.

---

### Example Usage Scenarios

1. **Browser History**: Implemented using a doubly linked list to allow backward and forward navigation.
2. **Undo Functionality**: Stacks (which can be implemented using linked lists) are used to keep track of actions.
3. **Image Viewer**: A circular doubly linked list can manage images, allowing infinite scrolling forward and backward.

---

### Summary

Linked lists are versatile data structures with various implementations tailored to specific needs:

- **Singly Linked Lists**: Simple and efficient for single-direction traversal.
- **Doubly Linked Lists**: Offer bidirectional traversal and more efficient deletions.
- **Sorted Linked Lists**: Maintain elements in a sorted order, beneficial for search-intensive applications.
