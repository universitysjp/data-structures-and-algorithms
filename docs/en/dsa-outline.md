---
title: "Data Structures and Algorithms Lecture 1"
---

You're looking for a comprehensive breakdown of all topics and subtopics covered across the provided resources, excluding the module outline. Here is a detailed list of the content, structured to highlight the hierarchy and key concepts:

### Data Structures and Algorithms Lecture 1

*   **Introduction to Data Structures and Algorithms**
    *   **Data**
        *   Data are raw facts.
        *   Different views of data.
        *   Data types.
    *   **Introduction** (to Data Structures and Algorithms)
        *   A **data structure** is an arrangement of data in a computer’s memory or sometimes on a disk.
            *   Examples include **arrays, linked lists, stacks, binary trees, and hash tables**.
        *   **Algorithms manipulate the data in these structures** in various ways, such as searching for a particular data item and sorting the data.
    *   **What sort of problems can be solved using this knowledge?**
        *   Real-world data storage.
        *   Programmer’s tools.
        *   Real-world Modeling.
    *   **Properties of Data Structure**
    *   **Definition of Algorithm**
    *   **Characteristics of Algorithm**
    *   **Difference of Algorithm and Pseudocode**

### Data Structures and Algorithms Lecture 10 (Recursion)

*   **Regular Method Calling**
    *   Purpose of a method (function) is to perform a specific task.
    *   Methods are executed by being called, typically by the `main` method in Java.
    *   A method can be called by another method that was itself called by `main`.
*   **Method Recursion**
    *   A method (function) can be called by itself.
    *   This means a method calling statement is included inside the method, with the name of the calling method being itself.
    *   This concept is called **method/function recursion**.
*   **Why Recursion?**
    *   Sometimes, the best way to solve a problem is by solving a smaller version of the exact same problem first.
    *   Some functional programming languages (e.g., Haskell, Scheme, Erlang) rely entirely on recursion for code repetition, lacking looping constructs.
    *   In recursion, the problem is divided into sub-problems of the same type, which are solved first, and then their results are combined to solve the bigger problem. This is also known as **divide-and-conquer**.
*   **General Recursive Design Strategy**
    *   **Identify the base case(s)**: Input(s) for which the method produces a result without recurring.
    *   **Determine the general case(s)**: Input(s) where the problem is expressed as a smaller version of itself (calls itself).
    *   **Devise a solution combining strategy**.
    *   **Example: Factorial** `n! = n(n − 1)!` for `n > 0` (General Case), `0! = 1` (Base Case).
*   **Triangular Numbers**
    *   Counts objects arranged in an equilateral triangle. Sequence: `0, 1, 3, 6, 10, 15, 21, 28, 36, 45, 55, 66, 78, …`.
    *   Recursive calculation: `Triangle(n) = Triangle(n-1) + n`.
    *   Base case: `Triangle(1) = 1`.
*   **Factorials**
    *   Similar to triangular numbers but use multiplication.
    *   Regular case: `Factorial(n) = n * Factorial(n-1)`.
    *   Base case: `Factorial(1) = 1`.
*   **Anagrams**
    *   A permutation is an arrangement of things in a definite order.
    *   Anagrams are all possible permutations of letters from an original word (e.g., "cat" yields "cat, cta, atc, act, tca, tac").
    *   The number of possibilities is the factorial of the number of letters (e.g., 3 letters = 3! = 6).
    *   **Programmatic approach**: Anagram the rightmost `n-1` letters, rotate all `n` letters, and repeat these steps `n` times. Rotation shifts letters left, with the leftmost moving to the right.
*   **Binary Search**
*   **Recursive Binary Search**
    *   Does not require changing `lowerBound` or `upperBound` variables directly; instead, the `find()` method is recursively called with new values as arguments.
    *   The loop structure is replaced by recursive calls.
