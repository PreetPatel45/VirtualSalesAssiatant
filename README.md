# Virtual Sales Assistant with RAG-Enabled FLAN-T5 on AWS

## Overview

This project implements a production-ready virtual sales assistant using Retrieval-Augmented Generation (RAG) architecture on AWS. The solution combines Google's FLAN-T5 Small language model deployed on Amazon SageMaker with a robust RAG pipeline powered by AWS Lambda and OpenSearch. Through sophisticated prompt engineering techniques, the system is specifically designed to function as an intelligent sales assistant capable of providing product information, handling customer inquiries, and supporting sales processes with context-aware responses.

## Architecture

![alt text](image.png)
### Architecture Components

The system follows a serverless, event-driven architecture with the following key components:

#### Core Infrastructure
- **Amazon S3**: Document storage and static website hosting for the frontend
- **Amazon SageMaker**: Hosts the FLAN-T5 Small model endpoint for text generation
- **Amazon OpenSearch**: Vector database for document indexing and similarity search
- **AWS Lambda**: Serverless compute for RAG processing and API endpoints
- **Amazon API Gateway**: RESTful API endpoints for frontend integration
- **AWS CloudFormation**: Infrastructure as Code (IaC) for reproducible deployments

#### Data Flow
1. **Document Ingestion**: Product documents, sales materials, and knowledge base content are uploaded to S3, triggering Lambda functions for processing
2. **Vectorization**: Documents are chunked, embedded, and indexed in OpenSearch
3. **Query Processing**: Customer/sales queries trigger the RAG pipeline via API Gateway
4. **Context Retrieval**: Relevant product information and sales materials are retrieved from OpenSearch using vector similarity
5. **Sales-Optimized Response Generation**: Retrieved context, user query, and specialized sales prompts are sent to FLAN-T5 on SageMaker
6. **Response Delivery**: Sales-focused, contextually appropriate responses are returned to the frontend via API Gateway

## Features

- **Virtual Sales Assistant**: Specialized AI assistant designed for sales support through advanced prompt engineering
- **Advanced Language Model**: FLAN-T5 Small deployed on SageMaker with Hugging Face integration
- **RAG Implementation**: Context-aware responses using product documentation and sales material retrieval
- **Sales-Focused Prompt Engineering**: Custom prompts optimized for sales conversations and customer support
- **Vector Search**: OpenSearch-powered semantic search capabilities for product information
- **Serverless Architecture**: Cost-effective, auto-scaling Lambda functions
- **Web Interface**: Clean HTML frontend for customer and sales team interaction
- **Document Processing**: Automated product documentation and sales material ingestion and indexing
- **Infrastructure as Code**: Complete CloudFormation templates for easy deployment

## Project Structure

```
├── cloudformation/
│   ├── opensearch-rag-pipeline.yaml    # OpenSearch cluster and RAG infrastructure
│   ├── upload-endpoint-template.yaml   # Document upload API endpoints
│   ├── rag-query-lambda.yaml          # Query processing Lambda functions
│   ├── s3-bucket.yaml                 # S3 bucket configuration
│   └── sagemaker-flan-t5.yaml         # SageMaker model deployment
├── frontend/
│   └── index.html                     # Minimalistic web interface
└── README.md
```

## Prerequisites

- AWS CLI configured with appropriate permissions
- AWS account with access to SageMaker, OpenSearch, Lambda, and S3
- Basic understanding of CloudFormation and AWS services

## Deployment Instructions

### Step 1: Deploy Core Infrastructure

Deploy the CloudFormation stacks in