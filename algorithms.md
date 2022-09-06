- [Algorithms](#algorithms)
  - [## Terms](#-terms)
    - [Divide and Conquer](#divide-and-conquer)
  - [## Algorithms](#-algorithms)
    - [Binary Search](#binary-search)
  - [## Things to learn](#-things-to-learn)

# Algorithms

## Terms
---

### Divide and Conquer

In short: Recursion.

Wikipedia defines [Divide and Conquer](https://en.wikipedia.org/wiki/Divide-and-conquer_algorithm) algorithms as recursive methods of dividing a problem down into two or more sub problems of the same, or related type, until the problems become simple enough to be solved directly.

## Algorithms
---

### Binary Search

> O(log n)

1. Must begin with sorted data.
2. Binary Search is a *Divide and Conquer* Algorithm

``` pseudocode
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

## Things to learn
---

Depth-first search
Breadth-first search
Writing sorting algorithms