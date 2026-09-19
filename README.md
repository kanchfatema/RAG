# RAG PDF Question Answering System

A Retrieval-Augmented Generation (RAG) project that allows users to ask questions about PDF documents and get answers based on the information contained in those documents.

The project loads PDF files, breaks them into smaller chunks, converts those chunks into embeddings, stores them in a vector database, retrieves the most relevant chunks for a user's question, and then uses an LLM to generate the final answer.

## How It Works

The project follows this pipeline:

**PDF → Text → Chunks → Embeddings → Vector Database → Retrieval → LLM → Answer**

### 1. PDF Loading

PDF documents are loaded from a directory using LangChain's PDF loaders.

### 2. Text Chunking

The extracted text is divided into smaller chunks using `RecursiveCharacterTextSplitter`.

This makes it easier to find the specific parts of a document that are relevant to a question.

### 3. Embeddings

Each text chunk is converted into a numerical representation called an embedding.

This project uses the `all-MiniLM-L6-v2` model from Sentence Transformers.

### 4. Vector Database

The embeddings are stored in ChromaDB.

When a user asks a question, the question is also converted into an embedding and compared with the stored document embeddings.

### 5. Retrieval

The system retrieves the most relevant document chunks based on similarity to the user's question.

### 6. LLM Response

The retrieved information is passed to a Groq-hosted LLM along with the user's question.

The LLM uses the retrieved context to generate the final answer.

## Project Structure

```text
RAG_Project/
│
├── data/
│   ├── pdfs/
│   └── vector_store/
│
├── src/
│   ├── ...
│
├── .env
├── .gitignore
├── requirements.txt
├── README.md
└── main.py
```

> The exact file structure may vary depending on how the project is organized.

## Technologies Used

* Python
* LangChain
* Sentence Transformers
* ChromaDB
* Groq
* Large Language Models (LLMs)
* Retrieval-Augmented Generation (RAG)

## Setup

### 1. Clone the repository

```bash
git clone YOUR_GITHUB_REPOSITORY_URL
cd YOUR_PROJECT_FOLDER
```

### 2. Create a virtual environment

```bash
python -m venv venv
```

Activate it on Windows:

```bash
venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Add your Groq API key

Create a `.env` file in the project root:

```env
GROQ_API_KEY=your_api_key_here
```

**Do not commit your `.env` file to GitHub.**

The `.gitignore` file should contain:

```gitignore
.env
__pycache__/
*.pyc
data/vector_store/
```

## Running the Project

Add your PDF documents to the project's PDF/data directory and run:

```bash
python main.py
```

Then enter a question related to the documents.

The system retrieves relevant information from the PDFs and uses the LLM to generate an answer.

## What I Learned

Through this project, I learned how the main components of a RAG system work together:

* Loading and processing documents
* Text chunking
* Generating embeddings
* Working with vector databases
* Similarity-based retrieval
* Connecting an LLM through an API
* Managing API keys using environment variables
* Building a complete RAG pipeline in Python

## Future Improvements

* Add a web-based user interface
* Support multiple document formats
* Add conversation history
* Improve re
