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


#### String

##### Concatenating

Template Literal: \`Using Backticks and ${"this syntax"} to join strings\`

##### Methods

(Exhaustive String Method List)[https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String]

* `trim()`
  * Remove all whitespace from start and end
* `slice(start, end)`
  * Extract part of a string and return the extraction in a new string
  * Negative numbers will wrap to the end of the string
* `substring(start, end)`
  * Same as slice, but negative numbers are treated as [0]
  * Omitting 'end' will extract to the end of the string.
* **DEPRECATED:** ~~`substr(start, length)`~~
  * same as substring, except has 'length' as 2nd parameter instead of an index
* `replace(search, replace)`
  * Replaces the first instance of the matched search substring and returns a new string, leaving the original string unchanged.
  * Can use regular expression in search
    * `"World! Hello, World!".replace(/World/g, "Moon");` will return the string: "Moon! Hello, Moon!"
* `toUpperCase()`
* `toLowerCase()`
* `concat()`
  * `"Hello".concat(" ", "World", "!")`
  * Useful if you don't want to use the plus operator for concatenation.
* `padStart(stringLength, characterToPadWith)`
* `padEnd(stringLength, characterToPadWith)`
* `charAt(index)` OR `variable[index]`
  * returns single character at specified index
* `charCodeAt(index)`
  * returns utf-16 code



#### Array

##### Properties

* length

##### Methods

* sort()
* includes(item)
* toString(): convert the contents of the array into a string
* join(strBetweenElements): convert the contents of the array into a string, specifying what to place between elements
* pop(): remove and return last element in array
* push(element): adds element to end of the array and returns new array length
* shift(): remove and return first element in array
* unshift(element): adds element to beginning of the array and returns new array length
* concat(array, …): adds array(s) to the end of this array
* splice(atIndex, deleteHowMany, item(s), …): insert items into an array, and optionally remove items
* slice(start, end=last): return a new array containing elements from start to end


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
