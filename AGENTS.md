# AI QE Engineering — Agent Instructions

## Purpose

This repository is Divyendu Shukla's hands-on portfolio for transitioning from senior/staff Software Quality Engineering into **AI Quality Engineering / AI Validation Engineering**.

The goal is not to collect AI tools or certifications. The goal is to build practical, defensible expertise in **testing AI/ML systems themselves**: correctness, reliability, safety, data quality, model behavior, evaluation, performance, observability, and production quality gates.

## Candidate Background

Divyendu is a Staff Software Engineer in Test with ~10 years of QE experience and strong existing expertise in:

- JavaScript / TypeScript
- Playwright
- API testing
- CI/CD
- Docker / Kubernetes
- k6 performance testing
- Datadog / Splunk observability
- OWASP security testing
- WCAG accessibility testing
- AWS
- Claude / AWS Bedrock
- MCP and agentic test automation

Do **not** treat these as beginner topics unless a project explicitly requires deeper understanding.

## Existing AI/QE Work

### QA-Agent

Public repository: https://github.com/divyendu13/qa-agent

QA-Agent is an autonomous AI quality-engineering agent using Claude via AWS Bedrock in a ReAct loop. It can browse an application, generate Playwright tests, run them, triage failures, perform OWASP ZAP security scanning, run axe-core accessibility checks, and execute k6 load tests. It also produces unified reports and runs through GitHub Actions.

When discussing QA-Agent, describe only capabilities that are actually implemented in that repository. Do not imply that it already performs LLM evaluation, RAG evaluation, model validation, hallucination detection, or other capabilities unless those capabilities are subsequently implemented.

## Published Articles

1. `articles/testcafe-playwright-ai-migration.md`
   - AI-assisted migration of 350+ E2E tests from TestCafe to Playwright.
   - Focuses on agent workflows, architectural constraints, a written "constitution", human review gates, lint/build enforcement, and AI failure modes.

2. `articles/playwright-ci-shard-balancing.md`
   - CI performance and Playwright sharding analysis.
   - Focuses on developer wait vs billed machine time vs idle time, timing-based splitting, infrastructure overhead, and measurement discipline.

These articles describe real engineering work. Preserve their factual claims and framing unless the user explicitly asks for editorial changes.

## Main Project: AI Quality Gate

The main new project is a hands-on **AI Quality Gate** platform.

Core question:

> Is this AI system good enough to ship?

Planned evolution:

```text
Data
  ↓
Data validation
  ↓
Feature validation
  ↓
ML model validation
  ↓
LLM evaluation
  ↓
RAG evaluation
  ↓
Safety / adversarial testing
  ↓
Performance / observability
  ↓
CI/CD AI quality gates
```

### Learning strategy

Learn by building rather than completing large courses first.

For each meaningful capability:

1. Explain the concept briefly and why it matters.
2. Implement it in the project.
3. Write automated tests.
4. Deliberately create a failure or bad input.
5. Observe the failure.
6. Fix or harden the implementation.
7. Document the lesson.

Do not build the entire platform in one pass. Keep the system incremental and demonstrable.

## Target Skills

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
- FastAPI
- DeepEval / RAGAS / promptfoo as appropriate
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

## Resume Alignment

The long-term target roles include:

- AI Quality Engineer
- AI/ML Validation Engineer
- AI SDET / GenAI QE
- AI Evaluation / Reliability Engineer

The portfolio should demonstrate the progression:

```text
AI-assisted QE
      ↓
AI-powered QE
      ↓
AI / ML validation
      ↓
LLM + RAG evaluation
      ↓
AI reliability / safety
      ↓
Production AI quality engineering
```

Do not prematurely list future skills as established expertise on the resume. Promote skills from "Learning / Building" to demonstrated capability only after they are implemented and defensible.

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

First milestone:

```text
FastAPI
  ↓
Simple scikit-learn model
  ↓
/predict API
  ↓
pytest API tests
```

The first milestone should teach the basics of Python, FastAPI, scikit-learn, model input/output, and API testing. Do not jump directly to LLMs before this foundation is working.

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
