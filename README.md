# Bangla RAG Project with ChromaDB and Custom Embeddings

A multilingual Retrieval-Augmented Generation (RAG) system designed to handle Bengali product queries using advanced embedding models and semantic search capabilities.

## Project Overview

This project implements a sophisticated RAG system that can process queries in Bengali (Bangla) and English, providing accurate product recommendations and information retrieval. The system uses ChromaDB as the vector database with Alibaba's multilingual embedding model for enhanced semantic understanding across languages.

## Architecture

### Core Components

1. **Custom Embedding Function**: Utilizes Alibaba-NLP's `gte-multilingual-base` model for generating high-quality embeddings that work effectively across Bengali and English languages.

2. **ChromaDB Vector Database**: Persistent vector storage with custom embedding integration for efficient similarity search and document retrieval.

3. **Multi-Strategy Search Engine**: Implements multiple search approaches:
   - Semantic search using embeddings
   - Intent-based filtering with category metadata
   - Keyword extraction and matching
   - Cross-lingual query processing

4. **Language Processing Pipeline**: 
   - Automatic language detection
   - Bengali to English translation using LLM
   - Intent extraction and classification
   - Keyword extraction using YAKE algorithm

5. **Large Language Model Integration**: Uses Groq's LLaMA-4 Scout model for translation, intent analysis, and response generation.

### Technical Stack

- **Embedding Model**: Alibaba-NLP/gte-multilingual-base (768-dimensional)
- **Vector Database**: ChromaDB with persistent storage
- **LLM Provider**: Groq (meta-llama/llama-4-scout-17b-16e-instruct)
- **Text Processing**: NLTK, YAKE keyword extraction
- **Language Support**: Bengali (primary), English
- **Development Environment**: Google Colab compatible

## Key Features

- **Multilingual Support**: Native Bengali query processing with English fallback
- **Intent Classification**: Automatic categorization of user queries into product categories
- **Multi-Modal Search**: Combines semantic, keyword, and intent-based search strategies
- **Custom Embeddings**: Leverages state-of-the-art multilingual embedding models
- **Persistent Storage**: ChromaDB ensures data persistence across sessions
- **Interactive Interface**: Command-line interface with real-time query processing

## Data Structure

The system processes structured product data with the following categories:
- Baby Products
- Electronics & Technology
- Home & Kitchen Appliances
- Fashion & Clothing
- Beauty & Personal Care
- Sports & Fitness
- Books & Education
- Food & Beverages
- Automotive & Tools
- Health & Wellness
- Pet Supplies
- Garden & Outdoor
- Office & Stationery

## How to Run

### Prerequisites

1. Python 3.7+ environment
2. Required packages (automatically installed):
   ```
   python-dotenv
   yake
   langchain-groq
   chromadb
   langdetect
   nltk
   sentence-transformers
   torch
   ```

### Setup Steps

1. **Environment Configuration**:
   - Create a `.env` file with your `GROQ_API_KEY`
   - Prepare your product data in `.txt` format

2. **File Upload** (for Google Colab):
   - Upload your `.env` file
   - Upload your product data file (`products.txt`)

3. **System Initialization**:
   - Run the notebook cells sequentially
   - The system will automatically download and initialize the embedding model
   - ChromaDB will be set up with persistent storage

4. **Data Loading**:
   - Product data is parsed and indexed automatically
   - Embeddings are generated using the custom Alibaba model
   - Vector database is populated with product information

5. **Interactive Usage**:
   - Enter Bengali queries in the command prompt
   - Use special commands:
     - `quit` - Exit the system
     - `toggle` - Switch NLP translation mode
   - Receive responses in Bengali with relevant product information

### Example Usage

```
Bengali Query: "pet supplier ki ki ache?"
System Response: Relevant pet products with details and pricing

Bengali Query: "10000tk er moddhe valo ki mobile ache?"
System Response: Available mobile phones with specifications
```

## Search Strategy

The system employs a four-pronged search approach:

1. **English Semantic Search**: Translated query processed through embeddings
2. **Intent-Based Search**: Category-filtered search using extracted intent
3. **Keyword Search**: Both Bengali and English keyword matching
4. **Direct Bengali Search**: Native Bengali query processing

Results are combined and deduplicated to provide comprehensive responses.

## Configuration Options

- **NLP Translation**: Can be toggled on/off during runtime
- **Search Parameters**: Configurable top-k results (default: 4-6)
- **Embedding Model**: Supports different multilingual models
- **LLM Temperature**: Adjustable for response creativity (default: 0.0-0.2)

This system provides a robust foundation for multilingual e-commerce search and can be extended to support additional languages and product categories.