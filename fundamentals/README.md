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

> [!TIP]
> This trick is often used for navigation. Desktop users see a list of links, whereas mobile users see a hamburger icon.

> [!IMPORTANT]  
> Inside the parentheses, we typically use either max-width to add styles on small screens, or min-width to add styles on larger ones.

### Pseudo-classes

**:hover**
```html
<style>
  button:hover {
    color: blue;
  }
</style>

<button>Hover over me!</button>
```

> [!NOTE]  
> Pseudo-classes let us apply a chunk of CSS based on an element's current state. In this case, we're adding a blue text color when the element is hovered.

**:focus**
```html
<style>
  button:focus {
    border: 2px solid royalblue;
    background: royalblue;
    color: white;
  }
</style>

<button>Hello</button>
<button>world</button>
<button>!</button>
```
> [!NOTE]  
> The :focus pseudo-class allows us to apply styles exclusively when an interactive element has focus.


> [!NOTE]  
> For most users, a button can be focused by clicking on it. Focus can then be moved between buttons by pressing “Tab” (to go forward) or “Shift” + “Tab” (to go backwards).


**:checked**

```html
<style>
  input:checked {
    width: 24px;
    height: 24px;
  }
</style>

<h1>Pizza Toppings</h1>
<br />
<label>
  <input type="checkbox" />
  Avocado
</label>
<br />
<label>
  <input type="checkbox" />
  Broccoli
</label>
<br />
<label>
  <input type="checkbox" />
  Carrots
</label>
```
> [!NOTE]  
> The :checked pseudo-class only applies to checkboxes and radio buttons that are "filled in". You can apply additional styles to indicate that the input is activated.


**:first/last child**
```html
<style>
  p {
    margin-bottom: 1em;
  }
  p:last-child {
    margin-bottom: 0px;
  }
</style>

<section>
  <p>This is a paragraph!</p>
  <p>This is another paragraph!</p>
  <p>
    What do you know, it's a third
    paragraph!
  </p>
</section>
```
> [!NOTE]  
> The :last-child pseudo-class will only select "p" tags which are the final element within its container. It needs to be the last child within its parent. Similarly, the :first-child pseudo-class will match the first child within a parent container.

### Pseudo-elements
> [!NOTE]  
> Pseudo-elements are like pseudo-classes, but they don't target a specific state. Instead, they target "sub-elements" within an element.

```html
<style>
  input {
    font-size: 1rem;
  }
  input::placeholder {
    color: goldenrod;
  }
</style>

<label>
  Postal Code:
  <input
    type="text"
    placeholder="A1A 1A1"
  />
</label>
```

> [!NOTE]  
> In terms of syntax, pseudo-elements use two colons instead of one (::), though some pseudo-elements also support single-colon syntax.

> [!NOTE]
> Pseudo-element selectors target elements in the DOM that we haven't explicitly created with HTML tags.

**before and after**
```html
<style>
  p::before {
    content: '→ ';
    color: deeppink;
  }
  
  p::after {
    content: ' ←';
    color: deeppink;
  }
</style>

<p>
  This paragraph has little arrows!
</p>
```
> [!NOTE]
> These pseudo-elements are added inside the element, right before and after the element's content.


### Combinators
```html
<style>
  nav a {
    color: red;
    font-weight: bold;
  }
</style>

<nav>
  <a href="">Home</a>
  -
  <a href="">Shop</a>
</nav>

<p>
  Hello world! You might be interested in reading <a href="">an article</a>!
</p>
```
> [!NOTE]
> By putting a space between nav and a, we're combining two selectors in a very specific way: we're saying that the styles should only apply to a tags that are nested within nav tags. The first two links in the snippet qualify, but the last one doesn't.

> [!NOTE]
> The term “combinator” refers to a character that combines multiple selectors. In this case, the space character combines nav and a to create a descendant selector.

