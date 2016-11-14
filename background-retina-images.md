---
layout: slide-deck

title: "Background & retina images"

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

  - type: interactive
    html: |
      <!--
        If the element doesn’t take up space,
        the image isn’t visible
      -->
      <div class="bg"></div>
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

  - content: |
      ## Retina images

      - With so many screens being Hi-DPI it’s a good idea to optimize images
      - We need to do it in a way that doesn’t make our website slower

  - content: |
      ## Retina image solutions

      - `<img srcset="…" alt="…">`
      - `<picture>`
      - “Compressive JPGs”

  - content: |
      ## Compressive JPGs

      - Recognizes that the images are scaled down
      - The quality can be much lower to save download time—yet still look good

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
      - [Images for retina screens ➔](/topics/images-for-retina/)
      - [Images cheat sheet ➔](/topics/images-cheat-sheet/)

---
