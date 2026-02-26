# Collaborative AI Agent Framework

A **scalable, production-ready AI orchestration platform** built using  
**FastAPI, PostgreSQL, Redis, Celery, and LangGraph-style workflows**.

This system demonstrates how **multiple AI agents can collaborate asynchronously**, pause for **human approval**, resume execution, and persist results with **full observability and test coverage**.

---

## Key Capabilities

### Multi-Agent Workflow
- Task submission stored with initial `PENDING` state
- Research phase executed asynchronously by a worker
- Workflow pauses for explicit human approval
- Writing phase resumes after approval
- Final output persisted and marked `COMPLETED`

### System Architecture
- **FastAPI** – REST API layer
- **PostgreSQL** – durable task and audit storage
- **Redis** – message broker and shared workspace
- **Celery** – distributed background task processing
- **Agent Graph Layer** – extensible orchestration logic
- **Structured JSON logging** – file-based and database-backed
- **WebSocket support** – real-time status updates (extensible)

---

## Testing Strategy

- Pytest-based test suite
- SQLite in-memory database for test isolation
- Deterministic execution mode (no external services required)
- Validates:
  - API contracts
  - Task lifecycle transitions
  - Agent logs and results
  - WebSocket endpoint availability

---

## Repository Layout

collaborative-ai-agent-framework/
│
├── src/ # Application source code
│ ├── agents/ # Specialized agent logic
│ ├── api/ # FastAPI routes
│ ├── graph/ # Workflow orchestration layer
│ ├── models/ # ORM database models
│ ├── schemas/ # Pydantic schemas
│ ├── services/ # Business and persistence logic
│ ├── tools/ # External agent tools
│ ├── utils/ # Shared helpers
│ ├── worker/ # Celery configuration and tasks
│ │ ├── celery_app.py
│ │ └── tasks.py
│ │
│ ├── init.py
│ ├── config.py # Environment configuration
│ ├── database.py # Database initialization
│ └── main.py # FastAPI entry point
│
├── tests/ # Automated tests
│ ├── conftest.py
│ ├── test_api_tasks.py
│ ├── test_integration.py
│ ├── test_websocket.py
│ └── test_workflow.py
│
├── .env.example # Environment variable template
├── .gitignore
├── docker-compose.yml # Multi-service orchestration
├── Dockerfile # Application container image
├── requirements.txt # Python dependencies
└── README.md
