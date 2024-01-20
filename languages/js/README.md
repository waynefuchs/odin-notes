# 🚧 Javascript <!-- omit from toc -->

Javascript is the path that I chose for The Odin Project.

- [Problem Solving](#problem-solving)
- [Errors](#errors)
- [Clean Code](#clean-code)
- [Variables](#variables)
  - [Defining](#defining)
    - [🚧 Number](#-number)
      - [Methods](#methods)
- [Scope](#scope)
  - [Variable Shadowing](#variable-shadowing)
- [Context](#context)
- [Regular Expressions](#regular-expressions)
- [Functions](#functions)
  - [Naming Guidelines](#naming-guidelines)
  - [Verb List](#verb-list)
    - [Alteration](#alteration)
    - [Creation](#creation)
    - [Establishment](#establishment)
    - [Obtain Data](#obtain-data)
    - [True or False](#true-or-false)
- [Destructuring Assignment](#destructuring-assignment)

# Problem Solving

1. Understand the Problem
2. Plan
   1. How does the program look? (Sketch UI)
   2. What functionality will the UI have?
   3. What inputs will the program require?
   4. Does the data come from a user, or from a data set?
   5. What is the desired output?
   6. What are the steps required to go from input --> output?
3. Divide and Conquer
   1. Pseudocode (Write the instructions to solve the problem in plain english)
   2. Write the solution

# Errors

- Syntax: not following grammatical rules for JS
- Reference: Referencing something that doesn't exist
- Type: Trying to perform some action on data that is inappropriate, or modifying a value that cannot be changed.

# Clean Code

> Code Tells You How, Comments Tell You Why

[AirBnB's JavaScript Style Guide](https://github.com/airbnb/javascript)

[Google's Style Guide for JS](https://google.github.io/styleguide/jsguide.html)

[JavaScript Standard Style](https://standardjs.com/rules.html)

# Variables

## Defining

- `let`: use this keyword to define mutable variables
- `const`: use this keyword to define immutable variables
- `var`: (old style, avoid use)

### 🚧 Number

Split this out into its own file, like String.

#### Methods

- toFixed(decimalPlaces): returns a string containing a number rounded to the specified decimal places.

# Scope

What variables are accessible.

## Variable Shadowing

Variable shadowing is reuse of a variable name in an inner scope. It should go without saying that variable shadowing is generally a code smell. The Wikipedia article on [Scope (computer science)](<https://en.wikipedia.org/wiki/Scope_(computer_science)>) has a really good language agnostic overview.

Scope, in javascript, should generally be limited to `global`,

```js
function example() {
  // The `const` keyword affects scope throughout the entire scope level
  // The following line would break access to the `example()` function,
  // even if it is the last line in this function! (Due to variable hoisting)
  // This manifests as a ReferenceError: Cannot access before initialization
  // ---------------------------------------------------------------------------
  // const example = "moo";
  if (typeof example === "function") {
    const example = "I am shadowing the outer function variable, `example`";
    if (typeof example === "string") {
      const example = 7n;
      if (typeof example === "bigint") {
        const example = 3;
        console.log("innermost level 4", example);
      }
      console.log("level 3", example);
    }
    console.log("level 2", example);
  }
  console.log("level 1", example);
}
example();
console.log("still a function in 'global scope'", example);
```

# Context

What `this` points at.

# Regular Expressions

[A video series on js regular expressions](https://www.youtube.com/playlist?list=PL4cUxeGkcC9g6m_6Sld9Q4jzqdqHd2HiD)

I know perl regular expressions pretty well. I don't know that I have the patience to sit through an hour and a half of regular expression training right now. But it looks like a pretty decent resources, so I'm saving it here.

# Functions

## Naming Guidelines

- Functions should usually start with a verb
- One action per function (Don't pop up an alert in a "getAge" function, just return the value and let the calling function handle it from there.)
- Don't use ultrashort function names, instead choose "concise and descriptive" names.

## Verb List

Words on this list can be prefixed to function names to provide clarity for what a function is doing. For example, `getList` can provide context, but `fetchListFromAPINAME` is more specific.

### Alteration

add, append, change, delete, disable, edit, hide, join, merge, remove, save, separate, set, show, split, store, update

### Creation

clone, copy, create, generate, make

### Establishment

being, open, start

### Obtain Data

check, close, fetch, find, get, read, retrieve, search

### True or False

can, has, is, should

# Destructuring Assignment

Destructuring is the assignment of variables through the unpacking of an object.

> ⓘ You can do some really neat things with this (destructuring) tool.

MDN [Destructuring assignment](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment) documentation.

```js
// Arrays
const [a, b] = array; // if array = [1, 2], then a=1 and b=2
const [a, , b] = array; // if array = [1, 2, 3] then a=1 and b=3

// Objects (Dicts)
const { a, b } = obj;
```
