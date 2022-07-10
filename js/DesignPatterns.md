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
  - [TOP Lessons](#top-lessons)
    - [Objects and Object Constructors](#objects-and-object-constructors)
    - [Factory Functions and the Module Pattern](#factory-functions-and-the-module-pattern-1)

# Design Patterns

TODO: Go through here and consolidate and review this at the end.

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


## TOP Lessons

### Objects and Object Constructors

> Personal Comments
>
> I got to the end of reading the following lesson for the third time, and realized I needed to come back and review this lesson as well. The Odin Project states that it is imperative that this information be completely understood at this level.

* Write an object constructor and instantiate the object.

  ```js
  function Constructor(name, value) {
    this.name = name;
    this.value = value;
  }
  const property = new Constructor("the meaning of life", 42);
  console.log(property.name);   // "the meaning of life"
  console.log(property.value);  // 42
  ```

* Describe what a prototype is and how it can be used.

  `prototype` in javascript is a linked list (chain) of inheritance.

* Explain prototypal inheritance.

  An object's prototype points to another `object (scope)` all the way until you reach the root / global scope. Each scope is tested for variables (including functions / methods) all the way up the chain/list.

* Understand the basic do’s and don’t’s of prototypical inheritance.

  The following example was given in The Odin Project lesson.

  ```js
  function Student() {
  }

  Student.prototype.sayName = function() {
    console.log(this.name)
  }

  function EighthGrader(name) {
    this.name = name
    this.grade = 8
  }

  EighthGrader.prototype = Object.create(Student.prototype)

  const carl = new EighthGrader("carl")
  carl.sayName() // console.logs "carl"
  carl.grade // 8
  ```

  DO:

    * Use Object.create() to assign prototype / inheritance (`ObjectA.prototype = Object.create(ObjectB.prototype);`)

  DO NOT (NEVER):
    
    * Manually set prototype (`objA.prototype = objB.prototype;`)
    * Attempt to loop a chain
    * Use `setPrototypeOf()`

* Explain what Object.create does

  `Object.create()` allows the programmer to create an object which will delegate to another object on failed lookups. (scope)

  ```js
  // This code is a bit of an aside.
  // But it demonstrates Object.create()
  // And how it relates to the `new` keyword
  function Animal (name, energy) {
    // const this = Object.create(Animal.prototype)
    this.name = name
    this.energy = energy
    // return this
  }
  const leo = new Animal('Leo', 7)
  ```

* How does `this` behave in different situations?

  Good god. What a loaded question.

  This article [Gentle Explanation of "this" in JavaScript](https://dmitripavlutin.com/gentle-explanation-of-this-in-javascript/) begins to tackle this answer, and it only takes about 30 pages.


### Factory Functions and the Module Pattern

> Personal Comments: 
> 
> For whatever reason I really struggled with this lesson.

* Describe common bugs you might run into using constructors.

  1. Can inadvertently introduce bugs into your code
  2. They look like regular functions, but do not behave as such
  3. If you forget the `new` keyboard, you can introduce difficult to trace bugs (eg: related to global scope)


* Write a factory method that returns an object.
  
  ```js
  const hitchhikerFactory = (name, meaning) => {
      const whatIs = () => { console.log(`The meaning of ${name} is ${meaning}`); }
      return {name, meaning, whatIs};
  }
  let hitchhiker = hitchhikerFactory("life, the universe, and everything", 42);
  hitchhiker.whatIs();  // The meaning of life, the universe, and everything is 42
  ```


* Explain how scope works in JavaScript (bonus points if you can point out what ES6 changed!).

  Simply: Scope is just a measure of what variables are available to your program at the point a line is executed. The addition of `const` and `let` in addition to the original `var` keywords are what changed.

  * `var`: Scope is `global` or `functional`.
  * `let` and `const`: Scope is `global`, `functional`, or `block`. NEW IN ES6


* Explain what Closure is and how it impacts private functions & variables.

  A closure is the combination of a function, bundled together with references to its surrounding state. (lexical environment)

  ```js
  function makeAdder(x) {
    return function (y) {
      return x + y;
    };
  }

  const add5 = makeAdder(5);
  const add10 = makeAdder(10);

  console.log(add5(2));   // 7
  console.log(add10(2));  // 12
  ```


* Describe how private functions & variables are useful.

  Removing the ability for tampering with unnecessary internal program variables and details makes for less bug-prone and easily testable code.


* Use inheritance in objects using the factory pattern.

  ```js
  const createAnimal = (type) => {
    const sayType = () => console.log(`I am a(n) ${type}!`);
    return {sayType};
  }
  const createCow = (type) => {
    const {sayType} = createAnimal("Cow");
    const sayMoo = () => console.log("Moo.");
    return {sayType, sayMoo};
  }
  const betsy = createCow();
  betsy.sayType();
  betsy.sayMoo();
  ```


* Describe IIFE. What does it stand for?

  An IIFE is an Immediately Invoked Function Expression.


* Explain the module pattern.

  It's the factory pattern, except it is immediately invoked (IIFE) instead of being used to create multiple objects.

  ```js
  let calculator = (() => {
    let name = "Calculator";
    const add = (a, b) => a + b;
    const subtract = (a, b) => a - b;
    const sayName = () => console.log(`${name} - ${typeof a === 'undefined' ? "none" : a}`);
    const setName = (a) => name = a;
    return {add, subtract, sayName, setName}
  })();
  console.log(calculator.add(1, 3));  // 4
  calculator.sayName();               // Calculator - none
  calculator.setName("Hairbrush");
  calculator.sayName();               // Hairbrush - none
  ```

* Briefly explain namespacing and how it’s useful.

  Namespacing is the separation of naming scope, where you can specify two functions in the same program with the same name. 
  
  Example: A calculator module that benefits from having an 'add()' function, and also a UI progress bar that benefits from being able to 'add()' progress. This is possible as long as you don't have namespace collisions.