*   **Divide-and-Conquer Algorithms**
    *   Recursive binary search is an example of this approach.
    *   A large problem is divided into smaller problems, which are then further divided until a simple, easily solvable base case is reached.
*   **Fibonacci Numbers**
    *   Sequence: `0, 1, 1, 2, 3, 5, 8, 13, 21, 34, ...`.
    *   Each number is the sum of the two preceding ones: `Fn = Fn-1 + Fn-2`.
    *   Base cases: `F0 = 0`, `F1 = 1`.
*   **The Towers of Hanoi**
    *   An ancient puzzle with disks on three columns.
    *   Objective: Transfer all disks from column A to column C.
    *   Rules: Only one disk can be moved at a time, and no disk can be placed on a smaller disk.

### Data Structures and Algorithms Lecture 11 (Binary Trees)

*   **Binary Trees**
    *   **Ordered Array vs. Linked List**
        *   Linked Lists have slow searching but quick insertion/deletion.
        *   Ordered Arrays have slow insertion but quick searching.
        *   Trees combine advantages, offering quick searching (like ordered arrays) and quick insertion/deletion (like linked lists).
    *   Binary trees are fundamental data storage structures.
*   **What is a Tree?**
    *   A subset of a more general category called a graph.
    *   Nodes represent entities (e.g., people, parts), and edges represent relationships.
    *   The **root** is the node at the top; there's only one root.
    *   **Children** are nodes connected below a given node.
*   **Tree Terminology**
    *   **Root**: The single node at the top of the tree.
    *   **Parent**: The node directly above another node, connected by an upward edge.
    *   **Child**: Nodes connected directly below a given node by a downward edge.
    *   **Leaf**: A node with no children.
    *   **Subtree**: Any node can be considered the root of a subtree, encompassing its descendants.
    *   **Visiting**: Program control arriving at a node.
    *   **Traversing**: Visiting all nodes in a specified order.
    *   **Levels**: How many generations a node is from the root.
    *   **Keys**: The data value held by a node.
    *   For a structure to be a tree, there must be exactly one path from the root to any other node.
*   **Binary Trees** (Specific Definition)
    *   Every node can have at most two children.
    *   Children are specifically called the **left child** and the **right child**.
    *   A node can have only a left child, only a right child, or no children (making it a leaf).
*   **Binary Search Trees**
    *   A node's left child must have a key less than its parent.
    *   A node's right child must have a key greater than or equal to its parent.
*   **Program Representation of Tree** (in Java)
    *   A `Node` class is created (similar to a Linked List node), which is self-referential.
    *   A `Tree` class is defined using the `Node` class, primarily containing a reference to the `root`.
    *   Methods like `find()`, `insert()`, and `delete()` are added to the `Tree` class.
*   **Finding a Node**
    *   Time Complexity: **O(logN)**.
*   **Inserting a New Node**
*   **Inserting Nodes** (Example for drawing a tree)

### Data Structures and Algorithms Lecture 12 (Binary Trees II)

*   **Traversing the Tree**
    *   Visiting each node exactly once in a specified order.
    *   Tree traversals are naturally recursive.
    *   Three simple ways to traverse a tree:
        *   **Pre-order**
        *   **In-order**
        *   **Post-order**
*   **In-Order Traversal**
    *   Nodes are visited in ascending order of their key values.
    *   Recursive method steps: 1. Traverse left subtree, 2. Visit the node, 3. Traverse right subtree.
    *   The node is visited **in the middle** of the process.
*   **Pre-Order Traversal**
    *   Node is visited **before** traversing left or right sub-trees.
    *   Recursive method steps: 1. Visit the node, 2. Traverse left subtree, 3. Traverse right subtree.
*   **Post-Order Traversal**
    *   Node is visited **after** visiting all left and right subtrees.
    *   Recursive method steps: 1. Traverse left subtree, 2. Traverse right subtree, 3. Visit the node.
