# AI QE Engineering — Agent Instructions

## Purpose

This repository is Divyendu Shukla's hands-on portfolio for transitioning from Staff Software Quality Engineering into:

- AI Quality Engineering
- AI/ML Validation Engineering
- AI SDET / GenAI QE
- AI Evaluation Engineering
- AI Reliability Engineering

The primary specialization remains **engineering quality, reliability, and confidence in AI-powered systems**.

The goal is not to collect AI tools, certifications, framework names, or disconnected demos.

The goal is to build practical, defensible expertise in:

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

A supporting goal is to develop enough **AI systems engineering capability** to build the systems being evaluated.

This includes practical exposure to:

- LLM application construction
- RAG pipelines
- Structured output and tool calling
- Agent orchestration
- Context engineering
- Structured-data integration
- Event/trigger-driven AI workflows
- Human feedback loops
- Production-oriented observability and failure handling

This does **not** change the repository into a generic AI Engineering or ML Engineering portfolio.

The guiding principle is:

> **Build enough of the AI system to evaluate it credibly, then engineer confidence in its behavior.**

Every project should ultimately help answer:

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

The learning effort should focus primarily on the **AI-system-under-test layer**, while developing enough system-construction knowledge to understand how AI applications actually work end-to-end.

Do not turn the learning journey into generic frontend development, backend development, cloud certification preparation, or ML research.

---

# Career Direction

The primary target roles are:

- AI Quality Engineer
- AI Evaluation Engineer
- AI Reliability Engineer
- AI/ML Validation Engineer
- AI SDET / GenAI QE
- Staff / Principal Quality Engineer working on AI systems

The portfolio may also develop transferable skills relevant to adjacent roles such as:

- AI Automation Engineer
- Agentic Systems Engineer
- Applied AI Engineer
- AI Platform Quality Engineer

However, these adjacent roles should not cause the repository to lose its Quality Engineering identity.

The differentiator should become:

> **Deep Quality Engineering experience + AI systems understanding + AI evaluation + reliability engineering.**

Do not position Divyendu as an ML researcher or as someone with years of production AI engineering experience unless future professional experience supports that claim.

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
AI system construction fundamentals
      ↓
AI / ML validation
      ↓
LLM evaluation
      ↓
RAG system construction + evaluation
      ↓
Agent construction + reliability evaluation
      ↓
AI-native automation
      ↓
AI safety / adversarial testing
      ↓
Production AI quality & reliability engineering
```

The "system construction" stages exist to make evaluation knowledge practical and defensible.

They are not intended to turn the portfolio into a collection of generic chatbot or AI application demos.

Whenever possible:

```text
BUILD
  ↓
UNDERSTAND FAILURE MODES
  ↓
EVALUATE
  ↓
BREAK
  ↓
OBSERVE
  ↓
HARDEN
  ↓
AUTOMATE QUALITY GATES
```

Do not prematurely list future skills as established expertise on the resume.

Promote skills from "Learning / Building" to demonstrated capability only after they are implemented and defensible.

---

# Main Project: AI Quality Gate

The main new project is a hands-on **AI Quality Gate** platform.

Core question:

> **Is this AI system good enough to ship?**

The Quality Gate should progressively evaluate increasingly realistic AI systems rather than remaining a collection of isolated scoring functions.

---

# Consolidated Roadmap

This plan supersedes the earlier FastAPI/classical-ML-first sequence.

## Week 1 — Evaluation Foundations

Complete only a very small practical ML validation exercise covering:

- train/test split
- precision
- recall
- F1
- thresholds
- model regression

Then begin the real AI Quality Gate with:

- versioned evaluation dataset
- deterministic evaluators
- structured evaluation results
- explicit pass/fail thresholds
- deliberate failure cases
- one semantic/model-based evaluator

Do not spend the full week on classical ML.

The purpose of the ML exercise is to understand evaluation thinking, not to become an ML engineer.

---

## Week 2 — LLM + RAG System and Evaluation

Do not evaluate RAG only as an abstract concept.

Build the smallest useful RAG system first.

Understand and implement the basic flow:

```text
User Query
    ↓
Retrieval
    ↓
Context
    ↓
LLM
    ↓
