---
layout: post
title: Keymap Editor
shortestDescription: passion project/obsession
lead: A web-based editor for ZMK keymaps with a GitHub integration
timeframe:
  start: 2020
  finish: ∞
thumbnailUrl: /assets/thumbnails/keymap-editor-dialog.png
publicUrl: https://nickcoutsos.github.io/keymap-editor/
---

<a target="_blank" href="{{ page.publicUrl }}">Try the app</a>

<img alt="Shows a screenshot of the Keymap Editor application featuring a graphical layout of the Corne Keyboard with a keymap loaded from the nickcoutsos/keymap-editor-demo-crkbd GitHub repository." class="only-in-dark-theme" srcset="/assets/screenshots/editor-screenshot-dark.png" />
<img alt="Shows a screenshot of the Keymap Editor application featuring a graphical layout of the Corne Keyboard with a keymap loaded from the nickcoutsos/keymap-editor-demo-crkbd GitHub repository." class="only-in-light-theme" srcset="/assets/screenshots/editor-screenshot-light.png" />

## Context

This project falls into a very specific niche and describing requires the right
amount of context.

- "enthusiast-level" computer keyboards (bear with me) often run firmware with
  advanced functionality and programmability
- a popular firmware, QMK, has a number of first/third-party tools that allow
  graphical keymap editing rather than via C code
- another firmware, ZMK, is known for its Bluetooth support but lacks the same
  ecosystem for tooling

This has been my main personal project, off and on, since mid-2020 or so. It has
changed quite a bit both in terms of feature set and implementation, has gained
traction with a number of ZMK users, and forms the basis of the editors for a
number of commercial products.

## Overview

ZMK Keymaps are described using [devicetree] syntax, which is normally used to
describe hardware for embedded systems. I started this project while I was still
becoming familiar with ZMK and devicetree syntax so that I could:

- rapidly test keymap changes
- avoid human error from manual edits
- preserve readability of devicetree source

## Technical Considerations

To properly convey this in terms of features you'd really need to review the
capabilities of ZMK and try the editor out for itself so I'm going to try to
keep this more abstract.

### GitHub API Integration

The preferred method of building ZMK is via GitHub Actions so that setting up a
dev environment is only necessary to work on ZMK itself. I integrate with GitHub
to enable editing without the need to clone and push changes back to the remote.

**Other Integrations**

More recently I've added a way to "import" and "export" keymap data from the
clipboard as well as via the [File System Access API] (where supported) for
users who don't want to use GitHub.

This also serves as a proof of concept for an adapter pattern that will allow me
to support Web Bluetooth-based keymap changes once ZMK offers a protocol.

### AST Manipulation

I leverage the [tree-sitter] library and a [devicetree grammar] to parse and
modify existing keymap files rather than spitting out a templated file on save.
This means that even if my editor doesn't support a new ZMK feature directly,
users can add it in code and still use the app to edit other parts of their
keymaps without the app clobbering the custom work.

This is my first project where I programmatically modify source code via its
syntax tree, so I also wrote a [helper app](https://github.com/nickcoutsos/tree-sitter-devicetree-viewer/)
to help me quickly look up the AST node for an arbitrary point in the devicetree
code and vice-versa.


[devicetree]: https://en.wikipedia.org/wiki/Devicetree
[devicetree grammar]: https://github.com/joelspadin/tree-sitter-devicetree
[tree-sitter]: https://github.com/tree-sitter/tree-sitter/
[File System Access API]: https://developer.mozilla.org/en-US/docs/Web/API/File_System_Access_API