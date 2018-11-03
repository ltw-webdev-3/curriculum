---
layout: lesson
title: "Different crops, same image"
desc: "Use the picture tag to create a responsive banner that adjusts the image to fit the screen while maintaining the design aesthetic better."

hide_show_for_marks: true
markbot_submit: true

extra_tutorials:
  - title: "Images for the web"
    url: image-formats
    highlight: true
  - title: "Images cheat sheet"
    url: images-cheat-sheet

goal:
  before: |
    We’re going to implement a different kind of responsive banner. Instead of have the text off the image on small screens, then on at larger screens, we’re going to make use of the `<picture>` tag to use the same general layout, but with differently cropped images.

fork:
  url: "https://github.com/acgd-webdev-3/different-crops-same-image/fork"

steps:
  - title: "Download & set up files"
    before: |
      After forking & cloning the repository, also download these PSD files for our images.

      ### [Download these files.](https://assets.learn-the-web.algonquindesign.ca/web-dev-3/different-crops-same-image-download.zip)

      Following our standard folder layout we should have this:
    folders:
      - label: "different-crops-same-image"
        type: folder
      - label: "assets"
        type: folder
        indent: 1
        fade: true
      - label: "prod"
        type: folder
        indent: 1
        notes: "These are the files you downloaded"
      - label: "banner.psd"
        indent: 2
      - label: "banner-l.psd"
        indent: 2
      - label: "banner-m.psd"
        indent: 2
      - label: "banner-s.psd"
        indent: 2
      - label: "different-crops-same-image"
        type: folder
        indent: 1
        notes: "The cloned GitHub repo"
      - label: "css"
        indent: 2
        type: folder
      - label: "main.css"
        indent: 3
      - label: "modules.css"
        indent: 3
      - label: "type.css"
        indent: 3
      - label: "index.html"
        indent: 2
    after: |
      *All the CSS has already been written. And some of the HTML has been written: mainly the boilerplate and the CSS connections.*

      **Notice that I’ve already created all the different sizes of banner graphics. They have different aspect ratios and different croppings to optimize their indented screen size.**
    notes:
      - label: "Naming conventions"
        text: "Don’t forget to follow the [naming conventions](/topics/naming-paths-cheat-sheet/#naming-conventions)."

  - title: "Save web-ready graphics"
    before: |
      Before we get started writing the HTML, let’s export all the banner graphics from Photoshop using the “Save for web” utility.

      **All the graphics are saved in their retina (2×) size. So we’ll need to resample them on save.

      **Large sizes: Open `banner-l.psd`**

      1. Use “Save for web” to save it as a JPG—around 55% quality looks okay.
      2. Name it `banner-l-2x.jpg` in your `images` folder.
      3. Now, “Save for web” again, and resize it down to `1200` pixels wide (in the bottom right corner of the dialog).
      4. Save it as `banner-l.jpg`, around 55% is okay.

      **Medium sizes: Open `banner-m.psd`**

      1. Same thing: save as JPG at its original size: `banner-m-2x.jpg`
      2. Resize to half size, `600px`, and save another JPG: `banner-m.jpg`

      **Small sizes: Open `banner-s.psd`**

      1. Same thing: save as JPG at its original size: `banner-s-2x.jpg`
      2. Resize to half size, `320px`, and save another JPG: `banner-s.jpg`
    folders:
      - label: "different-crops-same-image"
        type: folder
      - label: "assets"
        type: folder
        fade: true
        indent: 1
      - label: "prod"
        type: folder
        fade: true
        indent: 1
      - label: "different-crops-same-image"
        type: folder
        indent: 1
      - label: "css"
        type: folder
        indent: 2
        fade: true
      - label: "index.html"
        indent: 2
        fade: true
      - label: "images"
        type: folder
        indent: 2
      - label: "banner-l-2x.jpg"
        indent: 3
      - label: "banner-l.jpg"
        indent: 3
      - label: "banner-m-2x.jpg"
        indent: 3
      - label: "banner-m.jpg"
        indent: 3
      - label: "banner-s-2x.jpg"
        indent: 3
      - label: "banner-s.jpg"
        indent: 3

  - title: "Smush ’em real good"
    before: |
      Don’t forget to smush these JPGs! Drop them all into ImageOptim to get them as small as they can be.

      ![](smush.jpg)

  - title: "Write small screen HTML"
    before: |
      Now we’re ready to write the basic HTML for small screens. After that’s done we’ll add in the `<picture>` element to make responsive adaptations.
    code_lang: html
    code_file: "index.html"
    code: |
      ⋮
      <body>

        <div class="banner relative">
          <img class="img-flex" src="images/banner-s.jpg" alt="">
          <div class="absolute pin-lb island-1-2 max-length">
            <h1 class="push-1-8">Maize: cornerstone of culture &amp; spirituality</h1>
            <p class="push-1-2">Corn has played a significant role in empires, civilizations and people for thousands of years—Mayans even having a Maize God.</p>
            <a class="btn btn-ghost banner-btn" href="#">More about maize</a>
          </div>
        </div>

      </body>
      ⋮
    lines:
      - num: "2,13"
        fade: true
      - num: 5
        text: |
          We’re starting with the super basic image tag, just a single `<img>` that points to the `banner-s.jpg`
    after: |
      We don’t need to write any CSS, I’ve already done CSS for `.banner` & `.banner-btn` so we can concentrate on the HTML.

      *Pop that open in your browser and see what it looks like.*

      ![](basic-small.jpg)

  - title: "Add picture element for different sizes"
    before: |
      Now we’ll update the HTML to add a `<picture>` element that will allow the image to change depending on the screen size.
    code_lang: html
    code_file: "index.html"
    code: |
      ⋮
      <div class="banner relative">
        <picture class="img-flex">
          <source media="(min-width:60em)" srcset="images/banner-l.jpg">
          <source media="(min-width:38em)" srcset="images/banner-m.jpg">
          <img src="images/banner-s.jpg" alt="">
        </picture>
        <div class="absolute pin-lb island-1-2 max-length">
          <h1 class="push-1-8">Maize: cornerstone of culture &amp; spirituality</h1>
          <p class="push-1-2">Corn has played a significant role in empires, civilizations and people for thousands of years—Mayans even having a Maize God.</p>
          <a class="btn btn-ghost banner-btn" href="#">More about maize</a>
        </div>
      </div>
      ⋮
    lines:
      - num: "2,8-13"
        fade: true
      - num: 3
        text: |
          Add a new `<picture>` tag surrounding the old `<img>` tag. Notice that we moved the `.img-flex` class up to `<picture>` and removed it from `<img>`
      - num: 4
        text: |
          We start with the largest size possible: when the screen is larger than `60em`; link in the `banner-l.jpg` image.
      - num: 5
        text: |
          The next size is the medium-sized image at `38em`—our `banner-m.jpg`
      - num: 6
        text: |
          We deleted the `.img-flex` from the `<img>` and moved it up to the `<picture>` tag instead.
    after: |
      Now as we adjust the screen size you’ll see that the image changes to one of the alternatives. I think this is a much more direct & simple way to create a responsive banner than making a bunch of media queries. Plus we get the added benefit of the banner actually looking much more similar between different screen sizes.

      Check it out in your browser. Make sure to change the screen size!

      ![](medium.jpg)

  - title: "Add the retina images"
    before: |
      The final thing we’re going to do is modify the `<picture>` element further to add all our retina-ready graphics.
    code_lang: html
    code_file: "index.html"
    code: |
      ⋮
      <div class="banner relative">
        <picture class="img-flex">
          <source media="(min-width:60em)" srcset="images/banner-l-2x.jpg 2x, images/banner-l.jpg 1x">
          <source media="(min-width:38em)" srcset="images/banner-m-2x.jpg 2x, images/banner-m.jpg 1x">
          <img srcset="images/banner-s-2x.jpg 2x, images/banner-s.jpg 1x" src="images/banner-s.jpg" alt="">
        </picture>
        <div class="absolute pin-lb island-1-2 max-length">
          <h1 class="push-1-8">Maize: cornerstone of culture &amp; spirituality</h1>
          <p class="push-1-2">Corn has played a significant role in empires, civilizations and people for thousands of years—Mayans even having a Maize God.</p>
          <a class="btn btn-ghost banner-btn" href="#">More about maize</a>
        </div>
      </div>
      ⋮
    lines:
      - num: "2-3,7-13"
        fade: true
      - num: 4
        text: |
          I added `images/banner-l-2x.jpg 2x` to the start of the `srcset`

          Also notice the addition of the `1x` at the very end of the `srcset`

          No we’re specifying that on large screens there’s a retina-friendly graphic & a low-density graphic.
      - num: 5
        text: |
          Same deal for the second `<source>` tag—retina and non-retina versions for medium.
      - num: 6
        text: |
          Finally, I added a whole new attribute to the `<img>` tag: the `srcset` attribute. Like the two `<source>` tags it shows two different resolutions of images.

          **The `srcset` attribute in `<img>` tags is not a replacement for the basic `src`**
    after: |
      It’s a little harder to see these changes because the images look identical on retina and non-retina screens.

      *If you want to truly see it working, the only way I know how, is to use the browser’s developer tools and look in the “Network” panel. As you resize the screen and move the browser between retina & non-retina screens you’ll see the different versions download.*

---
