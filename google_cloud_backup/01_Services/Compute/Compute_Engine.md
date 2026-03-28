---
service_category: "Compute"
service_model: "IaaS"
management_level: "Unmanaged"
infrastructure_analogy: "Renting an empty building in the city where you provide the furniture, maintenance, and rules."
---
# Compute Engine

## 🎯 Definition & Purpose
- Google Compute Engine (GCE) delivers scalable, high-performance virtual machines (VMs) running in Google's data centers and worldwide fiber network.
- **Key Differentiator:** Offers Custom Machine Types (allowing you to tailor vCPU and memory exactly to your workload), transparent Live Migration (minimizing downtime during host maintenance), and sustained-use discounts that apply automatically.

## 🏙️ City Infrastructure Analogy
- "Think of it like renting an empty building in the city where you provide the furniture, maintenance, and rules." You get the raw space and utilities (compute, storage, network), but you are entirely responsible for the operating system, security patching, and managing the application runtime.

## 🚀 Primary Use Cases
- **Scenario 1:** Lift-and-shift migrations of existing on-premises virtual machines to the cloud without re-architecting.
- **Scenario 2:** Running specialized enterprise applications (like SAP, Active Directory, or legacy monolithic apps) that require specific OS environments or kernel-level modifications.
- **Scenario 3:** High-performance computing (HPC) or intensive batch processing workloads requiring attached GPUs or TPUs.
- **Anti-Patterns:** Do not use GCE for simple, stateless web applications or microservices. Using Cloud Run (serverless) or App Engine would drastically reduce operational overhead and cost for these workloads.

## 📏 Scaling Limits & Constraints
- **Scalability:** Scales horizontally via Managed Instance Groups (MIGs) based on CPU utilization, load balancing capacity, or custom Cloud Monitoring metrics.
- **Hard Quotas & Limits:** VMs can have up to 416 vCPUs and 5.75 TB of memory (depending on the machine family). Persistent disks can scale up to 64 TB per volume. Network egress bandwidth is generally capped based on the number of vCPUs assigned to the VM.

## 💰 Pricing Model
- **Billing Metric:** Per-second billing with a 1-minute minimum. You are charged for vCPU, memory, storage (Persistent Disks), and network egress.
- **Cost Optimization:**
  - Use **Spot VMs** (formerly Preemptible VMs) for fault-tolerant, interruptible batch jobs to get up to a 91% discount.
  - Leverage **Sustained Use Discounts** (applied automatically for running a VM for a significant portion of the billing month) or **Committed Use Discounts** (1- or 3-year commitments).
  - Apply **Right-sizing Recommendations** from the Cloud Console to eliminate over-provisioned resources.

## 🔗 Integrations & Relationships
*How does this connect to other GCP services?*
- **Integrates well with:** [[01_Services/Networking/Cloud_Load_Balancing|Cloud Load Balancing]] (for distributing traffic to MIGs), [[01_Services/Storage_and_Databases/Cloud_Storage|Cloud Storage]] (for storing backups, snapshots, and startup scripts).
- **Compared to:** [[01_Services/Compute/Google_Kubernetes_Engine|GKE]] (Containers as a Service) vs. [[01_Services/Compute/Cloud_Run|Cloud Run]] (Serverless). GCE gives maximum control at the cost of high management overhead.
- **Operations & IaC:** [[02_Operations_and_IaC/Compute_Engine_Ops|Compute Engine Operations]]

#services/compute

---
[[00_Index/01_Services_MOC|Back to Services Index]]
