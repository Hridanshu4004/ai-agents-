# 🤖 Build AI Agents from Scratch

📺 **YouTube Tutorial:** [Watch the full video here](https://www.youtube.com/@AI.with.Hassan/featured)

---

## Overview

Learn how to build an AI Agent from scratch using Python — no frameworks, no magic, just clean code. This project demonstrates how to create a tool-calling agent (`JarvisAgent`) that can autonomously decide when to invoke external tools (like a weather API) and incorporate the results into its responses.

## How It Works

1. **User sends a query** — e.g., *"What is the temperature in Tokyo today?"*
2. **The agent forwards it to an LLM** (via Groq) with a list of available tools.
3. **The LLM decides** whether to call a tool or respond directly.
4. **If a tool is called**, the agent executes it locally, sends the result back to the LLM, and lets it generate the final answer.
5. **The loop continues** until the LLM produces a final text response (no more tool calls).

## Architecture Diagram

See the visual overview of how the agent works in the [intro-to-aiagents.excalidraw](intro-to-aiagents.excalidraw) file. You can open it with [Excalidraw](https://excalidraw.com/) or the VS Code Excalidraw extension.

## Project Structure

```
├── main.py                        # Agent logic + tool definitions + entry point
├── intro-to-aiagents.excalidraw   # Architecture diagram
├── pyproject.toml                 # Project metadata & dependencies
├── README.md
└── .env                           # Your API keys (not committed)
```

## Prerequisites

- Python 3.11+
- A [Groq API key](https://console.groq.com/)

## Setup

1. **Clone the repo**

   ```bash
   git clone https://github.com/<your-username>/ai-agents-from-scratch.git
   cd ai-agents-from-scratch
   ```

2. **Install dependencies**

   ```bash
   pip install groq python-dotenv
   ```

3. **Create a `.env` file** in the project root

   ```
   GROQ_API_KEY=your_groq_api_key_here
   ```

4. **Run the agent**

   ```bash
   python main.py
   ```

## Example Output

```
Response from Alex: The current temperature in Tokyo today is 73°F.
```

## Key Concepts

| Concept | Description |
|---|---|
| **Agentic Loop** | The agent keeps calling the LLM in a loop until it gets a final text response (no pending tool calls). |
| **Tool / Function Calling** | Tools are defined as JSON schemas and passed to the LLM. The model decides when and how to invoke them. |
| **Dynamic Dispatch** | Tool functions are resolved at runtime using `globals()`, making the system easily extensible. |

## Tech Stack

- **Python** — Core language
- **Groq SDK** — LLM inference
- **python-dotenv** — Environment variable management

## License

This project is open-source and available for educational purposes.
