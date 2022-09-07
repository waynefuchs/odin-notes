- [Javascript](#javascript)
  - [Problem Solving](#problem-solving)
  - [Errors](#errors)
  - [Clean Code](#clean-code)
  - [Scope vs. Context](#scope-vs-context)
  - [Variables](#variables)
    - [Defining](#defining)
    - [Types](#types)
      - [Number](#number)
        - [Methods](#methods)
  - [Logical Operators](#logical-operators)
  - [Bitwise Operators](#bitwise-operators)
  - [Regular Expressions](#regular-expressions)
  - [Functions](#functions)
    - [Naming Guidelines](#naming-guidelines)
    - [Verb List](#verb-list)
      - [Alteration](#alteration)
      - [Creation](#creation)
      - [Establishment](#establishment)
      - [Obtain Data](#obtain-data)
      - [True or False](#true-or-false)

# Javascript

## Problem Solving

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

## Errors

* Syntax: not following grammatical rules for JS
* Reference: Referencing something that doesn't exist
* Type: Trying to perform some action on data inappropriately, or modifying a value that cannot be changed

## Clean Code

> Code Tells You How, Comments Tell You Why

(AirBnB's JavaScript Style Guide)[https://github.com/airbnb/javascript]

(Google's Style Guide for JS)[https://google.github.io/styleguide/jsguide.html]

(JavaScript Standard Style)[https://standardjs.com/rules.html] Used by companies like NPM and GitHub


## Scope vs. Context

* Scope: What variables you have access to
* Context: What `this` points at


## Variables

### Defining

* `let`: use this keyword to define mutable variables
* `const`: use this keyword to define immutable variables
* var (older)

### Types

The following are **primatives**:
1. `Number`
1. `BigInt`: Any number larger than (+/-)(2^53)-1 (9_007_199_254_740_991) - 9 quadrillion. **Note**: Add a 'n' to the end of the number while defining.
1. `String`
1. `Boolean`
1. `null`
1. `undefined`
1. `symbol`
1. `object` <== Special (Not primitive)


#### Number

##### Methods

* toFixed(decimalPlaces): returns a string containing a number rounded to the specified decimal places.

## Logical Operators

`||` (OR)

* Operands are evaluated left --> right
* expressions are converted to boolean, if a true result is reached all comparisons stop and the value is returned
* If all expressions are evaluated as false, the last operand is returned
* The returned value is returned in its *original form, prior to bool conversion*
* Precedence of OR is lower than AND

```
A       B       Out
false   false   false
false   true    true
true    false   true
true    true    true
```

`&&` (AND)

* Evaluated left --> right
* Returns the first falsy value encountered
* If all operands are truthy, the last operand is returned
* Precedence of AND is higher than OR

```
A       B       Out
false   false   false
false   true    false
true    false   false
true    true    true
```

`!` (NOT)

* Convert operand to boolean and return the inverse
* Double not (`!!` can be used to convert a value to a boolean)
* Has highest precedence (Higher than OR and AND)

`??` (Nullish Coalescing)

## Bitwise Operators

* AND `a & b`
* OR `a | b`
* XOR `a ^ b`
* NOT `~a`
* LEFT SHIFT `a << 1`
* RIGHT SHIFT `a >> 1`
* ZERO-FILL RIGHT SHIFT `a >>> 1` (Shifts negative bit)


## Regular Expressions

(A video series on js regular expressions)[https://www.youtube.com/playlist?list=PL4cUxeGkcC9g6m_6Sld9Q4jzqdqHd2HiD]
I know perl regular expressions pretty well. I don't know that I have the patience to sit through an hour and a half of regular expression training right now. But it looks like a pretty decent resources, so I'm saving it here.

## Functions

### Naming Guidelines

* Should usually start with a verb
* One action per function (Don't pop up an alert in a "getAge" function, just return the value and let the calling function handle it from there.)
* Don't use ultrashort function names, instead choose "concise and descriptive" names.

### Verb List

#### Alteration
*	add
*	append
*	change
*	delete
*	disable
*	edit
*	hide
*	join
*	merge
*	remove
*	save
*	separate
*	set
* show
*	split
*	store
*	update

#### Creation
*	clone
*	copy
*	create
*	generate
*	make

#### Establishment
* being
* open
* start

#### Obtain Data
* check
*	close
*	fetch
*	find
*	get
*	read
*	retrieve
*	search

#### True or False
*	can
*	has
*	is
*	should
