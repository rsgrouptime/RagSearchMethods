## Project Title
Comparative Analysis of Retrieval-Augmented Generation (RAG) Search Techniques

## Table of Contents
1. Overview
2. Project Structure
3. Installation
4. Usage
5. Features
6. Comparison Analysis
7. References
8. Acknowledgments
9. Future Enhancements

## Overview
This project provides a series of Jupyter notebooks that explore and compare various Retrieval-Augmented Generation (RAG) search techniques. Each notebook evaluates a different RAG method, focusing on key performance metrics like latency and response time, enabling developers and knowledge seekers to gain hands-on experience and insights into these techniques. Together, these notebooks serve as a "cookbook" for those looking to deepen their understanding of RAG search techniques, practice implementing them locally, and enhance their knowledge in search optimization and retrieval-augmented generation.

## Project Structure
        RagSearchMethods/
            ├── config/             # configuration files
            ├── data/               # Datasets or other input files
            ├── input_pdfs/         # Input Unstructured PDF documents
            ├── src/                # Source code and Jupyter Notebook files (.ipynb)
            ├── README.md           # Project overview and instructions
            ├── requirements.txt    # List of dependencies
            └── .gitignore          # files and directories to ignore when you make a commit

## Installation

**Python** - Installed Python 3.11.8 for this project structure, ensuring compatibility with the latest Python features and improvements.<br>

**Docker Desktop Setup on windows**

