# RAG project

This is a project done in the context of the Data warehousing and Business intelligence course during the Spring 2026. It works with Sample superstore data from the US that spans from 2014 to 2017. The system takes this row data, transforms it accordingly into different textual representations, and tests different chunking strategies. The most optimal chunking strategy found and used is the fixed-size with 1000 characters strategy. 

The documents are then embedded and stored with the corresponding metadata into the ChromaDB vector database using the MiniLM-L6-v2 model. Two different fetching functions are used and compared: similarity_search which retrieves all the documents that are relevant to the query, and metadata_filtering which comes to filter the returned documents based on the provided filter. The best results were obtained using the metadata_filtering approach and it is therefore the final selected method. The queries were embedded using the same embedding function.

Two different LLMs were used: Mistral and Gemma4 all provided through Ollama. Mistral provided average results and struggled with logic while Gemma4 showcased a strong performance across all queries, making it the final choice for the LLM. 

The pipeline is as follows: 
<p align="center">
  <img src="rag_pipeline_architecture.png" alt="RAG System Architecture" width="600"/>
</p>

# How to run it

1. Clone the repository (make sure that the files and the data file are in the same folder)
2. Install the dependences
```bash
pip install -r requirements.txt
```
3. Install Ollama from https://ollama.com
4. Run the data_preparation_final.ipynb file for the data preprocessing and textual representation creation
5. Run the vector database setup in rag_pipeline_final.ipynb . In the case where you want to repopulate the vector database after already populating it once, you can uncomment:
```bash
chroma_client.delete_collection(name="project")
```
7. Pull Mistral from Ollama using the terminal in your directory and the command:
```bash
ollama pull mistral
```
8. Run Mistral from Ollama using the terminal in your directory and the command
```bash
ollama run mistral
```
9. Run the "RAG Pipeline Implementation - Mistral Approach" section from rag_pipeline_final.ipynb
10. After it is done, click on CTRL+D to stop mistral from running in your terminal
11. Pull Gemma4 from Ollama using the terminal in your directory and the command:
```bash
ollama pull gemma4
```
12. Run Gemma4 from Ollama using the terminal in your directory and the command
```bash
ollama run gemma4
```
13. Run the RAG Pipeline Implementation - Gemma4 Approach" section to get the results with Gemma4
14. Run the FINAL FULL PIPELINE PERFORMANCE ON QUERIES section to get the final results on each of the chosen queries. 
