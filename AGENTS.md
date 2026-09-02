# AI QE Engineering — Agent Instructions

## Purpose

This repository is Divyendu Shukla's hands-on portfolio for transitioning from senior/staff Software Quality Engineering into **AI Quality Engineering / AI Validation Engineering**.

The goal is not to collect AI tools or certifications. The goal is to build practical, defensible expertise in **testing AI systems themselves**: LLM correctness and reliability, RAG quality, agent behavior, safety, observability, and production AI quality gates.

The central question for new work is:

> **Is this AI system good enough to ship, and what evidence proves it?**

## Candidate Background

Divyendu is a Staff Software Engineer in Test with ~10 years of QE experience and strong existing expertise in:

- JavaScript / TypeScript
- Playwright
- API and UI testing
- enterprise SaaS and distributed systems
- CI/CD
- Docker / Kubernetes
- JMeter / k6 performance testing
- Datadog / Splunk observability
- OWASP / OWASP ZAP security testing
- WCAG / axe-core accessibility testing
- AWS
- Claude / AWS Bedrock
- MCP and agentic test automation

Do **not** teach these as beginner topics unless a project explicitly requires deeper understanding. Use this existing Staff-level QE experience as leverage when introducing AI-specific testing concepts.

## Existing AI/QE Work

### QA-Agent

Public repository: https://github.com/divyendu13/qa-agent

QA-Agent is an autonomous AI quality-engineering agent using Claude via AWS Bedrock in a ReAct-style workflow. Implemented capabilities include:

- browser exploration
- Playwright test generation
- test execution
- AI-driven failure triage
- OWASP ZAP security scanning
- axe-core accessibility checks
- k6 load/performance testing
- unified reporting
- GitHub Actions integration

When discussing QA-Agent, describe only capabilities actually implemented in that repository. Do **not** imply that it already performs LLM evaluation, RAG evaluation, hallucination detection, model validation, agent trajectory scoring, or other capabilities unless those capabilities are subsequently implemented.

QA-Agent may later become a subject of agent evaluation, but it should remain a complementary project unless there is a strong architectural reason to merge it with the AI Quality Gate.

## Published Engineering Evidence

### AI-assisted TestCafe → Playwright migration

`articles/testcafe-playwright-ai-migration.md`

The project migrated 354 integration/E2E tests across 38 files, with roughly 55K lines of first-pass generated Playwright code.

The important engineering evidence is not simply that AI generated code. It includes:

- written engineering constraints / constitution
- architecture boundaries
- batch-loop execution
- machine-enforced conventions
- lint/build validation
- trace-based assertion review
- iterative correction
- human review gates

Preserve the distinction between **AI-assisted QE** and **testing AI systems themselves**.

### Playwright CI / shard balancing

`articles/playwright-ci-shard-balancing.md`

The investigation documents movement in PR feedback from roughly 45 minutes to 30 minutes and deliberately separates developer wait, billed machine time, and idle parallelism.

Important findings include:

- Playwright was approximately 2.3x faster per test than TestCafe.
- CI sharding was silently count-balanced rather than time-balanced.
- Playwright JUnit output lacked the `file` metadata expected by CircleCI timing-based splitting.
- A custom reporter restored usable timing metadata.
- Node spread improved from 7.6 minutes to 1.4 minutes.
- 73 superseded legacy specs were retired.
- Total test work dropped from 82.5 minutes to 67.2 minutes.
- Overall PR feedback moved from roughly 45 minutes to 30 minutes.
- Fixed environment/provisioning overhead created a practical lower bound.

These articles describe real engineering work. Preserve their factual claims and framing unless the user explicitly asks for editorial changes.

## Career Direction

Target roles include:

- AI Quality Engineer
- AI Test Engineer / Test Lead
- AI/ML Validation Engineer
- AI SDET / GenAI QE
- AI Evaluation / Reliability Engineer
- eventually Staff/Principal AI Quality Engineering roles

The portfolio story should progress as:

```text
AI-assisted QE
      ↓
AI-powered QE
      ↓
AI / ML validation
      ↓
LLM + RAG evaluation
      ↓
Agent reliability / safety
      ↓
Production AI quality engineering
```

