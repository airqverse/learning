# Google Cloud Knowledge Base (Obsidian)

This repository is a structured learning system for Google Cloud Platform (GCP), organized for clarity and progression. It follows a "Concepts-to-Architecture" workflow, using **City Infrastructure** as a consistent metaphor to explain complex cloud services and networking patterns.

**These notes are managed with Obsidian; interconnected links and MOCs (Maps of Content) are critical for navigation and discovery.**

## 📁 Folder Structure

- **`00_Index/`**: Entry points and category-specific Maps of Content (MOC).
- **`01_Compute/`**: The "Processing Power" phase. VMs (Compute Engine), Containers (GKE, Cloud Run), and Serverless (Cloud Functions).
- **`02_Storage_and_Databases/`**: The "Data Persistence" phase. Object storage (Cloud Storage), Relational (Cloud SQL, Spanner), and NoSQL (Firestore, Bigtable).
- **`03_Networking/`**: The "Connectivity" phase. VPCs, Load Balancing, Cloud DNS, and Interconnect.
- **`04_Security_and_IAM/`**: The "Protection" phase. Identity and Access Management, Resource Manager, and Security Command Center.
- **`05_Data_and_AI/`**: The "Analytics" phase. BigQuery, Dataflow, Vertex AI, and Pub/Sub.
- **`99_Templates/`**: Specialized templates ensuring consistent structure across all notes.

## 🛠 Guidelines for AI Assistants (Gemini/Cursor)

When modifying or adding new notes, strictly adhere to these principles:

1.  **Index-Driven Navigation**: Never link to a generic "home" page. Every note must link back to its specific category MOC (e.g., `[[00_Index/01_Compute_MOC|Back to Compute Index]]`).
2.  **Context-First**: Try to ground abstract cloud concepts with physical infrastructure analogies (e.g., VPC = Gated Community, Cloud Run = On-demand Worker Factory) or standard enterprise use cases.
3.  **Template Fidelity**: 
    - **Compute/Storage**: Focus on *Use Cases*, *Scaling Limits*, *Pricing Models*, and *`gcloud` CLI / Terraform* examples.
    - **Networking**: Focus on *Traffic Flow*, *Boundaries*, *Latency*, and *Topology*.
    - **Security/IAM**: Focus on *Principle of Least Privilege*, *Roles vs. Permissions*, and *Hierarchy* (Organization > Folder > Project).
    - **Data/AI**: Focus on *Ingestion vs. Processing vs. Serving*, *Throughput*, and *Integration*.
4.  **Tagging & Metadata**: Every note MUST include:
    - YAML frontmatter with `gcp_service_type` and `pricing_model`.
    - Category-specific tags (e.g., `#gcp/compute`, `#gcp/networking`).
5.  **Graph Optimization**: Avoid orphan notes. Link new notes in their respective category MOC in `00_Index` and maintain "Related" links between services that integrate well together (e.g., Cloud Run -> Cloud SQL).

## 🎨 Graph View Setup
To visualize the knowledge map effectively in Obsidian, use the following "Group by Path" colors:
- **`00_Index`**: Yellow (The Map)
- **`01_Compute`**: Blue (The Engines)
- **`02_Storage_and_Databases`**: Green (The Vaults)
- **`03_Networking`**: Orange (The Highways)
- **`04_Security_and_IAM`**: Red (The Guards)
- **`05_Data_and_AI`**: Purple (The Brain)

---
*Generated with care to bridge the gap between abstract cloud architecture and practical implementation.*
