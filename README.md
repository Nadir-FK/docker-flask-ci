# Flask CI/CD Pipeline

A production-style DevOps project demonstrating a complete CI/CD pipeline for a Python Flask application — from code push to a deployable Docker image on Docker Hub, with automated testing at every step.

![CI Pipeline](https://github.com/Nadir-FK/docker-flask-ci/actions/workflows/ci.yml/badge.svg)

---

## What this project does

Every time code is pushed to `main`, the pipeline automatically:

1. Installs dependencies
2. Runs the test suite with pytest — if tests fail, the pipeline stops
3. Builds a Docker image from the Dockerfile
4. Pushes the image to Docker Hub — ready to deploy on any server

No manual steps. No "works on my machine." Every release is tested and containerized automatically.

---

## Pipeline flow

```
git push
    │
    ▼
GitHub Actions triggered
    │
    ├── Install dependencies
    ├── Run pytest tests
    ├── Build Docker image
    └── Push to Docker Hub ──► deployable image
```

---

## Tech stack

| Tool | Purpose |
|---|---|
| Python / Flask | Web application |
| Docker | Containerization |
| Docker Compose | Multi-service local environment |
| GitHub Actions | CI pipeline automation |
| pytest | Automated testing |
| Docker Hub | Image registry |

---

## Project structure

```
flask-cicd-pipeline/
├── app.py                          # Flask application
├── requirements.txt                # Python dependencies
├── Dockerfile                      # Container definition
├── docker-compose.yml              # Multi-service setup
├── tests/
│   ├── __init__.py
│   └── test_app.py                 # pytest test suite
└── .github/
    └── workflows/
        └── ci.yml                  # GitHub Actions pipeline
```

---

## Run locally

**With Docker Compose (recommended):**

```bash
docker compose up --build
```

App will be available at `http://localhost:5000`

**Without Docker:**

```bash
pip install -r requirements.txt
python app.py
```

---

## Run tests

```bash
pip install -r requirements.txt
python -m pytest tests/ -v
```

---

## CI/CD pipeline (GitHub Actions)

The pipeline is defined in `.github/workflows/ci.yml` and runs on every push to `main`:

```yaml
test → build Docker image → push to Docker Hub
```

Secrets required in GitHub repository settings:
- `DOCKER_USERNAME` — your Docker Hub username
- `DOCKER_TOKEN` — your Docker Hub access token

---

## API endpoints

| Method | Endpoint | Description |
|---|---|---|
| GET | `/` | Returns welcome message |
| GET | `/health` | Health check — returns `{"status": "healthy"}` |

---

## What this demonstrates

- Containerizing a Python application with Docker
- Writing a multi-service environment with Docker Compose
- Building a fully automated CI pipeline with GitHub Actions
- Integrating automated tests as a quality gate before every build
- Publishing Docker images to a registry automatically

---

## Author

**Nadir** — DevOps Engineer specializing in Docker, CI/CD pipelines, and deployment automation.

[Upwork Profile](https://www.https://www.upwork.com/freelancers/~01fa327776c56beda1) · [Docker Hub](https://hub.docker.com)
