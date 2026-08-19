# AI Meeting Transcript Processor v0.1

A structured prompt framework designed to process raw meeting transcripts into executive summaries, key decisions, action items, open questions, and follow-up emails with explicit ambiguity tracking.

## Overview
Standard LLM prompts often infer deadlines, assignees, or priorities when raw transcripts are vague. This prompt enforces strict compliance rules: missing or ambiguous data is explicitly tagged using standardized markers.

> **Language Note:** The system prompt and generated markers are configured for Polish-language meeting transcripts (`[BRAK OSOBY]`, `[BRAK TERMINU]`, `[DO WERYFIKACJI]`, `[ZMIANA USTALENIA]`, `[SPRZECZNOŚĆ]`).

## Core Rules & Features
- **Hallucination Suppression**: Restricts inferred priorities, missing assignees, or unmentioned dates.
- **Explicit Ambiguity Tracking**:
  - Missing Assignee -> `[BRAK OSOBY]`
  - Missing Deadline -> `[BRAK TERMINU]`
  - Ambiguous Info -> `[DO WERYFIKACJI]`
- **Conflict & Superseded Resolution**:
  - Superseded Agreement -> `[ZMIANA USTALENIA]`
  - Unresolved Conflict -> `[SPRZECZNOŚĆ]`
- **Action Items Matrix**: Formatted Markdown table ready for export.

## How to Use
1. Open `prompt.txt` from this repository.
2. Copy the system prompt.
3. Paste it into your LLM (ChatGPT, Claude, Gemini) along with your raw transcript under the `TRANSKRYPCJA DO ANALIZY:` block.
