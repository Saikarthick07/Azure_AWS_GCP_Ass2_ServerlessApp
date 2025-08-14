# CST8917 – Serverless Applications

# Cloud Serverless Services Comparison

## Objective

This document compares the **Microsoft Azure** serverless services used in the "Serverless Application" course with their **Amazon Web Services (AWS)** and **Google Cloud Platform (GCP)** equivalents.  
The goal is to highlight similarities and differences in **features, triggers/bindings, integration options, monitoring**, and **pricing** for real-world architecture decisions.

---

## Quick Service Mapping

| Azure Service | AWS Equivalent | GCP Equivalent |
|---------------|---------------|----------------|
| Azure Functions | AWS Lambda | Cloud Functions |
| Durable Functions | Step Functions (with Lambda) | Workflows |
| Azure Logic Apps | AWS Step Functions (Workflow) & EventBridge Scheduler | Workflows (and Cloud Scheduler) |
| Azure Service Bus (Queues & Topics) | Amazon SQS & SNS | Pub/Sub |
| Azure Event Grid | Amazon EventBridge | Eventarc |
| Azure Event Hubs | Amazon Kinesis Data Streams | Pub/Sub (Streaming) |

---

## Detailed Comparisons

---

### 1. Azure Functions

| Feature | Azure Functions | AWS Lambda | GCP Cloud Functions |
|---------|-----------------|------------|---------------------|
| **Overview** | Event-driven serverless compute with triggers/bindings | Event-driven serverless compute | Event-driven serverless compute |
| **Triggers/Bindings** | HTTP, Blob, Queue, Timer, Event Hub, Event Grid, Cosmos DB, Service Bus | API Gateway, S3, DynamoDB, EventBridge, SQS, SNS, Step Functions | HTTP, Cloud Storage, Pub/Sub, Firestore, Eventarc |
| **Integration** | Native with Azure Storage, Event Grid, Logic Apps, API Management | Deep AWS service integration | Integrates with GCP services & Eventarc |
| **Monitoring** | Azure Monitor, Application Insights | CloudWatch Logs, X-Ray | Cloud Logging, Cloud Trace |
| **Pricing** | Consumption plan per execution & resource time; Premium plan available | Pay per request & execution time | Pay per invocation & execution time |
| **Strengths** | Rich trigger/binding model, deep Azure ecosystem | Mature ecosystem, wide integrations | Simple deployment, strong GCP data/event integration |
| **Weaknesses** | Cold start in consumption plan | Limited execution time (15 min) | Fewer bindings, limited languages vs. Lambda |

---

### 2. Durable Functions

| Feature | Durable Functions | AWS Step Functions (with Lambda) | GCP Workflows |
|---------|-------------------|-----------------------------------|---------------|
| **Overview** | Extension of Azure Functions for stateful orchestration | Visual workflow service orchestrating Lambda & AWS services | Orchestration of GCP services and APIs |
| **Patterns Supported** | Chaining, fan-out/fan-in, async HTTP APIs, human interaction | Sequential, parallel, map state, wait timers | Sequential & parallel steps, conditional branching |
| **Integration** | Any Azure Function trigger/binding | Any AWS service with API integration | Any GCP service/API with connectors |
| **Monitoring** | Azure Monitor, Application Insights | CloudWatch, Step Functions console | Cloud Logging, Workflow Execution UI |
| **Pricing** | Based on executions & storage for state | Based on state transitions | Based on number of steps executed |
| **Strengths** | Deeply integrated with Functions | Visual workflows, long-running orchestration | Native API integration, serverless |
| **Weaknesses** | Azure-only bindings | Cost grows with transitions | Limited out-of-the-box triggers |

---

### 3. Azure Logic Apps

