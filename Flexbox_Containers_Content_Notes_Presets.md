# Flexbox — Containers, Content, Notes & Presets

> A practical CSS Flexbox reference for students and frontend projects.

---

## 1. What is Flexbox?

**Flexbox (Flexible Box Layout)** is a CSS layout system used to arrange elements inside a container in a row or column.

Basic structure:

```html
<div class="container">
  <div class="item">Content 1</div>
  <div class="item">Content 2</div>
  <div class="item">Content 3</div>
</div>
```

```css
.container {
  display: flex;
}
```

The element with `display: flex` is the **flex container**.

Its direct children are called **flex items**.

---

# 2. Flexbox Terminology

```text
Flex Container
┌──────────────────────────────────────┐
│  Item 1   Item 2   Item 3            │
└──────────────────────────────────────┘
       ────────────────→
          Main Axis
```

### Important terms

| Term | Meaning |
|---|---|
| Flex container | Parent with `display: flex` |
| Flex item | Direct child of a flex container |
| Main axis | Primary direction of the layout |
| Cross axis | Direction perpendicular to the main axis |
| Main size | Size along the main axis |
| Cross size | Size along the cross axis |

---

# 3. Basic Flex Container

```css
.container {
  display: flex;
}
```

Default behavior:

```text
[Item 1] [Item 2] [Item 3]
```

Default direction is:

```css
flex-direction: row;
```

---

# 4. `flex-direction`

Controls the main axis.

## Row

```css
.container {
  display: flex;
  flex-direction: row;
}
```

```text
→ [1] [2] [3]
```

## Row Reverse

```css
.container {
  display: flex;
  flex-direction: row-reverse;
}
```

```text
[3] [2] [1] ←
```

## Column

```css
.container {
  display: flex;
  flex-direction: column;
}
```

```text
[1]
 ↓
[2]
 ↓
[3]
```

## Column Reverse

```css
.container {
  display: flex;
  flex-direction: column-reverse;
}
```

---

# 5. `justify-content`

Controls alignment along the **main axis**.

## Start

```css
.container {
  display: flex;
  justify-content: flex-start;
}
```

```text
[1] [2] [3]────────────
```

## Center

```css
.container {
  display: flex;
  justify-content: center;
}
```

```text
──────[1] [2] [3]──────
```

## End

```css
.container {
  display: flex;
  justify-content: flex-end;
}
```

```text
────────────[1] [2] [3]
```

## Space Between

```css
.container {
  display: flex;
  justify-content: space-between;
}
```

```text
[1]────────[2]────────[3]
```

## Space Around

```css
.container {
  display: flex;
  justify-content: space-around;
}
```

```text
──[1]────[2]────[3]──
```

## Space Evenly

```css
.container {
  display: flex;
  justify-content: space-evenly;
}
```

```text
──[1]──[2]──[3]──
```

---

# 6. `align-items`

Controls alignment along the **cross axis**.

## Center

One of the most useful Flexbox patterns:

```css
.container {
  display: flex;
  align-items: center;
}
```

For a row:

```text
┌──────────────────────────┐
│                          │
│      [1] [2] [3]         │
│                          │
└──────────────────────────┘
```

## Other values

```css
align-items: flex-start;
align-items: flex-end;
align-items: center;
align-items: stretch;
align-items: baseline;
```

---

# 7. Center Something Perfectly

Very common preset:

```css
.container {
  display: flex;
  justify-content: center;
  align-items: center;
}
```

This centers items horizontally and vertically when the main axis is a row.

Example:

```html
<div class="container">
  <div class="box">Centered</div>
</div>
```

```css
.container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
```

### Quick note

For a normal `row`:

- `justify-content` → horizontal
- `align-items` → vertical

For a `column`:

- `justify-content` → vertical
- `align-items` → horizontal

---

# 8. `flex-wrap`

Controls whether flex items move to another line.

## No Wrap

Default:

```css
.container {
  display: flex;
  flex-wrap: nowrap;
}
```

```text
[1] [2] [3] [4] [5] [6]
```

## Wrap

```css
.container {
  display: flex;
  flex-wrap: wrap;
}
```

```text
[1] [2] [3] [4]
[5] [6]
```

## Wrap Reverse

```css
.container {
  display: flex;
  flex-wrap: wrap-reverse;
}
```

---

# 9. `gap`

Creates spacing between flex items.

```css
.container {
  display: flex;
  gap: 20px;
}
```

You can also use:

```css
gap: 10px 20px;
```

Meaning:

```text
row-gap    column-gap
   ↓           ↓
  10px        20px
```

### Recommended

Prefer `gap` over manually adding margins when you simply need consistent spacing between flex items.

