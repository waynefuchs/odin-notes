# Design Patterns <!-- omit in toc -->

Design patterns are generic repeatable solutions to commonly occurring problems in software design using SOLID principles.

(Language Proficiency -> Data Structures & Algorithms -> Design Patterns)

- [Singleton](#singleton)
  - [Use cases](#use-cases)
  - [Caveats](#caveats)
  - [Example](#example)
- [🚧 Facade](#-facade)
  - [Use cases](#use-cases-1)
  - [Caveats](#caveats-1)
- [🚧 Bridge / Adapter](#-bridge--adapter)
  - [Use Cases](#use-cases-2)
  - [Caveats](#caveats-2)
- [🚧 Strategy](#-strategy)
  - [Use Cases](#use-cases-3)
- [🚧 Observer](#-observer)
  - [Caveats](#caveats-3)
- [Composite Design](#composite-design)
- [References](#references)

# Singleton

An object (class, module, etc) can only have one instance. Accessing that object from anywhere in your codebase will access the same instance.

## Use cases

- **A database driver**- Need to be able to access a database connection in many places across multiple files.
- **A configuration manager**- User configurable options in an application.

## Caveats

[From StackOverflow](https://stackoverflow.com/questions/137975/what-are-drawbacks-or-disadvantages-of-singleton-pattern)

- It is difficult to remove a singleton from an existing application in the event you no longer wish to use it, and will usually require a large refactor.
- They are generally used as a global instance, why is that so bad? Because you hide the dependencies of your application in your code, instead of exposing them through the interfaces. Making something global to avoid passing it around is a code smell.
- They violate the single responsibility principle: by virtue of the fact that they control their own creation and lifecycle.
- They inherently cause code to be tightly coupled. This makes faking them out under test rather difficult in many cases.
- They carry state around for the lifetime of the application. Another hit to testing since you can end up with a situation where tests need to be ordered which is a big no no for unit tests. Why? Because each unit test should be independent from the other.

## Example

```js
// my-singleton.js
const somePrivateState = [];
function privateFn() {} // ...

export default {
  method1() {}, // ...
  method2() {}, // ...
};
```

```js
// program-file.js
import myInstance from "./my-singleton.js";
```

# 🚧 Facade

Simplify program internals by serving a front-facing interface (api) that masks the complex underlying structural code. (Similar to a facade on the face of a factory hiding the work that goes on within.)

## Use cases

- **Compiler**- Allow the end user to access the incredibly complex functionality of a compiler without understanding how the entire thing works.

## Caveats

- An api can become oversimplified to the extent that it is no longer valuable
- The facade can become so specific to a single use case that it is no longer a generalized pattern

# 🚧 Bridge / Adapter

This pattern is meant to be used to decouple an abstraction from its implementation so that the two can vary independently.

## Use Cases

- **Database Interface**- You can abstract what database is being used and link to concrete implementations through the bridge / adapter.

## Caveats

- Can be used too much. (Don't overuse; this pattern can usually be easily be implemented after initial implementation) In the example of a "camera body" with the "lens bridge" so various lenses can be attached to the body; that is a desirable feature. However, adding a bridge for all of the controls, eyepiece, battery adapters, etc would not be desirable as it would just add fail points on the camera without providing significant benefit.

# 🚧 Strategy

Allow selecting an algorithm at runtime. Instead of implementing a single algorithm directly, code receives run-time instructions as to which in a family of algorithms to use.

## Use Cases

- **Customer Contact**- Strategies could help filter which customers to contact, and another strategy could determine how to contact, etc.

# 🚧 Observer

A subscription based pattern, also known as pub-sub, where events are triggered and listeners can react accordingly.

## Caveats

- Easy to go overboard
- Incredibly difficult to debug
- Easy to introduce event loops
- etc

# Composite Design

A hierarchal tree of objects, where each objects are treated uniformly. This means an object through a component interface knows whether it is a leaf or composite object.

# References

- "Design Patterns: Elements of Reusable Object-Oriented Software" by Gamma, Helm, Johnson, Vlissides (Gang of four)