Grounded Answer
```

The implementation should be intentionally small.

Then evaluate:

- correctness
- relevance
- groundedness
- hallucination
- retrieval quality
- context precision
- context recall
- citation accuracy
- missing context
- stale context
- conflicting context
- retrieval failure vs generation failure

Understand:

- embeddings
- chunking
- retrieval
- context construction
- generation

Only introduce vector databases or RAG frameworks when they provide clear value.

The goal is not to build an elaborate chatbot.

The goal is to understand enough of the RAG architecture to evaluate its quality properly.

Where useful, include structured business data or metadata so evaluation is not limited to document Q&A.

---

## Week 3 — Agent System + Reliability Evaluation

Build a small bounded agentic workflow before creating a large agent evaluation framework.

The agent should have a clear objective and a small number of tools.

Example:

```text
Goal
 ↓
Reason / Plan
 ↓
Select Tool
 ↓
Generate Arguments
 ↓
Execute
 ↓
Observe Result
 ↓
Choose Next Action
 ↓
Final Outcome
```

Where useful, introduce a simple event or trigger so the agent can respond to a system condition rather than only a user prompt.

Examples:

```text
Threshold exceeded
      ↓
Agent invoked
      ↓
Retrieve context
      ↓
Reason
      ↓
Select deterministic action
      ↓
Generate explanation
      ↓
Human feedback / escalation
```

Then evaluate observable agent behavior:

- task success
- tool selection
- tool arguments
- action order
- retries
- recovery
- loop detection
- authorization
- escalation
- unsafe/excessive agency
- prompt injection
- tool abuse
- final outcome quality
- latency
- cost

Evaluate observable behavior and system state.

Do not claim to evaluate hidden chain-of-thought.

Where actions have side effects, validate the resulting system state rather than only the natural-language response.

---

## Week 4 — Production AI Quality Engineering

Bring the previous capabilities together through:

- AI observability
- tracing
- regression detection
- evaluation reporting
- prompt/model/version comparison
- latency monitoring
- cost monitoring
- CI quality gates
- explicit PASS/BLOCK decisions

The final result should demonstrate a reproducible release decision based on explicit quality thresholds.

Where useful, capture:

```text
Input
 ↓
Retrieved Context
 ↓
Model / Agent Decision
 ↓
Tool Calls
 ↓
System Result
 ↓
Evaluation
 ↓
PASS / BLOCK
```

The Quality Gate should make failures diagnosable, not merely assign a score.

---

# AI Systems Engineering Supporting Track

AI system construction is a supporting competency, not a replacement for AI-QE.

Develop enough practical understanding of the following to evaluate realistic systems:

## LLM Application Construction

- model APIs
- prompts
- structured output
- tool/function calling
- context management
- error handling
- retries
- model configuration
- token/latency/cost awareness

## RAG

- ingestion
- chunking
- embeddings
- indexing
- retrieval
- context construction
- structured metadata
- grounding
- citation generation

## Agents

- bounded autonomy
- orchestration
- tool registries
- tool selection
- argument generation
- state
- memory where justified
- human-in-the-loop
- deterministic guardrails
- post-condition validation

## Operational AI Workflows

Understand architectures such as:

```text
Business/Data Signal
        ↓
Event / Trigger
        ↓
Context Retrieval
        ↓
LLM / Agent Reasoning
        ↓
Tool / Deterministic Action
        ↓
User / System Output
        ↓
Feedback
        ↓
Evaluation + Observability
```

This enables quality engineering for AI systems that actually perform business work rather than only generate text.

Do not over-engineer these systems.

Build only enough complexity to expose meaningful quality, reliability, safety, and observability problems.

---

# Deterministic Automation vs AI

An important engineering skill is deciding when AI should **not** be used.

For every AI-enabled workflow, ask:

1. Can this be solved reliably with deterministic software?
2. Does AI provide meaningful value?
3. Which decisions require probabilistic reasoning?
4. Which actions should remain deterministic?
5. What requires human approval?
6. What happens when the model is wrong?

Prefer:

```text
Deterministic software
        +
Bounded AI reasoning
        +
Explicit guardrails
        +
