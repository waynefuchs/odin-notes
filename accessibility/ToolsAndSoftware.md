- [Accessibility Tools and Software](#accessibility-tools-and-software)
  - [Screen Readers](#screen-readers)
    - [NVDA](#nvda)
    - [Orca](#orca)
    - [ChromeVOX](#chromevox)
    - [JAWS](#jaws)
  - [aplay](#aplay)

> TODO: What software development tools are available to assist in ensuring a good user experience for someone with disabilities? (Such as, how do I ensure that my site displays properly on a refreshable braille display considering i can't read braille and I don't have said display.)

# Accessibility Tools and Software

## Screen Readers

### NVDA

A modal reader, meaning there are modes you enter/exit, changing the way you interact with the reader.

For example, entering "application" mode or "form" mode to allow typing in input boxes.

- Website: [NVDA](https://www.nvaccess.org/download/)
- Free
- Windows Only
- [NVDA Shortcuts](https://dequeuniversity.com/screenreaders/nvda-keyboard-shortcuts)

### Orca

- Free
- Linux (Gnome) (on/off: `Super` + `Alt` + `S`)
- $ `orca -s` to access screen reader preferences to configure
- `/home/user/.local/share/orca` (delete if settings get messed up, like they did for me)

### ChromeVOX

- Website: [ChromeVOX](https://support.google.com/chromebook/answer/7031755?hl=en)

ChromeVOX is ChromeOS's screen reader.

### JAWS

- Website: [JAWS](https://www.freedomscientific.com/products/software/jaws/)
- ($95-1285/year)

## aplay

The following sequence will read a webpage; for those times when you want to pre-review the content while you do something else. The pronunciation is pretty bad in some cases, so you still want to read, follow links, and study. But I've found some success in knowing what type of information is contained in a lesson.

1. `lynx -dump -nolist [URL] > blah.txt`
2. `cat blah.txt | pico2wave -w blah.wav`
3. `aplay blah.wav`
