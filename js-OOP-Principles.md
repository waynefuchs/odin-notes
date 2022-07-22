# JavaScript OOP Principles


## SOLID

* Single Responsibility Principle
* Open/Closed Principle
* The Liskov Substitution Principle
* The Interface Segregation Principle
* The Dependency Inversion Principle

### Single Responsibility

Each class, object, module, etc should only have one responsibility. If an object has multiple responsibilities, changing one aspect may affect another. "Do one thing, and do it well."

Strategies for dealing with Single Responsibility:

1. Function name contains the word 'and' as in: `loginUserAndGetGroups()` should be `loginUser()` and `getGroups()`.
2. For every function that you write, try and see if there is a useful part that could be extracted into its own function for reuse.
3. After creating a function, scan it again for useful parts to extract.

A catch:

If the function you write has multiple parts to it, that will nearly always be called together, it is okay to create a wrapper function. So, for example: `getShowsAndMoviesAndMusic()` would become `getUserMedia()` that is comprised of three pure functions, like so: 
```js
function getUserMedia() {
    return {
        shows: getShows(), 
        movies: getMovies(), 
        music: getMusic()
    };
}
```

#### Loosely Coupled Objects

Objects that can stand alone, as much as possible. This is related to single responsibility from a different perspective.


### Open-Closed Principle

Open-Closed Principle means that our JavaScript modules should be open to extension, but closed to modification. Or: If a module's behavior needs to be extended, that module's code should not have to be edited.

An example of using interfaces in js to adhere to the open-closed principle, rather than have a series of if-else statements to determine how to calculate the area of a shape, each shape would instead be required to provide it's own method of calculating its area.

```js
const shapeInterface = (state) => ({
  type: 'shapeInterface',
  area: () => state.area(state)
})

const square = (length) => {
  const proto = {
    length,
    type : 'Square',
    area : (args) => Math.pow(args.length, 2)
  }
  const basics = shapeInterface(proto)
  const composite = Object.assign({}, basics)
  return Object.assign(Object.create(composite), {length})
}
```


### Liskov Substitution Principle

A subclass should be substitutable for the classes from which they were derived. For example, if MySubclass is a subclass of MyClass, you should be able to replace MyClass with MySubclass without bunging up the program.

Every subclass should override the parent class methods in a way that does not break functionality from a client's point of view.

"If it looks like a duck and quacks like a duck but it needs batteries, you probably have the wrong abstraction."


### Interface Segregation Principle

Clients should not be forced to depend on methods they don't use. If a class exposes so many members that those members can be broken down into groups that serve different clients that don't use members from the other groups, you should think about exposing those member groups as separate interfaces.


### Dependency Inversion Principle

High level modules shouldn't depend on low-level modules, but both should depend on shared abstractions. Abstractions should not depend on details- instead, details should depend on abstractions.