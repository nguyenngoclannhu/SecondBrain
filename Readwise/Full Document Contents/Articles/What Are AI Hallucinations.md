# What Are AI Hallucinations?

![rw-book-cover](https://cloud.google.com/_static/cloud/images/social-icon-google-cloud-1200-630.png)

## Metadata
- Author: [[Google Cloud]]
- Full Title: What Are AI Hallucinations?
- Category: #articles
- Summary: AI hallucinations are incorrect results produced by AI models, often due to poor training data or biases. These errors can lead to serious problems, especially in critical areas like healthcare or finance. To reduce hallucinations, it's important to use high-quality data and provide clear guidance to the AI model during training.
- URL: https://cloud.google.com/discover/what-are-ai-hallucinations?hl=en

## Full Document
AI hallucinations are incorrect or misleading results that [AI models](https://cloud.google.com/learn/what-is-artificial-intelligence) generate. These errors can be caused by a variety of factors, including insufficient training data, incorrect assumptions made by the model, or biases in the data used to train the model. AI hallucinations can be a problem for AI systems that are used to make important decisions, such as medical diagnoses or financial trading.

**New customers get up to $300 in free credits** to try Vertex AI and other Google Cloud products.

[Get started for free](https://console.cloud.google.com/freetrial?redirectPath=/vertex-ai/)[Learn about Vertex AI](https://cloud.google.com/vertex-ai)

#### How do AI hallucinations occur?

AI models are trained on data, and they [learn to make predictions](https://cloud.google.com/learn/what-is-machine-learning) by finding patterns in the data. However, the accuracy of these predictions often depends on the quality and completeness of the training data. If the training data is incomplete, biased, or otherwise flawed, the AI model may learn incorrect patterns, leading to inaccurate predictions or hallucinations.

For example, an AI model that is trained on a dataset of medical images may learn to identify cancer cells. However, if the dataset does not include any images of healthy tissue, the AI model may incorrectly predict that healthy tissue is cancerous.

Flawed training data is just one reason why AI hallucinations can occur. Another factor that may contribute is a lack of proper grounding. An AI model may struggle to accurately understand real-world knowledge, physical properties, or factual information. This lack of grounding can cause the model to generate outputs that, while seemingly plausible, are actually factually incorrect, irrelevant, or nonsensical. This can even extend to fabricating links to web pages that never existed.

An example of this would be an AI model designed to generate summaries of news articles may produce a summary that includes details not present in the original article, or even fabricates information entirely.

Understanding these potential causes of AI hallucinations is important for developers working with AI models. By carefully considering the quality and completeness of training data, as well as ensuring proper grounding, developers may minimize the risk of AI hallucinations and ensure the accuracy and reliability of their models.

#### Examples of AI hallucinations

AI hallucinations can take many different forms. Some common examples include:

* **Incorrect predictions**: An AI model may predict that an event will occur when it is unlikely to happen. For example, an AI model that is used to predict the weather may predict that it will rain tomorrow when there is no rain in the forecast.
* **False positives**: When working with an AI model, it may identify something as being a threat when it is not. For example, an AI model that is used to detect fraud may flag a transaction as fraudulent when it is not.
* **False negatives**: An AI model may fail to identify something as being a threat when it is. For example, an AI model that is used to detect cancer may fail to identify a cancerous tumor.

#### How to prevent AI hallucinations

##### There are a number of things that can be done to prevent AI hallucinations, including:

##### Limit possible outcomes

When training an AI model, it is important to limit the number of possible outcomes that the model can predict. This can be done by using a technique called "regularization." Regularization penalizes the model for making predictions that are too extreme. This helps to prevent the model from overfitting the training data and making incorrect predictions.

##### Train your AI with only relevant and specific sources

When training an AI model, it is important to use data that is relevant to the task that the model will be performing. For example, if you are training an AI model to identify cancer, you should use a dataset of medical images. Using data that is not relevant to the task can lead to the AI model making incorrect predictions.

##### Create a template for your AI to follow

When training an AI model, it is helpful to create a template for the model to follow. This template can help to guide the model in making predictions. For example, if you are training an AI model to write text, you could create a template that includes the following elements:

* A title
* An introduction
* A body
* A conclusion

##### Tell your AI what you want and don't want

When using an AI model, it is important to [tell the model](https://cloud.google.com/learn/what-is-natural-language-processing) what you want and don't want. This can be done by providing the model with feedback. For example, if you are using an AI model to generate text, you can provide the model with feedback by telling it which text you like and don't like. This will help the model to learn what you are looking for.

##### Solve your business challenges with Google Cloud

###### How Google Cloud can help prevent hallucinations

Learn how to use Google Cloud to help prevent AI hallucinations:
