# Agentic courses 

Skills, agents & instructions for agentic courses with GitHub copilit (CLI)

## Getting started
### APM - Agent Package Manager

- installeer (https://microsoft.github.io/apm/)[APM]

### Gebruik instructions, agents en skills

```
apm install ...
```

### COURSE.md

- Maak een `COURSE.md` bestand aan in de root-directory van je project
- Gebruik onderstaande template als beginpunt
- Vul de naam en omschrijving van je cursus in

> [!TIP]
> Je kan copilot vragen om dit bestand aan te vullen op basis van een reeds bestaande cursus 😉

```markdown
# Content Plan

This file is the single source of truth for the module and chapter structure of this course.
Agents (Claude, GitHub Copilot) MUST consult this file before creating or numbering any module or chapter.

## Course Overview

- **Title**: ... 
- **Description**: ...

## Status values

| Symbol | Meaning |
|--------|---------|
| planned | not yet started |
| in progress | being written |
| done | completed WITHOUT fails |
| failed | completed but WITH fails |

## Modules and Chapters

| #  | Folder | Module title | Chapter file | Chapter title | Status |
|----|--------|--------------|--------------|---------------|--------|

```

## Prompts

### From scratch

Je kan nu een eenvoudige prompt schrijven om een nieuw hoofdstuk aan te maken:

```text
create a new chapter in module 1 called "introductie". the chapter must contain a brief summary of the course with a detailed planning.
```

### From COURSE.md

Je kan ook zelf inhoud toevoegen aan het `COURSE.md`-bestand en daarna vragen aan copilot om deze hoofdstukken te genereren.