# Chapter 2: Project File Structure

In [Chapter 1: CSS Grid Layout Examples](01_css_grid_layout_examples_.md), we learned that the `CSSgrid-master` project is full of handy HTML files, each showing a specific webpage layout built with CSS Grid. Think of them as ready-made blueprints you can look at.

But wait, where exactly *are* these blueprint files? If you downloaded or cloned the project, you probably got a folder filled with different files and maybe even subfolders. How do you find your way around? That's what this chapter is all about!

## Why Does File Structure Matter?

Imagine you just bought a big box of LEGO® bricks, but instead of being sorted into bags, they were all dumped together randomly. Finding the specific pieces you need would be a mess!

A project's file structure is like a well-organized LEGO® box or a filing cabinet. It helps us:

1.  **Find Things Easily:** Know exactly where to look for the example HTML files.
2.  **Understand Relationships:** See how different parts of the project (like HTML examples and shared CSS styles) connect.
3.  **Keep Things Tidy:** A good structure prevents chaos as a project grows.

Our main goal right now is simple: **find and open the example HTML files** we talked about in Chapter 1. Understanding the project structure makes this super easy.

## Our Project's Filing Cabinet

Think of the main `CSSgrid-master` folder you downloaded as a **filing cabinet**.

```mermaid
graph TD
    A[📁 CSSgrid-master (The Filing Cabinet)] --> B(📄 example-1.html);
    A --> C(📄 cool-layout.html);
    A --> D(📄 ... other HTML files);
    A --> E[📁 css/ (A Separate Drawer)];
    E --> F(📄 shared-styles.css);
    A --> G(📄 README.md);

    style A fill:#f9f,stroke:#333,stroke-width:2px
    style E fill:#ccf,stroke:#333,stroke-width:2px
```

Let's break down what's inside:

1.  **The Main Cabinet (Root Folder):** This is the main `CSSgrid-master` folder itself. Inside, you'll find several files directly.
2.  **Individual Folders (HTML Files):** Right inside the main cabinet, you'll see various files ending with `.html`. Each of these `.html` files is one complete **[CSS Grid Layout Example](01_css_grid_layout_examples_.md)**. Think of each one as a separate folder in the filing cabinet, holding the blueprint and the finished model for one specific layout.
    *   `example-layout-1.html`
    *   `simple-two-column.html`
    *   `holy-grail-layout.html`
    *   *(and many others...)*
3.  **A Separate Drawer (`./css/` folder):** You might also see a folder named `css`. Think of this as a special drawer in our filing cabinet. This drawer holds common tools – specifically, CSS style files (`.css`) – that *some* of the HTML examples might use. Not every example needs things from this drawer; some examples are completely self-contained. But if an example needs some standard styles (like basic colors or fonts) that are used across *multiple* examples, it might link to a file inside this `css` folder.
4.  **Instruction Manual (`README.md`):** You'll also find a `README.md` file. This is like the instruction manual that came with the filing cabinet, giving you a quick overview of the project (like the one you might have already read!).

## How to Find and Use the Examples

Finding the examples is now straightforward:

1.  **Open the Project Folder:** Navigate to the main `CSSgrid-master` folder you downloaded or cloned.
2.  **Look for `.html` Files:** Inside this main folder, look for files ending in `.html`. These are your examples!
3.  **Open an Example:**
    *   **To See the Layout:** Double-click any `.html` file (e.g., `simple-two-column.html`). It will open in your web browser, showing you the visual result.
    *   **To See the Code:** Open the *same* `.html` file using a text editor (like Notepad, TextEdit, VS Code, Sublime Text, etc.). Now you can see the HTML structure and the CSS Grid rules that create the layout.

**What about the `css/` folder?**

For now, you mostly just need to know it exists. When you look at the code inside an `.html` file (using a text editor), you might see a line near the top, inside the `<head>` section, that looks something like this:

```html
<link rel="stylesheet" href="css/shared-styles.css">
```

This line tells the browser: "Hey, besides the styles written directly in this HTML file, also go look inside the `css` folder and use the styles defined in the `shared-styles.css` file."

If you *don't* see a line like that linking to a file in the `css` folder, it means that specific HTML example contains all the CSS it needs right inside itself (probably within `<style>` tags).

## Under the Hood: It's Just Organization!

There's no magic happening here! The file structure is simply about organizing files logically on your computer's disk. When you open an HTML file in your browser:

1.  The browser reads the HTML file top to bottom.
2.  It figures out the content (the "LEGO bricks" like `<header>`, `<div>`, etc.).
3.  It looks for CSS rules:
    *   It finds rules written directly inside `<style>` tags within the HTML file.
    *   If it sees a `<link rel="stylesheet" href="...">` tag pointing to a file (like one in the `css/` folder), it fetches and reads the rules from that file too.
4.  It uses all these CSS rules (especially the `display: grid;` and related grid properties) to arrange the HTML content on the screen according to the blueprint.

The folder structure simply helps the browser (and you!) find linked files like `css/shared-styles.css` easily because the `href="css/shared-styles.css"` path tells it exactly where to look relative to the HTML file.

## Conclusion

You've now learned how the `CSSgrid-master` project organizes its files! It's like a simple filing cabinet:

*   The main folder holds everything.
*   Individual `.html` files are the self-contained examples (blueprints + models).
*   The `css/` folder is an optional drawer holding shared styles used by some examples.

Knowing this structure makes it easy to navigate the project and find the specific **[CSS Grid Layout Examples](01_css_grid_layout_examples_.md)** you want to explore. Now that you know *where* to find the examples, you're ready to start opening them up, viewing the layouts, and looking at the code to see how CSS Grid works!

---

Generated by [AI Codebase Knowledge Builder](https://github.com/The-Pocket/Tutorial-Codebase-Knowledge)