<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Build a RAG API with FastAPI

**Project Link:** [View Project](http://nextwork.ai/projects/ai-devops-api)

**Author:** sumanth kotha  
**Email:** sumanthkothamasters@gmail.com

---

---

## Introducing Today's Project!

In this project, I'm going to implement RAG assisted AI, create a chromavector DB database and a Fast API-powered /ask endpoint to create a full RAG pipeline.This will help me improve my knowledge on python and REST API and LLM's.

### Key tools and concepts

The key tools I used include ollama, qwen2.5:0.5b, emma3:1b, nomic-embed-text, custom-code, python, Swagger UI. Key concepts I learnt include performing RAG both manually and by code, creating personal knowledge base with chromaDB and vector embeddings,  Build REST API and FASTAPI that implements full RAG pipeline, used nomic-embed text for semantic search and qwen2.5:0.5b for AI generated response, built multi-user AI directory with dynamic document ingestion.

### Challenges and wins

This project took me approximately 3 hours. The most challenging part was implementing python code for building /ask and /post parameters for web responses. And extending API usage to multi-user tenancy to implement with full RAG pipeline.

---

## Performing RAG Manually

In this step, I'm going to perform actions on RAG with a manual demo, setting up python project with a virtual environment, install all dependencies and pull the nomic-embed-text embedding model. RAG stands for Retrival Augmented Generation is an AI technique that provides LLM's to the models giving them access to external, up-to-date information.

![Image](http://nextwork.ai/warm_chartreuse_lucky_sow/uploads/ai-devops-api_v3j7x5b9)

### Understanding the three parts of RAG

I successfully implemented the manual RAG demo by incorporating my career goals into the prompt, which resulted in accurate, context-aware responses. Through this process, I gained a clear understanding of the three core components of RAG: Retrieval, Augmentation, and Generation.

### Comparing the two AI models

I observed a key functional distinction between the two models: Qwen 2.5:0.5b acts as a generative model that crafts responses based on provided keywords, while nomic-embed-text functions as an embedding model that transforms text into numerical vectors to facilitate efficient information retrieval.

---

## Building a Personal Knowledge Base

In this step, I'm going to write a personal profile document, build a Python script that loads, chunks and stores my profile as embeddings and run the script and verify my knowledge base is built.

![Image](http://nextwork.ai/warm_chartreuse_lucky_sow/uploads/ai-devops-api_g3h7m2r5)

### Creating the profile document

I included information about my name, career goals, tools and technologies that I worked on, hobbies and fun facts. Using this data, AI will analyze and provides the accurate response based on the prompts that we provide.

### How semantic search finds relevant chunks

When I ask a question, ChromaDB sends each text chunk to nomic-embed-text model which converts the text into 768-dimensional vector. So each number respresents a different aspect of texts meaning like topic, tone or text. When someone asks a question, even that converts into vector and chromaDB finds the chunks whose vectors are closest in the high-dimensional space.

---

## Creating the RAG API with FastAPI

In this step, I'm going to build an API that retrives the context, augment the prompt and generate the accurate response using /ask endpoint. I'll test it using the built-in Swagger UI.

![Image](http://nextwork.ai/warm_chartreuse_lucky_sow/uploads/ai-devops-api_j5m1r8t2)

### How the /ask endpoint works

When a question comes in, my endpoint retrives the 2 most relevant chunks of text from chromaDB, augments the prompts by combining those chunks with the relevant question and generates the grounded answer using qwen2.5:0.5b model.The response includes the context that was used so you can verify the AI's sources.

### Testing with Swagger UI

I tested my API by asking "What is my name?" The AI answered with "your name is sumanth kotha" The context used shows the exact chunks that ChromaDB retrieved from your knowledge base. This is the context that was injected into the prompt before the AI generated its answer.

---

## Extending to a Multi-User AI Directory

In this project extension, I'm adding multi-user support because in real-world RAG system almost always serve multiple users or data sources. Multi-tenancy means where the single instance of software application is used by multiple users called tenants. Each tenent shares the same application and database but their information is isolated from other customers.

![Image](http://nextwork.ai/warm_chartreuse_lucky_sow/uploads/ai-devops-api_d5g9k3n7)

### Adding the POST /documents endpoint

In this project extension, I added a POST endpoint that allows FASTAPI to add chunks of multiple user_names to filter. when a user provides the name, the chroma DB retrives out that particular user's chunks of data. Metadata filtering allows optional user parameter. When provided, ChromaDB's where filter only searches through that user's chunks. Without it, all profiles are searched.

![Image](http://nextwork.ai/warm_chartreuse_lucky_sow/uploads/ai-devops-api_r8t2w6y1)

### Verifying multi-user filtering

In this project extension, I tested multi-user queries by  passing user=Jordan, the code adds {"user_name": "Jordan"} to ChromaDB's "where" parameter. This tells ChromaDB to only look at chunks where the user_name metadata matches "Jordan".

---

## Wrapping Up

I did this project today to learn how to integrate AI in our local machines to gain knowledge base on AI agents and models, performing Retrival Augmented Generation for retriving our personal data in our local machine.

---

---