| Feature | Azure Logic Apps | AWS Step Functions & EventBridge Scheduler | GCP Workflows + Cloud Scheduler |
|---------|------------------|--------------------------------------------|---------------------------------|
| **Overview** | Low-code/no-code workflow automation | Step Functions for orchestration + EventBridge Scheduler for time-based triggers | Workflows for orchestration + Cloud Scheduler |
| **Integration** | 300+ connectors, on-premises & SaaS | Native AWS service integrations | Native GCP API calls, HTTP endpoints |
| **Monitoring** | Azure Monitor, run history | CloudWatch, Step Functions console | Cloud Logging, Execution history |
| **Pricing** | Per action execution | Per state transition | Per step execution |
| **Strengths** | Very rich connector library | Tight AWS integration | Serverless, integrated with GCP APIs |
| **Weaknesses** | Vendor lock-in on connectors | Limited connectors outside AWS | Fewer ready-made connectors |

---

### 4. Azure Service Bus (Queues & Topics)

| Feature | Azure Service Bus | Amazon SQS & SNS | GCP Pub/Sub |
|---------|-------------------|------------------|-------------|
| **Overview** | Enterprise-grade messaging with FIFO, topics, subscriptions | SQS (queue), SNS (pub/sub topics) | Pub/Sub: unified messaging |
| **Messaging Model** | Queues (point-to-point), Topics (pub/sub) | Separate queue & topic services | Unified pub/sub model |
| **Integration** | Native with Functions, Logic Apps, Event Grid | Native AWS integrations | Native GCP integrations |
| **Monitoring** | Azure Monitor | CloudWatch | Cloud Monitoring |
| **Pricing** | Per operation, message size, & tier | Per request, payload size | Per message & data volume |
| **Strengths** | Advanced features (sessions, transactions) | Reliable, simple APIs | Global scale, auto-scaling |
| **Weaknesses** | More complex config | No built-in topic+queue hybrid | Lacks FIFO until recently |

---

### 5. Azure Event Grid

| Feature | Azure Event Grid | Amazon EventBridge | GCP Eventarc |
|---------|------------------|--------------------|--------------|
| **Overview** | Fully managed event routing | Event bus for application & SaaS events | Event routing from GCP services & SaaS |
| **Event Sources** | Azure services, custom topics, third-party | AWS services, SaaS, custom apps | GCP services, SaaS, custom |
| **Integration** | Functions, Logic Apps, Service Bus, Event Hubs | Lambda, Step Functions, SQS | Cloud Run, Workflows, Functions |
| **Monitoring** | Azure Monitor | CloudWatch | Cloud Logging |
| **Pricing** | Per million operations | Per million events | Per million events |
| **Strengths** | Low latency, rich Azure event sources | Complex routing rules | Deep GCP integration |
| **Weaknesses** | Azure-centric | AWS-only event sources | Limited cross-cloud |

---

### 6. Azure Event Hubs

| Feature | Azure Event Hubs | Amazon Kinesis Data Streams | GCP Pub/Sub (Streaming) |
|---------|------------------|-----------------------------|-------------------------|
| **Overview** | Big data streaming ingestion | Streaming data platform | Global message/event streaming |
| **Use Cases** | Telemetry, logs, event streaming | Real-time analytics, ingestion | Real-time messaging/streaming |
| **Integration** | Stream Analytics, Functions, Databricks | Kinesis Analytics, Lambda | Dataflow, BigQuery |
| **Monitoring** | Azure Monitor | CloudWatch | Cloud Monitoring |
| **Pricing** | Throughput units + retention | Shard hours + payload | Data volume + retention |
| **Strengths** | High throughput, Kafka-compatible | Tight AWS integration | Global scale, seamless analytics |
| **Weaknesses** | Requires throughput planning | More complex scaling | Limited partition control |

---

## Summary

All three cloud providers deliver comparable serverless capabilities, but **differences lie in triggers/bindings, integration ecosystems, and monitoring depth**.  
Azure offers **tight binding integration** and strong enterprise connectors, AWS has **mature service integration** and **Step Functions**, and GCP emphasizes **simplicity and global scale** with unified eventing models.
