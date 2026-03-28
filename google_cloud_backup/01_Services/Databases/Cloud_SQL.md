---
service_category: "Databases"
service_model: "PaaS"
management_level: "Fully-Managed"
infrastructure_analogy: "The city's central, managed municipal records office."
---
# Cloud SQL

## 🎯 Definition & Purpose
- A fully managed relational database service for MySQL, PostgreSQL, and SQL Server.
- **Key Differentiator:** Provides lift-and-shift compatibility with standard relational databases without the operational overhead of managing underlying infrastructure, backups, high availability, or patching.

## 🏙️ City Infrastructure Analogy
- Think of it like a **Managed Municipal Records Office**. You don't have to hire the clerks, clean the building, or secure the vault (Google manages the infrastructure), but you still design the filing system (the database schema) and own the documents (the data).

## 🚀 Primary Use Cases
- **Standard Web Frameworks:** Backend for web applications built with frameworks like Django, Ruby on Rails, or Spring Boot that expect standard SQL dialects.
- **Lift and Shift Migrations:** Moving on-premises MySQL, PostgreSQL, or SQL Server workloads directly to the cloud.
- **Transactional Workloads (OLTP):** E-commerce shopping carts, user authentication systems, and basic financial transactions.
- **Anti-Patterns:** Not suitable for large-scale analytical workloads (OLAP) spanning petabytes (use BigQuery) or for global, multi-region active-active read/write scalability with strict consistency (use Cloud Spanner).

## 📏 Scaling Limits & Constraints
- **Scalability:** Primarily scales vertically (scaling up CPU and RAM), which generally requires downtime/restart. Supports read replicas for horizontal read scaling.
- **Hard Quotas & Limits:** Up to 64 TB storage capacity (with auto-storage increase). Storage can auto-grow but cannot auto-shrink. Maximum connection limits are tied to the instance's RAM size.

## 💰 Pricing Model
- **Billing Metric:** Charged by provisioned vCPUs, memory (GB), storage capacity (GB), and network egress. Commercial licensing costs (like SQL Server) apply on top of the infrastructure.
- **Cost Optimization:** Use Committed Use Discounts (CUDs) for predictable 24/7 workloads. Turn off development/staging databases during off-hours. Optimize queries to avoid over-provisioning machine types.

## 🔗 Integrations & Relationships
*How does this connect to other GCP services?*
- **Integrates well with:** [[01_Services/Compute/Compute_Engine|Compute Engine]], [[01_Services/Serverless/Cloud_Run|Cloud Run]] (via Cloud SQL Auth Proxy), and [[01_Services/Serverless/Cloud_Functions|Cloud Functions]].
- **Compared to:** [[01_Services/Databases/Cloud_Spanner|Cloud Spanner]] (Cloud SQL is regional and vertically scaled; Spanner is global and horizontally scaled) and [[01_Services/Compute/Compute_Engine|Compute Engine]] (Self-managed DB on a VM vs. fully managed DB).
- **Operations & IaC:** [[02_Operations_and_IaC/Cloud_SQL_Ops|Cloud SQL Operations]]

#services/Databases

---
[[00_Index/01_Services_MOC|Back to Services Index]]