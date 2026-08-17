---
title: "Sky Lanterns: A Sky Full of Practical Light Sources"
date: 2011-01-01T11:36:00+01:00
draft: false
categories: ["Personal & Technical Studies"]
tags: ["CGI", "Lighting", "Particle Simulation", "Atmospherics"]
featured_image: "thumb_Sky Lanterns.jpg"
description: "A 2011 CG study in the hardest kind of lighting problem — hundreds of individually emissive, individually moving light sources over a lit city at night."
---

![Sky Lanterns](thumb_Sky Lanterns.jpg)

### The Study

A night sky over a riverside city, filled with hundreds of rising paper lanterns.
The picture is pleasant. The problem behind it is not, and that is why I made it.

Almost every lighting exercise a student is given has a small, fixed number of
sources: a key, a fill, a rim, perhaps a practical in shot. This scene has
**hundreds of sources, all of which are also moving objects, all of which are also
translucent**. Each lantern is simultaneously an emitter, a piece of geometry lit
by its neighbours, and a diffuser scattering its own flame outward through paper.
None of those three roles can be solved in isolation.

Layered underneath is a second lighting environment that has to hold up
independently — a city at night, warm sodium windows reflecting off water, its own
falloff and its own haze — and the two have to read as one atmosphere. The
sequence also had to move: the lanterns rise on a simulation with enough drift and
irregularity to look released by individual hands rather than instanced by a
computer, which is a particle problem masquerading as an aesthetic one.

### Why It Still Matters to Me

This is from **2011**. That date is most of the point.

Today a scene like this is a reasonable ask of a production path tracer: many
emissive surfaces with importance sampling and volumetric scattering is a solved
category, and the render time is the main cost. In 2011 it was not, and every part
of it — the emitters, the translucency, the atmospheric depth, the interaction
between the lantern field and the city below — had to be reasoned about, split
apart, and reassembled rather than simply asked for.

I keep it on this site as a reminder of something worth saying to students who have
only ever worked inside a modern renderer: the tool absorbed the difficulty, it did
not remove it. Knowing *which* problem the software is solving on your behalf is
still the difference between directing an image and pressing render.
