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
