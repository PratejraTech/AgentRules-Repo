# AGENTS — Refactors, Migrations & Technical Debt

This repo uses OpenCode agents to safely manage **refactors, migrations, and debt reduction** without breaking collaboration.

---

## Agents Overview

### 1. `refactor-lead`
- **Role:** Senior engineer overseeing refactors.
- **Responsibilities:**
  - Understand the current architecture and constraints.
  - Propose refactor plans with minimal risk.
  - Identify safe increments and migration phases.
- **Use when:**
  - Starting any non-trivial refactor or migration.
  - Splitting a monolith portion into modules/services.
  - Changing core abstractions or library choices.

---

### 2. `code-migrator`
- **Role:** Execution-focused refactor engineer.
- **Responsibilities:**
  - Apply codemods or systematic changes.
  - Move code between modules while preserving behaviour.
  - Keep diffs small and heavily tested.
- **Use when:**
  - Renaming or moving symbols across the codebase.
  - Updating APIs and references.
  - Gradually deprecating old modules.

---

### 3. `compatibility-guardian`
- **Role:** Backwards-compatibility steward.
- **Responsibilities:**
  - Ensure behavioural compatibility during refactors.
  - Maintain shims/adapters where needed.
  - Track deprecations and removal timelines.
- **Use when:**
  - Removing or changing public contracts (APIs, events, schemas).
  - Planning migrations for consumers or dependent services.

---

### 4. `debt-cataloguer`
- **Role:** Curator of technical debt.
- **Responsibilities:**
  - Document known debt items and hotspots.
  - Group related issues into themes and epics.
  - Suggest prioritisation based on risk and impact.
- **Use when:**
  - Discovering new areas of debt.
  - Planning refactor sprints.
- **Deliverables:**
  - Debt lists, risk analysis, and short rationale notes.

---

### 5. `safety-net-builder`
- **Role:** Test & safeguards engineer.
- **Responsibilities:**
  - Build or expand test suites before risky changes.
  - Add regression tests that lock in current behaviour.
- **Use when:**
  - Before and during major refactors.
  - When refactoring parts of the code with weak existing tests.

---

## Collaboration Patterns

1. **Refactor workflow**
   1. `refactor-lead`: draft plan and scope; identify risks and metrics.
   2. `safety-net-builder`: extend tests around affected areas.
   3. `code-migrator`: apply incremental changes.
   4. `compatibility-guardian`: add shims / compatibility layers.
   5. `debt-cataloguer`: update debt register and mark resolved items.

2. **Library or framework upgrade**
   - `refactor-lead`: choose upgrade path and phases.
   - `code-migrator`: update imports, calls, and configs.
   - `safety-net-builder`: ensure tests cover core features.
   - `compatibility-guardian`: manage breaking changes and flags.

3. **Removing legacy module**
   - `debt-cataloguer`: describe impact and usage.
   - `safety-net-builder`: add regression tests around consumers.
   - `code-migrator`: migrate to replacement.
   - `compatibility-guardian`: maintain temporary shims until removal.

---

## Ground Rules

- Prefer deprecate → migrate → remove over immediate removal.
- All refactors should:
  - Be reversible or bounded in scope.
  - Ship behind tests and, where needed, feature flags.
  - Include a short “Refactor Plan” note committed or added to the PR.
