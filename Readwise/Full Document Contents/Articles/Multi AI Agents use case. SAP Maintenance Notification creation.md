# Multi AI Agents use case. SAP Maintenance Notification creation

![rw-book-cover](https://readwise-assets.s3.amazonaws.com/media/uploaded_book_covers/profile_1492393/SAP_R_grad_200x200_C9NhLeS.png)

## Metadata
- Author: [[MarioDeFelipe]]
- Full Title: Multi AI Agents use case. SAP Maintenance Notification creation
- Category: #articles
- Summary: This blog discusses how AI agents can assist Mary, a Maintenance Manager, in creating Maintenance Notifications in SAP. It outlines the use of a framework called Crew AI, which allows multiple AI agents to collaborate on tasks using specific goals and tools. The author emphasizes the importance of combining human expertise with AI capabilities to enhance efficiency in maintenance processes.
- URL: https://community.sap.com/t5/artificial-intelligence-and-machine-learning-blogs/multi-ai-agents-use-case-sap-maintenance-notification-creation/ba-p/13608309

## Full Document
The SAP Citizen Reporting App published at Github for Generative AI use cases is a great example of an application that will retrieve social media posts, processing through extraction and summarising capabilities of the LLM of SAP GenAI Hub, all the way to the outcome – which could be a Maintenance Notification transaction in SAP S/4HANA.

![Source: SAP](https://community.sap.com/t5/image/serverpage/image-id/66695i67854823FD2B10A4/image-size/large?v=v2&px=999)
The Citizen Reporting App is LLM powered and automated but keeps a human in the loop called Mary.

In this blog, I will focus on Mary, the Maintenance Manager, and we will try to AI enhance Mary's task of creating a Maintenance Notification using AI Agent capability.

The use case for AI Agents is to perform actions like humans do. For that, Agents use a combination of;

1. Goal
2. Knowledge
3. Tools
4. Thoughts (Actions)

More details can be found in [this blog post](https://community.sap.com/t5/artificial-intelligence-and-machine-learning-blogs/agents-is-the-most-important-btp-release-this-2024/ba-p/13601686)

In this blog, we will create a few AI Agents that will need to work together; for this, I will use a framework to create AI Agents that allows me to be combined; I decided to use Crew AI but all this can be achieved on other frameworks such as Langchain, and soon on **SAP** **Generative AI Hub**, and dramatically enhanced with **SAP Build Process Automation**.

At its core, the Crew AI framework enables the creation groups of **AI Agents** called **Crews**, each Agent with its own expertise and set of instructions. These agents collaborate to solve complex problems, as a Crew would do.

Crew AI uses a combination of

1. Tasks (Goal)
2. Tools (usage of *Langchain Tools)*
3. Agents (Knowledge)
4. Process (Thoughts/Actions)

![Captura de pantalla 2024-02-18 a las 11.50.46.png](https://community.sap.com/t5/image/serverpage/image-id/67127i12D98E8294ACEB00/image-size/large?v=v2&px=999)
That's a lot of information, I will explain it below, but the concept is the same; depending on the framework, they call it some way or another, no matter if you use AutoGen or LangServe. It is a little bit different from SAP Build Process Automation, though, as here we leverage and constantly use the power of LLMs to use word-based instructions and AI reasoning capabilities.

Although there will be some code in this blog, I removed fundamental parts of the code so we focus on the concept and not on "click and run." if interested, I will publish a GitHub repo with the SAP Maintenance Notification Agents.

Lets see how Crew looks like;

```
from crewai import Agent, Task, Crew, Process 
from langchain.agents import Tool 

# Define an agent with a role and a goal 
Mary_Maintenance_Manager = Agent( 
role='SAP Maintenance Manager', 
goal='The goal of an SAP Maintenance Manager is to ensure the proper functioning, availability, and optimal maintenance of assets. You will receive a Damage Notification and will decide if you open an SAP Maintenance Notification for that particular Equipment', 

# Instantiate your crew with a sequential process 
crew = Crew( 
agents=[agent1, agent2], 
tasks=[task1, task2], 
# Get your crew to work! 
result = crew.kickoff() 
print(result) 
```

We define a **Crew()**. A Crew represents a collaborative group of agents working together to achieve a set of tasks. Each crew defines the strategy for task execution, agent collaboration, and the overall workflow.

Now you understand the concept, we will break down into pieces of Agents, Tools, Task and Processes. Similarly, Langchain has wrapped all these actions on a library called LangGraph, but I found it way more complicated than CrewAI, although they can be easily combined on our notebooks.

**1️⃣ Agents**

An agent is an **autonomous unit** programmed to:

* Perform Tasks
* Make decisions
* Communicate with other agents

Think of an agent as a team member with specific skills and a particular job to do. The most important attributes are the Goals and Tools. Goals is a particular objective of the agent, its a description on why we are going to use this agent for, the unique objective of this agent, and Tools are the utilities that this Agent can use, in our SAP world, Tools will be the SAP APIs this particular agent may use.

Now, let's discuss the components of creating an Agent: the role, backstory, and goal. The role simply defines the job title of the agent. The goal should be specific, indicating what the agent aims to achieve. As for the backstory, it should support the goal, providing context and depth to the agent's identity. I found it a little bit redundant in the beginning, but think about it: you don't want to be highly specific on Goal, but you can be more specific on BackStory.

![Captura de pantalla 2024-02-17 a las 6.01.13.png](https://community.sap.com/t5/image/serverpage/image-id/66759i4858DD2092BCABA4/image-size/large?v=v2&px=999)
First and foremost, every agent should be results-driven. Without this focus, we risk receiving unreliable outcomes, leading to frustration. It's crucial to establish clear goals for each agent. These goals serve as their guiding purpose, ensuring they consistently produce desired outcomes.

**What would be the equivalent of an Agent in SAP Plant Maintenance?**

In facilities, we have maintenance planners, workshop managers, IT experts, field engineers, and **Mary**, our maintenance manager.

Mary's task as an SAP Maintenance Manager primarily involves overseeing Plant Maintenance activities, managing the budget and costs associated with maintenance, and supervising the maintenance department within an organization.

* Monitor all maintenance activities and ensure they are executed effectively.
* Controlling the maintenance budget and costs arising from maintenance activities.
* Managing all employees in the maintenance department, including recruitment decisions and task assignments to service providers and suppliers.
* Supervising the maintenance engineer, maintenance planner, maintenance supervisor, and technicians in the company hierarchy.
* Ensuring that maintenance operations are planned and executed efficiently based on pending loss statistics and maintenance demands.

Mary, then, must take **Actions** based on **Reasoning**, using given **Tools**, and being provided with accurate **Information**.

In SAP, we can enter an order for a technical object (functional location or piece of equipment) and perform a time confirmation; we can also perform planned and unplanned material withdrawals, as well as specify downtimes, completion confirmation texts, and causes of damage using remote function calls, previously BAPIs, now OData.

An API, then, is used to transfer the data to the SAP system and post it there (e.g., the OrderMaint BAPI or [API\_MAINTNOTIFICATION](https://api.sap.com/api/OP_API_MAINTNOTIFICATION/overview)).

![Captura de pantalla 2024-02-18 a las 12.13.30.png](https://community.sap.com/t5/image/serverpage/image-id/67141iB47934FF4D19CEB2/image-size/large?v=v2&px=999)
SAP provides the following some APIs for Mary's EAM day-to-day duties, summarized as;

1. For equipment, **Equipment** has methods such as *Create* to create equipment master records or Dismantle to dismantle equipment from functional locations or equipment hierarchies.
2. Functional locations, ***FunctionalLocation*** with methods such as *InheritChange* to change the inheritance parameters or *StrucAssign* to replace the assignment of superior functional locations.
3. For Notifications, ***MaintNotificBAPIs*** use *NotifCreate* to create notifications or *NotifListPlangroup* to create notification lists for each planner group.
4. For orders, ***MaintenanceOrderBAPI*** uses methods, such as *OrderMaintain*, to create and change orders.
5. For confirmations, ***MaintOrdConfirmation*** uses methods, such as *ConfCreate*, to create completion confirmations.
6. For material master records, ***Material*** has methods, such as *Edit* to change material master data or *GetMRPList* to generate the MRP list for a material.
7. Finally, for bills of material, **Material BOM** has methods, such as *CreateBomGroup*, to generate material BOMs.

Then it makes sense that our Maintenance Manager is, in reality, a Crew of (**7+1**) AI Agents , and today, Mary is interested in creating a Maintenance Notification, just that! It looks easy, but there is never an easy thing in SAP.

![Captura de pantalla 2024-02-17 a las 14.31.53.png](https://community.sap.com/t5/image/serverpage/image-id/66922i77080344882832C4/image-size/large?v=v2&px=999)
As we define the tasks for each agent, it's crucial to be highly descriptive and provide clear instructions. Let's take a step back from AI for a moment and consider hiring someone to do a job for you. You'd want to provide step-by-step instructions, leaving nothing to guesswork. The **goal** is to be crystal clear, just as if you were hiring an employee.

In our case, let me introduce AI Agent Jurgen, Jurgen's goal as an Agent is to create a Maintenance Notification. In SAP, a Maintenance Notification is a central element that records a maintenance task. Recording Maintenance Notification documents and stores information such as equipment breakdowns, preventive maintenance, and inspections. It's an input-output activity.

How Jurgen looks like on code;

```
from crewai import Agent 
from langchain.agents import Tool

jurgen_Maintenance_notification_agent = Agent( 
role='Maintenance Notification Expert', 
goal='your goal is recording Maintenance Tasks. A Maintenance Notification documents and stores information about maintenance activities, such as equipment breakdowns, preventive maintenance, and inspections. You provide a basis for planning and executing maintenance tasks, allowing for better organization and scheduling of maintenance activities. You provide a header containing information for identifying and managing maintenance tasks. You can help in identifying trends and patterns in maintenance activities.', 
tools=[NotifCreate , NotifGetDetail] 
) 
```

As simple as it looks, we have a Role, a Goal, and some Tools. In reality, we have 8 tools for Jurgen, we'll go through this later. The concept is that we dont decide when Jurgen needs to access one tool or another, he will pick whatever the Tool he needs to accomplish its Task.

**2️⃣ Tools**

Tools are interfaces that an AI Agent will use to interact, in our case, with SAP APIs. Tools combine a few things:

1. The name of the tool
2. A description of what the tool is
3. JSON schema of what the inputs to the tool are
4. The function to call
5. Whether the result of a tool should be returned directly to the user

The name, description, and JSON schema are all used in the prompt to the LLM. Therefore, they must be clear and describe precisely how the tool should be used. Unlike creating Agents, Tasks or Processes, you must have phyton knowledge to be able to generate Tools. We will need to build our tools since we will use SAP APIs. Let's see what a Tool looks like; more information is available on [this link;](https://python.langchain.com/docs/modules/agents/tools/custom_tools)

API parameters are:

* **NOTIF\_TYPE: Notification Type (mandatory)**
* **NOTIFHEADER: Service Notification for Creation (mandatory)**
* EXTERNAL\_NUMBER: Notification Number (optional)
* TASK\_DETERMINATION: Indicator (optional)
* SENDER: Logical System of Sender (optional)
* ORDERID: Order Number (optional)

***Notification Type, Functional Location, Equipment*** and ***Customer*** are the parameters we must know to do a Maintenance Notification; here is how this would look like to create a custom tool with the specified parameters. for maximum control, we must implement a class that inherits from the `*BaseTool*` and *BaseModel* classes provided by LangChain and Pydantic. Don't use @tool decorator for our SAP tools, as we need maximum control over the arguments for the input and the output. APIs in SAP are quite strict.

```
import requests
from pydantic import BaseModel
from langchain.tools import BaseTool

class NotifCreate(BaseTool):
    name = "NotifCreate"
    description = "Create a Maintenance Notification in SAP with the given arguments."

    def __init__(self):
        self.api_url = "https://s4hana-api-endpoint.com/maintenance_notifications"

    def _run(self, notification_type: str, functional_location: str, equipment: str, customer: str) -> str:
        notification_data = {
            "notification_type": notification_type,
            "functional_location": functional_location,
            "equipment": equipment,
            "customer": customer
        }

        notification = MaintenanceNotification.parse_obj(notification_data)

        response = requests.post(self.api_url, json=notification.dict())

        if response.status_code == 200:
            return f"Successfully created the maintenance notification with header: {response.headers['Location']}"
        else:
            return f"Error creating maintenance notification: {response.status_code}"

# Define the Pydantic model for the Maintenance Notification
class MaintenanceNotification(BaseModel):
    notification_type: str
    functional_location: str
    equipment: str
    customer: str

# Example usage
tool = NotifCreate()
header = tool.run("Equipment Malfunction", "Warehouse 1", "Forklift 001", "ABC Corp")
print(header)
```

The **`\_run`** method is where we would implement the logic to call the API function and process the results. In this example, it simply returns a string equivalent with the provided parameters equivalent to NOTIFHEADER\_EXPORT.

![Captura de pantalla 2024-02-18 a las 8.05.16.png](https://community.sap.com/t5/image/serverpage/image-id/67053i40CF8F78EA422D28/image-size/large?v=v2&px=999)
Tools have Descriptions, which will help Agent Jurgen know when he should use them. Descriptions must be detailed, and each tool must be deterministic so the output is relevant for the Agent. We create one Tool for every SAP API call we might use. This is another major difference with RPAs like SAP Build Process Automation, we will not be deterministic, Agents (which are powered with an LLM like GPT4) will decide which tool they use whenever they feel necessary, Agents know what they are assigned to accomplish and they will access their toolbox to see if they have a tool which can help them achieve their task, or they give up.

### **3️⃣** **Tasks**

Tasks are jobs or assignments that an agent needs to complete.

They encapsulate necessary information for execution, including a description, assigned agent, and required tools, offering flexibility for various action complexities.

![Captura de pantalla 2024-02-17 a las 15.07.18.png](https://community.sap.com/t5/image/serverpage/image-id/66933i81E917F561DE3462/image-size/large?v=v2&px=999)
The concept of Tasks can be Human generated or AI Generated, in other words, the Tasks will come from an instruction, is what we want the Crew or an Agent to complete, like take into consideration this, and that and that.

Here is what one of the Tasks looks like in our Maintenance Notification; this is the Task that Mary gave Jurgen.

```
from crewai import Task

NotifCreate = Task(
	description='Create a new notification. Here you have specific fields for your notification header, the Item is a pipe A405, cause is Corrosion, use the default Partner Data and if you receive an error on the response, try again two more times or return me an error',
	agent=jurgen_maintenance_notification
)
```

Who will give all this information? Probably Mary, because she will receive that information from the field, Mary can send a voice note to the software, and that note voice will be translated into Tasks.

But how all this information will be given to Jurgen? because Mary will know all that information, and Mary knows she must give clear and concise instructions to Jurgen to achieve its completion. This is what supervisors do because they have access to more high-level information than Jurgen does.

If Jurgen returns and says it can't achieve the task because it's missing the Functional Location, Mary will bring Hasso to retrieve it before informing Jurgen.

In each task, we designated which **agent** was responsible for its execution. However, we did not explicitly specify the tools each agent could use. This is where the inherent capabilities of Crew AI come into play. Crew AI autonomously determines the most appropriate tools to accomplish its tasks.

At this point, we will be very recommended to use **SAP BTP Services, specially SAP Build Process Automation** to maintain all the integration and access to SAP services. On the BTP, we can create a machine-learning model to identify maintenance tasks that need to be done, for example, a model that analyzes asset maintenance history and predicts the next maintenance task; for this, more data must be analyzed; this cant be done in the context of an Agent capability, a Model must be used.

### 4️⃣Process

Process is another of the areas where SAP expertise is crucial, for example, for Predictive Maintenace. The reality is that we must collect much information to determine when maintenance is needed.

Mary will know all the necessary outputs of its subordinate Agents to coordinate the subsequent actions to take.

![Captura de pantalla 2024-02-17 a las 17.38.43.png](https://community.sap.com/t5/image/serverpage/image-id/66946i89A534B1591D59BD/image-size/large?v=v2&px=999)
The cornerstone of Crew AI will be on its process management because it outlines the collaborative framework for the agents. The process determines how tasks are allocated among agents and facilitates their coordination. It acts as the binding force to ensure all necessary tasks are completed efficiently.

You can define the workflow to be **sequential**, where each agent completes its tasks before passing the baton to the next one or ***hierarchical,*** where process go up to a supervising model to decide what happens next.

![Captura de pantalla 2024-02-18 a las 6.18.23.png](https://community.sap.com/t5/image/serverpage/image-id/67015i8B8C8F086429811E/image-size/large?v=v2&px=999)
Looks like this;

```
from crewai import Agent, Task, Crew, Process

# Define agents with roles and goals
mary_sap_maintenance_manager = Agent(
    role='SAP Maintenance Manager',
    goal='Oversee the maintenance process and delegate tasks',
    backstory="""You are an experienced SAP maintenance manager, skilled in coordinating complex maintenance tasks.""",
    verbose=True,
    allow_delegation=True,
    tools=[search_tool]
)
jurgen_maintenance_notification = Agent(
    role='Maintenance Notification Agent',
    goal='Handle maintenance notifications and coordinate with the SAP Functional Location agent',
    backstory="""You are a skilled maintenance notification agent, responsible for managing and coordinating maintenance notifications.""",
    verbose=True,
    allow_delegation=False,
    tools=[bapi_alm_maintenance_notification]
)
hasso_sap_functional_location = Agent(
    role='SAP Functional Location Agent',
    goal='Manage SAP functional locations and provide maintenance insights',
    backstory="""You are an expert in SAP functional locations, skilled in analyzing and providing insights for maintenance tasks.""",
    verbose=True,
    allow_delegation=False,
    tools=[getStatus,Create]
)

# Define tasks for agents
task1 = Task(
    description="""Analyze maintenance notifications and provide insights for SAP functional locations.""",
    agent=hasso_sap_functional_location
)
task2 = Task(
    description="""Coordinate maintenance notifications and delegate tasks to the SAP Functional Location agent.""",
    agent=jurgen_maintenance_notification
)
manager_task = Task(
    description="""Coordinate the maintenance process and delegate tasks to the Maintenance Notification and SAP Functional Location agents.""",
    agent=mary_sap_maintenance_manager
)

# Instantiate your crew with a hierarchical process
crew = Crew(
    agents=[mary_sap_maintenance_manager, jurgen_maintenance_notification, hasso_sap_functional_location],
    tasks=[manager_task, task1, task2],
    process=Process.hierarchical,
    manager_llm=llm  # default GTP4
)

# Get your crew to work!
result = crew.kickoff()
print("######################")
print(result)
```

**Conclusion**

In this blog, I wanted to go to a particular use case for AI Agents in an SAP Scenario where we need a real person, Mary, to be more effective in one of her duties: Creating a Maintenance Notification in SAP.

Creating a Maintenance notification requires a process that can be coded in the modern AI Agents framework; I chose Crew to do it, but this can be moved to Generative AI Hub once we have the opportunity to do it.

The core components of a Multi-Agent scenario that I introduce are Agents, Tasks, Tools, and Processes, where we will be able to define all the logic we require for our company and the expertise we have gathered over the years in SAP to accomplish a task.

Mary will be fundamental to creating this Agent because Mary has the expertise in creating previous Maintenance Notifications, but the magic of AI is that her expertise, as we have seen, will be introduced in natural language to the Process part.

Now, Mary has software that can help her automate one activity (creating a Maintenance Notification on a S/4HANA Cloud), and she also has software that reasons the same way she wants it to reason. Mary can introduce as much knowledge as she wants to explain what Thoughs must happen to decide what Actions must be taken (here, tasks) before a Maintenance Notification is created or discarded.

SAP, a System Integrator or IT corporate department, brings our knowledge on the matter to give Mary the necessary Agents and Tools to make this task achievable. We have software that uses a powerful LLM to get the required output. This software interacts with other data sources, processes the outputs of queries, takes decisions, and brings humans like real Mary in the loop, if necessary, to accomplish its goal autonomously.

If you have already worked with SAP iRPA, now SAP Build Process Automation, this integration might help to provide a new capability to an automated process, adding an LLM intelligence to it while leaving the integration, workflow, and business rules to **Process Automation**.
