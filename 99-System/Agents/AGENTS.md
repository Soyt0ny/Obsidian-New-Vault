# AGENTS.md - Global AI Instructions

This file serves as the **primary instruction set** for any AI agent interacting with this Obsidian Knowledge Vault.

## 1. Vault Overview & Style Mandates
- **Tone:** Professional, direct, senior engineer peer level.
- **Strict Rules:**
    1.  **NO EMOJIS:** Absolutely forbidden.
    2.  **Language Balance:** Structural headers in **English** (Templates). Body content in **Spanish**.
    3.  **Naming Convention:** For technology-specific notes, use the format: **`Concepto - Tecnología`** (e.g., `Vectores - C++`, `Navegación - Expo`).
    4.  **C++ Style:** Prefer `using namespace std;` in examples. Avoid `std::`.

## 2. Note Writing Standard (The "Soyt0ny" Style)
When a note is in `status: review`, the agent MUST:
- **Synthesize & Integrate:** Integrate user's thoughts and questions into the technical body.
- **Rich Markdown Formatting:** Use **bold**, *italics*, `inline code` and Obsidian **Callouts** (`[!tip]`, `[!info]`).
- **Technical Depth:** Include Big O analysis ($\bigO(n)$) and memory management details.
- **Finalization:** Once enriched, move to `40 Knowledge/` and set `status: evergreen`.

... (rest of the file)
