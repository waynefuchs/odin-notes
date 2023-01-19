- [Array](#array)
  - [Creation](#creation)
    - [Speed](#speed)
  - [Properties](#properties)
  - [Methods](#methods)
    - [`sort()`](#sort)
    - [`includes(item)`](#includesitem)
    - [`toString()`](#tostring)
    - [`join(strBetweenElements)`](#joinstrbetweenelements)
    - [`pop()`](#pop)
    - [`push(element)`](#pushelement)
    - [`shift()`](#shift)
    - [`unshift(element)`](#unshiftelement)
    - [`concat(array, …)`](#concatarray-)
    - [`splice(atIndex, deleteHowMany, item(s), …)`](#spliceatindex-deletehowmany-items-)
    - [`slice(start, end=last)`](#slicestart-endlast)

# Array

## Creation

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

### Speed

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

## Properties

- length

## Methods

### `sort()`

### `includes(item)`

### `toString()`

convert the contents of the array into a string

### `join(strBetweenElements)`

convert the contents of the array into a string, specifying what to place between elements

### `pop()`

remove and return last element in array

### `push(element)`

adds element to end of the array and returns new array length

### `shift()`

remove and return first element in array

### `unshift(element)`

adds element to beginning of the array and returns new array length

### `concat(array, …)`

adds array(s) to the end of this array

### `splice(atIndex, deleteHowMany, item(s), …)`

insert items into an array, and optionally remove items

### `slice(start, end=last)`

return a new array containing elements from start to end
