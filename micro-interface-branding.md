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
  image: goal.png

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
      - label: "favicon-38.psd"
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

      **I’ve already made optimized icons at each screen size for you.**

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
      - label: "favicon-38.png"
        indent: 1
      - label: "favicon-196.png"
        indent: 1

  - title: "Smush ’em real good"
    before: |
      Don’t forget to smush these PNGs! Drop them all into ImageOptim to get them as small as they can be.

      ![](smush.jpg)

  - title: "Generate an ICO file"
    before: |
      The absolute *best* application to make favicons with is [**IconSlate**](http://www.kodlian.com/apps/icon-slate)—but it costs about $7. (*It’s totally worth it.*) No other application will allow us to use the `48px` icon that we really need.

  - title: "Insert into HTML"
---
