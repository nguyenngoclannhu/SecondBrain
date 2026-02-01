# Evaluating and Testing Your LLM Use Case

![rw-book-cover](https://readwise-assets.s3.amazonaws.com/media/uploaded_book_covers/profile_1492393/SAP-Learning-Socials_comprimida_fhiXs5y.png)

## Metadata
- Author: [[sap.com]]
- Full Title: Evaluating and Testing Your LLM Use Case
- Category: #articles
- Document Note: Guardrials, an open Python package use to evaluate outpus of LLM models
- Summary: This lesson teaches how to evaluate and test Large Language Model (LLM) use cases effectively. You will learn key performance metrics and best practices to ensure optimal performance in real-world applications. Additionally, MLOps plays a crucial role in automating testing and maintaining the reliability of LLM systems.
- URL: https://learning.sap.com/learning-journeys/navigating-large-language-models-fundamentals-and-techniques-for-your-use-case/evaluating-and-testing-your-llm-use-case_bf1eaef6-a9e0-4030-bc5f-3e059636b738

## Full Document
![](data:image/svg+xml,%3csvg%20xmlns=%27http://www.w3.org/2000/svg%27%20version=%271.1%27%20width=%2750%27%20height=%2750%27/%3e)
Explaining Product Development for LLM Use Cases at SAP

After completing this lesson, you will be able to identify methods to evaluate and test your LLM use case

#### Methods and Metrics for Model Evaluation

Once you have explored Large Language Models (LLMs), prompt engineering, fine-tuning, and other techniques to streamline the performance of LLMs for your use case, you want to assess the performance of LLM in your use case.

In this unit, you will learn about the key metrics and methods to assess LLM performance for your use case. You will learn basic concepts, for example, model inference, to provide stable and reliable LLM predictions. You will also identify some best practices to ensure optimal performance for LLM applications.

See the list of common metrics used to assess the LLM performance:

Perplexity:Perplexity measures how well a language model predicts a given sequence of words. Lower perplexity indicates better performance.Bilingual Evaluation Understudy (BLEU):BLEU assesses the quality of machine-generated translations by comparing them to reference translations. It computes precision for n-grams (typically 1 to 4) and averages them. N-grams are set a consecutive n-words like pairs of consecutive words, three consecutive words, and so on, that are extracted from a given sample of text or speech. These are used to analyze the word order or context for tasks like text classification. While commonly used in machine translation evaluation, BLEU can also be relevant for text generation tasks. For example, it can be used to measure the similarity of generated text (for example, summaries) to human reference text.

Recall-Oriented Understudy for Gisting Evaluation (ROUGE):ROUGE evaluates the quality of text summarization systems. It measures the overlap between system-generated summaries and reference summaries.Classification Accuracy:This metric measures the proportion of correctly predicted instances out of the total. For example, if an LLM classifies customer reviews as positive or negative sentiment, accuracy tells us how often it predicts correctly.Precision and Recall:These metrics are essential for binary classification tasks.* Precision quantifies how many of the predicted positive instances are positive. It helps avoid false positives.
* Recall (also known as sensitivity) measures how many actual positive instances were correctly predicted. It helps avoid false negatives.
F1 Score:Often used for text classification tasks, the F1 score balances precision (correctly predicted positive instances) and recall (actual positive instances).Word Error Rate (WER):WER assesses the accuracy of automatic speech recognition systems by comparing system-generated transcriptions to human transcriptions.Semantic Similarity Metrics:These metrics include Cosine Similarity, Jaccard Index, and Word Mover’s Distance (WMD). They measure semantic similarity between sentences or documents.
The evaluation metric that you must apply depends on your use case. Each metric provides different insights into model performance.

#### Best Practices for LLM Applications

See the video to learn more about assessing LLM's performance.

Performance metrics like accuracy, explanatory ability, robustness to errors and efficiency can be considered during model inference.

##### Use Model Inference

Model inference refers to the stage where a trained Large Language Model (LLM) is deployed into production for making predictions on real-world data. It is an essential phase in extracting value from LLMs.

During inference, new input text, documents, or queries are fed into the LLM API. This could be customer conversations, product descriptions, legal contracts, and so on, based on the business use case.

The LLM then uses its learned linguistic patterns and knowledge gained during pretraining and fine-tuning to analyze the new inputs. Common capabilities explored at inference time can include:

* Sentiment analysis
* Named entity recognition
* Text summarization
* Question answering
* Language translation
* Generating content like emails, reports, and others

The central aspect that distinguishes inference is that the LLM is no longer being trained here. Its parameters are fixed after the training phase. The focus in inference is on using the trained model for business applications by harnessing its predictive power on new, unseen data in a low-latency, scalable and cost-efficient manner. The key objective is to provide stable and reliable LLM predictions that translate into business value.

##### Explore Best Practices

See the list for some best practices to ensure optimal performance for LLM applications for your use case:

* **Fine-tune on domain-specific data:** Pretrain LLMs further on relevant industry or company data like customer support tickets, legal contracts, and others. This enhances accuracy on business terminology.
* **Incrementally update training data:** Add new product specifications, policy documents, and so on, to continually fine-tune LLMs to maintain performance as new data comes in.
* **Test with production workloads:** Evaluate LLMs with real customer queries, transactions, and others instead of synthetic data to measure production readiness.
* **Set rigorous quality metrics:** Define quantitative KPIs like accuracy, latency, explanation capability to benchmark model performance.
* **Monitor and address errors:** Log model failures during inference to identify areas of improvement and feedback into the next training iteration.
* **Optimize infrastructure costs:** Consider infrastructure, for example virtual machine service, or configurations used for training. Model the inference based on efficiency testing to reduce overprovisioning.
* **Failover policies for downtime:** Create a backup configuration and redundancy for mission-critical LLM applications to ensure 24/7 availability.
* **Leverage MLOps:** Standardize benchmarking, model retraining releases for maintainability, and reproducibility of LLM systems over time.

The role of MLOps in testing and evaluating LLM performance for your use case is described in the next topic.

The goal is to make LLMs easy to integrate and enhance continually across dynamic business use cases. Following these best practices aids reliability, cost control as well as supports future innovation.

##### Leverage MLops for Testing and Evaluating LLMs Use Case

MLOps plays an integral role in systematically testing and evaluating LLM performance for your use case through:

* Automated Benchmarking - MLOps pipelines enable running a diverse set of test cases through CI/CD to benchmark capabilities like accuracy, latency, and explainability across different models, versions, and code changes.
* Centralized Performance Logging - All evaluation metrics during training, validation, and inference are logged in an aggregated manner for analysis and model comparison.
* Smoother Retraining Setups - Old model versions can be retrained using updated datasets in a reproducible way to measure performance improvements.
* Error Analysis at Scale - Logs from all running instances are funneled to identify systematic gaps for models to address via feedback loops or architecture tweaks.
* Gradual Rollouts - Models are first served to a small percentage of traffic to test stability before rollout to higher production volumes in a safe manner.
* Automated Alerting - Integration with monitoring tools like Prometheus, Grafana, ElasticSearch, Kibana allows setting alerts on metrics deviations.

By standardizing LLM testing protocols and using automation, MLOps enables easier comparison between long running experiments, safe model upgrades, and provides rich analytics dashboards to track progress. This is invaluable for business-critical AI where continuity in performance rigor is essential.

##### Secure Your LLM Applications

You also need to evaluate the safety and security of your LLM applications and protect them against potential risks. Monitor and enhance security measures over time to safeguard your LLM applications. Detect and prevent critical security threats like hallucinations, jailbreaks, and data leakage. Explore real-world scenarios to prepare for potential risks and vulnerabilities.

#### Further Reading

This blog post discusses a use case involving multiple AI agents in the context of SAP: [Multi AI Agents use case. SAP Maintenance Notification creation](https://community.sap.com/t5/artificial-intelligence-and-machine-learning-blogs/multi-ai-agents-use-case-sap-maintenance-notification-creation/ba-p/13608309).

This page provides an overview of how SAP Business AI capabilities can be embedded into applications and scenarios: [Artificial Intelligence | SAP Business AI](https://www.sap.com/products/artificial-intelligence.html).

This page provides an overview of AI solutions on an SAP Business Technology Platform: [AI tools for SAP application development](https://www.sap.com/products/artificial-intelligence/business-technology-platform.html).
