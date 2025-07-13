# Chatbot
Running on public URL: https://ba15468e047b6de8bb.gradio.live(expires in 1 week)
# Loan Approval RAG Chatbot

## Overview

This project implements a Retrieval-Augmented Generation (RAG) chatbot for loan approval prediction using document retrieval and generative AI. The chatbot answers questions about loan approval criteria by:

1. Retrieving relevant information from a loan approval dataset
2. Generating intelligent responses using a lightweight language model

## Features

- **Document Processing**: Loads and indexes loan approval datasets
- **Retrieval System**: Uses sentence embeddings to find relevant information
- **Generation System**: Leverages Hugging Face's GPT-2 for response generation
- **Interactive Interface**: Includes both command-line and Gradio web interface options

## Dataset

The system uses the Loan Approval Prediction dataset from Kaggle, which includes:
- Training Dataset (614 records)
- Test Dataset
- Sample Submission File

Key features in the dataset:
- Applicant demographics (Gender, Married status, Dependents)
- Financial information (Income, Loan Amount, Credit History)
- Loan characteristics (Amount Term, Property Area)
- Approval status (Loan_Status)

## Technical Implementation

### Core Components

1. **Data Loading**: 
   - Handles file uploads in Colab environment
   - Creates knowledge base from dataset rows
   - Adds general loan approval information

2. **RAG System**:
   - Embedding: `all-MiniLM-L6-v2` from Sentence Transformers
   - Generation: GPT-2 from Hugging Face Transformers
   - Retrieval: Cosine similarity between query and document embeddings

3. **Interfaces**:
   - Command-line Q&A
   - Interactive chat loop
   - Gradio web interface

### Error Handling

Includes robust error handling for:
- File loading issues
- Missing data
- Model generation failures

## Setup Instructions

1. Install required packages:
```bash
pip install pandas numpy sentence-transformers scikit-learn transformers gradio
```

2. Upload dataset files:
   - Training_Dataset.csv
   - Test_Dataset.csv
   - Sample_Submission.csv

3. Run the notebook cells in order

## Usage Examples

```python
# Initialize chatbot
chatbot = RAGLoanApprovalChatbot()

# Ask questions
question = "What factors affect loan approval?"
answer = chatbot.generate_response(question)
```

Sample questions to try:
- "How does income affect approval chances?"
- "What credit history is needed?"
- "Does property area matter for approval?"

## Evaluation

The system includes test cases for:
- Credit score requirements
- Employment status impact
- Maximum loan amounts

## Deployment Options

1. **Local Web Interface** using Gradio:
```python
iface = gr.Interface(fn=chat_interface, 
                   inputs="text", 
                   outputs="text",
                   title="Loan Approval Chatbot")
iface.launch()
```

2. **API Endpoint** using FastAPI (example provided in code)

## Limitations

1. Uses lightweight models which may produce less sophisticated answers than larger LLMs
2. Basic retrieval system without advanced vector database
3. Knowledge base creation is simplistic

## Future Enhancements

1. Add conversation memory for follow-up questions
2. Implement user feedback mechanism
3. Connect to live loan application data
4. Upgrade to more powerful LLMs when available

## Dependencies

- Python 3.7+
- pandas
- numpy
- sentence-transformers
- scikit-learn
- transformers
- gradio (for web interface)

