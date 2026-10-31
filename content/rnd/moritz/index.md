---
title: "Moritz: A 3D Suite for People Who Think in 3ds Max"
date: 2026-10-31T09:00:00+01:00
draft: false
categories: ["Research & Development"]
tags: ["3ds Max", "C++", "Python", "Open Source", "3D Tools"]
featured_image: "featured.png"
description: "A free 3D creation suite that works the way 3ds Max users already think: Max navigation and keys, the Command Panel, Editable Poly and a real modifier stack."
---

### The Premise

A lot of 3ds Max users have tried to leave it. The reasons to go are good ones: open
3D software today renders, sculpts, animates and builds procedural geometry as well as
anything you can rent, for free. The reasons people come back are almost always the
same. It is not that the new tool can't do the work. It is that their hands no longer
know where anything is.

I read through thirteen years of switching stories, from forum threads and feature
requests to archviz post-mortems. Keymaps and navigation come up in more than half of
them. After that come the things a Max user reaches for without thinking and doesn't
find: an Edit Poly modifier in the middle of the stack, primitives you can still
change after you've made them, and proper spline tools.

**Moritz** is my answer: a complete, free 3D creation suite, shaped for people who
think in Max.

### What It Is

It is not a skin and not a keymap preset. It is its own application, with changes
reaching down into the core where they had to.

- **Your hands work on day one.** Max navigation and shortcuts, W/E/R, 1–5 for
  sub-object levels, the right-click quad menu, Transform Type-In, Align, Clone with
  Shift+drag. A Max keymap and a Moritz keymap are one click apart.
- **The Command Panel.** Create, Modify and Utilities. Create lists the object types
  in Max's order, and you drag them out with parameters you can still edit afterwards.
- **Editable Poly and Edit Poly.** Vertex, Edge, Border, Polygon and Element, with
  Max's tools under Max's names: Extrude, Chamfer, Connect, Swift Loop, Target Weld,
  Bridge, Smart Extrude, smoothing groups.
- **A real modifier stack.** Edit Poly sits anywhere in the stack while the modifiers
  below stay live, with Collapse To, instanced modifiers and Show End Result. Several
  other Max modifiers (Edit Spline, Cap Holes, ProOptimizer, Quadify Mesh and more)
  are native too.
- **Everything else a full suite needs.** Path-traced and real-time rendering,
  sculpting, animation and rigging, node-based procedural geometry, simulation and
  compositing.

![Edit Poly at polygon level in the Modify tab, with Bend and the Teapot below it in the stack](modify.png)

### What It Isn't

Moritz only adopts what Max genuinely does better. Where the existing way already
works well, such as UV editing, the node systems or the renderers, I left it alone.
It is not an attempt to clone 3ds Max; it closes the gaps that keep sending Max users
back.

### Who It's For

- **3ds Max users** in archviz, games and product design who want out of the
  subscription, or who have tried other free tools and kept bouncing off the
  interface.
- **Studios and classes** that want one free tool their Max people can use from the
  first day.
- **Students who learned Max** and would rather not start over.

### Status

This is **0.2, an early alpha**, for Windows 10/11. The modeling workflow is there and
the automated tests pass; expect rough edges everywhere else.

### Credit

Moritz is based on [Blender](https://www.blender.org), the free and open source 3D
creation suite, and is free software under the same GNU GPL. It reads and writes
`.blend` files. Moritz is not made or endorsed by the Blender Foundation or Autodesk.

<div class="mt-8 mb-12">
    <a href="https://github.com/cyberhirsch/moritz/releases/tag/v0.2.0" class="inline-flex items-center px-8 py-4 text-lg font-bold text-white transition-all bg-primary-600 rounded-lg hover:bg-primary-500 hover:scale-105 shadow-xl shadow-primary-900/20">
        Download Moritz 0.2 &nbsp; &rarr;
    </a>
</div>

[Join the Moritz Discord &rarr;](https://discord.gg/cA9x2yprmG)
