# Memolog AI Extraction Directives

When the user requests flashcard generation from a diary entry, follow these rules strictly.

## What to Extract

Focus on **friction points** — errors, hard limits, order-of-operations, unexpected constraints, and CLI gotchas. Do not generate cards for basic definitions (e.g., "What does Compute Engine do?").

CLI-heavy diary entries (labs, IAM bindings, deployment flags) are a valid input. Extract `gcloud` commands and their gotchas into cloze-deletion cards in `ACE_Operational/`.

## Dual-Level Targeting

Every extraction should attempt to create cards for both certification tracks:

- **ACE Level (`98_Flashcards/ACE_Operational/`):** Cloze deletions (`==text==`) for specific `gcloud` flags, default timeouts, IAM bindings, and exact commands the user actually ran.
- **PCA Level (`98_Flashcards/PCA_Architectural/`):** Multi-line scenario analysis (`?`) or comparative differentiators (`::`) based on the architectural "Why" discussed in the diary.

## Flashcard Syntax (Obsidian Spaced Repetition)

Use exactly these formats:

- **Multi-line Scenario (`?`):** Paragraph-long ambiguous requirements. Place `?` on its own line between prompt and answer. Answer must include the correct choice and why alternatives were wrong.
- **Cloze Deletion (`==text==`):** Hide precise parameters, flags, or limits within a contextual sentence.
- **Comparative Differentiator (`::`):** Test "Choose This over That" decisions. Format: `Question :: Answer`.

## Tag Routing

Every generated flashcard block MUST include `#flashcards/gcp/` followed by the specific domain (e.g., `#flashcards/gcp/networking`, `#flashcards/gcp/iam`).

## Transclusion

Use block transclusion (`![[Note_Name^block-id]]`) instead of duplicating content when referencing existing notes in the broader `google_cloud/` vault.
