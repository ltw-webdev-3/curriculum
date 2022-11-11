---
layout: lesson
title: "Using a11y testing tools"
desc: "An overview of what tools to use and what you’re looking for when using the tools on websites."

hide_markbot: true
hide_show_for_marks: true

extra_tutorials:
  - title: "Accessibility"
    url: accessibility
  - title: "Accessibility slide deck"
    url: /courses/web-dev-3/accessibility/
  - title: "Accessibility cheat sheet"
    url: accessibility-cheat-sheet
  - title: "Accessibility checklist"
    url: accessibility-checklist
  - title: "Accessibility testing checklist"
    url: accessibility-testing-checklist

goal:
  no_image: true
  before: |
    We’re going to look at using different accessibility tools and work towards understanding what the tools help us see and diagnose.

    **This list is essentially a checklist of what to check & how to check for accessibility problems.** *[There is also an accessibility checklist.](/topics/accessibility-checklist/)*
  notes:
    - label: "Type it, type it real good"
      text: "Remember the purpose of this lesson is to type the code out yourself—build up that muscle memory in your fingers!"

important:
  title: "Accessibility user testing is best"
  text: |
    **There is so much to making an accessible website. The list below is a good start but should not be considered “all there is”.**

    The only way to truly test website accessibility is with live user feedback. Find people and test your website with their different conditions and tools.

