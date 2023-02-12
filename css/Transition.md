- [Transition](#transition)
  - [Links](#links)
  - [Gotchas](#gotchas)
  - [transition-property](#transition-property)
  - [transition-duration](#transition-duration)
  - [transition-timing-function](#transition-timing-function)
  - [transition-delay](#transition-delay)
  - [transition](#transition-1)

# Transition

Animation between states.

## Links

[MDN Transition Documentation](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Transitions/Using_CSS_transitions): Includes js integration (eg: ball demo)

## Gotchas

- Be careful with **_context stacking_**. Performing multiple transforms will force a rerender of all parent elements and can cause performance issues.
- If performance is important, stick to **_opacity_** and **_transform_** transitions _only_. Other operations, such as animating color, can tax the visitor's browser.

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
