# VT-NLP: Extracting and Querying Complex Tables from PDF Using PhoBERT

## 1. Introduction

This project focuses on extracting complex tabular data from PDF documents and transforming it into structured, machine-readable data.
---

## 2. System Overview

The system consists of four main stages:

1. **PDF Preprocessing and Table Detection**
   The input PDF files are processed to detect and locate table regions. These tables may contain complex structures, such as merged cells, multi-line text, or irregular alignment.

2. **Data Extraction and Structuring**
   The detected tables are extracted and converted into a structured format such as CSV, JSON, or a database table. Noise is removed, and the data is normalized to ensure consistency.

3. **Semantic Processing with PhoBERT**
   PhoBERT is used to:

   * Understand the semantic meaning of questions
   * Encode textual content into vector embeddings
   * Support context-aware interpretation of multiple-choice questions

4. **Question Answering Module**
   The system allows users to input multiple-choice questions. Based on semantic similarity and structured data lookups, it determines the correct answer(s), including cases where more than one option is valid.

---

## 3. NLP Model: PhoBERT

PhoBERT is a state-of-the-art pre-trained language model for Vietnamese. In this project, PhoBERT is used for:

* Sentence and document embedding generation
* Semantic similarity measurement
* Contextual understanding of Vietnamese text
* Improving the accuracy of matching between questions and extracted content

Compared to traditional keyword-based methods, PhoBERT significantly enhances semantic understanding capabilities.

---

## 4. Role of `nv1.ipynb` and `nv2.ipynb`

The project includes two main Jupyter Notebooks responsible for the vectorization and matching processes:

### 4.1 `nv1.ipynb` – Document Encoding

This notebook is used to **encode each document (or extracted text segment) in the training input into vector representations** using PhoBERT.

Main functions:

* Load structured text extracted from PDF tables
* Preprocess and clean textual data
* Use PhoBERT to convert each document into a high-dimensional vector
* Store the resulting vectors in a local file or database for later retrieval

These vectors represent the semantic meaning of the original documents and serve as the reference embedding set.

---

### 4.2 `nv2.ipynb` – Question Encoding and Matching

This notebook is responsible for **encoding user questions and matching them with the most relevant document vectors generated in `nv1.ipynb`**.

Main functions:

* Take input questions (multiple-choice format)
* Encode each question into a vector using the same PhoBERT model
* Compute similarity (e.g., cosine similarity) between the question vector and the stored document vectors
* Identify the closest vectors (most semantically relevant documents)
* Select the correct answer(s) based on similarity ranking and content analysis




