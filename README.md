# MCP Server Project

## Overview
This project is a multi-server agent system built with LangChain, LangGraph, and MCP (Model Context Protocol) adapters. It demonstrates how to connect multiple tool servers (Math and Weather) to a central agent powered by an LLM (DeepSeek ).

## Components
- **client.py**: The main orchestrator script. It loads environment variables, connects to math and weather servers, loads available tools, and runs a conversational agent using an LLM. The agent can answer math and weather questions by invoking the appropriate tool server.
- **mathserver.py**: Provides math tools (addition and multiplication) via MCP protocol. The agent can call these tools to solve math problems.
- **weather.py**: Provides a weather tool via MCP protocol. The agent can call this tool to answer weather-related queries (currently returns a static response).

## How It Works
1. The math and weather servers are started (each in their own process or terminal).
2. The client script connects to both servers using MCP adapters.
3. The client loads available tools from both servers.
4. The agent (powered by DeepSeek) receives user questions and decides which tool to use (math or weather) to answer them.
5. The agent prints the responses for math and weather queries.

## Usage
1. Install dependencies from `requirements.txt`.
2. Set your API key in the `.env` file (e.g., `DEEPSEEK_API_KEY` ).
3. Start the weather server:
   ```pwsh
   D:/MCP_server/.venv/Scripts/python.exe weather.py
   ```
4. Start the math server:
   ```pwsh
   D:/MCP_server/.venv/Scripts/python.exe mathserver.py
   ```
5. Run the client:
   ```pwsh
   D:/MCP_server/.venv/Scripts/python.exe client.py
   ```

## Example
- Math: "what's (3 + 5) x 12?"
- Weather: "what is the weather in California?"

## Extending
- Add more tools to `mathserver.py` or `weather.py`.
- Replace the LLM in `client.py` with any supported provider.
- Update tool logic for real data sources.

# langchain-mcp-multitool
