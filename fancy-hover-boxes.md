---
layout: lesson
title: "Fancy hover boxes"
desc: "An exercise using transitions to create hover boxes that fade from black & white to colour."

markbot_submit: true
hide_show_for_marks: true

extra_tutorials:
  - title: "Transforms & transitions slide deck"
    url: "/courses/web-dev-3/transforms-transitions/"
  - title: "CSS animations & effects"
    url: css-animations-effects
    highlight: true
    videos: true
  - title: "CSS animations & effects cheat sheet"
    url: css-animations-effects-cheat-sheet
    highlight: true
  - title: "Images cheat sheet"
    url: images-cheat-sheet

goal:
  before: |
    We’re going to explore how to use transitions to make fancy hover boxes where images go from greyscale to coloured and zoom in when hovered.
  no_image: true
  video: "https://assets.learn-the-web.algonquindesign.ca/web-dev-3/fancy-hover-boxes/goal.mp4"
  video_poster: goal.jpg
  notes:
    - label: "Type it, type it real good"
      text: "Remember the purpose of this lesson is to type the code out yourself—build up that muscle memory in your fingers!"

fork:
  url: "https://github.com/acgd-webdev-3/fancy-hover-boxes"

steps:
  - title: "Project files"
    before: |
      After forking & cloning the repository to your computer you should have the following files:
    folders:
      - label: "fancy-hover-boxes"
        type: folder
      - label: "images"
        type: folder
        indent: 1
      - label: "black.jpg"
        indent: 2
      - label: "blue.jpg"
        indent: 2
      - label: "orange.jpg"
        indent: 2
      - label: "yellow.jpg"
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
      - label: "humans.txt"
        indent: 1
        notes: "Citations for image usage"
    after: |
      *There’s also some HTML & CSS already coded so we can concentrate completely on making the hover boxes work.*

  - title: "Start some HTML"
    before: |
      The HTML boilerplate already exists for us, we just need to write the hover box HTML. Open up `index.html` and we’ll add in the HTML for the first hover box.
    code_lang: "html"
    code_file: "index.html"
    code: |
      ⋮
      <body>

        <section class="grid">
          <div class="unit xs-1 s-1 m-1-2 l-1-4">
            <a class="hover-box" href="#">
              <div class="embed embed-3by2">
                <img class="hover-box-img embed-item" src="images/orange.jpg" alt="">
              </div>
              <div class="hover-box-caption">
                <h2>Orange butterflies</h2>
              </div>
            </a>
          </div>
        </section>

      </body>
      ⋮
    lines:
      - num: 2
        fade: true
      - num: 17
        fade: true
      - num: 6
        text: |
          Notice the `.hover-box` class is on the `<a>` tag—we’ll be styling that later.
      - num: 8
        text: "Another class here: `.hover-box-img`"
      - num: 10
        text: "And the final class here: `.hover-box-caption`"
    after: |
      If we were to refresh in the browser right now we’d see nothing. So we need a little CSS.

  - title: "Style the basic box"
    before: |
      Because Modulifier is hooked up, let’s start by adding a bunch of those classes for styling.
    multi_code:
      - code_lang: "html"
        code_file: "index.html"
        code: |
          ⋮
          <section class="grid text-center">
            <div class="unit [ xs-1 s-1 m-1-2 l-1-4 ]">
              <a class="hover-box block relative crop" href="#">
                <div class="embed embed-3by2">
                  <img class="hover-box-img embed-item" src="images/orange.jpg" alt="">
                </div>
                <div class="hover-box-caption island-1-4 w-1 absolute">
                  <h2 class="giga push-0 not-bold">Orange butterflies</h2>
                </div>
              </a>
            </div>
          </section>
          ⋮
        lines:
          - num: 2
            text: |
              Add the `.text-center` class here to make all the text inside the boxes centered.
          - num: 4
            text: |
              Add the following classes:

              - `.link-box` — makes the link `display: block`, to allow `<div>` tags inside, and removes the underlines from the text.
              - `.relative` — because we’ll be using `position: absolute` inside the link.
              - `.crop` — this will chop off the text labels because we want them to slide in when hovered.
          - num: 8
            text: |
              Some more styling classes here:

              - `.island-1-4` — for a little space.
              - `.w-1` — to make sure it fills all the way across.
              - `.absolute` — so we can position this with coordinates.
          - num: 9
            text: |
              Finally some styles for the heading itself—they’re pretty self-explanatory.
      - code_lang: "css"
        code_before: |
          Now for a little bit of CSS applied to the `.hover-box`:
        code_file: "css/main.css"
        code: |
          ⋮
          .hover-box {
            color: #fff;
          }

          .hover-box-caption {
            background-image: linear-gradient(to bottom, rgba(0, 0, 0, 0), rgba(0, 0, 0, .5));
            text-shadow: 1px 1px 5px rgba(0, 0, 0, .9);
          }
        lines:
          - num: 3
            text: |
              Though we can’t see the text, it will be white.
          - num: "7-8"
            text: |
              Make the text a little more legible—though we still can’t see anything.
    after: |
      After typing out the above code, refresh in the browser and you see this single butterfly:

      ![](first-box.jpg)

  - title: "Make the caption visible"
    before: |
      Next up we’re going to add a hover state: when hovering the box the caption should become visible.
    code_lang: "css"
    code_file: "css/main.css"
    code: |
      ⋮
      .hover-box-caption {
        bottom: -4em;
        background-image: linear-gradient(to bottom, rgba(0, 0, 0, 0), rgba(0, 0, 0, .5));
        text-shadow: 1px 1px 5px rgba(0, 0, 0, .9);
      }

      .hover-box:hover .hover-box-caption {
        bottom: 0;
      }
    lines:
      - num: "4-5"
        fade: true
      - num: 3
        text: |
          It’s important to define an initial location for the caption, here we’re setting it below the bottom of the image. And therefore it will be cropped off because of the `.crop` class we added earlier.
      - num: "8-10"
        text: |
          When we hover anywhere on the `.hover-box` we want to target the caption and change it’s `bottom` position to `0`, making it align to the bottom of the image now.
    after: |
      Check it out in the browser:

      ![](hover.jpg)

  - title: "Add the caption transition"
    before: |
      Now let’s make this a little fancy with a transition on the caption. The `transition` will allow the caption to animate into it’s location instead of just popping into place.
    code_lang: "css"
    code_file: "css/main.css"
    code: |
      ⋮
      .hover-box-caption {
        bottom: -4em;
        background-image: linear-gradient(to bottom, rgba(0, 0, 0, 0), rgba(0, 0, 0, .5));
        text-shadow: 1px 1px 5px rgba(0, 0, 0, .9);
        transition: all .2s linear;
      }
      ⋮
    lines:
      - num: "3-5"
        fade: true
      - num: 6
        text: |
          The `transition` property will allow any CSS numerical changes to animate. In this case only the `bottom` property changes, so it will be the thing that animates.

          - `all` properties that change will be animated.
          - `.2s` is the length of time the animation will take.
          - `linear` is the type of easing, “linear” meaning “no easing”.

  - title: "Add effects to the image"
    before: |
      Since this lesson is all about being “fancy” let’s fancify the image too. We’re going to make the image black & white, then when hovered it will become coloured and zoom in a little bit.
    code_lang: "css"
    code_file: "css/main.css"
    code: |
      ⋮
      .hover-box-img {
        filter: grayscale(100%);
        transition: all .2s linear;
      }

      .hover-box:hover .hover-box-img {
        filter: grayscale(0);
        transform: scale(1.1);
      }
    lines:
      - num: 3
        text: |
          The `filter` property allows us to add a bunch of different effects to all HTML elements, including text. Here we’re using the `grayscale()` filter to desaturate the image into black & white. The `100%` specifies that we want complete greyscale, a lower percent would be less greyscale and have more colour.

          **Make sure to spell “gray” the American way.**
      - num: 4
        text: |
          Since the `filter` is a numerical property we can totally transition it too.
      - num: 8
        text: |
          Undo the greyscale filter by setting it to `0`
      - num: 9
        text: |
          We can use the `transform` property to grow the image a little bit. The `scale()` function will allow us to grow or shrink HTML elements: `1` is what an element currently is, so `1.1` is just slightly larger.
    after_video: "https://assets.learn-the-web.algonquindesign.ca/web-dev-3/fancy-hover-boxes/hover-effect.mp4"

  - title: "Finish off the rest"
    before: |
      Now that we have that single butterfly working it’s up to you to add the remaining butterflies.

      **Add the following butterflies in this order:**

      - <del>orange.jpg</del> *Done!*
      - black.jpg
      - blue.jpg
      - yellow.jpg

      *Each should be a new `.unit` inside the same `<section>` `.grid`*

      Try ’em out. They should work great since the CSS is already done.

  - title: "Fix the keyboard focus state"
    before: |
      If we `Tab` to each element in the browser we get the focus ring (the big black outline). It isn’t really ideal because it gets hidden behind the elements that come after.

      So, with a little CSS we can make the focus ring work much better for keyboard navigation.
    code_lang: "css"
    code_file: "css/main.css"
    code: |
      ⋮
      .hover-box:focus {
        z-index: 10;
      }

      ⋮

      .hover-box:hover .hover-box-caption,
      .hover-box:focus .hover-box-caption {
        bottom: 0;
      }

      ⋮

      .hover-box:hover .hover-box-img,
      .hover-box:focus .hover-box-img {
        filter: grayscale(0);
        transform: scale(1.1);
      }
    lines:
      - num: "2-4"
        text: |
          When the `.hover-box` is focused we want it to move to the top of the pile, so let’s give is a higher `z-index`
      - num: 9
        text: |
          Add the `:focus` pseudo selector to the caption along with `:hover`—don’t forget the comma (`,`) between them!
      - num: 10
        fade: true
      - num: 16
        text: |
          Add the `:focus` pseudo selector to the image along with `:hover`—don’t forget the comma (`,`) between them!
      - num: "17-18"
        fade: true
    after: |
      Wonderful! Some fancy-fied butterflies.

---
