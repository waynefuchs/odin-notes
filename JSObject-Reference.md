# JavaScript Object Notes

## Definition

``` javascript
const variableProperty = "some value from somewhere";
const newProperty = "tagline";
var theObject = {
    aProperty: 'has some value',
    'has multiple word': true,  // cannot be accessed through 'dot access' must use theObject['has multiple words']
    lastPropertyCanHaveComma: 1234.5678,
    [variableProperty]: "some value",       // 1* See below
};
theObject[tagline] = "Zeus the almighty";   // 1* When using variable properties, it is common practice to define like this
theObject[tagline + "helloWorld"] = "Shenanigans";
```

Shorthand for properties:
``` javascript
function makeUser(name, age) {
    return {
        name,
        age,
        userName: name+age, // can use normal property definition along with shorthand
    };
} // returns: {name: name, age: age} -- variable names define the property
```

## Access

``` javascript
theObject = {
    name: "Zeus",
    phone: "1-800-thu-nder",
    age: 99_999_999,
};
// "Zeus"
console.log(theObject.name);

// "Zeus"
console.log(theObject["name"]);

// "Zeus"
var key = "name";
console.log(theObject[key]);

// "Zeus"
var propertyValue = prompt("Enter property value..."); // User enters "name"
console.log(theObject[propertyValue]);
```

## Adding a property

Just treat the property like you are overwriting an existing property to add it.

``` javascript
myObject.newKey = "This key is called newKey";
myObject.["anotherNewKey"] = "Another way to add a new key";
```

## Removing a property


``` javascript
delete myObject.newKey);
```

The return value of delete has to do with non-configurable properties.

``` javascript
// Initially the property is configurable
Object.getOwnPropertyDescriptor(myObject, "word");
// Output: {value: 'value', writable: true, enumerable: true, configurable: true}

// But I can set it to be not configurable (immutable)
Object.defineProperty(myObject, "word", {configurable: false});

// Now if I call delete...
delete myObject.word;
// This returns false, or will throw an Exception (`TypeError`) if using strict
// In all other cases, `delete` will return `true`.
```

> **Note / Take-away**:
>
> The return value is not related to success of the operation!

## Checking to see if a property exists:
``` javascript
var user = {
    name: "Zeus",
    username: "zeus3297bc",
    age: 3297 + 2022 + 1,
}
// A bit tricky negation due to checking against undefined
if(user.age !== undefined) console.log("Age Property Exists");
if(user.superPower === undefined) console.log("SuperPower Property does not Exist.");

// Alternatively (Much easier to read)
if('age' in user) console.log("Property 'age' is defined.");
```
> **NOTE:**
>
> If a value stored in an object is itself 'undefined', the `in` keyword is required to check if the property is in fact defined.
>
> In other words, it's better to just use `in`...

## Looping through keys

``` javascript
var myObject = {
    5: "Five",
    4: "Four",
    3: "Three",
    2: "Two",
    word: "value",
    someKey: "Some other Value",
    1: "One",
}
for(key in myObject) {
    console.log(`${key}: ${myObject[key]}`);
}
```

> **Note:**
>
> In the above example, the output is:
>
```
1: One
2: Two
3: Three
4: Four
5: Five
word: value
someKey: Some other Value
```
> This is due to "Integer Sorting" of objects. Integer properties are sorted, all non-integers are listed in the order that they are added to the object.


## Specify functions / methods in an object

``` javascript
var myObject = {
    a: "ABC",
    b: "BCD",
    c: "CDE",
    myfunc(input) {
        console.log(`${this.a} ${this.b} ${this.c} ${input}`);
    }
};
myObject.myfunc("Hello, Func!");
```
