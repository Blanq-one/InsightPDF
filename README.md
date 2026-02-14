# InsightPDF

InsightPDF is an advanced document-understanding application that transforms static PDF documents into interactive conversational interfaces using Retrieval-Augmented Generation (RAG). By leveraging LangChain's modular pipelines and OpenAI's large language models, InsightPDF provides context-grounded answers to user queries with high precision.

This tool is optimized for academic research, professional data analysis, and technical documentation review.

---

## Key Features

- Multimodal PDF processing (supports uploads up to 200MB per file).
- Advanced RAG architecture combining semantic search with generative synthesis.
- "Smart Search Mode" utilizing hybrid keyword and embedding-based retrieval for increased accuracy.
- Automated contextual follow-up question generation.
- Intelligent web fallback integration via SerpAPI for out-of-scope queries.
- Exportable chat history in standardized PDF format.
- Support for Optical Character Recognition (OCR) via Tesseract for scanned documents.
- Streamlined, high-performance dark-themed interface.

---

## Technical Architecture

| Component         | Technology           | Role                                                     |
|-------------------|----------------------|----------------------------------------------------------|
| User Interface    | Streamlit            | Frontend orchestration                                   |
| QA Pipeline       | LangChain            | Chaining, memory management, and RAG logic               |
| LLM Provider      | OpenAI API           | Generative answering and refinement                      |
| Vector Embeddings | OpenAIEmbeddings     | High-dimensional semantic representation                 |
| Document Parsing  | PyPDF2, pdf2image    | Text extraction and buffer management                    |
| OCR Engine        | Tesseract            | Text recovery for scanned image-based PDFs               |
| Web Search        | SerpAPI              | External knowledge augmentation                          |

---

## System Workflow

1. **Ingestion and Preprocessing**
   - Documents are parsed and converted using standardized extraction libraries.
   - Text is segmented into optimized chunks using recursive splitters to preserve context.

2. **Vectorization and Indexing**
   - Chunks are transformed into vector embeddings.
   - A high-performance retriever enables efficient similarity-based search.

3. **Inference and Retrieval**
   - Queries trigger a retrieval pass to identify the most relevant document segments.
   - Contextual data is synthesized with the user query and passed to the primary model for final response generation.

4. **Post-Processing**
   - Responses are rendered within the secure UI.
   - Predictive analysis suggests relevant follow-up questions.
   - Full session data is available for export as a PDF document.

---

## Installation and Deployment

Follow these instructions to deploy InsightPDF in a local environment.

### 1. Repository Initialization
Clone the repository and navigate to the project directory:
```bash
git clone https://github.com/shruti25838/my-projects.git
cd my-projects/askmydocs
```

### 2. Environment Configuration
It is recommended to use a virtual environment for dependency isolation:
```bash
python -m venv venv
# Windows execution policy
venv\Scripts\activate
```

### 3. Dependency Installation
Install the necessary Python packages:
```bash
pip install -r requirements.txt
```

### 4. System Requisites
For OCR support, ensure the following system-level dependencies are installed:

**macOS:**
```bash
brew install poppler tesseract
```

**Linux (Ubuntu/Debian):**
```bash
sudo apt update
sudo apt install poppler-utils tesseract-ocr
```

**Windows:**
- Install Tesseract OCR for Windows.
- Install Poppler for Windows.
- Ensure both are included in the system's PATH variable.

### 5. API Authentication
External service authentication requires valid API keys. Create a `.env` file in the root directory:
```env
OPENAI_API_KEY=your_key_here
SERPAPI_API_KEY=your_key_here
```

### 6. Application Execution
Launch the application using the Streamlit CLI:
```bash
streamlit run app.py
```
The application will be accessible at `http://localhost:8501`.


