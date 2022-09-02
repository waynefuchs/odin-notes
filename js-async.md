# JavaScript Asynchronous Code

## Resources

* [Avoid Callback Hell](http://callbackhell.com/)
  * Keep your code shallow (name anonymouse functions and separate them)
  * Modularlize (write lots of small packages that do one thing well)
  * Handle every single error (a linter like `standard` helps)

## Callback

A callback function is a function that is passed into another function as an argument, which is then invoked inside the outer function to complete some kind of routine or action.

An example of a callback is the function passed to `addEventListener`.

## Promise

Tutorial: [Understanding JavaScript Promises](https://www.digitalocean.com/community/tutorials/understanding-javascript-promises)

``` js
// true = success state
// false = failure state
let someCondition = true;

// This is a callback function for success
const thing = (resolve, reject) => {
  setTimeout(() => {
    if (!someCondition) return resolve("Error");  
    return reject("OK");
  }, 1000);
}

// In this example success and failure do the same thing
const success = (value) => console.log(value);
const failure = success;

let operation = new Promise(thing)
	.then(success, failure);
```