# Functional Array.prototype <!-- omit in toc -->

- [every](#every)
- [fill](#fill)
- [filter](#filter)
- [find | findIndex | findLast | findLastIndex](#find--findindex--findlast--findlastindex)
- [flat](#flat)
- [flatMap](#flatmap)
- [forEach](#foreach)
- [includes](#includes)
- [map](#map)
- [reduce](#reduce)
- [some](#some)
- [⚠️ sort](#️-sort)

[`Array.prototype` Mozilla Reference](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)

# every

Returns `true`|`false` on whether all elements pass the implemented test.

```js
// return `true` if every element is a number
[1, "a", 2, 3, 4].every((n) => !isNaN(n));
```

# fill

Changes specified elements to a static value.
`[].fill(StaticValue, StartIndex, ToIndex=EndOfArray)`

```js
// return: [1,99,99,4]
[1, 2, 3, 4].fill(99, 1, 3);
```

# filter

Return a new array, removing all elements that do not pass the implemented test.

```js
// return: [1,2,3,4] (remove 'a')
[1, "a", 2, 3, 4].filter((n) => !isNaN(n));
```

# find | findIndex | findLast | findLastIndex

|          Method | Description                                                                   |
| --------------: | ----------------------------------------------------------------------------- |
|          `find` | Return the **value** of the first element that satisfies the testing function |
|     `findIndex` | Return the **index** of the first element that satisfies the testing function |
|      `findLast` | Identical to `find`, except iterated in reverse                               |
| `findLastIndex` | Identical to `findIndex`, except iterated in reverse                          |

```js
// returns the 3rd element (99)
[0, 0, 99, 105].find((n) => n > 2);

// returns the 3rd element's index (2)
[0, 0, 99, 105].findIndex((n) => n > 2);

// returns the 4th element (105)
[0, 0, 99, 105].findLast((n) => n > 2);

// returns the 4th element's index (3)
[0, 0, 99, 105].findLastIndex((n) => n > 2);
```

# flat

Flatten an array, traversing into the array by `depth` amount. `flat(depth)` where depth defaults to 1.

`null` and `undefined` are left unaffected.

```js
// returns [1, 2, [3, 4], 5]
[1, 2, [[3, 4], 5]].flat(); // flat() = flat(1)

// returns [1, 2, 3, 4, 5]
[1, 2, [[3, 4], 5]].flat(2);
```

# flatMap

Combine `map` + `flat(1)` into a single operation.

```js
// [ false, 'foo', 'bar', false ]
[1, 2, 3].flatMap((n) => (n === 2 ? ["foo", "bar"] : false));
```

# forEach

Execute a provided function once for each element
`forEach((element, index, array) => {})`

```js
[1, 2, 3, 4].forEach((element, index, array) => {
  console.dir(array);
  console.log(`${element}:${index}`);
});
```

# includes

Return bool indicating whether specified element is contained in array.

# map

Map Elements to Results
`map((element, index, array) => {})`

```js
// input:   [1, 2, 3, 4]
// map:     (x+1)
// result:  [2, 3, 4, 5]
[1, 2, 3, 4].map((i) => i + 1);
```

# reduce

Combine all elements together in some manner.

`reduce((previousValue, currentValue, currentIndex, array) => {}, initialValue);`

Examples:

- Find Minimum Value
- Find Maximum Value
- Sum all values

```js
// Sum all values (10)
[1, 2, 3, 4].reduce((pv, cv) => pv + cv, 0);
```

# some

Test whether at least one element in the array passes the implemented test.

# ⚠️ sort

Sort is not functional, as it mutates the array. It can still be useful.

```js
const month = {
  January: 1,
  Jan: 1,
  February: 2,
  Feb: 2,
  March: 3,
  Mar: 3,
  April: 4,
  Apr: 4,
  May: 5,
  June: 6,
  Jun: 6,
  July: 7,
  Jul: 7,
  August: 8,
  Aug: 8,
  September: 9,
  Sep: 9,
  Sept: 9,
  October: 10,
  Oct: 10,
  November: 11,
  Nov: 11,
  December: 12,
  Dec: 12,
};
["March", "Jan", "February", "Dec"].sort(function (a, b) {
  return month[a] > month[b] ? 1 : month[a] === month[b] ? 0 : -1;
});
```
