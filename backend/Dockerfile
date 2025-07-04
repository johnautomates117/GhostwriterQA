# Backend Dockerfile
FROM python:3.11-slim

# Install system dependencies
RUN apt-get update && apt-get install -y \
    gcc \
    g++ \
    libpq-dev \
    curl \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /app

# Copy requirements first for better caching
COPY requirements.txt .

# Install Python dependencies
RUN pip install --no-cache-dir --upgrade pip && \
    pip install --no-cache-dir -r requirements.txt

# Copy application code
COPY . .

# Ensure the src directory is in Python path
ENV PYTHONPATH=/app

# Create logs directory
RUN mkdir -p logs

EXPOSE 8000

# Run migrations and start server
CMD ["sh", "-c", "cd /app && alembic upgrade head && uvicorn src.main:socket_app --host 0.0.0.0 --port 8000 --reload"]