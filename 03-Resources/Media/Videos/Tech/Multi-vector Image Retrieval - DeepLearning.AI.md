---
title: Multi-vector Image Retrieval - DeepLearning.AI
source: https://learn.deeplearning.ai/courses/multi-vector-image-retrieval/lesson/opbx8g/introduction
author:
  - "[[DeepLearning.AI - Learning Platform]]"
published: 2025-12-10
created: 2026-01-06
description: Build advanced retrieval systems that represent images with multiple vectors, enabling fine-grained matching between text queries and visual content for accurate multi-modal search.
tags:
  - AI
  - LLM
  - Multi-vector
cssclasses:
  - daily
  - tuesday
---
[![DeepLearning.AI](https://learn.deeplearning.ai/_next/image?url=%2Fassets%2Fdlai-logo.png&w=384&q=75)](https://learn.deeplearning.ai/)
# Multi-Vector Text Retrieval: ColBERT
## Single Vector Text Retrieval
### Bi-encoder
![[Pasted image 20260106155053.png]]
- Problems: 
	- Compressed the documents down to a single vector
### Cross-encoder
![[Pasted image 20260106155309.png]]
- Problem:
	- Computational Expensive
	- Feasible when searching for small batches
		- Can be used to choose the top 5 in the top 50 after the Bi-Encoder
## ColBERT: Multi-Vector 
### Representation
![[Pasted image 20260106155553.png]]
>[!importatnt]-
>A bi-encoder would pool all these vectors by averaging into one vector -> represent the document, but ==ColBERT keep the vectors for every token==.
- The same goes for ==query== representation.
### MaxSim: Cross-Token Similarity ^maxsim-similarity
![[Pasted image 20260106160119.png]]
- Properties:
	- Is asymetrics
		- (B, A) != (A, B)
- Cannot use HNSW