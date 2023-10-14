# [Easy and more consistent layouts using subgrid](https://youtu.be/IIQa9f0REtM)


### CSS Grid and Subgrid Introduction

CSS Grid Layout provides a two-dimensional grid-based layout system for web pages, allowing you to define columns and rows for your web content. The introduction of **subgrid** in the CSS Grid specification allows nested grids (child elements) to inherit the grid definition from their parent grid container. 

### Basic Grid Usage

Let's establish the basics of using a grid layout:

```css
.container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 20px;
}
```
```html
<div class="container">
  <div>Item 1</div>
  <div>Item 2</div>
  <div>Item 3</div>
  <!-- More Items -->
</div>
```
Here, `.container` is a grid with three equal-width columns. `grid-gap: 20px;` defines the space between grid items.

### Subgrid Usage

The subgrid feature allows a nested grid to use the grid tracks defined by its parent grid container. This ensures that the nested grid’s items align with the parent grid’s lines.

Here's an example of how subgrid might be used:

```css
.container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 20px;
}

.item {
  display: grid;
  grid-template-columns: subgrid;
  grid-gap: 5px;
}
```
```html
<div class="container">
  <div class="item">
    <div>Subitem 1</div>
    <div>Subitem 2</div>
    <div>Subitem 3</div>
  </div>
  <!-- More Items -->
</div>
```
In the example above, `.item` will have its columns aligned with `.container`’s columns, thanks to `grid-template-columns: subgrid;`. This enables a more consistent and aligned design when dealing with nested grids.

### Additional Subgrid Usage Note

Subgrid can also be used with rows, or both columns and rows, depending on the desired alignment and design:

- `grid-template-columns: subgrid;` aligns columns with the parent.
- `grid-template-rows: subgrid;` aligns rows with the parent.
- Using both will align both rows and columns with the parent.

### Practical Use Case: Card Layout

Imagine a set of cards with a title, image, and button, and we want the button to be aligned at the bottom of each card, regardless of content size:

```css
.card-container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 20px;
}

.card {
  display: grid;
  grid-template-rows: auto 1fr auto;
}

.button {
  grid-row: 3;
}
```
```html
<div class="card-container">
  <div class="card">
    <h2>Title</h2>
    <img src="image.jpg" alt="Image"/>
    <button class="button">Click me</button>
  </div>
  <!-- More Cards -->
</div>
```
This CSS and HTML structure allows card content to take up as much space as it needs, while ensuring that buttons are consistently placed at the bottom of each card.

### Considerations

- Browser compatibility: At the time of the last training data in January 2022, subgrid was not universally supported across all major browsers. Always check for the most recent compatibility updates [here](https://caniuse.com/css-subgrid).
  
- Subgrid works well for designs requiring alignment between parent and child grids, but be mindful of content sizes and ensure that your design is flexible and accessible.

- It's worthwhile to use fallbacks or alternative layouts for browsers that do not support subgrid to ensure that your website is usable and looks good across all platforms and browsers.

