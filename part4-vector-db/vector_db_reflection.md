# Vector Database Reflection

## Vector DB Use Case

**Question:** A law firm wants to build a system where lawyers can search 500-page contracts by asking questions in plain English (e.g., "What are the termination clauses?"). Would a traditional keyword-based database search suffice? Justify why or why not, and explain what role a vector database would play in this system.

**Answer:**

A traditional keyword-based search would **not** be enough for this system. Keyword searches only look for exact word matches. If a lawyer searches for the word "termination," but the contract uses a different phrase like "ending the agreement" or "closing the contract," a keyword search will fail to find those sections. In legal documents, the same idea is often written using many different words, making simple word-matching unreliable.

This is where a **vector database** becomes very helpful. Instead of just looking at the letters in a word, a vector database understands the **meaning** of the sentence. It turns the text of the 500-page contract into mathematical numbers called "embeddings." These numbers represent the actual concepts within the text.

In this system, the vector database acts as an intelligent filing cabinet. When a lawyer asks a question, the database finds the parts of the contract that have the most similar "meaning" to that question, even if the exact words are different. It then provides these relevant sections to an AI (like a Large Language Model) to generate a helpful answer. This process ensures that lawyers get accurate information quickly without having to guess which specific legal keywords were used in the original document.