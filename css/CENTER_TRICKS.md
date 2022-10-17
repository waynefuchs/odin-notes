# CSS Centering Tricks

I have wasted so much time trying to get things centered. I'm going to put 'recipies' of what worked for me here. Hope I will save time in the future.

## Centering with Translate

The relevant bit:
```css
#absolute-center {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
```

What I actually ended up using:
```css
#LandingPage .SearchBegins {
  /* position the element */
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);

  /* position the children elements */
  display: flex;
  align-items: center;
  gap: var(--spacing);
  
  /* style box */
  background-color: var(--c1-d);
  padding: var(--spacing);
  border-radius: var(--spacing);
  color: var(--c-light);
}
```