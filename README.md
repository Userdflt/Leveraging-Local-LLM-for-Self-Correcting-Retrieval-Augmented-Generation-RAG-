# Retrieval-Augmented Generation (RAG) from PDFs with Local Vector Storage (ChromaDB), Enhanced Reflection, and Iterative Self-Correction

[CLICK FOR NOTEBOOK - CODE](file-url)


## Problem Statement
This project aims to enhance the efficiency of answering user queries based on PDFs using Retrieval-Augmented Generation (RAG). The core focus is to refine the retrieval process, ensuring relevant document retrieval, improving the response accuracy through reflection, and employing self-correction mechanisms. The system utilizes local vector storage, managed via **ChromaDB**, to store and retrieve document embeddings efficiently.

## Industry/Domain Context
This method is highly relevant to industries requiring robust document processing and retrieval, such as legal, research, and corporate environments. The system's capability to extract relevant insights from PDFs enhances decision-making processes, especially in document-heavy fields.

## Business Question
- How can we efficiently retrieve and generate responses from PDFs using local vector storage to minimize costs and ensure accuracy?

## Data Question
- How can document embeddings be leveraged in local vector storage to improve retrieval accuracy?

## Data Overview
- The project uses **ChromaDB** for local vector storage of document embeddings. The embedding function utilizes the **"mxbai-embed-large"** model from **Ollama**. The documents are processed using a text-splitter that divides them into chunks for efficient retrieval.

## Process (more PDF files can be added)
1. **Data Preprocessing**:
    - PDFs are split into manageable chunks using the `RecursiveCharacterTextSplitter`. Each chunk is indexed by source and page for easy retrieval.
2. **Document Storage and Retrieval** (with update function if new files added):
    - The system uses **ChromaDB** to create collections of embeddings. New chunks are processed and added to the local database. 
    - **ChromaEmbeddingFunction** is used to create vector embeddings for retrieval.
3. **Vector Store Queries**:
    - Queries like "What are the permitted activities?" invoke the retriever, which pulls relevant chunks from **ChromaDB** based on similarity.

## Modeling
The system uses multiple models and processes to ensure accurate results:
- **Retrieval Grading**: A local model (**Llama3.1**) assesses the relevance of retrieved documents using a scoring mechanism that checks if the document contains keywords related to the query.
- **Answer Generation**: A local **RAG (Retrieval-Augmented Generation)** model generates answers based on the retrieved documents, ensuring a structured response.
- **Hallucination Checking**: Another instance of the **Llama3.1** model verifies whether the generated answer contains hallucinations or fabricated information.
- **Reflection**: The reflection process compares the generated response with the retrieved documents and suggests improvements if the answer lacks crucial information.

## Comparisons and Improvements
- **Retrieval Quality**: The system grades the relevance of documents, ensuring only relevant documents are passed to the generation stage. Irrelevant documents trigger additional retrieval or web search as a fallback.
- **Answer Generation**: The generated answers are refined through iterative reflection and hallucination checks. Incomplete answers are revisited, and documents are updated with missing information.

## Outcomes
- **Enhanced Retrieval**: By storing embeddings locally in **ChromaDB**, retrieval speed and accuracy are improved without relying on external API calls.
- **Improved Answer Quality**: Iterative self-correction through reflection ensures that incomplete or incorrect answers are flagged and corrected before presenting the final response.
- **Scalability**: The system's reliance on local vector storage makes it scalable to larger datasets without significant costs related to external storage or processing.

## Data Answer
- The use of local vector storage with **ChromaDB** allows for efficient retrieval and enhanced reflection processes, improving the relevance of the generated answers and ensuring that incomplete answers are flagged for correction.

## Business Answer
- This system provides a scalable and cost-effective solution for retrieving and generating accurate responses from PDFs, improving decision-making processes in document-heavy industries.

## End-to-End Solution
- The system provides an end-to-end solution for querying, retrieving, generating, and refining answers from PDF documents stored in a local vector database. It integrates local models for retrieval grading, hallucination checking, and reflection to ensure high-quality outputs.
