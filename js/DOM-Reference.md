- [DOM Reference](#dom-reference)
  - [References](#references)
  - [Selector](#selector)
  - [Element Creation](#element-creation)
  - [Styling](#styling)
  - [Update Attributes](#update-attributes)
  - [Working with Classes](#working-with-classes)
  - [Text Content](#text-content)
  - [HTML Content](#html-content)
  - [DOM (From old Javascript-Reference Notes)](#dom-from-old-javascript-reference-notes)

# DOM Reference

## References

(HTML DOM Events)[https://www.w3schools.com/jsref/dom_obj_event.asp]

## Selector

``` javascript
// Can use CSS selectors in:
//      document.querySelector()
//      document.querySelectorAll()
// Other selection methods may have (marginally) better performance
const container = document.querySelector("#container");
console.dir(container.firstElementChild);                
const controls = document.querySelector('.divcontainer');
console.dir(controls.previousElementSibling);
console.dir(controls.parentElement);
const allPs = document.querySelectorAll("p");
console.dir(allPs);
```


## Element Creation

``` javascript
const body = document.querySelector("body");
let paragraph = document.createElement('p');
paragraph.setAttribute("style", "background-color: orange;");
paragraph.textContent = "Hello There";
body.append(paragraph);
```

## Styling

``` javascript
div.style.background-color // doesn't work - attempts to subtract color from div.style.background
div.style.backgroundColor // accesses the div's background-color style
div.style['background-color'] // also works
div.style.cssText = "background-color: white;" // ok in a string
```

## Update Attributes

``` javascript
div.setAttribute('id', 'theidforthiselement'); // add/update
div.getAttribute('id');
div.removeAttribute('id');
```

## Working with Classes

``` javascript
div.classList.add('new-class');
div.classList.remove('new-class');
div.classList.toggle('new-class');
```

## Text Content

``` javascript
div.textContent = 'hello world';
```

## HTML Content

Use sparingly or not at all, can cause security issues. (javascript injection)

``` javascript
div.innerHTML = '<p>hi!</p>';
```


## DOM (From old Javascript-Reference Notes)

Select a container element and append a new paragraph element to it, then change the new paragraph to read "Hello World!".

``` javascript
const output = document.querySelector('.output');
const para = document.createElement('p');
output.appendChild(para);
para.textContent = "Hello World!";
```

