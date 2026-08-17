---
title: "Tabtop: Owning the First Screen You See"
date: 2026-07-12T10:05:00+02:00
draft: false
categories: ["Research & Development"]
tags: ["Web", "React", "Self-Hosting", "PocketBase", "Interface Design"]
featured_image: "featured.png"
launch_url: "https://cyberhirsch.github.io/Tabtop/"
description: "A self-hosted dashboard replacing the browser's new-tab page — a fine-grained widget grid on a PocketBase backend you run yourself, syncing live across devices."
---

### Why Bother

The new-tab page is, for most people, the single most frequently viewed screen on
their computer — and it is almost universally surrendered to whichever company
made the browser. It is a small piece of real estate with an outsized claim on
attention, and it is worth asking who it currently serves.

**Tabtop** takes it back. Not as a novelty skin, but as an actual dashboard with a
backend you own.

![A Tabtop dashboard: clock, greeting, quote, search, desktop icons and a to-do widget](featured.png)

### Two Kinds of Object

The design distinction I find most useful is between the two things that can live
on the surface:

- **Widgets** are framed and resizable — clocks (digital or analogue), weather,
  search bars, a to-do list. They have chrome because they have state.
- **Desktop icons** are frameless and clean — shortcuts to links and uploaded
  files. They have no chrome because they are just destinations.

Collapsing those two into one card type is the mistake most dashboard tools make,
and it produces a surface where a clock and a bookmark carry the same visual
weight despite doing entirely different jobs.

Positions live on a fine **64-column grid**, which gives close to pixel-level
control rather than the coarse three-across card layout that most new-tab
replacements settle for. Files can be dragged straight onto the dashboard to
upload and store them.

### Self-Hosted on Purpose

Layout and content are backed by a **PocketBase** collection rather than
`localStorage`, so the dashboard persists and syncs live across devices — and,
critically, across a database *you* run. There is an admin surface for user
management and plan status, and the deployment is two ordinary pieces: a
PocketBase instance and a static React build you can put behind any web server.

This matters more than it sounds. The moment a dashboard's data lives on someone
else's server, the list of every link you reach for daily is a behavioural profile
held by a third party. Since you host the instance, you have full control over the
data and the uploaded files, and the frontend reaches your backend through a single
environment variable.

Stack: React, Vite and Zustand, styled in plain modern CSS, with
`react-grid-layout` for the grid and PocketBase providing database, auth and
realtime. MIT licensed, with self-hosting instructions in the repository.

<div class="mt-8 mb-12">
    <a href="https://cyberhirsch.github.io/Tabtop/" class="inline-flex items-center px-8 py-4 text-lg font-bold text-white transition-all bg-primary-600 rounded-lg hover:bg-primary-500 hover:scale-105 shadow-xl shadow-primary-900/20">
        Launch Tabtop &nbsp; &rarr;
    </a>
</div>

[View source on GitHub &rarr;](https://github.com/cyberhirsch/Tabtop)
