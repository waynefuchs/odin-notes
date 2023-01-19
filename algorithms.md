- [Algorithms](#algorithms)
  - [Terms](#terms)
    - [Dynamic Programming](#dynamic-programming)
    - [Divide and Conquer](#divide-and-conquer)
  - [Algorithms](#algorithms-1)
    - [Binary Search](#binary-search)
    - [Linear Search](#linear-search)
    - [Maximum Subarray Problem with Kadane's Algorithm](#maximum-subarray-problem-with-kadanes-algorithm)
  - [Things to learn](#things-to-learn)
  - [Data Structures](#data-structures)
    - [Binary Tree](#binary-tree)
    - [Graph](#graph)
    - [Linked Lists](#linked-lists)
      - [Doubly Linked Lists](#doubly-linked-lists)
      - [Circular Linked Lists](#circular-linked-lists)
    - [Queue](#queue)
    - [Stack](#stack)

# Algorithms

## Terms

---

### Dynamic Programming

In short: Recursion + Storing calculated pieces for recall.

It is a technique for solving problems with overlapping sub-problems. You conquer each sub-problem recursively, and then combine the solutions to find a final solution.

Wikipedia defines [Dynamic Programming](https://en.wikipedia.org/wiki/Dynamic_programming) as simplifying a complicated problem by breaking it down into simpler sub-problems in a recursive manner.

Example Uses:

- Dijkstra's algorithm for the shortest path problem
- Fibonacci sequence
- A type of balanced 0-1 matrix
- Checkerboard
- Sequence alignment
- Tower of Hanoi puzzle
- Egg dropping puzzle
- Matrix chain multiplication

### Divide and Conquer

In short: Recursion.

Wikipedia defines [Divide and Conquer](https://en.wikipedia.org/wiki/Divide-and-conquer_algorithm) algorithms as recursive methods of dividing a problem down into two or more sub problems of the same, or related type, until the problems become simple enough to be solved directly.

## Algorithms

---

### Binary Search

---

`O(log n)`

Synopsis: Keep going to the middle of the list until you find what you're looking for.

> Requirement: Only works on sorted data.

> Type: Divide and Conquer

```pseudocode
WHILE customer_found = False:
  Find midpoint of list
  IF customer_name = record at midpoint of list THEN
    customer_found = True
  ELSE IF customer comes before the midpoint THEN
    throw away the second half of the list
  ELSE
    throw away the first part of the list
    OUTPUT customer details
```

1. [BBC: Binary Search Guide](https://www.bbc.co.uk/bitesize/guides/zts8v9q/revision/5)
2. [Wikipedia: Binary search Algorithm](https://en.wikipedia.org/wiki/Binary_search_algorithm)

### Linear Search

---

O(n)

Synopsis: Sequentially check every item in a list until you find what you're looking for.

> Type: Brute Force

> Avoid when possible

```pseudocode
SET pointer to first item in the list
WHILE item_found = False
    IF pointer is poiting at item THEN
        item_found = True
    ELSE
        increment pointer to next item in the list
```

### Maximum Subarray Problem with Kadane's Algorithm

An algorithm aimed at solving the [Maximum Subarray Problem](https://en.wikipedia.org/wiki/Maximum_subarray_problem), which is the task of finding a contiguous subarray with the largest sum within a one-dimensional array.

The solution is to iterate through the subarray, finding the maximum current sum as you go. If the current sum is ever less than zero, then you reset the count. Then you compare the maximum sum that you've seen while iterating to the current sum. If it is greater, then you update the maximum sum. When you have iterated all the way through the array, you have your answer.

```js
// Kadane's Algorithm
function kadane(nums) {
  let curSum = 0;
  let maxSum = Number.NEGATIVE_INFINITY;
  for (i of nums) {
    // placing the + i outside of max() here will
    // cause completely negative input arrays to work.
    curSum = Math.max(0, curSum) + i;
    maxSum = Math.max(curSum, maxSum);
  }
  return maxSum;
}
```

## Things to learn

---

Depth-first search
Breadth-first search
Writing sorting algorithms

## Data Structures

These are the requisite (abstract) data structures that are necessary to understand algorithms. I use the word 'abstract' because languages don't directly implement these data structures.

[CodesDope: Introduction to Data Structures](https://www.codesdope.com/course/data-structures-introduction/)

### Binary Tree

```
      ___F___           Level 0 (F)
     /       \
    D         J         Level 1 (DJ)
   / \       / \
  B   E     G   K       Level 2 (BEGK)
 / \         \
A   C         I         Level 3 (ACI)
             /
            H           Level 4 (H)
```

- Visiting a Node: Reading or Processing data in a node
- Tree Traversal: The process of visiting each node in the tree exactly once in some order.
- Breadth-First Traversal
  - Time Complexity: `O(n)`
  - Space Complexity: `O(1)` -> `O(n)`
  - ` L0:F -> L1:D,J -> L2:B,E,G,K -> L3:A,C,I -> L4:H`
  - Sometimes called Level-Order Traversal
  - Synopsis: Visit all nodes at each level before moving on to the next level by queuing a visit to all child nodes (left and right) for all nodes in the queue. [Binary tree: Level Order Traversal](https://www.youtube.com/watch?v=86g8jAQug04)
- Depth-First Traversal
  - Time Complexity: `O(n)`
  - Space Complexity: `O(log2 n)` -> `O(n)`
  - Synopsis: Recursively dig all the way into each node before backing out, one complete branch at a time. [Binary tree traversal: Preorder, Inorder, Postorder](https://www.youtube.com/watch?v=gm8DUJJhmY4)
  - Conventionally, left is visited prior to right branch traversal
  - Preorder
    - data-left-right (DLR)
    - data-right-left (DRL)
  - Inorder
    - Note: Data is visited in 'sorted order'
    - left-data-right (LDR) <- ascending
    - right-data-left (RDL) <- descending
  - PostOrder
    - left-right-data (LRD)
    - right-left-data (RLD)

### Graph

TODO: Tree is a special kind of graph

### Linked Lists

#### Doubly Linked Lists

#### Circular Linked Lists

### Queue

- FIFO (First-In First-Out)
- Synopsis: Works just like a line at the checkout.
- Enqueue: `array.push(item)`: Put item at the end of the queue
- Dequeue: `item = array.shift()`: Take item from the front of the queue

### Stack

- LIFO (Last-In First-Out)
- Synopsis: Works like the children's ring toy
- Push: `array.push(item)`: Add an item on to the top of the stack
- Pop: `item = array.pop()`: Take an item off of the top of the stack
