---
title: "This Website: Reverse-Engineering My Way Off Adobe Portfolio"
date: 2026-01-11T23:25:00+01:00
draft: false
categories: ["Research & Development"]
tags: ["Hugo", "Static Site Generator", "Web Design", "AI-Assisted Development", "Design Systems"]
featured_image: "images/portfolio/thumb_adobe_reverse.png"
description: "Moving my portfolio off a proprietary platform by reverse-engineering its design into Hugo and Tailwind — and treating the AI-assisted rebuild as a method worth documenting."
---

### The Motivation

Adobe Portfolio was a reasonable place to start and a bad place to stay. It gave
me a presentable site quickly; it also gave me a hard ceiling on customisation, a
subscription, and a portfolio that existed at somebody else's discretion.

For a Technical Director that is uncomfortable. For someone who teaches students
to own their tools it is difficult to defend. So I rebuilt the site from scratch
in **Hugo** and **Tailwind CSS**, and cancelled the subscription.

### Visual Analysis: From "Monolithic" to "Six Bars"

The rebuild started as a design analysis rather than a port, because I wanted to
understand what the original layout was actually doing before replacing it.

The Adobe Portfolio design was **monolithic**: a single background colour across
the entire page, relying on spacing and bold typography alone to separate
components. It works, and it has a specific failure mode — everything sits on one
plane, so hierarchy has to be carried entirely by type size, and the page reads as
a list.

![The original projects view](projects_old.png)

![The original about page](about_old.png)

The replacement uses what I ended up calling **six bars**: the page is broken into
distinct horizontal strips, each with its own tonal value, producing a rhythm
closer to a title sequence than to a document.

1. **Nav bar** — deep black foundation.
2. **Section banner** — medium grey introduction strip.
3. **Content body** — high-contrast dark grey narrative area.
4. **Imprint segment** — the legal footer bar.
5. **Social segment** — the interactive connection strip.
6. **Copyright segment** — the closing anchor.

The gain is that hierarchy becomes *structural* rather than typographic. A visitor
knows where they are on the page from tonal value alone, before reading anything.

### The Rebuild as Method

I did the rebuild with AI assistance — Antigravity — and I want to describe that
honestly, because "I used AI" is not a finding and the specifics are.

Three things were genuinely useful:

- **Extracting a single source of truth.** My eleven-page career history existed as
  a PDF. Parsing it into a structured `information.md` gave every project and
  academic milestone one canonical record that the templates read from. The model
  was good at the tedious structuring; the editorial decisions about what counted
  as a project remained mine, and had to.
- **Settling a voice problem.** The site needed to be approachable on the homepage
  and authoritative in the biography, which are different registers. Working
  through it produced a deliberate split — first person for the greeting, third
  person for the professional record — rather than an unexamined mixture.
- **Enforcing standards mechanically.** Every key image standardised to a **3:2
  aspect ratio** with top-anchored cropping. That is exactly the kind of rule that
  is easy to state, tedious to apply across a hundred assets, and instantly
  visible when it slips.

What did not transfer was judgement. The six-bar structure, the decision to leave
Adobe, and every choice about what belongs on the site came from looking at the
old design and disliking specific things about it. The assistance accelerated
execution; it did not supply the argument.

That distinction is the reason this entry is here at all. I teach students to work
with these tools, and the useful lesson is neither "it writes the site for you" nor
"it is worthless" — it is that the tool is fast at the parts you can specify, and
that specifying them remains the job.

### The Result

A static site I own completely: Hugo, Tailwind, plain Markdown content, versioned
in git, built and deployed automatically on push. No subscription, no platform, and
no part of it that I cannot open in a text editor.
