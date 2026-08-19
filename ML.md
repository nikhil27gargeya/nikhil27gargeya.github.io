# ML

Topics: machine learning fundamentals, supervised learning, unsupervised learning, reinforcement learning, classification, regression, clustering, training sets, validation sets, test sets, feature engineering, data preprocessing, normalization, standardization, overfitting, underfitting, bias-variance tradeoff, regularization, evaluation metrics, linear regression, logistic regression, decision trees, random forests, gradient boosting, support vector machines, k-nearest neighbors, neural networks, backpropagation, optimization, gradient descent, convolutional neural networks, recurrent neural networks, transformers, embeddings, attention, large language models, prompting, retrieval-augmented generation, fine-tuning, vector databases, model inference, model deployment, MLOps, model monitoring, data drift, model drift

Foundational model is an architecture unique model

Evals:
Understanding the performance of an AI agent in executing tasks, task success, and alignment with user intent (includes benchmark testing, human-in-the-loop assessments, A/B testing and real world simulations) 
Single turn eval is just checking an output against expected output (https://www.ibm.com/think/topics/ai-agent-evaluation)
Agent eval is where there is an agent loop so we need unit tests to verify that the end output is working
An evaluation harness is the infrastructure that runs evals end-to-end. It provides instructions and tools, runs tasks concurrently, records all the steps, grades outputs, and aggregates results

Latency optimization:
Caching, batching

RAG:
We are using AI on our data -> embed the data, store in a vector db, retrieve chunks at a time and prompt on them

Fine tuning is taking a pre-trained LLM (a generalist odel) and providing it a direct dataset to be further trained upont to adjust their inner weights to be better at those types of tasks

Parameter-efficient Fine Tuning (PEFT): Finetuning a subset of parameters

QLoRA: quantizing the precision of the weight parameters in the pre-trained LLM to 4-bit precision (compressed from 32 bit). This reduces the memory footprint of the LLM, making it possible to finetune it on a single GPU. Utilizes adapters (an adapter is a lightweight layer inserted inside a transformer)
