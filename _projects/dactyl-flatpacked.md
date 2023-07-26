---
title: Dactyl Flatpacked
layout: post
shortestDescription: Ergonomic Keyboard
lead: >-
  My own take on an open source ergonomic keyboard, adapted to 2D for laser
  cutting and a better result than I could expect from my available 3D printer
  at the time.
timeframe:
  start: 2018
heroImageUrl: /assets/jpg/dactyl-flatpacked-assembled.jpg
heroImageAltText: >-
  The assembled keyboard sitting on my desk in the office. On the front of the
  keyboard's frame are thumb joysticks that I was experimenting with at the time
  to control the mouse cursor (left stick) and vertical/horizontal scrolling
  (right stick) which I quickly abandoned.
thumbnailUrl: /assets/jpg/dactyl-flatpacked-test-assembly.jpg
---
The inspiration for this project is the [Dactyl Keyboard] by Matthew Adereth, a
3D-printable ergonomic keyboard designed in Clojure.

When I first came across this project I had access to an older 3D printer that
didn't appear up to the task, and the included guide suggested that having a 3D
printing service produce the needed parts could be quite costly.

This project was largely an exploration in an alternative approach: using 2D
pieces slotted together to create the same 3D structure.

## TL;DR

It's a wildly different physical keyboard layout, but only because we've become
accustomed to keyboard layouts that designed for constraints that no longer
exist. It took some time to get used to this one, but I use a variation of this
layout on a daily basis and would recommend it to anyone.

## Materials

Throughout most of the development I expected to work with wood, at least as a
prototype. I could get sheets of balsa or basswood from craft stores and use a
coping saw to cut along the lines of a simple printed template. That went badly
so I went back to the success of my Star Projector laser cutting and had a local
service use the template to laser cut a sheet of acrylic.

<img
  src="/assets/jpg/dactyl-flatpacked-test-pieces.jpg"
  alt="A pile of small pieces of acrylic I had just picked up from the laser cutting service strewn about the surface of my desk"
  title="A pile of small pieces of acrylic I had just picked up from the laser cutting service strewn about the surface of my desk"
/>
<img
  src="/assets/jpg/dactyl-flatpacked-test-assembly.jpg"
  alt="Test assembly of the pieces to check the shape of the keyboard before gluing"
  title="Test assembly of the pieces to check the shape of the keyboard before gluing"
/>

## Designing in OpenSCAD

This is a "scripted CAD" tool for generating models using code. I dislike a lot
of it, frankly, as a programming language, but I really like the model-as-code
concept and the parametric design process.

The author of the original project used `scad-clj`, Clojure bindings for
OpenSCAD, which makes a number of improvements on the basic API as well as
enabling a functional programming paradigm, complicates the iteration process
by involving a Java-based pipeline for transpiling to native OpenSCAD code.

There was a lot of the original model I wouldn't be using anyway, so I opted to
re-write it in native OpenSCAD.

The challenges of this project come from thinking about different parts in terms
of how they'll be transformed into 3D space and relating parts in different
transformations so that I can avoid interference in tight spaces while staying
true to the original layout.

I've written more in my [dactyl-flatpacked] GitHub repository.

[Dactyl Keyboard]: https://github.com/adereth/dactyl-keyboard/
[dactyl-flatpacked]: https://github.com/nickcoutsos/dactyl-flatpacked