# Groq ChromaDB RAG Assistant

A simple Retrieval-Augmented Generation (RAG) application built with **Python, FastAPI, Groq, ChromaDB, and Sentence Transformers**.

The application allows users to provide documents and ask questions about their content. Relevant information is retrieved from the local ChromaDB vector database and then passed to a Groq LLM to generate an answer.

## 🚀 Features

- 📄 Supports PDF, TXT, and Markdown documents
- 🔎 Semantic document search using embeddings
- 🧠 Retrieval-Augmented Generation (RAG)
- ⚡ Fast responses using Groq
- 🗄️ Local ChromaDB vector database
- 🌐 FastAPI backend
- 🤖 Sentence Transformers embeddings
- 🔐 API key stored securely in `.env`

## 🛠️ Technologies Used

- Python
- FastAPI
- Groq API
- ChromaDB
- Sentence Transformers
- PyPDF
- Uvicorn
- HTML / CSS / JavaScript

## 📁 Project Structure

```text
groq_chromadb_rag/
│
├── app/
│   ├── document_loader.py
│   ├── ingest_service.py
│   └── ...
│
├── data/
│   └── sample.txt
│
├── chroma_db/
│   └── Local vector database
│
├── ingest.py
├── api.py
├── .env.example
├── .gitignore
├── requirements.txt
└── README.md
```

## ⚙️ Installation

### 1. Clone the repository

```bash
git clone https://github.com/Rohama789-blip/groq_chromadb_rag.git
cd groq_chromadb_rag
```

### 2. Create a virtual environment

```bash
python -m venv venv
```

### 3. Activate the virtual environment

For Windows CMD:

```cmd
venv\Scripts\activate
```

### 4. Install dependencies

```bash
pip install -r requirements.txt
```

## 🔑 Configure Environment Variables

Create a `.env` file based on `.env.example`.

```env
GROQ_API_KEY=your_groq_api_key_here

GROQ_MODEL=openai/gpt-oss-120b

EMBEDDING_MODEL=sentence-transformers/all-MiniLM-L6-v2

CHROMA_PATH=./chroma_db
CHROMA_COLLECTION=knowledge_base

TOP_K=5
CHUNK_SIZE=1200
CHUNK_OVERLAP=200
EMBEDDING_BATCH_SIZE=64
```

**Never upload your `.env` file or API key to GitHub.**

## 📚 Add Documents

Place your documents inside the `data` folder.

Supported formats:

- `.pdf`
- `.txt`
- `.md`

Example:

```text
data/
├── sample.txt
└── research_paper.pdf
```

## 🔄 Ingest Documents

After adding or changing documents, run:

```cmd
python ingest.py --reset
```

This creates the embeddings and stores the document data in ChromaDB.

## ▶️ Run the Application

Start the FastAPI server:

```cmd
uvicorn api:app --host 127.0.0.1 --port 8000 --reload
```

Then open:

```text
http://127.0.0.1:8000
```

## 💬 How It Works

The application follows a simple RAG pipeline:

```text
Document
   ↓
Document Loader
   ↓
Text Chunking
   ↓
Sentence Transformer Embeddings
   ↓
ChromaDB
   ↓
User Question
   ↓
Semantic Search
   ↓
Relevant Context
   ↓
Groq LLM
   ↓
Generated Answer
```

## 🧪 Example

After adding a document, you can ask questions such as:

```text
What is the main topic of this document?

What methodology was used?

What are the main findings?

Summarize the document.
```

The system retrieves relevant information from the indexed documents before generating the answer.

## 🔐 Security

The following files and folders should not be committed to GitHub:

```text
.env
venv/
.venv/
chroma_db/
__pycache__/
*.pyc
```

These are already included in `.gitignore`.

## 📝 Notes

- The application answers questions based on the documents available in the ChromaDB collection.
- Run the ingestion command whenever documents are added or modified.
- PDF files containing selectable text work best with the default PDF extraction.
- Scanned/image-only PDFs may require OCR.

## 👩‍💻 Author

**Rohama**

GitHub:  
https://github.com/Rohama789-blip

## ⭐ Future Improvements

- Chat history
- Multiple document collections
- Better PDF processing
- OCR support for scanned PDFs
- Streaming responses
- User authentication
- Improved UI/UX
- Deployment to a cloud platform

---

## 📄 License

This project is intended for educational and development purposes.