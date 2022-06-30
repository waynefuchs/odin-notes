- [Pseudo Classes (0, 0, 1, 0)](#pseudo-classes-0-0-1-0)
  - [Links](#links)
  - [List](#list)
  - [Form Specific Pseudo Classes](#form-specific-pseudo-classes)

# Pseudo Classes (0, 0, 1, 0)

Pseudo Classes are keywords (prefixed by `:`) that allow me to select css elements by their state.

## Links

[Psuedo-Class Reference](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes)
[Form-Specific Pseudo Classes](https://developer.mozilla.org/en-US/docs/Learn/Forms/UI_pseudo-classes)

## List

General

* `:root`
* `:first-child`
* `:last-child`
* `:empty`
* `:nth-child(5)` | `:nth-child(3n)` | `:nth-child(3n+2)` | `:nth-child(even)`

Clicking Stuff

* `:active`
* `:focus`
* `:hover`

Links

* `:link`
* `:visited`

Forms

* `:valid`
* `:invalid`
* `:in-range`
* `:out-of-range`
* `:checked`
* `:indeterminate`
* `:default`
* `:required`
* `:optional`
* `:enabled`
* `:disabled`
* `:read-write`
* `:read-only`


## Form Specific Pseudo Classes

``` css
input {
    /* black border at start and while editing */
  border: 2px solid #000;
  margin-bottom: 15px;
  padding: 5px;
  border-radius: 5px;
}

input:invalid,
input:out-of-range {
    /* red border when invalid */
    border-color: red;
}

input:valid,
input:in-range {
    /* green border when valid */
    border-color: green;
}

input:checked {
    color: purple;
}

input:indeterminate {
    color: lime;
}

input:default {
    color: lightgray;
}

input:required { 
    border: 2px dotted #000;
}

input:optional {
    border: 2px double #000;
}

input:enabled,
input:read-write {
    background-color: white;
}

input:disabled,
input:read-only {
    background-color: darkgray;
}
```