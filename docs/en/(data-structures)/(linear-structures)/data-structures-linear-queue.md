---
title: "Introduction to Queues"
---

A **Queue** is a linear data structure that follows the **First-In-First-Out (FIFO)** principle. This means that the first element added to the queue will be the first one to be removed. Queues are analogous to real-life queues, such as a line of people waiting for service.

### Queue Operations

A typical queue supports the following core operations:

1. **Enqueue**: Adds an element to the end of the queue.
2. **Dequeue**: Removes and returns the element at the front of the queue.
3. **Front (Peek)**: Retrieves the front element without removing it.
4. **isEmpty**: Checks if the queue is empty.
5. **Size**: Returns the number of elements in the queue.

---

### Queue Implementation in Java

### [Full Code Example](https://github.com/universitysjp/data-structures-and-algorithms/blob/main/Data%20Structures/Linear/Queue/Queue.java)

#### 1. **Enqueue Operation**

The `enqueue` method adds an element to the rear of the queue. It checks if the queue is full before adding the element. If the rear reaches the end of the array, it wraps around to the beginning.

```java
public void enqueue(int value) {
    if (nItems == maxSize) {
        System.out.println("Queue is full");
    } else {
        if (rear == maxSize - 1) {
            rear = -1; // Wrap around
        }
        queueArray[++rear] = value;
        nItems++;
    }
}
```

**Explanation:**
- **Check if Full**: If `nItems` equals `maxSize`, the queue is full.
- **Wrap Around**: If `rear` is at the last index, reset it to `-1` to wrap around.
- **Add Element**: Increment `rear` and add the new value.
- **Increment Count**: Increase `nItems` to reflect the new element.

#### 2. **Dequeue Operation**

The `dequeue` method removes and returns the front element of the queue. It checks if the queue is empty before attempting to remove an element. If the front reaches the end of the array, it wraps around.

```java
public int dequeue() {
    if (nItems == 0) {
        System.out.println("Queue is empty");
        return -1;
    } else {
        int temp = queueArray[front++];
        if (front == maxSize) {
            front = 0; // Wrap around
        }
        nItems--;
        return temp;
    }
}
```

**Explanation:**
- **Check if Empty**: If `nItems` is `0`, the queue is empty.
- **Retrieve Element**: Store the front element in `temp`.
- **Increment Front**: Move `front` forward; wrap around if necessary.
- **Decrement Count**: Decrease `nItems` to reflect the removal.
- **Return Element**: Return the dequeued element.

#### 3. **Front (Peek) Operation**

The `front` method returns the front element without removing it from the queue.

```java
public int front() {
    if (nItems == 0) {
        System.out.println("Queue is empty");
        return -1;
    } else {
        return queueArray[front];
    }
}
```

**Explanation:**
- **Check if Empty**: If `nItems` is `0`, the queue is empty.
- **Return Front**: Return the element at the `front` index.

#### 4. **isEmpty Operation**

The `isEmpty` method checks whether the queue is empty.

```java
public boolean isEmpty() {
    return (nItems == 0);
}
```

**Explanation:**
- **Check Count**: Returns `true` if `nItems` is `0`, otherwise `false`.

#### 5. **Size Operation**

The `size` method returns the number of elements currently in the queue.

```java
public int size() {
    return nItems;
}
```

**Explanation:**
- **Return Count**: Returns the value of `nItems`.

---

## 2. Introduction to Circular Queues

A **Circular Queue** is a variation of a standard queue where the last position is connected back to the first position, forming a circle. This design efficiently utilizes the available space by allowing the queue to wrap around, preventing the waste of space that can occur in a linear queue.

### Circular Queue Operations

The operations in a Circular Queue are similar to those in a standard queue but are adjusted to handle the circular nature:

1. **Enqueue**: Adds an element to the rear of the queue. Wraps around if the rear reaches the end.
2. **Dequeue**: Removes and returns the front element. Wraps around if the front reaches the end.
3. **Front (Peek)**: Retrieves the front element without removing it.
4. **isEmpty**: Checks if the queue is empty.
5. **isFull**: Checks if the queue is full.
6. **Size**: Returns the number of elements in the queue.

---

### Circular Queue Implementation in Java

### [Full Code Example](https://github.com/universitysjp/data-structures-and-algorithms/blob/main/Data%20Structures/Linear/Queue/CircularQueue.java)

#### 1. **Enqueue Operation**

The `enqueue` method adds an element to the rear of the circular queue. It wraps around to the beginning if the rear reaches the end of the array.

