### Deep Research AI Agentic System 🔎✨
An advanced AI-powered research and drafting assistant built using LangGraph, LangChain, Tavily Search API, and Google Gemini 1.5 Flash.

## 📌 Project Overview
The Deep Research AI Agentic System is a dual-agent, streaming, graph-based AI assistant that:

Researches deeply using real-time online sources.

Drafts professional, polished responses suitable for reports or presentations.

Handles errors smartly during tool interactions.

Visualizes the agent workflow as a graph.

Streams intermediate responses live while maintaining full conversation state.

It is designed with retries, tool fallback, memory-based checkpointing, and error handling, ensuring robustness, clarity, and professional output.

## ⚙️ System Architecture
# Agents and Nodes:

# 🧠 Research Agent:

Queries Tavily Search for latest data.

Uses a structured research prompt.

Routes based on the need for tool use or drafts.

# 🛠️ Research Tools (ToolNode):

Invokes Tavily Search API if tool calls are detected.

Handles tool errors gracefully with a fallback mechanism.

# ✍️ Draft Agent:

Takes research content and transforms it into a professional draft.

Structured, formal, polished writing based on given guidelines.

## Graph Workflow:



## 🚀 Key Features
Streaming Updates: Real-time event-based output during the workflow.

Fallback for Tool Failures: If Tavily fails, fallback logic gracefully handles the error.

Memory Saver Checkpoints: Saves state between steps with MemorySaver.

Dynamic Routing: Routes between tools and agents based on message structure.

Graph Visualization: Generates a Mermaid diagram and opens the graph image automatically.

Error Handling: Retries if an agent fails and provides meaningful error messages.

Environment Validation: Safely loads API keys from .env and throws errors if missing.

## 🏗️ Implementation Details
# 1. Environment Setup
.env must contain GEMINI_API_KEY.

TAVILY_API_KEY is hardcoded for demo (you should replace it with env variable for production).

# 2. Agents Setup
Research and Draft prompts are designed using ChatPromptTemplate.

Agents are wrapped inside a custom Assistant class that adds retries and fallback on empty responses.

# 3. Graph Creation
LangGraph is used to create a StateGraph.

Three main nodes: Research Agent, Research Tools, Draft Agent.

Edges connect nodes based on conditions like tool calls.

# 4. Tool Node with Fallback
ToolNode wraps around Tavily Search and a fallback error handler using RunnableLambda.

# 5. Visualization
graph.get_graph(xray=True).draw_mermaid_png() generates a visual PNG of the system workflow.

# 6. Streaming Execution
Events are streamed with live output printed after each step.

Final state is logged at the end.

## 🖥️ Tech Stack

Technology	Usage
Python 3.11+	Core Language
LangGraph	Agent graph orchestration
LangChain	LLM and tools interface
Gemini 1.5 Flash	LLM for responses
Tavily API	Real-time search
dotenv	Secure environment variable loading
Pydantic	State schema validation
Logging	Color-coded logs
Platform/OS	Auto-opening images

## 🛡️ Important Design Decisions
Retries: Agent retries up to 3 times on failure to improve reliability.

Tool Fallback: If Tavily search fails, fallback error response is automatically injected.

Max Length Management: Limits streaming output length to avoid flooding console.

User-Friendly Logs: Custom logs in color format for better CLI experience.

Input Validation: Validates user queries (empty or overly long inputs are blocked).

Professional Draft Output: Ensures the final output is suitable for business settings.

📸 Demo Screenshots
(You can add a few screenshots of your CLI outputs here — like when the system is searching, drafting, or visualizing the graph.)

## 🛠️ Setup Instructions
bash
Copy
Edit
# 1. Clone the repository
git clone https://github.com/yourusername/deep-research-agentic-system.git
cd deep-research-agentic-system

# 2. Create and activate a virtual environment
python -m venv venv
source venv/bin/activate  # On Windows, use venv\Scripts\activate

# 3. Install the dependencies
pip install -r requirements.txt

# 4. Create a .env file
echo "GEMINI_API_KEY=your_gemini_api_key_here" > .env

# 5. Run the system
python main.py

## 📢 Future Improvements
✅ Use dynamic configurable API keys (Tavily from env).

✅ Add parallel tool execution (for multiple tools at once).

✅ Introduce intermediate memory summarization for long sessions.

✅ Support multilingual research and drafts.

## ✨ Final Note
This system showcases how multi-agent workflows, tool integration, and error-tolerant designs can be orchestrated into an elegant LangGraph pipeline.
It is scalable, modular, and ready for further real-world production use!
