# DataSageAI

## Overview

DataSageAI is an AI-powered knowledge retrieval system that scrapes the web, stores information in a vector database, and uses an LLM to generate context-aware responses. Given a topic and URLs, the system fetches relevant content, processes it, and allows users to query for insights based on retrieved knowledge.

## Features

- Accepts user-defined topics and URLs for web scraping.
- Automatically finds related URLs to expand knowledge coverage.
- Stores scraped content as embeddings using **multi-qa-mpnet-base-dot-v1**.
- Uses **ChromaDB** for similarity search on stored embeddings.
- Generates contextually relevant responses using **T5-small** LLM.
- Interactive querying after initial data processing.

## Installation

Ensure you have the required dependencies installed. Run the following commands in your Colab environment:

```bash
pip install -U langchain-community
pip install tavily-python
pip install langchain
pip install chromadb
pip install sentence_transformers
pip install huggingface_hub
```

## Usage

1. Open the Colab notebook.
2. Input a **topic** and a list of **URLs**.
3. Wait for the system to scrape, process, and store the data.
4. Once processed, you can query the system multiple times using natural language questions.
5. The system will retrieve the most relevant context and generate an answer using the LLM.

## Configuration

- **Tavily API Key**: Required for web scraping. Set it up in the notebook.
- **Hugging Face Access Token**: Needed for loading the embedding model.
- Other configurations (like number of related URLs fetched) can be modified in the notebook settings.

## Architecture

1. **Input:** User provides topic and URLs.
2. **Web Scraping:** Tavily fetches content from the provided and related URLs.
3. **Vector Storage:** Processed text is converted to embeddings using **multi-qa-mpnet-base-dot-v1** and stored in **ChromaDB**.
4. **Querying:** The user provides their query.
5. **Similarity Search:** User query is converted to an embedding and compared against stored embeddings.
6. **LLM Response Generation:** Retrieved context is passed to **T5-small**, which generates an answer.

## Notebook Explanation

The Colab notebook is organized into distinct sections to promote clarity and modularity:

- **Crawler Agent:** Handles web scraping using Tavily, retrieving content from provided and related URLs.
- **QnA Agent:** Manages the querying process by performing similarity searches on the vector database (ChromaDB) and generating responses with the T5-small LLM.

Detailed explanations, inline comments, and design rationales are provided throughout the notebook.&#x20;

---

Possible future improvements: Implementing more advanced embedding models and LLMs for enhanced answer quality, optimizing embedding retrieval for faster and more accurate results, and improving web scraping capabilities to extract richer information.

