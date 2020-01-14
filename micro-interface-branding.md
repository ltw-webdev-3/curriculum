---
layout: lesson
title: "Micro interface branding"
desc: "A lesson on making the minimal/necessary amount of favicons at different dimensions & getting them to load."

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
    We’re going to make proper favicons for the most common sizes & hit most of the use cases. You can go really crazy with different favicons for different platforms and crazy amounts of sizes. But most often it’s unnecessary—doing just the most common minimum version is good enough.
  notes:
    - label: "Type it, type it real good"
      text: "Remember the purpose of this lesson is to type the code out yourself—build up that muscle memory in your fingers!"

fork:
  url: "https://github.com/acgd-webdev-3/micro-interface-branding/fork"

steps:
  - title: "Download & set up files"
    before: |
      After forking & cloning the repository, also download these PSD files for our favicons.

      ### [Download these files.](https://assets.learn-the-web.algonquindesign.ca/web-dev-3/micro-interface-branding-download.zip)

      Following our standard folder layout we should have this:
    folders:
      - label: "micro-interface-branding"
        type: folder
      - label: "prod"
        type: folder
        indent: 1
        notes: "These are the files you downloaded"
      - label: "favicon-16.psd"
        indent: 2
      - label: "favicon-32.psd"
        indent: 2
      - label: "favicon-48.psd"
        indent: 2
      - label: "favicon-196.psd"
        indent: 2
      - label: "micro-interface-branding"
        type: folder
        indent: 1
        notes: "The cloned GitHub repo"
      - label: "index.html"
        indent: 2
    after: |
      **Go ahead and make your `index.html` file with the standard `html5` & `viewport` snippets—but we won’t need anything else.**
    notes:
      - label: "Naming conventions"
        text: "Don’t forget to follow the [naming conventions](/topics/naming-paths-cheat-sheet/#naming-conventions)."

  - title: "Make all the sizes"
    before: |
      Favicons are made up of a bunch of differently sized icons. We need all these different icons sizes for different situations, different browsers, and better rendering.

      - `16 × 16 px` — the most basic, used on browser tabs on non-retina screens
      - `32 × 32 px` — used in browser tabs on retina screens & bookmarks
      - `48 × 48 px` — used lots on Windows & when larger icons are needed
      - `196 × 196 px` — used on device homescreens, bookmarks, etc, wherever a large size is helpful

      ### Why don’t we just use one icon and scale it to the different sizes automatically?

      Because our logos & graphics can get really distorted at smaller pixel dimensions. It’s best to spend a few minutes to tweak and massage the icon for different sizes. *Or even make a modified/simplified version for the smallest pixel sizes.*

      *I’ve already made optimized icons at each screen size for you.*
    folders:
      - label: "micro-interface-branding"
        type: folder
      - label: "prod"
        type: folder
        indent: 1
      - label: "favicon-16.psd"
        indent: 2
        notes: "A modified version of the icon best for 16 pixels"
      - label: "favicon-32.psd"
        notes: "Another modified version that looks good at 32 pixels"
        indent: 2
      - label: "favicon-48.psd"
        indent: 2
        notes: "The full version of the icon, but close to the sides"
      - label: "favicon-196.psd"
        indent: 2
        notes: "The full, original version of the icon"
      - continue: true
    after: |
      **When making your own favicons don’t be lazy and use the same icon for every size, spend time optimizing it for different pixel dimensions.**

  - title: "Save all sizes as PNGs"
    before: |
      The second step, after making optimized graphics, is exporting them all as PNGs. Use Photoshop’s “Save for Web” and choose “PNG-24”.

      *We don’t need it for these icons, but be sure to select “Transparency” for your own icons if they have see through areas.*

      **Save these icons somewhere temporary, like your desktop.**
    folders:
      - label: "Desktop"
        type: folder
      - label: "favicon-16.png"
        indent: 1
      - label: "favicon-32.png"
        indent: 1
      - label: "favicon-48.png"
        indent: 1
      - label: "favicon-196.png"
        indent: 1

  - title: "Smush ’em real good"
    before: |
      Don’t forget to smush these PNGs! Drop them all into ImageOptim to get them as small as they can be.

      ![](smush.jpg)

  - title: "Generate an ICO file"
    before: |
      We need to generate a specialized favicon file: the ICO file. This is a container format that actually has multiple differently sized graphics inside. Specifically we want `16px`, `32px` & `48px` size icons inside the ICO container. *The browser will choose whichever suits its purpose.*

      **On non-retina screens browsers will chose the `16px` icon size—form within the single `.ico` file—to show in tabs. But on retina screens they’ll choose the `32px` size icon—all from within the single file format.**

      The absolute *best* application to make favicons with is [**IconSlate**](http://www.kodlian.com/apps/icon-slate)—but it costs about $7. (*It’s totally worth it.*) No other application will allow us to use the `48px` icon that we really need.

      *I would suggest you use IconSlate to generate the favicon, but if you don’t want to spend the money, skip to the next step and see how to do it for free.*
    image_steps:
      - url: "iconslate-sizes.jpg"
        text: |
          Make a new document in IconSlate and select the appropriate format & sizes: `ico` with `16`, `32` & `48`
      - url: "iconslate-copy.jpg"
        text: |
          Drag each differently sized PNG graphic to the appropriately sized box in IconSlate.
      - url: "iconslate-build.jpg"
        text: |
          Press the “Build” button, which will output your `favicon.ico` file. Save it to your Desktop for now.
    image_steps_after: |
      If you check out your Desktop now, you’ll have the 4 PNG files and your new ICO file.
    folders:
      - label: "Desktop"
        type: folder
      - label: "favicon-16.png"
        indent: 1
        fade: true
      - label: "favicon-32.png"
        indent: 1
        fade: true
      - label: "favicon-48.png"
        indent: 1
        fade: true
      - label: "favicon-196.png"
        indent: 1
        fade: true
      - label: "favicon.ico"
        indent: 1
        notes: "You’ll probably have to rename the icon"
    after: |
      **Make sure you rename you brand new favicon to exactly `favicon.ico` for it to work properly.**

  - title: "Generate an inferior ICO file for free"
    before: |
      You can generate a multi-size favicon for free using the [X-Icon Editor](http://www.xiconeditor.com/) web application. Unfortunately it does not support the `48px` size icon so it’ll make favicons that are missing a big chunk of use cases.
    image_steps:
      - url: "xicon-import.jpg"
        text: |
          Go to the X-Icon Editor web application and press the “Import” button.
      - url: "xicon-upload-16.jpg"
        text: |
          Then, press the “Upload” button—choose **only** your `16px` PNG graphic.
      - url: "xicon-select-16.jpg"
        text: |
          In the sizes interface, select only `16px`—**deselect all the other sizes.**
      - url: "xicon-okay-16.jpg"
        text: |
          Press “Okay”.
      - url: "xicon-import-32.jpg"
        text: |
          Press the “Import” button again to insert your `32px` icon.
      - url: "xicon-upload-32.jpg"
        text: |
          Repeat again, uploading only your `32px` icon and deselecting everything except the `32px` size. Press “Okay”.
      - url: "xicon-export.jpg"
        text: |
          Press the “Export” button.
      - url: "xicon-download.jpg"
        text: |
          Press the “Export your icon” button.

  - title: "Move files to the right location"
    before: |
      First we need to move the files we’re keeping to the correct location.

      1. Move the `favicon.ico` into your website repository
      2. Move the `favicon-196.png` into your website repository

      *It’s best practice to keep the favicons in the root of the whole website folder.*
    folders:
      - label: "micro-interface-branding"
        type: folder
      - label: "prod"
        type: folder
        indent: 1
        fade: true
      - label: "micro-interface-branding"
        type: folder
        indent: 1
      - label: "index.html"
        indent: 2
        fade: true
      - label: "favicon.ico"
        indent: 2
      - label: "favicon-196.png"
        indent: 2
    after: |
      You should go ahead and do some clean up. We don’t need the smaller favicon PNGs any more, so delete the following images:

      - Delete: `favicon-16.png`
      - Delete: `favicon-32.png`
      - Delete: `favicon-48.png`

  - title: "Insert into HTML"
    before: |
      Finally we can insert the favicons into our HTML. We only need two new tags to make this work—both in the `<head>` of our HTML document.
    code_lang: html
    code_file: "index.html"
    code: |
      <!DOCTYPE html>
      <html lang="en-ca">
      <head>
        <meta charset="utf-8">
        <title>Fully Fern</title>
        <meta name="viewport" content="width=device-width,initial-scale=1">
        <link rel="shortcut icon" href="favicon.ico">
        <link rel="icon" type="image/png" href="favicon-196.png">
      </head>
      <body>
      ⋮
    lines:
      - num: "1-6,9,10"
        fade: true
      - num: 7
        text: |
          Include the default `favicon.ico` file—this will be used in tabs and many different situations. The browser will extract whichever size from within the file that it needs.
      - num: 8
        text: |
          Browsers will look for the larger icon when they need it, for homescreens, etc.
    after: |
      That’s it! Check out your new favicon in the browser.

      *Notice how the browser will switch between the `16px` & `32px` icon when you switch between retina and non-retina screens.*
---
