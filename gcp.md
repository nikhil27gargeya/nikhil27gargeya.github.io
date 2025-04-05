# GCP

**GCP** is a product suite that offers services like computing/hosting, storage, networking, and ML resources

**BigLake** is cloud native (built and deployed to have microservices with independent scaling and automation). Microservices are an architectural approach where a single application is comprised of smaller independent components or services, which is advantageous for non-intrusive improvements, independent scaling, and testing. For example, a travel website's microservices could be flights, hotels, cars, deals, trip planner, etc.  However, using multiple  services requires more management because these services typically maintain their own stack of technologies including backend services, communicating with one another through the use of APIs. Loosely coupled services align well with DevOps as they are better for testing and reliability in theory, although there could be downstream effects in practice that are caused by upstream services. Microservices are deployed within containers, which are application source code combined with libraries and dependencies needed to run the code. Containers allow for consistent deployment. Very useful for hybrid multicloud (public cloud along with private cloud). Hybrid multicloud allows for customizable on premise infrastructure (which could be cost effective in certain scenarios) while using public cloud services for scalability and serverless options).  At scale, a container orchestration platform like Kubernetes helps automate management. (https://www.ibm.com/think/topics/cloud-native).

**BigLake** is disaggregated, meaning that storage and compute resources are decoupled. Traditionally, storage and compute are integrated within the same server. Decoupling storage and compuae allows for dynamic allocation of storage resources based on what the compute nodes need. Pay as you go model for businesses and higher resource efficiency. 

**BigLake** combines data management needs like security and governance along with flexibility of open source format as it is able to store a variety of data (structured, unstructured) and perform analytics over this data. BigLake tables allows for data governance, BigLake object tables support using BigQuery for unstructured data (treating them as first class citizens that can be queried direclty), and BigQuery Omni is used for non GCP clouds. So to summarize, **BigLake** extends BigQuery capabilities (ie. dataplex for data governance) and unifies data warehouses. It maintains a single copy of data and makes it uniformally accessible to open source engines like Vertex AI for BQML inference.

**Transition to Lakehouse paradigm** Traditional data warehousing is OLAP (multidimensional database) and there is a new convergence to lakehouse architecture that merges the traditional approach with data lakes storing raw data as well as structured data

Workflow for using BQML:
1. Store pre trained model artifact in Cloud Storage Bucket OR use a deployed remotely hosted model on VertexAI
2. CREATE MODEL (import model)
   CREATE MODEL 'model_name'
     OPTIONS (
      MODEL_TYPE = {'TENSORFLOW'},
      MODEL_PATH = 'path_to_model'
     )
4. ML.PREDICT (make predictions)
   //Connect the model if it is a remote model
   //use object tables if unstructured data (ie. images)
   SELECT * //all columns of data will be returned
   FROM
     ML.PREDICT(
       MODEL bqml_test.imported_model, //model
       (SELECT * FROM input_table) //input data for the model
     )

**BigQuery** is a serverless (no need for user to manage servers), multi-tenant cloud (several cloud customers can access the same environment) data warehouse that provide scalable analytics and frameworks over large datasets
Terms:
Data Silos: Data collection(s) that are isolated from other systems
Data Warehouse: A central repository of data that can be analyzed (conglomerate of data)

Clustered (Organizes through sorting) vs Partitioned Data (Smaller Tables)

**BigQuery DataFrames** is a pythonic dataframe API to create regression models and clean up training data. Colab Enterprise Notebooks (where functionality like BQDF and code completion because it is hosted on Google Cloud) are available. Jupyter notebook plugins are also available.

**BigQuery Metastore** is a unified metadata (shorthand representation of other data) service as metastore are typically coupled with data processing engines, and this leads to multiple copies of data. BigQuery Metastore fits in with the lakhouse paradigm of maintaining a single copy of data and a single shared metastore. Tables in Apache Spark, Iceberg, etc. can be queried by BigQuery with a single source of metadata. 

How BigQuery works: Distributed storage using Colossus and Dremel (query engine) to compute data using memory shuffle (for data partitioning) as a middle layer. Slots (units of computation) are allocated to execute queries. Optimizing queries involves limiting bytes through columns needed, late + seldom aggregations (uses less slots/computation), nesting repeated data, and filters before JOINs (preventing larger JOINs).

BigLake Tables (querying external data stores) can be used with data in Amazon S3 (simple storage service) without copying the data but by reading it without data movement. This is done using BigQuery Omni (because when data gets siloed, it is difficult to get insights the collective store of data) so this can be used for cross-cloud joins/transfers etc. 

Cross Cloud Joins (best practice is for one time use)

Cross Cloud Transfer (also for one time use to optimize query performance)

Cross Cloud View (caching is important, and external data can be queried repeatedly)
ie. Google Dashboard for risk detection
The materialized view in BQ summarizes the risk data through a query
Scheduled to refresh daily (SCHEDULE OPTIONS)

---

**VertexAI** is an AI platform used to build/deploy/scale ML models on Google Cloud
Terms:
AutoML: model training w/o code/data splits (for image data in the example of identifying neighborhoods from photos of houses, video data for classification/action recognition/object tracking in the example of sports clips, text data for entity tracking/sentiment analysis in the example of reviews, tabular data for forecasting or predicting categories of customers) 
Custom: write training code and hyperparameter turning
GenAI: Tune Google's LLM for deployment

Workflow:
Ingest, Analyze, Transform (Data Prep) using Managed Databasets
Train (AutoML or Custom)
Evaluate (explainable AI, which factors lead to predictions)
Deploy (deployment includes scalable resources)
Predict (either batch prediction or deployment prediction)

Creating dataset requires identifying the use case:
1. What is outcome to achieve? ie. Classify unsafe driving from dashcam video
2. What categories are needed to achieve this outcome? Normal, Distracted driving (texting, inebriated, eating, talking)
3. Are these human deducible categories? In most cases
4. What are the best representative examples of classificatory data? Varied times of day, noncircumstantial factors (ie. extreme driving conditions)

Ideally have 1000+ examples per data label.

There are various APIs for AI features using Vertex AI endpoints that BigQuery ML supports.
Cloud Natural Language API for NLP on sentiment analysis tasks and classification
Document AI for feature extraction from documents
Computer Vision for image classification

ML.EVALUATE lets you evaluate model metrics (depends on the model) ie. for regression models, the function returns trial_id, precision, recall, accuracy, f1_score, log_loss, roc_auc

Supervised Learning (labeled training data)
Since the output data is already known
1. Classification (predicting categorical label through features which are characteristics of the model used as input to create prediction)
2. Regression (predicting real or continuous value, where the algorithm determines a relationship between 2+ variables)
   
Unsupervised Learning (non labeled training data, identifies pattern through the raw data without instruction)
1. Clustering (ie. K-means clustering or overlapping clustering
2. Association (ie. identifying buying patterns)
   
Hybrid (includes supervised learning)
