- [Algorithms](#algorithms)
  - [Terms](#terms)
    - [Dynamic Programming](#dynamic-programming)
    - [Divide and Conquer](#divide-and-conquer)
    - [Greedy Algorithm](#greedy-algorithm)
  - [Algorithms](#algorithms-1)
    - [Binary Search](#binary-search)
    - [Linear Search](#linear-search)
  - [Specific Algorithms](#specific-algorithms)
    - [Dijkstra's Algorithm](#dijkstras-algorithm)
    - [Kadane's Algorithm (Maximum Subarray Problem)](#kadanes-algorithm-maximum-subarray-problem)
    - [Prefix Sum](#prefix-sum)
    - [Prim's Algorithm / Kruskal’s Algorithm](#prims-algorithm--kruskals-algorithm)
  - [Things to learn](#things-to-learn)

# Algorithms

I have three books on algorithms. I will reference page numbers where relevant.

- Stephen S. Skiena (2020). _The Algorithm Design Manual_
- Thomas H. Cormen, Charles E. Leiserson, Ronald L. Rivest, Clifford Stein-The MIT Press (2022) (**CLRC**). _Introduction to Algorithms_
- Gayle Laakmann McDowell (2015). _Cracking the Coding Interview_

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

---

### Divide and Conquer

In short: Recursion.

Wikipedia defines [Divide and Conquer](https://en.wikipedia.org/wiki/Divide-and-conquer_algorithm) algorithms as recursive methods of dividing a problem down into two or more sub problems of the same, or related type, until the problems become simple enough to be solved directly.

---

### Greedy Algorithm

An algorithm that **locally** chooses the best option without regard for the **global** best solution. These algorithms generally produce an approximation, for example, a shortest route between two paths, where the actual fastest route may include a ladder or wormhole that is discarded due to the algorithm's greedy nature. (Wikipedia's [Greedy Algorithm](https://en.wikipedia.org/wiki/Greedy_algorithm) page.)

---

## Algorithms

---

### Binary Search

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

---

### Linear Search

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

---

## Specific Algorithms

While working through leetcode problems, I am coming across many questions that require very niche algorithmic knowledge. This section is where I am going to attempt to document what I have learned to the best of my ability.

---

### Dijkstra's Algorithm

Wikipedia defines [Dijkstra's Algorithm](https://en.wikipedia.org/wiki/Dijkstra's_algorithm) as a way to find the shortest path between nodes in a graph.

It operates in a similar manner to A\* path-finding, except that it supports things like portals and more abstract graphs where distances between nodes are unknown and possibly not uniform.

- Class
  - Search algorithm
  - Greedy algorithm
  - Dynamic Programming
- Data Structure (Input): Graph
- Data Structure (Implementation): Queue or Heap

---

### Kadane's Algorithm (Maximum Subarray Problem)

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

---

### Prefix Sum

(Cumulative Sum, Inclusive Scan)

Wikipedia describes [Prefix Sum](https://en.wikipedia.org//wiki/Prefix_sum) page describes the algorithm as working off a second data set that contains the running sum of the input data set.

It is useful in finding a contiguous substring within the original data set that sums to a desired total. (See [Leetcode 974](https://leetcode.com/problems/subarray-sums-divisible-by-k/))

---

### Prim's Algorithm / Kruskal’s Algorithm

> Skiena pp. 245 / 248

> Wikipedia:
>
> [Prim's Algorithm](https://en.wikipedia.org/wiki/Prim's_algorithm)
>
> [Kruskal's Algorithm](https://en.wikipedia.org/wiki/Kruskal%27s_algorithm)

Convert a weighted undirected graph into a minimum spanning tree.

---

## Things to learn

> TODO: Outdated

- Depth-first search
- Breadth-first search
- Writing sorting algorithms(?)
