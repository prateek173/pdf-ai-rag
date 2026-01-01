# ai-pdf-rag

ai-pdf-rag is an AI-powered PDF question-answering system built using LangChain and LangGraph.
It allows users to upload PDF documents, stores their semantic embeddings in a vector database, and answers user queries using retrieval-augmented generation (RAG) with large language models.

This project demonstrates an agentic architecture where document ingestion and query handling are orchestrated as graph-based workflows.

# Tech Stack

1. LangChain

2. LangGraph

3. OpenAI (or compatible LLM)

4. Supabase (Vector Store)

5. Node.js, TypeScript

6. Next.js, React

# What It Does

1. Ingests PDF documents and converts them into vector embeddings

2. Stores embeddings in a Supabase vector database

3. Retrieves relevant document chunks during query time

4. Generates context-aware answers with streamed responses

5. Uses LangGraph to orchestrate ingestion and retrieval agents

# High-Level Architecture

1. Ingestion Agent
Parses PDFs, chunks text, and stores embeddings in the vector store

2. Retrieval Agent
Handles user queries, performs semantic search, and generates responses

3. Frontend UI
Allows users to upload PDFs and interact with the assistant via chat

# Prerequisites

1. Node.js v18+ (v20 recommended)

2. Yarn package manager

3. A Supabase project configured for vector search

4. OpenAI API key (or another LangChain-supported provider)

# Supabase must include:

1. A documents table

2. A match_documents function for similarity search

# Running the Project (Minimal Setup)

1. Clone the repository and install dependencies:

```bash
git clone https://github.com/prateek173/pdf-ai-rag.git
cd ai-pdf-rag
yarn install
```
# Environment Variables

Each service uses its own .env file.
Copy the example files and update the required values.

# Frontend (frontend/.env)

1. Create the environment file:
```bash
cp frontend/.env.example frontend/.env
```

2. Required variables:
```ini
NEXT_PUBLIC_LANGGRAPH_API_URL=http://localhost:2024
LANGGRAPH_INGESTION_ASSISTANT_ID=ingestion_graph
LANGGRAPH_RETRIEVAL_ASSISTANT_ID=retrieval_graph
```

3. Optional (recommended for tracing):
```ini
LANGCHAIN_API_KEY=your-langsmith-key
LANGCHAIN_TRACING_V2=true
LANGCHAIN_PROJECT=ai-pdf-rag
```
# Backend (backend/.env)

1. Create the environment file:

cp backend/.env.example backend/.env


2. Required variables:
```ini
OPENAI_API_KEY=your-openai-key
SUPABASE_URL=your-supabase-url
SUPABASE_SERVICE_ROLE_KEY=your-supabase-service-role-key
```

3. optional:
```ini
LANGCHAIN_TRACING_V2=true
LANGCHAIN_PROJECT=ai-pdf-rag
```
# Start the Application
# Backend

1. Navigate to backend:
```bash
cd backend
```

2. Start LangGraph:
```bash
yarn langgraph:dev
```

-Runs the LangGraph server on port 2024

-LangGraph Studio can be used to inspect workflows

# Frontend

1. Navigate to frontend:
```bash
cd frontend
```

2. Start the development server:
```bash
yarn dev
```


3. Open in browser:

http://localhost:3000

# Usage

1. Open the web UI

2. Upload one or more PDF files

3. Wait for ingestion to complete

4. Ask questions related to the uploaded PDFs

5. Receive streamed, context-aware responses with sources

# Notes

1. PDF uploads are limited to 5 files, each under 10 MB (configurable)

2. Chat history is session-based and not persisted by default

3. Document embeddings persist across sessions via the vector database