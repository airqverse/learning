---
service_category: "Serverless"
service_model: "FaaS"
management_level: "Serverless"
infrastructure_analogy: "A single-task automated toll booth that performs one specific action instantly every time a coin (event) is dropped."
---
# Cloud Functions

## 🎯 Definition & Purpose
- A lightweight, fully managed, serverless execution environment for building and connecting cloud services. It allows you to write simple, single-purpose functions that are attached to events emitted from your cloud infrastructure and services.
- **Key Differentiator:** It is highly code-centric. You deploy source code snippets (Node.js, Python, Go, Java, etc.) directly without needing to write a Dockerfile or manage containers (unlike Cloud Run).

## 🏙️ City Infrastructure Analogy
- Think of it like a **Single-Task Automated Toll Booth**. It sits there doing absolutely nothing (and costing nothing) until a car pulls up and drops a coin (an event trigger). The machine wakes up, performs its one specific programmed task (opens the gate, flashes a camera), and immediately goes back to sleep. 

## 🚀 Primary Use Cases
- **Event-Driven Processing:** Automatically resizing an image immediately after it is uploaded to a Cloud Storage bucket.
- **Data Ingestion & ETL:** Processing real-time data streams by triggering a function every time a new message is published to a Pub/Sub topic.
- **Lightweight Webhooks:** Building simple HTTP APIs or webhook endpoints for third-party integrations (like Stripe or GitHub webhooks).
- **Firebase Backend:** Writing backend logic for mobile and web apps built on Firebase (e.g., reacting to new user sign-ups or Firestore database writes).
- **Anti-Patterns:** Not suitable for complex, multi-tiered applications or APIs with dozens of endpoints (use Cloud Run or App Engine). Not suitable for long-running batch jobs that exceed the maximum execution timeout (use Cloud Run Jobs or Dataproc).

## 📏 Scaling Limits & Constraints
- **Scalability:** Automatically scales up to handle massive influxes of events and scales down to zero when idle. 
- **Hard Quotas & Limits:** 
  - **Generation 1:** Maximum execution timeout is 9 minutes (540 seconds). Each instance handles exactly one concurrent request.
  - **Generation 2:** Built on top of Cloud Run and Eventarc. Maximum execution timeout increases to 60 minutes for HTTP requests, and it supports processing concurrent requests on a single instance.
- **Cold Starts:** When a function scales from zero, the initial request takes longer to process as the environment initializes. This can be mitigated by configuring "Minimum Instances."

## 💰 Pricing Model
- **Billing Metric:** Billed based on the number of invocations (requests), compute time (measured in 100-millisecond increments), and the amount of memory/CPU provisioned.
- **Cost Optimization:** 
  - Keep functions lean and minimize dependencies to reduce cold start times and compute duration.
  - Use Generation 2 functions to take advantage of concurrency, processing multiple requests per instance rather than spinning up a new instance for every single event.

## 🔗 Integrations & Relationships
*How does this connect to other GCP services?*
- **Integrates well with:** [[01_Services/Storage/Cloud_Storage|Cloud Storage]] (Object finalize triggers), [[01_Services/Integration_Services/Pub_Sub|Pub/Sub]] (Message published triggers), and [[01_Services/Databases/Firestore|Firestore]] (Document change triggers).
- **Compared to:** [[01_Services/Serverless/Cloud_Run|Cloud Run]] (Cloud Functions is for code snippets and simple event glue; Cloud Run is for full containerized applications). Cloud Functions Gen 2 is actually deployed as a Cloud Run service under the hood.
- **Operations & IaC:** [[02_Operations_and_IaC/Cloud_Functions_Ops|Cloud Functions Operations]]

#gcp/services/Serverless

---
[[00_Index/01_Services_MOC|Back to Services Index]]