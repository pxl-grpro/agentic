---
description: "Use when creating or updating Course/Modules/*/slides.adoc files that summarize a module as an Asciidoctor reveal.js presentation."
applyTo: "Course/Modules/*/slides.adoc"
---

# Slides Assembly For Modules

Use these rules when building the `slides.adoc` file inside a module folder.

## Purpose

A module `slides.adoc` is a single presentation file that summarizes the most important
subjects of that module, written with the Asciidoctor reveal.js converter syntax.
It is a summary for classroom use, not a full copy of the chapter content.

Official syntax reference: https://docs.asciidoctor.org/reveal.js-converter/latest/converter/features/[https://docs.asciidoctor.org/reveal.js-converter/latest/converter/features/^]

## File Location And Scope

- one `slides.adoc` file per module, placed directly in the module folder (for example `Course/Modules/02-variables/slides.adoc`)
- do not create per-chapter slide files
- the file is standalone: it does not `include::` chapter files, it summarizes them in the presenter's own slide content
- before editing, check whether `slides.adoc` already exists; update an existing placeholder in place instead of creating a duplicate file
- use `COURSE.md` and the actual module directory name as the source of truth for the module number, folder, and Dutch title; preserve the repository's path casing

## Required Document Header

Every `slides.adoc` starts with a title slide carrying the document attributes needed by the reveal.js backend:

```adoc
= <Module Title>
= Variabelen
:revealjsdir: https://cdn.jsdelivr.net/npm/reveal.js@4.5.0
:revealjs_theme: night
:source-highlighter: rouge
:icons: font
:revealjs_progress: true
```

- `<Module Title>` is the Dutch module title, matching the title used in `COURSE.md`
- keep this attribute set consistent across all modules unless a module has a proven reason to deviate

## Content Selection

- source material comes from the numbered chapter files of the module (files matching `^[0-9]`)
- exclude `00-objectives.adoc`, `pdf.adoc`, `slides.adoc`, and non-numbered files (`extra.adoc`, `labo.adoc`, `oefeningen.adoc`)
- for each included chapter, distill only the most important subjects: key concepts, definitions, and one short representative code example when useful
- do not paste full chapter text — summarize into concise bullet points a presenter can talk over
- keep the slide order aligned with the chapter order in the module (ascending numeric prefix)

## Slide Structure

- one top-level `==` slide per main subject; use vertical `===` sub-slides for a subject that needs more than one screen
- keep bullet lists short: a handful of concise bullets per slide, not full sentences copy-pasted from the chapter
- use `[.columns]` / `[.column]` blocks when comparing multiple short items side by side
- use `[.stretch]` above a slide title when the slide's main content is a code block or image that should fill the slide
- use AsciiDoc source listing blocks (`[source,csharp]` followed by `----`), matching the language used in the chapter
- use standard AsciiDoc admonitions (`NOTE`, `TIP`, `WARNING`) sparingly, only to highlight the same tips/pitfalls already flagged in the chapters
- add speaker notes with a `[.notes]` block when extra context helps the presenter but should not be visible on the slide itself:

```adoc
[.notes]
--
* extra context for the presenter
--
```

## Writing Style

- slide content is written in Dutch, using `je` form, consistent with the rest of the course (see `course-authoring.instructions.md`)
- code examples keep English identifiers and comments, consistent with the course's code example rules
- prefer keywords and short phrases over full sentences — slides are a visual aid, not the chapter text

## Validation

- check the document header, main-slide order, and absence of placeholder text before considering the deck complete
- when `asciidoctor` is available, compile the file to a temporary HTML output as a focused syntax check, for example:

```powershell
asciidoctor Course/Modules/02-variables/slides.adoc -o "$env:TEMP/module-slides.html"
```

- compilation checks AsciiDoc syntax only; it does not replace a reveal.js rendering check when the reveal.js toolchain is available

## Checklist

- title slide has the required reveal.js attributes
- one slide (or vertical slide group) exists per major subject from the module's numbered chapters
- no chapter is copy-pasted verbatim; content is distilled into slide-appropriate bullets
- code examples are short, tagged with the correct language, and directly support the point of the slide
- excluded files (`00-objectives.adoc`, `extra.adoc`, `labo.adoc`, `oefeningen.adoc`, `pdf.adoc`) are not summarized as slides
- the file compiles successfully with the available AsciiDoc toolchain, or the unavailable tool is reported
