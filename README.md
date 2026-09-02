# Laksh Goyal

I write systems software from scratch, mostly C++20, Go and Rust, and I publish
the benchmarks where my own work loses. CS @ UC San Diego, class of 2028.

[LinkedIn](https://linkedin.com/in/lakshgoyal) · [lakshgoyal.com](https://lakshgoyal.com) · lakshgoyal06@gmail.com

---

## Where I've worked

**GMI Cloud** · SWE Intern, AI Platform · Jun 2026 to now
Built Mint, the lead-research tool the GTM team runs on. Shipped a model-routing
layer that cut inference cost 47%. Benchmarked 8 routing setups on cost per
solved task.

**DR Financial** · SWE Intern · Jul 2026 to now
Built the production pipeline that decides whether a doctor can be contracted.
Raised auto-clearance from 41% to 73%. Ran the adversarial miss-rate testing.

**Qualcomm Institute, Engineers for Exploration** · SWE, ML Systems · Oct 2025 to Jun 2026
Built the wildlife-audio training pipeline and doubled the usable data coming out
of multi-terabyte archives. Wrote the boundary-aware eval metric the group still
gates releases on.

**AWS Student Builder Club @ UC San Diego** · Technical Lead
Ran workshops on EC2, EKS, Lambda and S3. Built the shared GPU queue its 20
members submit training jobs to.

---

## Systems

**[Strata](https://github.com/lgoyal6/strata)** · LSM-tree storage engine in C++20
Beats RocksDB 50x on synchronous commits through group commit, and I publish the
workloads where RocksDB wins. Killed it mid-write 11,149 times and it recovered
every one of 2.2M acknowledged writes.
`C++20` `libFuzzer` `ASan/UBSan/TSan` · [demo](https://lgoyal6.github.io/strata/)

**[Taut](https://github.com/lgoyal6/taut)** · Reliable-UDP transport library
6x lower worst-case latency than the kernel at 5% packet loss, 12x at 20%. The
kernel wins bulk throughput by 27x, which is in the README rather than left out.
`C++20` `epoll` `netem` · [demo](https://lgoyal6.github.io/taut/)

**[Franq](https://github.com/lgoyal6/franq)** · Crash-safe message queue, Go stdlib only
Durable writes scale 59x to 22,979 records/s by batching every concurrent commit
into one fsync. Crashed the live server 40 times mid-traffic and still delivered
all 17,990 acknowledged messages exactly once.
`Go` `write-ahead log` `group commit`

**[Tollgate](https://github.com/lgoyal6/tollgate)** · Multi-tenant gateway for shared LLM keys
Lets a team share one paid API key with per-member limits and revocation. Rate
limiting stays exact past one replica: 300 req/s holds across 3 Kubernetes
replicas through Redis Lua, where per-replica limiting admitted 3x the ceiling.
`Go` `Redis` `Kubernetes` `Terraform` · [demo](https://lgoyal6.github.io/tollgate/)

**[Basis](https://github.com/lgoyal6/basis)** · A ledger that argues with your broker
Recomputes every position from your own trade history and reports each
disagreement. Found 14 cost-basis errors across 9 real brokerage accounts.
`Java 21` `Spring Boot` `PostgreSQL` · [live](https://basis-web-production.up.railway.app)

**[TickVault](https://github.com/lgoyal6/tickvault)** · Full-depth order book archive
Records order books across 6 crypto venues in Rust at 2.7M rows/s, capturing 100%
of wall-clock time on 5 of 6 feeds and publishing the sixth as 0% verified rather
than rounding it up.
`Rust` `Arrow` `Parquet` · [PyPI](https://pypi.org/project/tickvault-ob/) · [demo](https://lgoyal6.github.io/tickvault/)

---

## GPU and inference

**[Winnow](https://github.com/lgoyal6/winnow)** · Quantized KV cache with a fused Triton kernel
One kernel unpacks, gathers from the codebook and inverse-rotates in a single GPU
launch, lifting dequantization 34x from 8 GB/s to 286 GB/s for 0.47 LongBench-E
points. KV memory drops 1.97x at 8-bit.
`CUDA` `Triton` `PyTorch` `vLLM`

**[Firecracker live migration](https://github.com/lgoyal6/fc-live-migration)** · Moving a running microVM between hosts
Firecracker's maintainers closed the request for this. A ~250-line Rust patch to
the VMM adds it anyway: blackout under 18 ms against a 30 ms budget, with open
TCP connections surviving the host switch.
`Rust` `Go` `KVM`

**[GPU Broker](https://github.com/lgoyal6/gpu-broker)** · One queue across cloud, spot and a lab GPU
Survived 315 spot interruptions across 100 concurrent training jobs with zero
work lost. Reclaimed 16% of the club's shared credit pool from machines that were
held but not used.
`Python` `boto3` `FastAPI` · [live](https://gpu-broker-status.vercel.app)

**[decode-anatomy](https://github.com/lgoyal6/decode-anatomy)** · Where a decode step actually goes
Empirical roofline for an RTX A6000: compute-bound is 0.0% at every point, and
the biggest long-context kernel is a memcpy.
`PyTorch` `Nsight`

---

## Things people use

**[amac](https://github.com/lgoyal6/amac)** · Control plane for the AI coding agents on your Mac
Every session and automation on one page, on your phone, over Tailscale. Work
queue with fencing, proved against SIGKILL.
`Go` `tmux` `Tailscale`

**[Hacklist SF](https://luma.com/hacklist-sf)** · Hackathon calendar for the Bay Area
Around 100 subscribers. Seven keyless sources feed one classifier, and the
pipeline refuses to publish an event it cannot date, so nobody sees a dead
listing. [Source](https://github.com/lgoyal6/hacklist-sf)
`Next.js` `Cloudflare Workers` `iCalendar`

**[third-degree](https://github.com/lgoyal6/third-degree)** · Get grilled on a repo you built
Paste a repo, get a guided map of it, then up to 10 questions climbing from
language fundamentals to what breaks if you rename a schema field.
`TypeScript` `Next.js`

**[LooseAPI](https://github.com/lgoyal6/LooseAPI)** · Dev and subscription spend from your inbox
Projects cloud credit balances to zero before the account shuts off.
`JavaScript` `TypeScript`

---

## Open source contributions

---

## Recognition

**6x hackathon winner**

- [Vigil](https://github.com/lgoyal6/vigil) | 1st, Akash track, AWS Loop Engineering
- [Locus](https://github.com/lgoyal6/Locus) | 1st, Convex track
- [Antibody](https://github.com/psagar29/Antibody) | 1st, Runloop and Reflex tracks
- [EduForge](https://github.com/lgoyal6/EduForge) | 2nd, Replay track, AWS Self-Evolving
- [Pylon](https://github.com/lgoyal6/pylon) | 2nd, BowCapital Defense

**Also**

- OpenAI Student Collective, 1 of 140 U.S. leads across 70 universities from 25,000 applicants
- Published through the Lumiere Research Program, top 10% of ~200 submissions
- 2nd place, World Robotics Olympiad India | autonomous pipeline inspection robot

---

<details>
<summary><b>Full stack</b></summary>
<br>

**Languages**
C++20 · C · Go · Rust · Python · Java 21 · TypeScript · JavaScript · SQL · Bash

**Systems and debugging**
CMake · gdb · libFuzzer · ASan/UBSan/TSan · fault injection · deterministic
replay · perf profiling · netem · epoll · io_uring · write-ahead logging · group
commit · SWIM

**GPU and inference**
CUDA · Triton · PyTorch · Transformers · vLLM · CUDA graphs · KV-cache
quantization · Modal · ONNX

**Backend**
FastAPI · Spring Boot · Flask · Node · gRPC · REST · Pydantic · async job
pipelines · WebSockets · Redis

**Data and storage**
PostgreSQL · Redis · SQLite · Supabase · Cloudflare D1 · Arrow · Parquet

**Infra and tooling**
Docker · Kubernetes · AWS EKS/EC2/Lambda/S3/IAM · Terraform · Helm · Cloudflare
Workers · GitHub Actions · pytest · JUnit 5 · Playwright · k6 · Linux

**Frontend**
React · Next.js (App Router) · Tailwind · Zustand · Framer Motion · deck.gl ·
Mapbox GL · React Native

**ML**
scikit-learn · MONAI · LightGBM · OpenCV · NumPy · pandas · SciPy · torchaudio ·
Optuna · Ray Tune · LangGraph · LiteLLM

</details>

<details>
<summary><b>Freelance</b></summary>
<br>

I take on a limited number of contracts. Best fit:

- Backend and distributed systems: storage, queues, gateways, and the durability and concurrency guarantees underneath them
- LLM and agent systems: routing and cost optimization, RAG pipelines, eval harnesses
- ML and GPU infrastructure: training pipelines, inference serving, benchmarking that reports the losing axis

Reach me at lakshgoyal06@gmail.com.

</details>