The biggest current gap is **not general software engineering**. The primary gap is demonstrating the ability to systematically evaluate an AI system and produce defensible evidence that it is good enough to ship.

## Target AI-QE Capability Model

Prioritize practical capability in the areas commonly expected from enterprise AI Test Engineer / AI QE roles.

### LLM validation

- accuracy and factual correctness
- consistency
- robustness
- response relevance
- completeness
- hallucination detection
- context adherence
- citation quality
- multi-turn behavior and context retention

### RAG validation

- retrieval quality
- context relevance
- grounding / faithfulness
- answer correctness
- answer completeness
- context precision
- context recall
- stale or contradictory knowledge
- citation correctness

### Agentic AI validation

- task completion
- planning outcomes
- tool selection
- tool arguments
- execution order
- trajectory/path quality
- recovery behavior
- state handling
- repeated tool calls
- loops
- policy compliance
- efficiency

Traditional QE often asks:

> Did the expected function result occur?

Agentic QE must additionally ask:

> Did the agent make acceptable decisions and reach an acceptable outcome within defined constraints?

### AI safety / adversarial testing

- prompt injection
- indirect prompt injection
- jailbreak attempts
- data leakage
- unsafe tool invocation
- authorization failures
- privilege escalation
- tenant isolation
- guardrail effectiveness

### Evaluation and production quality

- golden / benchmark datasets
- synthetic evaluation data
- deterministic evaluators
- semantic / model-based evaluators
- evaluation pipelines
- regression detection
- thresholds and quality gates
- observability and tracing
- latency / throughput / cost
- CI/CD integration

## Tools to Learn Through Use

Tools are means, not achievements. Introduce them when they solve a concrete evaluation problem.

Likely useful tools include:

- pytest
- FastAPI
- DeepEval
- RAGAS
- Promptfoo
- LangSmith or Phoenix
- LangGraph or an equivalent agent framework
- Chroma or another simple vector store
- AWS Bedrock and/or another cloud LLM API where appropriate

Do not turn the roadmap into a checklist of libraries. The portfolio must show **why an evaluator exists, what defect it catches, what it misses, and how its result affects a release decision**.

## Main Project: AI Quality Gate

The main project is a hands-on **AI Quality Gate** platform.

Core question:

> Is this AI system good enough to ship?

The near-term project should emphasize GenAI evaluation rather than spending the month on a broad academic ML curriculum.

Planned progression:

```text
Evaluation dataset
      ↓
LLM evaluation
      ↓
Broken RAG system
      ↓
RAG evaluation
      ↓
Agent evaluation
      ↓
Safety / adversarial testing
      ↓
Observability
      ↓
CI/CD AI quality gate
```

Classical ML/data validation remains useful background and may be added later, but it must not displace the higher-priority LLM/RAG/agent evaluation work during the current intensive roadmap.

## Four-Week Intensive Roadmap

The current preparation window is approximately one intensive month. Optimize for interview-defensible evidence, not course completion.

### Week 1 — Evaluation foundations + practical Python

Learn only the Python needed to build and test the project effectively:

- pytest
- fixtures / parametrization
- async basics
- Pydantic
- FastAPI
- JSON/data processing
- embeddings
- cosine similarity intuition

Develop the mental model for:

- factuality
- faithfulness / groundedness
- answer relevance
- context precision
- context recall
- hallucination
- robustness
- consistency

Primary deliverable: a versioned evaluation dataset containing fields such as:

```text
question
expected_answer
expected_context
actual_answer
retrieved_context
evaluation_result
```

The dataset should become a first-class test artifact, not disposable demo data.

### Week 2 — Deliberately broken RAG system

Build a small RAG application over a corpus where ground truth can be labelled confidently. Existing public portfolio articles or public framework documentation are suitable sources.

Inject controlled defects such as:

- poor chunking
- irrelevant retrieval
- missing context
- stale documents
- contradictory information
- weak grounding
- unsupported answers
- citation errors

Use RAGAS, DeepEval, or custom deterministic checks where appropriate.

