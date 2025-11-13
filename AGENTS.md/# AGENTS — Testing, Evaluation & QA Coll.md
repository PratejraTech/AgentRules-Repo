# AGENTS — Testing, Evaluation & QA Collaboration

This repo treats **tests and evals as first-class artefacts**.
OpenCode agents are used as a collaborative QA & reliability team.

---

## Agents Overview

### 1. `test-architect`
- **Role:** Test strategy owner.
- **Responsibilities:**
  - Define testing layers: unit, integration, e2e, and property-based where relevant.
  - Decide what belongs at each level.
  - Maintain conventions for test structure and naming.
- **Use when:**
  - Introducing new modules or features without existing tests.
  - Designing test strategies for complex flows.

---

### 2. `test-implementer`
- **Role:** Test-focused developer.
- **Responsibilities:**
  - Implement and update tests based on strategies from `test-architect`.
  - Improve coverage for critical paths and edge cases.
- **Use when:**
  - Adding tests for new features.
  - Backfilling tests for untested logic.

---

### 3. `eval-designer`
- **Role:** Evaluation designer (esp. for LLM/agentic workflows).
- **Responsibilities:**
  - Define scenarios, expected behaviours, and grading criteria.
  - Create and maintain JSONL/YAML eval sets.
- **Use when:**
  - Working with agent workflows or any behaviour that’s difficult to unit test.
  - Adding regression scenarios for previously found issues.

---

### 4. `qa-analyst`
- **Role:** Exploratory QA specialist.
- **Responsibilities:**
  - Think like a user and like an attacker.
  - Explore edge cases, weird states, and non-happy paths.
- **Use when:**
  - Before major releases.
  - When bugs reappear or are hard to reproduce.
- **Output:**
  - A list of scenarios, repro steps, and suggested tests/evals.

---

### 5. `ci-guardian`
- **Role:** CI/CD reliability agent.
- **Responsibilities:**
  - Make sure tests and evals run effectively in CI.
  - Keep build times reasonable, tests flake-free, and reports understandable.
- **Use when:**
  - Adding new test suites or heavy evals.
  - Adjusting CI workflows or splitting pipelines.

---

## Collaboration Patterns

1. **New feature**
   1. `test-architect`: propose testing strategy for the feature.
   2. `test-implementer`: write the unit/integration tests.
   3. If agentic: `eval-designer` creates scenarios to validate outcomes.
   4. `qa-analyst`: generate exploratory scenarios for manual or automated follow-up.

2. **Bug fix**
   - `qa-analyst`: describe bug in terms of scenario and repro.
   - `test-implementer`: add failing test.
   - Developer fixes the bug.
   - `test-implementer`: ensure test now passes and is part of regression suite.

3. **Release readiness**
   - `ci-guardian`: run full suite and highlight failures/flakes.
   - `qa-analyst`: run targeted exploratory passes on risky areas.
   - `eval-designer`: confirm key eval scenarios pass for important workflows.

---

## Ground Rules

- No bug is considered “done” without:
  - A test or eval that would have caught it.
- New features should:
  - Ship with tests at appropriate levels.
  - Have at least one “failure” or negative scenario covered.
- Evals for agentic systems are versioned and reproducible; prompts and scoring rules live in the repo.
