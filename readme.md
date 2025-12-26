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

## Project Structure (Suggested)

.
├── main.py
├── app/
│   ├── api/                # routes/controllers
│   ├── core/               # config, env, logging
│   ├── services/           # RAG pipeline, embeddings, retrieval
│   ├── utils/              # PDF parsing, chunking helpers
│   └── models/             # Pydantic schemas
├── data/
│   ├── uploads/            # stored PDFs (optional)
│   └── chroma/             # ChromaDB persistence directory
├── requirements.txt
├── .env.example
└── README.md


## Example Usage (cURL)
Upload
curl -X POST "http://127.0.0.1:8000/api/upload" \
  -F "file=@./sample.pdf"

Query
curl -X POST "http://127.0.0.1:8000/api/query" \
  -H "Content-Type: application/json" \
  -d '{"question":"Summarize the key points", "top_k": 5}'

Architecture Diagram
PDF Upload → Text Extract → Chunk → Embed → ChromaDB
                                   ↑
Question → Embed → Similarity Search ┘ → Context + Prompt → LLM → Answer + Citations


(Optional: Add an image from /docs/architecture.png)

Testing the Build (Fresh Environment)

Generate requirements.txt:

pip freeze > requirements.txt


Test in a clean environment:

python -m venv test_env
source test_env/bin/activate
pip install -r requirements.txt
uvicorn main:app --reload


If you want, I can **shorten this further for ATS / recruiter skimming**, or add an **“Interview Talking Points”** section at the end.
