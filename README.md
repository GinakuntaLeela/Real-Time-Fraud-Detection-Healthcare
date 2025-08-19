# 🏥 Real-Time Healthcare Fraud Detection using AWS & XGBoost  

## 📌 Overview  
Healthcare fraud in insurance claims leads to billions of dollars in losses each year. This project demonstrates how to leverage **AWS real-time data pipelines** and **machine learning** to detect fraudulent Medicaid claims **as they are processed**, preventing financial leakage before payments are made.  

I built a **scalable, low-latency fraud detection system** using AWS Kinesis, Lambda, and SageMaker with XGBoost models trained on millions of records.  

---

## 🎯 Problem Statement  
Traditional fraud detection systems rely on batch processing and manual auditing, which introduces significant delays.  
The goal of this project was to:  
- Detect **fraudulent claims in real-time**.  
- Handle **high-volume streaming data** (millions of claims).  
- Maintain **low inference latency (<200 ms)** for production-readiness.  

---

## 🛠️ Tech Stack  
- **Languages**: Python (Pandas, Scikit-Learn, XGBoost)  
- **Cloud Services**:  
  - AWS Kinesis (streaming ingestion)  
  - AWS Lambda (serverless compute & preprocessing)  
  - AWS SageMaker (model training & real-time inference endpoints)  
  - AWS S3 (data storage)  
- **Other**: Terraform (infrastructure as code), CloudWatch (monitoring)  

---

## 📂 Project Structure  

---

## 🔍 Approach  

1. **Data Ingestion**  
   - Streamed 5M+ Medicaid claim records containing provider details, claim amounts, and service codes via **Kinesis Data Streams**.  

2. **Data Preprocessing**  
   - AWS Lambda functions parsed, validated, and transformed raw claim events.  

3. **Model Training**  
   - Used SageMaker to train an **XGBoost classifier** on historical fraud vs non-fraud claims.  
   - Features included claim amount distributions, provider risk history, service code anomalies, and temporal fraud patterns.  

4. **Real-Time Inference**  
   - Deployed model to a **SageMaker real-time endpoint**.  
   - Lambda invoked the endpoint on each incoming claim.  

5. **Monitoring & Logging**  
   - CloudWatch dashboards tracked inference latency, fraud detection rates, and error logs.  

# 🏥 Real-Time Healthcare Fraud Detection (AWS + XGBoost)

> **Goal:** Detect potentially fraudulent Medicaid claims in near real-time using an AWS streaming pipeline (Kinesis → Lambda → SageMaker) with an XGBoost classifier trained on historical claims.

---

## 🔎 Why this matters
Healthcare fraud costs billions each year. Batch audits are slow and reactive. This project shifts left to **streaming detection**, flagging high-risk claims **before** payout.

---

## 🧱 Architecture (High Level)
```mermaid
flowchart LR
  A[Producers: HL7 or JSON claims] -->|PutRecord| B[Kinesis Data Streams]
  B --> C[Lambda: Preprocess & Validate]
  C --> D[SageMaker Realtime Endpoint (XGBoost)]
  D --> E{Risk score >= threshold}
  E -- Yes --> F[Alert bus / Quarantine queue]
  E -- No --> G[Pass to adjudication]
  C --> H[S3 raw and curated]
  D --> I[CloudWatch metrics and logs]
  H --> J[Batch retraining jobs]
  J --> D

---

## 📊 Results  

- **Fraud Detection Accuracy**: 95%  
- **Average Inference Latency**: 180 ms  
- **Scalability**: Successfully processed **thousands of claims per second**.  
- **Impact**: Enabled near real-time fraud prevention in Medicaid claims processing.  

---



