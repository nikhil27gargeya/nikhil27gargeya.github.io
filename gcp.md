# GCP

**GCP** is a product suite that offers services like computing/hosting, storage, networking, and ML resources

**BigLake** is cloud native (built and deployed to have microservices with independent scaling and automation). Microservices are an architectural approach where a single application is comprised of smaller independent components or services. These services typically maintain their own stack of technologies including backend services, communicating with one another through the use of APIs. These fits in with DevOps as loosely coupled services are better for testing and reliability in theory, although there could be downstream effects in practice that are caused by upstream services. Microservices are deployed within containers, which are application source code combined with 

https://www.ibm.com/think/topics/cloud-native

**BigQuery** is a serverless, multi-tenant cloud data warehouse that provide scalable analytics and frameworks over large datasets
Terms:
Data Silos: Data collection(s) that are isolated from other systems
Data Warehouse: A central repository of data that can be analyzed (conglomerate of data)

**BigLake** extends BigQuery capabilities (ie. dataplex for data governance) and unifies data warehouses. It maintains a single copy of data and makes it uniformally accessible to open source engines like Vertex AI

How BigQuery works: Distributed storage using Colossus and Dremel to compute data using memory shuffle (for data partitioning) as a middle layer. Slots (units of computation) are allocated to execute queries. Optimizing queries involves limiting bytes through columns needed, late + seldom aggregations (uses less slots/computation), nesting repeated data, and filters before JOINs (preventing larger JOINs).

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
