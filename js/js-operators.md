- [Operators](#operators)
  - [Bitwise Operators # TODO: UNFINISHED](#bitwise-operators--todo-unfinished)
  - [Logical Assignment Operators](#logical-assignment-operators)
    - [Logical AND](#logical-and)
    - [Logical OR](#logical-or)
    - [Nullish Coalescing](#nullish-coalescing)


# Operators

## Bitwise Operators # TODO: UNFINISHED

> Note: When applying bitwise operators on numbers, the number is first converted to a 32-bit integer.

> Note: Bit masking is generally considered a bad practice in javascript. Aside from odd `Number` issues that can arise from the 64-bit => 32-bit conversion, bit masking tends to make the code more difficult to read, understand, and maintain. Acceptable use case would be in situations where size optimization is absolutely necessary.
> 
> Instead: Use an array of booleans or an object with boolean values assigned to named properties.

> TODO: This section is unfinished

## Logical Assignment Operators

Note that Logical Asignment does not work to define variables. The variable must have been, at the least, previously defined. As far as I can tell, these operators are *only* useful when used on map/dictionary keys.

### Logical AND

The [Logical AND Assignment Operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_AND_assignment) tests the variable being assigned, and will only assign the value if the original variable is truthy.

``` js
// map.example is not truthy, so no change is made.
const map = {};
map.example &&= "This will not be set";
console.log(`Error: ${map.example} :: ${map.fusrohdah}`);
// Error: undefined :: undefined

// map.example is truthy, so the string is assigned.
map.example = true;
map.example &&= "This will be set";
console.log(`Success: ${map.example}`);
// Success: This will be set
```

### Logical OR

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

The reason the "Gotcha" situation is potentially dangerous, is in the case that the value for `map.example` has been initialized to a falsy value, the *Logical OR* operator could potentially unintentially overwrite that default value.

### Nullish Coalescing

The [Nullish Coalescing Assignment Operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Nullish_coalescing_assignment) will only make an assignment if the variable being assigned is nullish. (`null` or `undefined`)

```js
map ??= {}

```