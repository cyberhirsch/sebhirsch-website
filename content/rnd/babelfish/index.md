---
title: "Babelfish: Clause-Streaming Offline Voice Translation"
date: 2026-07-18T12:00:00+02:00
draft: true
categories: ["Research & Development"]
tags: ["Kotlin", "Android", "Speech Recognition", "Machine Translation", "On-Device AI"]
description: "An Android voice translator that runs entirely on-device, releasing speech a clause at a time so the translation has enough context to be grammatical."
---

### The Project

**Babelfish** is an offline voice translator for Android — English, German, and
Turkish — where the interesting problem is not recognition or translation but
*when to translate*.

The pipeline is straightforward on paper: Vosk decodes microphone audio
continuously on-device, a stable-prefix committer confirms words once they stop
changing across partial hypotheses, ML Kit translates, and Android's offline TTS
speaks the result.

### Why Clauses

The naive version of this feeds each committed word to the translator as it
arrives, and the output is unusable. A translation model given one word at a time
has no context to work with: German loses case agreement, and Turkish — being
verb-final — cannot place the verb *at all* until the source clause is finished.

So a **clause assembler** sits between the committer and the translator. It
buffers confirmed words and releases them one clause at a time, triggered by
terminal punctuation, a twelve-word cap, or a pause in speech. Because Vosk's
small language packs emit lowercase text without punctuation, each clause is
capitalised and terminated before it reaches the translator. This single stage is
what makes the difference between word salad and readable output.

### Offline by Construction

Each input language's Vosk pack (35–45 MB) is downloaded once from the official
model repository, after which recognition needs no network at all. The download
is staged in a temporary directory and moved into place only after verification,
so an interrupted install cannot leave behind a pack that looks complete but
isn't. Translation models are likewise fetched once and then run on-device.

ML Kit is deliberately a placeholder: its `TranslationEngine` interface is the
seam where an open-weight Bergamot JNI backend with OPUS-MT language packs is
intended to replace it.

*Prototype — source-only, no public build.*

[View source on GitHub &rarr;](https://github.com/cyberhirsch/babelfish)
