# HTML Styleguide

## Table of Contents

1. [Base Template](#base-template)
2. [Syntax & Formatting](#syntax-and-formatting)
3. [Accessibility](#accessibility)

## Base Template

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title></title>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
  </head>
  <body>
  </body>
</html>
```

[&uarr; Back to Table of Contents](#table-of-contents)

## Syntax and Formatting

### Quotation Marks

Use double quotation marks for all attributes.

#### Example

```html
<!-- Good -->
<a href="www.element84.com">Element 84</a>

<!-- Bad -->
<a href='www.element84.com'>Element 84</a>
```

[&uarr; Back to Table of Contents](#table-of-contents)

## Accessibility

This section addresses general guidelines for best practices with creating accessible HTML documents.

- [Language Attribute](#language-attribute)
- [Landmark Roles](#landmark-roles)
- [Links](#links)
- [Images](#images)
- [Forms](#forms)
- [Audio and Video](#audio-and-video)
- [Color Contrast](#color-contrast)
- [Invisible Content](#invisible-content)

### Language Attribute

Declare a language attribute on all HTML documents to ensure that screen readers are able to read out the text with the correct pronunciation.

#### Example

`<html lang="en">`

### Landmark Roles

Ensure the following ARIA Landmark Roles are used in your document if they exist on the page:

- `<header role="banner">`
- `<nav role="navigation">`
- `<main role="main">`
- `<article role="article">`
- `<aside role="complementary">`
- `<footer role="contentinfo">`
- `<form role="search">`

### Links

Popular misconception: The proper attribute for links is `title`, not `alt`.

Rule of thumb: With that said, **don't** use the `title` attribute except in special circumstances.* Instead, all anchor tags must have text (even if hidden away visually).

While the attribute is usually perceived to be an accessibility bonus, the opposite is actually true. So just serve all of your users the same content.

*The exception to this is when using `<frame>` or `<iframe>` elements.

### Images

All image tags used for content are **required** to have an `alt` attribute.

Contrary to popular belief, the `alt` attribute describes the function of an image, as opposed to a detailed description of the image. As a result, just because an image is used multiple times on a page does not automatically mean that the alt tag is the same for each one.

In the event that there is no functional purpose for the image (i.e., decorative container borders), then it is appropriate to leave the `alt` attribute with an empty string. This is **not** the same as leaving off the attribute itself.

### Forms

The basic guidelines for forms are as follows:

- there is a logical layout (i.e., tabbing through the form follows a logical pattern)
- a `label` exists for all form controls even though it may be visibly hidden
- ensure that `placeholder` attributes are **NOT** being used in place of `label` tags
- group related form elements with `fieldset`

### Audio and Video

It is mandatory that all auditory and visual media is accessible to people who are deaf or hard of hearing. Whenever possible, try to do both of the following:

- text transcripts
- synchronized subtitles for videos

### Color Contrast

Best done early in the design process, ensure that your text color and background-color meet the contrast ratio for users who have issues with color sensitivity.

#### Suggested Tool

[Contrast Ratio](leaverou.github.io/contrast-ratio/)

[&uarr; Back to Table of Contents](#table-of-contents)

## Invisible Content

There will be a number of times where content (such as text) is overly verbose for visual users while visually impaired users require the necessary content. In these cases, it is advised to utilize the following utility class:

```scss
.is-invisible {
  position: absolute !important;
  left: -10000px;
  top: auto;
  width: 1px;
  height: 1px;
  overflow: hidden;
}
```

More modern solution may include techniques like `clip-path`, but for now, utilize this classical solution.

Source: [WebAIM: Invisible Content](http://www.webaim.org/techniques/css/invisiblecontent)

[&uarr; Back to Table of Contents](#table-of-contents)
