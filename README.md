# French-pdfs

How the System Works

PDF Processing

PDF files are first read page by page and converted into clean text.
The extracted text is normalized, filtered, and split into overlapping chunks to preserve context and ensure stable retrieval from long legal documents.

Encoder Model (Semantic Retrieval)

A multilingual sentence-embedding encoder converts both document chunks and user questions into numerical vectors that represent their meaning.
These embeddings are stored in a FAISS index, enabling fast and accurate semantic search to retrieve the most relevant passages related to a question.

Retriever

The retriever compares the question embedding with document embeddings and selects the highest-scoring text chunks.
Only passages above a similarity threshold are kept, ensuring that irrelevant content is excluded early.

Decoder Model (Answer Generation)

A lightweight sequence-to-sequence decoder generates a short French answer using only the retrieved passages.
The model is strictly constrained to the provided facts and is instructed to respond “Je ne sais pas d’après ce document.” when the information is missing or unclear.

Safety and Reliability

Single-document answering to avoid mixing legal sources

Page-level source attribution

Strict prompt and output validation to reduce hallucinations
