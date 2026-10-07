---
title: "Stack - The LIFO Data Structure"
---

## Overview
A **Stack** is a linear data structure that follows the **Last-In-First-Out (LIFO)** principle. Think of it like a stack of plates - you can only add or remove plates from the top. Stacks are fundamental programmer's tools used for memory management, expression evaluation, and algorithm implementation.

## 📚 Table of Contents
- [Key Characteristics](#key-characteristics)
- [Stack Operations](#stack-operations)
- [Implementation](#implementation)
- [Applications](#applications)
- [Complexity Analysis](#complexity-analysis)
- [Study Notes](#study-notes-for-students)
- [Practice Problems](#practice-problems)

## Key Characteristics

### 🔹 **LIFO Principle**
- **Last In, First Out**: The most recently added element is the first to be removed
- Only the **top element** is accessible at any time
- **Restricted access**: Cannot access elements in the middle

### 🔹 **Abstract Data Type**
- More of a **programmer's tool** than a real-world data model
- **Interface-focused**: Defined by operations, not physical representation
- Can be implemented using arrays or linked lists

### 🔹 **Single Access Point**
- All operations occur at the **top** of the stack
- **Push**: Add to top
- **Pop**: Remove from top

## Stack Operations

### 📁 [Complete Implementation](https://github.com/universitysjp/data-structures-and-algorithms/blob/main/Data%20Structures/Linear/Stack/Stack.java)

### Core Operations

#### 1. **Push** - Add Element to Top
```java
public void push(int value) {
    if (top == maxSize - 1) {
        System.out.println("Stack Overflow!");
    } else {
        stackArray[++top] = value;
    }
}
```
**Time Complexity**: O(1) | **Space Complexity**: O(1)

#### 2. **Pop** - Remove and Return Top Element
```java
public int pop() {
    if (top == -1) {
        System.out.println("Stack Underflow!");
        return -1;
    } else {
        return stackArray[top--];
    }
}
```
**Time Complexity**: O(1) | **Space Complexity**: O(1)

#### 3. **Peek/Top** - View Top Element Without Removal
```java
public int peek() {
    if (top == -1) {
        System.out.println("Stack is empty");
        return -1;
    } else {
        return stackArray[top];
    }
}
```
**Time Complexity**: O(1) | **Space Complexity**: O(1)

#### 4. **isEmpty** - Check if Stack is Empty
```java
public boolean isEmpty() {
    return (top == -1);
}
```
**Time Complexity**: O(1) | **Space Complexity**: O(1)

#### 5. **size** - Get Number of Elements
```java
public int size() {
    return top + 1;
}
```
**Time Complexity**: O(1) | **Space Complexity**: O(1)

### Visual Representation

```
Stack Operations:

Push(10):           Push(20):           Pop():              Peek():

    │     │            │  20 │ <- top      │     │            │  10 │ <- top
    │  10 │ <- top      │  10 │            │  10 │ <- top      │     │
    └─────┘            └─────┘            └─────┘            └─────┘

    Size: 1            Size: 2            Size: 1            Size: 1
                                         Returns: 20         Returns: 10
```

## Implementation

### 📁 [View Complete Code](https://github.com/universitysjp/data-structures-and-algorithms/blob/main/Data%20Structures/Linear/Stack/Stack.java)

### Array-Based Implementation
```java
class StackStructure {
    private int maxSize;        // Maximum stack size
    private int[] stackArray;   // Array to store elements
    private int top;           // Index of top element

    public StackStructure(int size) {
        maxSize = size;
        stackArray = new int[maxSize];
        top = -1;              // Empty stack
    }

    // Implementation of all operations...
}
```

### Key Implementation Details
- **Top pointer**: Tracks the index of the top element
- **Boundary checking**: Prevents stack overflow and underflow
- **Efficient operations**: All operations are O(1)

## Applications

### 🛠️ **Programming Applications**

#### 1. **Delimiter Matching**
Check if parentheses, brackets, and braces are balanced:
```java
public static boolean isBalanced(String expression) {
    Stack<Character> stack = new Stack<>();
    for (char ch : expression.toCharArray()) {
        if (ch == '(' || ch == '[' || ch == '{') {
            stack.push(ch);
        } else if (ch == ')' || ch == ']' || ch == '}') {
            if (stack.isEmpty()) return false;
            char top = stack.pop();
            if (!isMatchingPair(top, ch)) return false;
        }
    }
    return stack.isEmpty();
}
```

#### 2. **Expression Evaluation**
- **Infix to Postfix conversion**
- **Postfix expression evaluation**
- **Calculator implementation**

#### 3. **Function Call Management**
- **Call stack**: Track function calls and local variables
- **Recursion**: Manage recursive function calls
- **Return address storage**

#### 4. **Backtracking Algorithms**
- **Undo operations**: Text editors, games
- **Path finding**: Maze solving, tree traversal
- **State management**: Decision trees

### 🌐 **Real-World Applications**

#### System-Level
- **Memory management**: Stack segment in process memory
- **Processor architecture**: Hardware stack for subroutines
- **Compiler design**: Syntax analysis and code generation

#### Application-Level
- **Web browsers**: Back button functionality
- **Text editors**: Undo/Redo operations
- **Game development**: State management, move history

## Complexity Analysis

| Operation | Time Complexity | Space Complexity | Notes |
|-----------|----------------|------------------|-------|
| **Push** | O(1) | O(1) | Constant time insertion |
| **Pop** | O(1) | O(1) | Constant time removal |
| **Peek** | O(1) | O(1) | No data movement |
| **isEmpty** | O(1) | O(1) | Simple boolean check |
| **size** | O(1) | O(1) | Return counter value |

### Space Complexity
- **Overall**: O(n) where n is the maximum number of elements
- **Per operation**: O(1) additional space

## Study Notes for Students

### 🎯 **Key Concepts to Master**

#### 1. **LIFO Principle Understanding**
- Visualize the stack as a physical stack of objects
- Only the top element is accessible
- Order of removal is reverse of insertion order

#### 2. **Stack vs Other Structures**
```
Stack (LIFO):    Queue (FIFO):    Array (Random Access):
   │ 3 │ <- top     │ 1 │ <- front    │ 0 │ 1 │ 2 │ 3 │
   │ 2 │           │ 2 │              ↑   ↑   ↑   ↑
   │ 1 │           │ 3 │ <- rear    any element accessible
   └───┘           └───┘
```

#### 3. **Implementation Choices**
- **Array-based**: Fixed size, efficient memory usage
- **Linked list-based**: Dynamic size, more memory overhead
- **Built-in classes**: Language-provided implementations

### 📖 **Common Programming Patterns**

#### Stack-based Problem Solving
1. **Identify LIFO behavior** in the problem
2. **Push** when encountering opening elements
3. **Pop** when encountering closing elements
4. **Check stack state** for validation

#### Typical Algorithm Structure
```java
Stack<Type> stack = new Stack<>();
for (each element in input) {
    if (opening condition) {
        stack.push(element);
    } else if (closing condition) {
        if (stack.isEmpty()) {
            // Handle error
        }
        Type item = stack.pop();
        // Process item
    }
}
// Check final stack state
```

### ⚠️ **Common Mistakes**

#### 1. **Stack Overflow/Underflow**
```java
// WRONG: No boundary checking
public void push(int value) {
    stackArray[++top] = value;  // May exceed array bounds
}

// CORRECT: Check bounds
public void push(int value) {
    if (top == maxSize - 1) {
        throw new StackOverflowException();
    }
    stackArray[++top] = value;
}
```

#### 2. **Forgetting to Check Empty Stack**
```java
// WRONG: Pop without checking
int value = stack.pop();  // May cause underflow

// CORRECT: Check before pop
if (!stack.isEmpty()) {
    int value = stack.pop();
}
```

### 🧠 **Problem-Solving Strategies**

#### When to Use Stacks
- ✅ Need to process data in **reverse order**
- ✅ **Matching pairs** problems (parentheses, tags)
- ✅ **Backtracking** algorithms
- ✅ **Recursive** algorithm simulation
- ✅ **Undo/Redo** functionality

#### Alternative Considerations
- ❌ Need **random access** → Use Array/ArrayList
- ❌ Need **FIFO behavior** → Use Queue
- ❌ Need **sorted access** → Use Priority Queue
- ❌ Need **key-based access** → Use HashMap

## Practice Problems

### 🟢 **Beginner Level**
1. **Valid Parentheses**: Check if string has balanced parentheses
2. **Reverse String**: Use stack to reverse a string
3. **Min Stack**: Design stack that supports getMin() in O(1)
4. **Stack using Queues**: Implement stack using two queues
5. **Baseball Game**: Calculate final score using stack operations

### 🟡 **Intermediate Level**
1. **Evaluate Postfix Expression**: Calculate result of postfix notation
2. **Infix to Postfix**: Convert infix expression to postfix
3. **Next Greater Element**: Find next greater element for each array element
4. **Valid Parentheses II**: Handle different types of brackets
5. **Simplify Path**: Simplify Unix-style file path

### 🔴 **Advanced Level**
1. **Largest Rectangle in Histogram**: Find largest rectangular area
2. **Trapping Rain Water**: Calculate trapped rainwater using stack
3. **Calculator**: Implement basic calculator with +, -, *, /
4. **Remove K Digits**: Remove k digits to make smallest number
5. **Asteroid Collision**: Simulate asteroid collisions

## Common Interview Questions

### Conceptual Questions
1. **Explain LIFO principle** and provide real-world examples
2. **Compare stack vs queue** - when to use each?
3. **Array vs LinkedList implementation** - pros and cons?
4. **Stack overflow** - causes and prevention

### Coding Questions
1. **Implement stack** from scratch using arrays
2. **Valid parentheses** checker
3. **Evaluate postfix** expression
4. **Next greater element** finder

## Related Topics
- [**Queues**](./data-structures-linear-queue) - FIFO counterpart to stacks
- [**Recursion**](./algorithms-recursion) - Uses implicit stack
- **Expression Evaluation** - Stack applications
- [**Backtracking**](./algorithms-backtracking) - Stack-based algorithms
- [**Tree Traversal**](./data-structures-non-linear-tree) - Stack-based traversals

```java
// Pop operation
public int pop() {
    if (top == -1) {
        System.out.println("Stack is empty");
        return -1;  // Return -1 if stack is empty
    } else {
        return stackArray[top--];  // Return element and decrement top
    }
}
```

### 3. **Peek/Top Operation**

The `peek` method returns the top element of the stack without removing it. It checks if the stack is empty and returns the top element.

```java
// Peek operation
public int peek() {
    if (top == -1) {
        System.out.println("Stack is empty");
        return -1;  // Return -1 if stack is empty
    } else {
        return stackArray[top];  // Return top element
    }
}
```

### 4. **isEmpty Operation**

The `isEmpty` method checks whether the stack is empty. It returns `true` if the stack has no elements.

```java
// isEmpty operation
public boolean isEmpty() {
    return (top == -1);  // True if stack is empty
}
```

### 5. **Size Operation**

The `size` method returns the current number of elements in the stack. It calculates this by returning the value of `top + 1`.

```java
// Size operation
public int size() {
    return top + 1;  // Size is top index + 1
}
```

### Efficiency and Comparison with Other Data Structures

The efficiency of stack operations depends on the underlying implementation. When implemented using an array, the stack has:

- **Push**: O(1) – Constant time for adding an element (if the stack isn't full).
- **Pop**: O(1) – Constant time for removing an element.
- **Peek**: O(1) – Constant time for viewing the top element.
- **Space Complexity**: O(n) – Linear space for storing `n` elements.

However, stacks can also be implemented using linked lists, which may offer more flexibility at the cost of slightly increased overhead due to dynamic memory allocation.

#### Comparison with Other Data Structures:

1. **Arrays**: Arrays allow random access to elements in O(1) time, but resizing and insertion/removal (other than from the end) can be costly, O(n). Stacks restrict operations to the top, leading to more predictable performance.

2. **Queues**: A queue follows a First-In-First-Out (FIFO) principle, which is opposite to the stack's LIFO behavior. Operations like enqueue and dequeue in queues have O(1) complexity when implemented with linked lists or circular arrays.

3. **Linked Lists**: Linked lists provide flexibility in terms of dynamic sizing and efficient insertion/removal from both ends. However, accessing elements in a linked list takes O(n) time due to the need to traverse the list.

4. **Trees**: Trees, like binary search trees, allow hierarchical data organization with O(log n) insertion, deletion, and lookup times (for balanced trees), making them more suited for search-heavy applications compared to stacks.

5. **Hash Tables**: Hash tables provide O(1) average time complexity for insertions, deletions, and lookups, but are more complex in terms of collision handling and aren't ordered like stacks.

### Big-O Notation Summary for Stack Operations

| Operation | Array (Stack) | Linked List (Stack) | Time Complexity |
| --------- | ------------- | ------------------- | --------------- |
| Push      | O(1)          | O(1)                | O(1)            |
| Pop       | O(1)          | O(1)                | O(1)            |
| Peek      | O(1)          | O(1)                | O(1)            |
| isEmpty   | O(1)          | O(1)                | O(1)            |
| Size      | O(1)          | O(n)                | O(n) (for linked list) |

