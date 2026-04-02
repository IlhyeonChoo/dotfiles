# Research Brief Template

Use this document as the canonical handoff brief for Codex agents working on a research program.

The goal is to give agents enough context to investigate, implement, evaluate, and synthesize without re-deriving the project state from scratch.

## 1. Agent Handoff Guide

Use this section to route work efficiently.

### Quick Routing by Situation

- Use `context-manager` when the brief is long and another agent first needs a compact project snapshot.
- Use `search-specialist` when you need papers, benchmarks, related methods, code references, or prior art.
- Use `research-analyst` when the main need is to frame the research question, compare options, and produce a decision-oriented brief.
- Use `data-scientist` when you need help interpreting metrics, designing ablations, checking confounders, or judging whether a result is meaningful.
- Use `workflow-orchestrator` when the work must be split into stages such as literature review, implementation, experiments, and synthesis.
- Use `knowledge-synthesizer` when several agents or experiment notes already exist and you need one non-redundant conclusion.
- Use `python-pro` or `cpp-pro` when the next step is implementation in the actual training, viewer, optimization, or evaluation code.
- Use `performance-engineer` when the main question is VRAM, memory transfer, runtime, profiling, scalability, or bottleneck localization.
- Use `debugger` when a current experiment fails, diverges, crashes, regresses, or shows unexpected artifacts.
- Use `documentation-engineer` when stable findings need to be turned into clean notes, reports, method descriptions, or durable documentation.

### context-manager

- Ask for a compact restatement of this brief before a long task.
- Use when a new agent needs a clean, low-token snapshot.

### search-specialist

- Use for literature scans, codebase searches, benchmark hunting, and reference implementation discovery.
- Provide exact search targets, not broad prompts.

### research-analyst

- Use for decision-oriented investigations.
- Always provide the decision question, current constraints, and the strongest known evidence.

### data-scientist

- Use for metric interpretation, ablation design, and confounder analysis.
- Always provide metric definitions, sample counts, and experiment splits.

### workflow-orchestrator

- Use when the work spans discovery, implementation, validation, and synthesis.
- Provide dependencies, blockers, and what can be parallelized safely.

### knowledge-synthesizer

- Use after multiple agents return results.
- Provide all source outputs and ask for conflict-aware synthesis.

### python-pro / cpp-pro

- Use for implementing validated experiment ideas in the actual codebase.
- Provide exact files, interfaces, and constraints to preserve.

### performance-engineer

- Use for VRAM, throughput, and memory-transfer investigations.
- Provide profiler outputs, target bottlenecks, and the exact workload.

### debugger

- Use when artifacts, regressions, instability, or unexpected quality drops appear.
- Provide reproduction steps and the smallest failing case.

### documentation-engineer

- Use to convert stable findings into durable docs, experiment notes, or method summaries.

## 2. Brief Metadata

- Brief title:
- Brief ID:
- Last updated:
- Owner:
- Repository / workspace:
- Research stage: idea | setup | implementation | experiment | analysis | write-up
- Current priority: high | medium | low
- Primary decision needed now:
- Expected agent output: investigation | implementation plan | experiment design | result analysis | synthesis | debugging

## 3. Program Snapshot

- Program goal:
- One-sentence thesis:
- Why this matters:
- Near-term milestone:
- Longer-term roadmap:
- Non-goals:
- Hard constraints:
- Available compute budget:
- Time budget:
- Required baselines to beat:

## 4. Current Research Tracks

List each active or planned track in one line first, then fill detailed sections below.

- Track A:
- Track B:
- Track C:

Suggested starting point for the current program:

- Track A: Reduce VRAM by controlling the data transferred from 3DGS training/runtime to the viewer side.
- Track B: Improve optimization convergence speed and final quality by inserting object-level Gaussian-set priors from a reusable library at initialization.
- Track C: Resolve boundary-quality degradation introduced by block-wise training, similar to CityGaussian-style partitioning.

## 5. Track Detail Template

Copy this section once per track.

