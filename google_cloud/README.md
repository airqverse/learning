# Google Cloud Knowledge Base (Professional Certification Prep)

This repository is a structured learning system for Google Cloud Platform (GCP), specifically designed as a knowledge base to prepare for **Google Cloud Professional Certifications**. It follows a "Concepts-to-Architecture" workflow, using **City Infrastructure** as a consistent metaphor to explain complex cloud services and networking patterns.

**These notes are managed with Obsidian; interconnected links and MOCs (Maps of Content) are critical for navigation, discovery, and spaced repetition.**

## 📁 Folder Structure

- **`00_Index/`**: The Map. Entry points and category-specific Maps of Content (MOC).
- **`01_Services/`**: Main Google Cloud core services.
  - `Compute/`
  - `Data_and_ML/`
  - `Networking/`
  - `Security_and_IAM/`
  - `Storage_and_Databases/`
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
    - **`01_Services`**: Focus on *Use Cases*, *Scaling Limits*, *Pricing Models*, and *`gcloud` CLI / Terraform* examples.
    - **`02_Operations_and_IaC`**: Focus on *Deployment pipelines*, *Monitoring (Cloud Monitoring/Logging)*, *Terraform configurations*, and *SRE principles*.
    - **`03_Design_Patterns`**: Focus on *Trade-offs*, *High Availability (HA) vs. Disaster Recovery (DR)*, *Cost optimization*, and *Architectural blueprints*.
    - **`04_Case_Studies`**: Focus on *Business requirements*, *Before/After architectures*, and *"Why they chose X over Y"*.
    - **`05_Exam_Prep` & `06_Flashcards`**: Focus on *Key differentiators*, *exact quotas/limits*, and *tricky wording often found in exam questions*.
4.  **Tagging & Metadata**: Every note MUST include:
    - YAML frontmatter with attributes like `gcp_service_type`, `pricing_model`, or `exam_topic`.
    - Category-specific tags (e.g., `#gcp/services/compute`, `#gcp/operations`, `#gcp/exam_prep`).
5.  **Graph Optimization**: Avoid orphan notes. Link new notes in their respective category MOC in `00_Index` and maintain "Related" links between services that integrate well together.

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

---
*Generated with care to bridge the gap between abstract cloud architecture, practical implementation, and certification readiness.*
