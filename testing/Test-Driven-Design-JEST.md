- [Test Driven Design (TDD)](#test-driven-design-tdd)
  - [Writing Testable Code](#writing-testable-code)
    - [Write Pure Functions](#write-pure-functions)
      - [Pure functions](#pure-functions)
      - [Side Effects](#side-effects)
      - [Fixing Tightly Coupled code](#fixing-tightly-coupled-code)
  - [Setup / Installation](#setup--installation)
  - [Scoping / Test Set-Up](#scoping--test-set-up)
  - [Common Matchers](#common-matchers)
  - [Examples](#examples)

# Test Driven Design (TDD)

TODO:
NOTE: Identification of a weak area: 'Mock'

I need to revisit this topic and put some more time in here after spending some time with TDD.

## Writing Testable Code

[Arrange Act Assert](http://wiki.c2.com/?ArrangeActAssert)

[Testing Asynchronous Code](https://github.com/mrdulin/react-act-examples/blob/master/sync.md)

### Write Pure Functions

#### Pure functions

1. The function always returns the same result if the same arguments are passed in. It does not depend on any state, or data, change during a program’s execution. It must only depend on its input arguments.
2. The function does not produce any observable side effects such as network requests, input and output devices, or data mutation.

#### Side Effects

- Making a HTTP request
- Mutating data
- Printing to a screen or console
- DOM Query/Manipulation
- Math.random()
- Getting the current time
- Depending on global variables / state

#### Fixing Tightly Coupled code

1. Remove dependencies
2. Mock in testing

## Setup / Installation

---

The [Jest](https://jestjs.io/docs/getting-started) website. (Getting Started)

1. Install Jest:

```
npm install --save-dev jest
curl https://raw.githubusercontent.com/github/gitignore/main/Node.gitignore > .gitignore
```

2. Create a JavaScript and Test file:

   - `script.js`
   - `script.test.js`

3. Add the following to the `package.json`:

```
{
  "scripts": {
    "test": "jest"
  }
}
```

4. Run the tests

```
npm test
```

## Scoping / Test Set-Up

```js
// The describe block allows tests to be run with different scope
// in the same file.
describe('Specific tests with scope' () => {
  beforeAll(()=> {});         //...Once
  afterAll(()=> {});          //...Once
  beforeEach(()=> {});        //...Before Each Test
  afterEach(()=> {});         //...After Each Test
  test('do some test', () => {}); //...
})

test.only('ignore all other tests', () {}); // ...
```

## Common Matchers

---

| method                          | description                             |
| ------------------------------- | --------------------------------------- |
| `toBe(value)`                   | Match exact equality                    |
| `toBeGreaterThan(value)`        | Match greater than value                |
| `toBeGreaterThanOrEqual(value)` | Match greater than or equal to value    |
| `toBeLessThan(value)`           | Match less than value                   |
| `toBeLessThanOrEqual(value)`    | Match less than or equal to value       |
| `toBeCloseTo(value)`            | Match against floating point numbers    |
| `not.toBe(value)`               | Match inequality (Opposite of Equality) |
| `not.toBe(value)`               | Match inequality (Opposite of Equality) |
| `toBeNull()`                    | Match only `null`                       |
| `toBeUndefined()`               | Match only `undefined`                  |
| `toBeDefined()`                 | Match everything but `undefined`        |
| `toBeTruthy()`                  | Matches truthy                          |
| `toFeFalsy()`                   | Matches falsy                           |
| `toContain([array])`            | Matches an item in an array or iterable |

## Examples

---

```js
// Testing 'null'
test("null", () => {
  const n = null;
  expect(n).toBeNull();
  expect(n).toBeDefined();
  expect(n).not.toBeUndefined();
  expect(n).not.toBeTruthy();
  expect(n).toBeFalsy();
});

// Testing 'zero'
test("zero", () => {
  const z = 0;
  expect(z).not.toBeNull();
  expect(z).toBeDefined();
  expect(z).not.toBeUndefined();
  expect(z).not.toBeTruthy();
  expect(z).toBeFalsy();
});
```

```js
// Using regex in toMatch()
test("there is no I in team", () => {
  expect("team").not.toMatch(/I/); // ha ha
});
```

```js
// Show that testing works on arrays
test("the shopping list has milk on it", () => {
  const shoppingList = [
    "diapers",
    "kleenex",
    "trash bags",
    "paper towels",
    "milk",
  ];
  expect(shoppingList).toContain("milk");
  expect(new Set(shoppingList)).toContain("milk");
});
```

```js
// Error testing
function compileAndroidCode() {
  throw new Error("you are using the wrong JDK");
}
test("compiling android goes as expected", () => {
  expect(() => compileAndroidCode()).toThrow();
  expect(() => compileAndroidCode()).toThrow(Error);
  // You can also use the exact error message or a regexp
  expect(() => compileAndroidCode()).toThrow("you are using the wrong JDK");
  expect(() => compileAndroidCode()).toThrow(/JDK/);
});
```
