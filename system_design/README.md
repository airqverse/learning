# System Design Knowledge Base

This repository is a structured learning system for **System Design**, specifically tailored for mastering large-scale distributed systems, architectural patterns, and preparing for high-stakes **Technical Engineering Interviews**. It follows a "Primitives-to-Systems" workflow, building from fundamental constraints up to massive, real-world case studies.

**These notes are managed with Obsidian; interconnected links and MOCs (Maps of Content) are critical for navigation, discovery, and spaced repetition.**

## 📁 Folder Structure

- **`00_Index/`**: The Map. Entry points and category-specific Maps of Content (MOC).
- **`01_Core_Concepts/`**: Fundamental principles of distributed systems.
  - *Examples: CAP Theorem, PACELC, Consistency Models, Data Partitioning, Networking Protocols.*
- **`02_Building_Blocks/`**: The "Lego bricks" of system architecture.
  - *Examples: Load Balancers, API Gateways, Caches, Message Queues, Databases (Relational vs. NoSQL).*
- **`03_Architecture_Patterns/`**: Blueprint patterns for connecting building blocks.
  - *Examples: Microservices, Event-Driven Architecture, CQRS, Lambda/Kappa Architectures.*
- **`04_Case_Studies/`**: Deconstructions of real-world systems and interview prompts.
  - *Examples: Design Twitter, Design Uber, Design WhatsApp, Design a Rate Limiter.*
- **`05_Interview_Prep/`**: Frameworks, constraints, and execution strategies.
  - *Examples: Back-of-the-envelope calculations, PEDALS framework, Non-Functional Requirements (NFRs).*
- **`98_Flashcards/`**: Spaced-repetition flashcard files for active recall.
- **`99_Templates/`**: Templates for automation with Gemini-CLI, ensuring consistent structure across all notes.

## 🛠 Guidelines for AI Assistants (Gemini/Cursor)

When modifying or adding new notes, strictly adhere to these principles:

1.  **Index-Driven Navigation**: Never link to a generic "home" page. Every note must link back to its specific category MOC (e.g., `[[00_Index/02_Building_Blocks_MOC|Back to Building Blocks Index]]`).
2.  **Context-First**: Always ground abstract components with real-world analogies (e.g., Message Queue = Post Office, Load Balancer = Traffic Cop) and highlight *Trade-offs* explicitly.
3.  **Template Fidelity**: 
    - **`01_Core_Concepts`**: Focus on *Definitions*, *Constraints*, *Mathematical proofs/limits*, and *Trade-offs*.
    - **`02_Building_Blocks`**: Focus on *Use Cases*, *Scaling Limits*, *Common Implementations (e.g., Redis, Kafka)*, and *Trade-offs*. **NO deep application code.**
    - **`03_Architecture_Patterns`**: Focus on *System flow*, *Bottlenecks*, *Failure modes*, and *When NOT to use it*.
    - **`04_Case_Studies`**: Focus on *Functional/Non-Functional Requirements*, *High-Level Design*, *Deep Dives/Bottlenecks*, and *"Why they chose X over Y"*.
    - **`05_Interview_Prep` & `98_Flashcards`**: Focus on *Back-of-the-envelope math constants*, *System limit estimations*, and *Comparative analyses*.
4.  **Tagging & Metadata**: Every note MUST include:
    - YAML frontmatter with attributes like `concept_type`.
    - Category-specific tags (e.g., `#core_concepts`, `#building_blocks/databases`, `#interview_prep`).
5.  **Graph Optimization**: Avoid orphan notes. Link new notes in their respective category MOC in `00_Index` and maintain "Related" links between components that frequently interact.

### 🤖 Automated Generation Rules (For Gemini/Cursor)

1.  **Template Placeholders**: Do not use Templater syntax (`{{}}` or `<% %>`). Use the explicit bracket syntax (e.g., `[COMPONENT_NAME]`, `[TRADE_OFFS]`) defined in `99_Templates`.
2.  **MOC Anchor Linking**: When generating a new note, you MUST automatically add a link to it in the corresponding `00_Index/` MOC file. Look for the anchor comment `# Gemini CLI: Insert actual...` and insert the new link on the line directly below it (or replace the placeholder).
3.  **Strict Separation of Concerns**:
    - `02_Building_Blocks/` is for **Component Theory** (What it is, limits, trade-offs).
    - `04_Case_Studies/` is for **Applied Architecture** (How it is used in a specific system).
    - These notes must cross-link to each other.
4.  **Strict Frontmatter Enums**: Do not invent YAML values. Strictly adhere to these lists when applicable:
    - `availability_level`: [Low, High, Critical]
    - `consistency_model`: [Strong, Eventual, Causal, Read-Your-Writes]

## 📝 File and Folder Naming Conventions

