Shamba AI — AI-Powered Agricultural Advisory System for Smallholder Farmers
Overview

Shamba AI is a serverless agricultural advisory platform built on AWS that helps smallholder farmers access fast, practical, and affordable farming advice using Artificial Intelligence.

The system combines Generative AI, Retrieval-Augumented Generation (RAG) , Conversation memory, Knowledge-base retrieval and Serverless cloud architecture to deliver context aware agricultural recommendations in real time. 

The goal is to make reliable farming knowledge accessible to farmers who may not have immediate access to agronomists or extension officers.

This Project Matters because Agriculture supports millions of livelihoods across Kenya yet many farmers lack access to timely agricultural guidanceand can't afford professional consultancy services. 

Shamba AI addresses this challenge by providing:
- Instant farming advice
- Context-aware conversations
- Knowledge-grounded responses
- Low-cost scalable infrastructure
- Cloud-native automation

The system is designed to support farmers using simple interfaces such as SMS and mobile applications.

Architecture Overview
Shamba AI is built using a fully serverless AWS architecture.

AWS Services Used;
Amazon API Gateway — Receives incoming farmer requests
AWS Lambda — Handles application logic
Amazon DynamoDB — Stores conversation memory
Amazon Bedrock — Generates AI responses using Claude 3 Haiku
Amazon Bedrock Knowledge Base — Provides Retrieval-Augmented Generation (RAG)
Amazon S3 — Stores agricultural documents and datasets
Amazon CloudWatch — Logging, monitoring, observability, and cost awareness

How the System Works;
Farmer sends a question through API Gateway
AWS Lambda receives the request
Conversation history is retrieved from DynamoDB
Lambda builds a context-aware prompt
Amazon Bedrock Knowledge Base retrieves relevant agricultural information
Claude 3 Haiku generates the response
If retrieval fails, fallback logic invokes the base model directly
Response is returned to the farmer
Conversation is stored for future memory
Logs and usage metadata are captured in CloudWatch

Some of the Key Features implemented in the project are;
- Multi-Turn Conversation Memory
The system remembers previous farmer interactions using DynamoDB. For example, the farmer texts "Why are my maize leaves yellow?" then later texts " It is at seedling stage" 
The AI understands the follow-up context.

- Retrieval-Augmented Generation (RAG)
Instead of relying only on general AI knowledge, the system retrieves trusted agricultural information from uploaded farming documents stored in Amazon S3.

This improves accuracy, relevance and reliability. 

- Fallback Logic
If the Knowledge Base retrieval fails or returns weak results the system automatically falls back to the base model ensuring the farmer still receives assistance. 

- Observability & Monitoring
CloudWatch logging was implemented to support:
Request monitoring
Error tracking
Token usage tracking
Execution duration visibility
Basic operational observability

- Cost-Aware Design
The project was intentionally designed with cost optimization in mind. The use of serveless architecture, lightweight model selection, token usage logging and controlled response sizes all adapted with cost control in mind. 


