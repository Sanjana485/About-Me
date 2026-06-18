# Sanjana Garimella

`Master's in Data Science @ UC San Diego`

📬 sanjanagarimella6@gmail.com · [LinkedIn](https://www.linkedin.com/in/sanjana--garimella/)

---

I'm currently doing my Master's in Data Science at UC San Diego. Before this I spent 2.5 years as an SDE at IBM on the Security and Privacy by Design team for IBM Z, working on security data pipelines, vulnerability and CVE analysis, and an LLM-based provisioning system.

Right now I'm a research intern at Scripps Research on a clinical AI project in neurology, and leading MediRare on the side, a research project that tries to surface misdiagnosis patterns in rare autoimmune diseases by mining PubMed case reports with BioBERT, building a disease confusion graph, and connecting an LLM agent grounded in Orphanet, OMIM, and HPO.

The systems thinking from IBM and grad coursework got me thinking more broadly about data and ML at scale, from LLM inference behavior under long multi-turn workloads to distributed pipelines, recommender systems, and multi-database architectures. Doppelgamer and GridGreen came out of that thread.

---

## 🔧 Projects

---

### 🧬 MediRare - Rare Disease Misdiagnosis Detection

🔗 [Repository](https://github.com/sanjana-garimella/MediRare) · *Active Research · Project Lead · AISC San Diego*

Patients with rare autoimmune diseases like Lupus, Sjogren's, and MCTD wait 6+ years on average for a correct diagnosis. MediRare mines thousands of PubMed case reports to build a structured misdiagnosis knowledge graph, then connects an LLM reasoning agent to that graph, grounded in Orphanet, OMIM, and HPO, to generate explainable clinical reports with traceable reasoning chains.

- **CV pipeline** : ResNet/ViT classifying medical figures (rash photos, histology slides, lab charts) extracted from open-access PubMed PDFs
- **NLP pipeline** : BioBERT extracting misdiagnosis events → disease confusion knowledge graph via NetworkX
- **MCP reasoning agent** : vLLM + LangChain querying the confusion graph and structured rare disease databases

`PyTorch · BioBERT · PubMedBERT · vLLM · LangChain · MCP · FAISS · ChromaDB · NetworkX · Streamlit`

---

### 🎮 Doppelgamer - Behavioral Cloning + LLM Inference Benchmarking

🔗 [Repository](https://github.com/sanjana-garimella/dopplegamer)

LLM inference benchmark using game environments as stateful, multi-turn workload generators. Measures KV-cache memory growth, TTFT, TPOT, scheduling overhead, and prefix cache hit rate across HuggingFace, vLLM, Preble, and InferCept as context accumulates across turns. Also trains NGramImpostor and LSTMImpostor behavioral clones from player gameplay and runs Turing tests to measure clone detection rate.

22 environments · 9 agent types (PPO, BC+RL, ReAct LLM, adaptive router) · 7-table SQLite schema · 130 tests passing

`Python · PyTorch · Stable-Baselines3 · LangGraph · vLLM · Preble · InferCept · ChromaDB · FastAPI · Streamlit`

---

### 🏆 GridGreen - Carbon-Aware ML Copilot

🔗 [Repository](https://github.com/datahacks-2026/grid-green) · *DataHacks 2026 · Cloud Track Winner · MLH Best Use of Snowflake API*

AST-based carbon estimator using FLOPs scaling laws + MiniLM retrieval index over 58 curated model-swap pairs with benchmark retention citations + 48-hour EIA grid forecast for lowest-carbon scheduling. Delivered as a FastAPI web app and MCP server compatible with Claude Desktop, Cursor, and Claude Code.

| Avg compute reduction | CO2 reduction | Latency |
| --------------------- | ------------- | ------- |
| 77.6%                 | 37.0%         | <20ms   |

`Python · FastAPI · Next.js 15 · Sentence-Transformers · Snowflake Cortex · Databricks DLT · AWS SageMaker · Prophet · MCP`

---

### 🏥 MediDB - Multi-Database Clinical Decision Support

🔗 [Repository](https://github.com/eemilycchen/drug_safety_and_recommendation)

Patient ID + proposed drug → PostgreSQL EHR lookup → BioLORD-2023 vector similarity search over 50K+ FAERS adverse event records (Qdrant HNSW) → 10 alternatives ranked by similarity and FAERS % serious → Neo4j drug interaction validation → severity score with full evidence links. Four databases chosen for structural fit, not convenience.

`PostgreSQL · Neo4j · Qdrant · MongoDB · BioLORD-2023 · FastAPI · Docker · Streamlit`

---

### 🚕 NYC Taxi Big Data Pipeline

🔗 [Repository](https://github.com/blue-octopus235/dsc291-2026)

Distributed ETL pipeline over 3.4B NYC taxi records (57GB) on S3, reduced 3.41B rows to 2.9M aggregated rows with 660x Parquet compression, cut runtime from 40 to 15 minutes via adaptive PyArrow batch tuning. Distributed PCA with Davis-Kahan stability bounds, bootstrap validation, and geospatial demand analysis via interactive Folium maps.

`Python · Dask · PyArrow · AWS S3/EC2 · Folium · geopandas · scipy · XGBoost`

---

### 🤖 Socially-Aware Recommender System

🔗 [Repository](https://github.com/sanjana-garimella/socially-aware-spatial-markov-random-field-for-personalized-recommendation)

Top-N recommendation under 99.99% sparsity (Epinions dataset). Standard collaborative filtering collapses at this density, AUC 0.4997, essentially random. Proposed a Bayesian Markov model with MRF social smoothing that propagates preference signals through directed trust edges and PageRank, reaching AUC 0.6248, 25% over the Jaccard baseline and 6% over the IJCAI 2017 paper. Deployed with an A/B comparison UI on Hugging Face Spaces.

`Python · scikit-learn · NetworkX · FastAPI · Docker · Hugging Face Spaces`

---

### 🤖 ML Systems · Spring 2026

Started by building a reverse-mode autodiff engine from scratch, implementing forward and backward passes for core operators like MatMul, Softmax, and LayerNorm, then used it to train a decoder-only transformer without ever calling .backward(). From there, moved into GPU programming, writing a fused matmul+add+ReLU Triton kernel with shared memory tiling and fp16/fp32 accumulation on an NVIDIA A10. The distributed side covered MPI allreduce and alltoall from point-to-point primitives, tensor and data parallelism across 8 processes, and Mixture of Experts in both tensor parallel and expert parallel variants. Finished with LLM inference, going deep on PagedAttention, FlashAttention, quantization, and speculative decoding, and implementing a speculative decoder pairing Pythia-1.4B with Pythia-160M as the draft model.

`Python · PyTorch · Triton · MPI · CUDA`

---

### 📐 Language Models as Cognitive Models · Spring 2026

Studied how LLMs behave as test subjects for linguistic and cognitive questions, covering language acquisition, surprisal theory, and mechanistic interpretability. Co-presented Sparse Feature Circuits (Marks et al., ICLR 2025), which shows that a few hundred interpretable SAE features can explain model behavior on syntax tasks where neuron circuits need tens of thousands, and that those circuits are legible enough to enable targeted model editing. For the final project, drew from how children learn grammar despite noisy input and simulated the same for language models by training LSTMs and RNNGs on subject-verb agreement corpora with controlled levels of grammatical noise. Ran the full training sweep, built the checkpointing and trajectory evaluation pipeline, and analyzed how models shift from hierarchical agreement rules toward linear heuristics as noise increases.

`minicons · HuggingFace · Pythia · GPT-2 · BERT · BLiMP · PyTorch`

---

## 📚 Writing

🤖 [Tackling Cold-Start Recommendations with Socially-Aware Spatial Markov Models](https://www.linkedin.com/pulse/tackling-cold-start-recommendations-socially-aware-markov-garimella-9sufc)

📊 [Role of Data Science in Healthcare](https://www.linkedin.com/pulse/video-blog-role-data-science-health-care-g-g-sanjana)

⚙️ [Carbon-aware Machine Learning Systems: Hyperparameters and Hidden Compute Costs](https://www.linkedin.com/pulse/carbon-footprint-hyperparameter-weve-been-overlooking-garimella-7bbfc)
