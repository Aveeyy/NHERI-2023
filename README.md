**Mini Retrieval-Augmented QA for Technical Documentation**

This project implements a lightweight retrieval-augmented question answering (RAG) pipeline over Markdown-based technical documentation. Given a natural-language question, the system retrieves the most relevant document sections using embeddings and cosine similarity, then generates an answer grounded strictly in the retrieved context.

The goal of this project is to explore document ingestion, chunking strategies, semantic search, and prompt construction for factual QA over unstructured technical text.

**How It Works**

1.Document Ingestion

    -Markdown files are loaded from a local directory.

    -Files are converted to HTML and parsed using BeautifulSoup.

    -Headings and their associated paragraphs are grouped into logical sections.

2.Chunking & Token Budgeting

    -Long sections are split into smaller chunks using a word-based chunking strategy.

    -Each chunk is annotated with an approximate token count (GPT-2 tokenizer) for prompt budgeting.

3.Embedding & Retrieval

    -Each document chunk is embedded using the OpenAI Embeddings API.

    -For a given query, cosine similarity is used to retrieve the most relevant chunks.

4.Prompt Construction & Answering

    -Retrieved chunks are concatenated into a bounded context window.

    -The model is instructed to answer only using the provided context, and to respond with “I don’t know” if the answer is not present.
