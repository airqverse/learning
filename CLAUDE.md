# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Repository Is

This is a collection of interconnected **Obsidian vaults** for technical interview and certification preparation. It is a spaced-repetition-powered knowledge graph, not a flat file system. The goal is building muscle memory for live pair-programming interviews (DSA) and Google Cloud Professional Certification exams.

## Vault Structure

| Vault | Purpose |
|---|---|
| `dsa/` | Data structures, algorithms, techniques, and complexity analysis for pair-programming interviews |
| `google_cloud/` | GCP services, operations/IaC, design patterns, case studies, and exam prep for Professional Certifications (ACE, PCA, PCSE) |
| `system_design/` | Distributed systems concepts, building blocks, architecture patterns, and case studies for senior engineering interviews |
| `google_cloud_memolog/` | Diary-driven flashcard system — raw daily learning diaries in `01_Daily_Diaries/` get AI-extracted into flashcards in `98_Flashcards/` |

Each vault (except memolog) shares a common internal layout:
- `00_Index/` — Maps of Content (MOCs), the navigation entry points
- Numbered content directories (`01_*` through `05_*`)
- `98_Flashcards/` — Spaced repetition cards mirroring the content directory structure
- `99_Templates/` — Blueprints for generating new notes

## Critical Rules When Modifying Notes

### Separation of Concerns
- **Concepts vs. Implementation must never be mixed.** In GCP: architecture lives in `01_Services/`, Terraform/gcloud code lives in `02_Operations_and_IaC/`. In DSA: algorithm theory lives in `02_Algorithms/`, LeetCode solutions live in `05_Problems/`. Cross-link between them.

### Naming Conventions
- **Never use spaces in file or folder names.** Use underscores exclusively.
- Content files: `Pascal_Snake_Case` (e.g., `Cloud_Load_Balancing.md`)
- Directories: `[Number]_Pascal_Snake_Case` (e.g., `01_Services/`)
- Templates: match target directory name + `_Template` suffix
- MOCs: `[Number]_Concept_MOC.md`
- Use Obsidian aliases to hide underscores in display text: `[[Binary_Search|Binary Search]]`

### Tagging System
Tags map 1-to-1 to directory paths (excluding numeric prefixes):
- `01_Data_Structures/Trees.md` → `#data_structures/trees`
- `00_Index/` files get flat `#index`
- Flashcards always root at `#flashcards/` (e.g., `#flashcards/services/networking/load_balancing`)

### MOC Linking
When creating a new note, **always** add a link to it in the corresponding `00_Index/` MOC file. Look for the anchor comment `# Gemini CLI: Insert actual...` and insert below it.

### Flashcard System (98_Flashcards/)
- Directory structure must **mirror** the parent vault's content paths
- Flashcard file names use `_Flashcards` suffix (e.g., `BFS_Flashcards.md`)
- Use Obsidian Spaced Repetition plugin syntax:
  - Multi-line scenario: `?` on its own line between prompt and answer
  - Cloze deletion: `==hidden text==`
  - Comparative Q&A: `Question :: Answer`
- Use block transclusion (`![[Note_Name^block-id]]`) instead of duplicating content (DRY)
- Focus on analytical friction, not basic trivia: scenario analysis, hard limits, "X vs Y" decisions, and exact syntax recall

### Language
All code examples must be in **Python** unless explicitly requested otherwise.

### Frontmatter Enums (GCP vault)
- `service_model`: IaaS, PaaS, SaaS, FaaS, CaaS
- `management_level`: Unmanaged, Managed, Fully-Managed, Serverless

### Frontmatter Enums (System Design vault)
- `availability_level`: Low, High, Critical
- `consistency_model`: Strong, Eventual, Causal, Read-Your-Writes

### Template Placeholders
Use explicit bracket syntax (`[SERVICE_NAME]`, `[COMPONENT_NAME]`) — never Templater syntax (`{{}}` or `<% %>`).

## Memolog Workflow (google_cloud_memolog/)
This vault is different: the user writes raw stream-of-consciousness diary entries in `01_Daily_Diaries/`. When asked, extract testable flashcards focusing on friction points — errors, hard limits, order-of-operations, unexpected constraints — not basic definitions. CLI-heavy diary entries (labs, IAM bindings, deployment flags) are a valid diary format and flow through the same pipeline. Tag with `#flashcards/gcp/[domain]`.

Dual-level targeting — every extraction should attempt cards for both tracks:
- **ACE (`98_Flashcards/ACE_Operational/`):** Cloze deletions (`==text==`) for specific `gcloud` flags, default timeouts, IAM bindings, and exact commands actually used.
- **PCA (`98_Flashcards/PCA_Architectural/`):** Multi-line scenario analysis (`?`) or comparative differentiators (`::`) based on architectural "Why". Answers must include the correct choice and why alternatives were wrong.
