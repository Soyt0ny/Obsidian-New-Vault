# AGENTS.md - Global AI Instructions

This file serves as the **primary instruction set** for any AI agent (Claude, Copilot, ChatGPT, etc.) interacting with this Obsidian Knowledge Vault.

## 1. Vault Overview & Style Mandates
- **Name:** Soyt0ny's Knowledge Vault.
- **Methodology:** PARA (Projects, Areas, Resources, Archives).
- **Tone:** Professional, direct, and senior engineer peer level.
- **Strict Rules:**
    1.  **NO EMOJIS:** Absolutely forbidden in filenames, headers, or body content.
    2.  **Language Balance:** Use **English** for structural headers (from templates) and **Spanish** for all body content/explanations.
    3.  **Preservation:** During "Review/Enrichment", **NEVER** delete the user's original thoughts, questions, or process. Add technical context, examples, and corrections *around* them.
    4.  **C++ Style:** Use `using namespace std;` style in examples. Avoid `std::` prefixing unless specifically required for clarity.

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
1.  **Frontmatter:** All notes MUST have YAML frontmatter (`tags`, `status`, `tech`, `domain`).
2.  **Templates:** Always use the appropriate template from `Templates/` when creating new notes.
3.  **Links:** Use standard `[[WikiLinks]]`.
4.  **Tags:** Keep tags minimal and relevant (e.g., `note`, `project`, `area`). Avoid adding extra tags unless requested.

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

## 6. Maintenance Workflows (Review & Enrichment)
- **Review:** Edit/Review files only where `status: review` is present.
- **Enrichment Protocol:**
    - Identify the core concept.
    - Add technical depth (Complexity, Best Practices, Examples).
    - **Crucial:** Maintain the user's learning log and original questions (e.g., "Gemini dijo", "Original thought").
- **Finalization:** Move finalized review notes to `40 Knowledge/` and set `status: evergreen`.
