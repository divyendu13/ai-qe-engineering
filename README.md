# AI Quality Engineering

A hands-on portfolio exploring how Quality Engineering evolves for AI/ML and Generative AI systems.

I am a Staff Software Engineer in Test with ~10 years of experience building scalable automation, CI/CD, observability, performance, security, and distributed-system testing. This repository documents my transition from testing software with AI to engineering quality, evaluation, and reliability for AI-powered systems.

## Why this repository exists

AI systems introduce a different class of quality problems: model behavior is probabilistic, outputs can be difficult to assert deterministically, data can drift, retrieval can fail independently of generation, and an application can be technically healthy while producing poor or unsafe results.

The goal of this portfolio is to explore those problems through working systems, automated tests, evaluation frameworks, and production-style quality gates.

## Focus Areas

- AI / ML quality engineering
- Generative AI and LLM testing
- Prompt testing and response validation
- RAG testing and retrieval evaluation
- AI agent reliability
- Data and feature validation
- Model evaluation and regression testing
- Hallucination and grounding validation
- Responsible AI, safety, and adversarial testing
- AI API testing
- Performance and latency testing for AI services
- Observability and production validation
- AI quality gates in CI/CD
- AI system reliability and end-to-end validation
- RAG system construction and evaluation
- Agentic workflow construction and evaluation
- Tool-use and action validation
- Context engineering and structured-data integration
- Evaluation-driven AI development
- Fuzz testing and OpenAPI robustness validation
- Bias, toxicity, and unsafe-output evaluation
- Distributed AI service reliability: queues, retries, backpressure, idempotency, and failure recovery
- golden datasets / benchmark evaluation
- agent evaluation and trajectory testing
- human-in-the-loop safety controls
- model/prompt baseline-vs-candidate comparison
- production AI observability: tracing, token/cost, fallbacks, escalations

## Articles

### [Migrating 350+ E2E Tests to Playwright in 3 Months — With AI Writing the First Draft](./articles/testcafe-playwright-ai-migration.md)

A practical case study on using AI agents for large-scale test automation migration. It explores the difference between code generation and code translation, why a written engineering "constitution" mattered more than the agent, how human review gates controlled risk, and what the agent still got wrong.

### [Your Playwright Shards Aren't Balanced, and CI Has Been Telling You All Along](./articles/playwright-ci-shard-balancing.md)

A deep dive into CI measurement, timing-based test splitting, workload imbalance, infrastructure overhead, and why performance claims need to distinguish developer wait, billed machine time, and idle parallelism.

## Projects

### AI Quality Gate — In Progress

A hands-on AI/ML quality engineering platform focused on answering one question:

> **Is this AI system good enough to ship?**

The project is at the evaluation-design stage; application implementation has not started. The first milestone is a small evaluation runner with a versioned dataset, deterministic checks, structured results, explicit thresholds, deliberate failures, and one semantic/model-based evaluator.

The implementation is intentionally incremental. Each capability is learned by building it, testing it, deliberately breaking it, and then hardening the quality checks.

The long-term goal is a reusable evaluation platform for LLM, RAG, and agentic systems, with versioned golden datasets, configurable evaluators, regression comparison, safety checks, observability, and CI-integrated release gates.

## Existing AI / QE Work

### QA-Agent

I built an autonomous AI quality engineering agent that uses Claude via AWS Bedrock in a ReAct loop to browse applications, generate Playwright tests, run them, triage failures, perform OWASP security scanning, check WCAG accessibility, and run k6 load tests from a single workflow.

**Repository:** [github.com/divyendu13/qa-agent](https://github.com/divyendu13/qa-agent)

The project includes a Playwright-based browser skill, AI-driven test generation and failure triage, OWASP ZAP integration, axe-core accessibility scanning, k6 load testing, a unified HTML report, and GitHub Actions CI. The agent orchestrates these capabilities through a ReAct loop rather than a fixed test script.

## Current Engineering Foundation

**Quality Engineering**

Playwright · TypeScript · JavaScript · API Testing · CI/CD · Docker · Kubernetes · k6 · Datadog · Splunk · OWASP · Accessibility

**AI / GenAI**

Claude · AWS Bedrock · ReAct · MCP · Agentic Test Automation

**Learning / Building**

Python · pytest · pandas · NumPy · scikit-learn · FastAPI · LLM Evaluation · RAG · AI Safety

## Roadmap

The next month is organized around small working evaluation capabilities:

| Week | Planned focus |
|---|---|
| 1 | Evaluation fundamentals and the first AI Quality Gate runner: versioned/golden datasets, deterministic checks, structured results, explicit thresholds, deliberate failures, and a first semantic evaluator. |
| 2 | Build a minimal RAG workflow, then evaluate correctness, relevance, grounding, hallucination, retrieval quality, citations, missing/stale context, prompt variants, and retrieval-versus-generation failures. |
| 3 | Build a bounded agentic workflow, then evaluate tool selection/arguments, action order, retries, recovery, loops, authorization, human-in-the-loop handoffs, memory/state, prompt injection, tool abuse, and distributed workflow failures. |
| 4 | Production AI quality engineering: observability, tracing, regression/drift detection, model/prompt comparison, safety/red-teaming, bias/toxicity, API fuzzing, performance/load, and CI gates that produce PASS/BLOCK from explicit thresholds. |

Python and pytest support the evaluation work. FastAPI is optional. Evaluation frameworks such as DeepEval, RAGAS, and promptfoo will be considered only after implementing and understanding the underlying concepts. OpenAPI-driven fuzzing tools such as CATS or Schemathesis may be introduced where they help validate inference and backend APIs under malformed, unexpected, or adversarial inputs. These are planned capabilities, not completed project claims.

The working approach is to explain a needed concept, reason about the quality strategy, implement and test it, deliberately demonstrate a failure, improve validation, and document the evidence. Persistent working instructions and the current checkpoint live in [AGENTS.md](./AGENTS.md).

The objective is not to collect AI tools. It is to develop the ability to **design, test, evaluate, and operationalize AI systems end-to-end**.

## Author

**Divyendu Shukla** — Staff Software Engineer in Test

[Website](https://divyendushukla.in) · [LinkedIn](https://linkedin.com/in/divyendushukla) · [GitHub](https://github.com/divyendu13)
