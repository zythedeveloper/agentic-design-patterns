# Agentic Design Patterns

Jupyter notebooks covering common agentic design patterns (prompt chaining, routing, parallelization, reflection) built on LangChain / LangGraph.

## Prerequisites

- [uv](https://docs.astral.sh/uv/) installed
- Python 3.12.12+ (uv will fetch it for you)

## Setup

Clone the repo and sync dependencies (this also creates the `.venv` and installs the `ipykernel` dev dependency required to run the notebooks):

```bash
git clone <repo-url>
cd agentic-design-patterns
uv sync
```

## Configure environment variables

The notebooks call a chat-completions endpoint via LangChain and read credentials from a `.env` file in the project root using `python-dotenv` (`find_dotenv(usecwd=True)`).

Create a `.env` next to `pyproject.toml`:

```bash
API_KEY=your_api_key_here
BASE_URL=https://your-endpoint/v1
```

`API_KEY` is passed as `api_key` and `BASE_URL` as `base_url` to the LangChain chat client. Use any OpenAI-compatible endpoint.

## Register the kernel for Jupyter

After `uv sync`, register the project's virtualenv as a Jupyter kernel:

```bash
uv run python -m ipykernel install --user --name agentic-design-patterns --display-name "Python (agentic-design-patterns)"
```

## Run the notebooks

Either open them in JupyterLab / VS Code and select the **Python (agentic-design-patterns)** kernel, or run from the CLI:

```bash
uv run jupyter lab notebooks/
```

If you launch Jupyter outside the project venv (e.g. a global install), make sure to pick the `agentic-design-patterns` kernel so the `langchain` / `langgraph` packages resolve.

## Notes

- `uv.lock` is committed — always run `uv sync` (not `uv add`) to reproduce the exact environment.
- If you add a new dependency, use `uv add <pkg>` and commit the updated `pyproject.toml` + `uv.lock`.
