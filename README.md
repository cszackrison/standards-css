# AllenComm CSS / Sass / Less Styleguide

## Table of Contents

1. [Terminology](#terminology)
    - [Rule Declaration](#rule-declaration)
    - [Selectors](#selectors)
    - [Properties](#properties)
1. [CSS](#css)
    - [Formatting](#formatting)
    - [Comments](#comments)
    - [ID Selectors](#id-selectors)
1. [Sass/Less](#sassless)
    - [Syntax](#syntax)
    - [Ordering](#ordering-of-property-declarations)
    - [Variables](#variables)
    - [Mixins](#mixins)
    - [Nested selectors](#nested-selectors)

## Terminology

### Rule declaration

A “rule declaration” is the name given to a selector (or a group of selectors) with an accompanying group of properties. Here's an example:

```css
.listing {
    font-size: 18px;
    line-height: 1.2;
}
```

### Selectors

In a rule declaration, “selectors” are the bits that determine which elements in the DOM tree will be styled by the defined properties. Selectors can match HTML elements, as well as an element's class, ID, or any of its attributes. Here are some examples of selectors:

```css
.my-element-class {
    /* ... */
}

[aria-hidden] {
    /* ... */
}
```

### Properties

Finally, properties are what give the selected elements of a rule declaration their style. Properties are key-value pairs, and a rule declaration can contain one or more property declarations. Property declarations look like this:

```css
/* some selector */ {
    background: #f1f1f1;
    color: #333;
}
```

**[⬆ back to top](#table-of-contents)**

## CSS

### Formatting

* Use tabs or 4 spaces for indentation.
* Prefer dashes over camelCasing in class names.
* Do not use ID selectors unless absolutely necessary.
* When using multiple selectors in a rule declaration, give each selector its own line.
* Put a space before the opening brace `{` in rule declarations.
* In properties, put a space after, but not before, the `:` character.
* Put closing braces `}` of rule declarations on a new line.
* Put blank lines between rule declarations.

**Bad**

```css
.avatar{
    border-radius:50%;
    border:2px solid white; }
.no, .nope, .not_good {
    // ...
}
#lol-no {
    // ...
}
```

**Good**

```css
.avatar {
    border-radius: 50%;
    border: 2px solid white;
}

.one,
.selector,
.per-line {
    // ...
}
```

### Comments

* Prefer line comments (`//` in Sass-land) to block comments.
* Prefer comments on their own line. Avoid end-of-line comments.
* Write detailed comments for code that isn't self-documenting:
  - Uses of z-index
  - Compatibility or browser-specific hacks

### ID selectors

While it is possible to select elements by ID in CSS, it should generally be considered an anti-pattern. ID selectors introduce an unnecessarily high level of [specificity](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity) to your rule declarations, and they are not reusable.

**[⬆ back to top](#table-of-contents)**

## Sass/Less

### Syntax

* Order your regular CSS declarations alphabetically as much as you can

### Ordering of property declarations

1. Property declarations

    List all standard property declarations, anything that isn't a nested selector.

    ```scss
    .btn-green {
        background: green;
        font-weight: bold;
        // ...
    }
    ```

2. Nested selectors

    Nested selectors, _if necessary_, go last, and nothing goes after them. Add whitespace between your rule declarations and nested selectors, as well as between adjacent nested selectors. Apply the same guidelines as above to your nested selectors.

    ```scss
    .btn {
        background: green;
        font-weight: bold;

        .icon {
            margin-right: 10px;
        }
    }
    ```

### Variables

Prefer dash-cased variable names (e.g. `$my-variable`, `@my-variable`) over camelCased or snake_cased variable names. 

### Mixins

Mixins should be used to DRY up your code, add clarity, or abstract complexity--in much the same way as well-named functions. 

### Nested selectors

Try not to use selectors more than three levels deep.

```scss
.page-container {
    .content {
        .profile {
            // STOP!
        }
    }
}
```

When selectors become this long, you're likely writing CSS that is:

* Strongly coupled to the HTML (fragile) *—OR—*
* Overly specific (powerful) *—OR—*
* Not reusable


Again: **never nest ID selectors!**

If you must use an ID selector in the first place (and you should really try not to), they should never be nested. If you find yourself doing this, you need to revisit your markup, or figure out why such strong specificity is needed. If you are writing well formed HTML and CSS, you should **never** need to do this.

**[⬆ back to top](#table-of-contents)**
