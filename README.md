# Sanjana Garimella

`Master's in Data Science @ UC San Diego`

📬 sanjanagarimella6@gmail.com · [LinkedIn](https://www.linkedin.com/in/sanjana--garimella/)

---

Graduate student at UC San Diego working on machine learning systems, large-scale data engineering, and language model–driven AI systems. My work sits at the intersection of data infrastructure, retrieval systems, and agent-based LLM applications, with an emphasis on building systems that remain reliable under scale, distribution, and real-world operational constraints.

Across multiple projects, I design and implement end-to-end pipelines that transform large, heterogeneous datasets into structured representations for modeling and decision-making. This includes distributed processing over billions of records, multi-database architectures that combine relational, graph, and vector stores, and retrieval systems that integrate embedding-based search with structured filtering. A recurring focus is ensuring that these systems are not only performant but also auditable, reproducible, and resilient to data drift and schema variability.

On the language model side, my work involves building retrieval-augmented and tool-augmented systems where LLMs function as reasoning components inside larger pipelines rather than standalone interfaces. This includes designing ReAct-style agent workflows, structured tool invocation patterns, and multi-step reasoning systems grounded in external knowledge sources such as biomedical literature and structured ontologies. I also work with inference-layer constraints such as KV cache behavior, batching strategies, and latency–throughput trade-offs in serving frameworks like vLLM, where system-level efficiency directly affects usability at scale.

In parallel, I work on multi-agent and behavioral modeling systems where learned policies, behavioral cloning, and reinforcement learning agents operate in interactive environments. These systems are used both for evaluation and benchmarking of inference systems and for studying behavioral consistency, fidelity, and generalization under sequential decision-making settings.

A significant portion of my work also involves multimodal and domain-specific applications, including biomedical NLP systems that extract structured knowledge from scientific literature and clinical datasets, as well as recommendation and decision-support systems that combine graph-based reasoning, vector similarity search, and probabilistic modeling. These systems emphasize traceability of outputs and grounding in verifiable data sources rather than purely generative outputs.

At the infrastructure level, I build distributed data pipelines and ML systems that integrate batch processing frameworks, cloud services, and multi-store architectures. This includes optimizing data ingestion, compression, and transformation workflows, as well as designing systems that scale across high-volume datasets while maintaining correctness guarantees through schema enforcement, indexing strategies, and validation layers.

Overall, my work focuses on building AI systems that are not only model-centric but system-centric—where data pipelines, retrieval mechanisms, inference efficiency, and agentic reasoning components are designed together to produce reliable, scalable, and interpretable outcomes.


---

## 🔧 Projects

---

### 🧬 MediRare — Rare Disease Misdiagnosis Detection
🔗 [Repository](https://github.com/sanjana-garimella/MediRare) · *Active Research · Project Lead · AISC San Diego · Targeting AMIA / JBI*

Patients with rare autoimmune diseases like Lupus, Sjogren's, and MCTD wait 6+ years on average for a correct diagnosis. MediRare mines thousands of PubMed case reports to build a structured misdiagnosis knowledge graph, then connects an LLM reasoning agent to that graph — grounded in Orphanet, OMIM, and HPO — to generate explainable clinical reports with traceable reasoning chains.

- **CV pipeline** — ResNet/ViT classifying medical figures (rash photos, histology slides, lab charts) extracted from open-access PubMed PDFs
- **NLP pipeline** — BioBERT extracting misdiagnosis events → disease confusion knowledge graph via NetworkX
- **MCP reasoning agent** — vLLM + LangChain querying the confusion graph and structured rare disease databases

`PyTorch · BioBERT · PubMedBERT · vLLM · LangChain · MCP · FAISS · ChromaDB · NetworkX · Streamlit`

---

### 🎮 Doppelgamer — Behavioral Cloning + LLM Inference Benchmarking
🔗 [Repository](https://github.com/sanjana-garimella/doppelgamer)

LLM inference benchmark using game environments as stateful, multi-turn workload generators — the condition most production agents run under but most benchmarks don't test. Measures KV-cache memory growth, TTFT, TPOT, scheduling overhead, and prefix cache hit rate across HuggingFace, vLLM, Preble, and InferCept as context accumulates across turns. Also trains NGramImpostor and LSTMImpostor behavioral clones from player gameplay and runs Turing tests to measure clone detection rate.

22 environments · 9 agent types (PPO, BC+RL, ReAct LLM, adaptive router) · 7-table SQLite schema · 130 tests passing

`Python · PyTorch · Stable-Baselines3 · LangGraph · vLLM · Preble · InferCept · ChromaDB · FastAPI · Streamlit`

---

### 🏆 GridGreen — Carbon-Aware ML Copilot
🔗 [Repository](https://github.com/sanjana-garimella/green-watts) · *DataHacks 2026 · Cloud Track Winner · MLH Best Use of Snowflake API*

AST-based carbon estimator using FLOPs scaling laws + MiniLM retrieval index over 58 curated model-swap pairs with benchmark retention citations + 48-hour EIA grid forecast for lowest-carbon scheduling. Delivered as a FastAPI web app and MCP server compatible with Claude Desktop, Cursor, and Claude Code.

| Success rate | Avg compute reduction | CO2 reduction | Latency |
|---|---|---|---|
| 100% (12/12) | 77.6% | 37.0% | <20ms |

`Python · FastAPI · Next.js 15 · Sentence-Transformers · Snowflake Cortex · Databricks DLT · AWS SageMaker · Prophet · MCP`

---

### 🏥 MediDB — Multi-Database Clinical Decision Support
🔗 [Repository](https://github.com/eemilycchen/drug_safety_and_recommendation)

Patient ID + proposed drug → PostgreSQL EHR lookup → BioLORD-2023 vector similarity search over 50K+ FAERS adverse event records (Qdrant HNSW) → 10 alternatives ranked by similarity and FAERS % serious → Neo4j drug interaction validation → severity score with full evidence links. Four databases chosen for structural fit, not convenience.

`PostgreSQL · Neo4j · Qdrant · MongoDB · BioLORD-2023 · FastAPI · Docker · Streamlit`

---

### 🚕 NYC Taxi Big Data Pipeline
🔗 [Repository](https://github.com/blue-octopus235/dsc291-2026)

Distributed ETL pipeline over 3.4B NYC taxi records (57GB) on S3 — reduced 3.41B rows to 2.9M aggregated rows with 660x Parquet compression, cut runtime from 40 to 15 minutes via adaptive PyArrow batch tuning. Distributed PCA with Davis-Kahan stability bounds, bootstrap validation, and geospatial demand analysis via interactive Folium maps.

`Python · Dask · PyArrow · AWS S3/EC2 · Folium · geopandas · scipy · XGBoost`

---

### 🤖 Socially-Aware Recommender System
🔗 [Repository](https://github.com/sanjana-garimella/socially-aware-spatial-markov-random-field-for-personalized-recommendation)

Top-N recommendation under 99.99% sparsity (Epinions dataset). Standard collaborative filtering collapses at this density — AUC 0.4997, essentially random. Proposed a Bayesian Markov model with MRF social smoothing that propagates preference signals through directed trust edges and PageRank, reaching AUC 0.6248 — 25% over the Jaccard baseline and 6% over the IJCAI 2017 paper. Deployed with an A/B comparison UI on Hugging Face Spaces.

`Python · scikit-learn · NetworkX · FastAPI · Docker · Hugging Face Spaces`

---

### 🤖 DSC 291 ML Systems (Prof. Hao Zhang) — Spring 2026

- Reverse-mode autodiff engine from scratch; trained a decoder-only transformer using only this engine — no `loss.backward()`
- Triton fused matmul+add+ReLU kernel on NVIDIA A10: shared memory tiling, fp16/fp32 accumulation, operator fusion, block config grid search
- MPI `myAllreduce` and `myAlltoall` from point-to-point primitives across 8 processes; tensor + data parallel FC layer sharding

---

### 📐 Language Models as Cognitive Models — Spring 2026

Surprisal-based evaluation of LM syntactic knowledge using BLiMP minimal pairs across anaphor agreement, wh-island constraints, and Principle A c-command. Built 3 custom minimal pair datasets; tracked Pythia-70m across training checkpoints. Pythia-160m outperforms 70m on distributional tasks, underperforms on structural ones — scale does not substitute for what the training data encodes.

`minicons · HuggingFace · Pythia · GPT-2 · BERT · BLiMP · PyTorch`

---

## 🧰 Technical Skills

Work across the full ML stack — from writing GPU kernels and distributed training primitives (Triton, MPI) to building retrieval pipelines (Qdrant, FAISS, ChromaDB), LLM agents with grounded reasoning (LangChain, LangGraph, MCP, vLLM), and production data infrastructure (Dask, PyArrow, Databricks, AWS). Primary language is Python; also use SQL, TypeScript, R, and Bash regularly.

**ML & DL** — PyTorch · scikit-learn · HuggingFace Transformers · XGBoost · Stable-Baselines3 · Detectron2 · pyGAM

**LLMs, NLP & Agents** — LLaMA (fine-tuning) · BioBERT · PubMedBERT · BioLORD-2023 · Sentence-Transformers · LangChain · LangGraph · vLLM · MCP · RAG

**ML Systems & GPU** — Triton · MPI/mpi4py · Tensor + data parallelism · Autodiff from scratch · fp16/fp32 mixed precision

**Vector Search** — Qdrant (HNSW, payload indexes) · FAISS · ChromaDB · Snowflake Cortex

**Data Engineering** — Dask · PyArrow · Delta Lake · Databricks (DLT, MLflow) · Prophet · Distributed ETL

**Databases** — PostgreSQL · Neo4j · MongoDB · Qdrant · SQLite · InfluxDB · Snowflake · MySQL

**Infrastructure** — FastAPI · Next.js 15 · Docker · AWS (S3, EC2, SageMaker) · NVIDIA Brev · W&B · Jenkins · pytest · Linux

---

## 🏅 Achievements

🏆 **DataHacks 2026 — Cloud Track Winner + MLH Best Use of Snowflake API** for GridGreen

🏆 **Star of the Month — IBM** for enhancing open-source vulnerability tracking and automating onboarding workflows across global teams

🌟 **Infrastructure All-Hands Recognition — IBM** for streamlining SPbD security onboarding across 18 subsystems

🎖 **People's Choice Award — IBM Developer Jumpstart** for a LLaMA-based provisioning system that cut multi-cloud infrastructure costs by 40%

---

## 📚 Writing

🤖 [Tackling Cold-Start Recommendations with Socially-Aware Spatial Markov Models](https://www.linkedin.com/pulse/tackling-cold-start-recommendations-socially-aware-markov-garimella-9sufc)

📊 [Role of Data Science in Healthcare](https://www.linkedin.com/pulse/video-blog-role-data-science-health-care-g-g-sanjana)

---
