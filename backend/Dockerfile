# Official Python image
FROM python:3.12-slim

# Environment variables
ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1

# The working directory in the container
WORKDIR /app

# Install system dependencies (for mysqlclient)
RUN apt-get update && \
    apt-get install -y \
    build-essential \
    pkg-config \
    libmariadb-dev \
    && rm -rf /var/lib/apt/lists/*

# Install dependencies
COPY requirements.txt /app
RUN pip install --no-cache-dir -r requirements.txt

# Copy project files into the container
COPY . /app

# Expose port 8000
EXPOSE 8000

# Run server
CMD ["gunicorn", "maskani.wsgi:application", "--bind", "0.0.0.0:8000"]