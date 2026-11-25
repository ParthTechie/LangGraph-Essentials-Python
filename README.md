# LangGraph Essentials - Python

Labs for the core LangGraph pieces: state, nodes, edges, memory, and interrupts. The last notebook puts them together in an email support workflow.

These notebooks follow the [LangChain Academy LangGraph Essentials](https://github.com/langchain-ai/lca-langgraph-essentials) course. The original material is MIT licensed. Copyright stays with LangChain, Inc.

## Labs

| Notebook | What you build |
| --- | --- |
| `L1_nodes.ipynb` | State and nodes |
| `L2_edges.ipynb` | Parallel edges, and a reducer (`operator.add`) that accumulates results |
| `L3-L4_cedges_memory.ipynb` | Conditional edges and memory |
| `L5_interrupt.ipynb` | Interrupts and human-in-the-loop |
| `L6_EmailAgent.ipynb` | An email workflow: classify, route, draft, and pause for review |
| `studio/` | The same email workflow in LangGraph Studio |

## Setup

Python 3.11 through 3.13. You need [uv](https://docs.astral.sh/uv/) (or pip) and an OpenAI API key.

```bash
git clone https://github.com/ParthTechie/LangGraph-Essentials-Python.git
cd LangGraph-Essentials-Python
```

Copy the env template and put your key in it.

```bash
# Windows
copy example.env .env

# macOS / Linux
cp example.env .env
```

```env
OPENAI_API_KEY=your_openai_api_key_here

# Optional LangSmith tracing
LANGSMITH_API_KEY=your_langsmith_api_key_here
LANGSMITH_TRACING_V2=true
LANGSMITH_PROJECT=langgraph-py-essentials
# EU instance only:
# LANGSMITH_ENDPOINT=https://eu.api.smith.langchain.com
```

Install and open the notebooks.

```bash
uv sync
uv run jupyter lab
```

If you would rather activate the virtualenv yourself:

```bash
# Windows
.venv\Scripts\activate

# macOS / Linux
source .venv/bin/activate

jupyter lab
```

Pip works too: `pip install -r requirements.txt`, then `jupyter lab`.

## LangSmith Studio

Optional. Create a [LangSmith](https://smith.langchain.com/) account and an API key if you want traces, or if you want to open the email graph in Studio.

```bash
# Windows
copy .env studio\.env

# macOS / Linux
cp .env studio/.env

cd studio
uv run langgraph dev
```

Sample inputs for the Studio graph are in `studio/studio-examples.txt`. When the graph pauses for human review, reply with JSON, for example `{"approved": true}`.
