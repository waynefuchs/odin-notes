- [Transition](#transition)
  - [Links](#links)
  - [Gotchas](#gotchas)
  - [will-change](#will-change)
  - [transition-property](#transition-property)
  - [transition-duration](#transition-duration)
  - [transition-timing-function](#transition-timing-function)
  - [transition-delay](#transition-delay)
  - [transition](#transition-1)

# Transition

***Simple*** Animation between states. *(See [Animation-Keyframes](Animation-Keyframes.md) for complex animation)*

## Links

- [CSS Triggers List](https://csstriggers.com/): Show what effect various CSS triggers will have on performance.
- [MDN Transition Documentation](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Transitions/Using_CSS_transitions): Includes js integration (eg: ball demo)
- [Animations Guide](https://web.dev/animations-guide/): Handy section on debugging slow / janky animations.
- [will-change](https://dev.opera.com/articles/css-will-change-property/): "Everything you need to know about the CSS will-change property" (Opera Blog Post)

## Gotchas

- **Avoid properties that trigger layout or paint** ([CSS Triggers](https://csstriggers.com/))
- Be careful with **_context stacking_**. Performing multiple transforms will force a rerender of all parent elements and can cause performance issues.
  - `opacity` and `transform` are safer options
  - Using z-index layering can assist the browser in determining when re-renders are not required.
- If performance is important, stick to **_opacity_** and **_transform_** transitions _only_. Other operations, such as animating color, can tax the visitor's browser.

## will-change

*Use sparingly* - will notify the browser that the css author expects the element to change. Applying the property can cause the browser to waste memory.

If the page is performing well / as intended, do not use.

This property is intended to be predictively set by a script as part of optimization. It can be used in CSS, but will cause the optimizations to be held in memory for much longer than necessary.

```css
/* will-change example, if required in css */
body > .sidebar {
  will-change: transform;
}
```

```js
// Rough generic example
// Get the element that is going to be animated on click, for example
var el = document.getElementById('element');

// Set will-change when the element is hovered
el.addEventListener('mouseenter', hintBrowser);
el.addEventListener('animationEnd', removeHint);

function hintBrowser() {
	// The optimizable properties that are going to change
	// in the animation's keyframes block
	this.style.willChange = 'transform, opacity';
}

function removeHint() {
	this.style.willChange = 'auto';
}
```

- `auto`: default optimizations
- `scroll-position`: It is expected that the scroll position of the element will change
- `contents`: It is expected that something about the element's contents will change

## transition-property
---

Define what property will be transitioned.

| property   | description                                                                                               |
| ---------- | --------------------------------------------------------------------------------------------------------- |
| none       | No properties will transition                                                                             |
| all        | All properties that can transition will transition                                                        |
| `specific` | [List of Animatable Properties](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_animated_properties) |

## transition-duration

---

The length of time the transition will take.

## transition-timing-function

---

Change the velocity of the transition over the course of its duration.

| Timing Function              | description                                                                                                                        |
| ---------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| ease                         |                                                                                                                                    |
| linear                       |                                                                                                                                    |
| ease-in                      |                                                                                                                                    |
| ease-out                     |                                                                                                                                    |
| ease-in-out                  |                                                                                                                                    |
| cubic-bezier(p1, p2, p3, p4) |                                                                                                                                    |
| steps(n, `jumpterm`)         | Displays the transition with `n` "stops" during playback of the animation, where each stop is displayed for equal lengths of time. |
| step-start                   |                                                                                                                                    |
| step-end                     |                                                                                                                                    |

| Jump Term  | description                                             |
| ---------- | ------------------------------------------------------- |
| jump-end   | Continuous left ► right playback with a jump at the end |
| end        | Alias for `jump-end`                                    |
| jump-start | Continuous right ◄ left playback                        |
| start      | Alias for `jump-start`                                  |
| jump-none  |                                                         |
| jump-both  |                                                         |

For more info, see [transition-timing-function](https://developer.mozilla.org/en-US/docs/Web/CSS/transition-timing-function) at MDN.

## transition-delay

How long to wait before performing the transition.

## transition

A shorthand property for

```css
/*
  Below is shorthand for:
    transition-property
    transition-duration
    transition-timing-function
    transition-delay

  transition: {property} {duration} {timing-func} {delay};
*/

.example1 {
  background-color: green;
  transition: background-color 1s ease-out 0.25s;
}
.example1:hover {
  background-color: red;
}
```
