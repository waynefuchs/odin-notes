# Array <!-- omit in toc -->

Arrays are fixed-size contiguous memory chunks. The javascript implementation has _many_ helper methods.

> ⓘ An Array in javascript isn't actually an array, it is technically a List.
>
> Unless you consider performance, memory, and garbage collection; you can ignore the distinction between lists and arrays, and most people in the javascript world use `list` and `array` interchangeably.
>
> A list can be resized and behaves like a linked list with the ability to insert items into the array.
>
> The [ArrayBuffer](./ArrayBuffer.md) data structure in javascript behaves like a traditional C-style array.

- [Array Creation](#array-creation)
  - [Speed](#speed)
- [Properties](#properties)
- [Methods](#methods)
  - [`includes(item, *fromIndex)`](#includesitem-fromindex)
  - [`join(strBetweenElements)`](#joinstrbetweenelements)
  - [`pop()`](#pop)
  - [`push(element)`](#pushelement)
  - [`reverse()`](#reverse)
  - [`shift()`](#shift)
  - [`slice(start, end=last)`](#slicestart-endlast)
  - [`sort()`](#sort)
  - [`splice(atIndex, *deleteCount, *...item)`](#spliceatindex-deletecount-item)
  - [🔥 `toReversed()`](#-toreversed)
  - [🔥 `toSorted()`](#-tosorted)
  - [🔥 `toSpliced(start, *deleteCount, *...items)`](#-tosplicedstart-deletecount-items)
  - [`toString()`](#tostring)
  - [`unshift(element)`](#unshiftelement)
  - [🔥 `with(index, replaceValue)`](#-withindex-replacevalue)

# Array Creation

There are many ways to create arrays in JavaScript. Here are a few common ones.

```js
// Method 1
const arr = [1, 2, 3];

//Method 2
const length = 3;
const arr = new Array(length); // each index is initialized to `undefined`
arr[0] = 1;
arr[1] = 2;
arr[3] = 3;

// Method 3
const arr = Array.of((1, 2, 3));

// Method 4
const length = 3;
let a;
(a = []).length = length;
a[0] = 1;
a[1] = 2;
a[3] = 3;

// Method 5
let a = [];
a.push(1);
a.push(2, 3);

// Method 6
let a = [];
a.unshift(3);
a.unshift(2);
a.unshift(1);
```

## Speed

I have looked this up a few times. Stack Overflow actually has some conflicting and really bad information in the result that keeps getting suggested to me through google. So I set up a rudimentary test for myself. It looks like creating an array with the `new Array(#)` constructor, and self-initializing it to 0 is the most efficient; with map() not too far behind. Fill, on the other hand, takes a significant amount of time. I would guess that error checking is taking place.

```js
// Test E: 1.662s
// The winner
const a = new Array(50000000);
for (i = 0; i < a.length; i++) a[i] = 0;
```

```js
// Test C: 1.725s
(a = []).length = 50000000;
for (i = 0; i < a.length; i++) a[i] = 0;
```

```js
// Test D: 2.175s
// This one looks clean, but allocates the memory twice
const a = [...new Array(50000000)].map((v) => 0);
```

```js
// Test A: 6.376s
// My favorite in terms of clear intent.. but for large arrays, it will be slow
const a = new Array(50000000).fill(0);
```

```js
// Test B: 6.449s
(a = []).length = 50000000;
a.fill(0);
```

# Properties

- length

# Methods

This is a non-inclusive list, more along the lines of methods that I was looking up frequently as I transitioned from other languages to javascript at the beginning of my Odin journey. See the MDN [Array.prototype](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) page for an inclusive list.

## `includes(item, *fromIndex)`

Checks to see if `item` exists in the array. There are some "gotchas" that you can read about in MDN's [Array.prototype.includes()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/includes) page.

## `join(strBetweenElements)`

Returns a new string containing the contents of each array element converted into a string, with `strBetweenElements` placed between every element.

## `pop()`

Mutates the array, removing and returning the last element in the array.

## `push(element)`

Mutates the array, adding an element to end of the array and returns new array length

## `reverse()`

Mutates the array in to reverse order.

## `shift()`

remove and return first element in array

## `slice(start, end=last)`

return a new array containing elements from start to end

## `sort()`

Mutates the array into sorted order.

## `splice(atIndex, *deleteCount, *...item)`

Returns an array containing the removed items.

Mutates the array to contain remaining items, with `item`s added at the selection point.

```bash
# Define an array
> m = [1, 2, 3, 4]
[ 1, 2, 3, 4 ]

#          | Index 1
#          |  | 1 item replaced (the 2)
#          |  |  |-----| inserting [5, 6, 7] at index 1
> m.splice(1, 1, 5, 6, 7)
[ 2 ]

# Results in: [1] + [5, 6, 7] + [3, 4], or:
> m
[ 1, 5, 6, 7, 3, 4 ]
```

## 🔥 `toReversed()`

> ⚠️ Requires Node 20.0.0+

Returns a copy of the array in sorted order.

## 🔥 `toSorted()`

> ⚠️ Requires Node 20.0.0+

Returns a copy of the array in sorted order.

## 🔥 `toSpliced(start, *deleteCount, *...items)`

> ⚠️ Requires Node 20.0.0+

Return a new array with some elements removed and/or replaced

insert items into an array, and optionally remove items

## `toString()`

Returns a new string containing the contents of the array as a comma separated string.

> ⚠️ Warning: There may be unpredictable results if the array contains elements that produce commas when processed to strings.

```
> [1, 2, 3, "4,", 5].toString()
'1,2,3,4,,5'
```

## `unshift(element)`

adds element to beginning of the array and returns new array length

## 🔥 `with(index, replaceValue)`

> ⚠️ Requires Node 20.0.0+

Returns a copy of the array with the value at `index` replaced with `replaceValue`.
