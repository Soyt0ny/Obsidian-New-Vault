# GEMINI.md - Obsidian Knowledge Vault (Soyt0ny)

This is a personal knowledge management (PKM) vault organized using the **PARA** (Projects, Areas, Resources, Archives) method. It is primarily focused on Software Engineering, Academic studies (University), and AI Agent integration.

## Project Overview

- **Type:** Obsidian Knowledge Vault.
- **Methodology:** PARA Method + Atomic Note-taking.
- **Core Technology:** Markdown, YAML Frontmatter, Obsidian Plugins (Git, Calendar, etc.).
- **Style:** Professional, concise, and strictly **NO EMOJIS** in filenames, headers, or body content.

## Vault Structure

| Folder | Purpose |
| :--- | :--- |
| `00 Inbox/` | Initial capture point for unorganized thoughts and notes. |
| `10 Daily/` | Daily logs named `YYYY-MM-DD.md`. |
| `20 Projects/` | Active, time-bound efforts (e.g., `Engineering/`, `School/`). |
| `30 Areas/` | Ongoing responsibilities and skill maintenance (e.g., `Software Engineering/`). |
| `40 Knowledge/` | Evergreen atomic notes and research. |
| `99 System/` | Internal vault management: `Agents/`, `Archive/`, `Attachments/`, `Books/`. |
| `Templates/` | Blueprints for creating consistent notes. |

## Note Conventions & Workflows

### 1. Metadata (YAML Frontmatter)
All notes must include YAML frontmatter. Tags should use the multi-line format.
Example:
```yaml
---
tags:
  - note
status: in-progress
tech: React
domain: Frontend
---
```

### 2. Mandatory Templates
Never create a note from scratch. Use the corresponding template from `Templates/`:
- **Daily Note:** `2-Daily Note.md` (includes Focus, University, Engineering, and Reflection sections).
- **Project Note:** `4-Project.md` (includes `status`, `owner`, and `area`).
- **Knowledge Note:** `3-Knowledge Note.md` (includes Core Idea, Explanation, Connections, and References).
- **Course Note:** `1-Course.md` (includes `semester` and `professor`).

### 3. Review & Archiving Workflow
- **Review:** Only edit/review files where `status: review` is present in the frontmatter.
- **Enrichment:** When reviewing, add context, examples, or clarifications to make the note "richer."
- **Completion:** Once a task/note is finalized:
    1. Change `status` to `finish`.
    2. Move the file to `99 System/Archive/`.

### 4. AI Agent Configuration
Custom agent instructions and skills are stored in `99 System/Agents/`.
Structure: `99 System/Agents/<AgentName>/skills/<SkillName>/SKILL.md`.

## Maintenance Commands (Manual/Git)

This is a non-code project, but it uses Git for version control via the `obsidian-git` plugin.
- **Sync:** Handled by the `obsidian-git` plugin (auto-commit/push).
- **Dashboard:** Keep `Home.md` updated with "Active Projects" and "Courses" as a central entry point.

## Style Guidelines (Strict)
- **Conciseness:** Be direct and avoid fluff.
- **No Emojis:** Strictly forbidden in any part of the vault.
- **Naming:** Folders use `NN Name` format. Daily notes use `YYYY-MM-DD`. Knowledge notes use descriptive titles.
