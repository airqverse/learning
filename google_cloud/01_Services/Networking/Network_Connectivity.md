---
service_category: "Networking"
service_model: "IaaS"
management_level: "Fully-Managed"
infrastructure_analogy: "The bridges, tunnels, and highways connecting the city to the rest of the world."
---
# Network Connectivity

## 🎯 Definition & Purpose
- Google Cloud **Network Connectivity** encompasses the suite of services used to connect your on-premises infrastructure, other cloud providers, and remote users to your Google Cloud VPC networks.
- **Key Differentiator:** Google's global private network backbone. Once traffic enters a Google edge location, it travels on Google's private fiber, avoiding the public internet for lower latency, higher throughput, and better security.

## 🏙️ City Infrastructure Analogy
- Think of Network Connectivity as the **external transportation infrastructure**:
  - **Cloud Interconnect:** A massive, dedicated multi-lane bridge built exclusively for heavy freight trucks (high bandwidth, low latency, private connection).
  - **Cloud VPN:** A secure, armored tunnel running underneath public roads (encrypted connection over the public internet).
  - **Cloud Router:** The sophisticated traffic control center at the border that dynamically updates maps for all incoming and outgoing vehicles (BGP dynamic routing).
  - **Network Connectivity Center (NCC):** The central dashboard managing all global bridges, tunnels, and highways from a single pane of glass.

## 🚀 Primary Use Cases
- **Scenario 1 (Hybrid Cloud Migration):** An enterprise migrating to GCP establishes a **Dedicated Interconnect** to move petabytes of on-premises database data securely and quickly into Cloud Storage without traversing the public internet.
- **Scenario 2 (Secure Remote Access):** Establishing an **HA VPN (High Availability VPN)** connection over the public internet between a small regional branch office and a GCP VPC to access internal applications securely.
- **Scenario 3 (Multi-Cloud Connectivity):** Using **Cross-Cloud Interconnect** to establish a direct, private link between Google Cloud and AWS or Azure for multi-cloud data processing architectures.
- **Anti-Patterns:** Do not use Cloud VPN for sustained, massive data transfers (it's limited by internet bandwidth and VPN gateway quotas; use Interconnect instead). Do not use Dedicated Interconnect for small, temporary workloads (it's expensive and takes weeks to provision physically).

## 📏 Scaling Limits & Constraints
- **Scalability:** 
  - **Cloud VPN:** HA VPN offers an SLA of 99.99%. Each tunnel supports up to 3 Gbps.
  - **Cloud Interconnect:** Scales from 50 Mbps (Partner Interconnect) up to 100 Gbps or multiple 100 Gbps circuits (Dedicated Interconnect).
- **Hard Quotas & Limits:** 
  - **Cloud Router:** BGP learned routes are strictly limited (e.g., typically 10,000 to 100,000 depending on the configuration and peering limits).
  - **Cloud VPN:** Maximum of 100 tunnels per region per VPC network.

## 💰 Pricing Model
- **Billing Metric:** 
  - **Cloud Interconnect:** Billed by a flat monthly port fee (based on capacity) plus egress data transfer rates (which are heavily discounted compared to standard internet egress).
  - **Cloud VPN:** Billed an hourly rate for each active tunnel plus standard internet egress data transfer costs.
  - **Cloud Router:** Billed an hourly rate per router, plus premium charges if routing traffic globally.
- **Cost Optimization:** For consistent, high-volume data egress, Cloud Interconnect is often cheaper than Cloud VPN or public internet because the per-GB egress rate is significantly lower, offsetting the fixed port costs.

## 🔗 Integrations & Relationships
*How does this connect to other GCP services?*
- **Integrates well with:** [[01_Services/Networking/VPC_Network|VPC Network]] (the destination for all these connections), [[01_Services/Networking/Network_Services|Network Services]] (Cloud DNS can resolve names across VPN/Interconnect using forwarding zones).
- **Compared to:** AWS Direct Connect or Azure ExpressRoute (equivalents to Cloud Interconnect).
- **Operations & IaC:** [[02_Operations_and_IaC/Networking_Ops|Networking Operations]]

## ⚙️ Architecture & Configurations

### Cloud Interconnect
- **Description:** Provides direct physical connections between your on-premises network and Google's network. 
- **Use Case:** **Dedicated Interconnect** requires a physical presence in a colocation facility. **Partner Interconnect** uses a third-party service provider to bridge the gap if you cannot physically meet Google.

### Cloud VPN (Virtual Private Network)
- **Description:** Securely connects your peer network to your Virtual Private Cloud (VPC) network through an IPsec VPN connection.
- **Use Case:** **HA VPN** provides an industry-leading 99.99% SLA using dynamic BGP routing and redundant tunnels. **Classic VPN** is deprecated for new deployments.

### Cloud Router
- **Description:** Enables dynamic Border Gateway Protocol (BGP) route updates between your GCP VPC and your on-premises network.
- **Use Case:** Automatically propagating new VPC subnets to your on-premises routers without requiring manual configuration updates on both sides of the VPN or Interconnect.

### Network Connectivity Center
- **Description:** A hub-and-spoke model for managing network connectivity across Google Cloud, multi-cloud, and on-premises environments.
- **Use Case:** Using Google's global backbone to route traffic *between* two different on-premises data centers (Data Center A -> GCP Backbone -> Data Center B).

#services/networking

---
[[00_Index/01_Services_MOC|Back to Services Index]]