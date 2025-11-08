# Agents is the most important BTP release this 2024

![rw-book-cover](https://readwise-assets.s3.amazonaws.com/media/uploaded_book_covers/profile_1492393/SAP_R_grad_200x200_Fa0aJOF.png)

## Metadata
- Author: [[MarioDeFelipe]]
- Full Title: Agents is the most important BTP release this 2024
- Category: #articles
- Summary: Agents are a new approach in AI that use language models to reason and choose actions, enhancing tasks like automation and chatbots. They have components like memory and planning to improve their effectiveness and adaptability. This technology is evolving rapidly, promising greater autonomy and better performance in various applications.
- URL: https://community.sap.com/t5/artificial-intelligence-and-machine-learning-blogs/agents-is-the-most-important-btp-release-this-2024/ba-p/13601686

## Full Document
I will first explain Agents in general, and then I will go around what all this has to do with SAP. For the interest of the readers and my mental health, I shortened this blog and will split it into others as we progress, talking about new *Thoughting* techniques and Agent Evaluations. So, if you are already skilled on Agents, go to point 2.

Initially, large language models (LLMs) functioned as basic, reactive machines, predominantly designed for processing and predicting language patterns. Early GPTs showcased the ability to generate coherent text and condense information effectively, yet they did not possess **objectives**, **distinct personas**, or the **capacity for autonomous action**—they were merely algorithmic linguists, with no ambition.

In October 2022, paper "**ReAct: Synergizing Reasoning and Acting in Language Models**" by Princeton and Google Brain introduced a framework with the idea to amalgamate reasoning with action in language models to enhance their functionality, versatility, and interoperability, they called it ReACT, and **Agents** were born.

The ReACT Agent, or **ReAct**, was presented as a pioneering approach devised for prompting LLMs in tasks necessitating explicit reasoning and/or action. Inspired by human decision-making that combines "acting" and "reasoning,"

The core idea of **Agents** is to use a language model to choose a sequence of actions to take. In chains, a sequence of actions is predefined. In Agents, a language model is used as a *reasoning* engine to determine which actions to take and in which order.

![MarioDeFelipe_0-1707576353142.png](https://community.sap.com/t5/image/serverpage/image-id/63602i4DB4BF5C541FCCC7/image-size/large?v=v2&px=999)
1. Actions lead to observation feedback from an external environment (ENV)
2. Reasoning traces only affect the internal state of the LLM
3. The state is updated with information to support future actions and reasoning

### MarioDeFelipe_1-1707576352988.png

Think of an Agent as our piece of code which will be calling a Language model (which is NOT our piece of code) to accomplish a task that we want to do. Agents are ours; Models are not. An Agent goes through a cyclic process of generating a thought, taking an action, and then observing the result of the action before it decides if it continues doing stuff or goes over. Combining reasoning traces and actions allows us to perform dynamic reasoning, maintain high-level plans, and interact with external environments to gather additional information; the better the Agent is, the better it will serve us, our users, and customers, so let's see what we need to do to be good at it.

As users experimented and interacted with these systems, it became apparent that with strategic prompt crafting, these LLMs could produce responses that mirrored human-like interaction. By embedding personas and identities within the prompts, the responses from LLMs began to take on specific tones, showcase particular viewpoints, and draw from a more defined base of knowledge. This evolution in prompt design unlocked the potential for LLMs to engage in planning, self-reflection, and basic reasoning, setting the stage for the emergence of more autonomous, agent-like behaviors.

#### 1.1 Evolution of Generative AI into Agents

![MarioDeFelipe_2-1707576353217.png](https://community.sap.com/t5/image/serverpage/image-id/63603i3F5DF7C324315981/image-size/large?v=v2&px=999)
More advanced Agent engineering is a distinctive approach aimed at augmenting the capabilities of an agent, setting it apart from model fine-tuning and prompt engineering.

Trial-and-error describes how an agent performs an action, followed by an evaluation from a pre-defined critic. If the action falls short of expectations, the agent adapts by integrating the critic's feedback.  

Crowd-sourcing is the Agent's capability to leverage collective intelligence to enhance agent capabilities. Agents start by providing individual responses to a question. Inconsistencies among responses prompt them to consider others' insights, leading to an iterative process of updating and improving responses until a consensus is reached.

![MarioDeFelipe_3-1707576353218.png](https://community.sap.com/t5/image/serverpage/image-id/63604iA68DD481C5A50AB7/image-size/large?v=v2&px=999)
The agent's behavior is shaped by detailed prompts that define its personality, capabilities, and boundaries. Depending on its programming, an LLM Agent can range from being reactive to taking proactive steps.

Agents can operate semi-independently, aiding in diverse tasks like powering chatbots or automating workflows. They are adaptable, understand natural language, and work alongside humans.

For enhanced autonomy, LLM Agents are given access to extensive knowledge sources and reasoning tools. Through prompt engineering, they're endowed with skills for comprehensive analysis, planning, execution, and self-improvement. With the right knowledge and prompts, they can handle workflows requiring minimal human supervision.

![MarioDeFelipe_4-1707576353220.png](https://community.sap.com/t5/image/serverpage/image-id/63605i9990F5363315F6B5/image-size/large?v=v2&px=999)
Focusing on the aspect of language modeling previously discussed, it's evident that language models often lack sufficient knowledge about customers to deliver a satisfactory customer experience. For language models to craft a personalized and effective customer experience, they must have access to both raw and processed customer data, the latter of which is derived from analytical services.

Therefore, it's essential to provide language models with access to various analytical outputs, things like churn, retention scores, segmentation models, product recommendations, and customer journey analytics if the Agent is on e-Commerce for example, this will give the Agent access to information which we, as humans, might miss on a day to day activities, enhancing our productivity.

#### 1.2 Agents Architecture

During the last weeks and months, we have experienced an increasing number of methods around two key points;

* ***Memory (Persistence specially)***: An agent's memory stores past experiences. It is crucial for learning, as it allows the agent to reference previous outcomes and adjust future actions accordingly.
* ***Planning (Thoughts aka Reasoning)***: Planning, Thoughts, Reasoning processes involve analyzing observations, drawing from memory, and considering possible actions. It's the agent's internal decision-making process, which may be powered by LLM.

![Captura de pantalla 2024-02-09 a las 11.19.52.png](https://community.sap.com/t5/image/serverpage/image-id/63623iFD305555E8DD9B8D/image-size/large?v=v2&px=999)
Although I will not dive specifically in this blog, the architecture of an Agent, especially when built upon a Large Language Model (LLM) foundation, encompasses several critical components that enable it to understand, plan, and interact with its environment effectively. Any given Agent framework available in opensource or closed source, divides the architecture into four key modules: Profile, Memory, Planning, and Action.

**Profile** module serves as the foundation of the Agent's identity and capabilities. It defines the Agent's knowledge base, preferences, skills, and any predefined information that shapes its interactions. This component is crucial for personalizing the Agent's responses and actions to align with its intended purpose or the specific requirements of its users.

**Memory** **Modules** is the Agent's ability to learn from and reference past interactions, experiences, or information it has processed. This module is not static; it evolves over time, allowing the Agent to build a more nuanced understanding of its environment, users, and tasks. This is an area which is receiving more exploration.

**Planning Module (Reasoning)** is where the Agent synthesizes information from the Profile and Memory modules to make decisions and formulate strategies for achieving its goals. This involves understanding the task at hand, considering potential actions, and evaluating the outcomes of those actions within the context of the Agent's objectives and the information available to it. Planning is a dynamic process that may involve generating multiple action paths, predicting their effectiveness, and selecting the most appropriate course of action based on the current context. I will describe this a little further below.

**Action Module** is where the Agent executes the decisions made during the Planning phase. This involves interacting with the external environment, whether through generating text, performing tasks within a digital framework, or manipulating external APIs and tools.

Together, these modules form a comprehensive architecture for Agents based on LLMs.

#### 1.3 Reasoning Techniques

![MarioDeFelipe_6-1707576353221.png](https://community.sap.com/t5/image/serverpage/image-id/63609i26AE82AAC2CD8EF3/image-size/large?v=v2&px=999)
The Planning is where we will apply our knowledge and expertise within an Agent's, designed to navigate complex tasks by breaking them down into smaller, more manageable sub-tasks and devising effective strategies for accomplishing them. Think about this as; this is where you, as an expert, or an SAP expert, will introduce your knowledge on how to accomplish a task, which things could happen, all the characteristics, problematics, which could be encountered on a business process. I will go through this during the SAP specific chapter.

Planning module operates through two primary types of planning: feedback-independent plans and feedback-based plans.

**Single-Path Reasoning** method involves creating plans in a linear, step-by-step sequence. Each step is determined based on the outcome of the previous one, leading to a cascading series of actions that aim to achieve the task's objective.

**Multi-Path Reasoning**, unlike single-path reasoning, multi-path reasoning explores multiple potential paths to achieve the task's goal. This approach generates a variety of alternative plans, organizing them in a tree or graph-like structure to assess different outcomes and pathways. It allows for a more comprehensive exploration of possible actions and their consequences.

#### 1.4 Types of Agents

![MarioDeFelipe_7-1707576353173.png](https://community.sap.com/t5/image/serverpage/image-id/63608i81C8CCC76442294B/image-size/large?v=v2&px=999)
In my view, there are two types of AI agents: **conversational agents** and **task-oriented agents**.

**Conversational Agents** (like SAP Joule) are designed for human-like dialogue, adept at engaging in conversations that can mimic human interaction. They are personalized through prompt engineering to exhibit specific tones, styles, and knowledge bases. They're used in scenarios where a natural and adaptive conversational partner is beneficial, such as customer service or as virtual advisors in various domains.

**Task-Oriented Agents** are pragmatic and focused on achieving specific goals. They are skilled in breaking down complex tasks, executing actions, and reporting outcomes. Through prompt engineering, they can approach problems strategically and refine their methods. They can work semi-autonomously or in teams to handle complex projects or workflows. Task-oriented agents are becoming crucial in automation and productivity enhancement within enterprises, where they act upon detailed instructions to accomplish tasks.

Understanding these categories helps choose and direct the right agent for specific needs, whether for engaging in dialogue or goal-oriented tasks.

#### 1.5 Memory of the Agent

Memory plays a pivotal role in the development of Agents, encompassing not just the interactions between AI and tools but also the interactions between users and AI. A third, increasingly prominent aspect in recent research on agents is personalization—enabling an agent to possess its own objectives and persona. Typically, this personalization is initiated by embedding specific roles and goals directly within the prompt, instructing the agent on its intended function and characteristics.

However, emerging research is exploring more dynamic methods of cultivating long-term memory in agents, allowing their personas and objectives to evolve over time. One notable area of work focuses on generative agents, examining innovative approaches to imbue agents with a sense of continuous memory and adaptability

"**Generative Agents: Interactive Simulacra of Human Behavior**" is an arxiv paper that delves into generative agents, examining innovative approaches to imbue agents with a sense of continuous memory and adaptability.

#### 1.6 Agents usage

1. Search
2. API calls
3. DB Calls
4. Run Code
5. etc

The motivation for using Agents stems from their ability to utilize tools and interface with external data sources and computational resources like search APIs and databases. This capability is crucial for addressing some inherent limitations of language models, such as their lack of access to specific data or their limited mathematical abilities.

While the concept of tool usage is not exclusive to Agents—since one can link language models (LLMs) to search engines or databases without an **agent framework (**aka**Generative AI Hub**or**Langchain**or**AutoGPT)**—the advantages of employing Agents lie in their enhanced flexibility and power. Agents facilitate better error recovery and are adept at handling complex, multi-step tasks by leveraging their role as a reasoning engine.

A fitting example is interacting with a database. Without an agent, this interaction might follow a linear process: translating a natural language query into a SQL query, executing it, and then interpreting the results back into a natural language in relation to the original question. This straightforward approach can be effective but doesn't account for potential complications, such as errors in the SQL query, hallucinated table or field names, or queries that necessitate multiple underlying queries for a comprehensive answer.

While a simple linear approach might address a majority of scenarios, it's the edge cases and more complex requirements where Agents prove their value. Their adaptable framework allows for navigating around these challenges more efficiently, showcasing their utility in scenarios where flexibility and robust error handling are essential.

#### 1.7 Agent Typical Implementation

1. Tool Selection
2. Observe the output of that Tool
3. Repeat the action until the condition is met, or use another Tool
4. Exit conditions can be LLM-determined or determined

Discussing the typical implementation of Agents at such an early stage in this domain might seem premature, given that the field is likely to evolve with various approaches. However, the standard process involves receiving a user query, employing the language model (LLM) as the agent to select an appropriate tool, and determining the input for that tool. Following this, the agent executes the action, observes the outcome, and feeds this information back into the language model. This cycle repeats until a stopping condition is met.

Exit conditions vary, but often, the language model determines when it has sufficiently addressed the query or completed the task, signaling that it's time to relay the outcome back to the user. Additionally, there can be predefined rules to ensure reliability; for example, if an agent has gone through several steps without reaching a conclusive answer, it might be programmed to respond regardless. Some tools might also have built-in mechanisms to generate responses automatically.

#### 1.8 Challenges with Agents

1. Getting them to use tools in appropriate scenarios
2. Not use tools if not needed
3. Parsing LLM output to tool invocation
4. Remembering previous steps taken
5. Incorporating long observations
6. Evaluation

Navigating the evolving landscape of Agent implementation presents a host of challenges, given that the field is still in its nascent stages. Understanding the hurdles they face is crucial for enhancing their reliability and functionality. One foundational challenge is enabling Agents to use tools correctly within relevant scenarios, with strategies like Chain of Thought (CoT) prompting and explicit instructions regarding available tools aiming to address this, emphasizing the importance of providing detailed tool descriptions to inform the Agent about each tool's capabilities.

However, scaling this with numerous tools introduces complexity, potentially leading to context length issues, and tool retrieval mechanisms offer a solution by filtering the most relevant tools for the task at hand. Another challenge is preventing Agents from defaulting to tool usage in scenarios where a direct response would suffice, especially in conversational contexts, with techniques including incorporating reminders within prompts or introducing a 'return to user' tool as a clever workaround to guide the Agent towards the desired behavior.

Translating the Agent's textual instructions into executable actions requires parsing the output into actionable code, and structuring requests can simplify this process, with JSON schemas and output parsers playing a pivotal role in converting and correcting the model's output into a format ready for execution.

Remembering previous steps (Memory) is essential for continuity in tasks, yet this becomes challenging with long sequences, and combining recent actions with the most relevant past actions through retrieval methods can help manage this, though balancing this with context limitations is key.

The last point, but not the last one on my list, is that dealing with extensive outputs from APIs or databases poses difficulties in maintaining context, and simplifying or dynamically summarizing these outputs ensures that only the most relevant information is retained for the Agent's use.

### MarioDeFelipe_8-1707576352990.png SAP use cases for Agents

There are several use cases where Agents can have an immediate benefit in the SAP world.

1. Personas
2. Workflows
3. Automation
4. Joule (Joule is an Agent, but potentially could be combined with other Agents)

the concept of Persona has been around for a while; let's bring an example of Asset Manager in the Oil and Gas industry.

#### MarioDeFelipe_9-1707576352993.png MarioDeFelipe_10-1707576352995.png *Asset Manager* in Oil and Gas

![MarioDeFelipe_11-1707576353247.png](https://community.sap.com/t5/image/serverpage/image-id/63612i559B99A173B2B727/image-size/large?v=v2&px=999)
![MarioDeFelipe_12-1707576353004.png](https://community.sap.com/t5/image/serverpage/image-id/63613iF9272FC571E78353/image-size/small?v=v2&px=200)
![MarioDeFelipe_13-1707576353214.png](https://community.sap.com/t5/image/serverpage/image-id/63614i7B66D798427957FB/image-size/large?v=v2&px=999)
Actions for **Asset Management** are very *agentic*;

**1) Analyze the issue (FL, Asset, Description, Time, Issue, Category Type, Class) and Act – IAM(PM + APM):**  

This refers to the process of analyzing issues related to facilities, assets, and their descriptions, time, issue type, category, and class using SAP Integrated Asset Management (IAM) in combination with SAP Plant Maintenance (PM) and SAP Asset Performance Management (APM). Accessing these tools help in managing and optimizing the performance of assets, as well as identifying and resolving issues.

**2) Check on the availability of resources (Equipment, People, and parts), Order, and Act – IAM + RSH:**  

This involves checking the availability of equipment, people, and parts resources using SAP Integrated Asset Management (IAM) and SAP Resource Scheduling and Health (RSH). The RSH tool helps in scheduling and managing resources, while IAM ensures that the resources are utilized efficiently.

**3) Find the optimal time for scheduling and dispatching – IAM + RSH:**  

This refers to the process of finding the optimal time for scheduling and dispatching resources using SAP Integrated Asset Management (IAM) and SAP Resource Scheduling and Health (RSH). These tools help in optimizing resource utilization and scheduling to ensure efficient operations.

**4) Analyze the Financial Impact (both Production and cost) - IAM + Finance + SAC:**  

This involves analyzing the financial impact of asset management decisions on production and costs using SAP Integrated Asset Management (IAM), SAP Finance, and SAP Analytics Cloud (SAC). These tools help in understanding the financial implications of asset management decisions and optimizing financial performance.

**5) Health Safety and ESG reporting – EH&S + IAM:**  

The process of generating health, safety, and Environmental, Social, and Governance (ESG) reports using SAP Environment, Health, and Safety (EH&S) and SAP Integrated Asset Management (IAM). Access to these tools help an Agent in ensuring compliance with health, safety, and ESG standards, as well as optimizing asset management to support ESG goals.

Please note that these tools are part of the broader SAP ecosystem, and their specific functionalities may vary depending on the SAP solution and version being used.

#### 2.2 Agents combined with Robotic Process Automation (iRPA)

SAP Process Automation, previously iRPA, is a powerful idea with mixed results. Process Automation is based on the RPAs from vendors like UIPath, BluePrism, or Pega.

Robotic Process Automation (RPA) technology generated hype until 2021, due to its potential to automate repetitive, rule-based tasks, thereby increasing efficiency and reducing human error. However, RPAs have not made as significant an impact as initially expected for several reasons, let me bring 4 of them;

1. Limited scope: RPAs are designed to automate simple, repetitive tasks and are not equipped to handle complex decision-making processes.

2. Interface dependency: RPAs interact with systems at the strict interface level, which can be a potential concern. Interfaces are prone to updates and changes, and RPAs may not always be flexible enough to adapt to these changes, leading to reduced effectiveness.

3. Vulnerability to change: In rapidly evolving industries, RPAs may become outdated quickly, as new technologies and processes emerge. They require continuous updates and maintenance.

However, RPAs can still be valuable tools for automating repetitive tasks and improving efficiency when used appropriately and in conjunction with an Agent, for example, with Probabilistic Workflows.

#### 2.3 SAP will go there as well

Just in time for this blog, I am happy to see that fresh from the lab, SAP announced this first week of February 2024, a new Automation engine called "Business Process Expert," which goes exactly in this direction.

![MarioDeFelipe_14-1707576353216.png](https://community.sap.com/t5/image/serverpage/image-id/63615i5D056A544547EE72/image-size/large?v=v2&px=999)
SAP announcement in the field of Robotic Process Automation (RPA) and the integration of generative AI into business process modeling and automation with features like;

Adding *recognition* in RPA, which can be either attended (requiring human intervention) or unattended (fully automated). This highlights the flexibility and adaptability of RPA technologies to different operational needs.

**Low-Code Generation and AI Integration** (by Mid-2024). There will be advancements in low-code generation platforms equipped with executable process AI. This development is likened to existing challenges in learning and applying the CAP (Cloud Application Programming) framework within business application studios. The aim is to simplify the modeling of complex business processes and automations, acknowledging that these processes are often intricate for valid reasons.

**Interactive Modeling and Generative AI** focus on enhancing interactive modeling capabilities with proactive recommendations and validations powered by generative AI. This approach will enable business experts to input descriptions in natural language, which the system will interpret to generate process automations, forms, and decision-making frameworks. These generated artifacts can be reviewed and modified as necessary, streamlining the process of modeling complex business processes.

#### **2.3 SAP Automation Pilot (name subject to change)**

![MarioDeFelipe_15-1707576353222.png](https://community.sap.com/t5/image/serverpage/image-id/63616i97B42E1044318F9C/image-size/large?v=v2&px=999)
This is a capture from the video, but initially called**SAP Automation Pilot**, looks a significant addition to the BTP development and operations (DevOps) portfolio.

Check out at SAP

<https://assets.dm.ux.sap.com/webinars/sap-user-groups-k4u/pdfs/btp_unveiled_ai_vision_strategy.pdf>

#### 2.4 Combined with Fiori

There is quite significant research in Web Agents. A Web Agent, like the one described in paper "**WebVoyager: Building an End-to-End Web Agent with Large Multimodal Models,**" is an advanced artificial intelligence (AI) system designed to interact with the web and complete user instructions end-to-end.

![MarioDeFelipe_16-1707576353215.png](https://community.sap.com/t5/image/serverpage/image-id/63617i0223C435EBECD6A2/image-size/large?v=v2&px=999)
Key concept is to combine LLM like GPT4-V (Vision) with annotated HTML code from the webpages to augment the input and achieve the goal assigned to the Agent, in this case;

1. Open the Apple website.  

2. Search for "Smart Folio for iPad".  

3. Select the desired product.  

4. Click on "Check availability".  

5. Enter the zip code "90038".  

6. The closest pickup location is "Apple Tower Theatre".

![MarioDeFelipe_17-1707576353224.png](https://community.sap.com/t5/image/serverpage/image-id/63618iA3685F4A0955E03F/image-size/large?v=v2&px=999)
### MarioDeFelipe_18-1707576353005.png Additional Information on Agents

I will keep myself up to date with Agents in BTP, but if you are interested in Agents, I bring two *recent* papers;

The paper "**A Survey on Large Language Model-based Autonomous Agents**" by colleagues from Renmin University of China provides an in-depth review of the burgeoning field of autonomous agents powered by large language models (LLMs). It outlines how LLMs, with their ability to process vast amounts of web knowledge, are propelling these agents towards achieving human-level intelligence, marking a departure from traditional agent training methods limited by isolated environments and narrow knowledge bases. <https://arxiv.org/pdf/2308.11432.pdf>

"**The Rise and Potential of Large Language Model Based Agents: A Survey**" by colleagues from the Fudan NLP Group, dives into the evolution and potential of artificial intelligence (AI) agents powered by large language models (LLMs). The survey articulates the journey towards achieving Artificial General Intelligence (AGI) through AI agents—entities that perceive their environment, make decisions, and act upon them. It highlights the limitations of current approaches focused on algorithmic advancements and training strategies for specific tasks.

<https://arxiv.org/pdf/2309.07864.pdf>

I hope you like this; I read you in the comments!
