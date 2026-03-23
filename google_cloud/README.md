# Google Cloud Knowledge Base (Professional Certification Prep)

This repository is a structured learning system for Google Cloud Platform (GCP), specifically designed as a knowledge base to prepare for **Google Cloud Professional Certifications**. It follows a "Concepts-to-Architecture" workflow, using **City Infrastructure** as a consistent metaphor to explain complex cloud services and networking patterns.

**These notes are managed with Obsidian; interconnected links and MOCs (Maps of Content) are critical for navigation, discovery, and spaced repetition.**

## 📁 Folder Structure

- **`00_Index/`**: The Map. Entry points and category-specific Maps of Content (MOC).
- **`01_Services/`**: Main Google Cloud core services.
  - `Analytics/`
  - `App_Development/`
  - `Artificial_Intelligence/`
  - `CI_CD/`
  - `Compute/`
  - `Databases/`
  - `Distributed_Cloud/`
  - `Integration_Services/`
  - `Management/`
  - `Networking/`
  - `Observability/`
  - `Operations/`
  - `Security/`
  - `Serverless/`
  - `Storage/`
  - `Tools/`
  - `Web3/`
- **`02_Operations_and_IaC/`**: Infrastructure as Code, deployment, monitoring, and SRE.
- **`03_Design_Patterns/`**: Google Cloud Design Patterns and architecture blueprints.
- **`04_Case_Studies/`**: Real-world case studies and migration examples.
- **`05_Exam_Prep/`**: Notes for test questions, practice exams, and tricky scenarios.
- **`06_Flashcards/`**: Spaced-repetition flashcard files for active recall.
- **`99_Templates/`**: Templates for automation with Gemini-CLI, ensuring consistent structure across all notes.

## 🛠 Guidelines for AI Assistants (Gemini/Cursor)

When modifying or adding new notes, strictly adhere to these principles:

1.  **Index-Driven Navigation**: Never link to a generic "home" page. Every note must link back to its specific category MOC (e.g., `[[00_Index/01_Services_MOC|Back to Services Index]]`).
2.  **Context-First**: Try to ground abstract cloud concepts with physical infrastructure analogies (e.g., VPC = Gated Community, Cloud Run = On-demand Worker Factory) or standard enterprise use cases.
3.  **Template Fidelity**: 
    - **`01_Services`**: Focus on *Use Cases*, *Scaling Limits*, *Pricing Models*, and *Architecture*. **NO implementation code.**
    - **`02_Operations_and_IaC`**: Focus on *Deployment pipelines*, *Monitoring (Cloud Monitoring/Logging)*, *Terraform configurations*, and *SRE principles*.
    - **`03_Design_Patterns`**: Focus on *Trade-offs*, *High Availability (HA) vs. Disaster Recovery (DR)*, *Cost optimization*, and *Architectural blueprints*.
    - **`04_Case_Studies`**: Focus on *Business requirements*, *Before/After architectures*, and *"Why they chose X over Y"*.
    - **`05_Exam_Prep` & `06_Flashcards`**: Focus on *Key differentiators*, *exact quotas/limits*, and *tricky wording often found in exam questions*.
4.  **Tagging & Metadata**: Every note MUST include:
    - YAML frontmatter with attributes like `service_category`.
    - Category-specific tags (e.g., `#gcp/services/compute`, `#gcp/operations`, `#gcp/exam_prep`).
5.  **Graph Optimization**: Avoid orphan notes. Link new notes in their respective category MOC in `00_Index` and maintain "Related" links between services that integrate well together.

### 🤖 Automated Generation Rules (For Gemini/Cursor)

1.  **Template Placeholders**: Do not use Templater syntax (`{{}}` or `<% %>`). Use the explicit bracket syntax (e.g., `[SERVICE_NAME]`, `[CATEGORY_NAME]`) defined in `99_Templates`.
2.  **MOC Anchor Linking**: When generating a new note, you MUST automatically add a link to it in the corresponding `00_Index/` MOC file. Look for the anchor comment `# Gemini CLI: Insert actual...` and insert the new link on the line directly below it (or replace the placeholder).
3.  **Strict Separation of Concerns**:
    - `01_Services/` is for **Concepts & Architecture** (What it is, limits, analogies).
    - `02_Operations_and_IaC/` is for **Implementation & Code** (Terraform, gcloud scripts).
    - These two notes must cross-link to each other.
