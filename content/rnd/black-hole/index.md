---
title: "Black Hole: Ray-Traced Geodesics Around an Event Horizon"
date: 2026-04-30T11:05:44+02:00
draft: false
categories: ["Research & Development"]
tags: ["General Relativity", "Ray Tracing", "WebGPU", "Physics", "Experiments"]
featured_image: "featured.png"
launch_url: "https://cyberhirsch.github.io/Experiments/04_Black Hole/Black Hole_v001.html"
description: "An accretion disk and event horizon rendered by integrating light paths through curved spacetime rather than tracing them in straight lines."
---

### The Experiment

Every conventional renderer assumes light travels in straight lines. Near a black
hole that assumption fails, and the failure *is* the image: the accretion disk
behind the hole is bent up and over the top into view, the disk in front is bent
under, and the two join into the halo that has no counterpart in flat-space
optics.

**Black Hole** drops the straight-line assumption. Rather than intersecting rays
with geometry, each ray is **numerically integrated as a geodesic** through
curved spacetime, stepping along the path a photon would actually take.

![A ray-traced black hole with its accretion disk](featured.png)

### What Falls Out of It

Nothing in this scene is an artistic effect layered on afterwards — each feature
is a consequence of the integration:

- **Gravitational lensing** of the disk and the background starfield, including the photon ring where paths orbit the hole before escaping.
- **The shadow** — not a black sphere drawn at the horizon, but the set of directions whose geodesics terminate at the singularity instead of reaching infinity.
- **Relativistic beaming**, which is why one side of the disk is conspicuously brighter: material approaching the viewer is Doppler-boosted, material receding is dimmed.

The cost is that every pixel requires an ODE integration rather than a ray-object
intersection, which is precisely the kind of embarrassingly parallel, arithmetic-heavy
workload a GPU is built for.

### Live Experiment

<div class="mt-8 mb-12">
    <a href="https://cyberhirsch.github.io/Experiments/04_Black%20Hole/Black%20Hole_v001.html" class="inline-flex items-center px-8 py-4 text-lg font-bold text-white transition-all bg-primary-600 rounded-lg hover:bg-primary-500 hover:scale-105 shadow-xl shadow-primary-900/20">
        Launch Black Hole &nbsp; &rarr;
    </a>
</div>

*(Requires WebGL2 / WebGPU. Best experienced on desktop.)*

[View the Experiments collection &rarr;](https://github.com/cyberhirsch/Experiments)
