# RAG Pipeline & Chatbot

## Objective  
Design and automate a Retrieval-Augmented Generation (RAG) pipeline that ingests documents from Google Drive, generates embeddings using OpenAI, stores them in Pinecone, and enables a chatbot interface via OpenRouter that queries this knowledge base upon user message input.

## Skills Learned  
- **RAG Architecture Design**: Developed an end-to-end flow integrating file ingestion, vector storage, and conversational AI using modular nodes.  
- **Embedding Generation**: Leveraged OpenAI’s embedding API to vectorize documents for semantic search.  
- **Vector Store Integration**: Configured Pinecone to store, update, and retrieve vectorized content in real-time.  
- **Conversational AI Deployment**: Integrated OpenRouter as the LLM interface for answering user queries based on document context.  
- **Automation with Triggers**: Used n8n’s Google Drive trigger to auto-process new files without manual intervention.

## Tools Used  
- **n8n**: Workflow automation platform  
- **Google Drive Trigger**: Auto-detects newly added files  
- **OpenAI Embeddings**: Converts text into vector representations  
- **Pinecone**: Vector database for semantic search  
- **OpenRouter**: LLM chat interface for real-time querying  
- **Recursive Text Splitter**: Preprocesses documents for optimal embedding  
- **Default Data Loader**: Handles document structuring for embedding workflows  

## Steps  

![image](https://github.com/user-attachments/assets/cf6faa41-d760-449b-b319-a5d2ace9341c)

1. **Initiated Workflow with Google Drive Trigger**  
   Configured n8n to automatically detect new files uploaded to a specific Google Drive folder (`fileCreated` event), ensuring real-time ingestion with zero manual overhead.

2. **Downloaded Incoming Files for Processing**  
   Used the `Download File` node to retrieve the newly added documents in preparation for vectorization.

3. **Split Documents Using Recursive Character Text Splitter**  
   Implemented fine-grained text segmentation to preserve semantic coherence while optimizing for token limits during embedding generation.

4. **Loaded Cleaned Text via Default Data Loader**  
   Structured and normalized document input using n8n's internal loader to ensure consistent formatting for downstream processing.

5. **Generated Embeddings with OpenAI**  
   Converted each document chunk into high-dimensional vectors using OpenAI’s Embeddings API for efficient matching.

6. **Stored Embeddings in Pinecone Vector DB**  
   Indexed the embeddings within Pinecone, enabling fast vector similarity searches for question-answer retrieval.

7. **Set Up AI Agent to Handle User Queries**  
   Deployed an `AI Agent` that listens for incoming chat messages and routes queries through a RAG workflow.

8. **Integrated OpenRouter Chat Model**  
   Connected OpenRouter as the chat model responsible for generating responses based on relevant context pulled from Pinecone.

9. **Enabled Vector Tool Lookup for Retrieval**  
   Equipped the AI agent with a “Tool” connected to Pinecone, allowing it to query the most relevant embedded data before crafting a response.

10. **Tested and Validated End-to-End RAG Functionality**  
    Simulated document uploads and real-time chat prompts to confirm correct ingestion, vectorization, retrieval, and conversational output.

Example:

When asking it what is the warranty policy of an FAQ document uploaded in the Google Drive:

![image](https://github.com/user-attachments/assets/336d4ee5-af00-4214-99c1-8eac98b1b539)

