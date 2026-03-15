# AGENTS.md - Global AI Instructions

This file serves as the **primary instruction set** for any AI agent interacting with this Obsidian Knowledge Vault.

## 1. Vault Overview & Style Mandates
- **Tone:** Professional, direct, senior engineer peer level.
- **Strict Rules:**
    1.  **NO EMOJIS:** Absolutely forbidden in any part of the vault.
    2.  **Language Balance:** Structural headers in **English** (from templates). Body content and explanations in **Spanish**.
    3.  **C++ Style:** Prefer `using namespace std;` in code examples. Avoid `std::` prefix unless strictly required for clarity.

## 2. Note Writing Standard (The "Soyt0ny" Style)
When a note is in `status: review`, the agent MUST:
- **Synthesize & Integrate:** Do NOT use a "Chat" format (e.g., "User said / AI said"). Instead, integrate the user's original thoughts and questions into the technical body of the note.
- **Rich Markdown Formatting:**
    - Use **bold** for key terms and *italics* for emphasis or analogies.
    - Use `inline code` for technical identifiers.
    - Use Obsidian **Callouts** (`[!tip]`, `[!info]`, `[!warning]`) to highlight doubts, secrets, or "expert tips" derived from the conversation.
- **Technical Depth:** Include Big O complexity ($\bigO(n)$), memory management details, and "When to use / When to avoid" sections.
- **Finalization:** Once enriched, move to `40 Knowledge/` and set `status: evergreen`.

## 3. Directory Structure (PARA)
- `00 Inbox/`: Initial capture point.
- `10 Daily/`: Daily logs.
- `20 Projects/`: Time-bound active efforts.
- `30 Areas/`: Ongoing responsibilities.
- `40 Knowledge/`: Evergreen atomic notes.
- `99-System/`: Internal management.

## 4. Maintenance Workflows
- **Review:** Process notes where `status: review`.
- **Enrichment:** Summarize learning logs into permanent technical documentation.
- **Connections:** Always look for and create `[[WikiLinks]]` to relevant or future notes.
