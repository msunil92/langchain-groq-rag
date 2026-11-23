# RAG notebooks

This folder contains notebook examples for the main stages of retrieval-augmented generation (RAG): loading documents, splitting text, embedding chunks, storing and retrieving them, and using retrieved context in a chat.

## Notebooks

- [read_docs.ipynb](./read_docs.ipynb) demonstrates loading a local text file, web pages, and a PDF.
- [splitter.ipynb](./splitter.ipynb) compares character-based and recursive text splitting using `../data/essentials.txt`.
- [embeddings_vectors.ipynb](./embeddings_vectors.ipynb) embeds a Wikipedia page with `sentence-transformers/all-MiniLM-L6-v2`, searches Chroma and FAISS vector stores, and demonstrates the Wikipedia retriever.
- [retrievers.ipynb](./retrievers.ipynb) builds an in-memory vector store from Anthropic's Wikipedia page and compares similarity search with `WikipediaRetriever`.
- [chat_rag_agent.ipynb](./chat_rag_agent.ipynb) runs a RAG chat over Anthropic content, keeping conversation history between turns.

The notebooks are independent examples; run the cells in a notebook from top to bottom. Use the repository's Python environment as the notebook kernel. Each notebook includes package installation cells. Internet access is needed to fetch web pages and model weights.

## Chat configuration

`chat_rag_agent.ipynb` uses Groq. Set `GROQ_API_KEY` in the environment or in a local `.env` file before running its setup cells. Do not commit the key.

## Generated vector-store data

Running `embeddings_vectors.ipynb` creates local Chroma and FAISS data under `chroma_langchain_db/` and `faiss_langchain_db/`.

The FAISS example loads a pickle-backed document store with `allow_dangerous_deserialization=True`. Only load an index you created and trust; a modified or untrusted pickle can execute code.
