- ["Big O" Notation](#big-o-notation)
  - [Orders of Common Functions](#orders-of-common-functions)
  - [Orders of Uncommon Functions](#orders-of-uncommon-functions)
  - [Examples](#examples)
    - [O(1)](#o1)
    - [O(log n)](#olog-n)
    - [O(n)](#on)
    - [O(n log n)](#on-log-n)
    - [O(n$^2$)](#on2)
  - [Graph](#graph)

# "Big O" Notation

**Big O** is a measure of **memory** and/or **time** complexity in an algorithm and is recorded in terms of "worst-case".

The "O" in "Big O" stands for Order. (Ordnung)

## Orders of Common Functions

The short list below is taken from Harvard's CS50. A more complete list can be found on the [wiki](https://en.wikipedia.org/wiki/Big_O_notation#Orders_of_common_functions).

| Big O      | Time Complexity Description                                           | Type            | Speed     |
| ---------- | --------------------------------------------------------------------- | --------------- | --------- |
| O(1)       | Operation does not change based on amount of data                     | Constant        | Very Fast |
| O(log n)   | Divide and Conquer, Binary Search Tree                                | Logarithmic     |
| O(n)       | An examination of all data in an array                                | Linear          |
| O(n log n) | Read entire set and perform a logarithmic set operation for each read | Polylogarithmic |
| O(n$^2$)   | Examination of data set twice                                         | Quadratic       | Very Slow |
|            | **_Acceptibility / Unacceptability Line_**                            |                 |           |

## Orders of Uncommon Functions

| Big O        | Time Complexity Description                                 | Type        | Speed           |
| ------------ | ----------------------------------------------------------- | ----------- | --------------- |
| O($\sqrt n$) | Between `log n` and `n` time complexity.                    | square root | Acceptable      |
|              | **_Acceptibility / Unacceptability Line_**                  |             |                 |
| O(n$^3$)     | Worse than n$^2$, there is usually a more optimal solution. | cubed       | Extremely Slow  |
| O(2$^n$)     | Doubles for every n                                         | doubling    | Incredibly Slow |
| O(n!)        | Anything over n=8 becomes difficult to solve.               | Factorial   | Unacceptable    |

## Examples

The data set for all examples: `const data = [0, 1, .. n];`

### O(1)

```js
// A simple array read
console.log(data[n - 1]);
```

### O(log n)

```js
const
```

### O(n)

```js
// Linear Search (Find the first instance of `searchValue` in `data`)
function linearSearch(searchValue, data) {
  for (let x = 0; x < data.length; x++) {
    if (data[x] === searchValue) return x;
  }
  return false;
}
```

### O(n log n)

You can assume (for interview questions, and as a rule of thumb) that most sorting operations, using a language's built-in sort, operate on the `O(n log n)` time complexity.

```js

```

### O(n$^2$)

```js
// Naive implementation
// Note the nested for loops
function hasDuplicates(data) {
  for (let x = 0; x < data.length; x++) {
    for (let y = 0; y < data.length; y++) {
      if (x === y) continue;
      if (data[x] === data[y]) return true;
    }
  }
  return false;
}
```

## Graph

Big O is used to ballpark how a particular piece of code may perform.

However, I wanted to know in slightly more concrete terms how much more poorly O(n$^2$) performed against something like O(log n). This graph in conjunction with a concrete data size of 50 really shows how a poor algorithm could eat cpu cycles.

![Big O](_images-for-notes/big-o.png)

> Since writing the Octave code was a bit of a rabbit hole of it's own, I have included it here. I really miss mathcad. I wish I had learned Matlab instead of Mathcad, then a transition to Octave would be better. I just really need to force myself to use it.

```matlab
# Octave GNU
# clear;clc;close all;

scale = 50;
x = 1:0.1:scale;
plot(
  x, (x-x)+1, "-;O(1) [1];",
  x, log(x) + 1, "-;O(log n) [4];",
  x, x, "-;O(n) [50];",
  x, 1 + x .* log(x), "-;O(n log n) [196];",
  x, x.^2, "-;O(n^2) [2500];"
);


grid on;
xlabel("n");
ylabel("time");
title("Big O Notation");
legend("location", "north");
ylim([0 scale]);
#axis("equal");
```
