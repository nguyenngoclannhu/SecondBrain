# How to Develop Large Language Model (LLM) Applications

![rw-book-cover](https://builtin.com/sites/www.builtin.com/files/styles/og/public/2023-10/llm-api-app-development.jpg)

## Metadata
- Author: [[Mojtaba Alfardan]]
- Full Title: How to Develop Large Language Model (LLM) Applications
- Category: #articles
- Summary: Large language models (LLMs) like ChatGPT have sparked interest in developing applications that use LLM APIs for both human-to-machine and machine-to-machine interactions. Building these applications comes with challenges, such as managing output consistency and token limits. As LLM technology evolves, integrating these models into software will become easier and more effective, enhancing user experiences.
- URL: https://builtin.com/artificial-intelligence/large-language-model-application-development

## Full Document
![Developer writing code for AI chat application](https://cdn.builtin.com/cdn-cgi/image/f=auto,fit=cover,w=1200,h=635,q=80/https://builtin.com/sites/www.builtin.com/files/2023-10/llm-api-app-development.jpg)
Image: Shutterstock / Built In

[Large language models (LLMs)](https://builtin.com/data-science/beginners-guide-language-models) have made a big splash since the release of OpenAI’s [ChatGPT](https://builtin.com/artificial-intelligence/what-is-chatgpt) 3.5 in November 2022. Ever since the first users interacted with the chat interface there’s been a lot of interest in the tech community over how this could be incorporated into the software industry and in LLM [APIs](https://builtin.com/software-engineering-perspectives/api). That interest was fueled further when ChatGPT 4 was released in March of 2023.

When it comes to interacting with software, there are two main types of interfaces, the first is human-to-machine interface, which is an interface designed around [human interactions](https://builtin.com/machine-learning/human-in-the-loop-hitl) like chat interfaces and web and mobile apps. The other is machine-to-machine interactions, which is designed for an interaction between two computers, for example HTTP APIs, programming libraries and database interfaces.

#### What Is a Large Language Model (LLM) API?

LLM APIs are application interfaces that allow developers to integrate natural language processing into an app. Popular LLM APIs include OpenAI’s ChatGPT and Google’s Bard. They can be applied to apps that handle either human-to-machine interactions or machine-to-machine interactions.

Developers often attempt to repurpose an interface initially designed for human-to-machine (HMI) interactions towards machine-to-machine (MMI) interactions. However, this transition isn’t always smooth sailing.

The current LLM APIs are all chat based which makes them inherently more suited for human interaction, and that’s part of what makes them so interesting. But this type of intelligence has a diverse set of applications, including those where it would be useful for a machine to consume the output. For those types of applications, there are additional hurdles to overcome due to the nature of this interface.

I’m going to use my experience in building apps on top of LLM APIs to go over the challenges faced with those two types of interfaces and how I overcame them.

#### Building a Human-to-Machine Interaction (HMI)

I developed an LLM app designed to process contract documents, enabling the users to inquire or reason about the content of the contracts through a chat interface. This is relatively simpler to build since all the LLM APIs are geared toward chat interfaces.

The app feeds the content of the documents and the questions in a prompt template to the LLM API and outputs the answer to the user, keeping the history of the prompts and feeding it back for the next questions.

Here are the main challenges faced during [building this app](https://builtin.com/software-engineering-perspectives/app-development) and how they were overcome.

[22 Interesting ChatGPT Examples](https://builtin.com/artificial-intelligence/chatgpt-examples)

##### How to Prevent Hallucinations

In the context of LLMs, [hallucination](https://builtin.com/artificial-intelligence/ai-hallucination) is when the output of the model is incorrect, nonsensical, or not real, even though the question posed to the model is about objective truths or the model is claiming that it is.

Despite providing the LLM API with the documents as a source of truth we still run into hallucinations occasionally, especially if the question tries to reason about a piece of the contract.

This is an open problem in LLM research without a definite solution, but all of the LLM APIs have an adjustable temperature parameter that controls the randomness of the output. When you lower the temperature, the output is more deterministic. This is useful when building applications that have a source of truth like this one.

According to OpenAI, the lower your [temperature](https://platform.openai.com/docs/guides/gpt/how-should-i-set-the-temperature-parameter), the more consistent the output, while setting higher values generate more diverse and creative results. You’ll want to set a temperature value based on the desired trade-off between coherence and creativity for your specific application.

Another way to deal with this problem is to do [consecutive prompts](https://builtin.com/artificial-intelligence/prompt-engineering) to the LLM model automatically and ask it to cite where it got the answer from.

For example, assume we have a contract that has an agreed upon price of $1000. here is the interaction that the app would do:

* **User:**What’s the agreed upon price?
* **App to model:**Here is the contract [insert contract here] and I have this question about it, What's the agreed upon price?
* **App to user:**$1000
* **App to model:**Could you cite where and how you found the answer.
* **App to user:**[it would insert the paragraph where it found or reasoned the result from].

Asking the model to cite the answers usually lowers the incidents of hallucinations.

One other thing to keep in mind is to design the app with this problem in mind and keep the users expectations in check by allowing the user to re-run any query similar to how most LLM chat applications do right now.

##### How to Address Context Size

The number of words that you can send or receive to an LLM API is limited, The limit is measured in tokens, which is around four characters. The range of popular LLM APIs goes from 4,000 tokens for ChatGPT 3.5, to 32,000 tokens for ChatGPT 4, and up to 100,000 for Anthropic’s Claude 2. For context 100,000 tokens can fit a small novel inside it.

Employing vector databases like [pinecone](https://www.pinecone.io/) is a strategic approach to navigate the token limitations commonly associated with interfacing with an LLM API. These databases store data in a numerical vector format, encapsulating complex textual information efficiently.

Before querying an LLM, a selective process can be performed within the vector database to pinpoint the most relevant data for the task at hand. By doing so, only pertinent vectors are passed on to the LLM, minimizing the token usage and ensuring that the LLM’s computational resources are expended judiciously.

This preliminary selection process in the vector database not only aids in economizing token usage but also in honing the focus of the LLM query, which is likely to yield more precise and meaningful results. The compact representation of data in vector databases facilitates a more effective and streamlined interaction with the LLM via the API, making the system more adept at managing resources and navigating token constraints.

Through this method, the communication between the vector database and the LLM API becomes more efficient, scalable and cost-effective, providing a robust solution to the challenges posed by token limitations in LLM APIs.

#### Building a Machine-to-Machine Interaction LLM Application

One application I developed that had an MMI was a system to generate and maintain E2E tests for websites based on natural language instructions. The inputs are what the test should do and the HTML code of the web pages, the output is the validated test code.

Translating natural language to code is one of the main features of LLM APIs, and they are relatively good at it. The challenging part here is that we are passing the web page code, which always runs against the context size limit mentioned earlier, and the fact that we are taking the code from the LLM API and executing it to validate the output.

##### How to Address Non-Repeatable, Arbitrary Output

The main challenge that’s unique to MMI is dealing with an API output meant for conversational human consumption to be consumed by a machine instead.

The first part of this challenge is that it’s hard to test the app and prompt integration since the output is non deterministic. Every time you prompt an LLM, it can give you a different answer. Evaluating the quality of your prompt has to be done through statistical analysis of the outputs over time. It also requires testing the result of the output in a high level instead of expecting an exact output every time because that’s impossible with this type of API.

It’s also hard to limit the LLM to only structured outputs grounded to a certain format repeatedly. In my app, I was trying to limit the output to only [JavaScript](https://builtin.com/software-engineering-perspectives/javascript) code with a certain context and that was challenging to do.

Fortunately, frameworks like [LangChain](https://python.langchain.com/docs/get_started/introduction) and new features provided by recent advances in LLM interfaces like [OpenAIs function calling](https://platform.openai.com/docs/guides/gpt/function-calling) made handling this easier.

OpenAI functions and LangChain are key tools that tackle the challenges tied to arbitrary output and formatting issues encountered when interacting with LLMs. OpenAI functions offer a customizable layer, enabling users to outline the structure and format of the engagement with the LLM, ensuring consistency and predictability in the responses.

Meanwhile, LangChain provides a mechanism for structured interaction with LLMs, through a protocol for defining and executing natural language-based agreements. This aids in standardizing the format of queries and responses, making the interaction with LLMs more organized and reducing ambiguities. Utilizing these tools, developers can define the desired format and structure of the output, enhancing the usability of LLM responses and easing their integration into various applications.

The synergy between OpenAI functions and LangChain presents a robust solution to address the issues of arbitrary output and inconsistent formatting, which are prevalent challenges when navigating the sophisticated yet highly adaptable nature of LLMs.

[Is Generative AI the New Metaverse](https://builtin.com/artificial-intelligence/is-generative-ai-new-metaverse)

#### Future of Building LLM Applications

The adventure of adding LLM APIs into apps is both a tricky and thrilling one. As we step ahead, diving into new ways and frameworks will keep making conversations between machines, and between us and machines, smoother.

Moreover, the push to polish up LLM APIs and try out new ideas is ready to take this field to new places. Mixing LLMs with upcoming tech like [edge computing](https://builtin.com/cloud-computing/what-is-edge-computing) is all set to pump up the power of apps based on LLMs. Also, as LLMs get better, they’ll clear up the blurry parts of putting them into apps, making the whole thing less of a headache. And as the API interfaces get smarter in the future, they’ll make bringing LLMs into apps a breeze, which will help a lot.

Developing apps with LLMs is all about bettering how we chat with technology.

As the world of LLMs keeps changing, so will the ways to fit LLM APIs in both people-to-machine and machine-to-machine apps, making our digital chats even more enjoyable. The road ahead is full of promise, with LLMs and smarter API interfaces making our tech talks a lot more natural and fun, showcasing the cool possibilities waiting for us in this exciting journey.
