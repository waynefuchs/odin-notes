# Algorithms <!-- omit from toc -->

Algorithms are simply a set of steps used to complete a specific task.

> TODO: Things to learn
>
> - Depth-first search
> - Breadth-first search
> - Writing sorting algorithms(?)

- [Recursion](#recursion)
- [Searching](#searching)
  - [Binary Search](#binary-search)
  - [Linear Search](#linear-search)
- [Sorting](#sorting)
  - [Bubble Sort O($n^2$)](#bubble-sort-on2)
  - [QuickSort O($n$ $log$($n$)) to O($n^2$)](#quicksort-on-logn-to-on2)
- ["Named" Algorithms](#named-algorithms)
  - [Dijkstra's Algorithm](#dijkstras-algorithm)
  - [Kadane's Algorithm (Maximum Subarray Problem)](#kadanes-algorithm-maximum-subarray-problem)
  - [Newton's method](#newtons-method)
  - [Prefix Sum](#prefix-sum)
  - [Prim's Algorithm / Kruskal’s Algorithm](#prims-algorithm--kruskals-algorithm)
- [Algorithm Related Terms and Concepts](#algorithm-related-terms-and-concepts)
  - [Dynamic Programming](#dynamic-programming)
  - [Divide and Conquer](#divide-and-conquer)
  - [Greedy Algorithm](#greedy-algorithm)
  - [Weak Ordering](#weak-ordering)
- [Interview Algorithms](#interview-algorithms)
  - [95% of interviews ask](#95-of-interviews-ask)
  - [The other 5%](#the-other-5)
- [Book Recommendations](#book-recommendations)

# Recursion

1. Base case (ensure the base case is understood)
2. (then) recurse

# Searching

Algorithms for finding data.

## Binary Search

Time Complexity: `O(log n)`

Synopsis: Iterate over a list, halving it each time until you find the element that you're looking for or exhaust all options. The list must exist in a sorted state before beginning a binary search.

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

## Linear Search

Time Complexity: `O(n)`

Synopsis: Sequentially check every item in a list until you find what you're looking for.

> Type: Brute Force

> Avoid when possible

```pseudocode
SET pointer to first item in the list
WHILE item_found = False
    IF pointer is pointing at item THEN
        item_found = True
    ELSE
        increment pointer to next item in the list
```

# Sorting

Algorithms aimed at ordering data.

> ⓘ Sorting should only be attempted when the data is mutable. Copy any immutable data sets into a mutable array, then perform the sorting.

## Bubble Sort O($n^2$)

```pseudocode
FOR length of input array (x)
    FOR length of the input array, reduced by parent loop (length-x)
    IF this data at position x is greater than the data at x+1
        Swap x position with it's neighbor, moving the larger value toward the end of the array
    END IF
ENDFOR
```

## QuickSort O($n$ $log$($n$)) to O($n^2$)

In a word; **pivot**. (QuickSort would be better labeled as PivotSort.) QuickSort is _not_ always quick.

QuickSort is a [divide and conquer](#divide-and-conquer) sorting algorithm that utilizes [weak ordering](#weak-ordering).

> ⓘ The reason for the range on the Big-O efficiency is that the choice of the partitioning routine and the data set will dictate efficiency. (QuickSort will not always sort quickly)

```pseudocode
QuickSort(arr, low, high)
  IF low < high
    pivot = Partition(arr, low, high)
    QuickSort(arr, low, pivot)
    QuickSort(arr, pivot+1, high)

Partition(arr, low, high)
  pivot = arr[low]
  leftWall = low

  FOR i = low + 1 to high
    IF arr[i] < pivot
      swap(arr[i], arr[leftWall])
        leftWall = leftWall + 1

  swap(pivot, arr[leftWall])

  return leftWall
```

# "Named" Algorithms

While working through leetcode problems, I am coming across many questions that require niche algorithmic knowledge to accomplish various tasks.

## Dijkstra's Algorithm

Wikipedia defines [Dijkstra's Algorithm](https://en.wikipedia.org/wiki/Dijkstra's_algorithm) as a way to find the shortest path between nodes in a graph.

It operates in a similar manner to A\* path-finding, except that it supports things like portals and more abstract graphs where distances between nodes are unknown and possibly not uniform.

- Class
  - Search algorithm
  - Greedy algorithm
  - Dynamic Programming
- Data Structure (Input): Graph
- Data Structure (Implementation): Queue or Heap

## Kadane's Algorithm (Maximum Subarray Problem)

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

## Newton's method

A converging method, used to find the square root of a number. Iterate over `z -= (z * z - x) / (2 * x)`. $z^2$ − x is how far away $z^2$ is from where it needs to be (x), and the division by 2z is the derivative of z², to scale how much we adjust z by how quickly $z^2$ is changing.

```js
function square_root(x) {
  let z = 1;
  for (i = 0; i < 10; i++) z -= (z * z - x) / (2 * x);
  return result;
}

// 1.4142103896495881
// 1.4142135623730951
console.log(square_root(2));
console.log(Math.sqrt(2));
```

## Prefix Sum

(Cumulative Sum, Inclusive Scan)

Wikipedia describes [Prefix Sum](https://en.wikipedia.org//wiki/Prefix_sum) page describes the algorithm as working off a second data set that contains the running sum of the input data set.

It is useful in finding a contiguous substring within the original data set that sums to a desired total. (See [Leetcode 974](https://leetcode.com/problems/subarray-sums-divisible-by-k/))

## Prim's Algorithm / Kruskal’s Algorithm

> Skiena pp. 245 / 248

> Wikipedia:
>
> [Prim's Algorithm](https://en.wikipedia.org/wiki/Prim's_algorithm)
>
> [Kruskal's Algorithm](https://en.wikipedia.org/wiki/Kruskal%27s_algorithm)

Convert a weighted undirected graph into a minimum spanning tree.

# Algorithm Related Terms and Concepts

## Dynamic Programming

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

## Divide and Conquer

In short: Recursion.

Wikipedia defines [Divide and Conquer](https://en.wikipedia.org/wiki/Divide-and-conquer_algorithm) algorithms as recursive methods of dividing a problem down into two or more sub problems of the same, or related type, until the problems become simple enough to be solved directly.

## Greedy Algorithm

An algorithm that **locally** chooses the best option without regard for the **global** best solution. These algorithms generally produce an approximation, for example, a shortest route between two paths, where the actual fastest route may include a ladder or wormhole that is discarded due to the algorithm's greedy nature. (Wikipedia's [Greedy Algorithm](https://en.wikipedia.org/wiki/Greedy_algorithm) page.)

## Weak Ordering

Formalization of the concept of the loose intuitive ranking of a set, and in computer science is useful to partition refinement algorithms, which can yield significant speed increases.

# Interview Algorithms

> Source: The Primeagen

## 95% of interviews ask

Be able to write:

- Breadth First Search
- Depth First Search
- Binary Search

Know what the following is used for:

- Linked List
- Queue
- Stack

## The other 5%

- An obtuse algorithm that it is unfair to ask
- Maximum Subarray
- dynamic programming

# Book Recommendations

1. **_Introduction to Algorithms_** by (CLRS)
   Thomas H. **C**ormen,
   Charles E. **L**eiserson,
   Ronald L. **R**ivest,
   Clifford **S**tein

   This is _the_ algorithms book. A note: The math is somewhat heavy in this book.

2. **The Algorithm Design Manual** by
   Stephen S. Skiena (2020)

   I use this book to get a general feel for how the algorithm works before diving into CLRS.

3. **Cracking the Coding Interview**
   Gayle Laakmann McDowell (2015)

   A good place to start in order to get good at algorithms for the interview process.
