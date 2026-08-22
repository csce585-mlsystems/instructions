# CSCE 585: Project Proposal and Presentation Guidelines

These instructions explain how to propose, refine, and present a semester project for CSCE 585: Machine Learning Systems.

The project should address a real machine-learning systems question. A strong project does more than apply a model to a dataset: it studies how an ML system is designed, implemented, operated, measured, or improved. Concretely, a project should combine **an ML component** (a model class, algorithm, or learned artifact) **with a systems component** (a platform, performance, scalability, reliability, or trustworthy-AI concern such as bias, robustness, privacy, security, or explainability). A model trained purely for accuracy, with no systems question attached, is not a fit for this course.

The project is the largest part of the course grade (see the syllabus for the current weighting) and no late work is accepted for any deliverable below, so build buffer time into your team's schedule rather than targeting deadlines exactly. Teams must be finalized early in the semester per the syllabus's team-formation policy. If anything here appears to conflict with the syllabus or a class announcement, the syllabus and announcements govern.

For course logistics beyond this document, see [Lectures](https://pooyanjamshidi.github.io/mls/lectures/), [Policies](https://pooyanjamshidi.github.io/mls/policies/), and the [Projects](https://pooyanjamshidi.github.io/mls/projects/) page, which also links examples from past semesters worth skimming for calibration before you scope your own project.

## At a Glance

| Deliverable | Due | Format | Main purpose |
|---|---:|---|---|
| Project idea presentation | August 28 | 3-minute talk + 2-minute feedback; 1 title slide + 3 content slides | Test whether the problem, proposed solution, and evaluation plan are clear and feasible |
| Written project proposal | September 4 | Markdown file in the team's GitHub repository | Turn the pitch into a concrete, evidence-based, actionable plan |
| Final presentation | Week 15; exact date announced in class | 10-12 minute talk; concise visual slides | Communicate what the team built, how it was evaluated, what was learned, and what evidence supports the conclusions |

## 1. Choose a Project with a Systems Question

Your project should fit one of these broad types:

1. **Replication and extension:** Reproduce important results from an ML systems paper, validate them on your hardware or workload, and add a meaningful extension.
2. **Extension of current research:** Add a clearly defined new systems contribution to research already underway. State what already exists, what is new in this course project, and discuss the scope with your research advisor.
3. **Real-world system or tool:** Address a genuine problem experienced by identifiable users or practitioners. Explain who has the problem, why current approaches are insufficient, and how you will determine whether your system helps.
4. **Exploration of an open systems question:** Investigate a focused question about efficiency, reliability, scalability, monitoring, security, sustainability, or orchestration.

Good projects have all of the following:

- a clear ML systems problem, not only a model-accuracy objective;
- one or more testable research questions or hypotheses;
- a system, prototype, benchmark, or reproducible experimental artifact;
- meaningful baselines and measurable outcomes;
- a scope that can produce evidence within one semester;
- an explicit plan for risks, compute limits, data access, and team responsibilities.

**Ask about compute and data access early.** GPU access, model weights, API quota, and datasets are common early bottlenecks in ML systems projects, and lead times can run longer than expected. Identify what your project needs during the idea-presentation stage, not after the proposal, so any request can be resolved before it blocks Week 1 or 2 of your timeline.

### Turning a broad topic into a project question

| Too broad | Better project question |
|---|---|
| "Study LLM inference" | How do continuous batching and prefix caching affect p50/p95 latency, throughput, and GPU memory under three request-load patterns? |
| "Build a multi-agent system" | Does an orchestrator-worker workflow improve task success enough to justify its added latency and token cost compared with a single-agent baseline? |
| "Detect data drift" | Which drift detector provides the best detection-delay/false-alarm trade-off under controlled gradual and abrupt shifts in a streaming pipeline? |
| "Make ML greener" | How do quantization and batch size change energy per generated token, latency, and output quality on one fixed hardware platform? |
| "Test LLM security" | How effective are three prompt-injection defenses against a fixed attack suite, and what utility, latency, and cost penalties do they introduce? |

## 2. Project Idea Presentation

### Format and timing

- **Total slot:** 5 minutes per team.
- **Presentation:** 3 minutes.
- **Feedback and discussion:** 2 minutes.
- **Slides:** one unnumbered title slide plus exactly three content slides: Problem, Solution, and Evaluation.
- Rehearse with a timer. The class must finish all team presentations, so the time limit will be enforced.
- If a team member cannot attend, another member must be ready to present. Volunteer for an early slot if you must leave class early.

### Title slide: identity and team

Include:

- a short, specific title that communicates the project;
- each team member's name, major, and role;
- optional high-resolution headshots;
- one brief sentence explaining why the team is well matched to the problem;
- the team's planned coordination rhythm, such as a weekly meeting and an asynchronous progress check.

**Example title:** *When Does Prefix Caching Pay Off? A Workload-Aware Study of LLM Serving*

### Slide 1: Problem

Answer:

- What exact problem will you investigate?
- Who experiences this problem, and in what setting?
- Why does it matter from an ML systems perspective?
- Why is the team interested and equipped to study it?
- Which project type does it represent?
- What is the central research question or hypothesis?

**Example:** "We hypothesize that prefix caching reduces p95 latency for workloads with repeated system prompts, but provides little benefit and may waste memory when prefix reuse is low."

### Slide 2: Proposed solution

Answer:

- What will you build, modify, reproduce, or compare?
- What is the primary artifact: code, benchmark harness, service, dashboard, dataset, or analysis?
- Which existing implementations will you reuse?
- What will your team add or change?
- What is explicitly outside the project scope?

Prefer one readable architecture or workflow figure. Visually distinguish existing components from components your team will create or modify.

**Example:** Show a request generator, two serving configurations, telemetry collection, and an analysis pipeline. Mark the workload generator and experiment harness as the team's contributions.

### Slide 3: Evaluation

State the evaluation plan before implementation begins:

- **Research questions:** What will each experiment answer?
- **Independent variables:** What will you change, such as batch size, request rate, model size, quantization, or orchestration pattern?
- **Baselines:** What current or simpler approach will you compare against?
- **Metrics:** Include both system metrics and task-quality metrics when relevant.
- **Workloads and data:** What datasets, traces, prompts, or synthetic loads will you use?
- **Rigor:** How many repetitions, random seeds, or workloads will you use? How will you report variability?
- **Expected evidence:** What plots, tables, or qualitative examples will appear in the final report?

Useful systems metrics include throughput, time to first token, end-to-end latency, p50/p95/p99 latency, memory use, energy, availability, failure rate, recovery time, and cost per request. Pair them with a task-quality measure when an optimization may change output quality.

**Example evaluation matrix:**

| Factor | Values |
|---|---|
| Serving configuration | no cache; prefix cache |
| Prefix-reuse rate | 0%, 25%, 50%, 75%, 100% |
| Offered load | low, medium, saturation |
| Primary outcomes | p50/p95 latency, requests/s, peak GPU memory |
| Controls | same model, hardware, prompts, output lengths, software versions |

### Slide design checklist

- Use high-resolution images and readable diagrams.
- Prefer one message per slide and minimal prose.
- Label axes, units, legends, baselines, and sources.
- Do not use screenshots of dense text or code.
- Use consistent typography, colors, and terminology.
- Test the deck on the classroom display and export a backup PDF.
- End on the Evaluation slide so the audience can give targeted feedback.

## 3. Capture and Use Feedback

Before presenting, assign one team member as the **scribe**. During the two-minute discussion, the scribe should record all verbal feedback, including questions, concerns, suggested papers, baselines, metrics, and scope changes.

At the beginning of the written proposal, include a feedback table:

| Feedback received | Source/date | Team response | Change made or reason not adopted |
|---|---|---|---|
| Add a simpler baseline | Class discussion, Aug. 28 | Accepted | Added the default serving configuration as Baseline 1 |
| Test three model sizes | Class discussion, Aug. 28 | Partially accepted | We will test two sizes because of GPU limits and document this constraint |

The goal is not to accept every suggestion. The goal is to show that the team considered the feedback and made a reasoned decision.

## 4. Written Project Proposal

### Submission requirements

- Submit a Markdown (`.md`) file in the team's GitHub repository by **September 4**.
- Add the repository link to the course project spreadsheet shared through Piazza.
- Use stable links or commit hashes when referring to external code.
- Ensure the instructor can access the repository.

### Required structure

Use the following headings.

```markdown
# Project Title

## Team and Responsibilities
## Feedback Received and Responses
## Problem and Motivation
## Research Questions and Hypotheses
## Related Work
## Proposed System or Approach
## Evaluation Plan
## Expected Deliverables
## Timeline and Milestones
## Risks and Mitigations
## Reproducibility Plan
## References
```

### What each section should contain

#### Team and responsibilities

List each member's role and relevant strengths. Explain how work will be coordinated, how frequently the team will meet, and how decisions and progress will be documented. Responsibilities may evolve, but every member should contribute to both the technical work and understanding the results. Keep a lightweight, ongoing record of who did what — commit history plus short per-milestone notes in the README is enough — so individual contribution is visible if the team is asked about it later.

#### Problem and motivation

Define the system context, affected users, current limitation, and why the problem matters. Support factual claims with citations or preliminary evidence. Avoid opening with a solution before the problem is clear. If the system under study touches privacy, fairness, security, safety, or environmental cost, name the relevant risk briefly here — a sentence or two is enough unless the risk is central to the project.

#### Research questions and hypotheses

Write two to four focused questions. When possible, make a directional prediction.

**Example:**

- RQ1: How does request concurrency affect tail latency with and without continuous batching?
- RQ2: At what load does batching improve throughput but violate the p95 latency target?
- H1: Continuous batching will increase peak throughput by at least 20%, but its benefit will diminish for long, heterogeneous prompts.

#### Related work

Include at least two or three key references. For each reference, state what it contributes, which result or artifact you rely on, and how your project differs. A list of paper titles without synthesis is not sufficient.

#### Proposed system or approach

Provide a diagram and describe components, interfaces, inputs, outputs, and the team's contribution. Identify reused systems and dependencies. For replication work, identify the exact claims, figures, or tables you will reproduce and define the extension separately.

#### Evaluation plan

Include:

- research question-to-experiment mapping;
- datasets and workloads;
- baselines and ablations;
- controlled and varied factors;
- system and quality metrics, including units;
- hardware and software environment;
- number of trials or seeds and how variability will be reported;
- planned plots and tables;
- success criteria and interpretation of negative results.

**Example success criterion:** "The optimization is useful only if it lowers p95 latency by at least 15% at equal output quality without increasing peak memory by more than 10%."

#### Expected deliverables

Name concrete artifacts: source code, configuration files, automated experiment scripts, raw and processed results, figures, documentation, a demo, and the final report. Avoid vague promises such as "a working system."

#### Timeline and milestones

Assign owners and define observable completion criteria.

| Period | Milestone | Evidence of completion | Owner(s) |
|---|---|---|---|
| Week 1 | Reproduce baseline | Script runs end-to-end and produces one validated result | A, B |
| Week 2 | Implement treatment | Feature passes correctness checks | B, C |
| Week 3 | Pilot experiments | One plot exposes feasibility or design problems | A, C |
| Week 4 | Full experiment sweep | Versioned raw results and experiment log | Team |
| Week 5 | Analysis and report | Final figures, interpretation, limitations | Team |

#### Risks and mitigations

Include technical and execution risks. Each risk needs an early warning sign, mitigation, and fallback.

| Risk | Early warning sign | Mitigation | Fallback |
|---|---|---|---|
| Required model does not fit available GPU memory | Out-of-memory error during baseline setup | Test memory in the first week; use quantization | Use a smaller model and preserve the same research question |
| Dataset access is delayed | No approved access by milestone date | Begin approval immediately; prepare public proxy data | Evaluate on the proxy dataset and document external validity limits |
| Full benchmark is too expensive | Pilot cost exceeds budget | Reduce the factorial design; use power-aware sampling | Run fewer conditions with more repetitions and narrower claims |

#### Reproducibility plan

Record dependency versions, hardware, random seeds, configuration files, dataset versions, commands, raw results, and analysis scripts. Someone outside the team should be able to reproduce at least one principal result from the README. If the team used AI coding or writing assistants (for example, an LLM-based code assistant) in a way that materially shaped the code or results, note where and how, consistent with the course's academic-integrity policy on acknowledging sources and collaborators — a line or two is sufficient.

## 5. Final Presentation Guidelines

Unless superseded by an announcement, plan for a **10-12 minute presentation** in Week 15. Every team member should participate and be prepared to answer questions about the entire project.

A useful structure is:

1. **Hook and problem (1 minute):** What is the real problem, and why should the audience care?
2. **Research questions and contribution (1 minute):** What precisely did you investigate or build?
3. **System design (2 minutes):** How does the system work? What did the team contribute?
4. **Methodology (2 minutes):** What were the baselines, workloads, variables, metrics, and controls?
5. **Results (3-4 minutes):** Present the smallest set of figures needed to answer the research questions.
6. **Limitations, lessons, and conclusion (1-2 minutes):** What can and cannot be concluded? What would you do next?

For every result slide:

- use a claim as the slide title, not a generic label such as "Results";
- show the evidence supporting that claim;
- explain the comparison and the practical magnitude, not only statistical significance;
- disclose uncertainty, failed runs, or confounding factors;
- state the takeaway in one sentence.

**Weak title:** "Latency Results"

**Stronger title:** "Prefix caching cuts p95 latency only when prefix reuse exceeds 50%"

Prepare backup slides for detailed configurations, extra results, threat models, statistical tests, and architecture details. If your talk includes a live demo, prepare a short backup recording of it in case of a technical failure during the session. Include a repository link or QR code on the final slide.

## 6. How Projects Will Be Judged

Use these dimensions as a self-check throughout the semester:

- **Experimentation and rigor:** reproducible experiments, appropriate baselines, controlled comparisons, clear metrics, and justified conclusions;
- **Novelty and challenge:** a meaningful, ambitious, and ML systems-relevant question;
- **System design:** a coherent system or pipeline with a clearly identified team contribution;
- **Communication:** clear writing, legible figures, an engaging presentation, and claims matched to evidence;
- **Milestone progress:** steady progress, early risk reduction, and timely deliverables.

A polished demo cannot compensate for an unclear question or weak evaluation. Likewise, a negative result can be valuable when the experiment is rigorous and the limitations are analyzed honestly.

## 7. Suggested Themes and Example Projects

### LLM serving and efficiency

- Compare batching, prefix caching, speculative decoding, or quantization under realistic loads.
- Study latency-throughput-quality-cost trade-offs rather than reporting speed alone.
- Example: *At what concurrency does continuous batching outperform static batching while keeping p95 latency below the service objective?*

### Agentic AI systems

- Compare single-agent, prompt-chain, and orchestrator-worker designs.
- Evaluate task success, latency, token cost, failure recovery, and run-to-run variance.
- Example: *Does parallelizing repository analysis improve issue-resolution success enough to offset additional tool calls and cost?*

### Data quality, observability, and monitoring

- Build or compare drift detection, lineage, data validation, or model-monitoring methods.
- Example: *Which detector identifies gradual covariate shift earliest at a fixed false-alarm rate?*

### Energy and sustainability

- Profile energy across models, accelerators, inference settings, or scheduling policies.
- Example: *Which quantization level minimizes joules per correct answer under a fixed latency target?*

### Trustworthy ML systems

- Evaluate adversarial robustness, prompt injection, privacy, reliability, or recovery mechanisms.
- Example: *How do three prompt-injection defenses trade off attack success rate, benign-task accuracy, latency, and cost?*

### Replication and extension

- Select a recent ML systems paper with available code and a feasible experimental setup.
- Reproduce a named result before adding one controlled extension.
- Example: *Reproduce a published throughput-latency curve on available hardware, then test whether the reported trend holds for longer prompts and a quantized model.*

## 8. Useful Resources

### Textbooks and foundational references

- [Machine Learning Systems (Harvard/MIT Press, open access)](https://mlsysbook.ai/) - a two-volume, freely available textbook covering ML systems foundations through fleet-scale deployment, with accompanying labs and slides; a good first stop for background reading and vocabulary before diving into papers.

### Finding papers and artifacts

- [MLSys conference proceedings](https://proceedings.mlsys.org/) - peer-reviewed ML systems papers.
- [Papers with Code](https://paperswithcode.com/) - papers linked to public implementations and benchmarks; verify claims against the original paper and repository.
- [Artifact Evaluation](https://sysartifacts.github.io/) - practical guidance for packaging reproducible systems artifacts.

### Experiment design and reproducibility

- [ACM artifact review and badging](https://www.acm.org/publications/policies/artifact-review-and-badging-current) - criteria for available, functional, and reproducible artifacts.
- [MLflow documentation](https://mlflow.org/docs/latest/) - experiment tracking, parameters, metrics, and artifacts.
- [Weights & Biases experiment tracking](https://docs.wandb.ai/) - optional experiment logging and visualization.
- [Docker documentation](https://docs.docker.com/) and [Conda environment management](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html) - environment capture and repeatability.

### Systems measurement

- [vLLM benchmarking documentation](https://docs.vllm.ai/en/latest/benchmarking/cli/) - online serving, latency, throughput, and load-pattern experiments.
- [MLPerf Inference documentation](https://docs.mlcommons.org/inference/) - standardized inference scenarios, metrics, and methodology.
- [NVIDIA Nsight Systems](https://docs.nvidia.com/nsight-systems/) - CPU/GPU timeline profiling.
- [PyTorch Profiler](https://docs.pytorch.org/tutorials/recipes/recipes/profiler_recipe.html) - operator-level CPU and GPU profiling.
- [Prometheus documentation](https://prometheus.io/docs/introduction/overview/) - service metrics and monitoring.

### Agents, evaluation, and reliability

- [LangGraph documentation](https://docs.langchain.com/oss/python/langgraph/overview) - graph-based agent orchestration.
- [Microsoft Agent Framework documentation](https://learn.microsoft.com/en-us/agent-framework/) - Microsoft's unified agent SDK, which now consolidates the former AutoGen and Semantic Kernel frameworks; use this rather than legacy AutoGen docs for new work.
- [SWE-bench](https://www.swebench.com/) - benchmark for resolving real-world software issues; review its setup and cost before choosing it.
- [τ²-bench (tau2-bench)](https://github.com/sierra-research/tau2-bench) - benchmark for agent performance in realistic, tool-using, multi-turn conversations (successor to the original tau-bench); useful for evaluating agentic-system reliability, not just task success.
- [GAIA benchmark](https://huggingface.co/gaia-benchmark) - general-assistant benchmark spanning reasoning, tool use, and multi-modality; useful when comparing agent designs on tasks broader than coding.
- [lm-evaluation-harness](https://github.com/EleutherAI/lm-evaluation-harness) - reproducible language-model task evaluation.

### Data monitoring and sustainability

- [Evidently documentation](https://docs.evidentlyai.com/) - data and model evaluation and monitoring.
- [Great Expectations documentation](https://docs.greatexpectations.io/) - data validation and quality checks.
- [CodeCarbon documentation](https://docs.codecarbon.io/latest/) - local compute energy and emissions tracking.

Use tools because they support a research question, not because they are popular. Read limitations, validate metric definitions, pin versions, and record configuration details.

## 9. Before You Submit

### Presentation readiness

- [ ] The title is specific and informative.
- [ ] The problem, proposed solution, and evaluation each fit on one content slide.
- [ ] The research question and project type are explicit.
- [ ] The evaluation names baselines, workloads, metrics, and expected evidence.
- [ ] The deck uses clean, legible, high-quality visuals.
- [ ] The talk has been rehearsed within three minutes.
- [ ] A scribe is assigned to capture feedback.
- [ ] Any compute, data, or access needs have been identified and, if needed, requested.

### Proposal readiness

- [ ] All required headings are present.
- [ ] Feedback and the team's response appear near the beginning.
- [ ] At least two or three key references are synthesized, not merely listed.
- [ ] The team's new contribution is distinguishable from reused work.
- [ ] Each research question maps to an experiment and success criterion.
- [ ] Risks have mitigations and fallbacks.
- [ ] Milestones have owners and observable completion criteria.
- [ ] The reproducibility plan records code, data, environments, results, and any AI-assistant use.
- [ ] Relevant broader impacts (privacy, fairness, security, environmental cost) are named where applicable.
- [ ] The repository is accessible and listed in the course spreadsheet.

## Extensions

If you need an extension, ask through Piazza. State what the team has completed, the specific remaining work, why more time is needed, and a concrete proposed submission date. Requests should reflect a genuine obstacle and a credible completion plan.
