# Rendering Logic

## Built-in Declarations and Inheritance

Built-in styles for "a" tags, in Chrome 86. These styles are part of the **user-agent stylesheet**. Each browser includes their own stylesheet full of base styles like this.
```css
a {
  color: -webkit-link;
  cursor: pointer;
  text-decoration: underline;
}
```

> [!IMPORTANT]  
> It was common to use a CSS reset? to strip away many of these default user-agent styles.

## Common Global Styles

```css
/*
  1. Use a more-intuitive box-sizing model.
*/
*, *::before, *::after {
  box-sizing: border-box;
}

/*
  2. Remove default margin
*/
* {
  margin: 0;
}

/*
  3. Allow percentage-based heights in the application
*/
html, body {
  height: 100%;
}

/*
  Typographic tweaks!
  4. Add accessible line-height
  5. Improve text rendering
*/
body {
  line-height: 1.5;
  -webkit-font-smoothing: antialiased;
}

/*
  6. Improve media defaults
*/
img, picture, video, canvas, svg {
  display: block;
  max-width: 100%;
}

/*
  7. Remove built-in form typography styles
*/
input, button, textarea, select {
  font: inherit;
}

/*
  8. Avoid text overflows
*/
p, h1, h2, h3, h4, h5, h6 {
  overflow-wrap: break-word;
}

/*
  9. Create a root stacking context
*/
#root, #__next {
  isolation: isolate;
}

```

### Inheritance

```html
<style>
  p {
    color: deeppink;
  }
</style>

<p>
  I know <em>you</em> are, but what am I?
</p>
```

> [!NOTE]  
> Certain CSS properties inherit. When I apply a color to an element, that value gets passed down to all children and grand-children. In the above example pink color got applied to "em" tag, though we applied pink color to "p" tag.

```css
<style>
  p {
    border: 1px solid hotpink;
  }
</style>

<p>
  I know <em>you</em> are, but what am I?
</p>
```
> [!IMPORTANT]  
> The border value doesn't get passed down to the "em" in the above example. We still only have 1 border, and it's around the entire paragraph. If we explicitly add the same border value to both paragraphs and emphasis tags, we can see a second border within our paragraph.

> [!TIP]
> Most of the properties that inherit are typography-related, like color, font-size, text-shadow, and so on.

**List of CSS Properties that are Inherited**

* border-collapse
* border-spacing
* caption-side
* color
* cursor
* direction
* empty-cells
* font-family
* font-size
* font-style
* font-variant
* font-weight
* font-size-adjust
* font-stretch
* font
* letter-spacing
* line-height
* list-style-image
* list-style-position
* list-style-type
* list-style
* orphans
* quotes
* tab-size
* text-align
* text-align-last
* text-decoration-color
* text-indent
* text-justify
* text-shadow
* text-transform
* visibility
* white-space
* widows
* word-break
* word-spacing
* word-wrap

**Forcing inheritance**
```html
<p>
  This paragraph contains <a href="#">a hyperlink</a>!
</p>
```
The trouble is that even though color is an inheritable property, it's being overwritten by the default style, color: -webkit-link?. We can fix this by explicitly telling anchor tags to inherit their containing text color:

```css
<style>
  a {
    color: inherit;
  }
</style>

<p>
  This paragraph contains <a href="#">a hyperlink</a>!
</p>
<p style="color: red;">
  This is a red paragraph with <a href="#">another link</a>.
</p>
```




## The Cascade

## BLock and Inline Directions

## The Box Model
### Padding
### Border
### Margin

## Flow Layout
### Width Algorithms
### Height Algorithms

## Margin Collapse
### Rules of Margin Collapse
### Will it Collapse?
### Using Margin Effectively?

## Example: Agency Page