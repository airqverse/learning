---
service_category: "Analytics"
service_model: "PaaS"
management_level: "Managed"
infrastructure_analogy: "A temporary, pop-up assembly line that processes raw materials quickly and is dismantled to save costs."
---
# Cloud Dataproc

## 🎯 Definition & Purpose
- A fully managed and highly scalable service for running Apache Hadoop, Apache Spark, Apache Flink, Presto, and other open-source data tools.
- **Key Differentiator:** Emphasizes **ephemeral clusters** and the separation of compute and storage. Instead of keeping a Hadoop cluster running 24/7 with data on HDFS, you store data cheaply in Cloud Storage, spin up a Dataproc cluster in 90 seconds to process it, and shut it down immediately after.

## 🏙️ City Infrastructure Analogy
- Think of it like a **Pop-Up Factory or Assembly Line**. If a city suddenly receives a massive shipment of unrefined raw materials, instead of building a permanent factory that sits empty half the year, they rent specialized equipment for the weekend, process everything, and immediately dismantle the setup to stop paying rent.

## 🚀 Primary Use Cases
- **Lift and Shift Hadoop/Spark:** Migrating existing on-premises Hadoop or Spark clusters to the cloud without rewriting code.
- **Batch Data Processing (ETL):** Processing large logs, cleaning up datasets, or transforming massive amounts of unstructured data on a schedule.
- **Machine Learning:** Training machine learning models using Apache Spark MLlib on large datasets.
- **Anti-Patterns:** Not ideal for real-time, low-latency stream processing where you need a serverless, auto-scaling pipeline (use Cloud Dataflow). Also not recommended for ad-hoc, interactive SQL queries on structured data (use BigQuery).

## 📏 Scaling Limits & Constraints
- **Scalability:** Clusters can scale up to thousands of nodes. Supports **Autoscaling** to add or remove worker nodes based on YARN memory metrics.
- **Hard Quotas & Limits:** Bound by underlying Compute Engine quotas (CPUs, IP addresses, disk quotas in the region/zone). Startup times are remarkably fast, typically under 90 seconds.

## 💰 Pricing Model
- **Billing Metric:** Billed per vCPU second for the Dataproc premium layer, *plus* the standard underlying costs for Compute Engine (VMs) and Cloud Storage.
- **Cost Optimization:** 
  - **Use Ephemeral Clusters:** The most critical cost-saving measure is deleting the cluster when the job finishes.
  - **Use Preemptible/Spot VMs:** Add Preemptible VMs as secondary workers to drastically reduce compute costs for fault-tolerant batch jobs.

## 🔗 Integrations & Relationships
*How does this connect to other GCP services?*
- **Integrates well with:** [[01_Services/Storage/Cloud_Storage|Cloud Storage]] (acts as a replacement for HDFS), [[01_Services/Analytics/BigQuery|BigQuery]] (via Dataproc BigQuery connector), and [[01_Services/Compute/Compute_Engine|Compute Engine]].
- **Compared to:** [[01_Services/Analytics/Cloud_Dataflow|Cloud Dataflow]] (Dataproc is server-based, open-source Spark/Hadoop; Dataflow is serverless Apache Beam) and [[01_Services/Analytics/BigQuery|BigQuery]] (Dataproc is for complex programmatic transformations; BigQuery is a data warehouse for SQL analytics).
- **Operations & IaC:** [[02_Operations_and_IaC/Cloud_Dataproc_Ops|Cloud Dataproc Operations]]

#services/Analytics

---
[[00_Index/01_Services_MOC|Back to Services Index]]