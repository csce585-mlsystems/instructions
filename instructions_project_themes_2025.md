# CSCE 585: Machine Learning Systems  
## Course Projects (Fall 2025)

### Overview
The capstone project is a major component of CSCE 585. Students will work in teams to **design, implement, and evaluate a machine learning system** that addresses a real systems challenge.  

Projects can take the form of:
- **Replication**: Reproduce results from an MLSys research paper, validate findings, and extend experiments.  
- **Extension**: Improve upon an existing system or framework (e.g., adding new optimization, monitoring, or evaluation features).  
- **Exploration**: Investigate an open-ended systems challenge (e.g., energy efficiency, agentic AI orchestration, robustness).  

### Goals
By the end of the project, you should demonstrate:
1. Ability to **formulate a systems problem** around ML pipelines, serving, monitoring, or trustworthiness.  
2. Skills in **designing reproducible experiments** (clear baselines, metrics, evaluation methodology).  
3. Critical analysis of **trade-offs**: latency vs. throughput, cost vs. accuracy, scalability vs. reliability.  
4. Clear **communication** of findings in a written report and oral presentation.  

---

## Project Timeline
- **Week 4 (Milestone 1: Motivation)**  
  Submit a 1–2 page proposal including:  
  - Problem statement and motivation  
  - Related work (2–3 references)  
  - Initial hypotheses and goals  

- **Week 8 (Milestone 2: Design & Initial Experiments)**  
  Submit a short report (3–4 pages) including:  
  - System design overview (diagram, components)  
  - Preliminary experiments (at least one plot/table)  
  - Risks and adjustments  

- **Week 15 (Final Deliverables)**  
  - **Report (8–10 pages, conference style)**  
  - **Presentation (10–12 minutes)**  

---

## Suggested Themes & Example Ideas

### 1. LLM Serving & Efficiency
- Replicate throughput/latency benchmarks with **vLLM**, **TensorRT-LLM**, or **Ray Serve**.  
- Evaluate trade-offs: batching, KV-cache reuse, speculative decoding.  
- Compare dense vs. quantized models (e.g., GPTQ, AWQ).  

**Example Prompt:**  
> *Measure how different batching strategies affect throughput and cost in vLLM compared to HuggingFace TGI.*  

---

### 2. Agentic AI Systems
Agentic AI systems combine LLMs with **planning, tool use, and orchestration**.  

- Build a **multi-agent workflow** using AutoGen, crewAI, or LangGraph.  
- Evaluate performance on benchmarks: **SWE-bench**, **AgentBench**, **WebArena**.  
- Compare **workflow patterns** (prompt chaining vs. orchestrator–workers).  
- Measure **cost, latency, and reliability** of agent pipelines.  

**Example Prompt:**  
> *Evaluate SWE-bench performance using a custom AutoGen multi-agent setup, and analyze cost/latency trade-offs.*  

---

### 3. Data & Monitoring
- Build a system for **data versioning and monitoring drift** in an ML pipeline.  
- Compare drift detection methods on streaming data.  
- Implement **privacy auditing or data lineage tracking** for LLMs.  

**Example Prompt:**  
> *Design a monitoring dashboard for data drift in a production ML pipeline, and evaluate it using a streaming dataset.*  

---

### 4. Energy & Sustainability
- Profile **energy usage** of ML inference or training across hardware (CPU, GPU, NPU).  
- Compare carbon footprint of different platforms.  
- Experiment with **carbon-aware scheduling** (delay jobs when grid is “dirty”).  

**Example Prompt:**  
> *Profile the carbon footprint of LLaMA-7B inference on GPU vs. CPU vs. Apple M-series NPU.*  

---

### 5. Trustworthy ML Systems
- Build an **adversarial robustness testing suite** (e.g., FGSM/PGD attacks, jailbreak prompts).  
- Replicate experiments from **Constitutional AI** (Anthropic).  
- Explore **causal methods for debugging ML pipelines**.  

**Example Prompt:**  
> *Develop a robustness evaluation suite for LLMs, including prompt-injection and jailbreak attacks.*  

---

### 6. Replication Projects
Choose a recent MLSys paper and replicate its results. Some suggestions:
- **InferLine**: ML inference pipeline composition  
- **vLLM**: Fast LLM serving with PagedAttention  
- **FlashAttention**: Memory-efficient Transformer attention  
- **MLPerf**: Benchmarking ML training/inference systems  
- **Voyager**: LLM-based embodied agent  

**Example Prompt:**  
> *Replicate the vLLM paper’s throughput/latency experiments on your chosen hardware and compare against HuggingFace TGI.*  

---

## Deliverables
1. **Proposal (Week 4)**  
   - Problem statement, goals, related work  
2. **Intermediate Report (Week 8)**  
   - System design + initial experiments  
3. **Final Report (Week 15)**  
   - 8–10 page writeup in conference format  
   - Must include: motivation, design, methodology, evaluation, related work, conclusion  
4. **Presentation (Week 15)**  
   - 10–12 minute talk with slides  

---

## Evaluation Criteria
- **Novelty & Challenge (20%)** – Is the project ambitious and MLSys-relevant?  
- **Experimentation & Rigor (30%)** – Are experiments reproducible, well-designed, with clear metrics?  
- **System Design (20%)** – Is there a coherent system or pipeline built?  
- **Communication (20%)** – Is the report clear, and the presentation engaging?  
- **Milestone Progress (10%)** – Did the team deliver on time?  

---

## Resources
- [vLLM GitHub](https://github.com/vllm-project/vllm)  
- [LangChain Documentation](https://python.langchain.com/)  
- [AutoGen Framework](https://microsoft.github.io/autogen/)  
- [MLPerf Benchmarks](https://mlcommons.org/en/mlperf/)  
- [Chip Huyen – Designing Machine Learning Systems](https://huyenchip.com/ml-sys/)  

---

**Tip:** Pick a project that excites you — whether replicating a cutting-edge paper, building an agent pipeline, or tackling system bottlenecks. The goal is to learn how **ML models become ML systems in practice**.