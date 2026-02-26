# Copilot Instructions

This is an **Obsidian knowledge vault** organized with the PARA method. There are no build, test, or lint commands — all work is creating or editing Markdown notes.

## Vault Structure

| Folder         | Purpose                                      |
|----------------|----------------------------------------------|
| `00 Inbox/`    | Quick capture; organize later                |
| `10 Daily/`    | One note per day                             |
| `20 Projects/` | Active work split by `Engineering/` and `University/` |
| `30 Areas/`    | Ongoing responsibilities (skills, courses)   |
| `40 Knowledge/`| Evergreen atomic notes                       |
| `99 System/`   | Templates, agent configs, attachments        |
| `Templates/`   | Note templates (do not place regular notes here) |

`Home.md` is the vault dashboard; update its **Active Projects** and **Courses** lists when adding new items.

## Note Conventions

### Frontmatter
All notes use YAML frontmatter. Tags use multi-line format:

```yaml
tags:
  - project
status: active
```

### Templates
Always base new notes on the appropriate template in `Templates/`:

| Template             | Use for                        | Required frontmatter                        |
|----------------------|--------------------------------|---------------------------------------------|
| `2-Daily Note.md`    | `10 Daily/` entries            | `date: YYYY-MM-DD`, `tags: [daily]`         |
| `4-Project.md`       | `20 Projects/` notes           | `tags: [project]`, `status: active`, `owner:`, `area:` |
| `1-Course.md`        | `30 Areas/University/Courses/` | `tags: [course]`, `semester:`, `professor:` |
| `3-Knowledge Note.md`| `40 Knowledge/` entries        | `tags: [note]`, `Tech:`, `Domain:`          |

Daily notes use `{date}` as the date placeholder and include sections: **Today Focus (Max 3 Priorities)**, **University — What I Learned**, **Engineering — Skill / Project Improvement**, **Backlog Tasks**, **Reflection**, **Links & Notes**.

Project frontmatter includes `start_date: '{"date":null}'` — keep this format from the template.

### Naming
- Folders use two-digit numeric prefixes with a space (`00 Inbox`, `10 Daily`, `20 Projects`, …)
- Daily notes are named `YYYY-MM-DD.md`
- All other note filenames are plain descriptive titles

### Style Guidelines
- **No Emojis:** Strictly avoid using emojis in filenames, titles, headers, or content body.
- Write in a professional, concise tone.

### Review Workflow
- **Only review files** where the frontmatter explicitly states `status: review`.
- If asked to review a file with any other status (e.g., `active`, `in-progress`), **ASK THE USER FOR CONFIRMATION** before proceeding.
- **Enrich Content:** Do not just fix errors. Add extra context, examples, or clarification to make the note richer and more useful for future reference or others. Ensure information is clear and professional.
- **On Completion:**
  1. Change `status` to `finish`.
  2. Move the file to `99 System/Archive/`.

## AI Agent Configurations

`99 System/Agents/` holds per-agent skill definitions (Claude, Codex, Gemini, Github). Each skill lives at:

```
99 System/Agents/<Agent>/skills/<skill-name>/SKILL.md
```

`SKILL.md` frontmatter and structure:

```yaml
---
name: <skill-name>
description: <short description>
---
```

Followed by `## Instructions` and `## Examples` sections.
