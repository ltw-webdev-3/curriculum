---
layout: lesson
title: "Background images"
desc: "Use multiple images as background to create more complex design solutions."

markbot_notes: |
  *Ignore the “there are no headings in this document” error message—but fix everything else.*

  Since this is the footer of a page, a heading isn’t terribly necessary.

extra_tutorials:
  - title: "Using images"
    url: using-images
  - title: "Images for retina screens"
    url: images-for-retina
  - title: "Images cheat sheet"
    url: images-cheat-sheet
    highlight: true

goal:
  image: goal.png
  before: |
    We’re going to explore how to use multiple background images as part of a design to create patterns, textures & symbols.
  notes:
    - label: "Type it, type it real good"
      text: "Remember the purpose of this lesson is to type the code out yourself—build up that muscle memory in your fingers!"

steps:
  - title: "Project setup"
    before: |
      To get started on this project we need to download a few graphics that are exported, compressed, smushed and ready to be used.

      ### [Fork this repo.](https://github.com/acgd-webdev-3/background-images/fork)

      **Make sure you clone it to your computer.**
    folders:
      - label: "background-images"
        type: folder
      - label: "images"
        type: folder
        indent: 1
      - label: "bg.svg"
        indent: 2
      - label: "border-bottom.svg"
        indent: 2
      - label: "border-top.svg"
        indent: 2
      - label: "spy-glass.svg"
        indent: 2
      - label: "css"
        type: folder
        indent: 1
      - label: "grid.css"
        indent: 2
      - label: "main.css"
        indent: 2
      - label: "modules.css"
        indent: 2
      - label: "type.css"
        indent: 2
      - label: "index.html"
        indent: 1
    after: |
      There’s also some HTML & CSS already coded so we can concentrate completely on background images.

  - title: "Spy glass image in search field"
    before: |
      Let’s start by adding the spy glass image as an icon into the search `<input>` field. It’s purely decorative—not part of the content—so a background image makes sense in this situation.
    code_lang: css
    code_file: "css/main.css"
    code: |
      ⋮
      .search-input {
        border-color: #84452f;
        background-image: url("../images/spy-glass.svg");
        background-repeat: no-repeat;
        background-position: .2em center;
        background-size: 1.2em auto;
        padding-left: 1.5em;
      }
      ⋮
    lines:
      - num: 4
        text: |
          The `background-image` property allows us to point to images and load them into the element with CSS.

          There’s no `alt=""` attribute or any backup for background images because they’re purely decoration—if they don’t load then the design & contnet should still be perfectly functional.

          The `../` part is telling the CSS to “go out of the folder we’re in” (aka the `css` folder) then find the `images` folder.
      - num: 5
        text: |
          By default background images are assumed to be patterns and automatically repeat in both directions.

          The `background-repeat` property allows us to control the repeating: to stop it or to force it in only one direction.

          Setting it to `no-repeat` will show the image only once.
      - num: 6
        text: |
          The `background-position` property allows us to control where inside the element the image is visible. It is always made up of a horizontal position & a vertical position.

          In this piece of code the numbers mean this:

          - `.2em` from the left edge of the element
          - `center` is to vertically centre the element

          Horizontal first, vertical second. Always.
      - num: 7
        text: |
          The `background-size` property allows us to scale the image to dimensions we want. Width first, height second.

          In this piece of code the numbers mean this:

          - `1.2em` — the width
          - `auto` — figure out the appropriate height to maintain the aspect ratio
    after: |
      The `padding` above is important because background images don’t take up any space. So the text would end up being on top of the image, making it really difficult to read.

      If you refresh your browser you should see the spy glass image inside the search field now:

      ![](spy-glass.png)

  - title: "Gradient on the button"
    before: |
      Next up we’ll add a gradient to the button. It’s a very subtle detail in the images.
    code_lang: "css"
    code_file: "css/main.css"
    code: |
      ⋮
      .search-btn {
        background-image: linear-gradient(to bottom, #794431, #8e4a32);
        border-color: #794431;
      }
      ⋮
    lines:
      - num: 3
        text: |
          Gradients are images that the browser generates for us, they overlay onto the `background-color` just like all background images.

          Here we’re generating a gradient that goes from the top to the bottom of the button with two colours. Gradients can get much more complex with stops and stuff.
      - num: 4
        text: |
          Change the border colour of the button so it matches the new gradient better.
    after: |
      This is what we should see with the refresh:

      ![](gradient.png)

  - title: "Pattern background"
    before: |
      Next up we’ll add a patterned texture to the background of the whole footer. Since the browser assumes we want a pattern there’s very little CSS to write.
    code_lang: "css"
    code_file: "css/main.css"
    code: |
      ⋮
      .footer {
        background-color: #da823b;
        border-bottom: 3px solid #8e4a32;
        border-top: 3px solid #8e4a32;
        background-image: url("../images/bg.svg");
        background-size: 18px auto;
      }
      ⋮
    lines:
      - num: "3-5"
        fade: true
      - num: "6-7"
        text: |
          We only need to specify the `url()` and the size—because the browser will automatically pattern the image for us.
    after: |
      We should now see a repeating background texture on the whole footer:

      ![](pattern.png)

  - title: "Double bordered edges"
    before: |
      For the final touch, we’re going to add a double border to the bottom and the top of the `<footer>`. The double border is actually a few more background images that we’ll place inside the footer.

      Elements can have as many background images as we want, each separated by a comma in the `background-image` property.

      The order is important—the first image in the list is on top, the last on the bottom.

      **We’re adding to and replacing the CSS we write into `.footer` in the previous step.**
    code_lang: "css"
    code_file: "css/main.css"
    code: |
      ⋮
      .footer {
        background-color: #da823b;
        border-bottom: 3px solid #8e4a32;
        border-top: 3px solid #8e4a32;
        background-image: url("../images/border-top.svg"), url("../images/border-bottom.svg"), url("../images/bg.svg");
        background-size: 2px 5px, 2px 5px, 18px auto;
        background-repeat: repeat-x, repeat-x, repeat;
        background-position: left top, left bottom, left top;
      }
      ⋮
    lines:
      - num: "3-5"
        fade: true
      - num: "6-9"
        text: |
          Multiple background images—separated by commas.

          And all their associated other properties also separated by commas: `background-size`, `background-repeat`, `background-position`
    after: |
      Have a look in the browser and see the final version of the footer.
---
