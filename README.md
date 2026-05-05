# Jenkins Pipeline with Blue Ocean

Part of my 100 DevOps Projects challenge.

## What this project does
Sets up a Jenkins CI/CD pipeline with the Blue Ocean UI plugin to automatically build, test, and dockerize a Python Flask app whenever code is pushed to GitHub.

## Tech Stack
- Python + Flask — the app
- pytest — testing
- Docker — containerization
- Jenkins + Blue Ocean — the pipeline

## Pipeline Stages
1. **Install** — installs Python dependencies
2. **Test** — runs pytest to verify the app works
3. **Docker Build** — builds a Docker image of the app

## How to run locally
pip install flask pytest
python app.py