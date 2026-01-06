# 🎙️ Voice RAG Chatbot with ElevenLabs, OpenAI & n8n

A **voice-enabled Retrieval-Augmented Generation (RAG) chatbot** built using **n8n**, **ElevenLabs**, **OpenAI**, and **Qdrant**.

Users can **ask questions via voice**, the system retrieves relevant information from documents stored in a vector database, and responds back with **natural AI voice**.

---

## 🚀 Features

- 🔊 Voice-based AI conversation (ElevenLabs)
- 🧠 RAG architecture with vector search
- 📄 Automatic document ingestion from Google Drive
- 🧩 n8n-based orchestration
- 📦 Qdrant vector database
- 🕒 Conversation memory support
- 🌐 Embeddable website widget

---

## 🛠️ Tech Stack

- **n8n** – Workflow orchestration
- **ElevenLabs Conversational AI** – Voice agent
- **OpenAI** – Embeddings & chat models
- **Qdrant** – Vector database
- **Google Drive** – Document source
- **LangChain (n8n nodes)** – RAG pipeline

---

## 🧩 Architecture Overview

**Flow:**

1. User speaks to ElevenLabs Voice Agent
2. ElevenLabs sends the question to n8n via webhook
3. n8n AI Agent:
   - Retrieves relevant chunks from Qdrant
   - Uses OpenAI to generate the answer
4. Response is sent back to ElevenLabs
5. ElevenLabs converts text → voice

---

## ⚙️ Setup Guide

### STEP 1: Create ElevenLabs Agent
- Create a Conversational Agent
- Add a **System Prompt**
- Add a **Webhook tool**
- Configure a body parameter:
  - `question` (type: string, LLM Prompt)

---

### STEP 2: Create Qdrant Collection
Update in workflow:
- `QDRANTURL`
- `COLLECTION`

Run **Create collection** node in n8n.

---

### STEP 3: Document Vectorization
- Connect Google Drive folder
- Download documents
- Split text into chunks
- Generate embeddings
- Store vectors in Qdrant

---

### STEP 4: RAG Question Answering
- ElevenLabs sends voice question
- n8n webhook receives it
- AI Agent retrieves context + answers
- Response sent back to ElevenLabs

---

### STEP 5: Embed Widget
Add this widget to your website:

```html
<elevenlabs-convai agent-id="AGENT_ID"></elevenlabs-convai>
<script src="https://elevenlabs.io/convai-widget/index.js" async></script>
