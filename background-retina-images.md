---
layout: slide-deck
title: "Background & retina images"
desc: "A quick overview of using CSS background images on a site and when they should be used."

slides:
  - type: super-big-text
    content: |
      **Background & retina images**

  - content: |
      ## Background vs. foreground

      - **`<img>` is for content**
        <br>The user would have difficulty understanding the page without this image

      - **`background-image` is for decoration**
        <br>The user wouldn’t miss the image if it didn’t load

  - content: |
      ## No alternatives

      Background images don’t have `alt=""` tags, because they aren’t important to the content

  - type: interactive
    html: |
      <div class="bg">
        <h1>Background images!</h1>
      </div>
    css: |
      .bg {
        background-image: url("../images/pattern.svg");
        border: 4px solid steelblue;
      }
    css_lines:
      - num: 2
        text: |
          Notice the `url()` function. The path to the image is written from the perspective of the CSS file.

          *It’ll very often start with `../` which means “go out of this folder” or, in this case, go out of the `CSS` folder.*

  - type: interactive
    html: |
      <!--
        If the element doesn’t take up space,
        the image isn’t visible
      -->
      <div class="bg"></div>
    html_lines:
      - num: 5
        text: |
          The background image isn’t visible because the `<div>` doesn’t take up any space in the layout.

          - If the `<div>` had content inside the image would be visible.
          - If the `<div>` had a `height` (not recommended to ever use `height`) the image would also be visible.
    css: |
      .bg {
        background-image: url("../images/pattern.svg");
        border: 4px solid steelblue;
      }

  - type: code
    css: |
      .thingy {
        /* Link to an image in another folder */
        background-image: url("../images/pattern.svg");

        /* Control how the image repeats: `repeat`, `no-repeat` `repeat-x` `repeat-y` */
        background-repeat: no-repeat;

        /* Change the size of the image: `width height` */
        background-size: 64px auto;

        /* Change the location of the image: `horizontal vertical` */
        background-position: left center;
      }

  - type: interactive
    html: |
      <div class="bg">
        <h1>Gradients!</h1>
      </div>
    css: |
      .bg {
        background-image: linear-gradient(to bottom, red, darkred);
        color: #fff;
      }
    css_lines:
      - num: 2
        text: |
          Gradients are background images that the browser generates for us. They will cover the `background-color`.

          *It’s a very good idea to also provide a `background-color` when using gradients.*

  - content: |
      ## Retina images

      - With so many screens being Hi-DPI it’s a good idea to optimize images
      - We need to do it in a way that doesn’t make our website slower

  - content: |
      ## Retina image solutions

      - `<img srcset="…" alt="…">`
      - `<picture>`
      - “Compressive JPGs”
    notes: |
      1. `srcset` is great when you want to provide different resolutions of the same graphic, like a 1× & a 2×. It’s backwards compatible because the regular `src` attribute should always point to the smallest image version.
      2. `<picture>` is great for different croppings of images, like a square image on small screens & a rectangular image on large screens. It’s generally backwards compatible because a standard `<img>` tag should be nested inside.
      3. “Compressive JPGs” are what we’ll concentrate on: making the images bigger than they’re displayed.

  - content: |
      ## Compressive JPGs

      - Recognizes that the images are scaled down
      - The quality can be much lower to save download time—yet still look good
    notes: |
      We’re going to be using Compressive JPGs almost exclusively because in many situations they’re the simplest solution to get the job done.

  - content: |
      ## Compressive calculations

      ```
      (maximum width in browser)
      × 2
      ===============================
      (image dimensions in Photoshop)
      ```

      Photoshop Save for Web JPG quality: `20%–30%`

  - content: |
      ## Videos & tutorials

      - [Using images ➔](/topics/using-images/)
      - [Responsive & retina images ➔](/topics/responsive-retina-images/)
      - [Images cheat sheet ➔](/topics/images-cheat-sheet/)

---
