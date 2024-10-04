# ProfSync-DataLoader

This Python script sets up a Retrieval-Augmented Generation (RAG) system using Google's Generative AI for embedding generation and Pinecone for vector storage and retrieval.

![PineCone Dashboard](./assets/Pinecone%20Dashboard.png)
## Features

- Connects to Google's Generative AI (Gemini) API
- Sets up a Pinecone vector database
- Processes review data and generates embeddings
- Uploads embeddings to Pinecone for efficient similarity search

## Prerequisites

Before you begin, ensure you have the following:

- Python 3.7 or higher
- A Google API key for accessing Generative AI services
- A Pinecone API key
- AWS account (for Pinecone serverless)


## Installation

1. Clone the repository:
   ```
   git clone [repository-url]
   ```

2. Navigate to the project directory:
   ```
   cd rag-professor-database
   ```

3. Install the required packages:
   ```
   pip install python-dotenv google-generativeai pinecone-client
   ```

4. Create a `.env` file in the root directory and add your API keys:
   ```
   GOOGLE_API_KEY=your_google_api_key_here
   PINECONE_API_KEY=your_pinecone_api_key_here
   ```

## Usage

1. Prepare your review data:
   - Ensure you have a `reviews.json` file in the project directory with the following structure:
     ```json
     {
       "reviews": [
         {
           "professor": "Professor Name",
           "review": "Review text",
           "subject": "Subject name",
           "stars": 5
         },
         ...
       ]
     }
     ```

2. Run the script:
   ```
   python rag_setup.py
   ```

The script will perform the following actions:
1. Connect to Google's Generative AI API
2. Create a Pinecone index named 'rag'
3. Process the review data and generate embeddings
4. Upload the embeddings to Pinecone

## Script Breakdown

1. **Environment Setup**: The script loads environment variables and imports necessary libraries.

2. **API Connections**: It establishes connections with Google's Generative AI and Pinecone.

3. **Pinecone Index Creation**: A new serverless Pinecone index is created with specific parameters.

4. **Data Processing**: The script reads the `reviews.json` file and processes each review.

5. **Embedding Generation**: For each review, an embedding is generated using Google's text-embedding-004 model.

6. **Data Upload**: The processed data, including embeddings and metadata, is uploaded to the Pinecone index.

7. **Index Statistics**: Finally, it prints the statistics of the Pinecone index.

## Customization

- You can modify the Pinecone index parameters (name, dimension, metric) in the `pc.create_index()` call.
- Adjust the embedding model or parameters in the `genai.embed_content()` function if needed.

## Troubleshooting

- Ensure all API keys are correctly set in the .env file.
- Check that the `reviews.json` file is properly formatted and located in the project directory.

## Other code modules of ProfSync

- Frontend module can be accessed [here](https://github.com/nh0397/ProfSync).
- Backend module can be accessed [here](https://github.com/nh0397/ProfSync-Backend)

## License

This project is licensed under the [Apache License 2.0](LICENSE).

