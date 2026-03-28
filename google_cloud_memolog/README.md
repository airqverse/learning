# Google Cloud Memolog (Diary-to-Flashcard Learning System)

This repository is an active learning engine designed to convert daily hands-on experiences and study sessions into long-term memory via spaced repetition. It is specifically tailored for preparing for the **Google Cloud Associate Cloud Engineer (ACE)** and **Professional Cloud Architect (PCA)** certifications.

**The core philosophy: Stop writing passive encyclopedias. Write active experiences, and let AI extract the testable facts.**

## 💡 The Origin: Why Diary-Driven Flashcards?
*(The raw idea behind this system)*

Traditionally, maintaining a knowledge base (like an Obsidian Vault full of MOCs and service templates) becomes a heavy maintenance burden. You spend more time formatting notes than actually studying, and rarely read the encyclopedias you've written. 

This project was born from a pivotal realization:
1.  **Writing notes is a pain** and they are rarely read again.
2.  **Flashcards are better for exams**, but creating them interrupts the "flow state" of hands-on learning.
3.  **Diaries are frictionless.** Writing a stream-of-consciousness "What I did today" diary naturally organizes thoughts without the pressure of perfect formatting.

**The Solution:** You only write the *diary* of your experiences or lab work. Whenever you want, you ask the AI to check those diaries. The AI acts as the knowledge extractor, pulling out the critical points you need to remember for the long term and formatting them directly into spaced-repetition flashcards. You focus entirely on the *experience*; the AI handles the *retention engineering*.

## 🔄 The "Memolog" Workflow

The process is designed for maximum speed and zero friction on the learner's part.

### 1. The Input (The Learner)
When you study a new concept, read documentation, or complete a Qwiklabs exercise, you do **not** write a formal, structured note. 
Instead, you write a stream-of-consciousness **Diary Entry** in the `01_Daily_Diaries/` folder.

*Focus on:*
- "What I did today..."
- "What broke and how I fixed it..."
- "What surprised me about this service's limits..."
- "Why the tutorial chose service X instead of service Y..."
- "What `gcloud` commands I ran and what tripped me up..." — CLI-heavy sessions (labs, IAM bindings, deployment flags) are a valid diary format. The AI should extract these into cloze-deletion cards in `ACE_Operational/`.

### 2. The Extraction (The AI Assistant - Gemini/Cursor)
When you are ready, you trigger the AI assistant to review your recent diaries. 
The AI acts as a knowledge synthesizer, extracting the critical, testable points and converting them into strict Obsidian-compatible flashcards.

### 3. The Output (The Spaced Repetition Decks)
The AI will automatically route the generated flashcards into the `98_Flashcards/` directory, split by certification level.

## 📁 Folder Structure

- **`01_Daily_Diaries/`**: The raw, unformatted brain-dumps of your daily learning. Name files by date (e.g., `2026-03-27.md`) or specific topic deep-dives (e.g., `GKE_Networking_Lab.md`).
- **`98_Flashcards/`**: The automatically generated, structured active recall decks.
  - `ACE_Operational/`: Flashcards focused on "How to do it" (gcloud commands, IAM roles, basic limits, tactical execution).
  - `PCA_Architectural/`: Flashcards focused on "Why do it" (Trade-offs, Cost vs. HA, Multi-service scenario analysis, strategic design).

## 🤖 AI Generation Directives (For Gemini/Cursor)

When the user requests flashcard generation from a diary entry, the AI MUST adhere to these strict rules:

### 1. Emphasize "Friction Points"
Do not generate flashcards for basic definitions (e.g., "What does Compute Engine do?"). Instead, focus on the friction points mentioned in the diary: the errors, the hard limits, the specific order-of-operations, and the unexpected architectural constraints.

### 2. Dual-Level Targeting
Every extraction should attempt to create cards for both certification tracks:
- **ACE Level:** Generate Cloze Deletions (`==text==`) for specific `gcloud` flags, default timeouts, and IAM bindings.
- **PCA Level:** Generate Multi-line Scenario Analysis (`?`) or Comparative Differentiators (`::`) based on the architectural "Why" discussed in the diary.

### 3. Strict Flashcard Syntax (Obsidian Spaced Repetition)
The AI must use the exact syntax required by the Obsidian Spaced Repetition plugin:

*   **Multi-line Scenario Analysis (`?`):**
    Paragraph-long, ambiguous architectural requirements mimicking official exam case studies. Place the `?` on its own line.
    ```markdown
    Your team needs to migrate... [Scenario details here]
    ?
    **Correct Answer:** [The correct architecture/service]
    **Why:** [Brief justification of why alternatives were wrong]
    ```

*   **Cloze Deletions (`==text==`):**
    For testing precise parameters or exact commands within a sentence.
    ```markdown
    To increase the default timeout of a Cloud Run service during deployment, use the flag ==--timeout=[VALUE]==.
    ```

*   **Comparative Differentiators (`::`):**
    Standard Q&A strictly testing "Choose This over That" decisions.
    ```markdown
    When should you use Cloud Run versus App Engine Standard? :: Use Cloud Run for containerized apps requiring custom system binaries; use App Engine for purely source-code deployments.
    ```

### 4. Tag Routing
Every generated flashcard block MUST be appended to the appropriate file in `98_Flashcards/` and MUST include the root tag `#flashcards/gcp/` followed by the specific domain (e.g., `#flashcards/gcp/networking`).

---
*Write fast, test hard.*