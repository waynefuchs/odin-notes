[figure-BigOGraph]: ../.project/figures/big-o.png

# "Big O" Notation <!-- omit in toc -->

**Big O** is a measure of computational **time** or memory complexity vs **input** relational to the input growth in an algorithm, and is (usually) analyzed in terms of "worst-case."

> ⓘ Average and Best case are alternative niche options.

> ⓘ Constants are disregarded resulting in different operating speeds within the same theoretical time complexity:
> O($n$)
> = O($n-14$)
> = O($33n$)

> ⓘ The "O" in "Big O" stands for Order. (From German word "Ordnung")

- ["Alternatives" to Big-O](#alternatives-to-big-o)
  - [Big Ω (Omega)](#big-ω-omega)
  - [Big-Θ (Theta)](#big-θ-theta)
- [Time / Space Complexity](#time--space-complexity)
- [Ranking of Common Big-O Functions](#ranking-of-common-big-o-functions)
- [Orders of Uncommon Functions](#orders-of-uncommon-functions)
- [Tricks 🎉](#tricks-)
  - [O(1)](#o1)
  - [O(log n)](#olog-n)
  - [O($\\sqrt n$)](#osqrt-n)
  - [O(n)](#on)
  - [O(n log n)](#on-log-n)
  - [O(n$^2$)](#on2)
  - [O(n$^3$)](#on3)
- [Graph](#graph)
- [References](#references)

## "Alternatives" to Big-O

Big-O makes the most sense to ensure confidence that algorithms scale properly and will work as intended without leaving users frustrated with load times and program lock-ups. However, it can be interesting to consider best-case or average-case complexity.

### Big Ω (Omega)

Considers the "best case" result of an algorithm. This is considered far less useful than Big-O because it usually does not suitably indicate how an algorithm will scale.

### Big-Θ (Theta)

Simply put, the area between Big-Omega and Big-O.

## Time / Space Complexity

Big-O is often used to discuss time complexity, but it also applies to space complexity (amount of memory an algorithm consumes), which can be important to consider, depending on your deployment environment. (eg: VM renting services, such as linode, are rather restricted in memory usage)

## Ranking of Common Big-O Functions

The short list below is taken from Harvard's CS50. A more complete list can be found on the [wiki](https://en.wikipedia.org/wiki/Big_O_notation#Orders_of_common_functions).

| Big O            | Time Complexity Description                                           | Type            | Speed      |
| ---------------- | --------------------------------------------------------------------- | --------------- | ---------- |
| O($1$)           | Operation does not change based on amount of data                     | Constant        | Very Fast  |
| O($log$ $n$)     | Divide and Conquer, Binary Search Tree                                | Logarithmic     |
| O($\sqrt n$)     | Between `log n` and `n` time complexity.                              | square root     | Acceptable |
| O($n$)           | An examination of all data in an array                                | Linear          |
| O($n$ $log$ $n$) | Read entire set and perform a logarithmic set operation for each read | Polylogarithmic |
| O($n^2$)         | Examination of data set twice                                         | Quadratic       | Very Slow  |
|                  | **_Acceptibility / Unacceptability Line_**                            |                 |            |

## Orders of Uncommon Functions

| Big O    | Time Complexity Description                                 | Type      | Speed           |
| -------- | ----------------------------------------------------------- | --------- | --------------- |
|          | **_Acceptibility / Unacceptability Line_**                  |           |                 |
| O($n^3$) | Worse than n$^2$, there is usually a more optimal solution. | cubed     | Extremely Slow  |
| O($2^n$) | Doubles for every n                                         | doubling  | Incredibly Slow |
| O($n!$)  | Anything over n=8 becomes difficult to solve.               | Factorial | Unacceptable    |

## Tricks 🎉

- Any time an algorithm repeatedly "halves" the search field, it will generally be O($n$ $log$ $n$) or O($log$ $n$).
- Summation problems are O($n^2$), denoted by $\sum_{i=1}^{n} i=  \dfrac{n(n+1)}{2}$. (Story of Gauss solving summation of 1..100 in mere seconds while in primary school.) When you FOIL that equation, $n^2 + n$ emerges and the $n$ is "constant" and therefore discarded due to being insignificant in comparison to $n^2$.

### O(1)

The result will always take constant time.

> ⚠️It is counter-intuitive that O($1$) = O(`constant`).
>
> However, this is why Big-O exists; to infer that constants in an algorithm's complexity are relatively meaningless. As long as the complexity does not increase with the growth of the input.

```js
// Accessing an array is O(1)
/* From a game that kids play in the first grade

The "game" teaches how to "make ten" from any number to begin thinking in base 10.
*/
function makeTen(iHave) {
  const array = [10, 9, 8, 7, 6, 5, 4, 3, 2, 1, 0];
  if (!(iHave >= 0 && iHave <= 10)) return undefined;
  return array[iHave];
}
console.log(getNthElementPlusFive([10, 9, 8, 7, 6, 5, 4, 3, 2, 1, 0], 3)); // 12

// This is O(1) even though it has a for loop!
function getNthElementPlusFive(input, n) {
  let result = input[n];
  for (let i = 0; i < 5; i++) {
    result++;
  }
  return result;
}

// Simple arithmetic operations are O(1)
/* This function is a silly solution of calculating the area of a square, merely to illustrate a Big-O concept.

Even though there are additional calculations that would make this O(2 + error checking), the theoretical Big-O notation is O(1)
*/
function areaOfASquare(n) {
  // I could do the calculation multiple times here
  // (as long as the calculation was not dependant on n)
  const result = n * n;
  const anotherResult = n ** 2;
  // I could do error checking here
  if (result !== anotherResult) return undefined;
  // The algorithm is still O(1)
  return result;
}
```

### O(log n)

Doubling the size of n, increases the complexity by 1. (Very good)

> ⓘ Note: Binary search trees operate on this level

```js
// Silly example
function logarithmicExample(data) {
  let numberOfLoops = 0;
  for (let logI = 1; logI < data.length; logI *= 2) {
    numberOfLoops++;
  }
  return numberOfLoops;
}
// Example n=8
console.log(logarithmicExample(Array(8))); // 3

/* Example n=64 w/ explanation:
(1) 64/2=32; 
(2) 32/2=16; 
(3) 16/2=8; 
(4) 8/2=4; 
(5) 4/2=2; 
(6) 2/2=1; 
   1/2=return result
*/
console.log(logarithmicExample(Array(64))); // 6
```

### O($\sqrt n$)

Not typically mentioned due to its obscure usage.

```js
// Given two crystal balls that will break if dropped from high enough distance,
// determine the exact spot in which it will break in the most optimized way.
// (Note: they take 0 damage from each fall, unless they break.)

// This would be a black-box function
function checkIfBallBreaks(floor) {
  return floor > 75 ? true : false;
}

// This is the algorithm
function twoCrystalBalls(buildingHeight) {
  const floor = Math.floor(Math.sqrt(buildingHeight));
  let ballBroken = false;
  let safeFloor = 0;

  // Increment by the square root of the building height
  for (let x = floor; !ballBroken; x += floor) {
    ballBroken = checkIfBallBreaks(x);
    if (ballBroken) {
      console.log("Broke at floor", x);
      break;
    }
    safeFloor = x;
    console.log("Safe:", safeFloor);
  }

  // Backtrack to one floor above the last known safe floor and increment floor by floor until your last crystal ball breaks.
  ballBroken = false;
  for (let x = safeFloor + 1; !ballBroken; x++) {
    ballBroken = checkIfBallBreaks(x);
    if (ballBroken) {
      console.log("Ball broke on floor", x);
      break;
    }
    safeFloor = x;
    console.log("Floor", safeFloor, "is safe...");
  }

  return safeFloor;
}

const g = twoCrystalBalls(300);
console.log(
  `You can drop crystal balls all day from floor ${g} without losing any.`
);
```

### O(n)

Linear complexity, as n grows, so does the complexity in a 1:1 constant.

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

The most simple way I can think to describe this one is: O($log$ $n$) + O($n$). In other words, process the entire data set once, then perform a $log$ $n$ "halving" operation on the same data set.

> ⓘ Personal rule of thumb: An algorithm that performs at this level, or worse, may benefit from optimization.

> ⓘ Note: Semi-safe to assume that sorting operations, using a language's built-in sort, operate on the O($n$ $log$ $n$) time complexity.

> ⓘ Note: Quicksort performs on this level.

```js
// A combination of the O(log n) and O(n) examples above...
function linearLogarithmic(data) {
  let loopCounter = 0;
  // Iterate through every 'n'
  for (let i = 0; i < data.length; i++) {
    // Perform an O(log n) algorithm for each element in the array
    for (let j = 1; j < data.length; j = j * 2) {
      loopCounter++;
    }
  }
  return loopCounter;
}
console.log(linearLogarithmic(Array(64))); // 384 (eg: 64×6; n=64, O(n)=64, O(log n)=6)
```

### O(n$^2$)

Quadratic complexity; an example is to iterate over every element in an array, and then inside of that array, also iterate over every element in that array. Usually not a great practice. Can work for a quick-and-dirty brute force solution. When I'm doing this, my code smell senses begin tingling.

```js
// Naive implementation
// Nested `for` loops
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

### O(n$^3$)

```js
const input = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

// O(n^3)
function sumValuesNested(data) {
  let sum = 0;
  for (let i = 0; i < data.length; i++) {
    for (let j = 0; j < data.length; j++) {
      for (let k = 0; k < data.length; k++) {
        sum += data[k];
      }
    }
  }
  return sum;
}

// O(n) solution for the same problem
const SumValuesBetter = (data) =>
  input.length ** 2 * input.reduce((p, v) => p + v, 0);

// output
console.log(sumValuesNested(input)); // 5500
console.log(sumValuesBetter(input)); // 5500
```

## Graph

Big O is used to ballpark how a particular piece of code may perform.

However, I wanted to know in slightly more concrete terms how much more poorly O(n$^2$) performed against something like O(log n). This graph in conjunction with a concrete data size of 50 really shows how a poor algorithm could eat cpu cycles.

![Big-O Graph][figure-BigOGraph]

> Since writing the Octave code was a bit of a rabbit hole of it's own, I have included it here.

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

## References

| Title                                                                                                                                                             | Site              | Description                                                                     |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------- | ------------------------------------------------------------------------------- |
| [Big O Time Complexity](https://frontendmasters.com/courses/algorithms/big-o-time-complexity/)                                                                    | Frontend Masters  | "The Last Algorithms Course You'll Need" by ThePrimeagen                        |
| [Big O Notation in Javascript](https://www.doabledanny.com/big-o-notation-in-javascript)                                                                          | Doable Danny      | The Ultimate Beginners Guide with Examples                                      |
| [The Big-O Cheat Sheet](https://www.bigocheatsheet.com/)                                                                                                          | Big-O Cheat Sheet | A very cool reference with graphs and data                                      |
| [Step-by-Step Big O Complexity Analysis Guide, using Javscript](https://www.sahinarslan.tech/posts/step-by-step-big-o-complexity-analysis-guide-using-javascript) | Şahin Arslan      | A beginner friendly presentation of Big-O                                       |
| [Big O: Space Complexity](https://dev.to/mwong068/big-o-space-complexity-lcm)                                                                                     | dev.to            | A beginner-level overview of space complexity.                                  |
| [Recursion and Space Complexity](https://dev.to/elmarshall/recursion-and-space-complexity-13gc)                                                                   | dev.to            | Uses an analogy to explain the _very_ basics of space complexity and recursion. |