### Track Name

- Status: active | planned | blocked | paused | complete
- Priority:
- One-sentence thesis:
- Problem statement:
- Decision objective:
- Why current methods are insufficient:
- Main hypothesis:
- Competing hypotheses:
- Success criteria:
- Failure criteria:
- Expected impact:
- Dependencies on other tracks:

### Technical Framing

- Target system or pipeline:
- Core mechanism under study:
- What is being changed:
- What must remain unchanged for a fair comparison:
- Suspected bottlenecks:
- Suspected failure modes:
- Important implementation constraints:

### Evidence Ledger

Split evidence by confidence level. Keep observed facts separate from interpretation.

#### Confirmed Facts

- Fact:
- Source or artifact:
- Confidence:

#### Working Inferences

- Inference:
- Why it is plausible:
- What evidence would confirm or refute it:

#### Open Questions

- Question:
- Why it matters:
- Best next way to answer it:

### Experiment Plan

- Experiment ID:
- Hypothesis tested:
- Exact change from baseline:
- Baseline definition:
- Dataset / scenes:
- Train / validation / test split:
- Metrics:
- Measurement procedure:
- Compute resources:
- Runtime / VRAM instrumentation plan:
- Expected win condition:
- Expected failure signature:
- Artifacts to save:

### Latest Results

- Latest experiment ID:
- Result summary:
- Best observed gains:
- Regressions or trade-offs:
- Confidence in the result:
- Main caveats:
- Recommended next move:

## 6. Shared Evaluation Protocol

- Primary quality metrics:
- Secondary quality metrics:
- VRAM metrics:
- Throughput metrics:
- Latency metrics:
- Scene categories:
- Ablation requirements:
- Statistical or repeated-run requirements:
- Visualization requirements:
- Acceptance threshold for claiming improvement:

## 7. Baselines and Comparators

- Main baseline:
- Strong baseline:
- Practical baseline:
- External papers / systems to compare against:
- What counts as a fair comparison:
- Known mismatch risks in comparison:

## 8. Data, Assets, and Artifacts

- Datasets:
- Scene lists:
- Pretrained checkpoints:
- Prior library assets:
- Viewer-side artifacts:
- Logging location:
- Experiment tracking location:
- Visualization / render output location:
- Important scripts or entry points:

## 9. Environment and Reproducibility

- Main language / runtime:
- Key dependencies:
- CUDA / GPU assumptions:
- Default training command:
- Default evaluation command:
- Default profiling command:
- Seed policy:
- Determinism caveats:
- Known environment issues:

## 10. Risks and Confounders

- Measurement confounders:
- Data leakage risks:
- Evaluation bias risks:
- Overfitting risks:
- Implementation risks:
- Scalability risks:
- Risks that could invalidate current conclusions:

## 11. Decision Log

Record decisions that future agents should not silently undo.

- Decision:
- Date:
- Chosen option:
- Alternatives considered:
- Why this option was chosen:
- Trigger for revisiting:

## 12. Instructions for Future Agents

- Treat `Confirmed Facts` and `Decision Log` as the current source of truth.
- Treat `Working Inferences` as unverified until supported by new evidence.
- Do not collapse quality, speed, and VRAM into a single claim unless the trade-off is explicitly measured.
- Preserve metric definitions across experiments unless the brief is updated to justify a change.
- Update the brief after any meaningful experiment, implementation change, or decision.
- If results conflict, record the conflict explicitly instead of averaging it away.

## 13. Current Priority Queue

- Highest-priority question:
- Second-priority question:
- Blocker preventing progress:
- Fastest useful next experiment:
- Most valuable missing evidence:

## 14. References

- Paper:
- Codebase:
- Issue / note / design doc:
- Relevant benchmark or dataset:

## 15. Minimal Fill Requirement

Before handing this brief to agents, fill at least the following:

- `Program Snapshot`
- At least one `Track Detail Template`
- `Shared Evaluation Protocol`
- `Baselines and Comparators`
- `Current Priority Queue`