*   **Deleting a Node**
    *   First, find the node to be deleted.
    *   Three cases for deletion:
        *   1. The node is a **leaf** (no children).
        *   2. The node has **one child**.
        *   3. The node has **two children**.

### Data Structures and Algorithms Lecture 2 (Arrays)

*   **Arrays**
    *   A collection of a fixed number of elements.
    *   Each element is identified by at least one array index or key.
    *   Length is fixed once created.
*   **Creating an Array**
    *   Examples include defining a reference and then creating (`int[] intArray; intArray = new int;`) or combining (`int[] intArray = new int;`).
*   **Initialization**
    *   Elements can be initialized directly with values (`int[] intArray = { ... };`) or individually by index (`intArray = 10;`).
*   **A Sample Program** (demonstrating array operations)
*   **Analysis of the Program**
    *   Creating an array.
    *   Placing data items.
    *   Searching for an item.
    *   Displaying items.
    *   Removing an item.
    *   Displaying remaining items.
*   **Insertion** (in an array)
    *   Done using normal array syntax (e.g., `arr = 33;`).
    *   `nElems` variable tracks the number of items.
*   **Searching** (in an array)
    *   Compares each element with a `searchKey`.
    *   Stops if found, or determines not found if the loop finishes without a match.
*   **Deletion** (in an array)
    *   Starts with a search for the item.
    *   If found, elements with higher indices are shifted down to fill the gap.
    *   `nElems` is decremented.
*   **Display** (of an array)
    *   Stepping through the array and accessing each element with `arr[j]`.

### Data Structures and Algorithms Lecture 3 (Searching Algorithms)

*   **Searching**
*   **Linear Search**
    *   The default algorithm for **unordered arrays**.
    *   Involves stepping through the array and comparing each element until a match is found.
*   **Binary Search**
    *   Performed with **ordered arrays**.
    *   Much faster than linear search for large arrays.
    *   Process: Set `Lower Bound` (first index) and `Upper Bound` (last index). Calculate `Middle` index. Compare `Search Key` with the middle item. Adjust bounds (`lowerBound` or `upperBound`) based on comparison (if search key is less, search left; if greater, search right) and repeat until found or bounds cross.
    *   Program examples provided.

### Data Structures and Algorithms Lecture 4 (Sorting Algorithms- Part I)

*   **Introduction** (to Sorting Algorithms)
    *   **Sorting**: Rearranging array items in a logical order based on an attribute.
    *   Can be a preliminary step to searching.
    *   Extensive research has led to sophisticated methods due to its importance and potential time consumption.
*   **Simple Sorting Algorithms**
    *   **Bubble sort**.
    *   **Selection sort**.
    *   **Insertion sort**.
    *   **Merge sort**.
    *   **Quick sort**.
*   **Bubble Sort**
    *   Very slow, but conceptually the simplest sorting algorithm.
    *   Algorithm: Compares adjacent items, swaps if out of order, and repeats passes until the array is sorted, with each pass moving the largest unsorted item to its correct position.
    *   Program examples provided.

### Data Structures and Algorithms Lecture 5 (Sorting Algorithms- Part II)

*   **Selection Sort**
    *   Improves on bubble sort by reducing the number of swaps, though comparisons remain the same.
    *   Offers significant improvement for large records that require physical movement in memory.
    *   Algorithm: Selects an item (starting from the first), finds the minimum item in the remaining unsorted part, and swaps it with the selected item. This process is repeated for each unsorted position.
    *   Program examples provided.
*   **Insertion Sort**
    *   Often the best among elementary sorts (bubble, selection), being about twice as fast as bubble sort and somewhat faster than selection sort in normal situations.
    *   Used as a final stage in more sophisticated sorts like quicksort.
    *   Algorithm: Iteratively removes an element from the input, finds its correct location within the already sorted list, and inserts it there. This involves shifting larger elements to the right to make space.
    *   Program example provided.
*   **Merge Sort** (Mentioned as a simple sorting algorithm)
*   **Quick Sort** (Mentioned as a simple sorting algorithm)

