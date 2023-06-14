[figure-brand-color-picking]: ../.project/figures/design/brand-color-picker.png
[figure-brand-color-examples]: ../.project/figures/design/brand-color-button-background.png

- [Design](#design)
- [Links](#links)
- [Color Palette](#color-palette)
- [Colors](#colors)
  - [Brand Colors](#brand-colors)
    - [Number of Brand Colors](#number-of-brand-colors)
    - [Should be a "middle color"](#should-be-a-middle-color)
    - [Should pass the "background test"](#should-pass-the-background-test)
  - [Supporting Colors (4 colors)](#supporting-colors-4-colors)
  - [Neutral (3 colors)](#neutral-3-colors)

# Design

> 🚧 TODO: Split Into multiple files(?)

I have started a "Design" section where I can start putting UI/UX design info.

# Links

| Title                                                                       | Author            | Description                                                                                                     |
| --------------------------------------------------------------------------- | ----------------- | --------------------------------------------------------------------------------------------------------------- |
| [US Brand Colors](https://usbrandcolors.com/)                               | U.S. Brand Colors | For a study on UI, why not look at successful brands? Check out the links to specific company brand resources.) |
| [AirBnB Design Language](https://airbnb.design/building-a-visual-language/) | AirBnB            | A very cool look at design and the design system used at AirBnB                                                 |
| [Huemint](https://huemint.com/)                                             | Huemint           | Generate color palette for a brand, website, or graphic                                                         |
| [UI Color Palettes](https://www.youtube.com/watch?v=yYwEnLYT55c)            | UX Tools          | A great video on color                                                                                          |
| [Color Blender](https://meyerweb.com/eric/tools/color-blend)                | Eric Meyer        | A fantastic site to blend between two colors                                                                    |
| [Penpot User Manual](https://help.penpot.app/user-guide/introduction/)      | Penpot            | The user manual for Penpot, a Figma replacement                                                                 |

> 🚧 TODO: I would _love_ to write my own Color Blender utility. That is on the horizon for me.
>
> What I need is a way to plug in `n` brand colors along with a neutral dark and light point, and generate my `color.css` file. Or just an xml snippet I can paste into penpot. I don't know. But there has to be a better way than manuall coming up with UI colors. Maybe not. It sure takes _(me)_ a long time.

# Color Palette

2. Supporting Colors
   - Used to draw attention or communicate using color
   - Usage: `Error Messages`, `Confirmation`, `Informational Dialogs`
3. Neutrals
   - Usage: `Text`, `Backgrounds`, `Border Colors`, `Secondary Buttons`

# Colors

Attempt at a description for what colors are required in a UI.

## Brand Colors

Brand Colors are used throughout a website as "splashes of color" to determine the feel of the site. A good example of this is "facebook blue" which makes the app "feel blue" even though most of the app is "grace"

One or Two colors

-
- Usage: `Buttons`, `Links`, `Icons`, `Navigation`

### Number of Brand Colors

| #   | Effect                                    |
| --- | ----------------------------------------- |
| 1   | Clean, but could be considered sterile    |
| 2   | Can be good, depending on design elements |
| 3+  | Entering Chaotic territory                |

The brand colors usually come from the business; and will likely have been chosen at the time the company developed their branding package. If there is no branding available, here are some tips to choose 'Brand Color' for UI/UX.

### Should be a "middle color"

A "middle color" is a color that has strong saturation and value. (from the highlighted region)

![Color Picker Location][figure-brand-color-picking]

### Should pass the "background test"

A brand color should work well as a button background color.

![Button Background Examples][figure-brand-color-examples]

## Supporting Colors (4 colors)

Supporting colors are used in dialog messages and icons to easily convey information to the user in a universal manner.

Color should not be the _only_ way that this information is conveyed, but things like red text in a form is pretty universal for "Something you entered is wrong in the terms of what this form was expecting."

1. Success Color: Usually a (Green) is needed
2. Warning Color: Usually a (Yellow or Orange)
3. Error Color: Usually a (Red)
4. Info Color: Usually a (Blue) for neutral informational messages

Supporting colors need to feel like they go along with your brand colors. Pay attention to saturation and brightness levels (HSV) in comparison to the brand colors. Both values (S & B) should be within 5 or 10 of the brand color. Once you have the S and B set, you can adjust the hue to be whatever you like.

## Neutral (3 colors)

I like to tint my neutrals towards the brand color(s), slightly.

- Dark (near black)
- Gray (near midpoint)
- Light (near white)

```css
/* example variable names */
:root {
  --c-dark: black;
  --c-mid: gray;
  --c-light: white;
}
```