To ensure cross-compatibility between human readability in Obsidian and automation tools (CLI, Git, AI Assistants), **NEVER use spaces in file or folder names.** Always use underscores (`_`).

Strictly adhere to the following naming formats:

1. **Content Notes (Concepts, Blocks, Case Studies):** Use `Pascal_Snake_Case`.
   - *Example:* `Consistent_Hashing.md`, `Design_Twitter.md`
2. **Directories / Folders:** Use `[Optional_Number_Prefix]_Pascal_Snake_Case`.
   - *Example:* `01_Core_Concepts/`, `Databases/`, `Messaging/`
3. **Utility and System Files (Templates, Configs):** Use `lowercase_snake_case`.
   - *Example:* `building_block_template.md`
4. **Maps of Content (MOCs) & Indexes:** Use `[Number]_Concept_MOC.md`.
   - *Example:* `02_Building_Blocks_MOC.md`, `00_System_Design_Master_Map.md`

*Note: For human readability in Obsidian text, use aliases when creating links to obscure the underscore (e.g., `[[Consistent_Hashing|Consistent Hashing]]`).*

## 🎨 Graph View Setup
To visualize the knowledge map effectively in Obsidian, use the following "Group by Path" colors for the top-level directories:
- **`00_Index`**: Yellow (The Map)
- **`01_Core_Concepts`**: Blue (Foundational Theory)
- **`02_Building_Blocks`**: Green (Components)
- **`03_Architecture_Patterns`**: Purple (Blueprints)
- **`04_Case_Studies`**: Orange (Real-world Applications)
- **`05_Interview_Prep`**: Red (Execution & Math)
- **`98_Flashcards`**: Pink (Active Recall)
- **`99_Templates`**: Grey (Automation & Structure)

## 🏆 System Design Study Strategy

To master System Design for senior-level engineering interviews, rely on a structured, iterative approach:

### 1. The Sequence of Execution
Do not jump straight into complex architectures. Build from the ground up.
- **Phase 1: Core Concepts & Math.** Understand the physical limits. CAP theorem, latency numbers every programmer should know, and back-of-the-envelope calculations.
- **Phase 2: Building Blocks.** Master the individual tools. Know when to use a relational database vs. a wide-column store, when to use Redis vs. Memcached, and how load balancing algorithms work.
- **Phase 3: Case Studies.** Synthesize the blocks into systems. Practice designing standard systems (Twitter, URL Shortener, Chat System) within a rigid 45-minute timeframe.

### 2. The "Trade-off" Rule
In System Design, there are no right answers, only trade-offs. 
- Every component choice MUST be accompanied by a discussion of its drawbacks.
- "Why X over Y" is the most important question in this repository. 

## 🧠 Flashcard Ecosystem & Spaced Repetition Guide

When creating active recall flashcards, strict adherence to the **Obsidian Spaced Repetition Plugin** rules is required to maintain a structured and automatically routed database.

### 1. Mirrored Directory Structure
The `98_Flashcards/` folder MUST mirror the structural paths of the broader vault to maintain logical separation.
- Do **not** dump flashcards into a flat root folder.
- *Example:* A flashcard for `02_Building_Blocks/Databases/Consistent_Hashing.md` must be saved exactly at `98_Flashcards/02_Building_Blocks/Databases/Consistent_Hashing_Flashcards.md`.

### 2. Strict Tag Hierarchy (Logical Routing)
Deck folders inside the review UI are generated dynamically via tag splitting.
- The tag structure MUST correspond directly to the physical folder path of the knowledge base (excluding the numerical prefixes).
- The absolute root tag MUST be: `#flashcards/`
- *Example:* A file in `02_Building_Blocks/Databases/` should use tags like `#flashcards/building_blocks/databases`.

### 3. System Design Flashcard Strategy
System Design flashcards should target deep understanding of constraints, limits, and architectural decisions, moving beyond simple definitions.

When generating flashcards, strictly adhere to the following strategic formats:

1. **Multi-line Scenario Analysis (`?`):** Present a specific system requirement or bottleneck and ask for the optimal architectural choice and its justification. Place the `?` on its own line.
2. **Cloze Deletions (`==text==`):** Use for testing precise latency numbers, standard port numbers, or specific math constants (e.g., "Reading 1MB sequentially from memory takes roughly ==250 us==").
3. **Comparative Differentiators (`::`):** Test "Choose This over That" decisions. (e.g., "When to use Long Polling vs. WebSockets? :: Use WebSockets for bi-directional, high-frequency data; use Long Polling if the client only needs to receive occasional updates from the server.")
4. **Block Transclusion:** To enforce the DRY principle, embed the source of truth from the main note instead of duplicating text. Use `![[Note_Name^block-id]]` on the back of the card so it dynamically fetches updates.
