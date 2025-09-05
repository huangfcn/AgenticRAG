# AgenticRAG: Deep Research Framework with Agentic RAG

AgenticRAG implements a powerful **Deep Research Framework** that combines intelligent query planning with reliable Retrieval-Augmented Generation (RAG) for comprehensive question answering. The system takes complex queries and automatically breaks them down into multiple focused sub-queries, processes each through the full Agentic RAG pipeline, and synthesizes all findings into comprehensive reports.

## Deep Research Framework (Main System)

The core innovation is a deep research framework that orchestrates comprehensive analysis:

```
Deep Research Framework with AgenticRAG
│
├── Search Planner (generate multiple focused queries)
│
├── For each query:
│   ├── AgenticRAG Processing
│   │   ├── Query Routing
│   │   ├── RAG Pipeline (with all reliability features)
│   │   │   ├── Document Retrieval
│   │   │   ├── Document Grading
│   │   │   ├── Query Rewriting (if needed)
│   │   │   └── Web Search Fallback
│   │   └── Answer Generation
│   └── Store individual answer
│
└── Final Report Generator (aggregate all answers)
```

### How It Works

1. **Intelligent Query Planning**: Automatically generates 3-5 diverse, focused search queries from complex topics
2. **Reliable Processing**: Each sub-query is processed through the full Agentic RAG pipeline with all reliability features
3. **Comprehensive Synthesis**: Results are aggregated into a well-structured, comprehensive report

### Example Workflow

For a query like "What are the latest advancements in quantum computing?":

1. **Query Planning**: Generates focused sub-queries:
   - "Recent breakthroughs in quantum hardware and qubit stability"
   - "Latest quantum algorithms for optimization and machine learning"
   - "Current industry applications of quantum computing"

2. **Agentic RAG Processing**: Each sub-query is processed with:
   - Intelligent routing (direct response, RAG, or web search)
   - Document retrieval and relevance grading
   - Query rewriting when needed (up to 3 retries)
   - Web search fallback for time-sensitive information

3. **Report Generation**: Synthesizes all findings into a comprehensive report

## System Architecture

The Agentic RAG system follows a modular architecture with the following components:

![Agentic RAG Architecture](resources/agenticrag_1.png)

## Prerequisites

- Python 3.8+
- Jupyter Notebook or JupyterLab
- Ollama with Qwen model (qwen3:8b)
- Serper API key for web search functionality

## Installation

1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd AgenticRAG
   ```

2. Install required dependencies:
   ```bash
   pip install langchain langchain-community langchain-huggingface langgraph faiss-cpu requests
   ```

3. Install Ollama and pull the Qwen model:
   ```bash
   # Install Ollama from https://ollama.com/
   ollama pull qwen3:8b
   ```

4. Set up your Serper API key:
   ```bash
   export SERPER_API_KEY=your_serper_api_key_here
   ```

## Usage

### Main Deep Research System

Open and run `notebooks/DeepResearch_with_AgenticRAG.ipynb`:

1. The system takes complex queries and automatically breaks them down into multiple focused sub-queries
2. Each sub-query is processed through the full Agentic RAG pipeline with all reliability features
3. Results are synthesized into a comprehensive report

Example complex query: "What are the latest advancements in quantum computing?"

The system will:
1. Generate focused sub-queries on different aspects
2. Process each through the reliable Agentic RAG system
3. Create a comprehensive report synthesizing all findings

## Core Agentic RAG Features (Component)

The Agentic RAG system that powers each query processing includes:

### Multi-Approach RAG Implementation

1. **Adaptive RAG**: Intelligently routes queries to the most appropriate processing path
2. **Corrective RAG**: Uses web search as a fallback when internal knowledge is insufficient
3. **Self-RAG**: Implements self-correction mechanisms to reduce hallucinations

### Intelligent Query Routing

Routes queries to one of three processing paths:
- **Direct Response**: For simple greetings or general knowledge questions
- **Vectorstore RAG**: For domain-specific questions with document relevance grading
- **Web Search**: As a fallback when internal RAG fails

### Advanced RAG Workflow

- Document relevance grading to ensure quality responses
- Query rewriting mechanism for improved retrieval on failed attempts
- Automatic fallback to web search after maximum RAG retries
- Stateful agent behavior with conversation history tracking

## Customization

### Knowledge Base Management

The notebooks include code to rebuild the FAISS vector database from source documents. You can customize the knowledge base by:

1. Modifying the source URLs in the database creation section
2. Adjusting chunk size and overlap parameters
3. Changing the embedding model

### Model Configuration

You can customize the LLM by modifying the `ChatOpenAI` configuration:
- Change the model name
- Adjust temperature for creativity vs. consistency
- Modify other model parameters

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

- This implementation is based on concepts from the LangChain documentation and tutorials
- The knowledge base is built from Lilian Weng's blog posts on LLM topics
- Uses FAISS for efficient vector similarity search
- Integrates with Serper API for web search capabilities