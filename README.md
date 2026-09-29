# Autonomous AI Bug Fixing Assistant

## Setup
1. Install Python 3.10+, Git, and Docker Desktop/Engine.
2. Create and activate a virtual environment.
3. Run `pip install -r requirements.txt`
4. Set your API key: `OPENAI_API_KEY=...` (or create a `.env` file).
5. Run:
`python main.py --repo /path/to/git/repo --bug "Describe the bug" --logs "Paste stack trace" --test-command "pytest -q"`

Artifacts are written under `artifacts/<run-id>/`: repository inventory, root-cause analysis, proposed patch, test result, and PR-style report.

## Important limitations
This is a demo, not production-ready autonomous software. It uses an OpenAI model, a modular sequence of agent roles, and Docker with network disabled and a read-only mount of the original repository. The patch is applied only to a disposable container copy. It does not commit or push. Review all patches manually.

The default sandbox is `python:3.11-slim`; this example is primarily for Python repositories. The image has no network, so dependencies must be present in the image or otherwise made available offline. Adapt the Docker image and dependency setup for other languages. Only run trusted repositories: repository tests and build scripts are untrusted code, and Docker is not an absolute security boundary.
