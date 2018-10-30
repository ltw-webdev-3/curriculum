---
layout: slide-deck
title: "Many images, you choose"
desc: "A quick overview of the different ways to serve images in modern browsers for the best performance and look."

slides:
  - type: super-big-text
    content: |
      **Many images, you choose**

  - content: |
      ## Giving away control

      *As a web designer we need to learn to give up control.*

      - We don’t control the browser size
      - We don’t control the font-size
      - [We don’t control the interaction method](/courses/web-dev-3/week-11/)
      - [We don’t control the download speed](/courses/web-dev-3/week-11/)
      - [We don’t control if JavaScript will run](/topics/progressive-enhancement/)

      **And now we don’t control what image—if any—is displayed to our users.**

  - content: |
      ## Users (and browsers) know best

      - Our users know what kind of images they need
      - Their browsers know the connection speed, the screen density, the screen size, etc.

      **We don’t know nothin’—so let the browser choose the best image for the user’s situation.**

  - content: |
      ## Order of image choice…

      1. Don’t use images, use CSS if it’s possible—and reasonable
      2. Use an SVG if it’s possible—and reasonable
      3. Use double-size JPGs for simplicity
      4. Use `<img srcset>` for better performance
      5. Use `<picture>` for more control

  - content: |
      ## Double-size JPGs

      We’ve looked at this method already: determine the max viewable size of the image & double it

      - It’s simple & straightforward
      - It’s easy to implement with no extra code
      - It doesn’t increase download times

      - **It drastically increases memory usage**—slower and older devices have to unpack and render an image that’s much bigger than necessary

  - content: |
      ## Exact image, different resolutions

      For the exact same image with different resolutions use `<img srcset="">`—and let the browser choose the best image

      - Requires multiple image sources
      - Requires more code

      - Doesn’t increase download times
      - Uses memory the device can handle

  - type: code
    before: |
      Give the browser a bunch of information and let it choose which image is best to display.
    html: |
      <!-- This is written on multiple lines for clarity only -->

      <img
        srcset="images/dino-l.jpg 2500w, images/dino-m.jpg 1000w, images/dino-s.jpg 320w"
        sizes="(min-width: 60em) 50vw, 100vw"
        src="images/dino-s.jpg"
        alt="A ginormous dinosaur">
    html_lines:
      - num: 3
        text: |
          First tell the browser about what images are available: the `srcset` attribute is a list of images & their width in pixels.

          *This `srcset` attribute says:*
          - There’s a `2500px` wide image named “dino-l.jpg”
          - There’s a `1000px` wide image named “dino-m.jpg”
          - And here’s a `320px` wide image named “dino-s.jpg”

          **Always put the biggest first—the browser will stop when it finds an image the fits best—so we always show the best available image.**
      - num: 4
        text: |
          Second tell the browser what sizes this image will be displayed at, using media queries.

          *This `sizes` attribute says:*
          - When the browser is wider than `60em`, the image will be displayed at half with window’s width
          - The rest of the time it will be displayed at full window width

          **Start with the largest screen size and work backwards—opposite to how we write CSS.**
      - num: 5
        text: |
          Still provide the basic `src` attribute for browsers that don’t support `srcset` and they’ll still show an image.

          **But make sure this is always the smallest image possible.**
      - num: 6
        text: |
          Don’t forget a descriptive `alt` attribute!

  - content: |
      ## Different sizes, different crops

      When you want to present different images & different croppings at different resolutions use the `<picture>`

      - Requires multiple image sources
      - Requires more code

      - Doesn’t increase download times
      - Uses memory the device can handle
      - Gives designers a little more control

  - type: interactive
    resizable: true
    before: |
      Give the browser a bunch of information, *suggest when to use each image*, and let it choose which image is best to display.
    html: |
      <picture class="img-flex">
        <source media="(min-width: 60em)" srcset="dino-l.png">
        <source media="(min-width: 38em)" srcset="dino-m.png">
        <img src="dino-s.png" alt="A ginormous dinosaur">
      </picture>
    html_lines:
      - num: 2
        text: |
          Start with the largest image possible, providing the media query where it should be shown and the image name.
      - num: 3
        text: |
          Add any other sizes that you’ve got, decreasing in size as you go down the code.

          **The first one that matches will be chosen, so we want the biggest matching one to display.**
      - num: 4
        text: |
          Finish off with a standard `<img>` tag. This is the fallback, **the smallest image**, and provides the alternative text for the whole `<picture>` element.
    css: |
      .img-flex,
      .img-flex img {
        display: block;
        width: 100%;
      }
    css_lines:
      - num: 2
        text: |
          When dealing with the picture tag we must also style the `<img>` tag inside for property scaling.

          **If you use Modulifier’s `.img-flex` class, this is already built in.**

  - type: code
    before: |
      If you want to really complicate things you can specify different sizes & resolutions for the `<picture>` tag.
    html: |
      <picture class="img-flex">
        <source media="(min-width: 60em)" srcset="dino-l-2x.png 2x, dino-l.png 1x">
        <source media="(min-width: 38em)" srcset="dino-m-2x.png 2x, dino-m.png 1x">
        <img srcset="dino-s-2x.png 2x, dino-s.png 1x" src="dino-s.png" alt="A ginormous dinosaur">
      </picture>

  - content: |
      ## Videos & tutorials

      - [Responsive & retina images](/topics/responsive-retina-images/)
      - [Images cheat sheet](/topics/images-cheat-sheet/)

---
