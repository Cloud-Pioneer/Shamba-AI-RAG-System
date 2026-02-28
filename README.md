# Shamba-AI-RAG-System
Serverless AI Agricultural Advisory System using AWS Lambda, Bedrock, DynamoDB and RAG
# Shamba AI – Serverless Agricultural Advisory System
# Overview

Shamba AI is a serverless AI-powered agricultural advisory system designed to assist smallholder farmers with crop-related guidance.

The system uses Retrieval-Augmented Generation (RAG) with Amazon Bedrock to provide context-aware, knowledge-grounded responses. Built fully on AWS using a serverless architecture.

# Services Used:
Amazon API Gateway
AWS Lambda
Amazon DynamoDB
Amazon Bedrock (Claude 3 Haiku)
Amazon Bedrock Knowledge Base (RAG)
Amazon S3 (document storage)
Amazon CloudWatch (logging & monitoring)

# System Flow
User sends request via API Gateway
Lambda receives and parses JSON input
Conversation memory fetched from DynamoDB
Knowledge Base retrieval via Bedrock

If retrieval fails → fallback to base model

Response generated
Conversation stored in DynamoDB
Logs and token usage captured in CloudWatch

# Key Features
Multi-turn conversation memory
Retrieval-Augmented Generation (RAG)
Fallback logic when KB returns empty
Defensive error handling
Observability mindset
Basic cost awareness logging
Serverless architecture (no servers to manage)

# Technical Design Decisions
# Why Serverless?
No infrastructure management
Automatic scaling
Cost-efficient (pay-per-invocation)
Ideal for unpredictable workloads

# Why DynamoDB for Memory?
Low latency
Fully managed
Scales automatically
Simple partition key (phone number) enables per-user conversation memory

# Why RAG?
LLMs alone may hallucinate.
RAG ensures:
Responses grounded in agricultural documentation
Reduced hallucinations
Better factual accuracy

# Why Fallback Logic?
Knowledge retrieval may fail due to no matching documents or KB misconfiguration

Runtime errors
Fallback to base model ensures system reliability and no user facing failures

# Monitoring & Operational Awareness
The system logs:
Request payload metadata
Retrieval path used (RAG or fallback)
Execution duration
Memory usage
Estimated token consumption

CloudWatch provides:
Execution tracing
Debugging visibility
Performance analysis
Failure investigation
This demonstrates production-level operational thinking.

# Cost Control Considerations
The architecture minimizes cost by:
Using lightweight model (Claude 3 Haiku)
Limiting max tokens
Avoiding unnecessary repeated model calls
Logging usage for future cost analysis
Using serverless services (no idle infrastructure cost)

# How to Test
Sample API Request
curl -X POST "YOUR_API_GATEWAY_URL" \
-H "Content-Type: application/json" \
-d '{"phone":"+254700000000","message":"What are the symptoms of Grey Leaf Spot in maize?"}'
Example JSON Response
{
  "phone": "+254700000000",
  "reply": "The main symptoms include long, narrow grey lesions restricted by veins...",
  "timestamp": "1771964895"
}

# Security Considerations
No credentials stored in code
IAM role-based access
Principle of least privilege
No sensitive user data stored beyond conversation context

# Edge Cases Handled
Missing phone or message → 400 error
Knowledge base empty response → fallback
Bedrock runtime failure → fallback
Unexpected runtime errors → 500 response

# Skills Demonstrated
AWS Serverless Architecture
API Design
Event-driven Systems
DynamoDB Data Modeling
AI Integration with Bedrock
RAG Implementation
Error Handling & Resilience
Observability & Monitoring
Cost-aware Engineering
Production-minded Design Thinking

