---
service_category: "Networking"
service_model: "IaaS"
management_level: "Fully-Managed"
infrastructure_analogy: "The city's intelligent traffic control system, directing cars to the fastest lanes and diverting them away from closed roads."
---
# Cloud Load Balancing

## 🎯 Definition & Purpose
- A fully distributed, software-defined managed service that scales your applications on Google Cloud by distributing user traffic across multiple instances or regions.
- **Key Differentiator:** Unlike traditional hardware load balancers that sit in a single data center, Google's **Global HTTP(S) Load Balancer** operates at the edge of Google's network (using Anycast IP). A single global IP address can route users to the closest healthy backend region worldwide, enabling true global failover and zero pre-warming.

## 🏙️ City Infrastructure Analogy
- Think of it like a **Global Intelligent Traffic Control System**. When a surge of commuters (traffic) hits the highway, the system doesn't just let them pile up in one lane. It actively monitors which exits (servers) are open and fast, directing cars to the nearest, least-congested off-ramp. If a bridge collapses in one city (regional outage), the traffic system instantly reroutes all cars to a neighboring city without anyone getting lost.

## 🚀 Primary Use Cases
- **Global Web Applications:** Distributing HTTP(S) traffic for a globally available web app to the region closest to the user to minimize latency (Global External Application Load Balancer).
- **High Availability (HA) & Disaster Recovery (DR):** Automatically failing over traffic to a secondary region if the primary region's backend instances fail their health checks.
- **Internal Microservices:** Routing traffic securely between internal backend services (like front-end VMs talking to back-end APIs) without exposing traffic to the public internet (Internal Load Balancer).
- **DDoS Protection:** Terminating malicious traffic at the edge before it reaches your backend servers (when combined with Cloud Armor).
- **Anti-Patterns:** Do not use a Global Load Balancer if strict data sovereignty laws require traffic to remain strictly within a single specific region (use a Regional Load Balancer instead). Do not use Application (Layer 7) load balancing if you need to pass raw TCP/UDP traffic (use a Network Layer 4 Load Balancer).

## 📏 Scaling Limits & Constraints
- **Scalability:** Scales instantly to support millions of requests per second with **no pre-warming** required (a huge differentiator compared to AWS ALB).
- **Hard Quotas & Limits:** There are limits on the number of forwarding rules per project (default 150) and backend services. Health check firewall rules must be specifically configured (allowing `130.211.0.0/22` and `35.191.0.0/16`) or the load balancer will think all backends are dead.

## 💰 Pricing Model
- **Billing Metric:** Billed based on a base hourly charge for the forwarding rules, plus a volumetric charge based on the amount of data processed (per GB).
- **Cost Optimization:** 
  - **Cloud CDN Integration:** Enable Cloud CDN on an External Application Load Balancer. Caching static content at the edge dramatically reduces the data processing costs of the load balancer and the egress costs of the backend servers.
  - **Consolidate Rules:** Share a single load balancer and IP address across multiple backend services using URL maps instead of spinning up separate load balancers for every microservice.

## 🔗 Integrations & Relationships
*How does this connect to other GCP services?*
- **Integrates well with:** [[01_Services/Compute/Compute_Engine|Compute Engine]] (Managed Instance Groups as backends), [[01_Services/Serverless/Cloud_Run|Cloud Run]] (Serverless NEGs as backends), [[01_Services/Security/Cloud_Armor|Cloud Armor]] (WAF rules applied at the load balancer), and [[01_Services/Networking/Cloud_CDN|Cloud CDN]] (edge caching).
- **Compared to:** [[01_Services/Networking/Cloud_DNS|Cloud DNS]] (DNS routes traffic based on name resolution; Load Balancing actively proxies traffic, terminates SSL, and checks server health).
- **Operations & IaC:** [[02_Operations_and_IaC/Cloud_Load_Balancing_Ops|Cloud Load Balancing Operations]]

#services/Networking

---
[[00_Index/01_Services_MOC|Back to Services Index]]