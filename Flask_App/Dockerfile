ARG PYTHON_VERSION=3.11.6
FROM python:${PYTHON_VERSION}-slim as base

ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1

WORKDIR /app

ARG UID=10001
RUN adduser \
    --disabled-password \
    --gecos "" \
    --home "/app" \
    --shell "/bin/sh" \
    --no-create-home \
    --uid "${UID}" \
    appuser

# Install the dependencies
COPY requirements.txt requirements.txt
RUN python -m pip install -r requirements.txt

USER appuser

COPY . .

EXPOSE 8000

# Run the application using Gunicorn
CMD ["gunicorn", "--bind", "0.0.0.0:8000", "app:app"]