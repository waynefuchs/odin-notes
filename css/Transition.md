- [Transition](#transition)

# Transition

Animation between states.

## Properties associated with transitions

### transition

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

### transition-property

Define what property will be transitioned.

### transition-duration

The length of time the transition will take.

### transition-timing-function

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

### transition-delay

How long to wait before performing the transition.
