---
layout: slide-deck
title: "SVG icons"
desc: "A quick introduction to SVG icon and different ways to use them: separate files or embedded in the HTML."

slides:
  - type: super-big-text
    content: |
      **SVG icons**

  - content: |
      ## SVG symbols

      - Just like Illustrator there can be symbols in SVG
      - We can create a symbol library—a sprite sheet
      - And use the symbols many times in our website

      *Makes for a great icon sets*
    notes: |
      When previewing a symbol library in Finder it will appear empty. That’s because the it doesn’t contain any artwork on the artboard—the symbols haven’t been used yet.

  - content: |
      ## Using SVG for icons

      - Icons can be at the top of the HTML
        <br>*or*
      - Icons can be in a separate file

      *A separate file is usually better for performance & maintenance because it can be shared, edited and reused.*

  - type: interactive
    html: |
      <!-- At the top of the HTML -->
      <svg hidden>
        <symbol id="the-circle" viewBox="0 0 48 48">
          <circle cx="24" cy="24" r="22" fill="tomato" />
        </symbol>
        <symbol id="the-triangle" viewBox="0 0 48 48">
          <polygon points="24,2 46,46 2,46" fill="yellowgreen" />
        </symbol>
      </svg>

      <!-- Further down the HTML -->
      <i class="icon i-128">
        <svg><use xlink:href="#the-triangle"></use></svg>
      </i>

      <i class="icon i-128">
        <svg><use xlink:href="#the-circle"></use></svg>
      </i>

      <i class="icon i-24">
        <svg><use xlink:href="#the-triangle"></use></svg>
      </i>
    html_hidden: |
      <link href="modules.css" rel="stylesheet">
    html_lines:
      - num: 2
        text: |
          We can paste the sprite sheet into the top of our HTML—notice how there is nothing inside the sprite sheet except `<symbol>` objects.
      - num: 3
        text: |
          Each symbol must have two pieces of information:

          1. An `id`—this is how we call to the icon and display it
          2. A `viewBox`—each `<symbol>` requires a unique `viewBox`, but the surrounding `<svg>` tag does not
      - num: 13
        text: |
          We can then import an SVG symbol into another `<svg>` graphic with the `<use>` tag. The `xlink:href` points to the `id` of the `<symbol>` we want to display.

  - type: interactive
    html: |
      <!-- Icons in a separate sprite sheet -->
      <i class="icon i-96">
        <svg><use xlink:href="images/icons.svg#the-circle"></use></svg>
      </i>

      <i class="icon i-128">
        <svg><use xlink:href="images/icons.svg#the-triangle"></use></svg>
      </i>

      <i class="icon i-48">
        <svg><use xlink:href="images/icons.svg#the-circle"></use></svg>
      </i>
    html_hidden: |
      <link href="modules.css" rel="stylesheet">
    html_lines:
      - num: 3
        text: |
          We can also import symbols from external SVG symbol libraries by providing a path to the `.svg` file followed by the icons’s `id`

  - type: interactive
    html: |
      <!-- No `fill` attributes in the symbol -->
      <svg hidden>
        <symbol id="the-circle" viewBox="0 0 48 48">
          <circle cx="24" cy="24" r="22" />
        </symbol>
      </svg>

      <i class="icon i-128">
        <svg><use xlink:href="#the-circle"></use></svg>
      </i>
    html_lines:
      - num: 4
        text: |
          If we completely remove the fill from a symbol we can control its colour in the CSS.

          To remove the fill set it to absolute black in Illustrator, `#000000`, then when exported it’ll get automatically removed.
    css: |
      .icon {
        color: tomato;
        transition: all .25s linear;
      }
      .icon:hover {
        color: orange;
      }
    css_lines:
      - num: "2-3"
        text: |
          We can add the `color` attribute (assuming we’ve included `modules.css`) to adjust the `fill` of the SVG symbol. Without `modules.css` we’d have to specify `fill` directly.

          And, of course, transitions work perfectly well too.

          ---

          **Why color works instead of fill?**

          We can use `color` instead of `fill` when `modules.css` is included because it has a little snippet of code to allow it.

          ```
          svg {
            fill: currentColor;
          }
          ```

          This snipped of code changes the `fill` to be the value of the current `color`
    html_hidden: |
      <link href="modules.css" rel="stylesheet">

  - type: figure
    image: spritebot.jpg
    caption: "Use Spritebot to combine different SVG graphics into a sprite sheet"
    notes: |
      Spritebot isn’t the only tool to create sprite sheets—there are a few others online but I didn’t find their user experience pleasant.

      Spritebot even allows you to edit a sprite sheet by dropping it in again where you can add & remove symbols.

  - content: |
      ## Videos & tutorials

      - [Image formats · SVG ➔](/topics/image-formats/#svg)
      - [Advanced SVG ➔](/topics/advanced-svg/)
      - [SVG cheat sheet ➔](/topics/svg-cheat-sheet/)
---
