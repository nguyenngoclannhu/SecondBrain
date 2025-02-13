# Understanding Principles of Prompt Engineering

![rw-book-cover](https://readwise-assets.s3.amazonaws.com/media/uploaded_book_covers/profile_1492393/SAP-Learning-Socials_comprimida_DswugOD.png)

## Metadata
- Author: [[learning.sap.com]]
- Full Title: Understanding Principles of Prompt Engineering
- Category: #articles
- URL: https://learning.sap.com/learning-journeys/navigating-large-language-models-fundamentals-and-techniques-for-your-use-case/understanding-principles-of-prompt-engineering_b5b022c1-bd02-476a-9992-41e665c8c6ee

## Highlights
- Chain-of-Thought (CoT):
  CoT is a straightforward technique used to generate multiturn responses by extending the input prompt. Instead of providing a single prompt, multiple related prompts are concatenated to form a chain. The model processes this concatenated chain as a single input, allowing it to maintain context and continuity throughout the conversation. By including previous conversation history, the generated responses become more consistent.
  Here is an example of explaining how a seed grows into a plant.
  Initial Prompt:
  "Can you explain how a seed grows into a plant?"
  Chain of Thought Prompts:
  Prompt 1: "What is the first stage of seed germination?"
  Prompt 2: "What happens during the seedling stage?"
  Prompt 3: "How does the plant develop leaves?"
  Prompt 4: "What is the role of sunlight in plant growth?"
  This CoT approach ensures that a complex process is broken down into easy-to-understand parts, making it simpler to grasp the overall concept.
  This chaining of prompts helps the model understand the context better and generate more focused responses.
  Tree-of-Thought (ToT):
  The Tree-of-Thought technique takes the concept of multiple prompts a step further by creating a branching structure. It allows for exploration of different paths in a conversation, enabling a more extensive and nuanced discussion.
  Each branch of the tree represents a different possible path or user query, maintaining its own context while staying connected to the main conversation. By organizing prompts in a tree-like structure, the model can handle different strands of thought simultaneously and switch between them more seamlessly.
  Considering same example of explaining how a seed grows into a plant. This approach will branch out into different stages and aspects of seed growth.
  Initial Prompt:
  "Can you explain how a seed grows into a plant?"
  ToT branches:
  • Branch 1: "What is the first stage of seed germination?"
  • Sub-branch 1.1: "What happens during imbibition?"
  • Sub-branch 1.2: "How does the seed coat break?"
  • Branch 2: "What happens during the seedling stage?"
  • Sub-branch 2.1: "How do roots develop?"
  • Sub-branch 2.2: "How does the shoot emerge?"
  • Branch 3: "How does the plant develop leaves?"
  • Sub-branch 3.1: "What is the role of cotyledons?"
  • Sub-branch 3.2: "How do true leaves form?"
  • Branch 4: "What is the role of sunlight in plant growth?"
  • Sub-branch 4.1: "How does photosynthesis work?"
  • Sub-branch 4.2: "Why is sunlight important for photosynthesis?"
  Both techniques aim to improve the depth and quality of LLM responses, but they do so in different ways that are suited to different types of problems. ([View Highlight](https://read.readwise.io/read/01jkqhmz4mvd54tzmxa99vnxrw))
