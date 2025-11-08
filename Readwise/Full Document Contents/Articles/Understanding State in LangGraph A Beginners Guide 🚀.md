# Understanding State in LangGraph: A Beginners Guide 🚀

![rw-book-cover](https://miro.medium.com/v2/resize:fit:1024/1*ViKq69OsDH7mLLPsiNpZQw.jpeg)

## Metadata
- Author: [[Rick Garcia]]
- Full Title: Understanding State in LangGraph: A Beginners Guide 🚀
- Category: #articles
- Summary: LangGraph is a tool for creating AI workflows that use the concept of "state" to track and manage information. Basic and complex state structures allow systems to remember details, such as conversation history or counts, while ensuring data remains immutable. Understanding state in LangGraph enables the development of more sophisticated and context-aware AI applications.
- URL: https://medium.com/@gitmaxd/understanding-state-in-langgraph-a-comprehensive-guide-191462220997

## Full Document
![An AI Generated picture of a parrot (LangChain Logo) with the words “Got State?” over it’s beak in a fun font.](https://miro.medium.com/v2/resize:fit:1400/1*ViKq69OsDH7mLLPsiNpZQw.jpeg)
LangGraph has emerged as a powerful tool for creating cyclical agentic AI workflows. One of the key concepts in LangGraph is the idea of “state” — a fundamental building block that allows our AI systems to maintain and manipulate information throughout the flow process.

In this article, we’ll cover the concept of state in LangGraph at an introductory level, exploring its implementation, manipulation, and practical applications.

The complete Python tutorial script is available for you at the bottom of this article👇. I’ll do my best to provide an educational walk-through of LangGraph state management in a easy to understand fashion.

### What is State in LangGraph?

State in LangGraph is a way to maintain and track information as an AI system processes data. Think of it as the system’s memory, allowing it to remember and update information as it moves through different stages of a workflow, or graph.

### 1. Basic State Definition

Let’s start with the simplest form of state in LangGraph:

```
from typing import TypedDict  
  
class BasicState(TypedDict):  
    count: int
```

This basic state definition creates a simple structure that can hold a single integer value, though it could be any value. While it may seem elementary, this type of state can be incredibly useful in many scenarios, such as:

* Tracking the number of turns in a conversation
* Counting the occurrences of a specific event
* Maintaining a simple score, metric, or AI output

### 2. Complex State Structures

As we move into more realistic applications, we often need more sophisticated state structures. LangGraph allows us to create complex states that can hold various types of information:

```
from typing import TypedDict, Annotated  
from langchain_core.messages import HumanMessage, AIMessage  
  
class ComplexState(TypedDict):  
    count: int  
    messages: Annotated[list[HumanMessage | AIMessage], add_messages]
```

This complex state not only tracks a count but also maintains a list of messages. The `Annotated` type provides additional metadata that LangGraph uses for special handling of message lists (Tuples). This structure is particularly useful for:

* Chatbots that need to remember conversation history
* AI assistants that maintain context over multiple interactions
* Systems that need to track both quantitative (count) and qualitative (messages) data

### 3. State Modification Functions

Once we have our state structures defined, we need ways to modify them. In LangGraph, we typically create new state objects rather than modifying existing ones, adhering to the principles of immutability:

```
def increment_count(state: BasicState) -> BasicState:  
    return BasicState(count=state["count"] + 1)  
  
def add_message(state: ComplexState, message: str, is_human: bool = True) -> ComplexState:  
    new_message = HumanMessage(content=message) if is_human else AIMessage(content=message)  
    return ComplexState(  
        count=state["count"],  
        messages=state["messages"] + [new_message]  
    )
```

These functions demonstrate how we can:

* Increment a counter in our basic state
* Add new messages to our complex state, distinguishing between human and AI messages
* Create new state objects that reflect these changes

### 4. Simple Graphs with State

Now that we understand the basics of state and how to modify it, let’s see how we can use state in a LangGraph:

```
from langgraph.graph import StateGraph, END  
  
def create_simple_graph():  
    workflow = StateGraph(BasicState)  
      
    def increment_node(state: BasicState):  
        return {"count": state["count"] + 1}  
      
    workflow.add_node("increment", increment_node)  
    workflow.set_entry_point("increment")  
    workflow.add_edge("increment", END)  
      
    return workflow.compile()
```

This simple graph demonstrates the fundamental structure of a LangGraph workflow:

1. We create a `StateGraph` using our `BasicState`.
2. We define a node function (`increment_node`) that modifies the state.
3. We add this node to our graph and set it as the entry point.
4. We create an edge from our node to the `END` of the graph.
5. Finally, we compile our workflow.

While this graph may seem basic, it serves as the foundation for more complex workflows.

### 5. Complex Graphs with State

Building on our understanding of somple graphs, let’s create a more advanced workflow:

```
def create_complex_graph():  
    workflow = StateGraph(ComplexState)  
      
    def process_message(state: ComplexState):  
        last_message = state["messages"][-1].content if state["messages"] else "No messages yet"  
        response = f"Received: {last_message}. Count is now {state['count'] + 1}"  
        return {  
            "count": state["count"] + 1,  
            "messages": state["messages"] + [AIMessage(content=response)]  
        }  
      
    workflow.add_node("process", process_message)  
    workflow.set_entry_point("process")  
    workflow.add_edge("process", END)  
      
    return workflow.compile()
```

This more complex graph showcases how we can:

* Use our `ComplexState` to maintain both a count and a message history
* Process incoming messages and generate responses
* Update our state with new information at each step

This type of graph could form the basis of a simple chatbot or AI assistant, demonstrating the power and flexibility of state in LangGraph.

Understanding and effectively using state in LangGraph opens up a world of possibilities for creating sophisticated, context-aware AI systems. From simple counters to complex conversational agents, the concept of state allows us to build AI workflows that can handle multi-step processes with ease.

As you continue to explore LangGraph, remember that mastery comes with practice. Don’t be afraid to experiment and see what you can create. The skills you’ve learned here will serve as a solid foundation as you build increasingly complex and powerful LangGraph workflows.

### Complete Python Script

Some content could not be imported from the original document. [View content ↗](https://medium.com/@gitmaxd/understanding-state-in-langgraph-a-comprehensive-guide-191462220997) 

I hope that you have found this article on LangGraph State Management helpful.

Please consider liking and sharing this content, and following me, [GitMaxd](https://x.com/gitmaxd) on X.
