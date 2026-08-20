---
applyTo: "Course/Modules/**/*.md"
description: "Rules for consolidating a course module's AsciiDoc chapters into one Markdown source for a custom Copilot or coding agent."
---

# Course Module Markdown

When creating or updating a consolidated Markdown source for a course module:

## Source Selection

- Consult `COURSE.md` for the chapter order and titles.
- Include the listed instructional chapters, objectives, lab, and exercises.
- Always exclude `pdf.adoc`, `slides.adoc`, and `extra.adoc`.
- Never modify the original `.adoc` files.

## Markdown Structure

- Use exactly one level-1 heading: the module name.
- Use level-2 headings for chapters, containing only the chapter name. Do not prefix them with the module name.
- Use level 3 or deeper for all content headings inside a chapter.
- Preserve chapter order and all instructional content, including code, exercises, solutions, links, admonition text, and media references.
- End every chapter with `---`, except the final chapter.

## Conversion Rules

- Convert `[source,csharp]` blocks to fenced code blocks such as ```` ```csharp ````.
- Convert AsciiDoc tables to Markdown tables when they contain text or data.
- Convert multi-image AsciiDoc tables to an HTML table with one `<tr>` and one `<td>` per image so the images remain side by side:

```html
<table>
<tr>
<td><img src="images/example-a.png" alt="..."></td>
<td><img src="images/example-b.png" alt="..."></td>
</tr>
</table>
```

- Preserve image paths, order, and alt text. Convert standalone `image::` entries to Markdown images or equivalent HTML when alignment, dimensions, or links require it.
- Convert admonitions to readable Markdown blockquotes, retaining their labels and text.
- Remove document attributes, TOC directives, include directives, and layout-only AsciiDoc separators.
- Do not rewrite, correct, translate, or improve the source wording or code.

## Validation

Before reporting completion, verify:

1. Exactly one H1 exists and it is the module name.
2. H2 headings match the included chapter list and order from `COURSE.md`.
3. No internal heading is H1 or H2.
4. Every non-final chapter is followed by `---`; the final chapter is not.
5. No `pdf.adoc`, `slides.adoc`, or `extra.adoc` content is present.
6. No unresolved `include::`, `image::`, `[source,`, or document-attribute directives remain.
7. Every multi-image source table has a side-by-side HTML image table in Markdown.
8. Source `.adoc` files are unchanged.
