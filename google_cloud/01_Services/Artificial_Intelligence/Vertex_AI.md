---
service_category: "Artificial_Intelligence"
service_model: "PaaS"
management_level: "Fully-Managed"
infrastructure_analogy: "A comprehensive city research hub and university, offering both off-the-shelf experts and facilities to train your own."
---
# Vertex AI

## 🎯 Definition & Purpose
- A fully managed, unified machine learning (ML) platform that allows data scientists and developers to build, deploy, and scale ML models faster.
- **Key Differentiator:** It unifies all of Google Cloud's ML services (formerly AI Platform and AutoML) into a single UI and API, providing end-to-end MLOps capabilities including Model Registry, Feature Store, and Pipelines. It also includes Generative AI capabilities via Vertex AI Studio.

## 🏙️ City Infrastructure Analogy
- Think of it like the city's **Central Research Hub**. You can either hire pre-trained "scholars" to do standard jobs without teaching them (AutoML / Pre-trained APIs) or you can rent out the laboratories and equipment to train your own custom "scientists" from scratch (Custom Training & MLOps).

## 🚀 Primary Use Cases
- **AutoML (No-code ML):** Quickly training high-quality models for image classification, tabular data prediction, or text sentiment analysis with minimal ML expertise.
- **Custom Model Training:** Training complex deep learning models using frameworks like TensorFlow, PyTorch, or Scikit-learn on distributed GPU/TPU clusters.
- **Generative AI:** Building applications powered by Google's foundational models (like Gemini) using Vertex AI Studio to generate text, code, or images.
- **MLOps:** Managing the entire ML lifecycle—deploying models to endpoints, monitoring for data drift, and automating retraining pipelines.
- **Anti-Patterns:** Not recommended if you simply need basic, out-of-the-box predictions where a dedicated API (like Cloud Vision API or Natural Language API) already exists and suffices. Do not use for general-purpose batch data ETL without ML (use Dataflow or Dataproc instead).

## 📏 Scaling Limits & Constraints
- **Scalability:** Prediction endpoints can auto-scale based on traffic, down to zero for cost savings (depending on the configuration). Distributed training scales across hundreds of GPUs/TPUs.
- **Hard Quotas & Limits:** Bounded by project-level quotas for specific GPU/TPU types per region. There are also limits on concurrent batch prediction jobs and API request rates.

## 💰 Pricing Model
- **Billing Metric:** Pricing is complex and divided by capability: 
  - **Training:** Billed per node-hour (Compute + GPU/TPU) used during training.
  - **Prediction:** Billed per node-hour for deployed endpoints or per prediction for serverless/AutoML.
  - **Generative AI:** Billed per 1,000 characters input/output, or per generated image.
- **Cost Optimization:** Turn off unused prediction endpoints. Use smaller, cheaper machine types for model experimentation and testing before scaling up to expensive A100/H100 GPUs for full training. Use batch predictions instead of online endpoints if real-time responses aren't required.

## 🔗 Integrations & Relationships
*How does this connect to other GCP services?*
- **Integrates well with:** [[01_Services/Analytics/BigQuery|BigQuery]] (BigQuery ML models can be registered in Vertex AI Model Registry), [[01_Services/Storage/Cloud_Storage|Cloud Storage]] (for storing training data and model artifacts), and [[01_Services/Compute/Compute_Engine|Compute Engine]] (underlying infrastructure for custom notebooks).
- **Compared to:** [[01_Services/Analytics/BigQuery|BigQuery ML]] (BigQuery ML is for SQL users doing basic ML on structured data; Vertex AI is for complex, custom, or unstructured ML workloads).
- **Operations & IaC:** [[02_Operations_and_IaC/Vertex_AI_Ops|Vertex AI Operations]]

#gcp/services/Artificial_Intelligence

---
[[00_Index/01_Services_MOC|Back to Services Index]]