**One more combinator(>)**
```html
<style>
  li {
    margin-bottom: 8px;
  }
  
  .main-list > li {
    border: 2px dotted;
  }
</style>

<ul class="main-list">
  <li>Salt</li>
  <li>Pepper</li>
  <li>
    Fruits & Veg:
    <ul>
      <li>Apple</li>
      <li>Banana</li>
      <li>Carrots</li>
    </ul>
  </li>
</ul>
```

## Color

```css
strong {
  color: red;
}
```

### Color Formats
```css
// hex codes
.colorful-thing {
  color: #FF0000;
  border-bottom: 3px solid hsl(100deg 75% 50%);
}


// HSL format
.colorful-thing {
  color: hsl(200deg 100% 50%);
  border-bottom: 3px solid hsl(100deg 75% 50%);
}
// HSL format with transparency
.fourth.box {
  background-color: hsl(340deg 100% 50% / 0.25);
}
```

### Background Color
```html
<style>
  em {
    background-color: hsl(50deg 100% 50%);
  }
</style>

<p>
  This is a paragraph with a
  <em>highlighted section</em>.
</p>
```

## Units

```css
# px unit
.box {
  width: 1000px;
  margin-top: 32px;
  padding: 8px;
}
```
> [!NOTE]  
> **Pixels** are nice because they correspond more-or-less with what you see on the screen*.

```html
<style>
  p {
    /* Change me! */
    font-size: 18px;
    
    padding-bottom: 2em;
    border: 1px solid;
  }
</style>

<p>
  This paragraph has a relative amount of bottom padding!
</p>
```
> [!NOTE]  
> **em** a relative unit, equal to the font size of the current element.

```html
<style>
  html {
    font-size: 16px;
  }
  h1 {
    font-size: 2rem;
    margin: 0;
  }
    h2 {
        font-size: 1.25rem;
        margin-bottom: 1.5rem;
        color: gray;
    }
    p {
    font-size: 1rem;
    }
</style>

<h1>What's a staple? The list expands.</h1>
<h2>Jan. 1, 1991</h2>
<p>Conventional agricultural wisdom holds that only a handful of crop species -- as few as 7 and no more than 30, depending on different assessments -- account for most of the plant food consumed by humanity. But a new study says more than 100 species and possibly as many as 200 are important food sources.</p>
```
> [!NOTE]  
> The **rem** unit is quite a lot like the em unit, with one crucial difference: it's always relative to the root element, the "html" tag.

> [!WARNING]  
> Please note, you shouldn't actually set a "px" font size on the html tag.


```html
<style>
  .box {
    width: 250px;
    height: 250px;
    background-color: pink;
  }

  .child {
    width: 50%;
    height: 75%;
    background-color: black;
  }
</style>

<div class="box">
  <div class="child"></div>
</div>
```
> [!NOTE]  
> The percentage unit is often used with width/height, as a way to consume a portion of the available space.

## Typography

### Font families
```css
* {
    font-family: Arial;
}
```

### Text Formatting
```css
* {
    font-weight: bold;
    font-weight: 300;
    font-style: italic;
}

nav a {
  text-decoration: none;
}
```

### Alignment
```html
<style>
    p.left {
  text-align: left;
    }
    p.right {
    text-align: right;
    }
    p.center {
    text-align: center;
    }

    p {
    margin-bottom: 32px;
    }
</style>

<p class="left">
  This paragraph uses the default “left” alignment.
</p>
<p class="right">
  This one, meanwhile, pops over to the other side! It flips the default behaviour.
</p>
<p class="center">
  Finally, we end in the middle.
</p>
```

### Text Transforms
```css
* {
    /* RENDER WITH ALL CAPS */
    text-transform: uppercase;

    /* Capitalize The First Letter Of Every Word */
    text-transform: capitalize;
}
```

### Spacing
```html
<style>
  /* Try tweaking these properties! */
  h3 {
    letter-spacing: 3px;
  }
  
  p {
    font-size: 1rem;
    line-height: 1.5;
  }
</style>

<h3>About Us</h3>
<p>
  The Lumen Group was founded in 1984 in Berlin, Germany. We create purposeful products for the next generation of leaders and executives, luminaries and visionaries of tomorrow.
</p>
```