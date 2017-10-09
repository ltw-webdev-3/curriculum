---
layout: slide-deck
title: "Advanced SVG"
desc: "An introduction to writing SVG code by hand and integrating it with CSS effects like animations & transitions."

slides:
  - type: super-big-text
    content: |
      **Advanced SVG**

  - content: |
      ## SVGs are just code

      We can open them directly in our code editor

      *They’re completely hackable!*

  - content: |
      ## Writing SVG

      SVGs look very similar to HTML—but they are XML

      - `<svg>` — everything goes inside
      - `<circle>`
      - `<rect>`
      - `<ellipse>`
      - etc.
    notes: |
      SVG isn’t nearly as forgiving as HTML because XML, what SVG is built on, is extremely strict.

      - Unclosed tags will stop the whole image from working
      - Self-closing tags must have a `/` at the end

  - type: interactive
    svg: |
      <svg width="256" height="256" viewBox="0 0 256 256" xmlns="http://www.w3.org/2000/svg">
        <circle cx="120" cy="120" r="50" />
        <rect x="0" y="0" width="75" height="75" />
        <ellipse cx="200" cy="200" rx="50" ry="30" />
      </svg>
    svg_lines:
      - num: 1
        text: |
          The `width`, `height` & `viewBox` are always necessary. The `xmlns` attribute is required only when the SVG is in a separate file.
      - num: 2
        text: |
          The `<circle>` element will draw a circle to the screen. It needs a few different attributes:

          - `cx` — the centre “x” coordinate
          - `cy` — the centre “y” coordinate
          - `r` — the radius of the circle

          **Notice that this must have a closing slash (`/`) at the end inside the element. If we compare this to another self-closing tag: the `<img>` tag, the image doesn’t need the slash because its HTML, but the SVG elements does because its XML.

  - content: |
      ## SVGs use CSS!

      Most of the visual look of SVGs comes from CSS

      *Just the properties are a little different*

  - type: interactive
    notes: |
      You may notice that the CSS properties for SVG are named more similarly to what Illustrator calls things: like `fill` instead of `background-color`
    svg: |
      <svg width="256" height="256" viewBox="0 0 256 256" xmlns="http://www.w3.org/2000/svg">
        <circle cx="120" cy="120" r="50" />
        <rect x="0" y="0" width="75" height="75" />
        <ellipse cx="200" cy="200" rx="50" ry="30" />
      </svg>
    css_lines:
      - num: 2
        text: |
          The `fill` CSS property changes the shape’s colour.
      - num: '6-7'
        text: |
          We can add borders, called `stroke` in SVG using the `stroke-*` properties.
    css: |
      rect {
        fill: yellow;
      }
      ellipse {
        fill: limegreen;
        stroke: #000;
        stroke-width: 5px;
      }

  - content: |
      ## Styles on tags

      We can also write the styles directly on the tags—and when we export from Illustrator that’s what happens

      *The SVG style attributes can be overwritten by CSS*

  - type: interactive
    svg: |
      <svg width="256" height="256" viewBox="0 0 256 256" xmlns="http://www.w3.org/2000/svg">
        <circle fill="limegreen" cx="120" cy="120" r="50" />
      </svg>
    svg_lines:
      - num: 2
        text: |
          Notice the `fill` attribute on the `<circle>`: it’s the same as using the CSS `fill` property.
    css: |
      circle {
        fill: yellow;
      }
    css_lines:
      - num: 2
        text: |
          The `fill` attribute in the SVG can be overwritten by the `fill` CSS property.

  - content: |
      ## Why have an extra file?

      The SVG code can be embedded directly in your HTML

      *Just copy and paste all the SVG code*

  - type: interactive
    html: |
      <body>
        <svg width="256" height="256" viewBox="0 0 256 256">
          <circle cx="120" cy="120" r="50" />
        </svg>
      </body>
    html_lines:
      - num: 2
        text: |
          When embedding SVG inside an HTML document we can get rid of the `xmlns` attribute. Why write extra code when we don’t have to.

  - content: |
      ## SVG interactivity

      Embedded SVGs can have effects:

      - `:hover`
      - `transition`
      - `animation`
      - `transform`

  - type: interactive
    notes: |
      Since the SVG is embedded in our HTML we can apply effects to it in our CSS like `transition` and `:hover`
    html: |
      <svg id="black-hole" width="256" height="256" viewBox="0 0 256 256">
        <circle cx="120" cy="120" r="50" />
      </svg>
    css: |
      #black-hole {
        transition: all .5s linear;
      }
      #black-hole:hover {
        fill: lightsteelblue;
      }

  - content: |
      ## Videos & tutorials

      - [Image formats · SVG ➔](/topics/image-formats/#svg)
      - [Advanced SVG ➔](/topics/advanced-svg/)
      - [SVG cheat sheet ➔](/topics/svg-cheat-sheet/)

---
