# CSS Styleguide

## Table of Contents

1. [Syntax & Formatting](#syntax-and-formatting)
2. [Default Styles](#default-styles)
3. [Classes, IDs & Variables](#classes-ids-and-variables)
4. [Naming Convention](#naming-convention)
5. [Declaration Sorting](#declaration-sorting)
6. [Numbers](#numbers)
7. [Colors](#colors)
8. [Organization](#organization)
9. [Nesting & Chaining](#nesting-and-chaining)
10. [Typography](#typography)
11. [Images](#images)

## Syntax and Formatting

This section deals with the basic formatting that all stylesheets must follow. The reason for this is that it is the foundation to consistency and how code is displayed in programs like Github.

The basic guidelines are as follows:

- ["four" width tabs (i.e., no spaces)](#four-width-tabs)
- [proper ruleset anatomy](#proper-ruleset-anatomy)
- [no trailing whitespace](#no-trailing-whitespace)
- [meaningful new line breaks](#meaningful-new-line-breaks)
- [use alignment when possible](#use-alignment)
- [80 characters wide lines](#80-characters-wide)
- [use double quotes](#use-double-quotes)

[&uarr; Back to Table of Contents](#table-of-contents)

### Four Width Tabs

Here are the general guidelines for managing indentation in CSS:

- use hard indents (spaces)
- **never** mix spaces and tabs for indentation

[&uarr; Back to Syntax & Formatting](#syntax-and-formatting)

### Proper Ruleset Anatomy

As a review the basic terminology of CSS rulesets, here they are:

```
[selector] {
  [property]: [value];
  [<--declaration-->]
}
```

The general guidelines to follow are:

- one space between the selector and opening curly bracket
- one declaration per line (no exceptions)
- no space between the property and the colon
- one space between the colon and the value
- end every declaration with a semi-colon
- closing curly bracket lives in its own new line

#### Example

```css
// Correct
.class-name {
  width: 100%;
  height: 50px;
  padding: 2em;
}

// Wrong
.class-name
{
  width:100%; height:50px;
  padding:2em }
```

#### Additional Guidelines

The following sections prescribe more specific treatmenet of different scenarios:

##### Multiple Selectors

When declaring multiple selectors for a declaration block, each selector should be on its own line and alphabetized. The primary exception to this rule is for related selectors.

###### Example

```css
// Good
.bar,
.baz,
.foo, .foo--md {
  ...
}

// Bad
.foo, .baz, .foo--md, .bar {
  ...
}
```

#### Single-line Rulesets

Particularly when declaring multiple modifier classes that only change one aspect of the parent class, be sure to use a single-line ruleset with alignment for optimum readability.

##### Example

```css
// Good
.btn {
  ...
}

.btn--caution { color: $yellow; }
.btn--error   { color: $red;    }
.btn--primary { color: $green;  }


// Acceptable, but the whitespace is overly verbose
.btn {
  ...
}

.btn--caution {
  color: $yellow;
}

.btn--error {
  color: $red;
}
.btn--primary {
  color: $green;
}
```

More specific rules regarding formatting will occur in the applicable sections (i.e., numbers, units, etc.).

[&uarr; Back to Syntax & Formatting](#syntax-and-formatting)

### No Trailing Whitespace

#### Rationale

Whitespace is invisible to the naked eye unless used between characters. In other words, having whitespsace at the end of a line of text means extra data (i.e., larger files) for no reason.

#### Recommendation

Most text editors have a setting that will automatically trim off trailing whitespaces on save.

**Sublime Text**: `trim_trailing_white_space_on_save": true`

[&uarr; Back to Syntax & Formatting](#syntax-and-formatting)

### Meaningful New Line Breaks

While other sections deal specifically with whitespace from a granular syntax perspective (i.e., space between a colon and a value), this section deals with new line breaks.

#### Space Between Rulesets

Each ruleset should be separated by one new line.

##### Example

```css
// Good
.class-one {
  ...
}

.class-two {
  ...
}

// Bad
.class-one {
  ...
}
.class-two {
  ...
}
```

#### Space Between Sections of Rulesets

When you have multiple sections in a single partial, utilize two line breaks between separate sections.

##### Example

```css
// Number related styles
.number-even {
  ...
}

.number-odd {
  ...
}


// Letter related styles
.letter-vowel {
  ...
}

.letter-consonant {
  ...
}
```

#### Spacing in Nested Items

When nesting selectors, use the following guidelines for line breaks:

- declarations for that selector follow immediately on the next line
- nested selectors or pseudo-selectors require one new line break

##### Example

```scss
.parent-class {
  width: 100%;
  height: 50%;

  .nested-class {
    ...
  }
}

.parent-class-2 {

  .nested-class-2 {
    ...
  }
}
```

[&uarr; Back to Syntax & Formatting](#syntax-and-formatting)

### Use Alignment

Align common and related strings as much as possible. This can either be the declarations or the values themselves.

#### Example

```css
// Best
.class-name {
  position: absolute;
  top:    0;
  bottom: 0;
  right:  0;
  left:   0;

  -webkit-border-radius: 8px;
     -moz-border-radius: 8px;
          border-radius: 8px;
}

// Acceptable, but not ideal
.class-name {
  position: absolute;
  top: 0;
  bottom: 0;
  right: 0;
  left: 0;

  -webkit-border-radius: 8px;
  -moz-border-radius: 8px;
  border-radius: 8px;
}
```

#### Rationale

In addition to being much easier to parse, most developers work in text-editors that support column editing for fast changes if this format is followed.

[&uarr; Back to Syntax & Formatting](#syntax-and-formatting)

### 80 Characters Wide

#### Rationale

This is an industry standard due to:

- improved legibility for files opened side by side
- improved readability on sites such as Github or on terminal windows
- provides a good comfortable line length for comments

Things like URLs and gradient syntax are naturally exempt from this rule.

[&uarr; Back to Syntax & Formatting](#syntax-and-formatting)

## Default Styles

These are recommended global styles to keep your life as easy as possible.

Set default box-sizing to be border-box. If you don't know why, feel free to check out [Chris Coyier's post on it here](https://css-tricks.com/international-box-sizing-awareness-day/).

```css
*,
*:after,
*:before {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}

html {
  box-sizing: border-box;
}
```

## Classes, IDs and Variables

The following conventions for basic classes, IDs, and variables should be very strictly followed:

- in lowercase
- multi-word names are separated by a hyphen (i.e., no camel case or underscores)
- they must be as short as possible, but as long as necessary [Google Styleguide](https://google.github.io/styleguide/htmlcssguide.xml)
- try and avoid naming classes with expressive styles (e.g., btn--green) and instead structure classes towards Atomic Design thinking (e.g., btn--primary)

### Constants

The only exception to these conventions are constants in preprocessors which have the following guidelines:

- all upppercase
- multi-word constants will be separated via underscore instead of a hyphen

[&uarr; Back to Table of Contents](#table-of-contents)

### Use Double Quotes

Use double quotes in your styles. This is particularly important for:

- String literals: `content: "";`
- URLs: `background: url("img/image.jpeg");`
- Attribute values: `input[type="radio"]`

[&uarr; Back to Table of Contents](#table-of-contents)

## Naming Convention

### Why Use a Naming Convention?

[Cole Peters](https://blog.colepeters.com/building-and-shipping-functional-css/) sums it up best in the excerpt below:

"Performance is critical. Bloated stylesheets cost users time, money, and processing cycles spent computing values. They also quickly push a website’s payload towards the initial congestion window (which is a mere 14.6kb, compressed).

Clarity trumps cleverness. Via Brent Jackson: “Simple, obvious styles are quicker to internalize, easier to use, and more widely adopted.”

Classes should be as reusable as possible. Via Adam Morse: “For every property you add to a class, the less reusable it becomes.”

Classes should be composable and free of side-effects. Via Jon Gold: “Not only should a class do the same thing every time, but it should never, ever change anything other than what you’re targeting."

### e84 Naming Convention

Here at Element 84, we utilize a naming convention inspired from Una's [Atomic OOBEMITSCSS](http://www.sitepoint.com/atomic-oobemitscss/).

The two key pillars of Element 84's naming convention are:

1. [Atomic Design](http://bradfrost.com/blog/post/atomic-web-design/) by Brad Frost
2. [BEM Documentation](https://en.bem.info/)

More details will be fleshed out regarding implementation, but the main concern is to properly architect all styles. **If you simply try and style according to the visual comp, you have not done your job.** Every single style must fit into the architecture as a whole.

[&uarr; Back to Table of Contents](#table-of-contents)

## Declaration Sorting

Ordering properties is a hotly debated topic in the community, but the model we will be using is called “Concentric CSS” and relies on the box-model to define the order of properties. In other words, start from the outside, and move inward as you go down the properties. This allows more specific details to sit lower on each selector.

### CSS Declarations

The basic order for CSS declarations is:

1. Position
2. Box Model
3. Content/Granular Styles
4. Animations

```scss
// Example
.some-class {
  // Position-related styles
  position: absolute;
  top: 50px;

  // Display-related styles
  display: inline-block;
  z-index: 999;

  // Box-model-related styles
  margin: 2em;
  border: 1px solid rgb(0, 0, 0);
  padding: 2em;
  width: 100px;
  height: 200px;
  background: rgb(255, 255, 255);
  overflow: hidden;

  // Content/Granular styles
  font-family: sans-serif;
  font-weight: bold;
  font-size: 1.5em;
  color: rgb(100, 255, 100);

  // Animations
  transition: 1s ease-in-out all;
}
```

### Sass Declarations

When using Sass, these guidelines take precendence to the CSS declaration from the previous section:

1. Local variables are the first thing declared before any declarations, and spaced from declarations by a new line
2. Mixin calls with no @content come next
3. Extend calls are last since it relates to pure CSS declarations

```scss
// Example
.some-class {
  // Variables
  $some-variable: "lorem string";
  $new-color: rgb(100, 100, 100);

  // Mixins
  @include cool-mixin;

  // Extend
  @extend .base-class;

  // Regular CSS properties
  ...

  // Nested Selectors
  .different-class {
    ...
  }
}
```

[&uarr; Back to Table of Contents](#table-of-contents)

## Numbers

This is a particularly important section as far as consistency goes for making it easier for developers to follow any mathematical computations.

The general guidelines are as follows:

- [values less than one have a leading zero](#leading-zeros)
- [no trailing zeros allowed](#trailing-zeros)
- [no space between a number and its unit](#units)
- [zeros do not have units](#units)
- [all calculations are wrapped in parentheses](#calculations)
- [add a space between operators in calculations](#calculations)
- [avoid magic numbers](#magic-numbers)

[&uarr; Back to Table of Contents](#table-of-contents)

### Zeros

#### Leading Zeros

All values less than one must display a leading zero before the decimal.

##### Example

```css
// Good
.some-class {
  padding: 0.5em;
  color: rgba(1, 1, 1, 0.9);
}

// Bad
.some-class {
  padding: .5em;
  color: rgba(1, 1, 1, .9);
}
```

##### Rationale

While there are arguments for why one should drop the zero, it is a best practice in math, science, medical, and engineering fields to always have a leading zero to values less than one. Again, consistency is the key focus here: 1.5 has a trailing number, and thus should 0.5. And if you look at the examples above, you’ll see that it’s not as easy to parse when the leading zero is missing.

#### Trailing Zeros

Never display trailing zeros. Never. Ever. Period.

```css
// Only choice
.some-class {
  padding: 2.5em;
  margin: 10px;
}

// Horrible
.some-class {
  padding: 2.50em;
  margin: 10.0px;
}
```

[&uarr; Back to Numbers](#numbers)

### Units

All units will be immediately behind the desired value. This is not only standard practice, but also is pertinent to how values are processed and can impact how the browser renders the value.

```css
// Always do this
.some-class {
  width: 100px;
  height: 2.5em;
}

// Never do this
.some-class {
  width: 100 px;
  height: 2.5 em;
}
```

All zero units will have no units attached to them.

```css
// So clean
.some-class {
  margin: 0;
  padding: 0;
}


// Wasted space
.some-class {
  margin: 0em;
  padding: 0px;
  }
```

[&uarr; Back to Numbers](#numbers)

### Calculations

All calculations should always be wrapped in parentheses. Not only does this improve readability, but it also ensures that any processing will be calculated as intended.

```css
// Good
.some-class {
  width: (100% / 7);
}

// Okay, but leaves room for error
.some-class {
  width: 100% / 7;
}
```

In addition, always leave a space between the mathematical operator in order to improve readability.

```css
// Good
.some-class {
  width: (2.5em * 3.33);
}

// Bad
.some-class {
  width: (2.5em*3.33);
}
```

[&uarr; Back to Numbers](#numbers)

### "Magic Numbers"

There will be times when you will define values that happen to “just work” in a specific context. This is to be avoided, but it does happen.

In the event that you need to use a specific number that does not have any reasonable explanation for why a certain number works, always add a comment to explain the thought process behind it.

```css
// Best
.some-class {
  // This magic number works because the parent impacts the position, but we should try and properly fix it in the future
  top: 0.932em;
}

// Okay, but future developers will be puzzled.
.some-class {
  top: 0.932em;
}
```

[&uarr; Back to Numbers](#numbers)

## Colors

### Notation Preference

The recommended color formats to use are listed in order of preference (from best to least preferred).

1. RGB Notation
2. HSL Notation*
3. Hexadecimal Notation**

However, for code brevity purposes; when defining your colors in a partial, use the following format:

```scss
$white: #fff; // rgb(255, 255, 255)
$black: #000; // rgb(  0,   0,   0)
```

*Sass guidelines recommends HSL as the best format to use due to the ease of creating colors, but it seems that RGB is still more commonly used, so we’ll stick with this for now.

**While hexadecimal is commonly used, it is close to indecipherable for the human brain as far as telling which color it is. In addition, it has no ability to add opacity which makes it less useful.

### Formatting

In addition to the CSS formatting practices in [Syntax & Formatting](#syntax-and-formatting), the following formatting should be followed for the respective notation.

#### RGB and HSL Notation

The general guidelines for RGB and HSL notation are as follows:

- no space between rgba/hsl and the opening parentheses
- no space between the opening parentheses and the first value
- no space between the closing parentheses and the last value
- space after every comma

##### Example

```css
// Good
.some-class {
  color: rgb(255, 255, 255);
  border-color: hsl(0, 100%, 50%);
}

// Bad
.some-class {
  color: rgb ( 255,255,255 );
  border-color: hsl ( 0,100%,50% );
}
```

#### Hexadecimal Notation

The general guidelines for hexadecimal notation are as follows:

- always use lowercase for improved readability
- shorten to three characters whenever possible

##### Examples

```css
// Good
.some-class {
  color: #fff;
  border-color: #6a5acd;
}

// Bad
.some-class {
  color: #FFFFFF;
  color: #6A5ACD;
}
```

[&uarr; Back to Table of Contents](#table-of-contents)

## Organization

Unless you are working on a very small project that requires very little CSS work, all styles should be broken out into different stylesheets that will be concatenated during the build step.

*Note: This section is written with the assumption that a preprocessor (i.e., Sass) is being used.*

### Overview of Architecture

*"All we had was a single CSS file, longer than a sleepless night." - Hugo*

*"A place for everyting and everything in its place." - Mrs. Beeton*

This architecture is based on a hybrid of SMACSS, ITCSS, and the 7-1 pattern from Sass.

The following is a comprehensive list of the folders that will comprise the full architecture listed in the order of importing:

1. [settings](#settings)
2. [vendor](#vendor)
3. [base](#base)
4. [layout](#layout)
5. [components](#components)
6. [pages](#pages)
7. [overrides](#overrides)

### Folder Definitions

#### Settings

This is where all the code and settings that don't compile to CSS lives. Examples of this include:

- variables
- mixins
- functions
- tools and helpers

If there are a large number of any one type of setting (i.e., mixins), create a sub-folder and organize them into their own partials.

[&uarr; Back to Organization](#organization)

#### Vendor

These contain files written by other people. Examples of this include external frameworks or libraries such as:

- Bootstrap
- grid frameworks
- third party styles

[&uarr; Back to Organization](#organization)

#### Base

This folder contains the lowest level changes that setup the foundation for enhancement with future styles. Examples include:

- resets and normalize
- typography settings
- styles for primitive HTML elements

[&uarr; Back to Organization](#organization)

#### Layout

This folder establishes the layouts that the project utilizes. Examples of this include:

- header
- main
- aside
- footer
- page layout

The key to this folder is to keep broad reusable layout styles here. Customized styles for specific page templates or layouts will come later on.

[&uarr; Back to Organization](#organization)

#### Components

This is where all the modules that make up the different sections of the site will live. Examples include:

- carousels
- accordians
- tabs
- social media bar

When creating the respective partials, try to adhere to [Atomic design principles](http://bradfrost.com/blog/post/atomic-web-design/). And if needed, create additional subfolders.

[&uarr; Back to Organization](#organization)

#### Pages

This folder will hold all custom page-styles that are more edge-case than a reusable module. Examples of this include:

- light/dark themes
- tailored styles to the home page
- custom pages for temporary marketing campaign

[&uarr; Back to Organization](#organization)

#### Overrides

This folder contains all styles that will take priority over the reusable modules written above. Examples of this include:

- alignment overrides
- display toggling classes
- positioning overrides

In addition, this folder will typically contain a `_hotfix.scss` for emergency changes where there is insufficient time for proper CSS development. The caveat with is that **all code in this file must be refactored by the next sprint**. Failure to do so will corrode the entire CSS architecture.

[&uarr; Back to Organization](#organization)

### Nesting and Chaining

While this could be considered a sub-category somewhere else, the importance of this topic merits its own category.

As a rule of thumb, do not nest (with a preprocessor) or chain selectors together.

The exceptions to this rule include:

- pseudo-selectors (i.e., :hover, :visited, etc.)
- component agnostic states like `.is-active`

If nesting (i.e., chaining) is used however, it should be no more than one level and should be used with intent while considering all other aspects of the CSS architecture.

In other words, if you find yourself using nesting (i.e., chaining), make sure you have tried finding a flatter way of doing so. And if you really think there's no other way, be ready to defend your decision when the code review comes around.

#### Rationale

As far as the short version of why this is the case, it boils down to one simple thing: avoiding [specificity wars](http://cssguidelin.es/#specificity). It is too often the case where CSS architecture dissolves into a chaotic spreadsheet because of people improperly using nesting (i.e., chaining).

[&uarr; Back to Table of Contents](#table-of-contents)

## Typography

For typography styles, we will follow the recommended strategy from Robin Rendle in his post [Use `rem` for Global Sizing; Use `em` for Local Sizing](https://css-tricks.com/rem-global-em-local/).

1. Define `font-size` of the document with `px`.

```scss
html {
  font-size: 16px;

  @media screen and (min-width: 900px) {
    font-size: 18px;
  }

  @media screen and (min-width: 1200px) {
    font-size: 20px;
  }
}
```

2. Define all textual elements (i.e., paragraphs, headings, blockquotes) with `em` because they share a relationship with each other.

```scss
h2 {
  font-size: 2em;
}

p {
  font-size: 1em;
}

pre {
  font-size: 0.8em;
}
```

3. Style all text within modules/components with `rem` so text is easily changed globally.

```scss
.module {
  font-size: 1.1rem;
}

.component {
  font-size: 1.3rem;
}
```

[&uarr; Back to Table of Contents](#table-of-contents)

## Images

Inspired by Ire Aderinokun's post on [Styling Broken Images](http://bitsofco.de/styling-broken-images/), it is strongly recommended to provide graceful degradation of images when they are broken.

Here is a sample style for broken images:

```scss
img {
  /* Same as first example */
  min-height: 50px;
}

img:before {
  content: " ";
  display: block;

  position: absolute;
  top: -10px;
  left: 0;
  height: calc(100% + 10px);
  width: 100%;
  background-color: rgb(230, 230, 230);
  border: 2px dotted rgb(200, 200, 200);
  border-radius: 5px;
}

img:after {
  content: "\f127" " Broken Image of " attr(alt);
  display: block;
  font-size: 16px;
  font-style: normal;
  font-family: FontAwesome;
  color: rgb(100, 100, 100);

  position: absolute;
  top: 5px;
  left: 0;
  width: 100%;
  text-align: center;
}
```

[&uarr; Back to Table of Contents](#table-of-contents)
