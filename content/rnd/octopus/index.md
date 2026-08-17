---
title: "Octopus: Rigging an Animal With No Skeleton"
date: 2021-01-01T12:00:00+01:00
draft: false
categories: ["Personal Project"]
tags: ["3D Modeling", "ZBrush", "Sculpting", "Rigging", "Character Design", "Anatomy"]
featured_image: "seb-hirsch-002.jpg"
description: "A character study of the octopus — an animal whose anatomy breaks nearly every assumption built into standard character rigging."
---

![Final render](seb-hirsch-002.jpg)

### Why the Octopus

It is my favourite animal, which is the honest reason. But it is also, from a
technical standpoint, close to the worst possible subject for a character
pipeline — and that turned out to be the more interesting reason to spend a year
on it.

Every convention in character rigging assumes a **skeleton**: a chain of rigid
segments joined at points that rotate. Bipeds, quadrupeds, birds, fish, dragons —
all of it is that same assumption with different proportions. The octopus has no
skeleton at all. Its arms are *muscular hydrostats*: constant-volume structures
that bend, extend, shorten and twist at any point along their length, with no
joints and no privileged axis of articulation.

You cannot rig that correctly. You can only decide, deliberately, how you are
going to be wrong — and that decision is the actual work.

### Sculpting

The process began in **ZBrush**, capturing the anatomy and the fluid forms. The
significant time went into two things: the skin, which is not a texture but an
active organ of camouflage covered in papillae the animal can raise and lower at
will; and the arms, where the sucker geometry has to diminish smoothly along the
taper while staying individually readable at the tips.

![ZBrush sculpt](seb-hirsch-zbrush.jpg)

### Retopology and Rig

After the high-poly sculpt came retopology and a custom rig built for extreme
flexibility rather than for anatomical accuracy — because in this case those two
goals genuinely conflict. A dense joint chain per arm approximates continuous
bending closely enough to be directable, and directability is the property that
matters: a rig an animator cannot pose is a failed rig regardless of how faithful
its underlying model is.

That trade-off is the thing I actually took away from the project, and the reason
I still use it as a teaching example. The goal was a character that felt
**anatomically grounded and expressive at the same time**, and the honest finding
is that those two requirements pull in opposite directions, that the resolution is
a judgement call rather than a technique, and that the judgement has to be made
consciously by somebody who understands what is being given up.