The deliverable is **not** "I used RAGAS." For each meaningful defect, capture:

```text
Injected defect
    ↓
Observed behavior
    ↓
Evaluator / metric that detected it
    ↓
Evaluator / metric that missed it
    ↓
Interpretation
    ↓
Quality decision
```

### Week 3 — Agent evaluation

Use QA-Agent as a foundation where practical, or build a deliberately small agent whose behavior can be controlled and evaluated.

Evaluate:

- task completion
- tool-selection correctness
- tool arguments
- execution order
- trajectory/path quality
- recovery
- state handling
- repeated tool calls
- loops
- policy compliance
- efficiency

Inject controlled failures such as:

- wrong tool
- wrong arguments
- tool timeout
- tool error
- ambiguous requirement
- partial result
- hallucinated capability
- repeated tool invocation
- infinite loop

Separate **final-answer correctness** from **trajectory correctness**. An agent reaching the right answer through an unacceptable path may still represent a latent defect.

### Week 4 — AI safety + CI quality gate

Test adversarial and governance scenarios including:

- direct prompt injection
- indirect prompt injection
- jailbreaks
- data leakage
- unsafe tool invocation
- authorization failures
- privilege escalation
- tenant isolation where applicable

Then combine evaluation into a release decision:

```text
AI system
    ↓
Evaluation dataset
    ↓
Deterministic + semantic evaluators
    ↓
Safety checks
    ↓
Threshold policy
    ↓
PASS / FAIL
    ↓
CI/CD
```

Document why each threshold exists and what type of regression should block a release.

## Priority Rules

### MUST learn / demonstrate

- practical Python for AI QE
- LLM evaluation fundamentals
- golden/evaluation datasets
- RAG fundamentals
- RAG evaluation
- hallucination / grounding testing
- agent behavior evaluation
- AI safety fundamentals
- CI quality gates
- metric limitations
- false positives / false negatives

### SHOULD learn through the project

- DeepEval
- RAGAS
- Promptfoo
- LangSmith or Phoenix
- LangGraph or equivalent
- vector database basics
- synthetic test generation
- AI observability

### NICE TO HAVE

- advanced knowledge-graph testing
- multiple agent frameworks
- deep model training/fine-tuning
- advanced fairness research
- broad cloud-AI vendor coverage

Do not allow NICE-TO-HAVE topics to consume time needed for MUST items.

## Evaluation Principles

Apply the same measurement discipline used in the CI investigation to AI evaluation.

- **Define the quantity before measuring it.** "AI quality" is not one metric.
- **Never treat one score as absolute truth.** Understand what each evaluator measures and misses.
- **Prefer deterministic checks when requirements are deterministic.** Examples include schema validity, citations existing, tool allowlists, authorization rules, maximum step counts, and required fields.
- **Use semantic evaluation where exact equality is inappropriate.**
- **Treat datasets as test infrastructure.** Version them, review them, and prevent them from silently going stale.
- **Measure distributions, not just averages.** A good mean can hide severe failures.
- **Understand evaluator variance.** Repeated LLM-as-judge results may not be identical.
- **Justify thresholds.** Do not choose pass/fail numbers because they look reasonable.
- **Test the evaluator.** Deliberately inject defects and verify whether the metric responds.
- **Track regressions against a baseline.** A relative degradation may matter even when an absolute threshold still passes.
- **Separate retrieval defects from generation defects.** A wrong answer caused by missing context is not the same failure as a wrong answer despite correct context.
- **Separate agent outcome from trajectory.** Final-answer success alone is insufficient for tool-using autonomous systems.

## Learning Strategy

Learn by building rather than completing large courses first.

For each meaningful capability:

1. Explain the concept briefly and why it matters.
2. Define the QE question and expected failure modes.
3. Implement the smallest useful capability.
4. Write automated tests/evaluators.
5. Deliberately introduce a failure or bad input.
6. Observe what detects it and what does not.
7. Fix or harden the system.
8. Document the lesson and limitations.
9. Extract interview-defensible evidence.

