# 🚧 Operators <!-- omit from toc -->

Operators can be Logical or Bitwise.

- [Logical Operators](#logical-operators)
  - [OR `||`](#or-)
  - [AND `&&`](#and-)
  - [NOT `!`](#not-)
  - [Nullish Coalescing `??`](#nullish-coalescing-)
  - [Logical Assignment Operators](#logical-assignment-operators)
    - [Logical AND Assignment](#logical-and-assignment)
    - [Logical OR Assignment](#logical-or-assignment)
    - [Nullish Coalescing](#nullish-coalescing)
- [Bitwise Operators](#bitwise-operators)
  - [Bitwise Operators](#bitwise-operators-1)
  - [AND (`a & b`)](#and-a--b)
  - [OR (`a | b`)](#or-a--b)
  - [XOR (`a ^ b`)](#xor-a--b)
  - [NOT (`~a`)](#not-a)
  - [LEFT SHIFT (`a << 1`)](#left-shift-a--1)
  - [RIGHT SHIFT (`a >> 1`)](#right-shift-a--1)
  - [ZERO-FILL RIGHT SHIFT (`a >>> 1`) - Shifts negative bit](#zero-fill-right-shift-a--1---shifts-negative-bit)

# Logical Operators

A logical operator works under the assumption that the entire variable can be evaluated to true or false.

## OR `||`

- Operands are evaluated left --> right
- expressions are converted to boolean, if a true result is reached all comparisons stop and the value is returned
- If all expressions are evaluated as false, the last operand is returned
- The returned value is returned in its _original form, prior to bool conversion_
- Precedence of OR is lower than AND

|   A   |   B   |  Out  |
| :---: | :---: | :---: |
| false | false | false |
| false | true  | true  |
| true  | false | true  |
| true  | true  | true  |

## AND `&&`

- Evaluated left --> right
- Returns the first falsy value encountered
- If all operands are truthy, the last operand is returned
- Precedence of AND is higher than OR

|   A   |   B   |  Out  |
| :---: | :---: | :---: |
| false | false | false |
| false | true  | false |
| true  | false | false |
| true  | true  | true  |

## NOT `!`

- Convert operand to boolean and return the inverse
- Double not (`!!` can be used to convert a value to a boolean)
- Has highest precedence (Higher than OR and AND)

## Nullish Coalescing `??`

## Logical Assignment Operators

Logical assignment is useful in reducing code verbosity. There are only two logical assignment operators.

> ⓘ Logical assignment is not the same as bitwise assignment.

> ⓘ **BOTH** left and right operands must be true boolean values for the resulting assignment to be boolean.

```js
let a = false;
let b = true;
a ||= true; // (false | true) = true
b &&= false; // (true & false) = false
console.log(a, b); // true false
```

### Logical AND Assignment

The [Logical AND Assignment Operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_AND_assignment) tests the variable being assigned, and will only assign the value if the original variable is truthy. **This is a very interesting behavior.**

#### Use Case 1 <!-- omit from toc -->

```js
// map.example is not truthy (undefined is not truthy),
// therefore the assignment is not evaluated.
const obj = {};
obj.example &&= "This will not be set";
console.log(`Nothing Happens: ${obj.example} :: ${obj.undefinedProperty}`);
// Error: undefined :: undefined

// map.example is truthy, so the string is assigned.
map.example = true;
map.example &&= "This will be set";
console.log(`Success: ${map.example}`);
// Success: This will be set
```

### Logical OR Assignment

The [Logical OR Assignment Operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_OR_assignment) tests the variable being assigned, and will only assign the value if the original variable is falsy.

```js
// map.example is falsy, so the "Default String" value is assigned
const map = {};
map.example ||= "Default String";
console.log(`Success: ${map.example}`);
// Success: Default String

// map.example is assigned and therefore truthy, so the value will not be overwritten
map.example ||= 0;
console.log(`NoChange: ${map.example}`);
// Success: Default String

// A potential "gotcha" situation
map.example = 0;
map.example ||= 1;
console.log(`Gotcha: ${map.example}`);
// Gotcha: 1
```

The reason the "Gotcha" situation is potentially dangerous, is in the case that the value for `map.example` has been initialized to a falsy value, the _Logical OR_ operator could potentially unintentially overwrite that default value.

### Nullish Coalescing

The [Nullish Coalescing Assignment Operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Nullish_coalescing_assignment) will only make an assignment if the variable being assigned is nullish. (`null` or `undefined`)

```js
map ??= {};
```

# Bitwise Operators

> ⓘ When applying bitwise operators on numbers, the number is first converted to a 32-bit integer.

> ⓘ Bit masking is generally considered a bad practice in javascript. Aside from odd `Number` issues that can arise from the 64-bit => 32-bit conversion, bit masking tends to make the code more difficult to read, understand, and maintain. Acceptable use case would be in situations where size optimization is absolutely necessary. **Instead**, use an array of booleans or an object with boolean values assigned to named properties.

## Bitwise Operators

## AND (`a & b`)

## OR (`a | b`)

## XOR (`a ^ b`)

## NOT (`~a`)

## LEFT SHIFT (`a << 1`)

## RIGHT SHIFT (`a >> 1`)

## ZERO-FILL RIGHT SHIFT (`a >>> 1`) - Shifts negative bit
