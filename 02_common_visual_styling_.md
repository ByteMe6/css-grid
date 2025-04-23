# Chapter 2: Common Visual Styling

Welcome to Chapter 2! In [Chapter 1: HTML Structure for Examples](01_html_structure_for_examples_.md), we learned about the basic building blocks – the HTML container (our bookshelf) and the items (our books) inside it. Now, before we start arranging those items using CSS Grid, let's give them some basic visual style!

## Why Add Styles Now?

Imagine you're setting up a display of different bookshelf arrangements. It helps if all the bookshelves have the same color frame and all the books have colorful covers so you can easily see them. Without any style, our HTML elements would just be plain text stacked on top of each other – very hard to see the structure!

This chapter covers the common CSS rules used in the `CSSgrid-master` project to make all the examples look consistent and clear. Think of it as applying a standard coat of paint and border style to all our "bookshelves" and "books" so we can easily tell them apart and see how they are arranged later. These styles are defined in the `css/usual.css` file, which is linked in our `index.html`.

## Key Styling Concepts

We'll apply styles to two main things:

1.  **The Grid Containers:** The parent `div` elements (like `<div class="grid">`, `<div class="grid2">`, etc.). We'll give them borders so we can clearly see their boundaries.
2.  **The Grid Items:** The child `div` elements (like `<div class="grid_item">`, `<div class="grid_item2">`, etc.). We'll give them background colors, center their content, and set font styles to make them stand out.

Let's look at how this is done in `css/usual.css`.

### 1. Styling the Grid Containers (The Bookshelves)

To easily see where each grid layout example begins and ends, we add a border around the container `div`s.

**The CSS Code:**

```css
/* css/usual.css */

/* Select all grid container divs */
.grid, .grid2, .grid3, .grid4, .grid5, .grid6, .grid7, .grid8, .grid9, .grid10 {
    /* Add a solid border, 4 pixels thick */
    border: 4px solid;
    /* Round the corners slightly */
    border-radius: 20px;
}
```

**Explanation:**

*   `.grid, .grid2, ... , .grid10`: This is a CSS selector. It tells the browser, "Find any element that has the class `grid`, OR the class `grid2`, OR `grid3`, and so on." This way, we apply the same style to *all* our example containers.
*   `border: 4px solid;`: This rule draws a line around the element. It's `4px` (pixels) thick and `solid` (not dashed or dotted). The color will default to the text color (usually black, but we'll see how grid properties might affect this later).
*   `border-radius: 20px;`: This softens the corners, making them rounded instead of sharp squares.

**Result:** Each example area in `index.html` will have a clearly visible, rounded border around it.

### 2. Styling the Grid Items (The Books)

Now let's make the items inside the containers visible and neat.

**The CSS Code (Part 1 - General Item Styles):**

```css
/* css/usual.css */

/* Select all grid item divs */
.grid_item, .grid_item2, .grid_item3, .grid_item4, .grid_item5, .grid_item6, .grid_item7, .grid_item8, .grid_item9, .grid_item10 {
    /* These 3 lines center the text/content inside the item box */
    display: flex;
    justify-content: center;
    align-items: center;

    /* Style the text */
    color: #fff; /* White text color */
    font-family: sans-serif; /* Use a common, simple font */
    font-size: 48px; /* Make the text large */
}
```

**Explanation:**

*   `.grid_item, .grid_item2, ...`: Similar to the container selector, this selects *all* the item `div`s across all examples.
*   `display: flex; justify-content: center; align-items: center;`: These three rules work together using a different CSS layout system called Flexbox (often used *inside* grid items). Don't worry too much about Flexbox now; just know that these lines make the content (like the dice faces 🎲 or numbers 1️⃣) perfectly centered within each item's box, both horizontally and vertically.
*   `color: #fff;`: Sets the text color to white (`#fff` is the code for white).
*   `font-family: sans-serif;`: Chooses a simple, clean font style available on most computers.
*   `font-size: 48px;`: Makes the text or symbols inside the items quite large and easy to read.

**The CSS Code (Part 2 - Item Background Colors):**

To make the items visually distinct, we'll give them different background colors in a repeating pattern.

