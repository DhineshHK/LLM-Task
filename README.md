# engAIge-GmbH

## Task: RAG Pipeline for PDF Text Extraction and Query Answering

This repository contains the solution to the task of creating a **Retrieval-Augmented Generation (RAG) pipeline** for extracting text from PDFs and answering queries using relevant passages from the documents. The implementation is done using two different transformer models for comparison.

### Overview

The project implements a pipeline that:
1. Extracts text from a collection of PDF documents.
2. Vectorizes the extracted text and stores it in a **FAISS** vector database.
3. Answers user queries by retrieving relevant text passages from the stored vectors.

Two models are used for vectorization to compare their performance:
- **DistilBERT**: A compact version of BERT that is faster.
- **SentenceTransformer (all-MiniLM-L6-v2)**: A model optimized for sentence-level similarity, providing more accurate results.

---

### Key Components

1. **PDF Text Extraction**:
   - Utilizes **PyMuPDF** to extract text from PDF documents.
   - The extracted text is chunked into larger sections for better context in passage retrieval.

2. **Text Vectorization**:
   - Two approaches for vectorizing the extracted text:
     - **DistilBERT**: A lightweight transformer model for faster processing.
     - **SentenceTransformer**: A more accurate model for sentence similarity tasks.

3. **Vector Database**:
   - **FAISS** (Facebook AI Similarity Search) is used to store and search for text vectors efficiently.

4. **Query Answering**:
   - User queries are vectorized and the most relevant text passages are retrieved from the FAISS database.
   - A custom function processes the retrieved chunks to provide a coherent and precise answer.

5. **Summarization**:
   - After retrieving relevant text chunks, a summarization pipeline is applied to generate concise and coherent responses.

---

### Models Used

1. **DistilBERT**:
   - Used for faster vectorization of text with moderate accuracy.
   
2. **SentenceTransformer (all-MiniLM-L6-v2)**:
   - Provides improved accuracy by generating semantically meaningful embeddings, especially at the sentence level.

---

### How the Pipeline Works

1. **Text Extraction**:
   - Extracts raw text from PDF files using **PyMuPDF** and splits it into larger sections to maintain context.

2. **Text Vectorization**:
   - The text sections are vectorized using either **DistilBERT** or **SentenceTransformer** models.

3. **Vector Storage**:
   - Vectorized text is stored in a **FAISS** index for fast similarity-based searches.

4. **Query Answering**:
   - User queries are converted into vectors and compared with the stored vectors.
   - The most relevant text chunks are retrieved, ranked, and summarized to provide a final response.

---

### Comparison of Models

- **DistilBERT**:
  - **Advantages**: Faster processing, lower computational load.
  - **Disadvantages**: Slightly less accurate in retrieving relevant passages.

- **SentenceTransformer**:
  - **Advantages**: More accurate due to better handling of sentence-level semantic similarity.
  - **Disadvantages**: Slower compared to DistilBERT.

---

### Results

- **DistilBERT** offers faster performance but with less precise retrieval of relevant passages.
- **SentenceTransformer** provides more accurate answers, especially for longer and more complex queries, due to its stronger sentence embedding capability.

---

### How to Use

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-username/engAIge-RAG-pipeline.git
   cd engAIge-RAG-pipeline
