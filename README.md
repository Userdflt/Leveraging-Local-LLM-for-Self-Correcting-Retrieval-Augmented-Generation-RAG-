# Leveraging Local LLM for Self-Correcting Retrieval-Augmented Generation (RAG)

![Diagram](mermaid-diagram-2024-09-11-202622.png)

[CLICK FOR NOTEBOOK - CODE](Local_RAG_LLM.ipynb)


It implements a system that autonomously performs a series of actions to answer user questions effectively.

1. **Autonomous Decision-Making**: The system decides whether to retrieve documents from a local vector store or perform a web search based on the user's question. This decision-making process is handled by the `indicator` function, which routes the question appropriately.

2. **Perception and Interaction with the Environment**:
   - **Retrieval**: It interacts with a local vector store (Chroma DB) to retrieve relevant documents based on the user's question.
   - **Web Search**: If necessary, it performs a web search to gather additional information.

3. **Action Execution**:
   - **Generation**: Uses a language model (LLM) to generate answers from the retrieved documents.
   - **Reflection**: Implements a reflection mechanism to assess the completeness and accuracy of the generated answer, potentially updating it with more information.
   - **Hallucination Checking**: Evaluates the generated answer for factual correctness, ensuring reliability.

4. **Goal-Oriented Behavior**: The agent's goal is to provide accurate and comprehensive answers to user questions. It employs strategies like relevance grading and reflection to improve the quality of its responses.

5. **Workflow Management**: Utilizes a state graph to manage the workflow of tasks, making conditional decisions and looping through processes like retrieval and generation as needed.

6. **Adaptability**: The system can adapt its actions based on the outcomes of previous steps (e.g., if the reflection step deems the answer incomplete, it will update the documents and regenerate the answer).

**Summary**: The project embodies the characteristics of an AI agent by autonomously processing user inputs, interacting with various data sources, making decisions, and generating outputs aimed at achieving a specific objective.
