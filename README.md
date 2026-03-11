📄 Multi-Utility RAG Chatbot (LangGraph + Streamlit)

A Retrieval Augmented Generation (RAG) based chatbot built using LangGraph, LangChain, Streamlit, and FAISS that allows users to interact with uploaded PDF documents and access additional utilities such as web search, stock price retrieval, and calculator tools.

The application supports multi-threaded conversations, enabling users to maintain separate chats with different documents while preserving conversation history.

🚀 Features

📑 PDF Question Answering

Upload a PDF and ask questions about its contents.

Uses RAG pipeline with FAISS vector search.

🧠 LangGraph Agent Workflow

Intelligent routing between:

Document retrieval

Web search

Calculator

Stock price API

🔎 Web Search Tool

Uses DuckDuckGo search for answering general knowledge queries.

📈 Stock Price Retrieval

Fetches real-time stock prices using Alpha Vantage API.

🧮 Built-in Calculator Tool

Performs basic arithmetic operations.

💬 Multi-Threaded Conversations

Each chat session is stored as a separate thread.

Chat history persists using SQLite checkpointing.

📊 Streaming Responses

Responses stream token-by-token in the Streamlit interface.

🏗️ System Architecture
User Query
     │
     ▼
Streamlit Frontend
     │
     ▼
LangGraph Agent
     │
     ├── RAG Tool (PDF Retrieval via FAISS)
     ├── Web Search Tool (DuckDuckGo)
     ├── Stock Price Tool (Alpha Vantage API)
     └── Calculator Tool
     │
     ▼
GPT-4o-mini (LLM)
     │
     ▼
Final Answer → Streamlit UI
🧠 How RAG Works in This Project

User uploads a PDF document.

The document is:

Loaded using PyPDFLoader

Split into chunks using RecursiveCharacterTextSplitter

Chunks are embedded using OpenAI Embeddings.

Stored inside a FAISS vector database.

When a question is asked:

Similar chunks are retrieved.

Sent as context to the LLM.

The LLM generates a context-aware answer.

🛠️ Tech Stack
Frameworks

LangChain

LangGraph

Streamlit

LLM & Embeddings

OpenAI GPT-4o-mini

OpenAI text-embedding-3-small

Vector Database

FAISS

Tools

DuckDuckGo Search

Alpha Vantage Stock API

Custom Calculator Tool

Storage

SQLite Checkpointing for conversation memory

📂 Project Structure
rag-chatbot/
│
├── rag_chatbot_streamlit_frontend.py   # Streamlit UI
├── rag_chatbot_backend_langraph.py     # LangGraph agent + RAG pipeline
├── chatbot.db                          # SQLite checkpoint database
├── .env                                # API keys
└── README.md
