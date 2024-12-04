# rag-bot

### Overview
This project involves an in-depth implementation of a RAG (Retrieval Augmented Generation) model using Langchain integrated with the Milvus vector database. On top of the basic pipeline, the following features have also been implemented:
  - **Hybrid search**: using an ensemble retriever (BM25 retriever and Milvus db retriever) to search for documents.
  - **RAPTOR indexing**: captures low-level and high-level details from the text. Rather than using regular chunks, it clusters those chunks, summarizes them to create new 'distilled' chunks, and so on recursively till a single 'root' cluster is left.
  - **Reranking**: After all the RAPTOR tree nodes have been embedded into the vector db, a reranking model has been used to rerank the context chunks according to relevance to the query for optimal output.

### How to run
1. Clone this repo (preferably in a virtual environment)
    ```bash
    git clone https://github.com/himanshuuu7/rag-bot.git
    ```
2. Make sure you have all the dependencies:
    ```bash
    pip install -r requirements.txt
    ```

3. Download text/PDFs online and replace them in the `data/` folder, or feel free to use mine.
4. Download an appropriate LLM model. You can use any option from OpenAI, Anthropic, etc., or run them locally. Look for .gguf model files [here](https://huggingface.co/TheBloke). **Pick according to available RAM**:
    ```bash
    wget https://huggingface.co/TheBloke/zephyr-quiklang-3b-4K-GGUF/resolve/main/zephyr-quiklang-3b-4k.Q4_K_M.gguf
    ```

5. Finally run the `main.ipynb` in colab or jupyterlab.

### Credits

I have also mentioned references in the notebook, the additional ones are:
  - [RAPTOR repo](https://github.com/parthsarthi03/raptor)
  - [Hybrid search](https://medium.com/etoai/hybrid-search-combining-bm25-and-semantic-search-for-better-results-with-lan-1358038fe7e6)
  - [Reranking](https://www.mixedbread.ai/blog/mxbai-rerank-v1)
  - [Milvus documentation](https://milvus.io/docs/integrate_with_langchain.md)
  
