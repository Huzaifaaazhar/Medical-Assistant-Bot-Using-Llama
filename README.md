# Medical Assistant - AI-Powered Medical Chatbot

This project is an AI-powered medical assistant that uses the LLaMA model and Pinecone for real-time, context-driven medical queries. The application allows users to interact with a chatbot interface to get AI-based medical advice from a PDF medical book, providing accurate and relevant information using machine learning embeddings and vector search.

---

## Project Structure

```plaintext
Medical-Assistant/
├── data/
│   └── Medical_book.pdf                # Medical knowledge source in PDF format
├── env/                                # Virtual environment directory (not included in Git)
├── model/
│   ├── instruction.txt                 # Model usage instructions
│   └── llama-2-7b-chat.ggmlv3.q4_0.bin # Pre-trained LLaMA model used for generating responses
├── research/
│   └── experiment.ipynb                # Notebook for experimenting with embeddings and queries
├── src/
│   ├── __pycache__/                    # Compiled Python cache files
│   ├── __init__.py                     # Initialization file for src package
│   ├── helper.py                       # Helper functions for loading PDFs, splitting text, and downloading embeddings
│   └── prompt.py                       # Prompt template for guiding the LLaMA model
├── static/
│   ├── style.css                       # Styles for the chat interface
│   └── .gitkeep                        # Placeholder file to keep the folder tracked in Git
├── templates/
│   └── chat.html                       # HTML template for the chatbot interface
├── .env                                # Environment variables (API keys for Pinecone)
├── app.py                              # Main Flask application file
├── requirements.txt                    # List of Python dependencies
├── setup.py                            # Setup file for initializing the application
└── store_index.py                      # Script for creating and storing the index in Pinecone
```

---

## Features

- **LLaMA Model**: The project uses a pre-trained LLaMA model for generating AI responses.
- **Pinecone Vector Search**: The project uses Pinecone to create a vector index from the medical book and search for relevant answers.
- **Flask Web Application**: A simple web interface is built using Flask where users can interact with the medical chatbot.
- **PDF Knowledge Base**: Medical knowledge is extracted from a PDF file that contains essential information.
- **Real-Time Interaction**: Users can submit queries through a web interface, and the AI will respond based on the data from the medical book.
- **Embeddings and Text Splitting**: The PDF text is split into smaller chunks and transformed into vector embeddings using Hugging Face models.

---

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/Medical-Assistant.git
cd Medical-Assistant
```

### 2. Create and Activate a Virtual Environment

```bash
python -m venv env
source env/bin/activate       # On Windows: .\env\Scripts\activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Set Up Environment Variables

Create a `.env` file in the project root directory and add your **Pinecone API Key** and **Environment**:

```
PINECONE_API_KEY=your_pinecone_api_key
PINECONE_API_ENV=your_pinecone_environment
```

### 5. Download the Model

Place the LLaMA model file (`llama-2-7b-chat.ggmlv3.q4_0.bin`) in the `model/` directory. 

> **Note**: Ensure that you have the appropriate licensing and permissions for using the model.

### 6. Run the Application

To start the Flask application, run:

```bash
python app.py
```

The application will be available at `http://0.0.0.0:8080`.

---

## Usage

1. **Load Medical Knowledge**: The PDF file located in the `data/` folder is used to load medical knowledge. The `helper.py` script extracts text from the PDF and splits it into chunks.

2. **Embedding**: The project uses Hugging Face embeddings (`sentence-transformers/all-MiniLM-L6-v2`) to convert text into vector space for querying.

3. **Chatbot Interface**: Navigate to the `/` route in your browser (`http://localhost:8080`) to interact with the chatbot. Type in medical queries, and the bot will respond with relevant information extracted from the medical book.

---

## File Descriptions

- **`app.py`**: Main entry point for the Flask application. Handles the chatbot UI and the query processing pipeline.
- **`src/helper.py`**: Contains helper functions for loading and processing the PDF data and downloading the embeddings.
- **`src/prompt.py`**: Defines the prompt template used to guide the LLaMA model for generating responses.
- **`store_index.py`**: A script used to create and save the Pinecone index from the medical book PDF.
- **`requirements.txt`**: Lists all the dependencies required to run the project.
- **`templates/chat.html`**: Front-end interface for interacting with the chatbot.
- **`static/style.css`**: Styles for the chatbot interface.
- **`setup.py`**: A script that can be used for initializing and configuring the project.

---

## Pinecone Indexing

The application uses Pinecone to manage and search through vectorized representations of the PDF. The index is built using the following steps:

1. Load the medical knowledge from the PDF using `PyPDFLoader`.
2. Split the loaded text into chunks using `RecursiveCharacterTextSplitter`.
3. Convert the chunks into vector embeddings using Hugging Face models.
4. Store the vector embeddings into a Pinecone index for fast search and retrieval.

---

## Model

The project uses a pre-trained **LLaMA model** (LLaMA 2, 7B) for generating responses. The model is loaded from the `model/` directory and used in conjunction with Pinecone to provide relevant, AI-generated answers to user queries.

---

## How to Contribute

1. Fork the repository.
2. Create a new branch for your feature or bug fix.
3. Commit your changes and push them to your fork.
4. Submit a pull request to the `main` branch of this repository.

---

## Acknowledgments

- The **LLaMA model** and **Hugging Face embeddings** are the core technologies used in this project.
- **Pinecone** is used for efficient vector search.
- Special thanks to the **LangChain** community for providing the document loading and processing tools.
