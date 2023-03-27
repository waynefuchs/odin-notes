- [Accessibility (a11y)](#accessibility-a11y)
  - [Links](#links)
  - [Semantic HTML](#semantic-html)
    - [Headings `<h1>` ... `<h6>`](#headings-h1--h6)
    - [`<button>`](#button)
    - [`<table>`](#table)
    - [`<label>`](#label)
    - [Landmarks](#landmarks)
    - [Semantic HTML Landmark Elements](#semantic-html-landmark-elements)
  - [Color Contrast](#color-contrast)
  - [Web Content Accessibility Guidelines (WCAG)](#web-content-accessibility-guidelines-wcag)
    - [WCAG Four Principles:](#wcag-four-principles)
    - [WCAG Conformance Levels](#wcag-conformance-levels)
  - [ARIA](#aria)
  - [Disability Types](#disability-types)
    - [Auditory](#auditory)
      - [Guidelines](#guidelines)
      - [Auditory Disabilities](#auditory-disabilities)
    - [Cognitive, Learning, and Neurological](#cognitive-learning-and-neurological)
      - [Guidelines](#guidelines-1)
      - [Cognitive, Learning, and Neurological Disabilities](#cognitive-learning-and-neurological-disabilities)
    - [Physical](#physical)
      - [Specialized Hardware](#specialized-hardware)
      - [Guidelines](#guidelines-2)
      - [Physical Disabilities](#physical-disabilities)
    - [Speech](#speech)
      - [Guidelines](#guidelines-3)
      - [Speech Disabilities](#speech-disabilities)
    - [Visual](#visual)
      - [Guidelines](#guidelines-4)
      - [Visual Disabilities](#visual-disabilities)
  - [Disability Aspects](#disability-aspects)
  - [Accessibility Tools and Software](#accessibility-tools-and-software)
    - [Screen Readers](#screen-readers)
      - [NVDA](#nvda)
      - [Orca](#orca)
      - [ChromeVOX](#chromevox)
      - [JAWS](#jaws)
  - [Gotchas](#gotchas)

> TODO: What software development tools are available to assist in ensuring a good user experience for someone with disabilities? (Such as, how do I ensure that my site displays properly on a refreshable braille display considering i can't read braille and I don't have said display.)

# Accessibility (a11y)

## Links

I have ordered these in the priority order that I think they will be useful to me in the future.

| Page Name                                                                                                                                  | Description                                                                                             |
| ------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------- |
| [ARIA Landmarks Example](https://www.w3.org/WAI/ARIA/apg/patterns/landmarks/examples/HTML5.html)                                           | An example of how to use ARIA Landmarks on a page                                                       |
| [WCAG 2 Guidelines](https://www.w3.org/TR/WCAG22/) ([Local Copy](<../Web%20Content%20Accessibility%20Guidelines%20(WCAG)%202.2.pdf>))      |                                                                                                         |
| [WCAG 2 Checklist](https://webaim.org/standards/wcag/WCAG2Checklist.pdf) ([Local Copy](../WCAG2Checklist.pdf))                             | A checklist that can be useful in ensuring a site is accessible.                                        |
| [ARIA Authoring Practices Guide (APG)](https://www.w3.org/WAI/ARIA/apg/patterns/)                                                          | By the web accessibility initiative (w3.org), how to use ARIA (for each html element) to assist in a11y |
| Wikipedia [WCAG (Web Content Accessibility Guidelines)](https://en.wikipedia.org/wiki/Web_Content_Accessibility_Guidelines)                | Contains multiple relevant links and history                                                            |
| [Diverse Abilities and Barriers](https://www.w3.org/WAI/people-use-web/abilities-barriers/)                                                | W3C Explanation of Disabilities                                                                         |
| [How People with Disabilities Access Digital Content](https://www.youtube.com/watch?v=Lu7a5RU5lM0)                                         | A video by UA Technology Accessibility that covers various assistive technologies. (45m)                |
| Google Chrome Developers [a117casts playlist](https://www.youtube.com/watch?v=HtTyRajRuyY&list=PLNYkxOF6rcICWx0C9LVWWVqvHlYJyqw7g&index=2) | A youtube playlist, by google, that walks through accessibility for developers.                         |
| Implementing [Dark Mode](https://css-tricks.com/a-complete-guide-to-dark-mode-on-the-web/)                                                 | A CSS-Tricks page with helpful hints on implementing styles on a webpage.                               |

> Note:
>
> I have had w3.org appear offline through cloudflare. (Why I have local copies)

## Semantic HTML

---

HTML Semantics are important because they provide _meaning_ and _context_ to content.

A tag like `<p></p>` provides meaning, but not context. That paragraph could be your company motto, a sales pitch, or a paragraph in an article. The browser doesn't know.

> Note: In forms, always use `type="<intended use>"`. (See: #type in [forms.md](forms.md#type))

### Headings `<h1>` ... `<h6>`

Headings mark sections of a page. Headings are important to get right for accessibility. A visually impaired person will typically listen to the headings of a page first to orient themselves to the content on the page before proceeding. Sort of like a telephone menu, or like a book index.

Use the heading numbers in nested sequential order.

### `<button>`

Screen readers will pronounce as: "Button Text, Button." (eg: "Submit, Button")

### `<table>`

If you are providing tabular data to your user, use the `<table>` element to make it easier to navigate and understand the data being presented.

### `<label>`

Provide labels for form elements to give a larger surface area to click on and bring the form element into focus and provide context to the field.

### Landmarks

Landmarks mark regions of a page.

| name          | description                                                                                                                    |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| banner        | `header`: Contains things like a logo, identity of the site sponsor, site-specific search, etc                                 |
| complementary | `aside`: Content that complements the main content.                                                                            |
| contentinfo   | `footer`: Copyright, privacy, and accessibility statements                                                                     |
| form          | `form`: Grouped inputs, except search (see search landmark)<br/>Form should be identified in an `h` tag using `aria-labeledby` |
| main          | `main`: primary content on the page                                                                                            |
| navigation    | `nav`: list of links that are intended to be used for navigation of the website or page                                        |
| region        | `<section aria-labelledby="region-name">`                                                                                      |
| search        | search functionality for a website (`role=search` is required for this landmark)                                               |

### Semantic HTML Landmark Elements

There are [seven](https://en.wikipedia.org/wiki/HTML_landmarks) elements which inherit default landmark roles.

|     | html element | associated landmark                                                                             |
| --- | ------------ | ----------------------------------------------------------------------------------------------- |
| 1   | aside        | [complementary](https://www.w3.org/WAI/ARIA/apg/patterns/landmarks/examples/complementary.html) |
| 2   | footer       | [contentinfo](https://www.w3.org/WAI/ARIA/apg/patterns/landmarks/examples/contentinfo.html)     |
| 3   | form         | [form](https://www.w3.org/WAI/ARIA/apg/patterns/landmarks/examples/form.html)                   |
| 4   | header       | [banner](https://www.w3.org/WAI/ARIA/apg/patterns/landmarks/examples/banner.html)               |
| 5   | main         | [main](https://www.w3.org/WAI/ARIA/apg/patterns/landmarks/examples/main.html)                   |
| 6   | nav          | [navigation](https://www.w3.org/WAI/ARIA/apg/patterns/landmarks/examples/navigation.html)       |
| 7   | section      | [region](https://www.w3.org/WAI/ARIA/apg/patterns/landmarks/examples/region.html)               |

> NOTE: Do **not** manually set `role=` (legacy), instead use the proper semantic element.

## Color Contrast

|                                  | Level AA | Level AAA |
| -------------------------------: | :------: | :-------: |
|    **Normal**<br />`< 18pt/24px` |  4.5:1   |    7:1    |
| **Large**<br />`>= 14pt/18.66px` |   3:1    |   4.5:1   |

## Web Content Accessibility Guidelines (WCAG)

---

WCAG is a standard for web accessibility that assists in making websites more accessible.

### WCAG Four Principles:

1. **Perceivable**: Information and user interface components must be presentable to users in ways they can perceive.
2. **Operable**: Users must be able to operate any user interfaces or navigation, and interfaces cannot require an interaction the user cannot perform.
3. **Understandable**: Users must be able to understand the information or user interface that is presented. (Including bad error messages, such as "ERROR 113: ID-10T")
4. **Robust**: Content must be accessible by current assistive technologies and other user agents, and must remain accessible as those technologies advance.

### WCAG Conformance Levels

- Level A: Essential support (The bare minium)
- Level AA: Ideal Support (What most sites strive to achieve)
- Level AAA: Specialized Support (Not recommended for most sites as some content makes this level impossible to reach)

## ARIA

I started to make a glossary, but decided I couldn't do better than: [ARIA Important Terms](https://www.w3.org/TR/wai-aria/#dfn-landmark)

## Disability Types

### Auditory

---

#### Guidelines

- transcripts and captions of audio content
- media players that display captions
- provide options to adjust the **text size** and **text color** of captions
- provide playback options for audio content (stop, pause, skip back, skip forward, volume)
- high-quality foreground audio that is clearly distinguishable from any background noise or music
- provide alternatives to voice-only content
- To make web content more understandable to many people:
  - Providing simpler text that is supplemented by images, graphs, and illustrations
  - (and, where possible) Provide important information in sign language
    - Sign language may be preferable / primary language (and the individual may not read as well as they can sign)

#### Auditory Disabilities

- **hard of hearing**: mild to moderate hearing impairments in one or both ears
- **deafness**: substantial, uncorrectable impairment of hearing in both ears
- **deaf-blindness**: substantial, uncorrectable hearing and visual impairment

### Cognitive, Learning, and Neurological

---

#### Guidelines

- Content that is clearly structured and facilitates overview and orientation
  - Avoid complex page layouts (or provide simple layouts)
  - Avoid complex sentences and unusual words
  - Allow web browser controls to adapt page design or allow custom css
- Consistency in labeling forms, buttons, and content
- Predictable link targets, function, and interaction
- Multiple ways of navigating websites
  - hierarchial menu
  - search
  - Avoid complex navigation mechanisms
- Options to suppress blinking, flickering, flashing, animation, audio, music, and distracting content
- simpler text, supplemented by images, graphs, and illustrations
  - Avoid long passages of text without images, graphs, or illustrations to highlight context
- grammar and spelling tools, used by CLN individuals require developers to consider web accessibility requirements which are often shared by people with hearing, physical, speech, and visual disabilities.

#### Cognitive, Learning, and Neurological Disabilities

- **Attention deficit hyperactivity disorder (ADHD)**: difficulty focusing on a single task, focusing for longer periods, or being easily distracted
- **Autism spectrum disorder (ASD)**: involves impairments of social communication and interaction abilities, sometimes restricted habits and interests.
- **Dyslexia**: Language based skill impairment, such as reading and spelling that is not related to intelligence.
- **Intellectual disabilities**: Impairment of intelligence, slow learning, or difficulty understanding complex concepts. (eg: down syndrome, as one example)
- **Learning Disabilities**: A functional term, not a medical condition and is not uniformly defined.
- **Mental health disabilities**: Anxiety, delirium, depression, paranoia, schizophrenia, and many others. May result in difficulty focusing on information, processing information, or understanding it. Prescribed medication may have side effects including blurred vision, hand tremors, and other impairments.
- **Memory impairments**: Limited short-term memory, missing long-term memory, limited ability to recall language. (eg: dementia)
- **Multiple sclerosis**: Causes damage to nerve cells in the brain and spinal cord, and can result in auditory, cognitive, physical, or visual ability issues
- **Neurodiversity**: A societal rather than medical term used to describe the natural diversity in neurocognitive function (eg: gender, ethnicity, sexual orientation, and disability)
- **Perceptual disabilities**: Difficulty processing auditory, tactile, visual, or other sensory information. This can impact reading (dyslexia), writing (dysgraphia), processing numbers (dyscalculia), or spatial and temporal orientation.
- **Seizure disorders**: Includes different types of epilepsy and migraines, which may be in reaction to visual flickering or audio signals at certain frequencies or patterns

### Physical

---

Physical disabilities (motor disabilities) include

- weakness
- limitations of muscular control
  - involuntary movements
  - tremors
  - lack of coordination
  - paralysis
- limitations of sensation
- joint disorders (such as arthritis)
- pain that impedes movement
- missing limbs

#### Specialized Hardware

- Ergonomic or specially designed keyboard and/or mouse
- Head pointer, mouth stick, or other aids to help with typing
- On-screen keyboard with trackball, joysticks, or other pointing device
- Switches operated by foot, shoulder, sip-and-puff, or other movements
- Voice recognition, eye tracking, and other approaches for hands-free interaction

#### Guidelines

> Note: People with cognitive and visual disabilities may also benefit from these guidelines

- Design for people using only a mouse or only a keyboard (or analogue)
- Provide full keyboard support (shortcuts, navigation, etc)
- Provide ample time to type, click, or carry out interactions (especially forms)
- Users may not be able to "chord" keys, and may only be able to press a single key at a time (not `ctrl+s` for example)
- Provide large clickable areas
- Provide error correction options (especially for forms)
- Provide visible indication of the current focus
- Provide mechanisms to skip over blocks, such as page headers and navigation bars
- Provide Consistent, Predictable, and simple navigation mechanisms and page functions

#### Physical Disabilities

- **Amputation**: Missing fingers, limbs, or other parts of the human body
- **Arthritis**: Inflammation, degeneration, or damage to the joints
- **Fibromyalgia**: Chronic pain of muscle and connective tissue
- **Rheumatism**: See Arthritis and Fibromyalgia
- **Reduced Dexterity**: A functional term (not medical) that describes disability in the control of the hand, such as hand-eye coordination
- **Muscular dystrophy**: Progressive weakness and degeneration of muscles
- **Repetitive stress injury (RSI) and Cumulative Trauma (CT)**: Injuries to the musculoskeletal system and the nervous system from repetitive tasks and damage
- **Tremor and spasms**: Involuntary movement or muscle contraction, including short twitches, and continual or rhythmic muscle contractions
- **Quadriplegia**: Partial or total paralysis to all four body limbs and the torso

### Speech

---

Speech disabilities include difficulty producing speech that is recognizable by others or by voice recognition software.

#### Guidelines

- Provide some manner of company contact (eg: e-mail or chat) and not just a phone number or voice service
- Don't limit user interface interaction to voice command (as cool as that could be)

#### Speech Disabilities

- **Apraxia of speech (AOS)**: inconsistent articulation and production of speech sounds, and errors producing sounds in the correct order making spoken words and phrases difficult to understand.
- **Cluttering**: includes increased speaking rate, incorrect rhythm, intonation, and co-articulation of sounds, and other influent speech that is sometimes similar to stuttering.
- **Dysarthria**: Weakness or complete paralysis of muscles that are necessary to produce speech, including lips, lungs, throat, tongue, and others.
- **Speech sound disorder**: Inability to produce certain sounds or patterns of sound and sometimes results in addition, distortion, omission, or substitution of such sounds with others.
- **Stuttering**: influent (not flowing) speech, repetition of individual sounds or entire words and phrases, and misplacement or prolongation of pauses and sounds while speaking that is different from cluttering.
- **Muteness**: inability to speak due to various reasons such as anxiety, brain injuries, or inability to hear and learn speech.

### Visual

---

#### Guidelines

- Allow enlarging or reducing text size
- Ensure information (text, images, etc) is not lost when resizing the page
- Ensure video content has text or audio alternatives (eg: audio-description track)
- Keep navigation mechanisms simple, consistent, and standard
- Ensure there is sufficient contrast between foreground and background in visual content (video, images)
- Allow custom colors
- Provide customization settings for fonts, colors, and spacing
- Ensure lists, headings, tables, and page structure is correctly identified by browsers and assistive technologies
- Support multiple presentations of the content and multiple ways of interaction
  - Consider not being able to see color / contrast / seeing entirely modified colors
  - Consider only seeing small portions of the content at a time
  - Consider keyboard only navigation due to not being able to see a mouse cursor
- Provide full keyboard support
- Ensure there is alt text for Images, Controls, and Structural elements (?)
- Test Hardware and Software solutions
  - Listen to text-to-speech (TTS) synthesis of your content
  - Listen to audio descriptions of visual content on your site
  - Read your site using refreshable Braille

#### Visual Disabilities

- **Color Blindness**: difficulty distinguishing between colors such as between red and green, or between yellow and blue, and sometimes inability to perceive any color.
- **Low vision**: Poor acuity (vision not sharp), tunnel vision, central field loss, clouded vision
- **Blindness**: substantial, uncorrectable loss of vision in both eyes
- **Deaf-blindness**: substantial, uncorrectable visual and hearing impairments.

## Disability Aspects

| Aspect                  | Description                                                                                                                                                                              |
| ----------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| age                     | functionally the same as other disabilities, but can have significant differences in regards to assistive technology                                                                     |
| multiple disabilities   | combinations of disabilities can result in additional a11y needs (eg: deaf + partially blind = captions helpful, but only if they can be resized with high contrast)                     |
| health conditions       | limited stamina, dexterity, concentration resulting in fatigue, pain, and other symptoms that limit the duration or extent of their web use                                              |
| changing abilities      | progressive or recurring limitations that impact usage differently at different times                                                                                                    |
| temporary impairments   | temporary impairments, such as those brought on by injury, surgery, or medication. note: the individual may not know about a11y solutions or features, or even be unaware of their needs |
| situational limitations | constraints due to surroundings, such as a loud concert, bright sunlight, internet issues, unable to afford assistive technologies, etc                                                  |

## Accessibility Tools and Software

### Screen Readers

#### [NVDA](https://www.nvaccess.org/download/)

NVDA is modal, meaning there are modes you enter/exit, changing the way you interact with the reader.

For example, entering "application" mode or "form" mode to allow typing in input boxes.

- Free
- Windows Only
- [NVDA Shortcuts](https://dequeuniversity.com/screenreaders/nvda-keyboard-shortcuts)

#### Orca

- Free
- Linux (Gnome) (on/off: `Super` + `Alt` + `S`)
- $ `orca -s` to access screen reader preferences to configure
- `/home/user/.local/share/orca` (delete if settings get messed up, like they did for me)

#### [ChromeVOX](https://support.google.com/chromebook/answer/7031755?hl=en)

- ChromeOS

#### [JAWS](https://www.freedomscientific.com/products/software/jaws/)

($95-1285/year)

## Gotchas

- Don't work around screen reader mispronunciations using things like `aria-label`, as that changes the captions and is what will be displayed on braille readers. People using screen readers are used to the mispronunciation quirks and prefer that you leave things as they are and let them work around it in their software, if they choose.
