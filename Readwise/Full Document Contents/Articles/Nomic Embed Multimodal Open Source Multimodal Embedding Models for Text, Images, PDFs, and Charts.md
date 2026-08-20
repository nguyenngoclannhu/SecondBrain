# Nomic Embed Multimodal: Open Source Multimodal Embedding Models for Text, Images, PDFs, and Charts

![rw-book-cover](https://www.nomic.ai/blog/nomic-embed-multimodal.png)

## Metadata
- Author: [[nomic.ai]]
- Full Title: Nomic Embed Multimodal: Open Source Multimodal Embedding Models for Text, Images, PDFs, and Charts
- Category: #articles
- Document Tags: [[ai]] [[inbox]] [[multimodal embeddng]] 
- Summary: Nomic released Embed Multimodal, open-source models that embed text, images, PDFs, and charts. The ColNomic 7B model sets a new state-of-the-art on visual document retrieval benchmarks. These models simplify retrieval by embedding visual and textual content together, improving accuracy and reducing preprocessing.
- URL: https://www.nomic.ai/blog/posts/nomic-embed-multimodal

## Full Document
#### Author: **Nomic Team**

We're excited to announce the release of Nomic Embed Multimodal, a suite of models that achieve state-of-the-art performance in embedding PDFs, images, papers, and charts.

This release includes four models, available in two sizes (3B and 7B parameters) and two variants:

* **ColNomic Embed Multimodal** (3B and 7B): Multi-vector late interaction multimodal embedding models (more powerful)
* **Nomic Embed Multimodal** (3B and 7B): Single-vector multimodal embedding models (faster & use less memory/storage)

Our best model, **ColNomic Embed Multimodal 7B**, achieves 62.7 NDCG@5 on Vidore-v2, a visual document retrieval benchmark focused on page-level retrieval, with a +2.8 point improvement over the previous state-of-the-art models. Additionally, Nomic Embed Multimodal 7B outperforms all other single-vector models on the benchmark.

| Model | Avg. | ESG Restaurant Human | Econ Macro Multi. | AXA Multi. | MIT Bio | ESG Restaurant Synth. | ESG Restaurant Synth. Multi. | MIT Bio Multi. | AXA | Econ. Macro |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| ColNomic Embed Multimodal 7B | 62.7 | 73.9 | 54.7 | 61.3 | 66.1 | 57.3 | 56.7 | 64.2 | 68.3 | 61.6 |
| ColNomic Embed Multimodal 3B | 61.2 | 65.8 | 55.4 | 61.0 | 63.5 | 56.6 | 57.2 | 62.5 | 68.8 | 60.2 |
| Nomic Embed Multimodal 7B | 59.7 | 65.7 | 57.7 | 59.3 | 64.0 | 49.2 | 51.9 | 61.2 | 66.3 | 63.1 |
| Nomic Embed Multimodal 3B | 58.8 | 59.8 | 57.5 | 58.8 | 62.5 | 49.4 | 49.4 | 58.6 | 69.6 | 63.5 |
| Llama Index vdr-2b-multi-v1 | 58.4 | 63.1 | 52.8 | 61.0 | 60.6 | 50.3 | 51.2 | 56.9 | 68.8 | 61.2 |
| Voyage Multimodal 3 | 55.0 | 56.1 | 55.0 | 59.5 | 56.4 | 47.2 | 46.2 | 51.5 | 64.1 | 58.8 |
| Amazon Titan Multimodal | 20.3 | 18.6 | 20.6 | 14.2 | 33.9 | 8.5 | 10.1 | 22.6 | 21.7 | 32.6 |

#### Challenges with PDFs, Papers, and Charts

Documents are visually rich structures that convey information not just through text, but through figures, page layouts, tables, and even fonts. Traditional retrieval systems primarily rely on extracted text, missing these crucial visual elements and often requiring complex, error-prone processing pipelines. Nomic Embed Multimodal, inspired by [ColPali](https://arxiv.org/abs/2407.01449) and [DSE](https://arxiv.org/abs/2406.11251), solves this problem by supporting interleaved text and image inputs, making it ideal for:

* PDF documents and research papers
* Screenshots of applications and websites
* Visually rich content where layout matters
* Multilingual documents where visual context is important

#### VLMs for Multimodal Embeddings

Before multimodal embedding models, representing multimodal data for retrieval required:

* Separate encoders for visual and text inputs
* Complex preprocessing pipelines to extract data from images

In contrast, VLMs provide a simple and accurate way to embed image and text data with a single model, eliminating these complexities while improving performance. This approach delivers superior accuracy compared to text-only approaches that require OCR, while being faster than complex pipelines with multiple processing steps. It also provides more comprehensive capture of visual information by directly processing images alongside related text.

![Multimodal Architecture](https://www.nomic.ai/blog/dse_multimodal.png)Figure 1: Multimodal embedding architecture (courtesy of [DSE](https://arxiv.org/abs/2406.11251))
Both the ColPali and DSE approach significantly outperform multimodal models with CLIP-style architectures by addressing the modality gap through interleaved processing of text and images.

The ColNomic Embed Multimodal models use a **multi-vector late interaction** mechanism. Instead of creating one embedding per document or query, ColNomic creates multiple embeddings. This allows for more precise matching during retrieval and leads to better performance.

#### How We Improved Multimodal Embeddings

Building on these advances, we applied our learnings from training high-performance text embeddings to create even better multimodal embeddings. Starting with [Qwen2.5-VL 3B Instruct](https://huggingface.co/Qwen/Qwen2.5-VL-3B-Instruct) as our baseline, we implemented several key improvements:

##### 1. Sampling From the Same Source

We discovered that naive sampling across dataset sources allows models to learn shortcuts rather than semantic relationships. By forcing sampling from the same source, we create harder in-batch negatives that prevent the model from "cheating" and improve its understanding of content relationships.

**Result: +2.9 point** improvement on Vidore-v2 NDCG@5

##### 2. Hard Negative Mining

We trained an initial dense model on the [ColPali training dataset](https://huggingface.co/datasets/vidore/colpali_train_set) and [VDR Multilingual Train Dataset](https://huggingface.co/datasets/llamaindex/vdr-multilingual-train), then used it to retrieve the top-k nearest neighbors for each query.

Additionally, we reduced false negatives using positive-aware hard negative mining, a technique first introduced in [NV-Retriever](https://arxiv.org/abs/2407.15831).

**Results:**

* 1 Hard Negative: **+3.5 points**
* 4 Hard Negatives: **+4.7 points**
* 6 Hard Negatives: **+5.2 points**

#### Integration with Real World RAG Workflows

VLMs like Nomic Embed Multimodal simplify how RAG systems handle documents with rich visual content. Documents with with equations, diagrams, charts, and tables provide essential context alongside the text.

Technical documentation presents similar challenges - code blocks, flowcharts, and screenshots need to be understood together with their surrounding text. The same applies to product catalogs with specifications and images, or financial reports containing charts and numerical data.

By embedding visual and textual content together, retrieval becomes more accurate and integrations into real systems become much easier to implement and experiment with. Removing preprocessing steps often makes indexing faster and reduces complexity, and the single API for both images and text keeps implementations straightforward.

#### Conclusion

Nomic Embed Multimodal offers state-of-the-art performance while substantially simplifying the retrieval pipeline. As part of the broader Nomic Embed Ecosystem, this technology demonstrates our commitment to pushing the boundaries of embedding capabilities. To read more about our complete ecosystem, you can [learn more on our detailed blog post](https://www.nomic.ai/embed).

##### Get Started With Nomic Embed Multimodal

You can get started with our new model collection here in Hugging Face:

And here are some guides demonstrating how to use the new models as retrievers for RAG workflows:

###### Nomic Documentation

###### Google Colab Tutorial Notebooks

![nomic logo](https://www.nomic.ai/nomic_white.svg)nomic logo
