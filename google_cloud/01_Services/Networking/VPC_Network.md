---
service_category: "Networking"
service_model: "IaaS"
management_level: "Fully-Managed"
infrastructure_analogy: "A private, gated city infrastructure with custom roads (routes) and checkpoints (firewalls)."
---
# VPC Network

## 🎯 Definition & Purpose
- Google Cloud Virtual Private Cloud (VPC) provides networking functionality to Compute Engine virtual machine (VM) instances, Google Kubernetes Engine (GKE) clusters, and serverless environments. It is a comprehensive, software-defined network.
- **Key Differentiator (Global vs. Regional):** GCP VPCs are **Global** resources (spanning the entire world), whereas subnets are **Regional**. This means instances in different regions can communicate via internal IP addresses within the same VPC without needing complex peering configurations.
- **Key Differentiator (No VPC-level IP Ranges):** Unlike other cloud providers (e.g., AWS), a GCP VPC network *itself* does not have an IP address range (CIDR block) assigned to it. The VPC is simply a global logical construct. All IP ranges are strictly defined at the **Subnet** level within specific regions.

## 🏙️ City Infrastructure Analogy
- **Think of it like a private, globally connected gated community.** 
- The **VPC** is the master blueprint of the city limits. 
- **Subnets** are the specific neighborhoods (regions). 
- **Routes** are the roads connecting them. 
- **Firewall rules** are the security guards at every house (VM), deciding who is allowed to enter (ingress) or leave (egress).

## 🚀 Primary Use Cases
- **Scenario 1:** Providing secure, private internal IP communication between compute resources (VMs, GKE clusters) across multiple regions worldwide.
- **Scenario 2:** Connecting an on-premises enterprise data center to Google Cloud seamlessly using Cloud Interconnect or Cloud VPN.
- **Scenario 3:** Isolating environments (e.g., Development, Staging, Production) by placing them in distinct, tightly controlled custom VPCs.
- **Anti-Patterns:** Using the "Auto-mode" default VPC for production environments. Always use "Custom-mode" VPCs to retain full control over IP address ranges and prevent overlapping subnets, especially when planning future VPC peering or on-premise connections.

## 📏 Scaling Limits & Constraints
- **Scalability:** Powered by Google's Andromeda software-defined networking stack, VPCs scale automatically to handle massive throughput without the need to provision virtual routers for basic routing.
- **Hard Quotas & Limits:**
  - **VPCs per project:** 5 (Default), can be increased up to 15 networks or higher.
  - **Subnets per project:** 7,000 (Default)
  - **VPC Peering:** Peering is strictly **non-transitive** (If A peers with B, and B peers with C, A cannot talk to C). Max 25 active peering connections per VPC network.

## 💰 Pricing Model
- **Billing Metric:** 
  - **Ingress:** Generally free.
  - **Egress:** Charged based on destination. Egress to the same zone is free. Egress between zones in the same region has a cost. Egress between regions has a higher cost. Egress to the public internet is the most expensive.
- **Cost Optimization:** Keep traffic localized (same zone/region) whenever possible. Use Premium Network Tier for performance, but Standard Network Tier can reduce costs for outbound traffic that doesn't need to traverse Google's private global backbone.

## 🔗 Integrations & Relationships
*How does this connect to other GCP services?*
- **Integrates well with:** [[01_Services/Networking/Cloud_Load_Balancing|Cloud Load Balancing]] (for distributing traffic into the VPC), [[01_Services/Compute/Compute_Engine|Compute Engine]] (workloads running inside).
- **Advanced Networking:** Serverless VPC Access (to let Cloud Run/Functions access internal VPC resources).
- **Operations & IaC:** [[02_Operations_and_IaC/VPC_Ops|VPC Operations]]

## ⚙️ Architecture & Configurations

### Auto vs. Custom Mode
- **Description:** Auto-mode automatically creates one subnet per GCP region with predefined IP ranges. Custom-mode starts with zero subnets, giving administrators full control over IP space.
- **Use Case:** Custom-mode is mandatory for production to avoid IP overlap, especially when implementing Hybrid Cloud connections or VPC Peering.

### Shared VPC
- **Description:** Allows an organization to connect resources from multiple distinct Google Cloud projects to a common VPC network. One project is designated as the "Host Project," while others are "Service Projects."
- **Use Case:** Centralized network administration. Network security teams control the Host Project (firewalls, subnets, routes), while developers manage isolated Service Projects for deploying application resources like VMs and GKE clusters.

### VPC Network Peering
- **Description:** Allows private, internal IP connectivity across two different VPC networks regardless of whether they belong to the same project or the same organization.
- **Use Case:** Connecting a SaaS provider's GCP VPC securely to a customer's GCP VPC without routing traffic over the public internet. Remember: it is non-transitive.

### Firewall Rules
- **Description:** Stateful inspection firewalls applied directly at the Virtual Machine's Network Interface (NIC). They can be defined using IP ranges, Network Tags, or Service Accounts.
- **Use Case:** Restricting access so that only backend database VMs (tagged `db-tier`) can receive traffic from web server VMs (using Service Account `web-sa`). Best practice dictates using Service Accounts over Network Tags for strict security.

#services/networking

---
[[00_Index/01_Services_MOC|Back to Services Index]]