- [String](#string)
  - [## Reference](#-reference)
  - [## Concatenating](#-concatenating)
  - [## Regular Expressions](#-regular-expressions)
    - [**TODO**: *Add this section some day as a refresher*](#todo-add-this-section-some-day-as-a-refresher)
  - [## Methods](#-methods)
    - [`charCodeAt(index)`](#charcodeatindex)
    - [`charAt(index)` OR `variable[index]`](#charatindex-or-variableindex)
    - [`concat()`](#concat)
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

## Reference
---
[Exhaustive String Method List](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)


## Concatenating
---

``` js
// Template Literal: 
// Be careful... eg: sql injection type issues (don't use with user input)
const templateLiteral = `Using Backticks and ${"this syntax"} to join strings`

// String 'Addition'
// Can be used across source file lines
const plusSymbol = 'you can' + ' ' + 
    'concatinate this way!';
```

## Regular Expressions
---

### **TODO**: *Add this section some day as a refresher*

Perhaps this should be in `js-string-regular-expressions.md`?


## Methods
---

### `charCodeAt(index)`

    returns utf-16 code

### `charAt(index)` OR `variable[index]`

    returns single character at specified index

### `concat()`

``` js
// 'Hello World!'
"Hello".concat(" ", "World", "!")
```

    Useful if you don't want to use the plus operator for concatenation.


### `padEnd(stringLength, characterToPadWith)`


### `padStart(stringLength, characterToPadWith)`

``` js
// For things like months that require 2 digits
// expected output: "05"
const str1 = '5';
console.log(str1.padStart(2, '0'));

// Or to hide parts of sensitive data (hopefully not client side lol)
// expected output: "************5581"
const fullNumber = '2034399002125581';
const last4Digits = fullNumber.slice(-4);
const maskedNumber = last4Digits.padStart(fullNumber.length, '*');
console.log(maskedNumber);
```

### `replace(search, replace)`

    Replaces the first instance of the matched search substring and returns a new string, leaving the original string unchanged.

    Can use regular expression in search

``` js
// will return the string: "Moon! Hello, Moon!"
"World! Hello, World!".replace(/World/g, "Moon");
```


### `slice(start, end)`

    Extract part of a string and return the extraction in a new string

    Negative numbers will wrap to the end of the string


### `substring(start, end)`

    Same as slice, but negative numbers are treated as [0]

    Omitting 'end' will extract to the end of the string.



### `toLowerCase()`

    Returns a new string in Lower Case

### `toUpperCase()`

    Returns a new string in Upper Case

### `trim()`

    Remove all whitespace from start and end of the string





### **DEPRECATED:** ~~`substr(start, length)`~~

    Don't use this; Same as substring, except has 'length' as 2nd parameter instead of an index
