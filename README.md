# Sanjana Garimella

`Master's in Data Science @ UC San Diego`

📬 sanjanagarimella6@gmail.com · [LinkedIn](https://www.linkedin.com/in/sanjana--garimella/)

---

SDE making the move into data science, currently doing my Master's at UC San Diego. I spent my early career at IBM building infrastructure, which left me with a habit of asking structural questions before ML ones, why this database, why this scheduler, where does the latency actually come from.
At IBM I built a LLaMA-based provisioning system that cut multi-cloud costs by 40%, and the more interesting question to me wasn't whether it worked but why, how much of that was the model versus the infrastructure decisions around it. That question followed me into grad school. Most LLM inference benchmarks test single prompts, but production agents run long stateful conversations where KV-cache pressure and scheduling overhead are the actual constraints. I needed a workload generator that could replicate that, game environments turned out to be a natural fit, stateful, multi-turn, and controllable. Once you're measuring compute that carefully, you start caring about when and where you're running it, which led me to building a carbon-aware scheduling tool on top of live grid forecasts.
The clinical work came from a different direction. Six years is how long patients with rare autoimmune diseases wait for a correct diagnosis on average. The misdiagnosis patterns exist in the literature, they're just locked inside thousands of unstructured case reports. That's a retrieval and reasoning problem, which turns out to be a good place to apply everything I'd learned about vector databases, knowledge graphs, and LLM agents.


---

## 🔧 Projects

---

### 🧬 MediRare - Rare Disease Misdiagnosis Detection
🔗 [Repository](https://github.com/sanjana-garimella/MediRare) · *Active Research · Project Lead · AISC San Diego · Targeting AMIA / JBI*

Patients with rare autoimmune diseases like Lupus, Sjogren's, and MCTD wait 6+ years on average for a correct diagnosis. MediRare mines thousands of PubMed case reports to build a structured misdiagnosis knowledge graph, then connects an LLM reasoning agent to that graph, grounded in Orphanet, OMIM, and HPO, to generate explainable clinical reports with traceable reasoning chains.

- **CV pipeline** : ResNet/ViT classifying medical figures (rash photos, histology slides, lab charts) extracted from open-access PubMed PDFs
- **NLP pipeline** : BioBERT extracting misdiagnosis events → disease confusion knowledge graph via NetworkX
- **MCP reasoning agent** : vLLM + LangChain querying the confusion graph and structured rare disease databases

`PyTorch · BioBERT · PubMedBERT · vLLM · LangChain · MCP · FAISS · ChromaDB · NetworkX · Streamlit`

---

### 🎮 Doppelgamer - Behavioral Cloning + LLM Inference Benchmarking
🔗 [Repository](https://github.com/sanjana-garimella/dopplegamer)

LLM inference benchmark using game environments as stateful, multi-turn workload generators , the condition most production agents run under but most benchmarks don't test. Measures KV-cache memory growth, TTFT, TPOT, scheduling overhead, and prefix cache hit rate across HuggingFace, vLLM, Preble, and InferCept as context accumulates across turns. Also trains NGramImpostor and LSTMImpostor behavioral clones from player gameplay and runs Turing tests to measure clone detection rate.

22 environments · 9 agent types (PPO, BC+RL, ReAct LLM, adaptive router) · 7-table SQLite schema · 130 tests passing

`Python · PyTorch · Stable-Baselines3 · LangGraph · vLLM · Preble · InferCept · ChromaDB · FastAPI · Streamlit`

---

### 🏆 GridGreen - Carbon-Aware ML Copilot
🔗 [Repository](https://github.com/datahacks-2026/grid-green) · *DataHacks 2026 · Cloud Track Winner · MLH Best Use of Snowflake API*

AST-based carbon estimator using FLOPs scaling laws + MiniLM retrieval index over 58 curated model-swap pairs with benchmark retention citations + 48-hour EIA grid forecast for lowest-carbon scheduling. Delivered as a FastAPI web app and MCP server compatible with Claude Desktop, Cursor, and Claude Code.

| Avg compute reduction | CO2 reduction | Latency |
|---|---|---|
| 77.6% | 37.0% | <20ms |

`Python · FastAPI · Next.js 15 · Sentence-Transformers · Snowflake Cortex · Databricks DLT · AWS SageMaker · Prophet · MCP`

---

### 🏥 MediDB - Multi-Database Clinical Decision Support
🔗 [Repository](https://github.com/eemilycchen/drug_safety_and_recommendation)

Patient ID + proposed drug → PostgreSQL EHR lookup → BioLORD-2023 vector similarity search over 50K+ FAERS adverse event records (Qdrant HNSW) → 10 alternatives ranked by similarity and FAERS % serious → Neo4j drug interaction validation → severity score with full evidence links. Four databases chosen for structural fit, not convenience.

`PostgreSQL · Neo4j · Qdrant · MongoDB · BioLORD-2023 · FastAPI · Docker · Streamlit`

---

### 🚕 NYC Taxi Big Data Pipeline
🔗 [Repository](https://github.com/blue-octopus235/dsc291-2026)

Distributed ETL pipeline over 3.4B NYC taxi records (57GB) on S3 , reduced 3.41B rows to 2.9M aggregated rows with 660x Parquet compression, cut runtime from 40 to 15 minutes via adaptive PyArrow batch tuning. Distributed PCA with Davis-Kahan stability bounds, bootstrap validation, and geospatial demand analysis via interactive Folium maps.

`Python · Dask · PyArrow · AWS S3/EC2 · Folium · geopandas · scipy · XGBoost`

---

### 🤖 Socially-Aware Recommender System
🔗 [Repository](https://github.com/sanjana-garimella/socially-aware-spatial-markov-random-field-for-personalized-recommendation)

Top-N recommendation under 99.99% sparsity (Epinions dataset). Standard collaborative filtering collapses at this density , AUC 0.4997, essentially random. Proposed a Bayesian Markov model with MRF social smoothing that propagates preference signals through directed trust edges and PageRank, reaching AUC 0.6248 , 25% over the Jaccard baseline and 6% over the IJCAI 2017 paper. Deployed with an A/B comparison UI on Hugging Face Spaces.

`Python · scikit-learn · NetworkX · FastAPI · Docker · Hugging Face Spaces`

---

### 🤖 ML Systems 

Built a reverse-mode autodiff engine from scratch and trained a decoder-only transformer on it without ever calling `.backward()`. Wrote Triton GPU kernels with shared memory tiling and operator fusion. Implemented MPI allreduce/alltoall from point-to-point primitives and applied tensor and data parallelism across 8 processes. Studied LLM inference in depth — vLLM, PagedAttention, FlashAttention, quantization, speculative decoding — through coursework and guest lectures from the engineers who built them.


---

### 📐 Language Models as Cognitive Models 

Explored LLMs as cognitive test subjects across language acquisition, processing, and mechanistic interpretability. Co-presented on Sparse Feature Circuits (Marks et al., ICLR 2025) — ~100 interpretable SAE features explain model behavior on syntax tasks where neuron circuits need thousands, and circuits are legible enough to enable targeted model editing. For the BLiMP evaluation, built custom minimal pair datasets across relative clause agreement, wh-islands, and Principle A, tracking Pythia across training checkpoints. Key finding: Pythia-160M beats 70M on distributional tasks but fails on structural ones — scale doesn't fix what the training data never encoded.


`minicons · HuggingFace · Pythia · GPT-2 · BERT · BLiMP · PyTorch`

---

## 🧰 Technical Skills

Python is my primary language. I also use SQL, Java, and C++ when needed.
ML & DL : PyTorch · HuggingFace Transformers · XGBoost · scikit-learn
LLMs & Agents : Open-source (LLaMA, Qwen, DeepSeek, Mistral, BioBERT, PubMedBERT, Phi) · Closed-source (OpenAI, Anthropic, Gemini) ·  LangChain · LangGraph · vLLM · MCP
ML Systems : Triton · MPI · Tensor + data parallelism · Autodiff from scratch · fp16/fp32 mixed precision
Retrieval & Databases : Qdrant · FAISS · ChromaDB · PostgreSQL · Neo4j · MongoDB · Snowflake
Data Engineering : Dask · PyArrow · Databricks · Delta Lake · Distributed ETL
Infrastructure : FastAPI · Docker · AWS (S3, EC2, SageMaker) · W&B · Linux

---

## 🏅 Achievements

🏆 **DataHacks 2026: Cloud Track Winner + MLH Best Use of Snowflake API** for GridGreen

🏆 **Star of the Month, IBM** for enhancing open-source vulnerability tracking and automating onboarding workflows across global teams

🌟 **Infrastructure All-Hands Recognition, IBM** for streamlining SPbD security onboarding across 18 subsystems

🎖 **People's Choice Award, IBM Developer Jumpstart** for a LLaMA-based provisioning system that cut multi-cloud infrastructure costs by 40%

---

## 📚 Writing

🤖 [Tackling Cold-Start Recommendations with Socially-Aware Spatial Markov Models](https://www.linkedin.com/pulse/tackling-cold-start-recommendations-socially-aware-markov-garimella-9sufc)

📊 [Role of Data Science in Healthcare](https://www.linkedin.com/pulse/video-blog-role-data-science-health-care-g-g-sanjana)

⚙️ [Carbon-aware Machine Learning Systems: Hyperparameters and Hidden Compute Costs](https://www.linkedin.com/pulse/carbon-footprint-hyperparameter-weve-been-overlooking-garimella-7bbfc)

---
