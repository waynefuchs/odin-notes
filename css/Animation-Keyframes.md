- [Animation using Keyframes](#animation-using-keyframes)
  - [Links](#links)
  - [`@keyframes`](#keyframes)
    - [Gotchas](#gotchas)
  - [`animation`](#animation)
    - [Animation Properties](#animation-properties)
      - [`animation-delay`](#animation-delay)
      - [`animation-direction`](#animation-direction)
      - [`animation-duration`](#animation-duration)
      - [`animation-fill-mode`](#animation-fill-mode)
      - [`animation-iteration-count`](#animation-iteration-count)
      - [`animation-name` (Optional)](#animation-name-optional)
      - [`animation-play-state`](#animation-play-state)
      - [`animation-timing-function`](#animation-timing-function)

> TODO: Combine `Animation-Keyframes.md` and `Transition.md`

# Animation using Keyframes

**_Complex_** animation between various states. _(See [Transition](Transition.md) for simple animation)_

## Links

- [W3C Source Specification](https://w3c.github.io/csswg-drafts/css-animations/#animation) (Use this. It is the clearest.)
- MDN [Using CSS Animations](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Animations/Using_CSS_animations) (This 'tutorial' was part 1 of the assignment on the "Keyframes" lesson)
- MDN [@keyframes](https://developer.mozilla.org/en-US/docs/Web/CSS/@keyframes)
- MDN [animation](https://developer.mozilla.org/en-US/docs/Web/CSS/animation)

## `@keyframes`

---

Define animation transitions.

```css
/*
The `from` keyword = 0% = start
The `to` keyword = 100% = end
@keyframes <name> {
  <from/%> {
    <css>;
  }
  <to/%> {
    <css>;
  }
}
*/
```

### Gotchas

- If you fail to specify a start (`from`/`0%`) or end (`to`/`100%`) a transition from/to the existing state will be used
- Don't use duplicate names for keyframes. They are not interpolated and will not both be used.
  - last named keyframe encountered by the parser is used to resolve naming conflicts
- Use of the `!important` keyword in keyframes is ignored

## `animation`

---

`animation` is a shorthand for several other animation properties and is useful for saving space.

> Note: The browser interprets the shorthand inputs, making the syntax a bit challenging to define. I found several "incorrect" examples (counter to the w3 definition) on various websites that worked. I can only assume that the syntax has evolved over time and backwards compatibility has been left in place.

Here is my attempt at it taken from several sources: (Mostly MDN)

```css
/*
Each individual animation is specified as:

zero, one, or two occurrences of the <time> value
zero or one occurrences of the following values:
  <single-easing-function>
  <single-animation-iteration-count>
  <single-animation-direction>
  <single-animation-fill-mode>
  <single-animation-play-state>
*/

.syntax1 {
  /*  
  animation:
    animation-name
    animation-duration 
    animation-timing-function 
    animation-delay 
    animation-iteration-count 
    animation-direction 
    animation-fill-mode 
    animation-play-state  */

  animation: SlideIn 3s ease-in 1s 2 reverse both paused;
}

.syntax2 {
  /*
  animation: 
    animation-name
    animation-duration 
    animation-timing-function
    animation-delay*/

  animation: SlideIn 3s linear 1s;
}

.syntax3 {
  /* Multiple Animations: [Separate using commas] */
  animation: SlideIn 3s linear, SlideOut 3s ease-out 5s;
}

element {
  /* Longhand demonstration */
  animation-name: SlideIn;
  animation-duration: 3s;
  animation-iteration-count: infinite;
  animation-direction: alternate;

  /* Becomes (Shorthand) */
  animation: SlideIn 3s ease infinite;
  animation: SlideIn 0.5s linear 1s infinite alternate;
}
```

### Animation Properties

Here are the properties that are (more commonly) set by the `animation` shorthand defined above.

#### [`animation-delay`](https://developer.mozilla.org/en-US/docs/Web/CSS/animation-delay)

---

Specifies the delay between the element loading and the start of the animation sequence.

By setting a negative delay, you can change the starting point in the animation.

```css
animation-delay: 250ms; /* Play the animation from its start after 0.25s */
animation-delay: 2s; /* Play the animation from it's start after 2 seconds */
animation-delay: -1s; /* If the animation is 1.3 seconds long, only the last 0.3 seconds of the animation will play */
```

#### [`animation-direction`](https://developer.mozilla.org/en-US/docs/Web/CSS/animation-direction)

---

Specify whether an animation should play forwards, in reverse, or alternate back and fourth.

| value             | description        |
| ----------------- | ------------------ |
| normal            | 0 --> 100          |
| reverse           | 0 <-- 100          |
| alternate         | 0 --> 100 <--> 0   |
| alternate-reverse | 100 --> 0 <--> 100 |

`inherit`, `initial`, `revert`, `revert-layer`, `unset`

```css
animation-direction: normal;
animation-direction: reverse;
animation-direction: alternate;
animation-direction: alternate-reverse;
```

#### [`animation-duration`](https://developer.mozilla.org/en-US/docs/Web/CSS/animation-duration)

---

Simply the length of time that an animation takes to complete one cycle. (in integer or floating point `s`, or `ms`)

```css
animation-duration: 750ms;
animation-duration: 3s;
animation-duration: 0s;
animation-duration: 1.333s, 222ms; /* multiple animations */
```

#### [`animation-fill-mode`](https://developer.mozilla.org/en-US/docs/Web/CSS/animation-fill-mode)

---

Defines how styles are applied before and after the animation execution.

| value     | description                                                                    |
| --------- | ------------------------------------------------------------------------------ |
| none      | styles are not retained at either end of animation                             |
| forwards  | style is held at the end of the animation                                      |
| backwards | style is set before the animation starts (eg: during the animation-delay)      |
| both      | style is set when the animation is loaded and held at the end of the animation |

```css
animation-fill-mode: none;
animation-fill-mode: forwards;
animation-fill-mode: backwards;
animation-fill-mode: both;
```

#### [`animation-iteration-count`](https://developer.mozilla.org/en-US/docs/Web/CSS/animation-iteration-count)

---

The number of times to play the animation. Floating point counts are allowed. (eg: 1.25 to play 1 and a quarter animations)

#### `animation-name` (Optional)

---

Specify the animation name of one or more `@keyframe` at-rules to apply to an element.

`none` can be specified.

```css
animation-name: none;
animation-name: slide;
animation-name: bounce;
animation-name: slide, bounce; /* do both */
```

#### [`animation-play-state`](https://developer.mozilla.org/en-US/docs/Web/CSS/animation-play-state)

---

Specifies what state of playback the animation is in.

Toggling between `paused` and `running` does not reset playback position.

```css
animation-play-state: running;
animation-play-state: paused;
```

#### [`animation-timing-function`](https://developer.mozilla.org/en-US/docs/Web/CSS/animation-timing-function)

---

Defines how the animation progresses through the duration of each cycle. I wrote about the `transition-timing-function`, which behaves basically the exact same way, in the [Transition](Transition.md#transition-timing-function) document.
