# Mini RAG Pipeline (LangChain + FAISS)

This project demonstrates a **basic Retrieval-Augmented Generation (RAG)** pipeline built using open-source tools only.

The goal of this project is to understand how document retrieval and generation work together and where they can fail.

---

## What is RAG?

Retrieval-Augmented Generation (RAG) is a technique where:
1. External documents are retrieved based on a user query
2. The retrieved information is provided as context to a language model
3. The model generates a more informed response

---

## Project Flow

1. Documents are split into chunks
2. Text is converted into embeddings (numerical representations)
3. Embeddings are stored in a FAISS vector database
4. A user query is embedded and matched against stored vectors
5. Relevant documents are retrieved
6. Retrieved context is passed to an LLM for answer generation

---

## Tech Stack

- **LangChain** – pipeline orchestration
- **Sentence-Transformers** – text embeddings
- **FAISS** – vector similarity search
- **Transformers (Hugging Face)** – local LLM (GPT-2 / FLAN-T5)
- **Google Colab** – execution environment

---

## Key Learnings

- Retrieval can work correctly while generation still fails
- Weak or non-instruction-tuned LLMs may hallucinate even with correct context
- RAG systems depend heavily on both retriever quality and LLM alignment

---
## Observed Limitation

When using GPT-2 for generation, the system retrieved correct documents but still produced incorrect/hallucinated answers.

This happened because:
- GPT-2 is not instruction-tuned
- It does not reliably follow prompts that restrict it to provided context
- Retrieval quality alone is not sufficient for grounded generation

This experiment highlights why modern RAG systems rely on instruction-tuned models.

---

## How to Run

1. Open the notebook in Google Colab
2. Run all cells
3. Use the `ask_rag()` function to query the system

---

## Notes

This is an educational mini-project intended to understand RAG fundamentals.  
No paid APIs or proprietary models are used.

---

## Possible Improvements

- Replace GPT-2 with a stronger instruction-tuned model (e.g., FLAN-T5)
- Improve document chunking and overlap
- Add metadata filtering during retrieval
- Use a larger or domain-specific embedding model
