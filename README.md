# RAG Pipeline & Chatbot

## Objective

Design and automate a Retrieval-Augmented Generation (RAG) pipeline that ingests documents from Google Drive, generates embeddings using OpenAI, stores them in Pinecone, and enables a chatbot interface via OpenRouter that queries this knowledge base upon user message input.

## Skills Learned

- RAG Architecture Design: Developed an end-to-end flow integrating file ingestion, vector storage, and conversational AI using modular nodes.
- Embedding Generation: Leveraged OpenAI’s embedding API to vectorize documents for semantic search.
- Vector Store Integration: Configured Pinecone to store, update, and retrieve vectorized content in real-time.
- Conversational AI Deployment: Integrated OpenRouter as the LLM interface for answering user queries based on document context.
- Automation with Triggers: Used n8n’s Google Drive trigger to auto-process new files without manual intervention.

## Tools Used

- n8n: Workflow automation platform.
- Google Drive Trigger: Auto-detects newly added files.
- OpenAI Embeddings: Converts text into vector representations.
- Pinecone: Vector database for semantic search.
- OpenRouter: LLM chat interface for real-time querying.
- Recursive Text Splitter: Preprocesses documents for optimal embedding.
- Default Data Loader: Handles document structuring for embedding workflows.
