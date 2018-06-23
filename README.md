# Advance CSS Course Notes

Advance CSS and Sass by Jonas Schmedtmann Course Notes

## Table of Contents

<!-- TOC -->

- [Advance CSS Course Notes](#advance-css-course-notes)
  - [Table of Contents](#table-of-contents)
  - [Progress](#progress)
  - [Section 01: Intro](#section-01-intro)
  - [Section 02: Natours Project - Part 01](#section-02-natours-project---part-01)
  - [Section 03: How CSS Works Behind the Scenes](#section-03-how-css-works-behind-the-scenes)
  - [Section 04: Introduction to SASS](#section-04-introduction-to-sass)
  - [Section 05: Natours Project - Part 02](#section-05-natours-project---part-02)

<!-- /TOC -->

## Progress

- [X] ~~*Section 01*~~ [2018-06-17]
- [X] ~~*Section 02*~~ [2018-06-17]
- [X] ~~*Section 03*~~ [2018-06-17]
- [X] ~~*Section 04*~~ [2018-06-23]
- [ ] Section 05
- [ ] Section 06
- [ ] Section 07
- [ ] Section 08
- [ ] Section 09
- [ ] Section 10

## Section 01: Intro

- Nothing of note, but I'm excited to skill up my CSS-fu.

## Section 02: Natours Project - Part 01

- **Best Practice**: wrap images inside a containing div
- **Best Practice**: control height and let width auto-scale for width
- Quick way to center elements relative to parent container:

```css
.element {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
```

- `transform` ➡ relative to parent element
- `translate` ➡ relative to element itself
- Two Types of Animations in CSS:
  1. transtition property
  2. CSS Animations (`@keyframes`)
- **Best Practice**: Browser optimized for opacity and transform animations (Don't go overboard with animations)
- `animation-delay` ➡️ animation delay in seconds or ms.
- `animation-iteration-count` ➡️ number of times animation will loop
- `animation-timing-function` ➡ ease, ease-in, ease-out, ease-in-out, linear, step-start, step-end
  - `ease-in` slow at start, good for element moving out 🚀
  - `ease-out` slow at end, good for element moving in 🇳🇮
- `backface-visibility: hidden` ➡️ hack to use if animation is shaky
- `display: inline-block` treated as text, can use `text-align: center` on parent element to center text horizontally
- `box-shadow: x-axis y-axis blur rgba` ➡️ adds 3D effect (elements cast shadow - raised elements relative to page plane)

## Section 03: How CSS Works Behind the Scenes

- **Three Pillars of Writing Good HTML and CSS**
  - **Responsive Design**
    - Fluid Layouts
    - Media queries
    - Responsive images _BIG TOPIC_
    - Correct units _Finally!_
    - Desktop-first vs mobile-first
  - **Maintainable and scalable code**
    - Clean
    - Easy-to-understand
    - Growth
    - **Reusable**
    - How to organize files
    - How to name classes
    - How to structure HTML
  - **Web Performance**
    - Less HTTP requests
    - Less code
    - Compress code
    - Use CSS preprocessor
    - Less images
    - Compress images
- **CSS Rules**: selector, declaration block, css property, declared value
- **The Cascade**: Process of combining different stylesheets and resolving between different CSS rules and declarations, when more than one rule applies to a certain element
- Author (me), User (client), Browser(user agent) styles
- Importance > Specificity > Source Order
- **Importance**
  1. User !important
  2. Author !important
  3. Author declarations
  4. User declarations
  5. Default browser declarations
- **Specificity**
  1. Inline styles
  2. IDs
  3. Classes, pseudo-classes, attribute
  4. Elements, pseudo-elements
  Specificity ➡️ (Inline, IDs, Classes, Elements)
- **Source Order**
  1. If above is equal, last rule is applied
- _Universal Selector_ * has specificity of (0,0,0,0)
- **Value Processing**:
  - Declared Value
  - Cascaded Value (winner among declared values)
  - Specified Value (default value if no cascade value)
  - Computed Value (relative units to absolute)
  - Used Value (final calc, based on layout, part of render)
  - Actual Value (rounding of Used Values)
- Relative Units (%, rem, em) to Absolute (px)
  - % fonts ➡️ based on parent's font-size
  - % lengths ➡️ based on parent's **width**
  - em fonts ➡️ based on parent's font-size
  - em lengths ➡️ based on current elements font-size
  - rem ➡️ based on root element font-size
  - vh ➡️ viewport height
  - vw ➡️ viewport width
- **Inheritance**
  - With inheritance, child property values are inherited from parent's computed values
- **Responsive Design Reset Tricks**

```scss
/* The NEW reset standard */
*,
*::before,
*::after {
  margin: 0;
  padding: 0;
  box-sizing: inherit;
}

html {
  font-size: 62.5%
}

body {
  box-sizing: border-box;
}
```

- **Visual Formating Model** ➡️ Algorithm that calculates box sizes and layout
  - Box Model: content, padding, border, margin, fill area
  - Box Type: inline, inline-block, block;
  - Positioning: static, relative, absolute, fixed, sticky
  - Stacking Context: z-index
- Layout: THINK, BUILD, ARCHITECT
- Component-Driven Design: modular-building blocks, re-usable, independent of parent elements
- BEM ➡️ Block__Element--Modifier
- Block ➡️ standalone component that is meaningful on its own
- Element ➡️ part of block that has no standalone meaning
- Modifier ➡️ a different version of block or element
- The 7-1 Pattern:
  - `/base`
  - `/components`
  - `/layout`
  - `/pages`
  - `/themes`
  - `/abstract`
  - `/vendors`

## Section 04: Introduction to SASS

- SASS ➡️ is a CSS preprocessor, an extension of CSS that adds power and elegance to the basic language
  - Variables ➡️ reusable values
  - Nesting ➡️ nested selectors
  - Operators ➡️ math
  - Partials and imports
  - Mixins ➡️ reusable CSS code
  - Functions
  - Extends ➡️ fancy inheritance for selectors
  - Control directives
  - Clearfix hack to prevent the GreatCollapse:

```scss
.clearfix::after {
  content: '';
  clear: both;
  display:table;
}
```

- SASS functions: `darken($color, 10%)` or `lighten($color, 10%)`

- mixin: reusable piece of code for css styling (clearfix mixin below)

```scss
@mixin clearfix {
  &::after {
    content: '';
    clear: both;
    display: table;
  }
}

nav {
  @include clearfix;
}
```

- Mixins can take arguments:

```scss
@mixin style-link-text($color) {
text-decoration: none;
text-transform: uppercase;
color: $color;
}
```

- DRY Code: Don't Repeat Yourself

- SASS functions:

```scss
@function divide($a, $b) {
  @return $a / $b;
}
```

- Extends (%):

```scss
%btn-placeholder {
  padding: 10px;
  display: inline-block;
  text-align: center;
  border-radius: 100px;
  width: $width-button;
  @include style-link-text($color-text-light)
}
```

- Mixins copies styling code into the body of calling selector, while with extends the selector replaces the extend-selector

## Section 05: Natours Project - Part 02