```css
/* css/usual.css */

/* Style the 1st, 4th, 7th, etc. item in EACH grid */
.grid_item:nth-child(3n + 1), /* ...and others... */ {
    background-color: #96ceb4; /* Light greenish color */
}

/* Style the 2nd, 5th, 8th, etc. item in EACH grid */
.grid_item:nth-child(3n + 2), /* ...and others... */ {
    background-color: rgba(165, 113, 217, 0.933); /* Purplish color */
}

/* Style the 3rd, 6th, 9th, etc. item in EACH grid */
.grid_item:nth-child(3n), /* ...and others... */ {
    background-color: #d0cd41; /* Yellowish color */
}
/* Note: The full selectors like .grid_item2:nth-child(3n+1) etc. are shortened here for clarity */
/* The actual file includes them all */
```

**Explanation:**

*   `:nth-child(...)`: This is a special CSS "pseudo-class" that lets us select items based on their position among their siblings (other items within the *same* container).
*   `3n + 1`: Selects the 1st child (3\*0 + 1), 4th child (3\*1 + 1), 7th child (3\*2 + 1), and so on. These get a light green background.
*   `3n + 2`: Selects the 2nd child (3\*0 + 2), 5th child (3\*1 + 2), 8th child (3\*2 + 2), etc. These get a purplish background.
*   `3n`: Selects the 3rd child (3\*1), 6th child (3\*2), 9th child (3\*3), etc. These get a yellowish background.
*   `background-color: ...;`: This rule sets the background color of the selected items.

**Result:** The items within each grid container will have a repeating pattern of three background colors (green, purple, yellow), making it easier to distinguish individual items.

## How It Works (Under the Hood)

How does the browser know to apply these styles from `usual.css` to the elements in `index.html`?

1.  **Linking:** Inside the `<head>` section of `index.html`, there's a line:
    ```html
    <link rel="stylesheet" href="./css/usual.css">
    ```
    This tells the browser to load and read the `usual.css` file.

2.  **Matching:** The browser reads the HTML structure (from Chapter 1) and builds an internal representation of the page. Then, it reads the CSS rules from `usual.css`. It goes through each rule and looks for HTML elements that match the selectors (e.g., it finds all elements with `class="grid"` and applies the border rules to them; it finds all elements with `class="grid_item"` and applies the centering and text styling rules, etc.).

3.  **Applying Styles:** The browser "paints" the elements according to the matched CSS rules *before* applying any specific grid layout rules (which we'll learn about next).

Here’s a simplified view:

```mermaid
sequenceDiagram
    participant HTML as index.html
    participant CSS as usual.css
    participant B as Browser
    participant Screen as Visual Output

    HTML->>B: Browser reads HTML, finds `<div class="grid">` and `<div class="grid_item">` etc.
    HTML->>B: Browser sees `<link rel="stylesheet" href="css/usual.css">`.
    B->>CSS: Browser requests and reads `usual.css`.
    CSS->>B: Provides style rules (e.g., `.grid { border: ...; }`, `.grid_item { background-color: ...; }`).
    Note over B: Browser matches CSS rules to HTML elements based on classes.
    B->>Screen: Browser applies the visual styles (borders, colors, text centering) to the elements.
    Note over Screen: Elements are now visible and styled, but likely just stacked vertically for now.
```

This common styling provides a consistent visual baseline for all our examples.

## Conclusion

You've now learned how the `usual.css` file provides a consistent look and feel for all the grid examples in the `CSSgrid-master` project. We added borders to containers and styled the items with colors, centered text, and specific fonts. This makes our "bookshelves" and "books" clearly visible and distinct.

With our HTML structure in place and basic styling applied, we're finally ready to start using the power of CSS Grid! In the next chapter, we'll learn how to turn our containers into actual grid layouts and define the basic structure of rows and columns.

Let's dive into making grids! Proceed to [Chapter 3: Grid Container & Basic Track Definition](03_grid_container___basic_track_definition_.md).

---

Generated by [AI Codebase Knowledge Builder](https://github.com/The-Pocket/Tutorial-Codebase-Knowledge)