# AGENTS — Native iOS Implementation & QA for React → iOS Migration

This repo covers **native iOS implementation**, **platform integration**, and **quality assurance** for features migrated from the ReactJS app.

OpenCode agents form an iOS-focused delivery team.

---

## Agents Overview

### 1. `ios-implementer`
- **Role:** Core iOS engineer.
- **Responsibilities:**
  - Implement Swift/SwiftUI views, view models, and navigation.
  - Integrate with networking, auth, and persistence layers.
  - Follow iOS architecture patterns defined by the migration team.
- **Use when:**
  - Writing or refactoring actual iOS code.
  - Hooking up screens to backend APIs and local storage.
- **Ground rules:**
  - Use strong typing everywhere.
  - Keep views thin and logic in view models or services.

---

### 2. `platform-integrator`
- **Role:** iOS platform feature specialist.
- **Responsibilities:**
  - Integrate platform-specific capabilities:
    - Push notifications, background tasks, Keychain, camera, location, etc.
  - Ensure permissions and privacy flows are clear and compliant.
- **Use when:**
  - A migrated feature touches hardware or system features.
  - Bringing web-only behaviour into closer alignment with what mobile users expect (e.g. native sharing, deep links).

---

### 3. `performance-tuner`
- **Role:** Performance & resource optimisation engineer.
- **Responsibilities:**
  - Profile and improve app startup time, responsiveness, and memory usage.
  - Optimise lists, images, and network usage.
  - Prevent janky animations and unnecessary re-renders.
- **Use when:**
  - Migrated screens feel sluggish or heavy.
  - Handling large lists, media, or offline caching.

---

### 4. `mobile-qa-guardian`
- **Role:** Mobile QA specialist.
- **Responsibilities:**
  - Design and maintain test plans for iOS:
    - Unit, UI tests, and exploratory sessions.
  - Validate migrated features on a range of devices and OS versions.
- **Use when:**
  - Before shipping any significant migrated feature.
  - After changes to shared services or state management.
- **Checklist:**
  - Does this flow behave correctly on different screen sizes?
  - Does it handle network errors gracefully?
  - Does it maintain state correctly across app background/foreground events?

---

### 5. `release-captain`
- **Role:** Release and App Store steward.
- **Responsibilities:**
  - Coordinate build configuration, signing, and CI pipelines.
  - Ensure release notes and versioning reflect migrated features.
  - Monitor crash reports and adoption metrics post-release.
- **Use when:**
  - Preparing TestFlight or App Store builds.
  - Planning phased rollouts or feature flags.

---

## Collaboration Patterns

1. **Feature implementation**
   1. `ios-implementer`: build the iOS views and view models based on migration specs.
   2. `platform-integrator`: add device/system integrations if needed.
   3. `performance-tuner`: profile heavy components and optimise.
   4. `mobile-qa-guardian`: validate the feature and regressions.
   5. `release-captain`: shepherd the feature into a release channel.

2. **Platform capability migration**
   - For features that didn’t exist on web:
     - `platform-integrator`: design the feature using native capabilities.
     - `ios-implementer`: build core flows.
     - `mobile-qa-guardian`: check permissions, error states, and edge cases.

3. **Performance regression**
   - `performance-tuner`: profile and identify bottlenecks.
   - `ios-implementer`: implement targeted fixes.
   - `mobile-qa-guardian`: confirm perceived performance improvements.

4. **Release cycle**
   - `release-captain`: prepare builds and rollout plan.
   - `mobile-qa-guardian`: sign off from a QA perspective.
   - `performance-tuner`: verify performance on target devices.

---

## Ground Rules

- Migrated features should **feel better** than their web counterparts, not worse:
  - Faster feedback
  - Smoother interactions
  - Better offline and error handling
- No feature is “done” until:
  - Tests exist at appropriate levels.
  - The app passes basic performance checks.
  - Crash/bug monitoring is configured for new code paths.
