# 🧠 Core Architecture & Philosophies for AI Assistants

This file serves as the absolute source of truth for all interactions within the `/learning/` repository. It defines the global architectural standards, knowledge base philosophies, and specific workflows that **MUST** be applied across all child vaults (`dsa`, `google_cloud`, etc.).

---

## 🏛️ 1. The "Obsidian Brain" Philosophy
This repository is not a flat file system; it is a highly interconnected, Spaced-Repetition-powered graph database managed via Obsidian.
- **The Ultimate Goal:** To build unshakeable, instinctive muscle memory for high-pressure technical environments (Live Pair-Programming Interviews, Google Professional Certification Exams).
- **Separation of Concerns:** Never mix concepts (The "What/Why") with execution (The "How/Code"). 
  - *Example in GCP:* Architecture lives in `01_Services/`; Terraform code lives in `02_Operations_and_IaC/`.
  - *Example in DSA:* The theory of BFS lives in `02_Algorithms/`; The LeetCode implementation lives in `05_Problems/`.

## 🧭 2. Global Path-Based Tagging (Strict Routing)
We do not use semantic or ambiguous tags. Every tag in this repository **MUST** map 1-to-1 with the physical directory structure (excluding numerical prefixes).
- **Rule:** If a file is in `03_Techniques/Sliding_Window.md`, its tag is strictly `#techniques/sliding_window`.
- **Root Level (`00_Index/`):** All Map of Content (MOC) files get a flat `#index` tag. Do not nest tags within the index.

## 🧠 3. The Flashcard Ecosystem (`98_Flashcards/`)
Flashcards are the engine of this repository. They are managed via the Obsidian Spaced Repetition plugin.
- **Mirrored Structure:** Flashcards must physically live in a mirrored directory structure inside `98_Flashcards/` (e.g., `98_Flashcards/01_Services/Compute/`).
- **Strict Tag Root:** Every flashcard MUST begin with `#flashcards/` followed by the path-based tag (e.g., `#flashcards/services/compute/machine_families`).
- **The DRY Principle (Transclusion):** Never duplicate large blocks of code or complex tables into a flashcard. Use Obsidian block transclusion (`![[Note_Name^block-id]]`) on the back of the card so it dynamically fetches updates from the source of truth.

## ⚙️ 4. Formats & Conventions
- **Naming Conventions:** All content files and directories use `Pascal_Snake_Case` (e.g., `Cloud_Load_Balancing.md`). No spaces allowed.
- **Language Preference:** All code examples, algorithms, and implementations MUST be written in **Python** unless explicitly instructed otherwise.
- **The "Mega-Note" Structure:** Avoid file bloat. Use H3 (`###`) headers and Markdown tables to group configurations (like GCP Machine Families) inside a single parent service note, rather than creating 50 micro-notes.

## 🎯 5. Flashcard Generation Strategy
Do not generate basic trivia. Flashcards must test analytical friction and high-level strategy:
1. **Multi-line Scenarios (`?`):** Paragraph-long, ambiguous requirements (mimicking exam case studies or vague interview prompts).
2. **Cloze Deletions (`==text==`):** Contextual sentences hiding exact hard limits, OSI layers, or Big O time complexities.
3. **Comparative Differentiators (`::`):** Testing "Choose This over That" (e.g., Cloud Run vs. App Engine; BFS vs. DFS).
4. **Muscle Memory Blocks (`?`):** Testing the exact syntax of a core algorithm (e.g., "Implement Binary Search") via transclusion.