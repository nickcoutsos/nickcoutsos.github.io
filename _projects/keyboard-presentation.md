---
layout: post
title: Keyboard Presentation
timeframe:
  start: 2018
lead: >-
  A stylized showcase of the world of keyboard ergonomics and my fondness for
  using three.js in presentations.
heroImageUrl: /assets/screenshots/keyboard-presentation.png
heroImageAltText: >-
  A 3D rendering of the assembled dactyl-flatpacked keyboard with keycaps added
  to better demonstrate how the 2D pieces create a concave keywell structure.
thumbnailUrl: /assets/thumbnails/keyboard-presentation.png
publicUrl: https://nickcoutsos.github.io/keyboard-presentation/
---

<a target="_blank" href="{{ page.publicUrl }}">View the slideshow</a>

I put together a presentation (early/mid 2018?) to share my side project:
building an ergonomic keyboard. It takes the form of a web-based slideshow that
uses WebGL heavily to show off my experience with _three.js_ and because it was
a great way to visually demonstrate data-driven concepts.

Going through it on your own now isn't the same as when I presented it live but
if you're looking at this now it's because I wanted to show you some of the cool
technical aspects of this presentation:

- data-driven 3D rendering of keyboard layouts using three.js
- "slideshow engine" inspired by reveal.js, but focusing on events that I can
  use for programmatic transitions
- tweening key positions/orientations between radically different keyboard
  layouts
- Mixing HTML/WebGL to display an on-screen ruler: hold any two keys on a slide
  that's displaying a keyboard layout and see how far apart those keys are.

---

### Keyboard Morphing Effect

I made a clip of just the transitions between keyboard layouts because it's fun
to look at.

<video autoplay muted loop style="border-radius: 0.25em; width: 100%">
  <source src="/assets/keyboards-morph-480p.mp4">
</video>