---

# 10. `row-gap` and `column-gap`

```css
.container {
  display: flex;
  flex-wrap: wrap;
  row-gap: 20px;
  column-gap: 30px;
}
```

---

# 11. `align-content`

Used mainly when there are **multiple flex lines** created by wrapping.

```css
.container {
  display: flex;
  flex-wrap: wrap;
  align-content: center;
}
```

Possible values:

```css
align-content: flex-start;
align-content: flex-end;
align-content: center;
align-content: space-between;
align-content: space-around;
align-content: space-evenly;
align-content: stretch;
```

### Important note

`align-content` is different from `align-items`.

- `align-items` → aligns items within a line
- `align-content` → aligns multiple lines

---

# 12. Flex Item: `flex-grow`

Controls how much an item can grow.

```css
.item {
  flex-grow: 1;
}
```

Example:

```css
.item1 {
  flex-grow: 1;
}

.item2 {
  flex-grow: 2;
}
```

The second item receives twice the available growth compared with the first.

---

# 13. `flex-shrink`

Controls how much an item can shrink when there is not enough space.

```css
.item {
  flex-shrink: 1;
}
```

Prevent shrinking:

```css
.item {
  flex-shrink: 0;
}
```

---

# 14. `flex-basis`

Sets the initial size of a flex item before remaining space is distributed.

```css
.item {
  flex-basis: 200px;
}
```

Think of it as the item's starting size along the main axis.

---

# 15. `flex` Shorthand

Instead of:

```css
.item {
  flex-grow: 1;
  flex-shrink: 1;
  flex-basis: 0;
}
```

You can write:

```css
.item {
  flex: 1;
}
```

Common:

```css
.item {
  flex: 1;
}
```

This is extremely useful for equal-width columns.

---

# 16. Equal Width Columns

```css
.container {
  display: flex;
  gap: 20px;
}

.item {
  flex: 1;
}
```

Result:

```text
┌──────────┬──────────┬──────────┐
│    1     │    2     │    3     │
└──────────┴──────────┴──────────┘
```

---

# 17. `align-self`

Overrides `align-items` for one particular item.

```css
.container {
  display: flex;
  align-items: center;
}

.item-special {
  align-self: flex-start;
}
```

Available values include:

```css
align-self: auto;
align-self: flex-start;
align-self: flex-end;
align-self: center;
align-self: stretch;
align-self: baseline;
```

---

# 18. `order`

Changes the visual order of flex items.

HTML:

```html
<div class="item one">A</div>
<div class="item two">B</div>
<div class="item three">C</div>
```

CSS:

```css
.one {
  order: 3;
}

.two {
  order: 1;
}

.three {
  order: 2;
}
```

Visual order:

```text
B → C → A
```

### Note

`order` changes visual layout, not the HTML/DOM order. For accessibility, don't use it unnecessarily.

---

# 19. Container vs Item Properties

## Flex Container Properties

Apply these to the parent:

```css
display
flex-direction
flex-wrap
flex-flow
justify-content
align-items
align-content
gap
row-gap
column-gap
```

## Flex Item Properties

Apply these to children:

```css
flex-grow
flex-shrink
flex-basis
flex
align-self
order
```

---

# 20. `flex-flow`

Shorthand for:

```css
flex-direction
flex-wrap
```

Instead of:

```css
.container {
  flex-direction: row;
  flex-wrap: wrap;
}
```

Use:

```css
.container {
  flex-flow: row wrap;
}
```

---

# 21. Responsive Card Layout Preset

```css
.cards {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
}

.card {
  flex: 1 1 250px;
}
```

Meaning:

```text
grow = 1
shrink = 1
basis = 250px
```

This is a very useful responsive Flexbox pattern.

---

# 22. Navbar Preset

```css
.navbar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 20px;
}
```

HTML:

```html
<nav class="navbar">
  <div class="logo">Logo</div>

  <div class="links">
    <a href="#">Home</a>
    <a href="#">About</a>
    <a href="#">Contact</a>
  </div>
</nav>
```

---

# 23. Vertical Stack Preset

```css
.stack {
  display: flex;
  flex-direction: column;
  gap: 16px;
}
```

Useful for:

- Forms
- Menus
- Cards
- Settings panels
- Mobile layouts

---

# 24. Perfect Center Preset

```css
.center {
  display: flex;
  justify-content: center;
  align-items: center;
}
```

For a full-screen section:

```css
.center {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
```

---

# 25. Button Group Preset

```css
.button-group {
  display: flex;
  gap: 12px;
  align-items: center;
  flex-wrap: wrap;
}
```

---

# 26. Sidebar + Main Content Preset

