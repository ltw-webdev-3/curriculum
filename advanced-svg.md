---
layout: slide-deck

title: "Advanced SVG"

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

  - type: interactive
    svg: |
      <svg width="256" height="256" viewBox="0 0 256 256" xmlns="http://www.w3.org/2000/svg">
        <circle cx="120" cy="120" r="50" />
        <rect x="0" y="0" width="75" height="75" />
        <ellipse cx="200" cy="200" rx="50" ry="30" />
      </svg>

  - content: |
      ## SVGs use CSS!

      Most of the visual look of SVGs comes from CSS

      *Just the properties are a little different*

  - type: interactive
    svg: |
      <svg width="256" height="256" viewBox="0 0 256 256" xmlns="http://www.w3.org/2000/svg">
        <circle cx="120" cy="120" r="50" />
        <rect x="0" y="0" width="75" height="75" />
        <ellipse cx="200" cy="200" rx="50" ry="30" />
      </svg>
    css_lines: "2,6-7"
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

  - content: |
      ## SVG interactivity

      Embedded SVGs can have effects:

      - `:hover`
      - `transition`
      - `animation`
      - `transform`

  - type: interactive
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
---
