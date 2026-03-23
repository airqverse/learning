---
service_category: Networking
service_model: IaaS
management_level: Fully-Managed
tags:
  - flashcards/services/networking
  - gcp/exam_prep/flashcards
---

# Cloud Load Balancing Flashcards

[[00_Index/05_Exam_Prep_MOC|Back to Exam Prep Index]]

## 1. Cloze Deletion (The Contextual Blank)
*Testing constraints within paragraph context.*

The Global External Application Load Balancer operates at Layer ==7== of the OSI model and routes traffic based on ==HTTP/HTTPS== headers. Unlike regional variants, it requires the ==Premium== Network Tier to provide a single global Anycast IP address. #flashcards/services/networking/load_balancing
<!--SR:!2026-03-26,3,250!2026-03-27,4,270!2026-03-23,1,230-->

When configuring an Internal Proxy Network Load Balancer, it routes ==TCP== traffic and operates exclusively at Layer ==4== without exposing the backend services to the public internet. #flashcards/services/networking/load_balancing
<!--SR:!2026-03-23,1,230!2026-03-24,1,230-->

## 2. Standard Single-line Q&A
*Testing quick recall using the `::` syntax.*

Which GCP Load Balancer uses Maglev technology under the hood to distribute traffic globally? :: Global External Passthrough Network Load Balancer #flashcards/services/networking/load_balancing
<!--SR:!2026-03-23,1,230-->

What is the required network tier for the Global External Application Load Balancer? :: Premium Tier #flashcards/services/networking/load_balancing
<!--SR:!2026-03-26,3,250-->

## 3. Multi-line Q&A (Exam-Style Scenarios)
*Testing deep analytical judgment using the `?` syntax.*

**Scenario:** You need to migrate a legacy application that relies on non-HTTP(S) SSL traffic. The application serves clients globally, and you must terminate SSL at the edge to offload processing from your backend VM instances. Which load balancing architecture is required?
?
**Answer:** Global External Proxy Network Load Balancer (SSL Proxy).
*Reasoning:*
- "Global" + "Edge termination" for non-HTTP(S) SSL strictly requires the SSL Proxy.
- Passthrough load balancers cannot terminate SSL at the edge.
#flashcards/services/networking/load_balancing
<!--SR:!2026-03-23,1,230-->

**Scenario:** Your microservices deployed on Google Kubernetes Engine (GKE) in `us-central1` need to securely load balance internal gRPC traffic between each other. The endpoints cannot be exposed to the public internet. Which load balancer should you implement?
?
**Answer:** Regional Internal Application Load Balancer.
*Reasoning:*
- It operates at Layer 7 (required for gRPC).
- It is Internal (no public internet exposure).
- It handles regional GKE traffic efficiently.
#flashcards/services/networking/load_balancing
<!--SR:!2026-03-24,1,230-->

## 4. Block Transclusion (The DRY Principle)
*Demonstrating how to reference a source of truth block from a parent note. This avoids duplicating code or definitions directly into the card.*

What is the architectural difference between Proxy and Passthrough load balancers in GCP?
?
![[Cloud_Load_Balancing^proxy-vs-passthrough]]
*(Note: If the `Cloud_Load_Balancing` note is updated, this flashcard's answer updates automatically).*
#flashcards/services/networking/load_balancing
<!--SR:!2026-03-23,1,230-->