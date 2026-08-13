---
title: "Slitscan Studio: A Non-Destructive Slit-Scan Workstation"
date: 2026-07-12T10:00:00+02:00
draft: false
categories: ["Research & Development"]
tags: ["Video Processing", "Generative Art", "Optical Flow", "Web"]
featured_image: "featured.png"
description: "A browser-based, non-destructive slit-scan workstation: import video, position a slit, and generate slit-scan imagery in real time."
---

### The Project

Slit-scan photography builds an image from a single narrow column sampled across
many moments in time, so the horizontal axis of the result is time rather than
space. **Slitscan Studio** brings the technique into the browser as a proper
workstation rather than a one-shot effect.

![Slitscan Studio with a source clip loaded](featured.png)

The whole edit is a **recipe** — in/out range, slit position and width, rotation,
output aspect and size, interpolation engine — held separately from the footage.
Nothing is baked until render, so a slit can be repositioned and the result
regenerated without ever touching the source.

### Frame Interpolation

The interesting constraint is that a slit-scan is only as smooth as its temporal
sampling: 945 source frames stretched across a 3840-pixel-wide output needs
roughly 7× more frames than exist. Studio treats the interpolation engine as a
swappable choice, from simple linear blending through optical-flow methods
(DIS) to learned interpolators (RIFE, GIMM-VFI, PerVFI, FILM) — so the tradeoff
between speed and temporal fidelity is the artist's to make per shot.

[View source on GitHub &rarr;](https://github.com/cyberhirsch/Slitscan-Studio)

*Source-only — no public build yet.*
