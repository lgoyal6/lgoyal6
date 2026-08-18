# Laksh Goyal

I write systems software from scratch, mostly C++20 and Go, and I publish the
benchmarks where my own work loses. CS @ UC San Diego (2028).

[LinkedIn](https://linkedin.com/in/lakshgoyal) · [lakshgoyal.com](https://lakshgoyal.com) · lakshgoyal06@gmail.com

---

## Systems I maintain

### [Strata](https://github.com/lgoyal6/strata) · LSM-tree storage engine in C++20
Matches RocksDB single-threaded and beats it 50x on synchronous commits (1,015 vs
20 ops/s) through group commit. I published the workloads where RocksDB wins,
because a comparison without its losing axis is not a comparison. Crash safety is
verified rather than asserted: 11,149 mid-write SIGKILLs recovered every one of
2.2M acknowledged writes with zero loss, and the same 12,000-iteration matrix
gates every push. Recovery-path parsers survive 26M+ fuzz executions and run
clean under ASan, UBSan, and TSan.

Two bugs came out of it that unit tests could not reach: a torn log tail that
stayed invisible until the process crashed again while recovering from the first
crash, and a ~1-in-10^4 race between the background fsync tick and the group
commit leader.

`C++20` `POSIX` `CMake` `libFuzzer` `ASan/UBSan/TSan` · [docs and benchmarks](https://lgoyal6.github.io/strata/)

### [Taut](https://github.com/lgoyal6/taut) · Reliable-UDP transport library
Sliding-window retransmission with selective acknowledgement, fast retransmit,
and an adaptive timer floored at 25 ms, so a dropped packet is resent on the next
round trip instead of stalling every packet queued behind it. Worst-case
round-trip latency runs 6x below the kernel default at 5% packet loss and 12x at
20%. The kernel wins bulk throughput on a clean link by 27x, which is in the
README rather than omitted from it.

Rare failures are reproducible instead of anecdotal: a seeded simulator replays
any one of them from a single flag, and a netem soak passes 20/20 byte-identical
10MB transfers at 5% loss.

`C++20` `epoll` `libFuzzer` `ASan/UBSan` `netem` `ENet baseline` · [docs and benchmarks](https://lgoyal6.github.io/taut/)

### [Tautq](https://github.com/lgoyal6/tautq) · Coordinator-less distributed webhook delivery
Runs on Taut. WAL replication, SWIM membership, and chaos testing. Building it
surfaced two protocol bugs in Taut that its own unit tests never reached, which
is the main argument for writing the thing that uses your library.

`C++20` `WAL replication` `SWIM` `chaos testing`

### [Franq](https://github.com/lgoyal6/franq) · Composable HTTP queue with its own write-ahead log
Zero dependencies outside the Go standard library. Durable writes scale 59x, from
364 to 22,979 records/s across 1 to 128 producers, by batching every concurrent
commit into one fsync while per-producer latency stays flat at 5.3 to 6.0 ms.
Survived 40 SIGKILLs of the live server across 17,990 acknowledged enqueues with
zero loss and zero double-delivery. A delayed, priority, aging LIFO queue is one
config call, and priority aging makes starvation impossible rather than unlikely.

`Go (stdlib only)` `write-ahead log` `group commit`

---

## Contributions to other people's code

[41 merged pull requests across 11 repositories](https://github.com/search?q=is%3Apr+author%3Algoyal6+is%3Amerged&type=pullrequests),
33 into repositories I do not own. The live search is the source of truth, since
it counts my own repos too and I would rather show both numbers than the
flattering one.

- [nathansso/Alongside](https://github.com/nathansso/Alongside) | 14 merged into a longitudinal care companion written in Jac, including a mandatory graph traversal that blocks a prescription conflicting with one a different doctor already wrote
- [UCSD-E4E/ml-mangrove](https://github.com/UCSD-E4E/ml-mangrove) | 3 merged into the Engineers for Exploration research codebase at UC San Diego
- [ishs0978/Industry_Scope](https://github.com/ishs0978/Industry_Scope) | 2 merged, 47 commits, sole code author
- [anirudh9280/ChainSense](https://github.com/anirudh9280/ChainSense) | real-time block subscriber
- [tijilchhabra1729/active-matter](https://github.com/tijilchhabra1729/active-matter) | agent-based T cell swarming simulation

Open, not merged: [partcleda/intern_challenge#64](https://github.com/partcleda/intern_challenge/pull/64),
a mixed-size chip placer in C++20 where zero overlap is structural rather than
tuned. Reading the grader turned up that it scored a different distance than its
own documentation claimed, so the solver optimizes the function actually being
measured.

---

## Things people actually use

**[Hacklist SF](https://luma.com/hacklist-sf)** is a hackathon calendar I built
because I kept hearing about events after they had closed. Around 100 people
subscribe, most of them have no idea who runs it, it earns me nothing, and I keep
it current because it stopped being mine the moment someone planned a weekend
around it. [Source](https://github.com/lgoyal6/hacklist-sf) ·
[board](https://hacklist-sf.modern-renaissance-artifacts.workers.dev)

**[SitRep](https://github.com/lgoyal6/SitRep)** is a Scrum/Kanban/XP tool I led
11 engineers through a 10-week Agile SDLC to ship, with 5 sprints, pair
programming, weekly role rotation, and a 5-stage CI pipeline gating every PR.
[Live](https://cse110-sp26-group15.pages.dev)

**[Checkit Health](https://github.com/lgoyal6/checkit_health)** monitors health
misinformation. [Live](https://checkit-health-s9p4.vercel.app)

---

## Also worth a look

- **[Winnow](https://github.com/lgoyal6/winnow)** | real-time LLM prompt compression along two orthogonal axes so the savings multiply, including a from-scratch AttentionRAG implementation since the paper ships no code
- **[Tollgate](https://github.com/lgoyal6/tollgate)** | multi-tenant API gateway for shared LLM keys, in Go. [Docs](https://lgoyal6.github.io/tollgate/)
- **[AgriShield](https://github.com/lgoyal6/AgriShield)** | wildfire risk and firebreak optimizer, 7-stage geospatial preprocessing into 11 ELMFIRE-ready rasters, 92 tests, `mypy --strict`
- **[Flightrisk](https://github.com/lgoyal6/flightrisk)** | leading indicators of bank deposit drawdown, walk-forward backtested on FDIC call reports
- **[Memharness](https://github.com/lgoyal6/memharness)** | agent-memory benchmark that accounts for ingest cost, not just retrieval quality

---

## Recognition

- 1st place, Akash track, AWS Loop Engineering Hackathon | [Vigil](https://github.com/lgoyal6/vigil), an AI on-call engineer with zero standing credentials
- 2nd place, Replay track, AWS Self-Evolving Hackathon
- 1st place, Voice Cursor x Convex
- 1st place, Voice Coding Hackathon
- 2nd place, BowCapital Defense Hackathon | [Pylon](https://github.com/lgoyal6/pylon), a counter-UAS sensor mesh, incubated at Bow Capital
- Published through the Lumiere Research Program, top 10% of ~200 submissions
- 2nd place, World Robotics Olympiad India | autonomous pipeline inspection robot

---

<details>
<summary><b>Full stack</b></summary>
<br>

**Languages**
C++20 · C · Go · Rust · Python · TypeScript · JavaScript · Java · SQL · Bash · HTML/CSS

**Systems and debugging**
CMake · gdb · libFuzzer · ASan/UBSan/TSan · fault injection · deterministic
replay · perf profiling · netem · epoll · io_uring · write-ahead logging · group
commit · SWIM

**ML and deep learning**
PyTorch · Transformers · MONAI · scikit-learn · LightGBM · OpenCV · NumPy ·
pandas · SciPy · torchaudio · librosa · Kymatio · Optuna · Ray Tune · Open3D ·
ONNX

**LLM and agent infrastructure**
LangGraph · LiteLLM · Anthropic API · OpenAI API · LLMLingua-2 / LongLLMLingua ·
Deepgram · RAG pipelines · tool-calling agents · eval harnesses · cost and
latency instrumentation · GPU serving on Modal

**Backend**
FastAPI · Flask · Node · Pydantic · Typer · gRPC · async job pipelines ·
WebSockets · Redis

**Frontend**
React · Next.js (App Router) · Tailwind · Zustand · Framer Motion · deck.gl ·
Mapbox GL · Recharts · React Native

**Data and storage**
PostgreSQL · Supabase · SQLite · Cloudflare D1 · Redis · Parquet · rasterio ·
GeoPandas

**Infra and tooling**
Docker · Kubernetes · AWS EC2 · Modal · Railway · Cloudflare Pages/Workers ·
GitHub Actions · Git · pytest · Vitest · Playwright · ruff · mypy --strict · Linux

</details>

<details>
<summary><b>Freelance</b></summary>
<br>

I take on a limited number of contracts. Best fit:

- LLM and agent systems: RAG pipelines, tool-calling agents, cost and latency optimization, eval harnesses
- ML pipelines: data ingestion, training infra, model deployment
- Full-stack builds where the hard part is the ML, not the CRUD

Reach me at lakshgoyal06@gmail.com.

</details>