Post-condition validation
```

over unnecessary autonomous behavior.

The objective is reliable systems, not maximum AI usage.

---

# Learning Strategy

Learn by building rather than completing large courses first.

For each meaningful capability:

1. Explain the concept briefly when the current build needs it.
2. Ask Divyendu to reason about the design or quality strategy where appropriate.
3. Challenge weak assumptions and unsupported claims.
4. Build the smallest useful system or capability.
5. Add automated validation.
6. Deliberately break the system or provide bad input.
7. Observe and diagnose the failure.
8. Improve the evaluation or system design.
9. Add a regression test.
10. Document the lesson and identify portfolio/interview evidence.

Do not build an entire platform in one pass.

Keep the system incremental and demonstrable.

Keep the journey self-contained in this workspace.

Before writing new code, briefly restate the current milestone and give the next single task.

Treat Divyendu as a Staff-level QE engineer transitioning into AI QE.

The objective is production AI evaluation, testing, reliability, security, observability, and quality gates — supported by enough AI system engineering to make those skills real.

---

# Target Skills

These are a longer-term skill inventory, not prerequisites or a mandatory one-month checklist.

The consolidated roadmap determines the order and scope.

Use Python/pytest for practical evaluation.

Do not turn the journey into generic Python training.

Introduce each technology only when its role in the current build is justified.

## ML / Data

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
- explainability concepts
- fairness / bias concepts

## GenAI

- LLM fundamentals
- prompting
- structured output
- tool calling
- context engineering
- hallucination testing
- response correctness / relevance
- safety testing
- RAG
- embeddings
- retrieval evaluation
- agent reliability
- agent orchestration fundamentals

## AI System Construction

- model API integration
- structured outputs
- retrieval pipelines
- small RAG applications
- bounded agent workflows
- deterministic tools
- state and workflow management
- structured-data integration
- event/trigger-driven AI workflows
- human feedback loops
- failure handling

These are supporting capabilities.

Do not prematurely present them as production expertise.

## Evaluation / Production

- pytest
- FastAPI only if an API genuinely helps the architecture; it is optional
- DeepEval / RAGAS / promptfoo only after the underlying evaluation concepts have been understood and implemented directly
- observability and tracing
- latency / throughput / cost
- evaluation datasets
- regression testing
- CI/CD quality gates
- AWS / production deployment concepts

---

# Engineering Principles

- **Build incrementally.** Prefer small working milestones over large speculative architecture.

- **Build enough to evaluate.** For RAG and agent systems, implement a small real workflow before abstracting its evaluation.

- **Tests are first-class.** New functionality should normally come with automated tests.

- **Test the AI, not only the wrapper.** Validate model/data/output behavior where possible.

- **Test the system, not only the model.** AI failures may originate in retrieval, context construction, orchestration, tools, data, infrastructure, or deterministic business logic.

- **Prefer deterministic checks when available.** Use exact assertions for deterministic values and appropriate semantic evaluation for probabilistic outputs.

- **Separate deterministic and probabilistic behavior.** Do not use LLM judges for conditions that can be validated exactly.

- **Validate outcomes, not hidden reasoning.** Evaluate observable decisions, tool calls, outputs, traces, and resulting system state.

- **Deliberately test failure modes.** A project without failure demonstrations is not sufficient evidence of QE skill.

- **Design for diagnosability.** A failed quality gate should explain what failed and where, not merely return a low score.

- **Measure before claiming improvement.** Never invent performance, accuracy, quality, or productivity numbers.

- **Do not fabricate experience.** Distinguish clearly between existing professional experience, personal project work, and current learning.

- **Keep claims interview-defensible.** Anything added to a resume or README should be backed by code, tests, documentation, or clearly stated project status.

- **Avoid unnecessary dependencies.** Add a library only when the project benefits from it and explain why when relevant.

- **Avoid framework tourism.** Understanding RAG, evaluation, agent behavior, and reliability matters more than collecting framework names.

- **Keep secrets out of Git.** Never commit API keys, cloud credentials, tokens, or private endpoints.

- **Keep public repos sanitized.** Do not introduce proprietary company/customer information into this repository.

- **Prefer clear Python and TypeScript/JavaScript over clever code.**

- **Document architectural decisions.** Especially decisions about evaluation methodology, quality thresholds, deterministic vs AI behavior, and system boundaries.

---

# Evidence Levels

Maintain a clear distinction between knowledge and demonstrated capability.

Use the following mental model:

```text
LEARNED
  ↓
