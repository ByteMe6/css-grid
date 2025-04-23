# Chapter 3: Grid Container & Basic Track Definition

Welcome back! In [Chapter 2: Common Visual Styling](02_common_visual_styling_.md), we gave our HTML elements some basic styles so we can see them clearly. Now, it's time for the real magic: turning our plain container into an actual grid!

## Why Do We Need a Grid Container?

Imagine you have a bunch of square sticky notes you want to arrange neatly on a whiteboard. You could just stick them randomly, but that would be messy. To make it organized, you'd probably draw faint horizontal and vertical lines on the whiteboard first, creating a grid structure. Then, you can place your sticky notes perfectly within the grid cells.

CSS Grid works the same way!
1.  First, we need to tell the browser which HTML element is our "whiteboard" – this is called the **Grid Container**.
2.  Then, we need to "draw" the horizontal and vertical lines – these define the **Grid Tracks** (columns and rows).

This chapter shows you how to do these two fundamental steps using CSS.

## Step 1: Creating the Grid Container

The first step is to pick an HTML element (our "whiteboard") and tell the browser, "Hey, I want this element to manage its children using a grid layout!" We do this using the `display` property in CSS.

Let's use our first example from `index.html`:

```html
<!-- index.html -->
<div class="grid">
    <!-- Items inside -->
    <div class="grid_item">&#x2681;</div>
    <div class="grid_item">&#x2680;</div>
    <!-- ... more items ... -->
</div>
```

To make the `div` with the class `grid` behave like a grid container, we add this CSS rule:

```css
/* css/grid1.css (or any other grid CSS file) */

.grid {
  display: grid; /* Make this element a grid container! */

  /* We'll add column and row definitions here next */
}
```

**Explanation:**

*   `.grid`: This CSS selector targets our container `div`.
*   `display: grid;`: This is the magic instruction! It tells the browser to switch this element's layout mode from the default (usually stacking things vertically) to the powerful CSS Grid layout system. The direct children of this `div` (our `.grid_item` elements) are now considered **Grid Items** and can be placed onto the grid we're about to define.

Just adding `display: grid;` doesn't visually change much yet. We've designated the whiteboard, but we haven't drawn any lines on it.

## Step 2: Defining Grid Tracks (Columns and Rows)

Now that we have a grid container, we need to define the structure – the columns and rows. Think of these as the slots or spaces created by the lines you draw on the whiteboard. In CSS Grid, the spaces between grid lines are called **Tracks**.

### Defining Columns: `grid-template-columns`

This property defines the vertical tracks (columns) of our grid. You specify the width of each column you want.

Let's create a grid with three columns, each 100 pixels wide:

```css
/* css/grid1.css */

.grid {
  display: grid;

  /* Define three columns, each 100px wide */
  grid-template-columns: 100px 100px 100px;
}
```

**Explanation:**

*   `grid-template-columns`: This CSS property is used to define the columns.
*   `100px 100px 100px`: We provide a list of sizes, separated by spaces. Each size corresponds to one column. So, this creates:
    *   Column 1: 100 pixels wide
    *   Column 2: 100 pixels wide
    *   Column 3: 100 pixels wide

### Defining Rows: `grid-template-rows`

Similarly, this property defines the horizontal tracks (rows) of our grid. You specify the height of each row you want.

Let's add two rows, the first 50 pixels tall and the second 80 pixels tall:

```css
/* css/grid1.css */

.grid {
  display: grid;
  grid-template-columns: 100px 100px 100px;

  /* Define two rows, with heights 50px and 80px */
  grid-template-rows: 50px 80px;
}
```

**Explanation:**

*   `grid-template-rows`: This CSS property defines the rows.
*   `50px 80px`: We list the heights for each row:
    *   Row 1: 50 pixels tall
    *   Row 2: 80 pixels tall

**What Happens Now?**

With these rules (`display: grid`, `grid-template-columns`, `grid-template-rows`), we've created a basic 3-column, 2-row grid structure. The browser will automatically start placing the grid items (our `div.grid_item` elements) into the cells of this grid, starting from the top-left cell and moving across the rows.

Our example `div.grid` contains 7 items. With a 3x2 grid (which has 6 cells), the first 6 items will fill the grid, and the 7th item will automatically create a new row (we'll learn more about automatic rows/columns later).

You can see this basic setup being used in all the example files (`grid1.css` through `grid6.css`). They all start by setting `display: grid` and defining some columns and rows, often using different units and techniques which we'll explore soon!

For example, look at the beginning of `css/grid2.css`:

```css
/* css/grid2.css */
.grid2{
    display: grid; /* It's a grid container! */
    /* Defines 5 columns, each taking an equal fraction of available space */
    grid-template-columns: repeat(5, 1fr);
    /* Defines 3 rows, each 100px tall */
    grid-template-rows: repeat(3, 100px);

    /* ... other rules for item placement ... */
}
```

This example uses `repeat()` and `fr` units, which we'll cover in the [next chapter](04_flexible_and_automatic_track_sizing_.md), but the core idea is the same: define the container and its basic track structure.

## How It Works (Under the Hood)

Let's visualize the process when the browser encounters these CSS rules.

1.  **HTML Parsing:** The browser reads `index.html` and understands the structure: a `div.grid` containing several `div.grid_item` children.
2.  **CSS Parsing:** The browser reads the linked CSS files (like `css/usual.css` and `css/grid1.css`).
3.  **Applying `display: grid`:** When the browser sees `display: grid;` for `.grid`, it changes the internal layout model for that element. It now knows this element will arrange its children according to grid rules.
4.  **Creating the Grid Structure:** It then reads `grid-template-columns` and `grid-template-rows`. Based on these values (e.g., `100px 100px 100px` and `50px 80px`), it creates an internal grid blueprint with specific column widths and row heights. This is often called the **explicit grid**.
5.  **Placing Items:** The browser takes the child elements (`.grid_item`s) and starts placing them into the cells of the defined grid, one after another (by default).
6.  **Rendering:** Finally, the browser draws the grid container and the positioned items on the screen, using the styles from `usual.css` (borders, background colors) and the layout defined by our grid rules.

```mermaid
sequenceDiagram
    participant HTML as index.html
    participant CSS as grid1.css
    participant Browser as Browser Engine
    participant Layout as Visual Layout

    HTML->>Browser: Reads `<div class="grid">` and children.
    CSS->>Browser: Reads `.grid { display: grid; grid-template-columns: ...; grid-template-rows: ...; }`.
    Note over Browser: Recognizes `.grid` needs grid layout.
    Browser->>Browser: Creates internal 3-column, 2-row grid structure based on CSS template rules.
    Browser->>Layout: Places child items (`.grid_item`s) into the grid cells automatically.
    Layout->>Layout: Renders the grid container and items visually according to the structure and styles.
```

## Conclusion

You've learned the absolute foundation of CSS Grid!
1.  You make an element a **Grid Container** using `display: grid;`.
2.  You define the columns using `grid-template-columns` and specify their widths.
3.  You define the rows using `grid-template-rows` and specify their heights.

This creates the basic structure, the "tracks," for your layout. Think of it as preparing your pegboard or drawing the initial lines on your graph paper.

In the examples so far, we used fixed pixel values (`100px`, `50px`). But what if you want columns that stretch or shrink depending on the available space? That's where flexible sizing comes in!

Ready to make your grids more adaptable? Let's move on to [Chapter 4: Flexible and Automatic Track Sizing](04_flexible_and_automatic_track_sizing_.md).

---

Generated by [AI Codebase Knowledge Builder](https://github.com/The-Pocket/Tutorial-Codebase-Knowledge)