steps:
  - title: "Open a website to test"
    before: |
      Let’s use the NASA website for our testing today; so go ahead and open the website in another tab:

      ### [Open NASA’s website ➔](https://www.nasa.gov/)

  - title: "Increase & decrease the text size"
    before: |
      **Not every human being needs the same font-size when viewing a website.** That’s exactly why we use `rem` and other relative measurements. *We need to confirm our website works with different font sizes.*

      ## Use Firefox

      Firefox still has the best text size adjustment capabilities. The other browsers use a “zooming” system—where Firefox will just bump the font-size up and down for us.

      But we need to enable the functionality:

      ![Turn on Firefox’s “Zoom Text Only” feature](firefox.jpg)

      *In the menu, go to `View > Zoom` and check `Zoom Text Only`*

      ## Increase by two increments

      On NASA’s website press `⌘+` twice. This will enlarge the text two stops. This simulates a user setting the default font-size of their browser to a larger size than `16px`

      ![NASA’s website with enlarged text](nasa-big-text.jpg)

      ## What problems might be found?

      Scroll through the website and look for these possible problems:

      - [ ] Is the layout still functional?
      - [ ] Can all the text be read?
      - [ ] Is there any overlapping elements?
      - [ ] Are there any text breaking out of boxes?

      *You may find that different media queries trigger as the font-size gets larger—that’s exactly the reason why we use `em`-based media queries, so the layout adapts to the available content space.*

      ## Decrease by two increments

      Now we want to test the opposite direction: making the text smaller.

      1. First, set the font-size back to default with `⌘0`
      2. Decrease the font-size by pressing `⌘-` twice.

      ![NASA’s website with shrunken text](nasa-small-text.jpg)

      ## What problems might be found?

      Scroll through the website and look for these possible problems:

      - [ ] Is the layout still functional?
      - [ ] Can all the text be read?
      - [ ] Are the hit areas of links still big enough to target properly by a non-professional mouse user?

  - title: "Test with a screen magnifier"
    before: |
      **Some users need to have very enlarged and focused text to be able to discern the website.** *We need to confirm that our website works properly with a screen magnifier.*

      ## Enabled MacOS’s screen magnification tools

      MacOS has a screen magnifier built into the operating system—let’s just make sure it’s enabled.

      Go to `System Preferences > Accessibility`. On the left list go to `Zoom`.

      ![Enable screen zooming on MacOS](a11y-zoom.jpg)

      *I like to make sure “Use keyboard shortcuts for zoom” is checked.*

      Now we can use `⌘⌥+` and `⌘⌥-` to zoom the screen in and out. As we move around with our mouse the screen will move with use to magnify small parts of the screen at a time.

      ![NASA’s website viewed with screen zooming](nasa-magnified.jpg)

      ## What problems might be found?

      Navigate through the magnified website and look for these possible problems:

      - [ ] Hover boxes that disappear when you try to move the mouse onto them to read the text
      - [ ] Content that becomes covered when hover events are triggered
      - [ ] Results of actions that are not within the vicinity of the mouse

  - title: "Check keyboard access"
    before: |
      **Not everybody can use a mouse to access our websites.** We can test keyboard accessibility by using only the keyboard to navigate our own websites. *We need to confirm that we’re able to access every piece on content & every piece of functionality using only the keyboard.*

      ## Press `Tab` to navigate

      In Chrome, Firefox, or Opera, (Safari isn’t the best choice for this test) navigate around your website using the `Tab` key. You should see a focus rectangle highlight the different parts of your website as you move around.

      Try activating elements with `Return`, `Space`, or the arrow keys.

      ![NASA’s website navigated with the tab key](nasa-tab.jpg)

      ## What problems might be found?

      Tab through the website and look for these possible problems:

      - [ ] Links & buttons that are skipped with pressing Tab
      - [ ] The focus rectangle becoming invisible or hard to distinguish
      - [ ] Form controls that are inaccessible
      - [ ] Buttons & controls that can’t be activated
      - [ ] Hover functionality that isn’t activated when the element is focused with the keyboard

  - title: "Disable CSS"
    before: |
      **Not every human can see our website and not every person chooses to view our website with the design intact.**

      Disabling CSS helps us understand a few different things:

      1. The order of our content and how that affects a screen reader,
      2. The available text content of our site,
      3. How our website will be presented in the text-only mode of some browsers.

      *Some users may choose to disable the CSS or use a text-only browser because they are susceptible to seizures and want to avoid any flashing.*

      ## Use the Web Developer Toolbar

      You should have the Web Developer Toolbar installed already, if not you can get it here: [**Install the Web Developer Toolbar**](http://chrispederick.com/work/web-developer/).

      *You can use any browser you wish for this test—they’ll all function equally.*

      1. Click the “gear” icon that represents the Web Developer toolbar.
      2. Click the “CSS” tab.
      3. Click “Disable All Styles”.

      ![NASA’s website with CSS disabled](nasa-no-css.jpg)

      ## What problems might be found?

      Scroll through the website and look for these possible problems:

      - [ ] Poor hierarchy of headings or missing headings
      - [ ] Confusing order of content
      - [ ] Content that’s confusing without design or imagery
      - [ ] Improperly labeled form fields
      - [ ] Jumbled bunches of text

  - title: "Replace images with alt attributes"
    before: |
      **Not everybody can see the images on our websites.** We can help ourselves understand how a page will be read by a screen reader by replacing the images with their `alt` attributes. *We need to confirm our website makes logical sense and is still usable without images.*

      ## Use the Web Developer Toolbar

      Again, we’ll use the Web Developer Toolbar to peek at the alt attributes on our pages.

      *You can use any browser you wish for this test—they’ll all function equally.*

      1. Click the “gear” icon that represents the Web Developer toolbar.
      2. Click the “Images” tab.
      3. Click “Replace Images with Alt Attributes”.

      ![NASA’s website without image and alt attributes instead](nasa-alt.jpg)

      ## What problems might be found?

      Scroll through the website and look for these possible problems:

      - [ ] Important information that’s missing
      - [ ] Confusing information because there’s no text descriptions
      - [ ] Text that gets lost because the images are gone and the background color is showing instead
      - [ ] Broken layouts because they depended on the image taking up a certain amount of space

  - title: "Check colour contrast"
    before: |
      **Not every human is able to see a full range of colours and may have troubles detecting the different between certain colours—red-green deficiency is the most common.** We can simulate colour blindness using software tools that give us an idea of what our website might look like. *We must confirm that everything on the website still makes sense under simulated colour blindness.*

      ## Use Sim Daltonism

      We’re going to use [Sim Daltonism](https://michelf.ca/projects/sim-daltonism/) to simulate colour blindness. You should already have this tool on your computer, if you don’t go download it and install it.

      Sim Daltonism creates a window on our screen that changes the colours below to simulate colour blindness. Try out all the different types of colour blindness on your website because they all present slightly different problems.

      ![NASA’s website under simulated colour blindness](nasa-colour-blindness.jpg)

      ## What problems might be found?

      Move the Sim Daltonism window over every part of your website website and look for these possible problems:

      - [ ] That there aren’t interface elements that depend on colour to be understood, like error messages
      - [ ] That there’s sufficient contrast between the text colour and the background colours
      - [ ] That elements aren’t disappearing because the colours are too similar to each other
      - [ ] That all the text is still legible and understandable

  - title: "Run through Chrome Accessibility Tools"
    before: |
      The Chrome Accessibility Tools don’t look for one single problem they search the code for common problems that might be found and flag them. *Markbot uses the same tools internally for checking accessibility.*

      ## Open the Chrome Developer Tools

      Open Chrome and open the Developer Tools by pressing `⌘⌥I`. Once in the Developer Tools go to the “Audits” tab.

      ![Run the accessibility audit in Chrome Developer Tools](nasa-a11y-tools-start.jpg)

      Uncheck all the audits except the accessibility audit and run.

      ![The results of the accessibility audit on NASA’s website](nasa-a11y-tools-after.jpg)

      You should see results flagging different problems on the website. You can click into the problems and get more information.

      ## What problems might be found?

      The Chrome Accessibility audits will show a whole bunch of different problems that we may have caught already and some we may not have noticed:

      - [ ] Colour contrast between text and background
      - [ ] Missing ARIA landmark roles
      - [ ] Links that point to different locations but have the same text
      - [ ] Links that are missing some textual information
      - [ ] Non-unique ID attributes
      - [ ] Form fields missing associated labels
      - [ ] Groups of checkboxes and radio buttons outside `<fieldset>` tags
      - [ ] Auto-playing audio & video
      - [ ] Missing captions for audio & video
      - [ ] Improperly coded tables
      - [ ] Proper language coding on the `<html>` tag
      - [ ] Proper order of heading tags

  - title: "Test with VoiceOver"
    before: |
      **Not everybody is able to see to navigate our websites.** They might use a screen reader to navigate the website and activate the functionality. *We need to confirm that our website is logical and functional when using a screen reader.*

      ## Use Safari with VoiceOver

      MacOS has a screen reader built into it that we can use. I’ve found that it works best with Safari because of the tight OS integration. So run these tests in Safari.

      To enable VoiceOver press `⌘-Fn-F5`. Then follow the audible instructions. The first thing you’ll need to press is `⌘⌥⇧↓` to enter the website for navigation.

      Here are some of the important VoiceOver navigation commands:
    shortcuts:
      - keys: '`⌘ F5`'
        text: 'Turn VoiceOver on/off'
      - keys: '`⌃`'
        text: 'Pause VoiceOver'
      - keys: '`⌃⌥ ➔`'
        text: 'Move to next item'
      - keys: '`⌃⌥ ←`'
        text: 'Move to previous item'
      - keys: '`⌃⌥ U`'
        text: 'Open the rotor (Use arrow keys to navigate)'
      - keys: '`⌃⌥⌘ H`'
        text: 'Next heading (+ `Shift` for previous)'
      - keys: '`⌃⌥⌘ L`'
        text: 'Next link'
      - keys: '`⌃⌥⌘ G`'
        text: 'Next graphic'
      - keys: '`⌃⌥⌘ X`'
        text: 'Next list'
    after: |
      ## What problems might be found?

      Navigate around your website using VoiceOver and look for the following possible problems:

      - [ ] Links that aren’t described
      - [ ] Images that are missing descriptions
      - [ ] Images that are announced but shouldn’t be
      - [ ] Inaccessible content and functionality
      - [ ] Confusing order of the content and headings
      - [ ] Missing ARIA landmarks for navigation

quiz:
  url: "https://activities.learntheweb.courses/using-a11y-testing-tools/"
---
