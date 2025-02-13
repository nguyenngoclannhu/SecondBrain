# Multi AI Agents use case. SAP Maintenance Notification creation

![rw-book-cover](https://readwise-assets.s3.amazonaws.com/media/uploaded_book_covers/profile_1492393/SAP_R_grad_200x200_C9NhLeS.png)

## Metadata
- Author: [[MarioDeFelipe]]
- Full Title: Multi AI Agents use case. SAP Maintenance Notification creation
- Category: #articles
- Summary: This blog discusses how AI agents can assist Mary, a Maintenance Manager, in creating Maintenance Notifications in SAP. It outlines the use of a framework called Crew AI, which allows multiple AI agents to collaborate on tasks using specific goals and tools. The author emphasizes the importance of combining human expertise with AI capabilities to enhance efficiency in maintenance processes.
- URL: https://community.sap.com/t5/artificial-intelligence-and-machine-learning-blogs/multi-ai-agents-use-case-sap-maintenance-notification-creation/ba-p/13608309

## Highlights
- Crew AI uses a combination of
  1. Tasks (Goal)
  2. Tools (usage of *Langchain Tools)*
  3. Agents (Knowledge)
  4. Process (Thoughts/Actions) ([View Highlight](https://read.readwise.io/read/01jkqnk7dz83wb701qc02yqy82))
- Goals is a particular objective of the agent, its a description on why we are going to use this agent for ([View Highlight](https://read.readwise.io/read/01jkqnmb3psdjytygj9eskhvzs))
- Tools are the utilities that this Agent can use, ([View Highlight](https://read.readwise.io/read/01jkqnmj067prced9qrtae9014))
- The goal should be specific, indicating what the agent aims to achieve ([View Highlight](https://read.readwise.io/read/01jkqnnet2vhgph80kh2v5yw9n))
- ackstory, it should support the goal, providing context and depth to the agent's identity ([View Highlight](https://read.readwise.io/read/01jkqnnm9h0taf53ffsq97jjmf))
- every agent should be results-driven. ([View Highlight](https://read.readwise.io/read/01jkqnp9vtyjv1yxggrj6d5x3t))
- establish clear goals for each agent. These goals serve as their guiding purpose, ensuring they consistently produce desired outcomes. ([View Highlight](https://read.readwise.io/read/01jkqnpn8ebe3emxs3tk5xeesy))
- This is another major difference with RPAs like SAP Build Process Automation, we will not be deterministic, Agents (which are powered with an LLM like GPT4) will decide which tool they use whenever they feel necessary ([View Highlight](https://read.readwise.io/read/01jksqadvbr70qj2mk1k3er53x))
    - Note: what is the difference?
- Tools are interfaces that an AI Agent will use to interact, in our case, with SAP APIs. Tools combine a few things:
  1. The name of the tool
  2. A description of what the tool is
  3. JSON schema of what the inputs to the tool are
  4. The function to call
  5. Whether the result of a tool should be returned directly to the user ([View Highlight](https://read.readwise.io/read/01jkqns1rd4ccr6p0v4egwjpx5))
- Tasks are jobs or assignments that an agent needs to complete. ([View Highlight](https://read.readwise.io/read/01jkqnwn65srrt04dz69k82hwm))
- like take into consideration this, and that and that. ([View Highlight](https://read.readwise.io/read/01jkqnxdc2feb01g3e0sydssmf))
- rew AI autonomously determines the most appropriate tools to accomplish its tasks. ([View Highlight](https://read.readwise.io/read/01jkqnz3c1w4997z71tm75mtry))
- recommended to use **SAP BTP Services, specially SAP Build Process Automation** to maintain all the integration and access to SAP services. ([View Highlight](https://read.readwise.io/read/01jkqnzgxkwt1ab8dtvtkvgxjc))
- process determines how tasks are allocated among agents and facilitates their coordination. It acts as the binding force to ensure all necessary tasks are completed efficiently. ([View Highlight](https://read.readwise.io/read/01jkqp23qvhackxc566ds325ft))
- **sequential**, where each agent completes its tasks before passing the baton to the next one ([View Highlight](https://read.readwise.io/read/01jkqp2ag655sv8f1x1qb9qp0z))
- ***hierarchical,*** where process go up to a supervising model to decide what happens next. ([View Highlight](https://read.readwise.io/read/01jkqp2fqqd4bg44ntv80e6d44))
