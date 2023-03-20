- [Accessibility (a11y)](#accessibility-a11y)
  - [Links](#links)
  - [Disability Types](#disability-types)
    - [Auditory](#auditory)
      - [Guidelines](#guidelines)
      - [Glossary](#glossary)
    - [Cognitive, Learning, and Neurological](#cognitive-learning-and-neurological)
      - [Guidelines](#guidelines-1)
      - [Glossary](#glossary-1)
    - [Physical](#physical)
      - [Specialized Hardware](#specialized-hardware)
      - [Guidelines](#guidelines-2)
      - [Glossary](#glossary-2)
    - [Speech](#speech)
      - [Guidelines](#guidelines-3)
      - [Glossary](#glossary-3)
    - [Visual](#visual)
  - [Disability Aspects](#disability-aspects)
  - [Accessibility Tools and Software](#accessibility-tools-and-software)
    - [Screen Readers](#screen-readers)

# Accessibility (a11y)

## Links

| Page Name                                                                                                                   | Description                                  |
| --------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------- |
| [Diverse Abilities and Barriers](https://www.w3.org/WAI/people-use-web/abilities-barriers/)                                 | W3C Explanation of Disabilities              |
| Wikipedia [WCAG (Web Content Accessibility Guidelines)](https://en.wikipedia.org/wiki/Web_Content_Accessibility_Guidelines) | Contains multiple relevant links and history |

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

#### Glossary

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

#### Glossary

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

#### Glossary

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

Speech disabilities include difficulty producing speech that is recognizable by others or by voice recognition software

#### Guidelines

- Provide alternate options to voice-only interaction (such as text-based chat)

#### Glossary

### Visual

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

[NVDA](https://www.nvaccess.org/download/) (Free)

[JAWS](https://www.freedomscientific.com/products/software/jaws/) ($95-1285/year)
