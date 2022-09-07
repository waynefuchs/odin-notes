- [Fonts](#fonts)
  - [Links](#links)
    - [Fonts](#fonts-1)
    - [Tips and Tricks](#tips-and-tricks)
  - [Property Example Usage](#property-example-usage)


# Fonts

## Links

### Fonts

* [Google Fonts](https://fonts.google.com/)
* [Font Library](https://fontlibrary.org/)
* [Adobe Fonts](https://fonts.adobe.com/): Non-free

### Tips and Tricks

* [Text Overflow](https://css-tricks.com/snippets/css/truncate-string-with-ellipsis/)

## Property Example Usage

``` css
@font-face {
    font-family: COUTUREBold;
    src: url(fonts/COUTUREBold.woff)
}
.overflowing {
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
.example {
    font-family: 'COUTUREBold';
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
