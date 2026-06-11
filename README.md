# Chunking Strategies for RAG Systems

## Overview

This lab explores different text chunking strategies commonly used in Retrieval-Augmented Generation (RAG) systems. The goal was to compare how different chunking methods preserve context, structure, and semantic meaning when applied to different types of content.

## Datasets

Two datasets were used:

1. **Ethics Guidelines for Trustworthy AI (PDF)**

   * Approximately 158,079 characters
   * Approximately 24,153 words

2. **The Blueprint for Trustworthy AI (Podcast Transcript)**

   * Approximately 18,622 characters
   * Approximately 3,075 words

## Chunking Methods Tested

### 1. Fixed-Size Chunking

Implemented using `CharacterTextSplitter`.

* Chunk size: 1000 characters
* Overlap: 100 characters

### 2. Recursive Character Chunking

Implemented using `RecursiveCharacterTextSplitter`.

* Chunk size: 1000 characters
* Overlap: 200 characters

### 3. Token-Based Chunking

Implemented using `TokenTextSplitter`.

* Chunk size: 250 tokens
* Overlap: 50 tokens

## Key Findings

* Fixed-size chunking was simple to implement but often split content at arbitrary boundaries.
* Recursive chunking preserved document structure and semantic meaning more effectively, particularly for the PDF document.
* Token-based chunking produced predictable chunk sizes suitable for LLM context windows but did not consistently preserve structure.
* Structured documents benefited more from recursive chunking than conversational transcripts.
* Transcript chunking was less sensitive to strategy because timestamped dialogue naturally created break points.

## Conclusion

Recursive chunking provided the best balance between context preservation and chunk consistency across the datasets tested. While token-based chunking remains valuable for managing LLM context limits, recursive chunking was generally the most effective approach for maintaining semantic coherence.

## Technologies Used

* Python
* Jupyter Notebook
* LangChain
* PyPDF2
* Git
* GitHub

## Repository Structure

```text
LAB_Chunking_Strategies/
├── data/
├── chunkingg_strategies.ipynb
├── README.md
├── lab_summary.md
└── .gitignore
```
