# GCP

**GCP** is a product suite that offers services like computing/hosting, storage, networking, and ML resources

**BigQuery** is a serverless, multi-tenant cloud data warehouse that provide scalable analytics and frameworks over large datasets
Terms:
Data Silos: Data collection(s) that are isolated from other systems
Data Warehouse: A central repository of data that can be analyzed (conglomerate of data)

**BigLake** extends BigQuery capabilities (ie. dataplex for data governance) and unifies data warehouses. It maintains a single copy of data nad makes it uniformally accessible to open source engines like Vertex AI

BigLake Tables (querying external data stores) can be used with data in Amazon S3 without copying the data but by reading it without data movement. This is done using BigQuery Omni (because when data gets siloed, it is difficult to get insights the collective store of data) so this can be used for cross-cloud joins/transfers etc.

---

**VertexAI** is an AI platform used to build/deploy/scale ML models on Google Cloud
Terms:
AutoML: model training w/o code/data splits
Custom: write taining code and hyperparameter turning
GenAI: Tune Google's LLM for deployment

Workflow:
Ingest, Analyze, Transform (Data Prep) using Managed Databasets
Train (AutoML or Custom)
Evaluate (explainable AI, which factors lead to predictions)
Deploy (deployment includes scalable resources)
Predict (either batch prediction or deployment prediction)
