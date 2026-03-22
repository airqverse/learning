---
service_category: "Storage"
service_model: "IaaS"
management_level: "Fully-Managed"
infrastructure_analogy: "The city's infinitely expanding, heavily guarded shipping container yard."
---
# Cloud Storage

## 🎯 Definition & Purpose
- A fully managed, highly durable, and highly available object storage service designed for storing any amount of unstructured data.
- **Key Differentiator:** Offers a single, unified API across all its storage classes (Standard, Nearline, Coldline, Archive). It provides strong global consistency (read-after-write) and seamless lifecycle management policies to automate moving data between temperature classes to optimize costs.

## 🏙️ City Infrastructure Analogy
- Think of it like the city's **Infinite Shipping Container Yard**. You can drop off anything—from a single envelope to a massive piece of machinery—as long as it fits in a container (object) and has a tracking number (metadata/key). You don't manage the yard's floor space; the yard automatically expands to hold whatever you bring.

## 🚀 Primary Use Cases
- **Data Lake Foundation:** Storing massive amounts of raw, unstructured data (JSON, CSV, logs) to be processed later by analytics engines like BigQuery or Dataproc.
- **Backup and Archival:** Storing disaster recovery backups, regulatory compliance data, and long-term archives using cheaper storage classes (Coldline, Archive).
- **Static Website Hosting:** Serving HTML, CSS, JavaScript, and images directly to users without needing a web server.
- **Media Storage and Delivery:** Storing user-generated content (videos, images) that can be cached and distributed globally via Cloud CDN.
- **Anti-Patterns:** Do not use for block storage like a virtual machine boot disk (use Persistent Disk). Do not use for fast, structured database queries (use Cloud SQL or BigQuery). Do not use for file-system-level shared storage requiring NFS/SMB protocols (use Filestore).

## 📏 Scaling Limits & Constraints
- **Scalability:** Virtually infinite scalability for total storage size and number of objects. Auto-scales bandwidth to handle extreme request rates.
- **Hard Quotas & Limits:** The maximum size of a single object is 5 TB. Bucket names must be globally unique across all of Google Cloud (not just your organization). 

## 💰 Pricing Model
- **Billing Metric:** Billed based on data stored (per GB/month), network egress (data leaving GCP), and the number of operations (Class A: mutations, Class B: reads). 
- **Cost Optimization:** 
  - **Storage Classes:** Match the class to access frequency. Use *Standard* for frequently accessed data, *Nearline* for once-a-month, *Coldline* for once-a-quarter, and *Archive* for once-a-year. 
  - **Lifecycle Policies:** Automate the downgrading of objects (e.g., move logs to Archive after 30 days) or automatic deletion.

## 🔗 Integrations & Relationships
*How does this connect to other GCP services?*
- **Integrates well with:** [[01_Services/Networking/Cloud_CDN|Cloud CDN]] (to cache objects globally at the edge), [[01_Services/Analytics/BigQuery|BigQuery]] (querying external tables stored in Cloud Storage), and [[01_Services/Compute/Compute_Engine|Compute Engine]] (storing startup scripts or VM images).
- **Compared to:** [[01_Services/Storage/Persistent_Disk|Persistent Disk]] (Cloud Storage is object storage accessed via API; Persistent Disk is block storage mounted directly to a VM).
- **Operations & IaC:** [[02_Operations_and_IaC/Cloud_Storage_Ops|Cloud Storage Operations]]

#gcp/services/Storage

---
[[00_Index/01_Services_MOC|Back to Services Index]]