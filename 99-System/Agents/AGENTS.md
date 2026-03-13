# AGENTS.md - Global AI Instructions

This file serves as the **primary instruction set** for any AI agent (Claude, Copilot, ChatGPT, etc.) interacting with this Obsidian Knowledge Vault.

## 1. Vault Overview
- **Name:** Soyt0ny's Knowledge Vault.
- **Methodology:** PARA (Projects, Areas, Resources, Archives).
- **Tone:** Professional, direct, and strictly **NO EMOJIS**.

## 2. Directory Structure
| Folder | Purpose |
| :--- | :--- |
| `00 Inbox/` | Initial capture point for unorganized thoughts. |
| `10 Daily/` | Daily logs (`YYYY-MM-DD.md`). |
| `20 Projects/` | Active, time-bound efforts (e.g., `Engineering/`, `School/`). |
| `30 Areas/` | Ongoing responsibilities (e.g., `Software Engineering/`). |
| `40 Knowledge/` | Evergreen atomic notes and research. |
| `99-System/` | Internal vault management: `Agents/`, `Archive/`, `Attachments/`. |

## 3. Core Mandates
1.  **No Emojis:** Do not use emojis in filenames, headers, or content.
2.  **Frontmatter:** All notes MUST have YAML frontmatter (`tags`, `status`, `tech`, `domain`).
3.  **Templates:** Always use the appropriate template from `Templates/` when creating new notes.
4.  **Links:** Use standard `[[WikiLinks]]`.

## 4. File Conventions
### Naming
- **Daily:** `YYYY-MM-DD`
- **General:** `NN Name` (e.g., `10 Daily`, `20 Projects`).
- **Notes:** Descriptive and concise.

### Metadata (YAML)
```yaml
---
tags:
  - note
status: in-progress # options: in-progress, review, evergreen, finish
created: YYYY-MM-DD
tech:
  - TechName
domain: DomainName
---
```

## 5. Agent-Specific Context
- Agent-specific configurations are located in `99-System/Agents/<AgentName>/`.
- Shared skills or instructions should be respected across all agents.

## 6. Maintenance Workflows
- **Review:** Check files with `status: review`.
- **Knowledge:** Move finalized review notes to `40 Knowledge/` and set `status: evergreen`.
- **Archive:** Move completed projects or obsolete info to `99-System/Archive/` and set `status: finish`.
