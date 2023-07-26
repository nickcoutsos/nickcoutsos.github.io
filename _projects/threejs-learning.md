---
title: three.js animation
lead: >-
  Introduction to animation in three.js focussing on the use of timing functions
  to generate simple programmatic animation of various properties.
shortestDescription: lunch-and-learn
layout: post
timeframe:
  start: 2019
heroImageUrl: /assets/screenshots/threejs-presentation.png
heroImageAltText: >-
  The introductory slide of a presentation about threejs animation, depicting a
  shaded gray cube on a plane with cartesian axes off to the side.
thumbnailUrl: /assets/thumbnails/threejs-presentation.png
publicUrl: https://nickcoutsos.github.io/threejs-animation-lunch-and-learn/
---

---
<a target="_blank" href="{{ page.publicUrl }}">View the slideshow</a>

Browse through the slides with the left and right arrow keys. Head's up, I
didn't try very hard on the responsive design, so hit <kbd>f</kbd> to toggle
fullscreen. And don't use a phone for the same reason.

---

## Presentation Topics

* tweening and timing functions
* threejs basics - scene graph and transforms
* breakdown of animations from older presentations

## "Broadcast Mode" Feature

Technical constraints in the office meant presenting using Zoom to screen share
both to remote participants and to the projector viewed by the local. To avoid
latency and framerate problems ruining the experience I wanted to enable all
viewers to follow along by running the same animations in their browser.

### Synchronization

I used a free Heroku dyno to accept websocket connections from the audience and
myself, using a _JSON Web Token_ to identify my own connection as the presenter.
There is no real logic happening on the backend so specific auth claims aren't
needed; if a request has a valid token at all it can publish to topics.

After I've connected all other connected clients are notified that the
presentation is now "live" and prompted to synchronize with it.

On my own computer I can navigate through the slideshow and my current position
will be published to each of the clients which will automatically advance to the
same slide.

### Temporary de-sync'd viewing

Additionally, viewers are free to go back or skip ahead in the slides at their
leisure and this has two effects:

- automatically syncing to my slide position is disabled, with a button to let
  the user resume synchronized viewing when ready
- a "picture-in-picture" view of the synced presentation is shown in the corner

<img
  style="float: right; height: 6em; margin: 0 1em"
  src="/assets/thumbnails/threejs-presentation-resync.png"
  alt="An example of the picture-in-picture preview of the live presentation with prompt to re-synchronize"
/>

That picture-in-picture view is achieved with a simple `iframe` of the same web
app, with a flag to indicate that it should auto-connect to the live
presentation and disables user controls.
