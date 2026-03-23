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
- **`98_Flashcards/`**: Spaced-repetition flashcard files for active recall.
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
    - **`05_Exam_Prep` & `98_Flashcards`**: Focus on *Key differentiators*, *exact quotas/limits*, and *tricky wording often found in exam questions*.
4.  **Tagging & Metadata**: Every note MUST include:
    - YAML frontmatter with attributes like `service_category`.
    - Category-specific tags (e.g., `#services/compute`, `#operations`, `#exam_prep`).
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
- **`98_Flashcards`**: Pink (Active Recall)
- **`99_Templates`**: Grey (Automation & Structure)

## 🏆 Certification Study Strategy

To successfully pass the Associate Cloud Engineer (ACE), Professional Cloud Architect (PCA), and Professional Cloud Security Engineer (PCSE) exams, passive video courses are not enough. Follow this tri-fold strategy:

### 1. The Sequence of Execution
Do not study for these simultaneously. They build on each other.
- **Phase 1: Associate Cloud Engineer (ACE).** Proves you can *operate* the cloud. Focus on muscle memory: `gcloud` CLI commands, the Console UI, and basic Terraform.
- **Phase 2: Professional Cloud Architect (PCA).** Proves you can *design* the cloud. Shift your mindset from "How do I deploy this?" to "Why should I deploy this instead of that?"
- **Phase 3: Professional Cloud Security Engineer (PCSE).** The most specialized. Requires the architectural foundation of the PCA, layered with deep knowledge of IAM, VPC Service Controls, Cloud Armor, and compliance.

### 2. The "Hands-On" Friction Rule
Courses teach theory; exams test practical friction. 
- You MUST supplement your notes with **Google Cloud Skills Boost (Qwiklabs)**.
- When you hit an error in a lab or discover a required order-of-operations, document that specific friction point in `02_Operations_and_IaC/`. 

### 3. Case Study Analysis (PCA Specific)
Roughly 20% of the PCA exam relies on fictional, multi-page business case studies (e.g., Mountkirk Games, EHR Healthcare). 
- You cannot pass by just memorizing technical limits. You must analyze the official Google Case Studies *before* exam day.
- Use the `04_Case_Studies/` directory to break down their current infrastructure, business constraints, and technical goals. Use AI to generate "What-If" scenario flashcards based on these specific businesses.

## 🧠 Flashcard Ecosystem & Spaced Repetition Guide

When creating active recall flashcards, strict adherence to the **Obsidian Spaced Repetition Plugin** rules is required to maintain a structured and automatically routed database.

### 1. Mirrored Directory Structure
The `98_Flashcards/` folder MUST mirror the structural paths of the broader vault to maintain logical separation.
- Do **not** dump flashcards into a flat root folder.
- *Example:* A flashcard for `01_Services/Networking/Cloud_Load_Balancing.md` must be saved exactly at `98_Flashcards/01_Services/Networking/Cloud_Load_Balancing_Flashcards.md`.

### 2. Strict Tag Hierarchy (Logical Routing)
Deck folders inside the review UI are generated dynamically via tag splitting.
- The tag structure MUST correspond directly to the physical folder path of the knowledge base (excluding the numerical prefixes).
- The absolute root tag MUST be: `#flashcards/`
- *Example:* A file in `01_Services/Networking/` should use tags like `#flashcards/services/networking/load_balancing`.
- *Example:* A file in `03_Design_Patterns/` should use tags like `#flashcards/design_patterns/ha`.

### 3. Professional Certification Flashcard Strategy
The flashcards in this vault are designed to bypass basic trivia and target the rigor of Google Cloud Professional exams (Architect/Security). While they cover the foundational knowledge needed for the Associate Cloud Engineer (ACE), their primary function is to drill architectural differentiators, hard limits, and complex scenario analysis.

When generating flashcards, strictly adhere to the following strategic formats:

1. **Multi-line Scenario Analysis (`?`):** This is the **primary format** for Professional exams. Construct paragraph-long, ambiguous architectural requirements that mimic official exam case studies. Place the `?` on its own line. The answer MUST include the correct architecture *and* a brief justification of why alternative services were incorrect.
2. **Cloze Deletions (`==text==`):** Use for testing precise parameters, hard quotas, OSI layers, or critical IAM roles *within* a surrounding architectural paragraph. (e.g., "The max size of a Cloud SQL instance is ==64 TB==, whereas Spanner scales horizontally.")
3. **Comparative Differentiators (`::`):** Avoid basic definitions. Instead, use standard Q&A strictly to test "Choose This over That" decisions. (e.g., "When to use Cloud Run vs. App Engine Standard? :: Use Cloud Run for containerized apps requiring custom system binaries; use App Engine for purely source-code deployments.")
4. **Block Transclusion:** To enforce the DRY principle, embed the source of truth from the main note instead of duplicating text. Use `![[Note_Name^block-id]]` on the back of the card so it dynamically fetches updates.

---
*Generated with care to bridge the gap between abstract cloud architecture, practical implementation, and certification readiness.*
