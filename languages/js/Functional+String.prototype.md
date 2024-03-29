# 🚧 TODO: Separate functional and non functional methods

- [🚧 TODO: Separate functional and non functional methods](#-todo-separate-functional-and-non-functional-methods)
- [String](#string)
- [Concatenating](#concatenating)
- [Methods](#methods)
  - [`at(index)`](#atindex)
  - [`charAt(index)`](#charatindex)
  - [`charCodeAt(index)`](#charcodeatindex)
  - [`charAt(index)` OR `variable[index]`](#charatindex-or-variableindex)
  - [`concat()`](#concat)
  - [`endsWith(searchStr, *endPosition=str.length)`](#endswithsearchstr-endpositionstrlength)
  - [`padEnd(stringLength, characterToPadWith)`](#padendstringlength-charactertopadwith)
  - [`padStart(stringLength, characterToPadWith)`](#padstartstringlength-charactertopadwith)
  - [`replace(search, replace)`](#replacesearch-replace)
  - [`slice(start, end)`](#slicestart-end)
  - [`substring(start, end)`](#substringstart-end)
  - [`toLowerCase()`](#tolowercase)
  - [`toUpperCase()`](#touppercase)
  - [`trim()`](#trim)
  - [**DEPRECATED:** ~~`substr(start, length)`~~](#deprecated-substrstart-length)

# String

The MDN [String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) documentation.

# Concatenating

```js
// Template Literal:
// Be careful... eg: sql injection type issues (don't use with user input)
const templateLiteral = `Using Backticks and ${"this syntax"} to join strings`;

// String 'Addition'
// Can be used across source file lines
const plusSymbol = "you can" + " " + "concatinate this way!";
```

# Methods

## `at(index)`

Nearly identical to accessing a string index using square brackets (`str[index]`) or `charAt`.

Returns a new string containing a single character.

- Negative indices will wrap around to the end of the string.
- Only UTF-16 characters are valid, meaning emoji will not be properly handled.
- Out of bounds (outside -str.length to str.length-1) access will return `undefined`

```js
"abcdefghijklmnopqrstuvwxyz".at(-2); // y
"abcdefghijklmnopqrstuvwxyz".at(2); // c
"abcdefghijklmnopqrstuvwxyz".at(-27); // undefined
"abcdefghijklmnopqrstuvwxyz".at(26); // undefined
```

## `charAt(index)`

Nearly identical to accessing a string index using square brackets (`str[index]`) or `at(index)`.

- Only UTF-16 characters are valid, meaning emoji will not be properly handled
- Out of bounds (outside 0 through str.length-1) returns empty string ('')

## `charCodeAt(index)`

    returns utf-16 code

## `charAt(index)` OR `variable[index]`

    returns single character at specified index

## `concat()`

```js
// 'Hello World!'
"Hello".concat(" ", "World", "!");
```

    Useful if you don't want to use the plus operator for concatenation.

## `endsWith(searchStr, *endPosition=str.length)`

Check to see if `searchStr` is at the end of the string, with an optional endPosition index.

```js
"hello world!".endsWith("hello"); // false
"hello world!".endsWith("hello", 5); // true
```

## `padEnd(stringLength, characterToPadWith)`

```js
// repeat character at end of line to specific length
// expected output: "Breaded Mushrooms........"
const str1 = "Breaded Mushrooms";
console.log(str1.padEnd(25, "."));

// expected output: "200  "
const str2 = "200";
console.log(str2.padEnd(5));
```

## `padStart(stringLength, characterToPadWith)`

```js
// For things like months that require 2 digits
// expected output: "05"
const str1 = "5";
console.log(str1.padStart(2, "0"));

// Or to hide parts of sensitive data (hopefully not client side lol)
// expected output: "************5581"
const fullNumber = "2034399002125581";
const last4Digits = fullNumber.slice(-4);
const maskedNumber = last4Digits.padStart(fullNumber.length, "*");
console.log(maskedNumber);
```

## `replace(search, replace)`

    Replaces the first instance of the matched search substring and returns a new string, leaving the original string unchanged.

    Can use regular expression in search

```js
// will return the string: "Moon! Hello, Moon!"
"World! Hello, World!".replace(/World/g, "Moon");
```

## `slice(start, end)`

    Extract part of a string and return the extraction in a new string

    Negative numbers will wrap to the end of the string

## `substring(start, end)`

    Same as slice, but negative numbers are treated as [0]

    Omitting 'end' will extract to the end of the string.

## `toLowerCase()`

    Returns a new string in Lower Case

## `toUpperCase()`

    Returns a new string in Upper Case

## `trim()`

    Remove all whitespace from start and end of the string

## **DEPRECATED:** ~~`substr(start, length)`~~

    Don't use this; Same as substring, except has 'length' as 2nd parameter instead of an index
