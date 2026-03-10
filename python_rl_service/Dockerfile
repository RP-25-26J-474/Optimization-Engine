# syntax=docker/dockerfile:1
FROM python:3.11-slim-bookworm

ENV PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1 \
    PIP_NO_CACHE_DIR=1

WORKDIR /app

RUN apt-get update \
    && apt-get install -y --no-install-recommends ca-certificates \
    && rm -rf /var/lib/apt/lists/*

COPY requirements.txt ./
RUN pip install --upgrade pip && \
    pip install -r requirements.txt

COPY . ./

# Expose port (defaulting to 5000 based on standard Flask/Gunicorn or 8001 if customized, assuming 5000 for standard run)
EXPOSE 5000

CMD ["flask", "run", "--host=0.0.0.0", "--port=5000"]
