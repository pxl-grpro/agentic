---
name: validate-chapter
description: Check an existing AsciiDoc chapter file against the course quality rules and report any violations as a PASS/FAIL table. Use this skill whenever the user asks to check, review, validate, audit, or verify a chapter — or asks whether a file follows the course rules. Examples: "does this chapter comply?", "review my adoc file", "check chapter quality", "validate the new section", "is this file correct?", "run a quality check on this chapter".
---

# validate-chapter

Audit an existing AsciiDoc chapter file against the course quality rules and produce a PASS/FAIL report.

## Input

The user provides a file path, or the file is currently open/selected in the IDE. If no file is specified and none is clearly implied, ask the user which file to check before proceeding.

If the file does not exist at the given path, report that immediately and stop — do not attempt the checks.

Read the full file content before running any checks.

## Checks to perform

Run every check below. For each one, report PASS or FAIL with a short explanation of what was found.

### 1. Standard document header
- First line is `= {Course Title}`
- Second line is `Graduaat programmeren`
- All required attributes are present: `:doctype:`, `:source-language:`, `:imagesdir:`, `:icons:`, `:sectnums:`, `:toc:`, `:toc-title:`, `:toclevels:`, `:nofooter:`, `:sectlinks:`

### 2. Discrete headings
- Module name is a `[discrete]` `==` heading
- Chapter title is a `[discrete]` `===` heading immediately after

### 3. Opening sentence
- The first paragraph after the chapter title starts with `In dit hoofdstuk leer je`

### 4. Thematic break and TOC
- A `'''` line appears before `toc::[]`

### 5. Body language
- Body text is written in Dutch (spot-check: flag any clearly non-Dutch paragraphs with the line number)

### 6. Spelling
- Scan body text (excluding code blocks) for obvious Dutch spelling errors — list any misspelled words with the suggested correction. If none found, mark PASS.

### 7. Code blocks tagged
- Every code block uses an explicit `[source,<lang>]` tag — no untagged fences or bare `----` blocks

### 8. No Dutch identifiers in code
- Spot-check code blocks: flag any Dutch variable names, method names, or identifiers

### 9. External links
- Every external `http://` or `https://` link ends with the `^` modifier inside `[...]`

### 10. Summary section
- File ends with `== In het kort` followed by a bullet list
- Skip this check (mark N/A) if:
  - the chapter title contains "Labo", or
  - the file is a module objectives/overview file (filename starts with `00-`)

### 11. File and folder naming
- File name is kebab-case, English words only, with a numeric prefix (e.g. `03-exception-handling.adoc`)
- File lives inside `Course/Modules/<module-folder>/`

### 12. COURSE.md registration
- Read `COURSE.md` and confirm this chapter file is listed with the correct module folder and title

## Output format

Print a Markdown table:

| Check | Result | Notes |
|-------|--------|-------|
| Standard header | PASS/FAIL | ... |
| Discrete headings | PASS/FAIL | ... |
| Opening sentence | PASS/FAIL | ... |
| Thematic break + TOC | PASS/FAIL | ... |
| Body language (Dutch) | PASS/FAIL | ... |
| Spelling | PASS/FAIL | ... |
| Code blocks tagged | PASS/FAIL | ... |
| No Dutch identifiers | PASS/FAIL | ... |
| External links (^) | PASS/FAIL | ... |
| Summary section | PASS/FAIL/N/A | ... |
| File naming | PASS/FAIL | ... |
| COURSE.md entry | PASS/FAIL | ... |

After the table, list only the FAILs with a brief, actionable fix suggestion for each.

If all checks pass (no FAILs), say so clearly.

## COURSE.md status update

After printing the report, **ask the user** whether to update the chapter's status in COURSE.md:
- If there are no FAILs → offer to set status to `done`
- If there are FAILs → offer to set status to `failed`

Only update COURSE.md if the user confirms.
