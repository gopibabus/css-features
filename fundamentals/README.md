# Fundamentals

## Anatomy of a Style Rule

Q. In the following css snippet, what is the **property** ?
```css

p {
    margin: 32px;
}
```

Ans:
```css
margin
```

Q. In the following css snippet, what is the **selector** ?
```css
.apple {
  background-color: red;
  border-radius: 50%;
}
```

Ans:
```css
.apple
```


Q. In the following css snippet, what is the **first declaration** ?
```css
.code-snippet {
  padding: 32px;
  white-space: pre-wrap;
}
```

Ans:
```css
padding: 32px;
```

Q. In the following css snippet, what is the **rule** ?
```css
p {
  color: red;
  font-family: sans-serif;
}
```

Ans:
```css
p {
  color: red;
  font-family: sans-serif;
}
```


Q. In the following css snippet, what is the **unit** ?
```css
p {
  padding-top: 24px;
}
```

Ans:
```css
px
```

Q. In the following css snippet, what is the **second declaration** ?
```css
main {
  max-width: 65ch;
  margin: 0 auto;
}
```

Ans:
```css
margin: 0 auto;
```


Q. In the following css snippet, what is the **first rule** ?
```css
p {
  font-size: 1rem;
}

.big-paragraph {
  font-size: 1.25rem;
  font-weight: 500;
}
```

Ans:
```css
p {
  font-size: 1rem;
}
```

## Media Queries

**Syntax**
```css
@media (condition) {
  /* Some CSS that'll run if the condition is met. */
}
```

**Example: 1**
```html
<style>
  @media (max-width: 300px) {
    .small-only {
      color: red;
    }
  }
</style>

<div class="small-only">
  Hello there!
</div>
```

> [!NOTE]
> If the window is between 0px and 300px wide, the CSS within will be applied.


**Example: 2**
```html
<style>
  .large-screens {
    display: none;
  }

  @media (min-width: 300px) {
    .large-screens {
      display: block;
    }
    .small-screens {
      display: none;
    }
  }
</style>

<div class="large-screens">
  I only show up on large screens.
</div>
<div class="small-screens">
  Meanwhile, you'll only see me on small ones.
</div>
```

> [!NOTE]
> If our window is at least 300px wide, however, we apply special overrides. This includes showing large-screens elements, and hiding small-screens elements.

> [!NOTE]
> This trick is often used for navigation. Desktop users see a list of links, whereas mobile users see a hamburger icon.

> [!IMPORTANT]  
> Inside the parentheses, we typically use either max-width to add styles on small screens, or min-width to add styles on larger ones.

## Selectors
### Pseudo-classes
### Pseudo-elements
### Combinators
### Examples

## Color

## Units

## Typography

## Debugging in the Browser