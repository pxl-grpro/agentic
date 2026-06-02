---
name: generate-objectives
description: Use when creating or updating a 00-objectives.adoc file for a course module so it matches the repository structure, Dutch writing style, and measurable objective phrasing.
---

# generate-objectives

Create or update a `00-objectives.adoc` chapter for a module using the standard course format and objective phrasing.

## Scope

Use this skill for files under `Course/Modules/*/00-objectives.adoc`.

## Required Output Structure

The file should follow this exact section order:

1. Standard AsciiDoc header
2. Discrete module title (`== <Module Name>`)
3. Discrete subsection `=== Doelstellingen`
4. One short orientation sentence in Dutch (`In dit hoofdstuk leer je wat je na het afronden van deze module kunt doen.`)
5. The separator line (`'''`)
6. `toc::[]`
7. `== Overzicht` with a concise module summary in Dutch
8. `== Leerdoelstellingen`
9. Objective list introduced by `Na het afronden van deze module kan je:`

## Header Template

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
```

## Objective Phrasing Rules

- Write all prose in Dutch and use the `je` form.
- Formulate each objective from student behavior (implicit form: `je kan ...`; attitude goals: `je wil ...`).
- Start each objective with an action-oriented infinitive verb (`uitleggen`, `vergelijken`, `aanmaken`, `instellen`, `bouwen`, `beschrijven`, `opzetten`, `registreren`, `gebruiken`, `integreren`).
- Use observable action verbs only. Avoid vague verbs such as `kennen`, `begrijpen`, `inzien`, `weten`.
- Keep objectives concrete and assessable: each item should describe observable behavior.
- Keep each objective single-action (one observable handeling per bullet).
- Make content specific and unambiguous (avoid broad placeholders like `de microscoop hanteren` without context).
- Prefer domain-specific wording over vague statements (`correct inzetten`, `thread-safe ... garanderen`, `de juiste keuze maken voor een gegeven context`).
- Keep a consistent level of detail across items.
- Use one bullet per objective.
- Add conditions or minimum performance criteria only when they are instructionally relevant and measurable.
- Keep code identifiers and framework types in English where relevant (for example `NavigationManager`, `EventCallback`, `EditForm`, `IDbContextFactory<T>`).

## Quality Checklist

Before finalizing, verify:

- The filename is exactly `00-objectives.adoc`.
- The module name in the discrete title matches the module folder topic.
- The intro sentence starts with `In dit hoofdstuk leer je`.
- `== Overzicht` is present and concise.
- `== Leerdoelstellingen` contains clear, measurable bullet points.
- Every objective is phrased as observable student behavior (implicitly `je kan`/`je wil`).
- Every objective uses an observable action verb (not `kennen`/`begrijpen`/`inzien`/`weten`).
- Every objective is single-action and concrete in inhoud.
- No objective is duplicated or overly broad.
- Terminology is consistent with nearby chapters in the same module.

## Example Objective Starters

- `uitleggen wat ...`
- `... vergelijken en de juiste keuze maken ...`
- `... aanmaken in Visual Studio ...`
- `... instellen op project- en componentniveau ...`
- `... bouwen met ...`
- `... beschrijven en de juiste ... gebruiken`
- `... opzetten met ...`
- `... registreren en injecteren via ...`
- `... gebruiken om ... te garanderen`
- `... integreren in een bestaande ...`

## Notes

- Keep this file as a temporary skill draft in the repository root.
- If promoted to a reusable skill, move it to a dedicated skill folder with filename `SKILL.md`.
