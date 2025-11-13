# Deep Dive: DSA & OOP Fundamentals

This guide provides a more detailed explanation of the Data Structures, Algorithms, and Object-Oriented Programming concepts covered in Block 1 of the study plan.

---

### 1. Complexity Analysis (Big O Notation)

*   **Concept:** Big O notation is used to describe the performance or complexity of an algorithm. It tells you how the runtime or memory usage of an algorithm grows as the input size (`n`) grows.
*   **Key Complexities:**
    *   **O(1) - Constant Time:** The runtime is the same, regardless of the input size. (e.g., accessing an element in an array by its index).
    *   **O(log n) - Logarithmic Time:** The runtime grows logarithmically with the input size. This is very efficient. (e.g., Binary Search).
    *   **O(n) - Linear Time:** The runtime grows linearly with the input size. (e.g., iterating through all elements in a list).
    *   **O(n log n) - Log-Linear Time:** A very common complexity for efficient sorting algorithms. (e.g., Merge Sort, Quick Sort).
    *   **O(n²) - Quadratic Time:** The runtime grows quadratically. This is common in algorithms that involve nested iterations over the data. (e.g., Bubble Sort, Insertion Sort).

---

### 2. Core Data Structures

#### A. Hash Maps (or Dictionaries)
*   **Concept:** A data structure that stores key-value pairs. It uses a **hash function** to compute an index into an array of buckets or slots, from which the desired value can be found.
*   **Why it's great:** It provides very fast lookups, insertions, and deletions on average: **O(1)**.
*   **Collision:** When the hash function generates the same index for two different keys. This is typically handled by **chaining**, where each bucket is a linked list of key-value pairs.

#### B. Linked Lists
*   **Concept:** A linear data structure where elements are not stored at contiguous memory locations. Each element (a **node**) contains data and a pointer to the next node in the sequence.
*   **Pros:** Efficient insertions and deletions anywhere in the list (**O(1)**) if you have a pointer to the node.
*   **Cons:** No random access. To access the k-th element, you must traverse the list from the beginning (**O(n)**).

#### C. Arrays & Strings
*   **Concept:** A collection of items stored at contiguous memory locations.
*   **Pros:** Fast random access. You can access any element by its index in **O(1)**.
*   **Cons:** Slow insertions and deletions in the middle of the array (**O(n)**) because elements need to be shifted.

---

### 3. Core Algorithms

#### A. Binary Search
*   **Concept:** A highly efficient searching algorithm that works on **sorted** arrays. It repeatedly divides the search interval in half.
*   **How it works:**
    1.  Compare the target value to the middle element of the array.
    2.  If they are not equal, the half in which the target cannot lie is eliminated.
    3.  The search continues on the remaining half until the target is found or the interval is empty.
*   **Complexity:** O(log n).

#### B. Merge Sort
*   **Concept:** A "divide and conquer" sorting algorithm.
*   **How it works:**
    1.  **Divide:** Recursively split the array in half until you have arrays of size 1.
    2.  **Conquer:** Merge the smaller sorted arrays back together in the correct order.
*   **Complexity:** O(n log n) in all cases (worst, average, best).

#### C. Quick Sort
*   **Concept:** Another "divide and conquer" sorting algorithm.
*   **How it works:**
    1.  **Pivot:** Pick an element as a pivot.
    2.  **Partition:** Reorder the array so that all elements with values less than the pivot come before it, while all elements with values greater than the pivot come after it.
    3.  **Recurse:** Recursively apply the above steps to the sub-arrays of elements with smaller and greater values.
*   **Complexity:** O(n log n) on average, but O(n²) in the worst case (e.g., on an already sorted array with a bad pivot choice).

---

### 4. Advanced Data Structures

#### A. Trees (Binary Search Tree - BST)
*   **Concept:** A tree data structure where each node has at most two children (left and right). In a BST, the left child's value is less than the parent's, and the right child's value is greater.
*   **Benefit:** Allows for fast search, insertion, and deletion: **O(log n)** on average for a balanced tree.

#### B. Graphs (BFS & DFS)
*   **Concept:** A data structure consisting of a set of **vertices** (or nodes) and a set of **edges** connecting them.
*   **Graph Traversal:** The process of visiting every vertex in a graph.
    *   **Breadth-First Search (BFS):** Explores neighbor nodes first, before moving to the next level neighbors. It uses a **queue**. Think of it as exploring in concentric circles. Useful for finding the shortest path in an unweighted graph.
    *   **Depth-First Search (DFS):** Explores as far as possible along each branch before backtracking. It uses a **stack** (often implicitly via recursion). Useful for finding a path, detecting cycles, or topological sorting.

---

### 5. The Four Pillars of OOP

#### A. Encapsulation
*   **Concept:** Bundling data (attributes) and methods that operate on the data into a single unit (a "class"). It hides the internal state of an object from the outside.
*   **Example:**
    ```python
    class Account:
        def __init__(self, balance):
            self.__balance = balance  # Private attribute

        def deposit(self, amount):
            if amount > 0:
                self.__balance += amount

        def get_balance(self):
            return self.__balance
    ```

#### B. Abstraction
*   **Concept:** Hiding complex implementation details and showing only the necessary features of an object.
*   **Example:** You use a TV remote (the abstraction) without needing to know how the infrared signals work (the implementation).

#### C. Inheritance
*   **Concept:** A mechanism that allows a new class (child) to inherit properties and methods from an existing class (parent). It promotes code reuse.
*   **Example:**
    ```python
    class Animal:
        def speak(self):
            raise NotImplementedError

    class Dog(Animal):  # Dog inherits from Animal
        def speak(self):
            return "Woof!"
    ```

#### D. Polymorphism
*   **Concept:** The ability of an object to take on many forms. It allows a single interface to be used for different data types.
*   **Example (Method Overriding):**
    ```python
    class Cat(Animal): # Cat also inherits from Animal
        def speak(self):
            return "Meow!"

    # Polymorphism in action
    animals = [Dog(), Cat()]
    for animal in animals:
        print(animal.speak()) # The same method call works for different objects
    ```
