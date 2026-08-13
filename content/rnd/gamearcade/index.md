---
title: "GameArcade: A Shared Controller Layer for Browser Games"
date: 2025-11-07T12:00:00+02:00
draft: false
categories: ["Research & Development"]
tags: ["Game Development", "Web", "Input", "API Design"]
featured_image: "featured.png"
launch_url: "https://cyberhirsch.github.io/GameArcade/"
description: "A browser arcade with a single shared input layer — configure controller profiles once and every game on the platform inherits them."
---

### The Project

Browser games each reinvent input handling, which means every one of them has its
own idea of what the buttons do and none of them remember your gamepad.
**GameArcade** pulls that concern out into a platform-level layer: controller
profiles and device assignments are configured once, for up to four players, and
every game hosted on the arcade reads from the same configuration.

![The GameArcade controller setup](featured.png)

Custom profiles can be created and remapped freely; defaults are provided and
protected from editing so there is always a known-good fallback. A documented API
lets a game opt into the layer rather than parsing raw key events itself.

### Live Experiment

<div class="mt-8 mb-12">
    <a href="https://cyberhirsch.github.io/GameArcade/" class="inline-flex items-center px-8 py-4 text-lg font-bold text-white transition-all bg-primary-600 rounded-lg hover:bg-primary-500 hover:scale-105 shadow-xl shadow-primary-900/20">
        Open GameArcade &nbsp; &rarr;
    </a>
</div>

[View source on GitHub &rarr;](https://github.com/cyberhirsch/GameArcade)
