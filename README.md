# Research Agent — Retrieval-Augmented Generation (RAG) Project

This repository is a notebook-first prototype implementing a Retrieval-Augmented Generation (RAG) workflow over a local document dataset (an arXiv subset). The project demonstrates loading documents, preprocessing and chunking text, creating embeddings, indexing them in a vector store, and answering queries by retrieving relevant context and using a text-generation model.

## What the project does

- Loads a small demo document dataset located under `files/` (JSON) and demonstrates preprocessing.
- Splits documents into text chunks suitable for embedding.
- Creates embeddings for chunks using a configurable embedding model.
- Indexes embeddings into a vector store for similarity search (e.g., FAISS).
- Runs retrieval + generation experiments inside the main Jupyter notebook `research-agent-LangGraph.ipynb`.

## Key components

- **Notebook**: `research-agent-LangGraph.ipynb` — the canonical workflow (data → embeddings → index → queries).
- **Dataset**: `files/arxiv_dataset.json` — small demo dataset (ignored by git; keep large datasets local).
- **Config**: `.env` (ignored) and `.env.example` (safe to commit) document environment variables used by the notebook.
- **Dependencies**: `requirements.txt` lists Python packages required to run experiments.
- **Ignore rules**: `.gitignore` excludes data, environment files, caches and other artifacts.

## Repository structure

- `.env` — Local environment variables (ignored by git; do not commit secrets).
- `.env.example` — Demo environment file safe to commit and use as a template.
- `.gitignore` — Rules for files that should not be committed.
- `requirements.txt` — Python dependencies.
- `research-agent-LangGraph.ipynb` — Main notebook implementing the RAG pipeline.
- `files/` — Local dataset and other large assets (ignored by git).
  - `files/arxiv_dataset.json` — demo dataset (JSON).

## Prerequisites

- Python 3.8 or newer.
- `pip` available to install dependencies.
- (Optional) Access to any external APIs you plan to use (e.g., OpenAI or other LLM providers). Configure API keys in your local `.env` file.

## Setup (Windows PowerShell)

1. Open PowerShell and change to the project directory:

```powershell
cd D:\python_project\RAG_Project
```

2. Create and activate a virtual environment:

```powershell
python -m venv .venv
# Activate in PowerShell
& .\\.venv\\Scripts\\Activate.ps1
```

3. Install dependencies:

```powershell
pip install -r requirements.txt
```

4. Copy the example environment file and fill in real values locally:

```powershell
Copy-Item .env.example .env
# Then edit .env with a text editor to insert your API keys and settings
```

Notes:

- If you use Bash (macOS/Linux) the equivalent commands are `python -m venv .venv` and `source .venv/bin/activate`.
- Keep `.env` out of version control. Only commit `.env.example` with placeholder values.

## Environment variables

Keep these in `.env` (use `.env.example` as a template). Replace placeholders with real values locally:

- `FLASK_ENV` — e.g. `development`
- `DEBUG` — `True` or `False`
- `SECRET_KEY` — application secret (keep private)
- `OPENAI_API_KEY` — API key for chosen LLM provider (if used)
- `DATABASE_URL` — optional database connection URL
- `S3_BUCKET_NAME`, `S3_ACCESS_KEY`, `S3_SECRET_KEY` — optional storage credentials
- `SOME_FEATURE_FLAG` — app-specific flags

## Usage

1. Start Jupyter or open the notebook in VS Code:

```powershell
jupyter notebook research-agent-LangGraph.ipynb
# or
code research-agent-LangGraph.ipynb
```

2. Run the notebook cells in order to:

   - Load and inspect the demo dataset.
   - Preprocess text and create chunks.
   - Generate embeddings and persist or load the vector index.
   - Run retrieval experiments and call the generation model.

3. If you prefer scripts over notebooks, extract the notebook cells into Python modules and run them as scripts:

```powershell
python scripts/preprocess.py
python scripts/embed_and_index.py
python scripts/query.py
```

## Data

- `files/arxiv_dataset.json` is included as a small demo. Large datasets and model caches should remain out of version control and stored locally or in external storage.

## Recommendations

- Use `.env` for all secrets and never commit real keys to GitHub.
- Keep `requirements.txt` updated when adding packages.
- Add small scripts to reproduce the notebook steps for CI or automation.

## Contributing

- Open an issue or submit a pull request.
- When adding features, add tests or a short demo notebook and update `requirements.txt`.
- Keep `.env.example` updated with any new configuration keys.

## License & Acknowledgements

This project is a small research prototype. Add a `LICENSE` file if you plan to publish under an open-source license.

---
