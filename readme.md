# LLM Knowledge Retrieval System (RAG)

AI-powered document Q&A system that lets you upload PDFs and ask questions with source citations, using Retrieval-Augmented Generation (RAG).

---

## Demo
Upload a PDF → Ask a question → Get an answer + cited snippets  

*(Add screenshots / short GIF here)*

---

## Key Features
- ✅ Upload PDF documents  
- ✅ Ask natural-language questions  
- ✅ Answers include source citations (document + chunk)  
- ✅ Persistent vector store (data survives restart)  
- ✅ Simple REST API (FastAPI)  
- ✅ Optional lightweight web UI (if you built one)

---

## Tech Stack
- **Backend:** FastAPI (Python)
- **Vector DB:** ChromaDB
- **Embeddings:** OpenAI `text-embedding-3-small`
- **LLM:** `gpt-4o-mini`

---

## How It Works (RAG Pipeline)

### Indexing
1. PDF → Text extraction  
2. Chunking (split into small overlapping text blocks)  
3. Embeddings (convert chunks into vectors)  
4. Store vectors + metadata in ChromaDB  

### Querying
1. User question → Embedding  
2. Similarity search in ChromaDB (top-k chunks)  
3. Retrieved chunks → injected as context into the LLM prompt  
4. LLM generates answer + citations  

---

