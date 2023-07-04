- [Data Types and Structures](#data-types-and-structures)
  - [Primative Values](#primative-values)
    - [Null](#null)
    - [Undefined](#undefined)
    - [Boolean](#boolean)
    - [Number](#number)
    - [BigInt](#bigint)
    - [String](#string)
    - [Symbol](#symbol)
  - [Object](#object)

# Data Types and Structures

> TODO: Note to future self:
> This is (currently) basically a copy of [JavaScript data types and data structures](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures)
>
> The reason I started this page was because I have had to look up javascript `dictionary`, `map`, and `object` differences quite a few times. I want to combine several resources here and make kind of an end-all-be-all data structure page here.
>
> I think I have taken notes on some data structures? (BST, Graph, etc?) I know I have separate Array, Object, and String notes. They need to be linked into this document. I may create a `data-structures` folder to keep those in, and link into that from this main document. The main `js` folder is getting a bit large.

## Primative Values

| Type      | `typeof` return value |
| --------- | --------------------- |
| Null      | object                |
| Undefined | undefined             |
| Boolean   | boolean               |
| Number    | number                |
| BigInt    | bigint                |
| String    | string                |
| Symbol    | symbol                |

### Null

Null can only be `null`.

Null is required at the end of a `prototype.chain`

`null` is a keyword.

### Undefined

- `return;` is the same as `return undefined;`
- Accessing an object property that doesn't exist is `undefined` (eg: `obj.iDoNotExist` will return `undefined`)
- Variable declaration without initialization will initialize the varaible to `undefined`. (eg: `const x;` is the same as `const x = undefined;`)
- Many methods (such as `Array.prototype.find()`) will return `undefined` when an element is not found.

`undefined` is an identifier (not a keyword) that happens to be a global property. `undefined` should not be redefined or shadowed.

### Boolean

`true` or `false`

### Number

Double precision 64-bit value, capable of storing floating-point numbers between ±(2^-1074 and 2^1024). Numbers smaller than Number.MIN_VALUE are converted to ±0. Numbers outside of the 2^1074 range are converted to ±Infinity.

-0 does exist, but is only noticable when you do something like "divide by zero," in which case 42/-0 will yield -Infinity.

`NaN` is a special kind of number where the result of an arithmatic operation cannot be expressed as a number.

### BigInt

Data type that can represent integers with arbitrary magnitude.

> TODO: (Source? I tried `1234512345123451234512345123451234512345n === 1234512345123451234512345123451234512345n` and it evalued to `true`) <==> BigInts are not strictly equal to another with the same mathematical vlue. (`1n === 1n` evaluates to `false`)

To specify a bigint, add a `n` to the end of the number.

A `TypeError` is thrown if a BigInt and a standard Number are used together in an expression or if they are implicitly converted to each other.

```js
const big = 123456789012345678901234567890n;
console.log(big + 1n);
// 123456789012345678901234567891n
```

Standard numerical operators work with BigInts. (`+`, `-`, `*`, `**`, `/`, and `%`)

### String

See my [String](js-string.md) documentation.

### Symbol

A [Symbol](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Symbol) is a unique and immutable primitive value and may be used as the key of an Object property (see below). In some programming languages, Symbols are called "atoms". The purpose of symbols is to create unique property keys that are guaranteed not to clash with keys from other code.

## Object

> TODO: Finish this section
>
> https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures
>
> (see above)
