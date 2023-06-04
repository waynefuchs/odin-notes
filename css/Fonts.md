- [Fonts](#fonts)
- [Links](#links)
  - [Font Resources](#font-resources)
  - [Tips and Tricks](#tips-and-tricks)
    - [`text-overflow`: Usage Example](#text-overflow-usage-example)
- [Font Weights](#font-weights)

# Fonts

# Links

| Title                                                                       | Site | Description                |
| --------------------------------------------------------------------------- | ---- | -------------------------- |
| [Font Weight](https://developer.mozilla.org/en-US/docs/Web/CSS/font-weight) | MDN  | `font-weight` css property |

## Font Resources

| Title                                     | Site         | Description                                                      |
| ----------------------------------------- | ------------ | ---------------------------------------------------------------- |
| [Google Fonts](https://fonts.google.com/) | Google       | An amazing font resource.                                        |
| [Font Library](https://fontlibrary.org/)  | Font Library | A libre/open font library with educational typography resources. |
| [Adobe Fonts](https://fonts.adobe.com/)   | Adobe        | Non-free, professional fonts                                     |

## Tips and Tricks

| Title                                                                               | Site       | Description                                                                                                                                                                                                                                                    |
| ----------------------------------------------------------------------------------- | ---------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Text Overflow](https://css-tricks.com/snippets/css/truncate-string-with-ellipsis/) | CSS Tricks | Being able to control text overflow with an ellipsis, at first glance, seems like a pretty cool thing to be able to do. However, I fail to come up with a real-world use case in which you would want information on your website to be truncated in this way. |

### `text-overflow`: Usage Example

```css
@font-face {
  font-family: COUTUREBold;
  src: url(fonts/COUTUREBold.woff);
}
.overflowing {
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
.example {
  font-family: "COUTUREBold";
  font-style: italic;
  letter-spacing: -0.15em; /* squish letters together */
  line-height: 1.5;
  text-transform: capitalize; /* uppercase, lowercase, none, full-width, full-size-kana */

  /* text-shadow */
  /* offset-x | offset-y | blur-radius | color */
  text-shadow: 1px 1px 2px black;
  /* color | offset-x | offset-y | blur-radius */
  text-shadow: #fc0 1px 0 10px;
  /* offset-x | offset-y | color */
  text-shadow: 5px 5px #558abb;
  /* color | offset-x | offset-y */
  text-shadow: white 2px 5px;
  /* offset-x | offset-y
    /* Use defaults for color and blur-radius */
  text-shadow: 5px 10px;
}
```

# Font Weights

| Value | Name                      |
| :---: | ------------------------- |
|  100  | Thin (Hairline)           |
|  200  | Extra Light (Ultra Light) |
|  300  | Light                     |
|  400  | Normal (Regular)          |
|  500  | Medium                    |
|  600  | Semi Bold (Demi Bold)     |
|  700  | Bold                      |
|  800  | Extra Bold (Ultra Bold)   |
|  900  | Black (Heavy)             |
|  950  | Extra Black (Ultra Black) |