IMPLEMENTED
  ↓
TESTED
  ↓
BROKEN DELIBERATELY
  ↓
HARDENED
  ↓
DOCUMENTED
  ↓
INTERVIEW-DEFENSIBLE
```

A technology or capability should not automatically become a resume skill simply because it was studied.

Strong portfolio evidence should ideally include:

- working implementation
- automated tests
- failure cases
- evaluation results
- architectural explanation
- documented tradeoffs
- reproducible execution

---

# Relationship to Distributed Systems Quality Engineering

A separate learning track may cover deeper cloud-native and distributed-systems quality engineering, including:

- messaging
- queues
- retries
- idempotency
- eventual consistency
- Kubernetes
- failure injection
- resilience
- observability

Do not duplicate that entire roadmap here.

However, connect the concepts when AI systems depend on them.

For example:

```text
Agent
 ↓
Tool Call
 ↓
API
 ↓
Event
 ↓
Queue
 ↓
Worker
 ↓
Business Action
```

Testing the LLM alone is insufficient.

Quality may depend on:

- correct tool selection
- valid arguments
- event delivery
- idempotency
- retries
- downstream state
- observability
- recovery

The long-term objective is to understand AI reliability as a **system property**, not merely a model property.

---

# Current State

- Two technical articles are published in this repository.
- README is positioned as an AI-QE portfolio landing page.
- QA-Agent exists as a separate public repository and is linked from the portfolio README.
- AI Quality Gate is the next major hands-on project.
- AI-system construction will be introduced incrementally when required by evaluation milestones.
- No future RAG/agent/evaluation capability should be represented as completed until corresponding implementation and evidence exist.

---

# Immediate Next Milestone

Create the initial project under:

```text
projects/ai-quality-gate/
```

Current milestone:

Define and build the smallest evaluation runner for a bounded AI response task.

Start by designing the first evaluation case:

- input
- authoritative context
- expected behavior
- acceptable variations
- explicit failure rule

Then incrementally implement:

- versioned dataset
- deterministic checks
- structured results
- thresholds
- deliberate failure
- one semantic/model-based evaluator

Use Python/pytest.

Demonstrate a bad response being caught.

Test the limitations of the semantic evaluator against reviewed examples.

Do **not** jump ahead to RAG or agent orchestration before the evaluation foundation works.

When Week 2 begins, build a minimal RAG system before evaluating RAG behavior.

When Week 3 begins, build a bounded agent workflow before implementing agent evaluation.

---

# Working Style for Codex

When starting a new task in this repository:

1. Read this file and the root README.
2. Inspect the existing project structure before changing anything.
3. Identify the current roadmap milestone.
4. Summarize the planned change briefly.
5. Make the smallest coherent change.
6. Run relevant tests/checks.
7. Deliberately test at least one meaningful failure case where appropriate.
8. Report what changed, what was tested, and any limitations.
9. Do not rewrite unrelated files.
10. Do not silently invent requirements.
11. Do not skip ahead in the roadmap merely because a framework makes it easy.
12. Do not add a technology solely for resume value.

When the user asks to learn a concept, teach just enough theory to support the current implementation and connect it to AI-QE testing.

When implementing RAG or agent functionality, explain the system behavior before introducing an abstraction/framework.

Prefer first-principles understanding before framework-specific convenience.

---

# Definition of Done

A feature is not considered complete merely because the code runs.

Prefer:

```text
Implementation
    +
Automated tests
    +
Failure / edge-case test
    +
Evaluation where appropriate
    +
Observability / useful diagnostics
    +
Clear README / documentation
    +
Reproducible execution
```

For AI-system features, also ask:

```text
What can fail?
      ↓
Can we observe it?
      ↓
Can we evaluate it?
      ↓
Can we reproduce it?
      ↓
Can we prevent regression?
```

The objective is a portfolio that demonstrates engineering judgment, system understanding, and AI quality expertise — not just code volume or framework familiarity.