4.  **Strict Frontmatter Enums**: Do not invent YAML values. Strictly adhere to these lists:
    - `service_model`: [IaaS, PaaS, SaaS, FaaS, CaaS]
    - `management_level`: [Unmanaged, Managed, Fully-Managed, Serverless]

## 📝 File and Folder Naming Conventions

To ensure cross-compatibility between human readability in Obsidian and automation tools (CLI, Git, AI Assistants), **NEVER use spaces in file or folder names.** Always use underscores (`_`).

Strictly adhere to the following naming formats:

1. **Content Notes (Services, Concepts, Patterns):** Use `Pascal_Snake_Case`.
   - *Example:* `Compute_Engine.md`, `Cloud_Load_Balancing.md`
2. **Directories / Folders:** Use `[Optional_Number_Prefix]_Pascal_Snake_Case`.
   - *Example:* `01_Services/`, `Compute/`, `Data_and_ML/`
3. **Utility and System Files (Templates, Configs):** Use `lowercase_snake_case`.
   - *Example:* `service_template.md`
4. **Maps of Content (MOCs) & Indexes:** Use `[Number]_Concept_MOC.md`.
   - *Example:* `01_Services_MOC.md`, `00_GCP_Master_Map.md`

*Note: For human readability in Obsidian text, use aliases when creating links to obscure the underscore (e.g., `[[Compute_Engine|Compute Engine]]`).*

## 🎨 Graph View Setup
To visualize the knowledge map effectively in Obsidian, use the following "Group by Path" colors for the top-level directories:
- **`00_Index`**: Yellow (The Map)
- **`01_Services`**: Blue (Core Building Blocks)
- **`02_Operations_and_IaC`**: Green (Maintenance & Deployment)
- **`03_Design_Patterns`**: Purple (Architecture & Strategy)
- **`04_Case_Studies`**: Orange (Real-world Applications)
- **`05_Exam_Prep`**: Red (Exam Preparation)
- **`06_Flashcards`**: Pink (Active Recall)
- **`99_Templates`**: Grey (Automation & Structure)

## 🧠 Flashcard Ecosystem & Spaced Repetition Guide

When creating active recall flashcards, strict adherence to the **Obsidian Spaced Repetition Plugin** rules is required to maintain a structured and automatically routed database.

### 1. Mirrored Directory Structure
The `06_Flashcards/` folder MUST mirror the structural paths of the broader vault to maintain logical separation.
- Do **not** dump flashcards into a flat root folder.
- *Example:* A flashcard for `01_Services/Networking/Cloud_Load_Balancing.md` must be saved exactly at `06_Flashcards/01_Services/Networking/Cloud_Load_Balancing_Flashcards.md`.

### 2. Strict Tag Hierarchy (Logical Routing)
Deck folders inside the review UI are generated dynamically via tag splitting.
- The tag structure MUST correspond directly to the physical folder path of the knowledge base (excluding the numerical prefixes).
- The absolute root tag MUST be: `#flashcards/`
- *Example:* A file in `01_Services/Networking/` should use tags like `#flashcards/services/networking/load_balancing`.
- *Example:* A file in `03_Design_Patterns/` should use tags like `#flashcards/design_patterns/ha`.

### 3. Flashcard Formatting Rules
1. **Cloze Deletions (`==text==`):** Use for testing precise parameters, OSI layers, or limits *within* a surrounding architectural paragraph.
2. **Standard Q&A (`::`):** Use for direct terminology mapping. (E.g., `Question :: Answer`)
3. **Multi-line Scenario Q&A (`?`):** Use for exam-style situational questions. Place `?` on its own line between the prompt and the answer/reasoning block.
4. **Block Transclusion:** To enforce the DRY principle, embed the source of truth from the main note instead of duplicating text. Use `![[Note_Name^block-id]]` on the back of the card so it dynamically fetches updates.

---
*Generated with care to bridge the gap between abstract cloud architecture, practical implementation, and certification readiness.*
