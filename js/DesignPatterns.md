- [Design Patterns](#design-patterns)
  - [Links](#links)
  - [Concepts](#concepts)
    - [Closure](#closure)
    - [Prototypes](#prototypes)
    - [IIFEs](#iifes)
  - [Patterns](#patterns)
    - [Plain Old JavaScript Objects and Object Constructors](#plain-old-javascript-objects-and-object-constructors)
    - [Factory Functions and the Module Pattern](#factory-functions-and-the-module-pattern)
    - [Classes](#classes)
    - [ES6 Modules](#es6-modules)

# Design Patterns

## Links

* The Free Book [You don't know JS](https://github.com/getify/You-Dont-Know-JS/tree/1st-ed#titles) explains how js works under the hood.
* Explanation of [JavaScript 'this' keyword](https://dmitripavlutin.com/gentle-explanation-of-this-in-javascript/)
* [A Beginner's Guide to JavaScript's Prototype](https://dmitripavlutin.com/gentle-explanation-of-this-in-javascript/)

## Concepts

### Closure

### Prototypes

The way to set object inheritance in JS/ES.

* Never use call `setPrototypeOf()` directly in production code, this prevents the JS engine from optimizing your program!! It can be helpful in testing things, but in general.. AVOID
  * ~~`Object.setPrototypeOf(obj, inheritedProtoObject)`: How to set the prototype~~ 
* Object.getPrototypeOf()
* `obj.hasOwnProperty("property")` returns true if the property is stored in the referenced object

### IIFEs

## Patterns

### Plain Old JavaScript Objects and Object Constructors


### Factory Functions and the Module Pattern


### Classes


### ES6 Modules