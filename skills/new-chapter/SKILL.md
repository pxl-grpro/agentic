---
name: new-chapter
description: Scaffold a new AsciiDoc chapter file that complies with the course structure defined in AGENTS.md, and register it in COURSE.md. Use this skill whenever the user asks to create, add, write, or start a new chapter, section, or lesson — even if they don't say "scaffold" or "AsciiDoc". Examples: "add a chapter about exceptions", "create a new section on APIs", "start chapter 3 in module 5", "write the intro chapter for loops".
---

# new-chapter

Create a new AsciiDoc chapter file that follows the course structure and writing style.

## Steps

1. **Consult COURSE.md** — read `COURSE.md` to find the correct module folder, numeric prefix for the new chapter file, and the exact chapter title. Never invent a number or title that contradicts COURSE.md.

2. **Determine the file path** — construct the path as:
   `Course/Modules/<module-folder>/<nn>-<kebab-title>.adoc`
   - use the next available numeric prefix in the module
   - filename must be kebab-case, English words only

3. **Ensure the images folder exists** — if `Course/Modules/<module-folder>/images/` does not exist, create it (place a `.gitkeep` inside so it is tracked by git).

4. **Write the file** — the file MUST start with this exact header (fill in Module Name and Chapter Title):

```adoc
= <Course Title>
Graduaat programmeren
:doctype: article
:source-language: csharp
:imagesdir: images
:icons: font
:sectnums:
:toc: macro
:toc-title: Inhoudsopgave
:toclevels: 3
:nofooter:
:sectlinks:

[discrete]
== <Module Name>
[discrete]
=== <Chapter Title>
In dit hoofdstuk leer je ...

'''

toc::[]

== <Eerste sectietitel>
```

   Writing rules (drawn from AGENTS.md):
   - Complete `In dit hoofdstuk leer je ...` with a concrete statement about what the reader will learn
   - Body text is written in Dutch, `je`-form, professional but approachable
   - Structure: introduction → explanation → example → practical usage
   - Code blocks use `[source,<lang>]` (e.g. `csharp`, `json`, `bash`) with English variable names and English comments — never Dutch identifiers inside code
   - External links must include the `^` modifier: `https://example.com[https://example.com^]`
   - Unless this is a labo chapter (title contains "Labo") or a module objectives/overview file (`00-`), end the file with `== In het kort` followed by a short bullet list summarising the key takeaways

5. **Draft starter content** — after the header, write at least the first section with a short orientation paragraph and one concrete example (code block if appropriate). Leave a `// TODO` comment where further sections are expected so the author knows where to continue.

6. **Update COURSE.md** — add a row for the new chapter in the correct position. Set status to `in progress`. Use the same column format as existing rows:
   `| <#> | <folder> | <Module title> | <filename> | <Chapter title> | in progress |`

7. **Update pdf.adoc** — open `Course/Modules/<module-folder>/pdf.adoc` and add an entry for the new chapter:
   - Append `<<<` as a page break separator
   - Add the Dutch `==` section heading that matches the chapter's first top-level section title
   - Add the include directive: `include::<filename>[leveloffset=+1,lines=24..-1]`
   - Insert the entry after the last existing numbered chapter entry, maintaining numeric order
   - If `pdf.adoc` does not yet exist for the module, create it using the standard template from the `## PDF Assembly File` section 

8. **Report** — tell the user the file path created and confirm the COURSE.md row and pdf.adoc entry were added.
