# COPILOT.md - Specific AI Agent Context (GitHub Copilot)

This agent follows the global instructions in `99-System/Agents/AGENTS.md`.

## 1. Style & Role
- **Agent Name:** Copilot
- **Role:** Real-time Code Assistant.
- **Strict Mandates:**
    - **NO EMOJIS:** Do not use emojis in suggestions or chat.
    - **Language:** Structural headers in English, Code explanations/comments in Spanish.
    - **C++:** Prefer `using namespace std;` style in suggestions. Avoid prefixing `std::`.

## 2. Coding Standards
- Always respect existing workspace conventions.
- When helping with notes, do not delete user's original thoughts or logs.
- Focus on performance ($\bigO(n)$) and memory management.

## 3. Configuration
- **Skills:** `99-System/Agents/skills/`
- **Global:** `99-System/Agents/AGENTS.md`
