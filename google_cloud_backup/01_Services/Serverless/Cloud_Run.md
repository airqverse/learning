---
service_category: "Serverless"
service_model: "CaaS"
management_level: "Serverless"
infrastructure_analogy: "An on-demand, highly trained task force that sits idle until summoned, completing the job instantly and then dispersing."
---
# Cloud Run

## 🎯 Definition & Purpose
- A fully managed compute platform that automatically scales your stateless containers.
- **Key Differentiator:** Abstracts away all infrastructure management while still giving you the flexibility of using Docker containers. Unlike App Engine, which has strict language runtimes, if your code can be built into a container and listen for HTTP requests on a port, it can run on Cloud Run.

## 🏙️ City Infrastructure Analogy
- Think of it like an **On-Demand Strike Team / Task Force**. You provide the blueprint for the soldier (the Docker container). When the city is quiet, there are zero soldiers on payroll (Scale to Zero). The second an emergency call (HTTP request) comes in, the city instantly spawns the exact number of soldiers needed to handle the crisis. Once the crisis is over, they vanish, and you stop paying.

## 🚀 Primary Use Cases
- **Web Services and APIs:** Hosting RESTful or gRPC APIs that experience spiky, unpredictable traffic and need to scale from zero to hundreds of instances in seconds.
- **Background Event Processing:** Triggering microservices via Eventarc when a new file is uploaded to Cloud Storage or a message is published to Pub/Sub.
- **Microservices Architecture:** Decoupling a monolith into smaller, independently scalable containerized services.
- **Scheduled Jobs:** Running periodic data processing tasks (using Cloud Scheduler to trigger the Cloud Run service or using Cloud Run Jobs).
- **Anti-Patterns:** Not suitable for applications that require heavy persistent local state (containers are stateless; use Cloud SQL or Firestore for state). Not ideal for legacy applications that require background processes that run 24/7 without HTTP traffic (consider Compute Engine or GKE).

## 📏 Scaling Limits & Constraints
- **Scalability:** Automatically scales instances based on incoming request volume or CPU utilization. A massive differentiator is that a single Cloud Run container instance can handle **concurrent requests** (up to 1,000 per instance), unlike Cloud Functions which handles one request per instance.
- **Hard Quotas & Limits:** Default request timeout is 5 minutes, configurable up to 60 minutes. Maximum memory per instance is 32 GiB; maximum vCPU per instance is 8. Cannot use background threads when the instance is not actively processing a request (unless CPU allocation is explicitly set to "always on").

## 💰 Pricing Model
- **Billing Metric:** Billed per 100 milliseconds of vCPU and memory allocated *only* while the container is actively processing a request (unless "CPU always allocated" is enabled). Also billed for network egress.
- **Cost Optimization:** 
  - **Concurrency:** Maximize the `concurrency` setting. If your container can handle 80 simultaneous requests without performance degradation, you pay for 1 instance instead of 80 separate instances.
  - **Scale to Zero:** Ensure your minimum instances setting is `0` for environments that don't receive 24/7 traffic (like dev/staging). 

## 🔗 Integrations & Relationships
*How does this connect to other GCP services?*
- **Integrates well with:** [[01_Services/Databases/Cloud_SQL|Cloud SQL]] (via built-in Cloud SQL Auth Proxy), [[01_Services/Storage/Cloud_Storage|Cloud Storage]] (to trigger event-driven processing via Eventarc), and [[01_Services/Networking/Cloud_Load_Balancing|Cloud Load Balancing]] (via Serverless NEGs to put a global Anycast IP in front of Cloud Run).
- **Compared to:** [[01_Services/Serverless/Cloud_Functions|Cloud Functions]] (Functions are snippet-based and single-concurrency; Run is container-based and multi-concurrency), [[01_Services/Compute/App_Engine|App Engine]] (App Engine is older PaaS with strict runtimes; Run is modern CaaS using any container), and [[01_Services/Compute/Google_Kubernetes_Engine|GKE]] (GKE requires managing the cluster; Run is fully serverless).
- **Operations & IaC:** [[02_Operations_and_IaC/Cloud_Run_Ops|Cloud Run Operations]]

#services/Serverless

---
[[00_Index/01_Services_MOC|Back to Services Index]]