```css
.layout {
  display: flex;
  min-height: 100vh;
}

.sidebar {
  flex: 0 0 250px;
}

.main {
  flex: 1;
}
```

Responsive version:

```css
@media (max-width: 700px) {
  .layout {
    flex-direction: column;
  }

  .sidebar {
    flex-basis: auto;
  }
}
```

---

# 27. Common Dashboard Preset

```css
.dashboard {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
}

.dashboard-card {
  flex: 1 1 300px;
}
```

---

# 28. Card With Footer at Bottom

Useful when cards have different content lengths:

```css
.card {
  display: flex;
  flex-direction: column;
}

.card-footer {
  margin-top: auto;
}
```

Example:

```html
<article class="card">
  <h2>Title</h2>
  <p>Some content...</p>

  <div class="card-footer">
    <button>Learn More</button>
  </div>
</article>
```

---

# 29. Common Mistakes

## Mistake 1: Using `justify-content` on the child

Wrong:

```css
.item {
  justify-content: center;
}
```

Usually you want it on the flex container:

```css
.container {
  display: flex;
  justify-content: center;
}
```

---

## Mistake 2: Forgetting `display: flex`

This does nothing by itself:

```css
.container {
  justify-content: center;
}
```

Correct:

```css
.container {
  display: flex;
  justify-content: center;
}
```

---

## Mistake 3: Confusing `align-items` and `align-content`

Remember:

```text
align-items
→ alignment of items

align-content
→ alignment of multiple flex lines
```

---

# 30. Quick Cheat Sheet

| Goal | CSS |
|---|---|
| Enable Flexbox | `display: flex` |
| Horizontal layout | `flex-direction: row` |
| Vertical layout | `flex-direction: column` |
| Center main axis | `justify-content: center` |
| Center cross axis | `align-items: center` |
| Allow wrapping | `flex-wrap: wrap` |
| Space between items | `gap: 20px` |
| Equal items | `flex: 1` |
| Change item order | `order: 1` |
| Individual alignment | `align-self: center` |
| Initial item size | `flex-basis: 200px` |
| Allow growth | `flex-grow: 1` |
| Prevent shrinking | `flex-shrink: 0` |

---

# 31. Best Presets to Memorize

## Preset A — Perfect Center

```css
.container {
  display: flex;
  justify-content: center;
  align-items: center;
}
```

## Preset B — Horizontal With Gap

```css
.container {
  display: flex;
  align-items: center;
  gap: 20px;
}
```

## Preset C — Vertical Stack

```css
.container {
  display: flex;
  flex-direction: column;
  gap: 16px;
}
```

## Preset D — Responsive Cards

```css
.container {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
}

.card {
  flex: 1 1 250px;
}
```

## Preset E — Navbar

```css
.navbar {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
```

## Preset F — Sidebar Layout

```css
.layout {
  display: flex;
}

.sidebar {
  flex: 0 0 250px;
}

.content {
  flex: 1;
}
```

---

# 32. Flexbox Mental Model

When writing Flexbox, ask these questions in order:

### 1. Who is the container?

```css
.parent {
  display: flex;
}
```

### 2. What direction?

```css
flex-direction: row;
```

or

```css
flex-direction: column;
```

### 3. How should items be distributed?

```css
justify-content: ...
```

### 4. How should items align?

```css
align-items: ...
```

### 5. Do items need multiple lines?

```css
flex-wrap: wrap;
```

### 6. How much space should be between them?

```css
gap: 20px;
```

### 7. Does an individual item need special behavior?

```css
flex: ...
align-self: ...
order: ...
```

---

# 33. One-Line Memory Trick

For a normal row:

```text
justify-content → Main axis → Horizontal
align-items     → Cross axis → Vertical
```

For a column:

```text
justify-content → Main axis → Vertical
align-items     → Cross axis → Horizontal
```

---

# 34. Minimal Flexbox Example

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    .container {
      display: flex;
      justify-content: center;
      align-items: center;
      gap: 20px;
      min-height: 300px;
    }

    .item {
      padding: 30px;
      border: 2px solid;
    }
  </style>
</head>

<body>

  <div class="container">
    <div class="item">1</div>
    <div class="item">2</div>
    <div class="item">3</div>
  </div>

</body>
</html>
```

---

# 35. Final Revision

If you remember only these properties first, learn them in this order:

1. `display: flex`
2. `flex-direction`
3. `justify-content`
4. `align-items`
5. `gap`
6. `flex-wrap`
7. `flex`
8. `align-self`
9. `order`
10. `align-content`

> **Core idea:** Flexbox is about controlling the relationship between a container and its direct child items. Start with the container properties, then control individual items when needed.
