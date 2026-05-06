from typing import TypedDict

class state(TypedDict):
    graph_state: str


def node(state: state):
    graph_state = state["graph_state"]
    print("this is a node")
    print("the graph state is {graph_state}")

from langgraph.graph import START, END, StateGraph 

builder = StateGraph(state)
builder.add_node('Node', node)
builder.add_edge(START, 'Node')
builder.add_edge('Node', END)

graph = builder.compile()

from ipython import display, image

display(image(graph.get_graph().draw_mermaid_png())) 

result = graph.invoke(input=('graph_state':'this is the graph_state'))

result

from typing import Literal
import random

def node1(state: state)-> state:
    graph_state = state("graph_state")
    print("this is node1")
    print("graph state: graph_state + "i am")

def node2(state: state)-> state:
    graph_state = state("graph_state")
    print("this is node2")
    print("graph state:" graph_state + "sad")

def node3(state: state)-> state:
    graph_state = state("graph_state")
    print("this is node3")
    print(""graph state" graph_state + "happy")    
    
def decide(state: state) -> Literal["node2","node3"]:
rand = random.random()
print("random number is," {rand})
if rand > 0.5:
    return "node2"
else:
    return "node3"

builder = StateGraph(state)
builder.add_node("node1", node1)
builder.add_node("node2", node2)
builder.add_node("node3", node3)


builder.add_edge(START, "node1")
builder.add_conditional_edge("node1", decide)
builder.add_edge("node2", END)
builder.add_edge("node3", END)  

graph = builder.compile() 

display(image(graph.get_graph().draw_mermaid_png()))

result = graph.invoke(input={'graph_state':"hi chibueze"})

result

from dotenv import load_dotenv
import os

load_dotenv

os.getenv("openai_api_key")

from langchain_openai import ChatOpenAI

llm = ChatOpenAI(model="gpt-3.5-turbo",api_key=os.getenv("openai_api_key"), temperature=0.9)



