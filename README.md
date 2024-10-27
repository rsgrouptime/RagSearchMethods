## Project Title
Comparative Analysis of Retrieval-Augmented Generation (RAG) Search Techniques

## Table of Contents
1. Overview
2. Project Structure
3. Installation
4. Usage
5. Features
6. References

## Overview:
This project provides a series of Jupyter notebooks that explore and compare various Retrieval-Augmented Generation (RAG) search techniques. Each notebook evaluates a different RAG method, focusing on key performance metrics like latency and response time, enabling developers and knowledge seekers to gain hands-on experience and insights into these techniques. Together, these notebooks serve as a "cookbook" for those looking to deepen their understanding of RAG search techniques, practice implementing them locally, and enhance their knowledge in search optimization and retrieval-augmented generation.

## Project Structure:
        RagSearchMethods/
            ├── config/             # configuration files
            ├── data/               # Datasets or other input files
            ├── input_pdfs/         # Input Unstructured PDF documents
            ├── src/                # Source code and Jupyter Notebook files (.ipynb)
            ├── README.md           # Project overview and instructions
            ├── requirements.txt    # List of dependencies
            └── .gitignore          # files and directories to ignore when you make a commit

## Installation:

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

4. Usage:
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

5. Features:
    - This is a breakdown of the functionality available in different notebooks. Follow the steps in each notebook sequentially to execute and verify their functionality, as listed below:<br>
        **1. RAG_dense_FastEmbed.ipynb**
        - This notebook applies the dense vector search technique to the *Fastembed Model* embedded data stored in the Qdrant database, specifically within the collection named **RAGdenseCollection**.
        
        **2. RAG_dense_HFEmbed.ipynb**
        - This notebook applies the dense vector search technique to the *Hugging Face Model* embedded data stored in the Qdrant database, specifically within the collection named **RAGdenseHFEmbedCollection**.

        **3. RAG_sparse_FastEmbed.ipynb**
        -  This notebook applies the sparse vector search technique to the *Fastembed Model* embedded data stored in the Qdrant database, specifically within the collection named **RAGSparseCollection**.

        **4. RAG_HybridSearch.ipynb**
        -  This notebook applies the hybrid search technique (Vector + Sparse(bm42)) to the *Fastembed Model* embedded data stored in the Qdrant database, specifically within the collection named **RAGCheckCollection**. Furthermore, it uses the (RRF) Reciprocal Rank Fusion is a rank aggregation method that combines rankings from multiple sources into a single, unified ranking for synthesization.

        **5. RAG_HyDE.ipynb**
        -  This notebook applies the hybrid search technique (Vector + Sparse(bm42)) to the *Fastembed Model* embedded data stored in the Qdrant database, specifically within the collection named **RAGCheckCollection**.It uses the (HyDE) Hypothetical Document Embedder is an embedding technique that takes queries, generates a hypothetical answer, and then embeds that generated document and uses that as to reterive the context from the retriever. Finally, it pass the hypothetical document + context to the LLM for the final answer generation.

        **6. RAG_HierIndexSearch.ipynb**
        -  This notebook applies the hybrid search technique (Vector + Sparse(bm42)) to the *Fastembed Model* embedded data stored in the Qdrant database, specifically within the collection named **RAGHierIndexCollection** for summaries index and **RAGHierIndexCollectionSummary** for detailed chunks. It uses the Hierarchical indexing in Retrieval-Augmented Generation (RAG) works by first create an index for summaries and a second index for document chunks. This strategy enables quick filtering of pertinent documents using summaries, allowing for deeper searches within the chosen documents for the improved comprehension and response generation.

        **SMALL TO BIG RAG SEARCH METHODS:**<br>
        **7. RAG_Parent_Child_Retrieval.ipynb** - Parent Document Retriever
        -  This notebook applies the hybrid search technique (Vector + Sparse(bm42)) to the *Fastembed Model* embedded data stored in the Qdrant database, specifically within the collection named **RAGParentChildCollection**. It uses the Parent Document Retriever in Retrieval-Augmented Generation (RAG) starts by obtaining smaller, highly relevant data segments to address a query. Next, use their corresponding parent identifiers to access and retrieve the larger parent data chunk, which will serve as context for the LLM (Large Language Model).

        **8. RAG_Sentence_Window_Retrievall.ipynb** - Senetence Window Retriever
        -  This notebook applies the hybrid search technique (Vector + Sparse(bm42)) to the *Fastembed Model* embedded data stored in the Qdrant database, specifically within the collection named **RAGSentenceWindowCollection**. The SentenceWindowNodeParser is a specialized tool, crafted to parse documents into individual sentences while maintaining a contextual window around each one. It works by dividing documents into sentences and attaching a customizable number of neighboring sentences as metadata. This "window" of additional context supports tasks requiring a deeper, nuanced understanding of the text.

6. References:

