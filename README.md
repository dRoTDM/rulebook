RAG System for Question Answering on the Cricket Rulebook

This project builds a small Retrieval-Augmented Generation (RAG) system to answer questions about the official cricket rulebook. The goal is to test how different language models behave when they rely on retrieved context from a long, technical document. We evaluate three models: Llama 3.2, Phi-3, and Mistral.

Project Overview

The cricket rulebook contains dense rules, exceptions, and detailed clauses. Standard LLMs often struggle with direct question answering on such documents.
To address this, we use a RAG pipeline that:

Splits the rulebook into small chunks

Converts each chunk into embeddings

Stores them in a vector database

Retrieves the top-k relevant chunks

Passes them to an LLM through a controlled prompt

Generates a grounded answer

We compare the accuracy and faithfulness of each model on a set of domain-specific questions.

Key Features

Simple RAG pipeline built with LangChain

Three LLM backends tested under the same setup

Custom evaluation metrics (accuracy vs. gold answer, faithfulness to retrieved context)

Plots and charts to visualize model performance

Reproducible notebook for end-to-end experimentation

Repository Structure
📁 project/
│── 📄 NLP_Project.ipynb        # Main Jupyter notebook
│── 📄 rulebook.pdf             # Source document
│── 📄 questions.json           # Domain-specific questions
│── 📄 gold_answers.json        # Reference answers
│── 📁 outputs/                 # Generated plots and logs
│── 📄 README.md                # This file

Models Evaluated

Llama 3.2

Phi-3

Mistral

Each model is tested with the same chunking, prompt template, and retrieval settings.

Evaluation Metrics

Accuracy: similarity to gold answer

Faithfulness: similarity to retrieved context

Hallucination detection: checking unsupported claims

Law/section correctness: whether the answer references the right rule

Results Summary

Mistral gives the most accurate answers overall.

Phi-3 is the most faithful to the retrieved text.

Llama 3.2 has more fluctuations and depends heavily on retrieval quality.

All models benefit from the RAG setup and show reduced hallucination when grounded in retrieved rules.

How to Run

Open the Jupyter notebook:

jupyter notebook Cricketrulebook.ipynb


Install dependencies inside the notebook:

!pip install langchain langchain-community sentence-transformers faiss-cpu


Run cells in order from top to bottom.

Make sure you have API keys set for the models you use.

Limitations

Small set of questions

Simple retrieval (similarity search only)

One document domain

No expert evaluation

Only three models tested
