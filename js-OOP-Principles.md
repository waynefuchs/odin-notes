# JavaScript OOP Principles

## Single Responsibility

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

## Loosely Coupled Objects

Objects that can stand alone, as much as possible. This is related to single responsibility from a different perspective.



## SOLID

* Single Responsibility Principle
* Open/Closed Principle
* The Liskov Substitution Principle
* The Interface Segregation Principle
* The Dependency Inversion Principle