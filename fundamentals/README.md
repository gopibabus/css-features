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

## Units

## Typography

## Debugging in the Browser