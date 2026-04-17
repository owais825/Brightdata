# NSE Stock Recommendation Agent

An AI-powered multi-agent system that provides short-term trading recommendations for Indian NSE-listed stocks using LangGraph and BrightData MCP.

## Architecture

The system uses a **supervisor-agent pattern** with four specialized agents orchestrated by a central supervisor:

| Agent | Role |
|---|---|
| `stock_finder_agent` | Identifies 2 promising NSE stocks based on performance, news, and volume |
| `market_data_agent` | Fetches real-time price, volume, trends, RSI, and moving averages |
| `news_analyst_agent` | Searches recent news (3–5 days) and classifies sentiment per stock |
| `price_recommender_agent` | Issues Buy/Sell/Hold recommendations with target entry/exit prices |

## Tech Stack

- **LLM:** `llama-3.3-70b-versatile` via [Groq](https://groq.com)
- **Orchestration:** [LangGraph](https://github.com/langchain-ai/langgraph) + `langgraph-supervisor`
- **Web Data:** [BrightData MCP](https://brightdata.com) via `langchain-mcp-adapters`
- **Framework:** LangChain

## Setup

### 1. Clone the repository

```bash
git clone <your-repo-url>
cd <repo-folder>
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

> **Note:** BrightData MCP requires Node.js. Ensure `npx` is available in your environment.

### 3. Configure environment variables

Create a `.env` file in the project root:

```env
GROQ_API_KEY=your_groq_api_key
BRIGHT_DATA_API_TOKEN=your_brightdata_api_token
```

### 4. Run the agent

```bash
python main.py
```

## Output

The system prints a structured recommendation for 2 NSE stocks including:
- Stock name and ticker
- Current price and trend
- News sentiment summary
- **Buy / Sell / Hold** action with a target price in INR

## Sample Output

![Agent Output]([Screenshot_2026-04-16_014333.png](https://github.com/owais825/Brightdata/blob/main/Screenshot%202026-04-16%20014333.png))

## Requirements

```
python-dotenv
langchain
langgraph
langchain-mcp-adapters
langchain-groq
langgraph_supervisor
```
