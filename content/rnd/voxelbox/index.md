---
title: "Voxelbox: A Node-Based Voxel Erosion Editor"
date: 2026-07-12T09:55:00+02:00
draft: false
categories: ["Research & Development"]
tags: ["WebGPU", "Procedural Generation", "Simulation", "React"]
featured_image: "featured.png"
description: "A browser-based, node-based voxel erosion editor built with React, TypeScript, XYFlow, and WebGPU."
---

### The Project

**Voxelbox** is a node-based editor for sculpting voxel terrain through erosion.
Terrain noise, domain warping, hardness patterns, erosion, and rendering are all
nodes on a graph; the resulting dense volume is simulated and raymarched live on
the GPU through WebGPU.

![Voxelbox running the SDF Hoodoos template](featured.png)

The screenshot above is the *Hoodoos* template mid-simulation: rain and wind
parameters undercut a layered sedimentary slab over 120 frames, exposing harder
strata as softer material erodes away. Erosion, structure, and sediment are
separately parameterised, and the timeline scrubs the simulation rather than
merely playing back a bake.

Meshes can be exported out of the graph, so a result can leave the browser and
continue into a normal 3D pipeline.

*Private repository — requires a WebGPU-capable browser and GPU.*
