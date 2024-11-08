# OnDemand Professor Q&A Bot

This project implements an OnDemand Q&A bot to assist professors in retrieving information from lecture slides and documents. It leverages natural language processing and vector-based document retrieval to respond to questions accurately.

## Requirements

### Environment
- **Operating System**: Windows/Linux/MacOS
- **Python Version**: 3.8 or higher
- **Virtual Environment**: (optional) Recommended to use `venv` or `conda` for managing dependencies.

### Setup
1. Clone this repository:
   ```bash
   git clone <repository-url>
   cd OnDemand-Professor-Q-A-Bot
2. Install required libraries
3. Environment Variables:
  Set up the Hugging Face API token by adding it to the environment variables:
    ```bash
    `export HUGGINGFACEHUB_API_TOKEN='your-huggingface-api-key'`

### Adopted Libraries
The following libraries are used in this project:

**Chainlit**: Provides real-time message handling and interaction.

**LangChain**: Powers LLM-based document retrieval and Q&A functionality.

**Chroma**: Used for vector storage of document embeddings.

**Hugging Face Hub**: For loading transformer models and embeddings.

**PyPDFLoader**: For loading PDF documents from a directory.

### System Architecture
![image](https://github.com/user-attachments/assets/8311c280-2827-415b-98bd-cfc8d39742f9)

## Flow of Execution

### Document Loading
- The `DirectoryLoader` and `PyPDFLoader` modules are used to read and split lecture slides and documents stored in the `Lectures` folder.

### Text Splitting and Embedding
- The text is split into manageable chunks using `RecursiveCharacterTextSplitter`.
- Each chunk is converted into an embedding vector using the Hugging Face `sentence-transformers` model.

### Vector Store and Retrieval
- The `Chroma` library stores the document embeddings, making it possible to retrieve relevant chunks based on a query.

### Question Answering (QA)
- Using the `HuggingFaceHub` for LLM queries, responses to questions are generated by retrieving relevant document chunks and passing them to the model for accurate answers.


## Commands to Run the Code
### Start the Q&A Bot
To start the bot, use the following command:
    
    chainlit run app.py -w

## Issues and Solutions

### Current Issues

#### Redundant or Repetitive Responses
- **Issue**: Responses sometimes contain redundant or repeated text.

#### Duplicate Source Information
- **Issue**: Duplicate source entries appear in the response.

#### Model Response Length
- **Issue**: The `gpt2` model may not always provide the most informative responses due to its smaller size.
- **Solution**: Consider switching to a more QA-optimized model from the Hugging Face Hub.

> **Note**: We were unable to use more advanced models like GPT-3.5 Turbo or DALL-E 3 as they are not freely available. Opting for these models could improve the accuracy and quality of responses in future versions if budget permits.

## Suggestions and Feedback

- **Use of GPT-3 Model**: For more complex queries, a larger model may improve response accuracy.
- **Enhanced Error Logging**: Consider adding more detailed logging for error handling to aid debugging.
- **Future Enhancements**: Incorporating more advanced document loaders (e.g., DOCX, HTML) could improve versatility.
