# Evaluating and Testing Your LLM Use Case

![rw-book-cover](https://readwise-assets.s3.amazonaws.com/media/uploaded_book_covers/profile_1492393/SAP-Learning-Socials_comprimida_fhiXs5y.png)

## Metadata
- Author: [[sap.com]]
- Full Title: Evaluating and Testing Your LLM Use Case
- Category: #articles
- Document Note: Guardrials, an open Python package use to evaluate outpus of LLM models
- Summary: This lesson teaches how to evaluate and test Large Language Model (LLM) use cases effectively. You will learn key performance metrics and best practices to ensure optimal performance in real-world applications. Additionally, MLOps plays a crucial role in automating testing and maintaining the reliability of LLM systems.
- URL: https://learning.sap.com/learning-journeys/navigating-large-language-models-fundamentals-and-techniques-for-your-use-case/evaluating-and-testing-your-llm-use-case_bf1eaef6-a9e0-4030-bc5f-3e059636b738

## Highlights
- See the list of common metrics used to assess the LLM performance:
  Perplexity:
  Perplexity measures how well a language model predicts a given sequence of words. Lower perplexity indicates better performance.
  Bilingual Evaluation Understudy (BLEU):
  BLEU assesses the quality of machine-generated translations by comparing them to reference translations. It computes precision for n-grams (typically 1 to 4) and averages them. N-grams are set a consecutive n-words like pairs of consecutive words, three consecutive words, and so on, that are extracted from a given sample of text or speech. These are used to analyze the word order or context for tasks like text classification.
  While commonly used in machine translation evaluation, BLEU can also be relevant for text generation tasks. For example, it can be used to measure the similarity of generated text (for example, summaries) to human reference text.
  Recall-Oriented Understudy for Gisting Evaluation (ROUGE):
  ROUGE evaluates the quality of text summarization systems. It measures the overlap between system-generated summaries and reference summaries.
  Classification Accuracy:
  This metric measures the proportion of correctly predicted instances out of the total. For example, if an LLM classifies customer reviews as positive or negative sentiment, accuracy tells us how often it predicts correctly.
  Precision and Recall:
  These metrics are essential for binary classification tasks.
  • Precision quantifies how many of the predicted positive instances are positive. It helps avoid false positives.
  • Recall (also known as sensitivity) measures how many actual positive instances were correctly predicted. It helps avoid false negatives.
  F1 Score:
  Often used for text classification tasks, the F1 score balances precision (correctly predicted positive instances) and recall (actual positive instances).
  Word Error Rate (WER):
  WER assesses the accuracy of automatic speech recognition systems by comparing system-generated transcriptions to human transcriptions.
  Semantic Similarity Metrics:
  These metrics include Cosine Similarity, Jaccard Index, and Word Mover’s Distance (WMD). They measure semantic similarity between sentences or documents.
  The evaluation metric that you must apply depends on your use case. Each metric provides different insights into model performance. ([View Highlight](https://read.readwise.io/read/01jkqm2esaym6baw75h971bn36))
- he focus in inference is on using the trained model for business applications by harnessing its predictive power on new, unseen data in a low-latency, scalable and cost-efficient manner. ([View Highlight](https://read.readwise.io/read/01jkqm7eej1mmbyt4wggrtyg0c))
- stable and reliable ([View Highlight](https://read.readwise.io/read/01jkqm7nymn5nbxke49mxspxdt))
- Automated Benchmarking - MLOps pipelines enable running a diverse set of test cases through CI/CD to benchmark capabilities like accuracy, latency, and explainability across different models, versions, and code changes. ([View Highlight](https://read.readwise.io/read/01jkqm9dbhvdbh4yjbftz12kn8))
- MLOps enables easier comparison between long running experiments, safe model upgrades, and provides rich analytics dashboards to track progress ([View Highlight](https://read.readwise.io/read/01jkqma6kvjy10bvqmax6cv935))
