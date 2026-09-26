# DOAIS workshop 3: llmapp09

This repository contains the `llmapp09` LLMOps exercise: a FastAPI backend, a Flask frontend, Promptfoo and DeepEval evaluations, Docker Compose, and GitHub Actions workflows.

## Run locally

1. Start Docker and set `OLLAMA_API_KEY` in your shell or in a local `.env` file. The `.env` file is ignored by Git and must not be committed.
2. Run `docker compose up --build -d` from this directory.
3. Open the frontend at <http://localhost:5000> and the API at <http://localhost:8080/swagger-ui.html>.
4. Run `docker compose down` when finished.

The frontend reaches the backend at `http://llm-multiroute:8080` over the Compose network.

## GitHub Actions setup

Set the repository variable `DOCKERHUB_USERNAME` to your Docker Hub username. Add the repository secrets `DOCKERHUB_TOKEN`, `OLLAMA_API_KEY`, `OLLAMA_BASE_URL`, and `OPENAI_API_KEY` under **Settings → Secrets and variables → Actions**. Do not put secret values in repository files.

The four workflows under `.github/workflows` run lint, unit tests, image scanning and publishing, Promptfoo, and DeepEval. Image publishing runs on pushes to `main`; pull requests build and scan without publishing. The evaluation workflows can also be started manually after the secrets are configured.

See [docker_readme.md](docker_readme.md) and [workflow_readme.md](workflow_readme.md) for details.
