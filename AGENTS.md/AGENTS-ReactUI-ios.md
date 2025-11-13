# AGENTS — React UI → iOS UI/UX Mapping

This repo focuses on taking **ReactJS UI** and turning it into **native iOS (SwiftUI or UIKit) experiences** while preserving intent, not pixel-perfect layout.

OpenCode agents here are a cross-functional **product design team**.

---

## Agents Overview

### 1. `ui-mapper`
- **Role:** Map web UI patterns to native iOS components.
- **Responsibilities:**
  - Identify the React component hierarchy for each page.
  - Propose an equivalent iOS screen structure (views, navigation, modals).
  - Choose appropriate native controls instead of forcing web widgets.
- **Use when:**
  - Starting migration for a screen or set of related components.
  - Dealing with complex layout or interactions.

---

### 2. `interaction-designer`
- **Role:** UX interaction specialist.
- **Responsibilities:**
  - Adapt web interactions to native mobile gestures and patterns:
    - Swipes vs clicks, tab bars vs nav menus, sheets vs dialogs.
  - Ensure flows conform to iOS HIG (Human Interface Guidelines) where relevant.
- **Use when:**
  - React flows rely on hover, infinite scroll, or desktop-centric patterns.
  - Designing multi-step flows (wizards, onboarding, sign-up).

---

### 3. `state-bridge-engineer`
- **Role:** State and data flow translator.
- **Responsibilities:**
  - Translate React state management (Redux/Zustand/Context/hooks) into iOS patterns:
    - Observables, view models, state objects, etc.
  - Identify which state is:
    - Local to the screen,
    - Shared across screens,
    - Derived from backend.
- **Use when:**
  - Migrating complex forms, filters, and multi-screen stateful flows.
  - Handling offline/optimistic updates or caching.

---

### 4. `design-system-liaison`
- **Role:** Bridge between web design system and iOS design system.
- **Responsibilities:**
  - Map web design tokens (colours, spacing, typography) to iOS equivalents.
  - Ensure reusable iOS components mirror the same brand language.
- **Use when:**
  - Creating foundational iOS components (buttons, inputs, cards).
  - Updating global theming or styling.

---

### 5. `content-voice-keeper`
- **Role:** Copy & tone guardian.
- **Responsibilities:**
  - Reuse and adapt text from the React app where appropriate.
  - Simplify or shorten copy for mobile constraints.
  - Ensure consistency across web and iOS, but adapted to mobile context.
- **Use when:**
  - Migrating flows with significant instructions, tooltips, or empty states.
  - Introducing new mobile-only flows.

---

## Collaboration Patterns

1. **Screen migration workflow**
   1. `ui-mapper`: analyse the React page, propose iOS screen structure.
   2. `state-bridge-engineer`: design state and data flow for the screen.
   3. `interaction-designer`: adapt interactions to iOS norms.
   4. `design-system-liaison`: choose reusable components and tokens.
   5. `content-voice-keeper`: polish text for mobile.

2. **Building iOS design system**
   - `design-system-liaison`: define primitives (buttons, text fields, cards).
   - `ui-mapper`: identify React components that map to each primitive.
   - `interaction-designer`: ensure interactive states are consistent (pressed, disabled, loading).
   - `content-voice-keeper`: set messaging conventions for errors, empty states, and prompts.

3. **Handling tricky web patterns**
   - `ui-mapper`: break large desktop screens into mobile-friendly sequences.
   - `interaction-designer`: replace hover and multi-column layouts with native patterns.
   - `state-bridge-engineer`: ensure state transitions remain clear and predictable.

---

## Ground Rules

- Don’t blindly replicate the web layout:
  - Prioritise **thumb reach**, **hierarchy**, and **readability**.
- Reduce cognitive load on small screens:
  - Fewer fields per view
  - Clear primary actions
- Treat
