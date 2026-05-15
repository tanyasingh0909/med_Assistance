# 🩺 AI Medical Assistant Chatbot — RAG-based Application

## 🧠 Project Overview
This application is a Medical Domain Chatbot built using Retrieval-Augmented Generation (RAG). It allows users to upload their own medical documents (e.g., textbooks, reports), and the system intelligently answers queries by retrieving the most relevant content before generating a final response.

---

## 🎓 What is RAG?
RAG (Retrieval-Augmented Generation) enhances language models by supplying relevant external context from a knowledge base, preventing hallucinations and improving accuracy, especially for factual or specialized domains like medicine.

---

## 🔄 Architecture

```text
User Input
   ↓
Query Embedding → Pinecone Vector DB ← Embedded Chunks ← Chunking ← PDF Loader
   ↓
Retrieved Docs
   ↓
RAG Chain (Groq + LangChain)
   ↓
LLM-generated Answer

📚 Features
Upload medical PDFs (notes, books, etc.)
Auto-extracts text and splits into semantic chunks
Embeds using Google/BGE embeddings
Stores vectors in Pinecone DB
Uses Groq's LLaMA3-70B via LangChain
FastAPI backend with endpoints for file upload and Q&A

🌐 Tech Stack
Component	Tech Used
LLM	Groq API (LLaMA3-70B)
Embeddings	Google Generative AI / BGE
Vector DB	Pinecone
Framework	LangChain
Backend	FastAPI
Frontend	Streamlit


📚 API Endpoints
POST /upload_pdfs/

Upload one or more PDF files.

POST /ask/

Ask a question using the form field:

question
📁 Folder Structure
📁 assets
📁 client
📁 server
├── routes
├── modules
├── middlewares
├── uploaded_docs
└── main.py
⚡ Quick Setup
Clone the Repository
git clone https://github.com/tanyasingh0909/med_Assistance.git
Backend Setup
cd medicalAssistant/server

# Create virtual environment
uv venv

# Activate virtual environment

# Windows
venv\Scripts\activate

# Install dependencies
uv pip install -r requirements.txt
Configure Environment Variables

Create a .env file inside the server folder:

GOOGLE_API_KEY=YOUR_API_KEY
GROQ_API_KEY=YOUR_API_KEY
PINECONE_API_KEY=YOUR_API_KEY

Run Backend Server
uvicorn main:app --reload --port 8000

Frontend Setup
cd medicalAssistant/client

# Create virtual environment
uv venv

# Activate virtual environment

# Windows
venv\Scripts\activate

# Install dependencies
uv pip install -r requirements.txt

# Run Streamlit app
streamlit run app.py