```java
public void enqueue(int value) {
    if (nItems == maxSize) {
        System.out.println("Circular Queue is full");
    } else {
        rear = (rear + 1) % maxSize;
        queueArray[rear] = value;
        nItems++;
    }
}
```

**Explanation:**
- **Check if Full**: If `nItems` equals `maxSize`, the queue is full.
- **Calculate New Rear**: Increment `rear` and use modulus to wrap around.
- **Add Element**: Insert the new value at the calculated `rear` position.
- **Increment Count**: Increase `nItems` to reflect the new element.

#### 2. **Dequeue Operation**

The `dequeue` method removes and returns the front element of the circular queue. It wraps around to the beginning if the front reaches the end.

```java
public int dequeue() {
    if (nItems == 0) {
        System.out.println("Circular Queue is empty");
        return -1;
    } else {
        int temp = queueArray[front];
        front = (front + 1) % maxSize;
        nItems--;
        return temp;
    }
}
```

**Explanation:**
- **Check if Empty**: If `nItems` is `0`, the queue is empty.
- **Retrieve Element**: Store the front element in `temp`.
- **Calculate New Front**: Increment `front` and use modulus to wrap around.
- **Decrement Count**: Decrease `nItems` to reflect the removal.
- **Return Element**: Return the dequeued element.

#### 3. **Front (Peek) Operation**

The `front` method returns the front element without removing it from the circular queue.

```java
public int front() {
    if (nItems == 0) {
        System.out.println("Circular Queue is empty");
        return -1;
    } else {
        return queueArray[front];
    }
}
```

**Explanation:**
- **Check if Empty**: If `nItems` is `0`, the queue is empty.
- **Return Front**: Return the element at the `front` index.

#### 4. **isEmpty Operation**

The `isEmpty` method checks whether the circular queue is empty.

```java
public boolean isEmpty() {
    return (nItems == 0);
}
```

**Explanation:**
- **Check Count**: Returns `true` if `nItems` is `0`, otherwise `false`.

#### 5. **isFull Operation**

The `isFull` method checks whether the circular queue is full.

```java
public boolean isFull() {
    return (nItems == maxSize);
}
```

**Explanation:**
- **Check Count**: Returns `true` if `nItems` equals `maxSize`, otherwise `false`.

#### 6. **Size Operation**

The `size` method returns the number of elements currently in the circular queue.

```java
public int size() {
    return nItems;
}
```

**Explanation:**
- **Return Count**: Returns the value of `nItems`.

---

## 3. Introduction to Priority Queues

A **Priority Queue** is a special type of queue where each element is associated with a priority. Elements are dequeued based on their priority rather than their insertion order. By default, Java's `PriorityQueue` implements a **min-heap**, where the smallest element has the highest priority.

### Priority Queue Operations

A typical priority queue supports the following core operations:

1. **Add (Enqueue)**: Inserts an element into the priority queue.
2. **Poll (Dequeue)**: Removes and returns the element with the highest priority.
3. **Peek**: Retrieves the element with the highest priority without removing it.
4. **isEmpty**: Checks if the priority queue is empty.
5. **Size**: Returns the number of elements in the priority queue.

---

### Priority Queue Implementation in Java

### [Full Code Example](https://github.com/universitysjp/data-structures-and-algorithms/blob/main/Data%20Structures/Linear/Queue/PriorityQueue.java)

#### 1. **Add (Enqueue) Operation**

The `add` method inserts an element into the priority queue. In a min-heap, elements are ordered such that the smallest element is always at the front.

```java
minHeap.add(30);
minHeap.add(10);
minHeap.add(20);
minHeap.add(40);
minHeap.add(50);
```

**Explanation:**
- **Insert Elements**: Elements are added to the heap, and the heap property is maintained automatically.

#### 2. **Poll (Dequeue) Operation**

The `poll` method removes and returns the element with the highest priority (smallest element in a min-heap).

```java
System.out.println("Removed element: " + minHeap.poll()); // Removes 10
```

**Explanation:**
- **Remove Element**: Removes the smallest element (`10`) from the min-heap.
- **Heap Reorganization**: After removal, the heap is reorganized to maintain the heap property.

#### 3. **Peek Operation**

The `peek` method retrieves the element with the highest priority without removing it.

```java
System.out.println("Front element: " + minHeap.peek()); // Should be 20
```

**Explanation:**
- **Retrieve Element**: Returns the smallest element (`20`) without removing it from the heap.

#### 4. **isEmpty Operation**

The `isEmpty` method checks whether the priority queue is empty.

