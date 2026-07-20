<img src="https://capsule-render.vercel.app/api?type=rect&color=40E0D0&height=150" width="100%" alt="banner">

# Laksh Goyal

ML systems and agentic AI. CS @ UC San Diego (2028).

I build systems that survive contact with production: inference pipelines, LLM
agent infrastructure, and the eval/observability layer that tells you when they
break. Currently splitting time between GTM engineering at a GPU cloud, applied
medical imaging ML, and whatever hackathon is happening that weekend.

Open to freelance work. Details at the bottom.

[LinkedIn](https://linkedin.com/in/lakshgoyal) · [Portfolio](https://lakshgoyal.vercel.app) · lakshgoyal06@gmail.com

---

## What I'm working on

- **GTM Engineering @ GMI Cloud** Outbound and revenue infrastructure for a GPU
  cloud: enrichment pipelines, automated workflows, and the data plumbing behind
  them.
- **Applied ML @ a medical imaging startup** Segmentation, depth estimation, 3D
  reconstruction, and structured clinical output from a single photo.
- **ML Systems @ Engineers for Exploration (Qualcomm Institute)** Multi-terabyte
  bioacoustic pipelines and domain-shift robustness for wildlife monitoring.

---

## Selected work

### [Winnow](https://github.com/lgoyal6/winnow) Real-time LLM prompt compression
Compresses prompts along two orthogonal axes so the savings multiply:
token-space (LLMLingua-2 + LongLLMLingua + a from-scratch AttentionRAG
implementation, since the paper ships no code) and model-space (TurboQuant as a
drop-in `DynamicCache` subclass, ~4-bit KV). Stacked with LCLM latent-context
compression for ~60x total KV reduction while beating the fp16 F1 baseline on
LongBench. Voice-first demo over Deepgram Nova-3, served on warm Modal A100s.

`PyTorch` `Transformers` `Modal` `FastAPI` `Next.js`

### [AgentBench](https://github.com/lgoyal6/agentbench) Eval framework for LangGraph agents
4K LOC. Scores accuracy, per-run cost, and latency percentiles, then ranks
agents on production trade-offs instead of raw accuracy (cost-adjusted accuracy,
efficiency score). Async-safe per-node usage attribution via `contextvars` that
survives `asyncio.gather`. Ray Tune + ASHA for prompt/model HPO. Shipped as a
package: Typer CLI, FastAPI leaderboard, GitHub Actions CI with `mypy --strict`,
OIDC PyPI publishing.

`Python` `LangGraph` `LiteLLM` `Ray Tune` `FastAPI`

### [AgriShield](https://github.com/lgoyal6/agrishield) Wildfire risk and firebreak optimizer
Geospatial simulation, not a notebook. A 7-stage preprocessing pipeline turns
farm boundary polygons into 11 ELMFIRE-ready rasters on a canonical 30m
EPSG:5070 grid, pulling live LANDFIRE and USGS 3DEP data behind SHA-256-keyed
caching with exponential backoff. Runs 8-bearing fire-spread ensembles, then
scores 24 candidate firebreak layouts on a 6-weight composite of protected-area
safety, risk reduction, and per-segment cost. 92 tests, `mypy --strict`, 100%
type coverage.

`Python` `rasterio` `GeoPandas` `SciPy` `Pydantic` `ELMFIRE`

### [SitRep](https://github.com/lgoyal6/sitrep) Team project management app
Led 11 engineers through a 10-week Agile SDLC (5 sprints, pair programming,
weekly role rotation) to ship a Scrum/Kanban/XP tool on Cloudflare Pages with
D1, session auth, and a 5-stage CI pipeline gating every PR.

`Vanilla JS` `Cloudflare D1` `Vitest` `Playwright` `GitHub Actions`

More in the pinned repos below.

---

## Recognition

Four hackathon wins across ML infra, defense tech, and scientific computing.
Highlights:

- 1st place, Loop Engineering Hackathon. Vigil, an AI on-call engineer with zero
  standing credentials (Best Use of Akash)
- 1st place, Vibe Coding Active Matter Hackathon. Agent-based T cell swarming
  simulation with chemotaxis and receptor desensitization
- 2nd place, BowCapital Defense Hackathon. Pylon, a counter-UAS sensor mesh,
  now incubated at Bow Capital
- Published through the Lumiere Research Program, top 10% of ~200 submissions
- 2nd place, World Robotics Olympiad India. Autonomous pipeline inspection robot

---

<details>
<summary><b>Full stack</b></summary>

<br>

**Languages**
Python · TypeScript · JavaScript · Java · C/C++ · SQL · HTML/CSS

**ML and deep learning**
PyTorch · Transformers · MONAI · scikit-learn · LightGBM · OpenCV · NumPy ·
pandas · SciPy · torchaudio · librosa · Kymatio · Optuna · Ray Tune · Open3D ·
ONNX · TensorFlow

**LLM and agent infrastructure**
LangGraph · LiteLLM · Anthropic API · OpenAI API · LLMLingua-2 / LongLLMLingua ·
Deepgram · RAG pipelines · tool-calling agents · eval harnesses · cost and
latency instrumentation · GPU serving on Modal

**Backend**
FastAPI · Flask · Node · Pydantic · Typer · async job pipelines · WebSockets ·
Redis

**Frontend**
React · Next.js (App Router) · Tailwind · Zustand · Framer Motion · deck.gl ·
Mapbox GL · Recharts · React Native

**Data and storage**
PostgreSQL · Supabase · SQLite · Cloudflare D1 · Redis · Parquet · rasterio ·
GeoPandas

**Infra and tooling**
Docker · AWS EC2 · Modal · Railway · Cloudflare Pages/Workers · GitHub Actions ·
Git · pytest · Vitest · Playwright · ruff · mypy --strict · Linux

**GTM engineering**
Clay · Apollo · Hunter · Instantly · n8n · Notion API

</details>

---

## Freelance

I take on a limited number of contracts. Best fit:

- LLM and agent systems: RAG pipelines, tool-calling agents, cost and latency
  optimization, eval harnesses
- ML pipelines: data ingestion, training infra, model deployment
- Full-stack builds where the hard part is the ML, not the CRUD
- GTM engineering: enrichment pipelines, outbound automation, and the data
  plumbing behind them

Reach me at lakshgoyal06@gmail.com.
