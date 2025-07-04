# GhostwriterQA

AI-powered API testing platform that transforms Swagger/OpenAPI documentation into comprehensive test suites.

## Architecture Overview

GhostwriterQA follows a microservices architecture with:
- **Backend**: Python FastAPI with async support
- **Frontend**: React 18 with TypeScript
- **Database**: PostgreSQL + Redis
- **Task Queue**: Celery with Redis broker
- **Container Runtime**: Docker for test isolation

## Project Structure

```
ghostwriter-qa/
├── backend/               # FastAPI backend service
│   ├── src/
│   │   ├── api/          # API endpoints
│   │   ├── services/     # Business logic
│   │   ├── models/       # Database models
│   │   ├── core/         # Core utilities
│   │   └── utils/        # Helper functions
│   ├── tests/            # Backend tests
│   └── alembic/          # Database migrations
├── frontend/             # React TypeScript frontend
│   ├── src/
│   │   ├── components/   # UI components (atomic design)
│   │   ├── pages/        # Page components
│   │   ├── services/     # API services
│   │   ├── store/        # Redux store
│   │   └── types/        # TypeScript types
│   └── public/           # Static assets
├── shared/               # Shared types/interfaces
├── infrastructure/       # Deployment configurations
│   ├── kubernetes/       # K8s manifests
│   └── docker/           # Dockerfiles
└── docs/                 # Documentation
```

## Getting Started

### Prerequisites
- Node.js 18+
- Python 3.11+
- Docker & Docker Compose
- PostgreSQL 15
- Redis 7

### Development Setup

1. Clone the repository:
```bash
git clone https://github.com/johnautomates117/GhostwriterQA.git
cd GhostwriterQA
```

2. Install backend dependencies:
```bash
cd backend
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
```

3. Install frontend dependencies:
```bash
cd frontend
npm install
```

4. Set up environment variables:
```bash
cp .env.example .env
# Edit .env with your configuration
```

5. Start services with Docker Compose:
```bash
docker-compose up -d
```

6. Run database migrations:
```bash
cd backend
alembic upgrade head
```

7. Start development servers:
```bash
# Backend (in backend directory)
uvicorn src.main:app --reload --port 8000

# Frontend (in frontend directory)
npm run dev
```

## Key Features

- **AI-Powered Test Generation**: Automatically creates comprehensive test suites from API specs
- **IDE-like Interface**: Monaco Editor integration for test editing
- **Real-time Execution**: WebSocket-based live test execution updates
- **Environment Management**: Secure credential storage and environment variables
- **Comprehensive Reporting**: Detailed analytics and visualizations

## License

Copyright (c) 2024 GhostwriterQA. All rights reserved.