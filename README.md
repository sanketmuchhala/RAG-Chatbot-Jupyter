RAG Chatbot with DeepSeek API and FAISS
This project implements a Retrieval-Augmented Generation (RAG) chatbot in a Jupyter Notebook, enabling users to query content from .pdf, .docx, or .txt files. It combines semantic search with generative AI to provide contextually relevant answers.
Overview
The RAG Chatbot processes documents by:

Extracting text from supported file formats.
Splitting text into overlapping chunks for context preservation.
Generating embeddings using a local sentence-transformers model (all-MiniLM-L6-v2).
Storing embeddings in a FAISS index for efficient similarity search.
Retrieving relevant chunks based on user queries.
Querying the DeepSeek Chat API with the retrieved context to generate answers.

The notebook is designed for practitioners interested in natural language processing (NLP), semantic search, and large language models (LLMs).
Prerequisites

Python: Version 3.7 or higher.
Jupyter Notebook: For running the .ipynb file.
DeepSeek API Key: Obtain from DeepSeek.
Supported File Formats: .pdf, .docx, or .txt files containing the content to query.

Installation

Clone or Download the Notebook:

Download RAG.ipynb to your local machine or clone the repository if hosted.


Install Dependencies:Run the following command to install required Python packages:
pip install faiss-cpu tiktoken openai python-docx pdfplumber PyMuPDF sentence-transformers --quiet


Set Up DeepSeek API Key:

Obtain your API key from DeepSeek.
In the notebook, replace "ENTER_YOUR_DEEPSEEK_API_KEY" with your actual key:os.environ["DEEPSEEK_API_KEY"] = "your-api-key-here"





Usage

Open the Notebook:

Launch Jupyter Notebook:jupyter notebook RAG.ipynb




Run Cells Sequentially:

Execute each cell in order to:
Install dependencies (if not already installed).
Import libraries and set the API key.
Load and process your document.
Generate and store embeddings.
Query the chatbot with your question.




Load a Document:

When prompted, enter the path to your .pdf, .docx, or .txt file. For example:/Users/username/Documents/sample.pdf




Ask Questions:

Input your question when prompted (e.g., "Tell me about the evolution of AI").
The chatbot retrieves relevant document chunks and generates an answer using the DeepSeek API.


View Results:

Retrieved chunks and the final answer are displayed in Markdown format within the notebook.



Flowchart
Below is a flowchart illustrating the RAG Chatbot's workflow, written in Mermaid syntax for rendering on compatible platforms (e.g., GitHub).
graph TD
    A[Start] --> B[Load Document<br>(.pdf/.docx/.txt)]
    B --> C[Extract Text]
    C --> D[Split Text into<br>Overlapping Chunks]
    D --> E[Generate Embeddings<br>(SentenceTransformer)]
    E --> F[Store Embeddings<br>in FAISS Index]
    F --> G[User Inputs Question]
    G --> H[Encode Question<br>(SentenceTransformer)]
    H --> I[Retrieve Top-K Chunks<br>from FAISS]
    I --> J[Combine Chunks<br>as Context]
    J --> K[Query DeepSeek API<br>with Context]
    K --> L[Display Answer<br>in Markdown]
    L --> M[End]

Project Structure

RAG.ipynb: The main Jupyter Notebook containing the RAG Chatbot implementation.
No additional files are required, but you need a document (.pdf, .docx, or .txt) to query.

Notes

Performance: The all-MiniLM-L6-v2 model is lightweight and runs locally, making it cost-effective and fast for embedding generation.
Token Limits: The DeepSeek API context is capped at 6000 characters to avoid token overflow. Adjust max_context_chars in the notebook if needed.
Error Handling: Ensure your DeepSeek API key is valid. Check for network issues if API requests fail.
Security: Verify the legitimacy of any external APIs or services used. Store API keys securely and avoid hardcoding them in production.
Customization:
Modify max_tokens (default: 500) or overlap (default: 50) in the split_text function to adjust chunk size.
Increase k in retrieve_top_k to retrieve more context chunks for broader answers.


Limitations:
The notebook assumes a single document. For multiple documents, modify the code to process and index multiple files.
The DeepSeek API requires an active internet connection.



Example
Input File: llm.pdf (a document about large language models).Question: "Tell me about the evolution of AI."Output: A detailed answer summarizing the evolution from bag-of-words models to modern LLMs, based on the document's content.
Troubleshooting

File Loading Errors: Ensure the file path is correct and the file format is supported.
API Errors: Check your DeepSeek API key and internet connection. Review the error message printed by the notebook.
Embedding Issues: If embeddings fail, ensure sentence-transformers is installed and the model (all-MiniLM-L6-v2) is downloaded.

Contributing
Feel free to fork this project, enhance the notebook, or submit pull requests with improvements. Suggestions for additional features (e.g., multi-document support, different embedding models) are welcome.
License
This project is licensed under the MIT License. See the LICENSE file for details (if applicable).
