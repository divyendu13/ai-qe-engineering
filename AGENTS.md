# AI QE Engineering — Agent Instructions

## Purpose

This repository is Divyendu Shukla's hands-on portfolio for transitioning from Staff Software Quality Engineering into:

- AI Quality Engineering
- AI/ML Validation Engineering
- AI SDET / GenAI QE
- AI Evaluation Engineering
- AI Reliability Engineering

The goal is not to collect AI tools, certifications, framework names, or disconnected demos.

The goal is to build practical, defensible expertise in **testing AI/ML systems themselves**:

- AI/ML correctness
- LLM evaluation
- RAG quality
- Agent reliability
- AI-native automation
- Safety and adversarial behavior
- Data quality
- Model behavior
- Prompt quality
- Performance
- Observability
- Drift and regression
- Production quality gates

Every project should answer a practical engineering question:

> **Is this AI system good enough to ship?**

---

# Candidate Background

Divyendu is a Staff Software Engineer in Test with ~10 years of QE experience.

Strong existing expertise includes:

- JavaScript / TypeScript
- Playwright
- Selenium / WebdriverIO
- API testing
- CI/CD
- Docker / Kubernetes
- k6 / JMeter performance testing
- Datadog / Splunk observability
- OWASP security testing
- WCAG / accessibility testing
- AWS
- Distributed systems and enterprise SaaS
- Claude / AWS Bedrock
- MCP
- Agentic test automation

Do **not** treat these as beginner topics unless a project explicitly requires deeper understanding.

The learning effort should focus primarily on the **AI-system-under-test layer**, not on relearning general QE.

---

# Existing AI / QE Work

## QA-Agent

Public repository:

https://github.com/divyendu13/qa-agent

QA-Agent is an autonomous AI quality-engineering agent using Claude via AWS Bedrock in a ReAct-style loop.

Implemented capabilities include:

- Browser exploration
- Playwright test generation
- Test execution
- AI-driven failure triage
- OWASP ZAP security scanning
- axe-core accessibility checks
- k6 load testing
- Unified reporting
- GitHub Actions execution

When discussing QA-Agent:

- Describe only capabilities actually implemented in the repository.
- Do not imply that it already performs LLM evaluation, RAG evaluation, model validation, hallucination detection, trajectory scoring, or other capabilities unless those capabilities are subsequently implemented.
- Prefer linking to concrete code, tests, and documentation when making claims.

QA-Agent is evidence of **AI-powered QE automation**.

It is not by itself evidence of systematic AI evaluation.

---

# Existing AI-Assisted QE Work

## TestCafe → Playwright Migration

The portfolio includes an AI-assisted migration of a large enterprise E2E suite.

Important engineering characteristics:

- 350+ E2E tests
- 38 files
- ~55K lines of first-pass Playwright code
- Agent-assisted code generation
- Written architectural "constitution"
- Batch-loop execution
- Machine-enforced conventions
- Lint/build validation
- Trace-based assertion review
- Iterative correction
- Human review gates

The important engineering lesson is:

> Give the agent the mechanical work, and spend engineering time on the architecture it has to conform to.

Do not present the migration as "AI wrote the tests."

The defensible story is that AI accelerated mechanical migration while the engineering work focused on constraints, validation, feedback loops, architecture, and quality control.

---

# Published Technical Writing

## TestCafe → Playwright AI Migration

Path:

`articles/testcafe-playwright-ai-migration.md`

Focus:

- AI-assisted test modernization
- Agent workflows
- Architectural constraints
- Written constitution
- Human review
- Validation
- AI failure modes

## Playwright CI Shard Balancing

Path:

`articles/playwright-ci-shard-balancing.md`

Focus:

- CI performance investigation
- Developer wait time
- Billed machine time
- Idle parallelism
- Timing-based sharding
- Infrastructure overhead
- Measurement discipline

These articles describe real engineering work.

Preserve their factual claims and framing unless explicitly asked to edit them.

Never invent metrics or simplify the findings into claims that the articles do not support.

---

# Portfolio

Public portfolio repository:

https://github.com/divyendu13/ai-qe-engineering

Portfolio site:

https://divyendushukla.in

QA-Agent:

https://github.com/divyendu13/qa-agent

The portfolio should tell a coherent progression:

```text
AI-assisted QE
      ↓
AI-powered QE
      ↓
AI / ML validation
      ↓
LLM evaluation
      ↓
RAG evaluation
      ↓
Agent reliability
      ↓
AI-native automation
      ↓
AI safety / adversarial testing
      ↓
Production AI quality engineering
```

Do not prematurely list future skills as established expertise on the resume. Promote skills from "Learning / Building" to demonstrated capability only after they are implemented and defensible.

---

## Main Project: AI Quality Gate

The main new project is a hands-on **AI Quality Gate** platform.

Core question:

> Is this AI system good enough to ship?

### Consolidated one-month roadmap

This plan supersedes the earlier FastAPI/classical-ML-first sequence.