Do not build the entire platform in one pass. Keep the system incremental, reproducible, and demonstrable.

## Engineering Principles

- **Build incrementally.** Prefer small working milestones over speculative architecture.
- **Tests are first-class.** New functionality should normally come with automated tests or evaluators.
- **Test the AI, not only the wrapper.** Validate output behavior, retrieval, decisions, trajectories, and safety where applicable.
- **Deliberately test failure modes.** A project without controlled failures is weak QE evidence.
- **Measure before claiming improvement.** Never invent performance, accuracy, quality, or productivity numbers.
- **Do not fabricate experience.** Distinguish professional experience, personal project work, current learning, and planned work.
- **Keep claims interview-defensible.** Anything added to a resume or README should be backed by code, tests, evaluation data, documentation, or clearly stated project status.
- **Avoid unnecessary dependencies.** Add a library because it solves a problem, not because it appears in a job description.
- **Keep secrets out of Git.** Never commit API keys, cloud credentials, tokens, private endpoints, or proprietary data.
- **Keep public repos sanitized.** Do not introduce proprietary company/customer information.
- **Prefer clear Python and TypeScript/JavaScript over clever code.**
- **Document architectural and evaluation decisions.** Especially evaluator choice, dataset construction, threshold rationale, and known limitations.

## Resume / Portfolio Credibility Rule

Never promote a planned skill to established expertise merely because it appears in this roadmap.

Maintain a clear distinction between:

- existing professional experience
- existing personal project work
- currently learning / building
- experimental capability
- demonstrated capability

A skill should move into strong resume language only when it is backed by evidence that can be defended under interview questioning.

## Current State

- Two technical engineering articles are published in this repository.
- The README is positioned as an AI-QE portfolio landing page.
- QA-Agent exists as a separate public repository and is linked from this portfolio.
- Existing work already demonstrates AI-assisted QE, agentic automation, CI measurement discipline, security, accessibility, performance, and production-oriented engineering judgment.
- The major missing public evidence is systematic **evaluation of AI systems themselves**.
- The next major task is therefore to begin the AI Quality Gate with evaluation-first milestones.

## Immediate Next Milestone

Create the initial project under:

```text
projects/ai-quality-gate/
```

Do **not** begin with a large ML platform or an elaborate agent architecture.

Start with the Week 1 evaluation foundation:

```text
Small versioned golden dataset
        ↓
Simple LLM/RAG-facing test target
        ↓
Deterministic baseline checks
        ↓
pytest evaluation runner
        ↓
Structured evaluation results
        ↓
One deliberately injected failure
```

The first milestone should make the distinction between traditional assertions and probabilistic AI evaluation concrete.

## Working Style for Codex and Other Coding Agents

When starting a new task in this repository:

1. Read this file and the root README.
2. Inspect the existing project structure before changing anything.
3. Identify which roadmap milestone the task supports.
4. Explain the AI-QE concept and test strategy briefly before implementing it when the user is learning the concept.
5. Summarize the planned change.
6. Make the smallest coherent change.
7. Add or update relevant automated tests/evaluators.
8. Where useful, add a controlled failure case demonstrating why the evaluation exists.
9. Run relevant tests/checks.
10. Report what changed, what was tested, observed results, and limitations.
11. Do not rewrite unrelated files.
12. Do not silently invent requirements, results, metrics, or experience.

When multiple implementation choices exist, prefer one recommended path and explain the tradeoff rather than presenting a large menu of tools.

When the user asks to learn a concept, teach only enough theory to support the current implementation and connect it explicitly to AI Quality Engineering.

## Definition of Done

A feature is not complete merely because the code runs. Prefer:

```text
Implementation
    +
Automated tests / evaluators
    +
Controlled failure / edge case
    +
Measured result
    +
Interpretation
    +
Clear README/documentation
    +
Reproducible execution
```

For AI evaluation work, also ask:

```text
What defect does this catch?
What defect can it miss?
Why is this evaluator appropriate?
What would make the quality gate fail?
Can the result be defended in an interview?
```

The objective is a portfolio that demonstrates **AI quality engineering judgment**, not code volume or tool collection.
