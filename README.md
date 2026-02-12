#  HALIMZ AI
### Agentic AI Search & Chat System with Real-Time Streaming

HALIMZ AI is a production-oriented AI chat system that combines conversational AI with real-time web search to generate grounded, up-to-date responses.

The system is built using an agentic architecture powered by **LangGraph**, enabling structured decision-making between LLM reasoning and external tool usage (web search).

---

## Project Objective

Design and implement a scalable AI system that:

- Streams responses in real time  
- Dynamically decides when to call external tools  
- Grounds responses with live web data  
- Maintains multi-turn conversational memory  
- Provides full transparency of AI reasoning stages  

---

##  System Architecture

The system follows a modular **Client–Server Architecture** with an agentic orchestration layer.

```
Client (Next.js)
        ↓  SSE
FastAPI Backend
        ↓
LangGraph Agent Flow
        ↓
LLM (Groq LLaMA-3) + Tavily Search Tool
```

---

##  Backend Architecture (FastAPI + LangGraph)

###  Agent Orchestration (LangGraph)

Implemented a structured graph-based workflow:

- User Input Node  
- LLM Reasoning Node  
- Tool Decision Node  
- Search Execution Node  
- Response Synthesis Node  

This enables:

- Conditional tool invocation  
- Deterministic control flow  
- Reduced hallucination risk  
- Clear separation between reasoning and tool usage  

---

###  LLM Layer

- Model: **LLaMA 3 (via Groq API)**  
- High-speed inference  
- Low-latency streaming  
- Cost-efficient deployment  

---

###  Tool Integration

- Tavily Search API  
- Dynamic query formulation  
- Search result parsing  
- Context injection into final prompt  

---

###  Streaming Layer

- Implemented using **Server-Sent Events (SSE)**  
- Token-level streaming  
- Real-time UI updates  
- Search stage event emission (searching → reading → writing)  

---

##  Frontend Architecture (Next.js + React)

- Modern React App Router structure  
- Streaming response handling via SSE  
- State management for:
  - Conversation history  
  - Search status  
  - Loading indicators  
- Clean, minimal UI inspired by Perplexity.ai  
- Fully responsive design  

---

##  Agent Workflow

1. User submits query  
2. LLM analyzes intent  
3. Agent decides whether to:
   - Respond directly  
   - Invoke the search tool  
4. If search is required:
   - Generate optimized search query  
   - Fetch results from Tavily  
   - Inject retrieved context into the prompt  
5. LLM synthesizes grounded response  
6. Response is streamed to the client in real time  

Search transparency indicators:

```
Searching → Reading → Writing
```

---

##  Key Engineering Highlights

- Agentic AI architecture using LangGraph  
- Tool-augmented LLM reasoning  
- Hallucination mitigation via retrieval grounding  
- Real-time token streaming with SSE  
- Clear separation of concerns (UI / API / Agent layer)  
- Production-ready folder structure  
- Environment-based configuration  

---

##  Tech Stack

### Frontend

- Next.js  
- React  
- TailwindCSS  
- Server-Sent Events (SSE)  

### Backend

- FastAPI  
- LangGraph  
- Groq API (LLaMA 3)  
- Tavily Search API  

---

##  Setup & Installation

###  Prerequisites

- Node.js 18+  
- Python 3.10+  
- Groq API Key  
- Tavily API Key  

---

### 1️ Clone Repository

```bash
git clone https://github.com/MohamedHalimmxx/HALIMZ-AI.git
cd HALIMZ
```

---

### 2️⃣ Backend Setup

```bash
cd server
python -m venv .venv
source .venv/Scripts/activate   # Windows (Git Bash)
pip install -r requirements.txt
```

Create a `.env` file inside the `server` directory:

```
GROQ_API_KEY=your_key_here
TAVILY_API_KEY=your_key_here
```

Run the backend:

```bash
uvicorn app:app --reload
```

---

### 3️⃣ Frontend Setup

```bash
cd client
npm install
npm run dev
```

Open in browser:

```
http://localhost:3000
```

---

##  Future Improvements

- Add citation rendering from Tavily sources  
- Add conversation persistence (database layer)  
- Implement multi-tool support  
- Add RAG vector database integration  
- Dockerize the application  
- Add CI/CD pipeline  
- Add monitoring & logging  

---

##  License

MIT License  

---

##  Acknowledgments

- Inspired by Perplexity.ai  
- Powered by Groq (LLaMA 3)  
- Search powered by Tavily  
- Orchestrated using LangGraph  
