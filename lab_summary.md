## Objective

The objective of this lab was to compare different text chunking strategies for Retrieval-Augmented Generation (RAG) systems. Three chunking approaches were tested: fixed-size chunking, recursive character chunking, and token-based chunking. The strategies were evaluated using both a structured PDF document and a conversational podcast transcript to determine how effectively each method preserved context, structure, and semantic meaning.

## Dataset

Two different data sources were used in this lab:

1. **Ethics Guidelines for Trustworthy AI (PDF)**, a structured document published by the European Commission's High-Level Expert Group on Artificial Intelligence. The extracted text contained approximately 158,079 characters and 24,153 words.

2. **The Blueprint for Trustworthy AI (Podcast & Podcast Transcript)**, a conversational transcript discussing the same subject matter. The transcript contained approximately 18,622 characters and 3,075 words.

Using both a formal document and a conversational transcript allowed the chunking strategies to be evaluated across different types of content structures.

## Methods Tested

Three chunking strategies were evaluated using the LangChain text splitter library:

1. **CharacterTextSplitter (Fixed-Size Chunking)**
   - Chunk size: 1000 characters
   - Chunk overlap: 100 characters
   - Splits text at fixed character intervals.

2. **RecursiveCharacterTextSplitter**
   - Chunk size: 1000 characters
   - Chunk overlap: 200 characters
   - Attempts to preserve semantic structure by splitting on paragraphs, line breaks, sentences, and words before resorting to character-level splitting.

3. **TokenTextSplitter**
   - Chunk size: 250 tokens
   - Chunk overlap: 50 tokens
   - Splits text according to token count, making it more suitable for managing LLM context windows.

   ## Key Findings

- Fixed-size chunking was the simplest method to implement but often split content at arbitrary points, reducing coherence.

- Recursive chunking generally preserved document structure and semantic meaning more effectively, particularly when working with the PDF document.

- Token-based chunking produced predictable chunk sizes that are useful for managing LLM context windows, but it did not consistently preserve structure or conversational flow.

- The PDF showed greater differences between chunking strategies because of its formal structure, headings, and sections.

- The podcast transcript was less sensitive to chunking strategy because the timestamped conversational format already provided natural break points.

## Conclusion

This lab demonstrated that different chunking strategies have different strengths and weaknesses depending on the type of content being processed. Fixed-size chunking was simple and predictable but often disrupted context. Recursive chunking provided the best balance between chunk size and semantic coherence, particularly for structured documents. Token-based chunking was useful for controlling LLM input size but was less effective at preserving meaning and structure.

Overall, RecursiveCharacterTextSplitter was the most effective strategy for the PDF document, while conversational transcripts benefited from larger chunks and careful handling of conversational context.