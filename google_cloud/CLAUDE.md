# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working within the google_cloud vault.

## Diary-Driven Workflow

The user writes raw stream-of-consciousness diary entries in `01_Diaries/`. When asked, extract testable flashcards focusing on friction points — errors, hard limits, order-of-operations, unexpected constraints — not basic definitions. CLI-heavy diary entries (labs, IAM bindings, deployment flags) are a valid diary format and flow through the same pipeline. Tag with `#flashcards/gcp/[domain]`.

Dual-level targeting — every extraction should attempt cards for both tracks:
- **Operational (`98_Flashcards/Operational/`):** Cloze deletions (`==text==`) for specific `gcloud` flags, default timeouts, IAM bindings, and exact commands actually used.
- **Architectural (`98_Flashcards/Architectural/`):** Multi-line scenario analysis (`?`) or comparative differentiators (`::`) based on architectural "Why". Answers must include the correct choice and why alternatives were wrong.

Use tags to distinguish certification scope (e.g., `#flashcards/gcp/ace/networking`, `#flashcards/gcp/pcse/iam`). A single diary can produce cards for multiple certs.

## Frontmatter Enums

- `service_model`: IaaS, PaaS, SaaS, FaaS, CaaS
- `management_level`: Unmanaged, Managed, Fully-Managed, Serverless
