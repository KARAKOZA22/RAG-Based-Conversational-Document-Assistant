# RAG with FAISS - Retrieval-Augmented Generation System

A comprehensive Retrieval-Augmented Generation (RAG) implementation using FAISS vector database for efficient document retrieval and Groq LLM for response generation. This system can process multiple document formats and web content to provide contextually relevant answers to user queries.

## 🌟 Features

- **Multi-format Document Support**: Process PDF, DOCX, TXT, and CSV files
- **Web Scraping Capabilities**: Extract and process content directly from URLs
- **Efficient Vector Search**: FAISS-based similarity search for fast retrieval
- **Flexible Chunking**: Configurable text chunking with overlap for optimal context preservation
- **LLM Integration**: Powered by Groq's Llama 3.3 70B model for high-quality response generation
- **Semantic Embeddings**: Uses HuggingFace's sentence-transformers for accurate text embeddings

## 🏗️ Architecture

The system consists of three main components:

1. **Retrieval Module**: Handles document processing, chunking, and vector search
2. **Generation Module**: Manages LLM interactions and response generation
3. **RAG Pipeline**: Orchestrates the complete workflow from query to response

## 🛠️ Installation

```bash
# Install required packages
pip install PyPDF2 python-docx langchain-community sentence-transformers 
pip install faiss-cpu groq scrapegraph_py python-dotenv pandas numpy transformers
```

## ⚙️ Setup

1. Create a `.env` file with your API keys:
```env
GROQ_API_KEY=your_groq_api_key_here
SCRAPE_API_KEY=your_scrape_api_key_here
```

2. Load the environment variables in your script

## 🚀 Usage

### Basic Usage with Local Files

```python
from rag_with_faiss import RAG

# Initialize RAG with a local file
rag_system = RAG(file_path='path/to/your/document.pdf')

# Generate response
response = rag_system.generate("What is the main topic discussed?", k=3)
print(response)
```

### Usage with Web URLs

```python
# Initialize RAG with a web URL
rag_system = RAG(url='https://example.com/article')

# Generate response
response = rag_system.generate("Summarize the key points", k=5)
print(response)
```

### Advanced Configuration

```python
# Custom chunking parameters
rag_system = RAG(file_path='document.txt')
# Modify chunk size and overlap in the Retrieval class
# chunk_size: Number of characters per chunk (default: 100)
# chunk_overlap: Overlap between chunks (default: 20)
```

## 📚 Supported File Formats

- **PDF**: Extracted using PyPDF2
- **DOCX**: Processed with python-docx
- **TXT**: Plain text files
- **CSV**: Converted to string representation
- **Web URLs**: Scraped using ScrapeGraph API

## 🔧 Configuration Options

### Retrieval Parameters
- `chunk_size`: Size of text chunks (default: 100 characters)
- `chunk_overlap`: Overlap between consecutive chunks (default: 20 characters)
- `k`: Number of relevant chunks to retrieve (configurable per query)

### Generation Parameters
- `model`: LLM model selection (default: "llama-3.3-70b-versatile")
- `temperature`: Response randomness (default: 0 for deterministic outputs)
- `max_completion_tokens`: Maximum response length (default: 1024)

## 🏃‍♂️ Example Output

```python
# Query: "What is philosophy?"
# Response: Based on the retrieved context, philosophy is the systematic study 
# of fundamental questions about existence, knowledge, values, reason, mind, 
# and language. It involves critical thinking and rational argument to explore 
# life's biggest questions...
```

## 📦 Dependencies

- `faiss-cpu`: Vector similarity search
- `sentence-transformers`: Text embeddings
- `langchain-community`: Document processing utilities
- `groq`: LLM API client
- `scrapegraph_py`: Web scraping functionality
- `PyPDF2`: PDF text extraction
- `python-docx`: Word document processing
- `pandas`: Data manipulation
- `numpy`: Numerical computations
