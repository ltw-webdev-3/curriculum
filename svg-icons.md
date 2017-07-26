---
layout: slide-deck

title: "SVG icons"

slides:
  - type: super-big-text
    content: |
      **SVG icons**

  - content: |
      ## Using SVG for icons

      *Also know as sprite sheets*

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
      <i class="icon i--128">
        <svg><use xlink:href="#the-triangle" /></svg>
      </i>

      <i class="icon i--128">
        <svg><use xlink:href="#the-circle" /></svg>
      </i>

      <i class="icon i--24">
        <svg><use xlink:href="#the-triangle" /></svg>
      </i>
    html_hidden: |
      <link href="modules.css" rel="stylesheet">

  - type: interactive
    html: |
      <!-- Icons in a separate sprite sheet -->
      <i class="icon i--96">
        <svg><use xlink:href="images/icons.svg#the-circle" /></svg>
      </i>

      <i class="icon i--128">
        <svg><use xlink:href="images/icons.svg#the-triangle" /></svg>
      </i>

      <i class="icon i--48">
        <svg><use xlink:href="images/icons.svg#the-circle" /></svg>
      </i>
    html_hidden: |
      <link href="modules.css" rel="stylesheet">

  - type: interactive
    html: |
      <!-- No `fill` attributes in the symbol -->
      <svg hidden>
        <symbol id="the-circle" viewBox="0 0 48 48">
          <circle cx="24" cy="24" r="22" />
        </symbol>
      </svg>

      <i class="icon i--128">
        <svg><use xlink:href="#the-circle" /></svg>
      </i>
    css: |
      .icon {
        color: tomato;
        transition: all .25s linear;
      }
      .icon:hover {
        color: orange;
      }
    html_hidden: |
      <link href="modules.css" rel="stylesheet">

  - type: image
    image: spritebot.jpg

  - content: |
      ## Videos & tutorials

      - [Image formats · SVG ➔](/topics/image-formats/#svg)
      - [Advanced SVG ➔](/topics/advanced-svg/)

---
