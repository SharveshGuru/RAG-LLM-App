# RAG System with Ollama and Mistral LLM

This project implements a Retrieval-Augmented Generation (RAG) system using Ollama's local Mistral LLM. The system is designed to answer questions based on the official Django documentation.

## Project Overview

The RAG system works by:
1. Loading and processing PDF documents (Django documentation)
2. Splitting the documents into chunks
3. Storing the chunks in a Chroma vector database
4. Using similarity search to find relevant context for a given query
5. Generating responses using the Mistral LLM through Ollama

## Requirements

- Python 3.x
- Google Colab (for easy setup and execution)
- Ollama
- Mistral LLM model

## Installation

1. Clone this repository or create a new Colab notebook.

2. Install the required Python packages:

   ```
   !pip install -r requirements.txt
   ```

   The `requirements.txt` file should contain:

   ```
   pypdf
   langchain
   chromadb
   pytest
   boto3
   colab-xterm
   langchain_community
   langchain-chroma
   langchain-ollama
   ```

3. Set up Ollama:

   a. Load the Colab terminal extension:
      ```python
      %load_ext colabxterm
      ```

   b. Launch the terminal:
      ```python
      %xterm
      ```

   c. In the terminal, install Ollama:
      ```bash
      curl https://ollama.ai/install.sh | sh
      ```

   d. Start the Ollama server:
      ```bash
      ollama serve
      ```

   e. Open a new terminal and pull the Mistral model:
      ```bash
      ollama pull mistral
      ```

## Usage

1. Set the appropriate paths for your environment:

   ```python
   CHROMA_PATH = "/content/chroma"
   DATA_PATH = "/content/data"
   ```

2. Load and process the documents:

   ```python
   documents = load_documents()
   chunks = split_documents(documents)
   add_to_chroma(chunks)
   ```

3. Run queries using the RAG system:

   ```python
   while True:
     print("Enter query or type \"Exit\" to exit.")
     query_text = input().strip().lower()
     if query_text == "exit":
       break
     query_rag(query_text)
   ```

## Project Structure

- `load_documents()`: Loads PDF documents from the specified directory.
- `split_documents()`: Splits documents into smaller chunks for processing.
- `add_to_chroma()`: Adds document chunks to the Chroma vector database.
- `calculate_chunk_ids()`: Assigns unique IDs to document chunks.
- `clear_database()`: Clears the existing Chroma database.
- `query_rag()`: Performs the RAG process to answer queries.

## Customization

You can customize the project by:
- Changing the `CHROMA_PATH` and `DATA_PATH` variables to point to your desired locations.
- Modifying the chunk size and overlap in the `split_documents()` function.
- Adjusting the number of similar documents retrieved in the `query_rag()` function.
- Changing the LLM model or its parameters in the `OllamaLLM` configuration.

## Notes

- This project is set up to run in Google Colab for ease of use and setup.
- The system uses Django's official documentation as the knowledge base, but you can replace it with any other PDF documents.
- Ensure you have sufficient storage and processing power when working with large document sets.

## Contributing

Contributions to improve the project are welcome. Please feel free to submit issues or pull requests.


