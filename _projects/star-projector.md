---
layout: post
title: Star Projector
timeframe:
  start: 2016
  finish: 2017
# lead: Project star patterns based on authentic astronomical catalogues onto polyhedra to generate laser cutting templates.
lead: >-
  A deep dive into spatial transformations using _three.js_, projecting stars
  onto both the surface of a 3D polyhedron and a 2D laser cutting template.
repositoryUrl: https://github.com/nickcoutsos/star-projector
webAppUrl: https://nickcoutsos.gitlab.io/star-projector
thumbnailUrl: /assets/thumbnails/star-projector-built.jpg
heroImageUrl: /assets/jpg/star-projector-built.jpg
heroImageAltText: >-
  A completed star projector sitting in the corner of a room projecting stars
  and constellations onto nearby walls
---

## Overview

The goal of this project was to produce an aesthetically pleasing light display
that would project points of light which represent accurate star positions based
on data collected from astronomical catalogues.

The end result is a physical object, but most of the work took the form of
software I wrote to:

- take a selection of suitable stars (generally based on perceived brightness)
- project them onto the surface of a regular polyhedron
- generate a vector image from the polyhedron's 2-dimensional net suitable for
  laser cutting

I used _three.js_, a popular scene graph WebGL renderer, both to leverage its
_substantial_ library of 3d math operations and to help me visualize the end
results.

## Technical Challenges

Everything I learned in high school algebra I had forgotten by the time I began
work on this, so I'll skip that.

The projection code is written generically so that it can use arbitrary (convex)
meshes, but the ideal target is a [regular polyhedron]. These shapes are made of
uniform polygonal faces joined at uniform angles and by cutting certain edges it
is possible to unfold the mesh into a 2D net. There are optimal nets, but this
can also be defined programmatically.

<img
  style="background-color: white"
  src="/assets/star-projector-net-final.svg"
  alt="Projected laser cutting template. Red lines represent cuts all the way through the material, blue lines are etched to help folding"
  title="Projected laser cutting template. Red lines represent cuts all the way through the material, blue lines are etched to help folding"
/>

Joining these edges back together with a physical cutout can be challenging, so
my software will generate tabs that match an edge with its mate. This is just a
simple quadrilateral attached to select edges but because they will overlap the
adjoining face, any cutting geometry on that face that will intersect the tab
must be copied into the tab's position in the template.

## Presentation

Once I was satisfied with the projected template and submitted it for laser
cutting I began to think about how I'd like to share the experience with my
colleagues. I wanted a dynamic way to present not just the finished product but
the tooling I made to get me there.

Using _three.js_ to visualize projections meant that I already had renderable
and animatable 3D models, so I used _reveal.js_ to create a presentation in the
form of an HTML document, and embedded components of the app wherever it made
sense to show rather than tell.

One important idea I wanted to express was how to get the sharpest possible
edges for the projected image. I created an interactive document with controls
to adjust the size and position of a light source relative to an aperture. By
controlling each of these variables you can observe the change in sharpness of
the light's projection.

### Inline demo

Apparently you can embed JavaScript in SVG documents to make them dynamic, so
here's the shadow demo ripped from my presentation

<object data="/assets/shadows-demo.svg" type="image/svg+xml">
  <img src="/assets/shadows-demo-fallback.gif" />
</object>
<sub>
  <em>
    Drag the various elements to change their size and position. Click on the
    circle to toggle the lamp. (If embedding fails you should be seeing a
    <a href="/assets/shadows-demo-fallback.gif">pre-recorded animation</a>)
  </em>
</sub>

### Laser cutting simulation

Having so much of the work being driven by data was excellent. Even the laser
cutting template the software produced, exported as a vector image, could be
parsed in my presentation code. The resulting paths were used to animate a
simulated "laser" and trace the path of the cuts.

<img
  src="/assets/screenshots/star-projector-laser-demo.png"
  alt="Screenshot from presentation: a simulation of a laser traces the paths of a cutting template SVG"
  title="Screenshot from presentation: a simulation of a laser traces the paths of a cutting template SVG"
/>

It was goofy and inaccurate but it was fun. The "laser" flashes on and off when
alternating between cutting and travel movements. For extra fun I played music
from Star Wars and the occasional longer non-cutting travel would play a sound
effect of a TIE Fighter flyby.

[regular polyhedron]: https://en.wikipedia.org/wiki/Regular_polyhedron