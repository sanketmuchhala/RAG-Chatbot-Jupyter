RAG Chatbot with DeepSeek API and FAISS

This project implements a Retrieval-Augmented Generation (RAG) chatbot in a Jupyter notebook, enabling users to query content from .pdf, .docx, or .txt files. It combines local embeddings for semantic search with the DeepSeek API for generating contextually grounded answers.
Table of Contents

Overview
Features
Prerequisites
Installation
Usage
Flowchart
File Structure
Troubleshooting
Contributing
License

Overview
The RAG Chatbot processes documents by extracting text, chunking it, generating embeddings using a local model (all-MiniLM-L6-v2), storing them in a FAISS index for efficient retrieval, and querying the DeepSeek API to generate answers based on retrieved context. This approach ensures answers are grounded in the document content while leveraging powerful language generation.
Features

Supports .pdf, .docx, and .txt file formats.
Uses sentence-transformers for local embeddings (no API cost).
Employs FAISS for fast vector-based semantic search.
Integrates with DeepSeek API for high-quality answer generation.
Handles large documents by chunking with overlap to preserve context.
Displays answers in formatted Markdown within Jupyter.

Prerequisites

Python 3.8 or higher
Jupyter Notebook
DeepSeek API key (sign up at DeepSeek)
Supported file types: .pdf, .docx, .txt

Installation

Clone the Repository (or download the notebook):
git clone <repository-url>
cd <repository-directory>


Install Dependencies:Run the following command to install required Python packages:
pip install faiss-cpu tiktoken openai python-docx pdfplumber PyMuPDF sentence-transformers


Set Up DeepSeek API Key:

Obtain your API key from DeepSeek.
In the notebook, replace "ENTER_YOUR_DEEPSEEK_API_KEY" with your key in the cell under Step 2:os.environ["DEEPSEEK_API_KEY"] = "your-api-key-here"





Usage

Open the Notebook:Launch Jupyter Notebook and open RAG.ipynb:
jupyter notebook


Run the Cells Sequentially:

Execute each cell in order, starting with library imports and API key setup.
When prompted, provide the path to your .pdf, .docx, or .txt file (e.g., /path/to/your/file.pdf).
Enter a question when prompted (e.g., "Tell me about the evolution of AI").


View Results:

The notebook will display the top retrieved document chunks and the DeepSeek API's answer in Markdown format.


Example:

Input file: llm.pdf
Question: "Tell me about the evolution of AI"
Output: A detailed answer summarizing the evolution of language AI, grounded in the document.



Flowchart
Below is a flowchart illustrating the RAG Chatbot's workflow, rendered using Mermaid syntax:
graph TD
    A[Start] --> B[Load Document<br>(.pdf/.docx/.txt)]
    B --> C[Extract Text]
    C --> D[Chunk Text<br>(500 tokens, 50 overlap)]
    D --> E[Generate Embeddings<br>(all-MiniLM-L6-v2)]
    E --> F[Store in FAISS Index]
    F --> G[User Inputs Question]
    G --> H[Encode Question]
    H --> I[Retrieve Top-K Chunks<br>(FAISS Search)]
    I --> J[Combine Chunks<br>as Context]
    J --> K[Query DeepSeek API]
    K --> L[Display Answer<br>(Markdown)]
    L --> M[End]

File Structure
├── RAG.ipynb        # Main Jupyter notebook with RAG implementation
├── README.md        # This file
└── <your-document>  # Your .pdf, .docx, or .txt file (user-provided)

Troubleshooting

API Key Error: Ensure your DeepSeek API key is correctly set in the notebook.
File Not Found: Verify the file path is correct and the file is a supported type (.pdf, .docx, .txt).
Module Not Found: Install all dependencies listed in the Installation section.
DeepSeek API Failure: Check your internet connection and API key validity. Inspect the error message printed in the notebook.
Line Spacing Issue: If Markdown rendering looks off, ensure no extra spaces or tabs exist in the notebook’s Markdown cells.

Contributing
Contributions are welcome! Please:

Fork the repository.
Create a feature branch (git checkout -b feature/new-feature).
Commit changes (git commit -m 'Add new feature').
Push to the branch (git push origin feature/new-feature).
Open a pull request.

License
This project is licensed under the MIT License. See the LICENSE file for details.