### Data Structures and Algorithms Lecture 6 (Computational Complexity Analysis)

*   **Computational Complexity Analysis**
    *   Addresses questions like algorithm time/space needs, comparative speed, and best algorithm selection for a task.
*   **Complexity Analysis**
    *   Evaluates algorithm/code efficiency.
    *   Covers resources: CPU (time), Memory, Disk, and Network usage.
*   **Analyzing Algorithms**
    *   Systematic measurement of an algorithm's "goodness" and data structure operations.
    *   Running time increases with input size, but can vary for same-sized inputs.
    *   Affected by hardware (processor, memory) and software (OS, language) environments.
*   **Experimental Studies**
    *   Method: Implement the algorithm, run experiments on various test inputs, record and compare execution times.
    *   In Java, `System.currentTimeMillis()` can measure elapsed time.
    *   **Challenges**: Difficult to compare across different environments; limited test inputs may not cover all cases; requires full implementation.
*   **Moving Beyond Experimental Analysis**
    *   Focus on analysis independent of hardware/software, without implementation, and considering all possible inputs.
*   **Counting Primitive Operations**
    *   Estimating running time without experiments, directly from a high-level description.
    *   A primitive operation is a low-level instruction with constant execution time (e.g., assigning a value, arithmetic operation, comparison, array access, method call/return).
    *   The number of primitive operations (t) is counted and is proportional to actual running time, assuming similar execution times for primitive operations.
    *   A function `f(n)` characterizes the number of primitive operations as a function of input size `n`.
*   **Worst-Case Analysis**
    *   Focuses on the longest running time for any input of a given size `n`.
    *   Easier than average-case analysis because it only requires identifying the worst-case input.
    *   If an algorithm performs well for the worst-case input, it will always perform better for other inputs.
*   **Asymptotic Analysis**
    *   Focuses on the growth rate of running time as a function of input size `n`, disregarding constant factors.
*   **Asymptotic Notation**
    *   Commonly used notations for calculating running time complexity:
        *   **Ο Notation (Big-O)**: Expresses the **upper bound** of an algorithm's running time, measuring worst-case complexity.
            *   Definition: `f(n)` is `O(g(n))` if there exist constants `c > 0` and `n0 ≥ 1` such that `f(n) ≤ c · g(n)` for all `n ≥ n0`.
            *   Allows ignoring constant factors and lower-order terms.
        *   **Ω Notation (Omega)**: Expresses the **lower bound** of an algorithm's running time, measuring best-case complexity.
        *   **θ Notation (Theta)**: Expresses **both the lower and upper bound** of an algorithm's running time.
*   **Comparative Analysis**
    *   Big-O notation is used to characterize running times and order classes of functions by asymptotic growth rate.
    *   Example ordering: `1 logn n nlog n n2 n3 2n`.
    *   An `O(n)` algorithm is asymptotically better than an `O(n2)` algorithm, though for small `n`, the `O(n2)` might have a lower running time.
*   **The Constant Function** (`f(n) = c`)
    *   Simplest function, value is always `c` regardless of `n`.
*   **The Logarithm Function** (`f(n) = logb n`)
    *   Common in data structure and algorithm analysis. `b` is the base.
*   **The Linear Function** (`f(n) = n`)
    *   Assigns `n` to input `n`.
*   **The N-Log-N Function** (`f(n) = n log n`)
    *   Assigns `n` times the logarithm base-two of `n` to input `n`.
    *   Grows faster than linear, but slower than quadratic.
*   **The Quadratic Function** (`f(n) = n2`)
    *   Often appears due to nested loops (e.g., `1+2+3+...+n = n(n+1)/2`).
*   **The Cubic Function** (`f(n) = n3`)
    *   Less frequent in algorithm analysis than constant, linear, and quadratic.
*   **The Exponential Function** (`f(n) = bn`)
    *   `b` is a positive constant base, `n` is the exponent.
    *   Arises when operations double with each iteration (e.g., `2n`).
