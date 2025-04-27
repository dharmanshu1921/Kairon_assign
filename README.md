# 🌐 Deep Research AI Agentic System 🔎✨

An advanced AI-powered research and drafting assistant built using **LangGraph**, **LangChain**, **Tavily Search API**, and **Google Gemini 1.5 Flash**.

---

## 📌 Project Overview

The **Deep Research AI Agentic System** is a **dual-agent**, **streaming**, **graph-based AI assistant** that:

- 🔎 **Researches deeply** using real-time online sources.
- 📝 **Drafts professional, polished responses** suitable for reports or presentations.
- 🚨 **Handles errors smartly** during tool interactions.
- 📈 **Visualizes** the agent workflow as a graph.
- 📡 **Streams intermediate responses live** while maintaining full conversation state.

It is designed with **retries**, **tool fallback**, **memory-based checkpointing**, and **robust error handling**, ensuring clarity, resilience, and professional output.

---

## ⚙️ System Architecture

### 🧠 Research Agent

- Queries **Tavily Search** for the latest data.
- Uses a **structured research prompt**.
- **Routes** based on the need for tool use or direct drafting.

### 🛠️ Research Tools (ToolNode)

- Invokes **Tavily Search API** if tool usage is required.
- Handles tool errors gracefully via a **fallback mechanism**.

### ✍️ Draft Agent

- Converts research content into a **professional draft**.
- Follows **structured, formal writing guidelines** for polished output.

---

## 🛤️ Graph Workflow

The system workflow is modeled using **LangGraph**'s `StateGraph`.  
Visual representation:

![Workflow Graph](https://github.com/dharmanshu1921/Kairon_assign/raw/main/workflow_graph.png)

---

## 🚀 Key Features

- **🔴 Streaming Updates:** Real-time event-based output during workflow execution.
- **🛡️ Fallback for Tool Failures:** If Tavily fails, fallback logic manages errors smoothly.
- **💾 Memory Saver Checkpoints:** Saves and restores system state efficiently.
- **🔀 Dynamic Routing:** Intelligent decision-making between agents and tools.
- **📈 Graph Visualization:** Auto-generates a **Mermaid diagram**.
- **⚡ Error Handling:** Automatic retries and meaningful error feedback.
- **🔑 Environment Validation:** Secure loading of API keys from `.env`.

---

## 🏗️ Implementation Details

### 1. Environment Setup
- `.env` must contain:
  - `GEMINI_API_KEY`
  - `TAVILY_API_KEY`

### 2. Agents Setup
- Research and Draft prompts are built using **ChatPromptTemplate**.
- Agents are wrapped in a custom **Assistant** class for retries and fallback support.

### 3. Graph Creation
- **LangGraph** builds a **StateGraph** with:
  - Research Agent
  - Research Tools
  - Draft Agent
- Edges connect nodes based on conditions like tool invocation.

### 4. Tool Node with Fallback
- **ToolNode** wraps **Tavily Search API** and an error handler using `RunnableLambda`.

### 5. Visualization
- Generates a system graph using:

```python
graph.get_graph(xray=True).draw_mermaid_png()
```

### 6. Streaming Execution
- Streams events live and prints intermediate outputs after each step.
- Logs the final state at the end.

---

## Output

![Output](https://github.com/dharmanshu1921/Kairon_assign/blob/main/output.png)

---

## 🖥️ Tech Stack

| Technology         | Usage                                  |
|---------------------|----------------------------------------|
| Python 3.11+         | Core Language                        |
| LangGraph           | Agent graph orchestration             |
| LangChain           | LLM and tool interface                |
| Gemini 1.5 Flash    | LLM for responses                     |
| Tavily API          | Real-time search                      |
| dotenv              | Secure environment variable loading  |
| Pydantic            | State schema validation               |
| Logging             | Color-coded console logs             |
| Platform/OS         | Auto-opening generated images         |

---

## 🛡️ Important Design Decisions

- **Retries:** Each agent retries up to 3 times upon failure.
- **Tool Fallback:** Automatic fallback if Tavily search fails.
- **Max Length Management:** Limits streaming outputs to prevent console flooding.
- **User-Friendly Logs:** Color-coded for better CLI experience.
- **Input Validation:** Blocks empty or overly long user inputs.
- **Professional Draft Output:** Business-grade writing ensured.

---

## 🛠️ Setup Instructions

```bash
# 1. Clone the repository
git clone https://github.com/yourusername/deep-research-agentic-system.git
cd deep-research-agentic-system

# 2. Create and activate a virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# 3. Install the dependencies
pip install -r requirements.txt

# 4. Create a .env file
echo "GEMINI_API_KEY=your_gemini_api_key_here" > .env
echo "TAVILY_API_KEY=your_tavily_api_key_here" > .env

# 5. Run the system
python Dual_agent.py
```

---

## 📢 Future Improvements

- ✅ Dynamic API key management.
- ✅ Parallel tool execution support.
- ✅ Intermediate memory summarization.
- ✅ Multilingual research and draft capabilities.

---

## ✨ Final Note

This system demonstrates how **multi-agent workflows**, **tool integration**, and **error-tolerant designs** can be orchestrated into a scalable, modular, and production-ready **LangGraph** pipeline.
