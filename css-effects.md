---
layout: slide-deck

title: "CSS effects"

slides:
  - type: super-big-text
    content: |
      **CSS effects**

  - content: |
      ## `transform`

      *Visual, non-interactive effects*

      - `rotate()`
      - `skew()`
      - `scale()`
      - etc.

  - type: interactive
    html: |
      <div class="violet"></div>
      <div class="purple"></div>
      <div class="green"></div>
    css: |
      .violet {
        transform: rotate(33deg);
      }
      .purple {
        transform: skew(24deg);
      }
      .green {
        transform: scale(1.5) rotate(-6deg);
      }
    css_hidden: |
      div {
        width: 100px;
        height: 100px;
        margin: 50px 100px;
      }
      .violet {
        background-color: #5e54af;
      }
      .purple {
        background-color: #9d35af;
      }
      .green {
        background-color: #00675a;
      }

  - content: |
      ## `transition`

      *Animations and effects with user interaction*

      - Triggered when a property changes on an element
      - **Must always be written on the default state**

  - type: interactive
    html: |
      <a class="btn" href="#">T-Rex!</a>
    css_lines: "3"
    css: |
      .btn {
        background-color: #5e54af;
        transition: all 200ms linear;
      }
      .btn:hover {
        background-color: #3c3670;
      }
    css_hidden: |
      .btn {
        display: inline-block;
        padding: .5em .75em;
        border: 0;
        border-radius: 10px;
        text-decoration: none;
        color: #fff;
      }

  - content: |
      ## `animation`

      *Complex keyframe-based animation—can autoplay*

      - Uses the `@keyframe` block
      - Keyframes are specified in percentages

  - type: interactive
    html: |
      <div class="purple"></div>
    css_lines: "2-3"
    css: |
      .purple {
        transform-origin: right bottom;
        animation: spin 1s infinite alternate;
      }
      @keyframes spin {
        0% { transform: rotate(0deg); }
        100% { transform: rotate(360deg); }
      }
    css_hidden: |
      div {
        width: 200px;
        height: 200px;
        margin: 100px;
      }
      .purple {
        background-color: #9d35af;
      }

  - type: image
    image: transition-or-animation.svg

  - content: |
      ## `:target`

      *Style an element if its ID is in the URL*

  - type: interactive
    url: |
      index.html
      index.html#thing
    html: |
      <a href="#thing">Go</a>
      <a href="#">Stop</a>
      <div class="panel" id="thing"></div>
    css: |
      .panel {
        background-color: #9d35af; /* Purple */
      }
      .panel:target {
        background-color: #00deaf; /* Teal */
        border: 10px solid #000;
      }
    css_hidden: |
      .panel {
        min-height: 200px;
      }

  - content: |
      ## Videos & tutorials

      [CSS animations & effects ➔](/topics/css-animations-effects/)

---
