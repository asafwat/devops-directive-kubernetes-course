#FROM python:3.12-slim AS generate-requirements
#RUN apt-get update && apt-get install -y curl && rm -rf /var/lib/apt/lists/*
#RUN curl -sSL https://install.python-poetry.org | python3 -
#COPY pyproject.toml poetry.lock ./
#RUN /root/.local/bin/poetry export --output requirements.txt


FROM python:3.12-slim AS generate-requirements

# Set environment variables
ENV POETRY_VERSION=1.6.1
ENV POETRY_HOME=/root/.local
ENV PATH="$POETRY_HOME/bin:$PATH"

# Install required packages and Poetry
RUN apt-get update && apt-get install -y curl \
    && curl -sSL https://install.python-poetry.org | python3 - \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Copy your pyproject.toml and poetry.lock files
COPY pyproject.toml poetry.lock ./

# Export dependencies to requirements.txt
RUN poetry export --without-hashes -o requirements.txt

###

FROM python:3.12-slim AS production
COPY --from=generate-requirements /requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY . . 
CMD ["python", "main.py"]