1. Install Docker Desktop<br>
    **Download:** Go to the [Docker Desktop download Page](https://docs.docker.com/desktop/install/windows-install/) and download the Windows version.<br>
    **Install:** Run the installer and follow the on-screen instructions.<br>
    **Enable WSL 2:** During installation, Docker will prompt you to enable Windows Subsystem for Linux 2 (WSL 2). Follow the prompts to do so if not already enabled.<br>
2. Start Docker Desktop<br>
    Launch Docker Desktop. It should automatically start Docker Engine and the WSL 2 backend.
3. Verify Installation<br>
    Open Command Prompt or PowerShell and **run** :
    > docker --version<br>
    > docker run hello-world <br>
   - The "hello-world" message confirms Docker is running correctly.
4. Configure Docker Settings (Optional)<br>
    Open Docker Desktop settings to allocate memory, CPU, or disk space based on your requirements.
    
**Qdrant VectorDB Setup**:

To search for Qdrant images in Docker Desktop, follow these steps:

1. Open Docker Desktop<br>
    Launch Docker Desktop on your Windows 11 machine.
2. Navigate to the Images Tab<br>
    In Docker Desktop, click on the Images tab located in the left sidebar.
3. Search for Qdrant<br>
    In the **search bar** at the top, type **"qdrant"** and press Enter.<br>
    Docker will search Docker Hub (Docker’s image repository) for any official or community images related to Qdrant.
4. Select and Pull the Qdrant Image<br>
    Browse through the search results to find the official Qdrant image, which is usually labeled as **"qdrant/qdrant"**.<br>
    Click on the Pull button next to the image to download it to your local system.
5. Verify Image Download<br>
    Once downloaded, the Qdrant image will appear in your Images list. You can then start a container based on the Qdrant image directly from Docker Desktop.<br>
These steps will help you locate, pull, and verify the Qdrant image in Docker Desktop.
    

**HuggingFace Credential Setup:**

To create Hugging Face credentials (token) using the provided URL, follow these steps:<br>

1. Open the URL<br>
    Go to [Hugging Face Pages](https://huggingface.co/settings/tokens).
2. Log in to Your Hugging Face Account<br>
    If you are not already logged in, you’ll need to sign in. If you don’t have an account, you can create one for free.
3. Generate a New Token<br>
    On the Access Tokens page, find the section labeled New token.<br>
    Enter a name for your token (e.g., "My Project Token").<br>
    Choose the Role (permissions level) for your token:<br>
    **Read:** For downloading models and datasets.<br>
    **Write:** For uploading new models or datasets.<br>
    **Admin:** Full access, including management of other tokens.<br>
    Click on the Generate New Token button.
4. Copy the Token<br>
    Once generated, copy the token immediately, as this is the only time you’ll be able to see it in full.
5. Save Your Token Securely<br>
    Store your token in a secure place (e.g., a password manager or an environment variable in your codebase) to use when accessing Hugging Face resources.<br>

Now you’re ready to use this token to authenticate API requests or set it in your code to download Hugging Face models and datasets.
    
**Python Packages**

To install Python packages from a requirements.txt file, follow these steps:<br>

1. Ensure Python and pip are Installed<br>
    Make sure you have Python and pip installed. You can verify by running:<br>
        
    > python --version
    > pip --version

2. Navigate to the Project Directory<br>
    Open a terminal (or command prompt) and navigate to the directory where the requirements.txt file is located:<br>
        
    > cd path/to/your/project

3. Install Packages from requirements.txt<br>
    Run the following command to install all packages listed in requirements.txt:<br>

    > pip install -r requirements.txt

4. Verify Installation<br>
    You can verify that the packages are installed by listing all installed packages:<br>

    > pip list

5. If you encounter permissions issues, add --user to install packages for the current user:<br>
        
    > pip install -r requirements.txt --user

6. For virtual environments, ensure the environment is activated before running the pip install command.<br>

This process will install all specified packages and their dependencies as listed in requirements.txt.

## Usage
**Qdrant vector DB:**<br>
To use a Qdrant Docker image in Docker Desktop for a Python application, follow these steps:<br>
- Pull the Qdrant Docker Image: Run this command in docker desktop to pull the latest Qdrant image:<br>
> docker pull qdrant/qdrant 

- Run the Qdrant Container: Start the Qdrant container with port mapping to access it from your Python application:<br>
This maps port 6333 on your local machine to Qdrant’s API port in the container.<br>

- Connect Python Application to Qdrant: In your Python code, connect to Qdrant using its API (e.g., qdrant-client library):<br>
> from qdrant_client import QdrantClient<br>
> client = QdrantClient(host="localhost:32768", port=6333)<br>

Connect to Qdrant instance running in Docker. Host port can be change when you start the container.<br>
Now, you can use client to interact with Qdrant for operations like creating collections, uploading data, and querying.<br>

**HuggingFace Token Declaration:**<br>
To use a Hugging Face token stored in a config/global_config.json file in a Python application, you can follow these steps:<br>
- Store the Token in JSON: Ensure your global_config.json has a structure like this:<br>
> {<br>"huggingface_token": "your_huggingface_token_here"<br>}<br>

- Load the Token in Python: Use Python's json library to load the token from the JSON file:<br>
> import json <br># Load the configuration file <br> with open('config/global_config.json', 'r') as f:<br>gconf = json.load(f)<br># Access the Hugging Face token<br>hf_token = gconf['huggingface_token']<br>

- Use the Token: Now you can use hf_token in your Hugging Face API calls, for instance, with transformers or huggingface_hub libraries.<br>

**Project Structure:**<br>
- src/
    - This folder contains different RAG Search .ipynb notebooks. Below are the available steps to execute the notebooks:
        1. Clone the Repository
            Start by cloning this repository to your local machine using the following command:
            
            > git clone <repository-url>
            > cd <repository-folder> 
        
        2. Set Up the Environment
            Ensure you have Python installed, and create a virtual environment to manage dependencies:

            > python -m venv env
            > source env/bin/activate  # On Windows: env\Scripts\activate

        3. Install Dependencies
            Install all the required packages from the requirements.txt file:

            > pip install -r requirements.txt
        
        4. Open Jupyter Notebook
            Launch Jupyter Notebook to access the .ipynb files:

            > jupyter notebook
            OR
            > python -m jupyter notebook

        5. Navigate to Notebooks
            In Jupyter Notebook, navigate to the folder containing the RAG search notebooks and open the desired .ipynb file.

        6. Run the Notebook Cells
            Each notebook is designed to be executed cell by cell. Run each cell sequentially by selecting the cell and pressing Shift + Enter. Follow any additional instructions within the notebook for each specific RAG search technique.

        7. Review and Compare Results
            Observe the outputs and performance metrics, such as latency and response time, to understand the differences among the various RAG search techniques.
- data/
    - This folder stores the converted nodes from extracted PDF documents in a JSON object. Read the saved nodes and create reuired embbendings to store into target Database.  
- input_pdfs/
    - This folder contains all the necessary input PDF files, which will have their extracted content stored in a vector database.
- config/
    - This folder contains the global_config.json file, where predefined variables are initialized with hardcoded values, which are subsequently used in the notebooks. Please update these variable values with your specific settings.

## Features
- This is a breakdown of the functionality available in different notebooks. Follow the steps in each notebook sequentially to execute and verify their functionality, as listed below:<br>
    **1. RAG_dense_FastEmbed.ipynb**
    - This notebook applies the dense vector search technique to the *Fastembed Model* embedded data stored in the Qdrant database, specifically within the collection named **RAGdenseCollection**.
    
    **2. RAG_dense_HFEmbed.ipynb**
    - This notebook applies the dense vector search technique to the *Hugging Face Model* embedded data stored in the Qdrant database, specifically within the collection named **RAGdenseHFEmbedCollection**.<br>
    DENSE Search Flow:<br><br>![image](https://github.com/user-attachments/assets/a1a6b57d-1f5e-4707-85de-4e4d6e1494d1)

    **3. RAG_sparse_FastEmbed.ipynb**
    -  This notebook applies the sparse vector search technique to the *Fastembed Model* embedded data stored in the Qdrant database, specifically within the collection named **RAGSparseCollection**.<br>
      Sparse Search Flow:<br><br> ![image](https://github.com/user-attachments/assets/2d8e5f08-6a26-48fe-9d3e-f8d61cacb383)<br>
      Used BM42 embedding model in this code repository. [Try with other COIL, TILDEv2, SPLADE, and more sparse based models](https://qdrant.tech/articles/modern-sparse-neural-retrieval/)   

    **4. RAG_HybridSearch.ipynb**
    -  This notebook applies the hybrid search technique (Vector + Sparse(bm42)) to the *Fastembed Model* embedded data stored in the Qdrant database, specifically within the collection named **RAGCheckCollection**. Furthermore, it uses the (RRF) Reciprocal Rank Fusion is a rank aggregation method that combines rankings from multiple sources into a single, unified ranking for synthesization.<br>
      Hybrid Search: ![image](https://github.com/user-attachments/assets/b85234bf-5632-4acd-87e4-650e8a5ef1b0)
      Fusion Search: ![image](https://github.com/user-attachments/assets/aa789c03-c850-40e0-8b5b-e36b1584051f)

    **5. RAG_HyDE_MannualFlow.ipynb**
    -  This notebook applies the hybrid search technique (Vector + Sparse(bm42)) to the *Fastembed Model* embedded data stored in the Qdrant database, specifically within the collection named **RAGCheckCollection**.It uses the (HyDE) Hypothetical Document Embedder is an embedding technique that takes queries, generates a hypothetical answer, and then embeds that generated document and uses that as to reterive the context from the retriever. Finally, it pass the hypothetical document + context to the LLM for the final answer generation.
      ![image](https://github.com/user-attachments/assets/703fdcc7-2baf-4ec9-99c9-6878990a7801)
    
    **6. RAG_HyDE_PredefinedFunction_HDE.ipynb**
    - This notebook applies the same approach as outlined in point 5, with one key difference: here, I've used the predefined LangChain HypotheticalDocumentEmbedder method. This streamlines the process by eliminating the manual effort required to call the LLM and embeddings externally to generate hypothetical answers.
      ![image](https://github.com/user-attachments/assets/91afabb4-9f24-4621-b690-9b3da55b7b2f)
      ![image](https://github.com/user-attachments/assets/0cb0e61f-c90b-4f8b-9ada-91f4e3fe2768)

    **7. RAG_HierIndexSearch.ipynb**
    -  This notebook applies the hybrid search technique (Vector + Sparse(bm42)) to the *Fastembed Model* embedded data stored in the Qdrant database, specifically within the collection named **RAGHierIndexCollection** for summaries index and **RAGHierIndexCollectionSummary** for detailed chunks. It uses the Hierarchical indexing in Retrieval-Augmented Generation (RAG) works by first create an index for summaries and a second index for document chunks. This strategy enables quick filtering of pertinent documents using summaries, allowing for deeper searches within the chosen documents for the improved comprehension and response generation.
      ![image](https://github.com/user-attachments/assets/ae2cc2c9-8f4f-45aa-9396-06d546b9c268)

    **SMALL TO BIG RAG SEARCH METHODS:**<br>
    **8. RAG_Parent_Child_Retrieval.ipynb** - Parent Document Retriever
    -  This notebook applies the hybrid search technique (Vector + Sparse(bm42)) to the *Fastembed Model* embedded data stored in the Qdrant database, specifically within the collection named **RAGParentChildCollection**. It uses the Parent Document Retriever in Retrieval-Augmented Generation (RAG) starts by obtaining smaller, highly relevant data segments to address a query. Next, use their corresponding parent identifiers to access and retrieve the larger parent data chunk, which will serve as context for the LLM (Large Language Model).
      ![image](https://github.com/user-attachments/assets/0acd9150-1e66-4a45-8a82-ac704053f884)

    **9. RAG_Sentence_Window_Retrievall.ipynb** - Senetence Window Retriever
    -  This notebook applies the hybrid search technique (Vector + Sparse(bm42)) to the *Fastembed Model* embedded data stored in the Qdrant database, specifically within the collection named **RAGSentenceWindowCollection**. The SentenceWindowNodeParser is a specialized tool, crafted to parse documents into individual sentences while maintaining a contextual window around each one. It works by dividing documents into sentences and attaching a customizable number of neighboring sentences as metadata. This "window" of additional context supports tasks requiring a deeper, nuanced understanding of the text.
      ![image](https://github.com/user-attachments/assets/1b94aadb-5c7e-4f5f-b07d-c9ef9f662517)

## Comparison Analysis of RAG Search Techniques
This report provides a comparative analysis of nine Retrieval-Augmented Generation (RAG) search techniques, focusing on their average latency and response times across multiple questions submitted to the LLM. Each technique was assessed by averaging the latencies for three main stages—Context Retrieval, Re-ranking, and Generation—and then computing the total response time. Please note that this analysis is based on CPU execution, and the specific LLM and embedding models used influence response and latency times, which may vary accordingly.

|Sr. No. |RAG Retrieval Methods|Context Latency (secs)|Re-Ranking Latency (secs)|Generation Latency (secs)|Overall Response Time (secs)|
|--------|---------------------|----------------------|-------------------------|-------------------------|----------------------------|
|1	 |Dense Search Fast Embed Model|0.03|0.83|3.40|6.09|
|2	 |Dense Search Hugging Face Embed Model|0.1|0.86|0.65|5.11|
|3	 |Sparse Search Fast Embed Model|0.03|0.30|2.82|4.1|
|4	 |Hybrid (Dense and Sparse) Search|0.12|1.33|1.21|5.23|
|5	 |Hybrid + Mannual HyDE (Hypothetical Document Embedding)|0.11|1.34|2.3|6.5|
|6       |Dense + Predefined HyDE (Hypothetical Document Embedding)|1.53|0.88|3.7|9.4|
|7	 |Hybrid + Hierarchical Indexing|0.3|0.23|0.28|3.28|
|8	 |Hybrid + Parent Document Retriever|0.37|0.18|1.8|4.4|
|9	 |Hybrid + Sentence Window Retrieval|0.14|0.33|1.45|4|

**Key Observations:**
1. Lowest Overall Response Time: The Hybrid + Hierarchical Indexing method had the lowest response time (3.28 seconds) with efficient latency across all stages, particularly in the Generation phase, making it well-suited for applications needing rapid responses.

2. Fast Re-Ranking: Methods employing sparse or hybrid retrieval—such as Hybrid + Parent Document Retriever and Hybrid + Sentence Window Retrieval—demonstrated lower re-ranking latency, contributing to faster processing times.

3. Higher Generation Latency: Dense + Predefined HyDE and Hybrid + Mannual HyDE methods exhibited elevated generation latencies, resulting in longer overall response times (9.4 and 6.5 seconds, respectively). These methods might be preferable when complex document structure and enhanced context precision are a priority over response speed.

4. Balanced Response and Latency: Dense Search Hugging Face Embed Model and Hybrid (Dense and Sparse) Search offered a balanced approach, with moderate overall response times (5.11 and 5.23 seconds). They achieved reasonable latency across context, re-ranking, and generation, making them suitable for tasks requiring a trade-off between speed and accuracy.

5. Low Generation Latency: Techniques using hierarchical indexing or smaller, dense embeddings, like Hybrid + Hierarchical Indexing and Sparse Search Fast Embed Model, showed reduced generation latency, improving speed without compromising quality. 

**Conclusion:**<br>
Each RAG retrieval method exhibits unique strengths across different latency stages, indicating potential use-case-specific applicability. Hybrid + Hierarchical Indexing is optimal for scenarios requiring minimal response time, while Hybrid approaches and Dense + Predefined HyDE may be better suited for handling complex document embedding or enhanced context precision.
This analysis underscores that these response and latency metrics are also influenced by the specific LLM and embedding models used, as well as the execution environment (e.g., GPU or TPU), allowing for flexibility in achieving optimized outcomes based on system architecture and application needs. Additionally, if the LLM stalls during processing and generation, response times can increase significantly, taking up to approximately 40 seconds to produce a final answer, as indicated by CPU analysis and testing.

## References:
- This project leverages a variety of Retrieval-Augmented Generation (RAG) techniques for comprehensive performance analysis. For <br> foundational guidance, the implementation of these techniques primarily references the Medium article [Hybrid RAG using Qdrant, BM42, LlamaIndex, and MistralAI](https://medium.com/@pavannagula76/hybrid-rag-using-qdrant-bm42-llamaindex-and-mistralai-5d0d51093e8f). <br> Building on these concepts, additional RAG search techniques with varied mechanisms were implemented to expand the scope of retrieval strategies and response comparison.<br>

- [Hierarchical Indexing RAG](https://arxiv.org/html/2403.00435v1)<br>
- [HyDE - Hypothetical Document Embedding RAG](https://arxiv.org/pdf/2212.10496)<br>
- [HyDE - Predefined HDE Function](https://medium.aiplanet.com/advanced-rag-improving-retrieval-using-hypothetical-document-embeddings-hyde-1421a8ec075a)
- [Advanced RAG — Improving retrieval using Hypothetical Document Embeddings(HyDE)](https://medium.aiplanet.com/advanced-rag-improving-retrieval-using-hypothetical-document-embeddings-hyde-1421a8ec075a)<br>
- [Advanced RAG 01: Small-to-Big Retrieval - Child-Parent RecursiveRetriever and Sentence Window Retrieval with LlamaIndex](https://towardsdatascience.com/advanced-rag-01-small-to-big-retrieval-172181b396d4)<br>
- [Sentence Window Retrieval](https://dev.to/rutamstwt/sentence-window-retrieval-optimizing-llm-performance-ie7)<br>
- [qdrant vector database documentation](https://qdrant.tech/documentation/)<br>
- [qdrant Tutorial](https://qdrant.tech/documentation/tutorials/)<br>
- [Install Docker Desktop on Windows](https://docs.docker.com/desktop/install/windows-install/)<br>
- [Efficient Information Retrieval with RAG Workflow](https://medium.com/@akriti.upadhyay/efficient-information-retrieval-with-rag-workflow-afdfc2619171)<br>
- [Retrieval Strategies](https://chatgen.ai/blog/the-ultimate-guide-on-retrieval-strategies-rag-part-4/)<br>
- [Advanced RAG Techniques](https://www.falkordb.com/blog/advanced-rag/)<br>

## Acknowledgments
A heartfelt thanks to all the open-source communities, authors, and researchers whose resources and insights made this project possible. Special appreciation to the creators of the tools, libraries, and articles referenced here. This project stands on the collective knowledge from multiple sources, and I am grateful for the documentation support and inspiration that enabled me to take on this initiative.

## Future Enhancements
*Exciting new implementations and enhancements are in progress! Upcoming updates will introduce additional topics such as LLM evaluation, context and answer relevancy analysis, and advanced techniques, along with more resources, performance optimizations, and expanded RAG search capabilities. Stay tuned for future improvements and project expansions!*
