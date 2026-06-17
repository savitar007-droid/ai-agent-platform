# Autonomous Retail Researcher Agent

A multi-agent AI system that researches retail topics in real time — market trends, competitor moves, product demand — and returns a structured, sourced summary instead of a wall of search results.

**Live demo:** https://ai-agent-platform-one-lake.vercel.app/

## Background

This started as a university project for an Agentic AI course, built with CrewAI and LangChain. I designed the original multi-agent architecture and integrated the search/LLM layer; a teammate built the original frontend. After the course ended, I rebuilt and extended it on my own — added a fourth agent (Storage), rebuilt the UI, and got it properly deployed.

## How it works

Four agents handle a query in sequence:

1. **Research** – pulls real-time web results via Tavily
2. **Analysis** – filters and ranks what comes back
3. **Summary** – uses a Groq-hosted LLM to turn that into a structured summary, grounded in the retrieved sources (RAG)
4. **Storage** – saves the result so past research is searchable later

The UI shows each agent's status as it runs, so a query isn't just a loading spinner — you can see which stage is active.

## Tech stack

| Layer | Tools |
|---|---|
| Agent framework | CrewAI, LangChain |
| Search / retrieval | Tavily |
| LLM | Groq |
| Backend | Python |
| Frontend | HTML | Javascript |CSS
| Deployment | Docker, Vercel |
| CI/CD | Jenkins |

## Running locally

```bash
git clone https://github.com/Aditya-Agrawal-Dev/ai-agent-platform.git
cd ai-agent-platform
```


Backend:
```bash
cd backend
pip install -r requirements.txt
python main.py
```

Frontend:
```bash
cd frontend
npm install
npm run dev
```

Or with Docker Compose:
```bash
docker-compose up
```

## Known limitations

- No automated test suite yet
- Result quality depends entirely on what Tavily returns for a given query — no fallback if a source is thin
- Single-LLM setup; no fallback if the Groq API is rate-limited or down

## Origin

Built originally for the Agentic AI – Datagami Skill Based Course at Medi-Caps University (Group D03G12). The original group submission is at [Collegemed/Autonomous-Retail-Researcher-Agent](https://github.com/Collegemed/Autonomous-Retail-Researcher-Agent). This repo is my independent continuation after the course.

## Author

Aditya Agrawal — B.Tech IT, Medi-Caps University