*   **Examples of Algorithm Analysis**
    *   Finding maximum of an array: O(n) time.
    *   Composing long strings (`repeat1` algorithm): O(n2) complexity.
    *   Three-Way Set Disjointness: worst-case running (complexity not fully stated in source).

### Data Structures and Algorithms Lecture 7 (Asymptotic Analysis)

*   **Big Oh Notation**
    *   Classifies algorithms based on how their running time or space requirements grow with input size.
    *   `O` refers to the **order of the function**.
    *   Provides an **upper bound** on the growth rate.
*   **O(1) Constant Time Complexity**
    *   Algorithms take the same amount of time regardless of input size (e.g., accessing an array element by index).
*   **O(LOG N) Logarithmic Time Complexity**
    *   Time is proportional to the logarithm of the input size `n`.
    *   Example: **Binary Search**.
*   **O(N) Linear Time Complexity**
    *   Time is directly proportional to the input size `n`.
    *   Example: **Linear Search**.
*   **O(N LOG N) Time Complexity**
    *   Time is proportional to a combination of linear and logarithmic growth.
    *   Example: **Merge Sort**.
*   **O(N2) Quadratic Time Complexity**
    *   Time is proportional to the square of the input size.
*   **O(2N) Exponential Time Complexity**
    *   Often seen in recursive algorithms that solve problems by recursively solving two smaller problems of size `N-1` (e.g., **Tower of Hanoi**).
*   **Examples of Complexity** (Code snippets with their complexities)
    *   `append` method: O(n2).
    *   `ContainsValue` method: O(n).
    *   `jump` method: O(nlogn).
    *   `sum` method: O(n3).

### Data Structures and Algorithms Lecture 8 (Stacks and Queues)

*   **Stacks and Queues**
*   **Introduction** (to Stacks and Queues)
    *   Often used as **programmer's tools**, unlike other data structures that model real-world objects.
    *   **Restricted Access**: Only one item can be read or removed at a given time (unlike arrays where any item can be accessed).
    *   More abstract entities.
*   **Stacks**
    *   Allows access only to the **last item inserted**.
    *   Follows the **Last-In-First-Out (LIFO)** principle.
    *   **Useful for**: checking balanced delimiters (parentheses, braces, brackets) in code, aiding algorithms for complex data structures (binary trees, graphs), microprocessor architecture, and parsing arithmetic expressions.
    *   **Main Operations**: **Push** and **Pop**.
*   **Operations on Stacks**
    *   **Push**: Add a new element onto the stack, placing it on the top.
    *   **Pop**: Retrieve and remove the element from the top of the stack.
*   **Stack Examples**
    *   Reversing a word.
    *   Delimiter matching (checking balanced `{}`, `[]`, `()` in text).
*   **Queues**
    *   Similar to a stack, but the **first item inserted is the first to be removed**.
    *   Follows the **First-In-First-Out (FIFO)** principle.
    *   Used as a programmer's tool, for searching graphs, and modeling real-world situations (e.g., people in line, airplanes waiting, data packets).
    *   Found in operating systems (e.g., printer queues, keystroke data).
*   **Operations on Queues**
    *   **Insert**: Add a new element at the rear.
    *   **Remove**: Retrieve and remove the element from the front.
    *   **Peek**: View the element at the front without removing it.
*   **A Circular Queue**
    *   Addresses inefficiency of shifting elements upon removal.
    *   When the rear reaches the end of an array, if there are empty cells at the front, new items are inserted into the beginning, making the front and rear pointers "wrap around".
    *   Also known as a **ring buffer**.
*   **Priority Queues**
    *   More specialized than stacks or ordinary queues.
    *   Items are removed from the front, but they are **ordered by key value** (lowest or highest key is always at the front).
    *   Items are inserted into their proper position to maintain order.
    *   Used in computer systems, e.g., preemptive multitasking operating systems may place programs in a priority queue.
