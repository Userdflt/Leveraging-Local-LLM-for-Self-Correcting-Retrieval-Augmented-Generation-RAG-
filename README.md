# **Self-Correcting Retrieval-Augmented Generation (RAG) with a Local LLM**

A system demonstrating **autonomous decision-making** to answer user questions, powered by a local vector store (Chroma DB) and optional web search. Through **reflection** and **hallucination checks**, it iteratively refines generated answers for higher accuracy.

![Diagram](flow_chart.jpeg)

[CLICK FOR NOTEBOOK - CODE](Local_RAG_LLM.ipynb)


## **Table of Contents**
1. [Overview](#overview)  
2. [Key Features](#key-features)  
3. [Technical Flow](#technical-flow)  
4. [Workflow Steps](#workflow-steps)  
5. [Summary](#summary)

---

## **1. Overview** <a id="overview"></a>
This project leverages a local Large Language Model (LLM) that autonomously decides whether to retrieve documents from a **local vector store** or perform a **web search**. After generating an initial answer, the system performs both **reflection** (to gauge completeness) and **hallucination checks** (to ensure factual correctness) before finalizing the response.

---

## **2. Key Features** <a id="key-features"></a>
- **Autonomous Decision-Making**  
  Routes user questions to local retrieval or web search based on context, via an `indicator` function.
- **Local Vector Store (Chroma DB)**  
  Efficiently stores and retrieves relevant documents for context.
- **Optional Web Search**  
  Gathers external data if the local store doesn’t suffice.
- **Reflection & Hallucination Checks**  
  Ensures answers remain accurate and complete.
- **Goal-Oriented Behavior**  
  Uses relevance grading and iterative refinement to achieve thorough responses.
- **State Graph Workflow**  
  Manages tasks (retrieval, generation, reflection) with conditional decisions and loops.

---

## **3. Technical Flow** <a id="technical-flow"></a>
1. **Indicator Function** – Routes the user’s question to local retrieval or web search.  
2. **Retrieval / Search** – Gathers relevant information from local vector storage or online sources.  
3. **Generation** – Drafts an initial answer using an LLM.  
4. **Reflection** – Evaluates completeness and may add missing details.  
5. **Hallucination Checking** – Screens for factual inaccuracies.  
6. **Regeneration** – Updates the context or re-generates the answer if necessary.

---

## **4. Workflow Steps** <a id="workflow-steps"></a>
1. **Autonomous Decision-Making**  
   The `indicator` function automatically routes queries to local or web-based retrieval.  
2. **Perception & Interaction**  
   - **Retrieval (Chroma DB)** – Scans the local vector store for relevant documents.  
   - **Web Search** – Executes search queries if local docs aren’t sufficient.  
3. **Action Execution**  
   - **Generation** – Produces an initial response from the LLM.  
   - **Reflection** – Checks for completeness.  
   - **Hallucination Checking** – Verifies factual correctness.  
4. **Goal-Oriented Behavior**  
   Continuously refines responses through reflection and relevance grading.  
5. **Adaptability**  
   Uses a state graph to loop back for re-generation when reflection deems the answer incomplete.

---

## **5. Summary** <a id="summary"></a>
This project showcases a **fully autonomous AI agent** that processes user inputs, retrieves or searches for context, and iteratively revises its answers. By combining **retrieval**, **generation**, **reflection**, and **hallucination checks**, it delivers thorough, context-rich responses aimed at achieving a specific goal with minimal human oversight.
