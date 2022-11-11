---
layout: lesson
title: "Retina images"
desc: "A quick look at exporting retina ready images using the compressive JPG technique."

markbot_submit: true
hide_show_for_marks: true

extra_tutorials:
  - title: "Background & retina images slide deck"
    url: "/courses/web-dev-3/background-retina-images/"
  - title: "Using images"
    url: using-images
  - title: "Responsive & retina images"
    url: responsive-retina-images
  - title: "Images cheat sheet"
    url: images-cheat-sheet
    highlight: true

goal:
  before: |
    We’re going to explore how to export images so they’re clear on retina screens.

    The technique we’re going to look at is called “Compressive JPGs”—essentially we make them double the width and scale them down while significantly reducing the quality.

fork:
  url: "https://github.com/ltw-webdev-3/retina-images/fork"

steps:
  - title: "Project setup"
    before: |
      To get started on this project we need to download a few PSDs to use on the website.

      ### [Download these PSDs.](https://assets.learntheweb.courses/web-dev-3/retina-images-download.zip)

      After downloading the PSDs and cloning the repo you should have a folder structure like this:
    folders:
      - label: "retina-images-lesson"
        type: folder
      - label: "prod"
        type: folder
        indent: 1
      - label: "bee-butt.psd"
        indent: 2
      - label: "bee-face.psd"
        indent: 2
      - label: "retina-images"
        type: folder
        indent: 1
        notes: "This is the cloned GitHub repo"
      - label: "images"
        type: folder
        indent: 2
      - label: "placeholder-3by2.svg"
        indent: 3
      - label: "placeholder-3by1.svg"
        indent: 3
      - label: "css"
        type: folder
        indent: 2
        fade: true
        notes: "We’re not going to touch the CSS"
      - label: "grid.css"
        indent: 3
        fade: true
      - label: "main.css"
        indent: 3
        fade: true
      - label: "modules.css"
        indent: 3
        fade: true
      - label: "type.css"
        indent: 3
        fade: true
      - label: "index.html"
        indent: 2
    after: |
      *Notice how the PSD files are not inside our Git repository, they’re in a folder beside the Git repository named `prod`.*

      **Creative Suite documents never go inside your Git repository!**

  - title: "Determine the image width"
    before: |
      So first, open up the `index.html` into your browser—you should see two placeholder images.

      ![](start.png)

      We need to determine the maximum width the images will ever be. *But we first have to pick a maximum size we want to view the site at.*

      Since we’re using an `xl` size media query, `90em`, in most of our websites let’s use that as the upper limit.

      **So resize the window so it’s exactly `1440px`.**

      Use the developer tools to measure the widths of each image—you should get these sizes:

      ![](measure.png)

  - title: "Calculate the retina width"
    before: |
      Now that we know the maximum width our images will display at we take that width and double it:
    multi_code:
      - code: |
          480 × 2 = 960
          960 × 2 = 1920
      - code_before: "So the formula for compressive JPGs is:"
        code: |
          (maximum width in browser) × 2 = (image dimensions in Photoshop)

  - title: "Resize the images"
    before: |
      With the correct dimensions we can now resize the images so they match the retina width we want.

      ![](psd-img.jpg)

      - Resize the `bee-face` to `1920px`, with a resolution of `72`
      - Resize the `bee-butt` to `960px`, with a resolution of `72`

  - title: "Save for Web"
    before: |
      With the images properly sized we’re now going to export them properly with “Save for Web”.

      The important part of exporting when making compressive JPGs is to make the **quality really low**, 20% low. Since the images will be scaled down by the browser the quality degradation won’t be noticeable.

      ![](export.jpg)

  - title: "Smush the images"
    before: |
      Because performance is probably the most important design consideration for The Web we need to make sure the images are as small as possible.

      Drop ’em into ImageOptim and remove all the extra cruft from the JPGs so they can be as small as possible.

      ![](imageoptim.jpg)

  - title: "Point to the new images"
    before: |
      Finally we’ll point our HTML to the new images.
    code_lang: "html"
    code_file: "index.html"
    code: |
      ⋮
      <div class="grid">
        <div class="unit xs-1 s-1 m-1-3">
          <div class="embed embed-3by2">
            <img class="embed-item" src="images/bee-butt.jpg" alt="">
          </div>
        </div>
        <div class="unit xs-1 s-1 m-2-3">
          <div class="embed embed-3by1">
            <img class="embed-item" src="images/bee-face.jpg" alt="">
          </div>
        </div>
      </div>
      ⋮
    lines:
      - num: "2-4"
        fade: true
      - num: "6-9"
        fade: true
      - num: "11-13"
        fade: true

---