| Week | Focus and deliverable |
|---|---|
| 1 | AI evaluation fundamentals. Complete only a very small practical ML validation exercise covering train/test split, precision, recall, F1, thresholds, and model regression. Begin the real AI Quality Gate with a versioned evaluation dataset, deterministic evaluators, structured evaluation results, explicit pass/fail thresholds, deliberate failure cases, and one semantic/model-based evaluator. Do not spend the full week on classical ML. |
| 2 | LLM and RAG evaluation: correctness, relevance, groundedness, hallucination, retrieval quality, citation accuracy, missing/stale context, and distinguishing retrieval failures from generation failures. |
| 3 | Agent evaluation and AI safety/control-plane testing: tool selection, tool arguments, action order, retries, recovery, loop detection, authorization, escalation, unsafe/excessive agency, prompt injection, tool abuse, and final outcome quality. Evaluate observable behavior, not hidden chain-of-thought. |
| 4 | AI observability, regression detection, reporting, and CI quality gates. Finish with a reproducible PASS/BLOCK decision based on explicit evaluation thresholds. |

### Learning strategy

Learn by building rather than completing large courses first.

For each meaningful capability:

1. Explain the concept briefly when the current build needs it.
2. Ask Divyendu to reason about the design or quality strategy where appropriate.
3. Challenge weak assumptions and unsupported claims.
4. Help implement the smallest working capability and automate its tests.
5. Deliberately break the system or provide bad input.
6. Observe and analyze the failure, then improve validation.
7. Document the lesson and identify portfolio/interview evidence.

Do not build the entire platform in one pass. Keep the system incremental and demonstrable.

Keep the journey self-contained in this workspace. Guide one step at a time without requiring movement between tools or chats. Before writing new code, briefly restate the current milestone and give the next single task. Treat Divyendu as a Staff-level QE engineer transitioning into AI QE; the objective is production AI evaluation, testing, security, observability, and quality gates, not ML research.

## Target Skills

These are a longer-term skill inventory, not prerequisites or a mandatory one-month checklist. The consolidated roadmap determines the order and scope. Use Python/pytest for practical evaluation; do not turn the journey into generic Python training. Introduce each technology only when its role in the current build is justified.

### ML / data

- Python
- NumPy
- pandas
- scikit-learn
- classification / regression / clustering
- train/validation/test concepts
- feature validation
- model evaluation metrics
- data quality
- data drift
- model regression testing
- explainability (for example SHAP)
- fairness / bias concepts

### GenAI

- LLM fundamentals
- prompting
- structured output / tool calling
- hallucination testing
- response correctness / relevance
- safety testing
- RAG
- embeddings
- retrieval evaluation
- agent reliability

### Evaluation / production

- pytest
- FastAPI only if an API genuinely helps the architecture; it is optional
- DeepEval / RAGAS / promptfoo only after the underlying evaluation concepts have been understood and implemented directly
- observability and tracing
- latency / throughput / cost
- CI/CD quality gates
- AWS / production deployment concepts

## Engineering Principles

- **Build incrementally.** Prefer small working milestones over large speculative architecture.
- **Tests are first-class.** New functionality should normally come with automated tests.
- **Test the AI, not only the wrapper.** Validate model/data/output behavior where possible.
- **Prefer deterministic checks when available.** Use exact assertions for deterministic values and appropriate semantic evaluation for probabilistic outputs.
- **Deliberately test failure modes.** A project without failure demonstrations is not sufficient evidence of QE skill.
- **Measure before claiming improvement.** Never invent performance, accuracy, quality, or productivity numbers.
- **Do not fabricate experience.** Distinguish clearly between existing professional experience, personal project work, and current learning.
- **Keep claims interview-defensible.** Anything added to a resume or README should be backed by code, tests, documentation, or clearly stated project status.
- **Avoid unnecessary dependencies.** Add a library only when the project benefits from it and explain why when relevant.
- **Keep secrets out of Git.** Never commit API keys, cloud credentials, tokens, or private endpoints.
- **Keep public repos sanitized.** Do not introduce proprietary company/customer information into this repository.
- **Prefer clear Python and TypeScript/JavaScript over clever code.**
- **Document architectural decisions.** Especially decisions about evaluation methodology and quality thresholds.

## Current State

- Two technical articles are published in this repository.
- README has been positioned as an AI-QE portfolio landing page.
- QA-Agent exists as a separate public repository and is linked from the portfolio README.
- Next major task: start the **AI Quality Gate** project incrementally.

## Immediate Next Milestone

Create the initial project under:

```text
projects/ai-quality-gate/
```

Current milestone: define and build the smallest evaluation runner for a bounded AI response task.

Start by designing the first evaluation case: input, authoritative context, expected behavior, acceptable variations, and an explicit failure rule. Then incrementally implement a versioned dataset, deterministic checks, structured results, and thresholds using Python/pytest. Demonstrate a bad response being caught. Add one semantic/model-based evaluator during Week 1 and test its limitations against reviewed examples.

The small ML validation exercise supports evaluation fundamentals; it is not a prerequisite for building an API or a separate full classical ML project. FastAPI is optional. No AI Quality Gate application code exists at this checkpoint; the first evaluation case is the next task to discuss.

## Working Style for Codex

When starting a new task in this repository:

1. Read this file and the root README.
2. Inspect the existing project structure before changing anything.
3. Summarize the planned change briefly.
4. Make the smallest coherent change.
5. Run relevant tests/checks.
6. Report what changed, what was tested, and any limitations.
7. Do not rewrite unrelated files.
8. Do not silently invent requirements.

When the user asks to learn a concept, teach just enough theory to support the current implementation and connect it to AI-QE testing.

## Definition of Done

A feature is not considered complete merely because the code runs. Prefer the following:

```text
Implementation
    +
Automated tests
    +
Failure/edge-case test
    +
Clear README/documentation
    +
Reproducible execution
```

The objective is a portfolio that demonstrates engineering judgment, not just code volume.
