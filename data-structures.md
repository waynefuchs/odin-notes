- [Data Structures](#data-structures)
  - [Binary Tree](#binary-tree)
  - [Graph](#graph)
  - [Linked Lists](#linked-lists)
    - [Doubly Linked Lists](#doubly-linked-lists)
    - [Circular Linked Lists](#circular-linked-lists)
  - [Queue](#queue)
  - [Stack](#stack)

# Data Structures

These are the requisite (abstract) data structures that are necessary to understand algorithms. I use the word 'abstract' because languages don't directly implement these data structures.

[CodesDope: Introduction to Data Structures](https://www.codesdope.com/course/data-structures-introduction/)

## Binary Tree

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

## Graph

TODO: Tree is a special kind of graph

## Linked Lists

### Doubly Linked Lists

### Circular Linked Lists

## Queue

- FIFO (First-In First-Out)
- Synopsis: Works just like a line at the checkout.
- Enqueue: `array.push(item)`: Put item at the end of the queue
- Dequeue: `item = array.shift()`: Take item from the front of the queue

## Stack

- LIFO (Last-In First-Out)
- Synopsis: Works like the children's ring toy
- Push: `array.push(item)`: Add an item on to the top of the stack
- Pop: `item = array.pop()`: Take an item off of the top of the stack
