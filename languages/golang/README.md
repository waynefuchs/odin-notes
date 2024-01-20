# Golang

# My journey

- [Google Search turned up this reddit page](https://www.reddit.com/r/golang/comments/1465pwq/fastest_way_to_learn_golang/)
- [A Tour of Go](https://go.dev/tour/welcome/1)
  - `shift`-`enter`: compile and run
  - `ctrl`-`enter`: format using `gofmt`
- CURRENT https://go.dev/tour/flowcontrol/1

# Basics

## Packages, variables, and functions.

### Packages

- Programs start running in package `main`
- Imports should be parenthesized into a "factored" import statement, but can be individually imported (bad style)
- Capitalization defines exported variables `Pi` is exported, `pi` is not.

| package     | description |
| ----------- | ----------- |
| `fmt`       |             |
| `math/rand` |             |

### Variables

- inside of a function, _short assignment_ can be used in place of `var` for implicit typing
- defined with the `var` or `const` keywords
- `const` cannot be declared using the `:=` syntax
- defined at package or or function level (scope)
- Variable declarations may be "factored" into blocks, just like import statements

```go
func main() {
  var explicit int = 42
  implicit := 42 + 1
}
```

#### Basic types

- if an integer is needed, use `int` unless you have a specific reason to use a sized or unsigned integer type
- `int` will be 32 bits or 64 bits depending on the architecture of the system
- variables that are declared uninitialized are assigned their zero value
  - `0` for numeric types
  - `false` for boolean types
  - `""` for strings
  - Type conversion can occur with `T(v)` which converts the value `v` to the type `T`; numeric <-> string conversions do not work

| Type                                                       |
| ---------------------------------------------------------- |
| `bool`                                                     |
| `string`                                                   |
| **`int`** `int8` `int16` `int32` `int64`                   |
| `uint` `uint8` `uint16` `uint32` `uint64` `uintptr`        |
| `byte` (alias for uint8)                                   |
| `rune` (alias for uint32; represents a unicode code point) |
| `float32` `float64`                                        |
| `complex64` `complex128`                                   |

```go
// Example of "factoring" variable declarations
var (
	ToBe   bool       = false
	MaxInt uint64     = 1<<64 - 1
	z      complex128 = cmplx.Sqrt(-5 + 12i)
)
```

### Functions

- If param types are the same, the type can be omitted from all but the last parameter. (see `funcName2`)
- Functions can return any number of results
- Naked returns should only be used in short functions; generally avoid

```go
// in function declaration, the type comes *after* the variable name
func funcName(paramName int, paramName2 int) {
  // do something
  return 1, 2, 3
}

// This is equivalent to the function above
func funcName2(paramName, paramName2 int) {
  // do something
  return 1, 2, 3
}

func divide(divisor, dividend int) (quotient, remainder int) {
  quotient = divisor / dividend
  remainder = divisor % dividend
  return
}
```

## Flow control statements: for, if, else, switch and defer

### for

Go only has the `for` looping construct taking in `init` (optional); `condition`; `post` (optional) without parentheses, like python. Curly braces are _always required_. If init and post are dropped, the semicolons can also be dropped, effectively making `for` into an alias for `while`

### if

If statements can start with an `init` statement to execute before the condition. `if` `init`; `condition` `{}`; initialized variables are only in scope until the end of the `if` block, **which also includes** follow-on `else if` and `else blocks`.

## More types: structs, slices, and maps.

Learn how to define types based on existing ones: this lesson covers structs, arrays, slices, and maps.

# Methods and interfaces

Learn how to define methods on types, how to declare interfaces, and how to put everything together.

## Methods and interfaces

This lesson covers methods and interfaces, the constructs that define objects and their behavior.

# Generics

Learn how to use type parameters in Go functions and structs.

## Generics

Go supports generic programming using type parameters. This lesson shows some examples for employing generics in your code.

# Concurrency

Go provides concurrency features as part of the core language.

This module goes over goroutines and channels, and how they are used to implement different concurrency patterns.

## Concurrency

Go provides concurrency constructions as part of the core language. This lesson presents them and gives some examples on how they can be used.