*   **Operations on Priority Queues**
    *   **Insert**: Add a new element, comparing its key value to find the correct position.
    *   **Remove**: Retrieve and remove the element at the front (highest priority).
    *   **Peek**: View the element at the front (highest priority).

### Data Structures and Algorithms Lecture 9 - Part I (Linked Lists)

*   **Linked List - Part I**
*   **Introduction** (to Linked Lists)
    *   A **versatile data structure**.
    *   Can replace arrays as a basic data structure (e.g., for stacks and queues).
    *   Useful when random access by index is not frequent.
    *   **Various types**: Simple linked lists, Double-ended lists, Sorted lists, Doubly linked lists, Lists with iterators.
*   **Advantages over Arrays**
    *   Ease of insertion/deletion.
    *   Dynamic size.
*   **Disadvantages** (compared to Arrays)
    *   No random access to elements.
    *   Requires extra memory space for a pointer in every element.
    *   Arrays have better cache locality (better performance).
*   **Simple Linked Lists**
    *   A linear collection of data elements.
    *   Sequence is determined by links (nodes) pointing to the next, not physical memory placement.
    *   **Terminology**:
        *   **Link (Node)**: Each element that stores data and a reference to the next link.
        *   **Next**: Reference within each link to the subsequent link.
        *   **Linked List**: Contains a connection link to the **first** link.
*   **Node Class** (Java Representation)
    *   A self-referential class (contains a field of its own type) that represents individual nodes/links.
*   **LinkedList Class** (Java Representation)
    *   A base class that uses `Node` objects to create a linked list, typically holding a reference to the `first` node.
*   **Simple Linked List Operations**
    *   **Insert**: Can be done at the front, rear, or middle; lecture focuses on insertion at the front.
        *   Steps for `insertFirst`: Create new node, set its `next` to the old `first` node, then update the list's `first` to the new node.
    *   **Delete**: Focuses on deleting the first node.
        *   Steps for `deleteFirst`: Save reference to first node, update list's `first` to the second node, set the temporary node's `next` to `null`.
    *   **Display List**: Traverse from `first` node, following `next` references until the end, displaying each node's data.
*   **Finding Specified Nodes**
    *   Similar to display, but iteration stops when the `search value` is matched. Returns the current node if found, or `null` if not.
*   **Deleting Specified Nodes**
    *   Requires tracking both the `current` node and the `previous` node.
    *   If the node is found, the `previous` node's `next` reference is set to the `current` node's `next`, effectively bypassing and deleting `current`.

### Data Structures and Algorithms Lecture 9 - Part II (Linked Lists)

*   **Linked List - Part II**
*   **Double-Ended Lists**
    *   Similar to ordinary linked lists, but include an additional reference to the **last link/node**.
    *   Allows direct insertion at the end of the list, as well as the beginning.
*   **Sorted Lists**
    *   Items are arranged in **sorted order by key value**.
    *   Deletion is often limited to the smallest (or largest) item at the start of the list.
    *   **Insertion**: Involves searching for the appropriate place to insert an item to maintain order, then adjusting `next` references of the new and previous nodes.
*   **Doubly Linked Lists**
    *   Addresses the difficulty of traversing backward in ordinary linked lists.
    *   Each link/node has **two references**: one to the `next` link and one to the `previous` link.
    *   **Traversal**: Includes `DisplayForward()` (like simple lists) and `DisplayBackward()` (traversing from `last` node using `previous` references).
    *   **Insertion**: Multiple routines exist: `insertFirst()`, `insertLast()`, and `insertAfter()` (inserting after a specified key).
    *   **Deletion**: Multiple routines exist: `deleteFirst()`, `deleteLast()`, and `deleteKey()`.
        *   For `deleteKey()`, if the node is not first or last, the `next` field of `current.previous` is set to `current.next`, and the `previous` field of `current.next` is set to `current.previous`.
