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
