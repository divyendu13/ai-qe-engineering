# AI Quality Engineering

A hands-on portfolio exploring how Quality Engineering evolves for AI/ML and Generative AI systems.

I am a Staff Software Engineer in Test with ~10 years of experience building scalable automation, CI/CD, observability, performance, security, and distributed-system testing. This repository documents my transition from **testing software with AI to testing the AI itself**.

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

## Articles

### [Migrating 350+ E2E Tests to Playwright in 3 Months — With AI Writing the First Draft](./articles/testcafe-playwright-ai-migration.md)

A practical case study on using AI agents for large-scale test automation migration. It explores the difference between code generation and code translation, why a written engineering "constitution" mattered more than the agent, how human review gates controlled risk, and what the agent still got wrong.

### [Your Playwright Shards Aren't Balanced, and CI Has Been Telling You All Along](./articles/playwright-ci-shard-balancing.md)

A deep dive into CI measurement, timing-based test splitting, workload imbalance, infrastructure overhead, and why performance claims need to distinguish developer wait, billed machine time, and idle parallelism.

## Projects

### AI Quality Gate — In Progress

A hands-on AI/ML quality engineering platform focused on answering one question:

> **Is this AI system good enough to ship?**

The project will progressively cover:

```text
Data
  ↓
Data validation
  ↓
Feature validation
  ↓
Model validation
  ↓
LLM / RAG evaluation
  ↓
Safety & adversarial testing
  ↓
Performance & observability
  ↓
CI/CD quality gates
```

The implementation is intentionally incremental. Each capability is learned by building it, testing it, deliberately breaking it, and then hardening the quality checks.

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

```text
AI-assisted QE
      ↓
AI-powered QE
      ↓
AI / ML validation
      ↓
LLM + RAG evaluation
      ↓
AI reliability & safety
      ↓
Production AI quality engineering
```

The objective is not to collect AI tools. It is to develop the ability to **design, test, evaluate, and operationalize AI systems end-to-end**.

## Author

**Divyendu Shukla** — Staff Software Engineer in Test

[Website](https://divyendushukla.in) · [LinkedIn](https://linkedin.com/in/divyendushukla) · [GitHub](https://github.com/divyendu13)
