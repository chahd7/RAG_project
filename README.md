# RAG project

This is a project done in the context of the Data warehousing and Business intelligence course during the Spring 2026. It works with Sample superstore data from the US that spans from 2014 to 2017. The system takes this row data, transforms it accordingly into different textual representations, and tests different chunking strategies. The most optimal chunking strategy found and used is the fixed-size with 1000 characters strategy. 

The documents are then embedded and stored with the corresponding metadata into the ChromaDB vector database using the MiniLM-L6-v2 model. Two different fetching functions are used and compared: similarity_search which retrieves all the documents that are relevant to the query, and metadata_filtering which comes to filter the returned documents based on the provided filter. The best results were obtained using the metadata_filtering approach and it is therefore the final selected method. The queries were embedded using the same embedding function.

Two different LLMs were used: Mistral and Gemma4 all provided through Ollama. Mistral provided average results and struggled with logic while Gemma4 showcased a strong performance across all queries, making it the final choice for the LLM. 

The pipeline is as follows: 
<p align="center">
  <img src="rag_pipeline_architecture.png" alt="RAG System Architecture" width="600"/>
</p>
