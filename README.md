# Rag_demonstration
This repo contains the Rag implementation for different Handling Documents with Mixed Formats and Improving Chunking and Retrieval Strategies

Installation

Clone this repository:

git clone https://github.com/your-repo/document-retrieval.git
cd document-retrieval

Create a virtual environment and install dependencies:

python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt

Set the OpenAI API key:

export OPENAI_API_KEY="your_openai_api_key"

Usage

1. PDF Processing

Extracts text and tables from PDFs using:

raw_pdf_elements = partition_pdf(
    filename="path_to_pdf",
    extract_images_in_pdf=False,
    infer_table_structure=True,
    chunking_strategy="by_title",
    max_characters=4000,
    new_after_n_chars=30,
    combine_text_under_n_chars=20,
)

2. Summarization

Summarizes tables and texts using GPT-4:

table_summaries = summarize_chain.batch(tables, {"max_concurrency": 5})
text_summaries = summarize_chain.batch(texts, {"max_concurrency": 5})

3. Storage & Retrieval

Stores summaries in Chroma vectorstore and InMemoryStore.

Retrieves context-aware answers using:

chain.invoke("Your question here")

Enhancements To Be Implemented

Better Table Formatting: Use Markdown-like table representation.

Semantic Chunking: Integrate embedding-based text chunking.

Multi-Step Retrieval: Implement multi-level search for better accuracy.

Complex Query Handling: Add query splitting and response synthesis.
