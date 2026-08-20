---
title: "Re: To built a strong understanding of how LLM and GenAi works and why it is important in todays wor"
source: https://community.sap.com/t5/artificial-intelligence-blogs-posts/to-built-a-strong-understanding-of-how-llm-and-genai-works-and-why-it-is/bc-p/14296812/emcs_t/S2h8ZW1haWx8ZGlnZXN0X25vdGlmaWNhdGlvbnxNSktYQTNXWTg4VTBEVHwtMXxPVEhFUlN8aEs#M843
author:
  - "[[Thakur_Avinash]]"
published: 2025-12-24
created: 2026-01-05
description: "Topics Covered Famous LLMs: GPT, Mistral, LLaMA, Claude Real-life use cases How an LLM actually works Why LLMs matter in 2025 What is an LLM? LLM stands for Large"
tags:
  - ai
  - LLM
  - articles
cssclasses:
  - daily
  - monday
  - "[[Inbox]]"
---
- [SAP AI Launchpad](https://community.sap.com/t5/c-khhcw49343/SAP%2520AI%2520Launchpad/pd-p/73555000100800003283)
- [AI Foundation](https://community.sap.com/t5/c-khhcw49343/AI%2520Foundation/pd-p/f080aab2-6cc2-4d93-bc68-abae077b8119)

Topics Covered

- Famous LLMs: GPT, Mistral, LLaMA, Claude
- Real-life use cases
- How an LLM actually works
- Why LLMs matter in 2025

What is an LLM?

LLM stands for Large Language Model.

It is a type of Artificial Intelligence designed to understand, generate, and interact using human language.

LLMs are trained on massive datasets such as books, websites, technical documentation, and Wikipedia.

Examples include ChatGPT, Claude, Gemini, LLaMA, and Mistral.

Think of an LLM as a highly advanced auto-complete system — not just for words, but for conversations, code, documents, and reasoning.

Why LLMs Matter in 2025

- “LLMs are **augmenting and, in some cases, replacing** traditional rule-based software
- They power chatbots, AI tutors, code assistants, and business analysis tools
- They are easy to integrate into applications via APIs
- The future of work is You + AI — LLMs act as intelligent assistants

![Thakur_Avinash_0-1766095870245.png](https://community.sap.com/t5/image/serverpage/image-id/353964i698ADA5286C429CD/image-size/medium?v=v2&px=400 "Thakur_Avinash_0-1766095870245.png")

Famous LLMs

- GPT (OpenAI): Strong reasoning, coding, and enterprise adoption
- Claude (Anthropic): Safe, long-context, document-heavy workloads
- LLaMA (Meta): Open-weight, customizable enterprise models
- Mistral: Lightweight, fast, cost-efficient open models

Real-Life Use Cases

- Customer support chatbots
- Document summarization
- Code generation and review
- SAP process guidance and copilots
- Knowledge search across enterprise documents

Start thinking of how you can build AI tools using LLMs, even if you're a beginner.

![Thakur_Avinash_1-1766095870271.png](https://community.sap.com/t5/image/serverpage/image-id/353963i849453E9924A6E51/image-size/medium?v=v2&px=400 "Thakur_Avinash_1-1766095870271.png")

How Does an LLM Actually Work?

Simple explanation:

1. **Tokenization**: Breaks your text into smaller units (tokens)
2. **Embedding**: Converts tokens into numbers (vectors)
3. **Transformer**: Uses an **attention mechanism** to decide which words matter
4. **Prediction**: Generates the next token (word/letter) based on training

“Attention is all you need”

– the core of how LLMs work

“Attention is all you need” — the core idea behind modern LLMs

![Thakur_Avinash_2-1766095870304.png](https://community.sap.com/t5/image/serverpage/image-id/353965iFCDE0CE053FA8378/image-size/medium?v=v2&px=400 "Thakur_Avinash_2-1766095870304.png")

![Thakur_Avinash_3-1766095870352.png](https://community.sap.com/t5/image/serverpage/image-id/353968i5BA501FC9BC4C709/image-size/medium?v=v2&px=400 "Thakur_Avinash_3-1766095870352.png")

### Step 1: Tokenization

Tokenization is the process of breaking input text into smaller units called **tokens**.  
Depending on the tokenizer, these tokens may represent **words, subwords, or characters**.

**Input:**  
"Create sales order for customer"

**Example (subword-style tokens):**  
\["Create", " sales", " order", " for", " customer"\]  
  
These are **not plain word splits**.  
Whitespace is preserved (for example, " sales" includes a leading space), which helps the model understand context and sentence structure more accurately.

This approach enables the model to:

- Handle **domain-specific terms** (e.g., *sales order*, *customer*)
- Support **multi-language enterprise data**
- Gracefully manage **unseen or rare words**

You can visualize how tokenization works using OpenAI’s tokenizer tool:  
🔗 [https://platform.openai.com/tokenizer](https://platform.openai.com/tokenizer)

## Step 2: Embeddings (Vector Representation)

After tokenization, **each token is converted into a numerical vector**, called an **embedding**.  
An embedding is a list of numbers that represents the **semantic meaning** of a token in a high-dimensional space.

**Important point (correctness):**

- One token → **one embedding vector**
- Typical vector sizes are **768, 1024, or higher**, depending on the model
- If a sentence has **N tokens**, the model produces **N vectors**

### SAP Business Example

**Input text:**  
"Create sales order for customer ABC"

**Example tokenization (simplified):**  
\["Create", " sales", " order", " for", " customer", " ABC"\]

Each token is converted into a vector:

"Create" → \[0.12, -0.55, 1.03,...\]" sales" → \[0.45, 0.82, 0.66,...\]" order" → \[0.78, -0.21, 0.14,...\]" customer" → \[-0.34, 0.91, 0.02,...\]

Individually meaningless, but meaningful **in relation to other vectors**

- Business intent
- Context (action vs object)
- Domain relevance (sales, order, customer)

## Do All LLMs Generate the Same Embedding?

**No — embeddings are NOT universal.**  
The same word (e.g., *Material*, *Vendor*, *Sales Order*) will have different vectors depending on:

1. **The model**  
	GPT, BERT, LLaMA, etc., use different architectures and objectives.
2. **Training data**  
	A model trained on enterprise or ERP data understands SAP terms more precisely.
3. **Tokenizer strategy**  
	BPE, WordPiece, or SentencePiece can split SAP terms differently  
	(e.g., SalesOrder vs Sales + Order).

## Why Embeddings Matter in SAP Semantic Search

Traditional SAP search works like this:

- Exact keyword match
- Field-based filtering
- Limited understanding of intent

### Embeddings change this completely.

🔹 With embeddings, **meaning is compared instead of text**.

**Example:**

User searches:

*"How to create a customer order?"*

SAP documents may contain:

- *"Sales Order creation using VA01"*
- *"Process flow for order-to-cash"*

Even though the words differ, embeddings place them **close together in vector space**, allowing the system to retrieve the right documents.

## Step 3: Transformer (Self-Attention)

This is where the model **understands context**.  
The Transformer uses a mechanism called **self-attention**, which allows it to look at **all tokens in the sentence at the same time** and determine:

- Which tokens are **most important**
- How tokens are **related to each other**
- Where the model should **focus more or less**

**Key correctness note:**  
Attention does **not** “think” sequentially like humans.  
Instead, it assigns **weights** to relationships between tokens based on learned patterns.

### Example (Conceptual)

**Input sentence:**  
"Most famous product in France"

The model learns relationships such as:

- **“product” ↔ “France”** (geographic relevance)
- **“famous”** increases importance by acting as a qualifier
- Contextually important tokens receive **higher attention weights**

As a result, the attention mechanism focuses more strongly on:

- " product"
- " France"

while giving less weight to supporting words like "most" or "in".

### SAP Business Example

**Input:**  
"Create sales order for customer ABC"

Through self-attention, the model learns:

- **“sales order”** is the core business object
- **“customer ABC”** provides critical context
- **“create”** indicates an action or intent

This enables the model to distinguish between:

- *Sales Order creation*
- *Customer master data*
- *Order-to-Cash process*

even though all words appear in the same sentence.

### Intuitive Explanation (Human Analogy)

You can think of attention like this:

“The key concept here is a Sales Order,  
the customer gives context,  
and the verb tells me what action is required.”

The model doesn’t reason like a human, but **self-attention mathematically achieves the same outcome** by emphasizing the most relevant parts of the input.

## Step 4: Prediction (Output Generation)

After processing the input through embeddings and transformer layers, the LLM produces a **probability distribution over the next possible tokens**.

At this stage, the model outputs **logits/probabilities**, which are then converted to text via decoding.  
Instead, it predicts **which token is most likely to come next**, based on everything it has learned so far (prompt + prior tokens).

### SAP Business Example

**Input prompt:**  
"Create sales order in SAP"

The model internally computes probabilities such as:

- " using" → 42%
- " for" → 28%
- " via" → 15%
- " transaction" → 10%
- " automatically" → 5%

A **decoding algorithm** (e.g., greedy decoding, top-k, or nucleus sampling) selects the next token based on these probabilities.

**Generated output (step by step):**

- "Create sales order in SAP using VA01"
- "Create sales order in SAP using VA01 transaction"

This process repeats **one token at a time** until a stopping condition is reached.

### What Influences the Prediction?

The final output depends on multiple factors:

- **Training data**  
	Determines how well the model understands SAP terminology and processes.
- **Prompt context**  
	Small prompt changes can significantly alter the output.
- **Temperature**
	- Low temperature → more deterministic, factual responses
	- High temperature → more creative, diverse outputs
- **Maximum token limit**  
	Controls how long the response can be.

**Correctness note:**  
The model always predicts **one next token at a time**, even when generating long paragraphs.

### How This Works Conceptually (Linked to the Diagram)

1. **Prompt + previous tokens** are fed into the LLM
2. The model computes a **probability distribution** over the vocabulary
3. A **decoding strategy** selects one token
4. The selected token is appended to the output
5. Steps 1–4 repeat until completion

![Thakur_Avinash_4-1766095870400.png](https://community.sap.com/t5/image/serverpage/image-id/353967iB7A02100BBD08E14/image-size/medium?v=v2&px=400 "Thakur_Avinash_4-1766095870400.png")

  
  

![Thakur_Avinash_5-1766095870425.png](https://community.sap.com/t5/image/serverpage/image-id/353966i5F844A76C297591A/image-size/medium?v=v2&px=400 "Thakur_Avinash_5-1766095870425.png")

  
  

## 1\. Temperature

**Temperature controls how random or deterministic the model’s output is.**  
It influences how the model samples from the probability distribution of the next token.

- **Low temperature (e.g., 0.2–0.3)**
	- Output is highly **deterministic**
	- The model almost always selects the **highest-probability token**
	- Best for **enterprise, SAP, and factual use cases**
- **High temperature (e.g., 1.0 or above)**
	- Output becomes more **diverse and creative**
	- The model samples from a **broader range of tokens**
	- Useful for **brainstorming, ideation, or creative writing**

In simple terms:

Lower temperature = *precision and consistency*  
Higher temperature = *variety and creativity*

## SAP-Oriented Intuition

**Prompt:**  
"Create sales order in SAP"

- **Low temperature:**  
	→ *"Create sales order in SAP using VA01"*
- **High temperature:**  
	→ *"Create a sales order in SAP through standard order processing steps"*

Same knowledge — different **expression style**, controlled by temperature

## 2\. Top-k Sampling

**Top-k sampling limits the model’s choices to only the** ***k*** **most likely tokens.**  
Instead of considering the entire vocabulary, the model:

- Selects the **top** ***k*** **tokens** with the highest probabilities
- **Discards all remaining tokens**
- Randomly samples **only from this reduced set**, weighted by their probabilities

Common values:

- k = 20–50 for balanced outputs
- Lower k → more deterministic
- Higher k → more diversity

### Simple Intuition

If the model predicts thousands of possible next tokens:

- **Top-k = 40**  
	→ Only the 40 most likely tokens are kept  
	→ Everything else is ignored  
	→ Sampling happens only within these 40 tokens

This prevents:

- Rare, nonsensical words
- Extremely low-probability noise

### SAP Business Example

**Prompt:**  
"Create sales order in SAP"

**Next-token probabilities (simplified):**

| **Token** | **Probability** |
| --- | --- |
| using | 0.45 |
| for | 0.25 |
| via | 0.15 |
| automatically | 0.08 |
| process | 0.03 |
| … | … |

With **Top-k = 3**:

- Allowed tokens → \["using", "for", "via"\]
- All other options are **discarded**
- Final token is sampled **only from these three**

This ensures outputs remain **relevant to SAP context**.  
  

![Thakur_Avinash_6-1766095870429.png](https://community.sap.com/t5/image/serverpage/image-id/353969i2BDDB98FE8EAE4BC/image-size/medium?v=v2&px=400 "Thakur_Avinash_6-1766095870429.png")

## 3\. Top-p Sampling (Nucleus Sampling)

🔹 **Top-p sampling selects the smallest set of tokens whose cumulative probability exceeds a threshold** ***p*****.**  
Instead of fixing the number of tokens (like Top-k), the model:

- Sorts tokens by probability (highest → lowest)
- Keeps adding tokens **until their total probability ≥ p** (e.g., 0.9)
- **Samples randomly only from this dynamic set**
- Discards all remaining tokens

Because the set size changes per step, Top-p is **more adaptive than Top-k**.

### Why Top-p Is Different from Top-k

- **Top-k** → fixed number of tokens (rigid)
- **Top-p** → variable number of tokens (context-aware)

If the model is confident:

- Few tokens may already reach p = 0.9

If the model is uncertain:

- More tokens are included automatically

### SAP Business Example

**Prompt:**  
"Create sales order in SAP"

**Next-token probabilities (simplified):**

| **Token** | **Probability** | **Cumulative** |
| --- | --- | --- |
| using | 0.45 | 0.45 |
| for | 0.25 | 0.70 |
| via | 0.15 | 0.85 |
| automatically | 0.08 | 0.93 |
| process | 0.04 | 0.97 |

With **Top-p = 0.9**:

- Selected tokens → \["using", "for", "via", "automatically"\]
- Sampling happens **only within this nucleus**

📌 This adapts naturally based on SAP context and wording.

## When to Use Top-p (SAP Perspective)

Use Top-p when you want:

- Stable, **context-aware enterprise responses**
- Flexibility across different prompts
- Fewer tuning headaches than Top-k

Common enterprise setting:

- top\_p = 0.9
- temperature = 0.2–0.4

## 4\. Min-p Sampling (Minimum Probability Cutoff)

**Min-p sampling removes all tokens whose probability falls below a fixed threshold** ***p*****.**  
Only tokens that individually meet the minimum probability requirement are allowed for sampling.

- Tokens with **probability < p** are **discarded**
- Sampling happens only among the **remaining high-confidence tokens**
- Unlike Top-k or Top-p, the cutoff is based on **absolute probability**, not rank or cumulative mass

Example threshold:

- min\_p = 0.05 or 0.1

### Simple Intuition

If the model predicts the next token with probabilities:

| **Token** | **Probability** |
| --- | --- |
| using | 0.45 |
| for | 0.25 |
| via | 0.15 |
| automatically | 0.08 |
| process | 0.04 |
| … | … |

With **min-p = 0.1**:

- Allowed tokens → \["using", "for", "via"\]
- Tokens like "automatically" and "process" are removed
- Sampling occurs only among **confident choices**

### SAP Business Example

**Prompt:**  
"Create sales order in SAP"

Using Min-p ensures:

- Rare or irrelevant words are filtered out
- Outputs stay **business-accurate**
- No low-confidence or nonsensical tokens appear in responses

Especially useful in:

- SAP copilots
- Transaction guidance
- Compliance-sensitive outputs

## When Min-p Is Useful (Enterprise Perspective)

Use Min-p when:

- You need **high precision**
- Hallucinations must be avoided
- The domain vocabulary is well-defined (SAP, ERP, finance)

**Recommended Enterprise Settings:**

- Temperature: 0.2 – 0.4
- Top-p: 0.9
- Min-p: 0.05
- Avoid very high temperature for business use

**Key Takeaway**

LLMs do not think like humans.

They predict the next most likely token — repeatedly — guided by probabilities and attention.

[1 Like](https://community.sap.com/t5/kudos/messagepage/board-id/aiblog-board/message-id/836/tab/all-users "Click here to see who liked this post")

> Excellent deep dive into how LLMs actually work. Loved the clear explanation of embeddings, self-attention, and decoding strategies with real-world SAP use cases. This is a great learning resource for anyone starting with LLMs and GenAI. The practical SAP examples and explanation of temperature, top-k, and top-p make it highly actionable. Thanks for sharing!

[1 Like](https://community.sap.com/t5/kudos/messagepage/board-id/aiblog-board/message-id/839/tab/all-users "Click here to see who liked this post")

Hi [@Thakur\_Avinash](https://community.sap.com/t5/user/viewprofilepage/user-id/1614040),  
  

This is an outstanding write-up demonstrating a deep grasp of LLM internals—from tokenization and embeddings to transformers and decoding strategies.  
  
The seamless linkage of theory with enterprise and SAP use cases, along with clear treatment of temperature, top-k, and top-p, makes the analysis both practical and technically rigorous.  
  
A very well-structured and insightful piece!!!