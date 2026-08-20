# Real-Time Transaction Risk Detector

A multi-agent fraud detection system built with LangGraph. Analyzes transactions in real time and flags suspicious activity for human review.

## How it works

1. **Transaction Analyst** — checks amount anomalies (spikes, high-value, velocity)
2. **Behavioral Profiler** — checks device, location, and destination anomalies
3. **Pattern Detector** — checks structuring, card testing, money mule patterns
4. **RAG Retrieval** (Qdrant) — pulls similar past fraud cases, runs only for higher-risk transactions
5. **Supervisor** — combines all signals into a final risk score, generates a summary, and sends high-risk transactions to a review queue

## Tech Stack

FastAPI · LangGraph · LangChain · PostgreSQL · Redis · Qdrant · React · Docker

LLM calls go through Gemini/Groq/Claude with automatic fallback to a mock response if no API key is set.

## Run it

\`\`\`bash
docker-compose up --build
\`\`\`

- Frontend: \`http://localhost:5173\`

Copy \`.env.example\` to \`.env\` and add your API key(s) to enable live LLM responses.
