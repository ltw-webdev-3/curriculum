---
layout: lesson
title: "Using SVG icons"
desc: "Use Illustrator & Spritebot to generate some SVG icons and use them in a website."

markbot_notes: |
  *Ignore the “there are no headings in this document…” error message—but fix everything else.*

extra_tutorials:
  - title: "Advanced SVG"
    url: advanced-svg
  - title: "Advanced SVG slide deck"
    url: /courses/web-dev-4/advanced-svg/

goal:
  image: goal.gif
  before: |
    We’re going to look at creating an SVG sprite sheet with some icons inside. Then we’ll use the icons on a website in a simple layout.
  notes:
    - label: "Type it, type it real good"
      text: "Remember the purpose of this lesson is to type the code out yourself—build up that muscle memory in your fingers!"

steps:
  - title: "Set up project"
    before: |
      To get started on this project we need to download a few graphics that we can manipulate & export.

      ### [Download these files.](https://assets.learn-the-web.algonquindesign.ca/web-dev-4/using-svg-icons-download.zip)

      Now create the following folder structure on your computer:
    folders:
      - label: "using-svg-icons"
        type: folder
      - label: "index.html"
        indent: 1
      - label: "css"
        type: folder
        indent: 1
      - label: "main.css"
        indent: 2
      - label: "modules.css"
        indent: 2
      - label: "images"
        type: folder
        indent: 1
    after: |
      1. Create a folder named `using-svg-icons`
      2. Make an `index.html` & add the boilerplate code.
      3. Make a `main.css` in your `css` folder—it can remain empty.
      4. Make a `modules.css` in your `css` folder—[get a new version from Modulifier](https://modulifier.web-dev.tools/). **Make sure to press “Select All”.**
    notes:
      - label: "Naming conventions"
        text: "Don’t forget to follow the [naming conventions](/topics/naming-paths-cheat-sheet/#naming-conventions)."
      - label: "HTML snippets"
        text: "Create the boilerplate with `html5`, `viewport`, `css`"

  - title: "Organize the Illustrator file"
    before: |
      The first step to using SVG icons is to organize the Illustrator document so it can be exported properly.

      For icons, the way we export is no different from standard SVGs: resize & name the artboards.

      Open up the Illustrator file and you should see this:

      ![](illlustrator.jpg)

      Our first step is to create multiple artboards—**each artboard should be `256px` × `256px`**

      ![](artboard.jpg)

      Move the dinosaur icons so that they are on individual artboards. I resized each icon to be `252px` wide.

      I named each artboard this:

      1. `brachiosaurus`
      2. `micropachycephalosaurus`
      3. `velociraptor`

      ![](all-artboards.jpg)

      The final change we need to make is the `fill`. Since we’re interested in colouring the icons in our CSS and want to have different hover colours we need to remove the fill colours in Illustrator.

      ![](fill-black.jpg)

      The simplest way to remove fill colours when exporting from Illustrator is to set all their colours to black. The default `fill` in SVG is black, so the optimizer will leave the fill off.

      **Of course you could remove the fill colour in Illustrator but then you wouldn’t be able to see the graphic and that’s just annoying.**

      *If you want differently coloured or multi-coloured icons then leave the fill.*

  - title: "Export the SVGs"
    before: |
      We’re ready to export our SVGs from Illustrator now. Go to:

      ```
      File > Export > Export for Screens…
      ```

      Assuming you’ve exported using “Export for Screens” before there shouldn’t really be any settings we need to change.

      [If you haven’t used “Export for Screens” before, see this tutorial.](/topics/image-formats/#export-for-screens)

      ![](export.jpg)

      **Be sure to set the correct output location: the `images` folder inside your `using-svg-icons` folder.**
    notes:
      - label: "Keyboard shortcut"
        text: |
          Export for screens: `⌥⌘E`

  - title: "Generate a sprite sheet"
    before: |
      We should now have 3 completely separate SVG files in our SVG folder, looking like this:
    folders:
      - label: "using-svg-icons"
        type: folder
      - label: "index.html"
        indent: 1
        fade: true
      - label: "css"
        type: folder
        indent: 1
        fade: true
      - label: "images"
        type: folder
        indent: 1
      - label: "brachiosaurus.svg"
        indent: 2
      - label: "micropachycephalosaurus.svg"
        indent: 2
      - label: "velociraptor.svg"
        indent: 2
    after: |
      Drop all 3 of the images into [**Spritebot**](https://github.com/thomasjbradley/spritebot)—which will compress and optimize the images for us.

      ![](spritebot.jpg)

      When Spritebot is ready we want to merge all the SVGs into a single file. This is called a sprite sheet. The benefit is performance: less downloads & faster websites.

      ![](delete-singles.jpg)

      After we’ve created & saved the sprite sheet, the original SVG graphics are useless—delete them.

      Now we’re ready to use the icons in our HTML!

  - title: "Write the HTML code"
    before: |
      Let’s write out the HTML we need to show the icons. For this quick example we’ll use a list and some links.
    code_lang: "html"
    code_file: "index.html"
    code: |
      ⋮
      </head>
      <body>

        <ul class="list-group-inline">
          <li class="center-text">
            <a class="block" href="#">
              <i class="icon i-96">
                <svg><use xlink:href="images/dino-icons.svg#brachiosaurus" /></svg>
              </i>
              <span class="block icon-text">Brachiosaurus</span>
            </a>
          </li>

          <!-- Add all the other <li> tags here-->

        </ul>

      </body>
      </html>
    lines:
      - num: "2-3"
        fade: true
      - num: 8
        text: |
          We’ll use the `<i>` tag and the `.icon` class to define the box surrounding our SVG icons.
      - num: 9
        text: |
          Now the `<svg>` tag. Inside it we have a `<use>` tag that points to our image.

          The `xlink:href=""` attribute on a `<use>` tag is comparable to the `src=""` attribute on an `<img>` tag.

          There are a few important parts to look at:

          1. `images/dino-icons.svg` — this is the path to the sprite sheet image file.
          2. The `#brachiosaurus` is the ID that Spritebot assigned the icon within the sprite sheet. The icon’s ID always matches it’s filename.
    after: |
      **Make sure you spell the ID properly in the `xlink:href=""`—Spritebot always makes the ID the same as the original filename you used to generate the sprite sheet.**

      Go ahead and put 2 more `<li>` tags into the code for each of the two other icons:

      - `#micropachycephalosaurus`
      - `#velociraptor`

  - title: "Preview in browser with “localhost”"
    before: |
      Now let’s load it up in our browser and see the icons.

      ![](chrome-error.jpg)

      *Or not…*

      If you’re using Firefox or Safari the icons should load right away. Chrome has tighter security restrictions and requires us to use a web server to see the icons.

      Luckily, Markbot has a web server built into it for use during our web development.

      ![](markbot.jpg)

      In the `File` menu go to `Browse Local Website` (`⌘B`)—this will pop open your default browser with the URL to your project running over with a web server.

      The URL will most likely be: [**https://localhost:8000/**](https://localhost:8000/).

      ![](chrome-security.jpg)

      Next up we’ll see a security error about the connection not being private. The browser doesn’t believe the HTTPS certificate Markbot uses is secure because it wasn’t signed by an authority.

      **You should never bypass this error message on websites.** In this situation it’s okay because we’re loading our “localhost” testing server.

      So, click “ADVANCED”.

      ![](chrome-security-proceed.jpg)

      Then click “Proceed to localhost (unsafe)”.

      ![](default-icons.jpg)

      Now we should see our icons!

  - title: "Add colours & hovers"
    before: |
      Our icons are currently using the default link colours: blue & purple. (If you click on them they should all go purple.)

      So let’s add a little touch of CSS to colour the links better.
    code_lang: "css"
    code_file: "css/main.css"
    code: |
      a {
        color: #76a500;
      }

      a:hover {
        color: #acc300;
      }
    after: |
      A real basic green colour and a slightly different hover green.

      Test it out—should work great.

---