```java
System.out.println("Is Priority Queue empty? " + minHeap.isEmpty());
```

**Explanation:**
- **Check Status**: Returns `true` if the priority queue is empty, otherwise `false`.

#### 5. **Size Operation**

The `size` method returns the number of elements currently in the priority queue.

```java
System.out.println("Priority Queue size: " + minHeap.size());
```

**Explanation:**
- **Return Count**: Returns the total number of elements in the priority queue.

#### 6. **Max-Heap Using Comparator**

By default, Java's `PriorityQueue` is a min-heap. To create a max-heap, you can provide a custom comparator.

```java
PriorityQueue<Integer> maxHeap = new PriorityQueue<>(Comparator.reverseOrder());

maxHeap.add(30);
maxHeap.add(10);
maxHeap.add(20);
maxHeap.add(40);
maxHeap.add(50);

System.out.println("Removed element from Max-Heap: " + maxHeap.poll()); // Removes 50
System.out.println("Front element in Max-Heap: " + maxHeap.peek()); // Should be 40
```

**Explanation:**
- **Custom Comparator**: `Comparator.reverseOrder()` creates a max-heap where the largest element has the highest priority.
- **Heap Operations**: Similar to the min-heap but with reversed priorities.

---

## 4. Efficiency and Comparison with Other Data Structures

Understanding the efficiency of various data structures is crucial for selecting the right one based on the problem requirements. Below is a comparison of **Stacks**, **Queues**, **Circular Queues**, and **Priority Queues** with other common data structures, along with their time complexities.

### Efficiency and Big-O Notation

#### Stack (Array-Based)

| Operation | Time Complexity |
|-----------|-----------------|
| Push      | O(1)            |
| Pop       | O(1)            |
| Peek      | O(1)            |
| isEmpty   | O(1)            |
| Size      | O(1)            |

#### Queue (Array-Based)

| Operation | Time Complexity |
|-----------|-----------------|
| Enqueue   | O(1)            |
| Dequeue   | O(1)            |
| Front     | O(1)            |
| isEmpty   | O(1)            |
| Size      | O(1)            |

#### Circular Queue

| Operation | Time Complexity |
|-----------|-----------------|
| Enqueue   | O(1)            |
| Dequeue   | O(1)            |
| Front     | O(1)            |
| isEmpty   | O(1)            |
| isFull    | O(1)            |
| Size      | O(1)            |

#### Priority Queue

| Operation | Time Complexity (Min-Heap) | Time Complexity (Max-Heap) |
|-----------|----------------------------|----------------------------|
| Enqueue   | O(log n)                   | O(log n)                   |
| Dequeue   | O(log n)                   | O(log n)                   |
| Peek      | O(1)                       | O(1)                       |
| isEmpty   | O(1)                       | O(1)                       |
| Size      | O(1)                       | O(1)                       |

### Comparison with Other Data Structures

#### 1. **Arrays**

- **Access Time**: O(1) for random access.
- **Insertion/Deletion**: O(n) unless adding/removing from the end.
- **Use Case**: Suitable for scenarios requiring frequent access to elements by index.

#### 2. **Linked Lists**

- **Access Time**: O(n) for accessing elements.
- **Insertion/Deletion**: O(1) if the position is known.
- **Use Case**: Ideal for applications with frequent insertions and deletions.

#### 3. **Trees (e.g., Binary Search Trees)**

- **Access Time**: O(log n) for balanced trees.
- **Insertion/Deletion**: O(log n) for balanced trees.
- **Use Case**: Best for hierarchical data and efficient search operations.

#### 4. **Hash Tables**

- **Access Time**: O(1) average case for insertions, deletions, and lookups.
- **Collision Handling**: Additional complexity due to collisions.
- **Use Case**: Optimal for scenarios requiring fast lookups, such as dictionaries or caches.

#### 5. **Graphs**

- **Access Time**: Varies based on representation (adjacency list vs. matrix).
- **Use Case**: Suitable for modeling complex relationships like networks, social connections, etc.

---

### When to Use Which Data Structure

- **Stack**: Use when you need LIFO access, such as undo mechanisms, function call management, or expression evaluation.
- **Queue**: Ideal for FIFO access needs, such as task scheduling, breadth-first search, or handling asynchronous data.
- **Circular Queue**: Best when you need a fixed-size queue with efficient space utilization, like buffering data streams.
- **Priority Queue**: Suitable for scenarios where elements need to be processed based on priority, such as job scheduling, Dijkstra's algorithm, or managing events in simulations.

