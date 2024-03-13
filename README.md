# Index Private PDFs for RAG and create Fine-Tuning Datasets from them

This project will take a google drive folder of PDF files that you provide and read them, index them in vector embeddings in Hopsworks for retrieval augmented generation (RAG) and create an instruction dataset for fine-tuning using a teacher model (GPT).


!(Hopsworks Architecture for Private PDFs Indexed for LLMs)[./private-pdfs-llm-hopsworks.png]

## Feature Pipeline
The Feature Pipeline does the following:

 * Download any new PDFs from the google drive
 * Extract chunks of text from the PDFs and store them in a Feature Group in Hopsworks
 * Use GPT to generate an instruction set for the fine-tuning  a foundation LLM and store as a feature group in Hopsworks

## Training Pipeline
The Training Pipeline does the following:

 * Uses the instruction dataset and LoRA to fine-tune the open-source LLM (Mistral-7 by default) 
 * Saves the fine-tuned model to Hopsworks Model Registry

## Inference Pipeline
* A chatbot written in Streamlit that answers questions about the PDFs you uploaded using RAG and an embedded LLM 
