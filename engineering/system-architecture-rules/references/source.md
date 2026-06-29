# 🏗️ System Architecture Rules

> "If you think good architecture is expensive, try bad architecture." — Brian Foote & Joseph Yoder

---

## 📜 Core Philosophy
Architecture is about the decisions that are hard to change later. A great system architecture is evolutionary, modular, and balances current constraints with future changeability. We prioritize separation of concerns, strict dependency directions, and isolating core business logic from outer delivery mechanisms (UI, databases, frameworks).

---

## 🏛️ Foundational Architectural Patterns

### 1. Clean / Hexagonal (Ports & Adapters) Architecture
*   **The Dependency Rule**: Source code dependencies must point only inward, toward the core business logic (Domain/Entities). Nothing in an inner circle can know anything about something in an outer circle.
*   **Entities (Core)**: Standardize enterprise business objects. They encapsulate the most general and high-level rules, unaffected by database or UI changes.
*   **Use Cases (Interactors)**: Contain application-specific business rules. They orchestrate the flow of data to and from the entities.
*   **Ports (Interfaces)**: Inward-facing boundaries (e.g., repository interfaces, service interfaces) defined by the core, implementing dependency inversion.
*   **Adapters (Implementations)**: Outward-facing implementations (e.g., SQL repositories, CoreData stores, REST controllers, UI views) that plug into the ports.

### 2. Modern Client-Side Architecture (iOS & Web)
*   **Model-View-ViewModel (MVVM)**:
    *   **Model**: Represents the raw domain data and business logic.
    *   **ViewModel**: Holds the state of the view, transforms model data for presentation, and exposes commands. Must be UI-independent (testable without importing `UIKit`/`SwiftUI` or browser DOM elements).
    *   **View**: Passive renderer of the state exposed by the ViewModel. Contains zero business logic.
*   **Unidirectional Data Flow (UDF)**:
    *   Used in Web (React Redux/Zustand) and iOS (The Composable Architecture - TCA).
    *   **State**: The single source of truth representing the current system condition.
    *   **Actions**: Explicit events sent to mutate state.
    *   **Reducers**: Pure functions that compute the next state based on the current state and incoming action.
    *   **Effects**: Side-effects (API requests, database reads) that run asynchronously and feed actions back into the system.

---

## 🧱 Modularization & Dependency Management

### 1. iOS Modularization (Swift Package Manager / Xcode Targets)
*   **Decoupled Targets**: Break monolithic apps into isolated SPM packages or framework targets:
    *   `CoreDomain`: Pure Swift, zero external dependencies, contains entities and use cases.
    *   `FeatureModule`: Contains SwiftUI views and ViewModels for a specific domain flow. Depends *only* on `CoreDomain` and lightweight UI design systems.
    *   `InfrastructureModule`: Concrete network clients, database stores (SwiftData/CoreData), and analytics implementations.
*   **Dependency Inversion**: Feature modules must never directly instantiate concrete infrastructure classes. Use dependency injection containers or composition roots to resolve dependencies.

### 2. Web Modularization (Monorepos & Workspaces)
*   **Workspace Decoupling**: Use standard package workspaces (npm/pnpm/yarn) to split features:
    *   `@app/core`: Pure TypeScript business logic, types, and clients.
    *   `@app/ui`: Reusable design system components (CSS/HTML skeleton).
    *   `@app/features/*`: Independent application features.
*   **Strict Imports**: Enforce boundaries via ESLint rules (e.g., `eslint-plugin-import` or Turborepo configurations) to prevent circular dependencies or illegal imports between sibling features.

---

## ⚡ Non-Negotiable Tactical Rules

1.  **Strict Dependency Inversion**:
    *   *Rule*: Lower-level modules (e.g., API clients, database wrappers) must depend on abstractions defined by higher-level modules (e.g., Business Logic / Use Cases).
    *   *Anti-pattern*: Importing a concrete API client directly inside a SwiftUI View or React Component.
2.  **Explicit Composition Root**:
    *   *Rule*: Perform all object instantiation and dependency wiring in a single, well-defined entry point of the application (e.g., `App.swift` or `main.ts`).
    *   *Benefit*: Simplifies testing and guarantees that dependencies are unified.
3.  **Boundary Isolation via DTOs (Data Transfer Objects)**:
    *   *Rule*: Convert network payloads (JSON) and database records (NSManagedObject, Prisma models) into clean domain models at the system boundaries.
    *   *Benefit*: Changes to API keys or database columns do not propagate into business logic or UI code.
4.  **No Speculative Generalization (YAGNI)**:
    *   *Rule*: Build systems for current requirements, but design them to be *replaceable*. Do not write "extensibility frameworks" for features you don't have.
5.  **Pure Domain Logic**:
    *   *Rule*: Keep core domain logic pure. It must not depend on UI rendering libraries, network sockets, or databases. If a class requires `import SwiftUI` or `import Express`, it is not a domain model.

---

## 🛠️ First-Principles Application Examples (Illustrative Stack: SvelteKit, SolidJS, Zero, Biome)

> [!IMPORTANT]
> **DO NOT FORCE A TECH STACK CHANGE**: You must detect the project's existing stack (e.g., Next.js, Express, React, React Native) and map these principles directly to those tools. Under no circumstances should you attempt to rewrite, migrate, or propose changing a codebase to SvelteKit, Bun, Drizzle, Zero, or Biome unless explicitly requested by the user. The stack below is purely illustrative.

### 1. Compilation-Based Reactivity vs. Virtual DOM (e.g., Svelte, SolidJS)
*   **Principle**: *Minimize runtime footprint and state tracking overhead via build-time optimization.* Svelte and SolidJS serve as prime examples, compiling reactivity directly into target DOM updates.
*   *Application*: Keep component state local and granular. In SolidJS (as an example of signal-based reactivity), signals are tracked at the DOM node level—avoid destructuring properties as it breaks tracking. Use local stores or runes (e.g., Svelte 5 `$state`) for unidirectional data flow.

### 2. Boundary Controller Isolation (e.g., SvelteKit Server Loads)
*   **Principle**: *Strictly decouple server data-retrieval contexts from presentation layouts.*
*   *Application*: In SvelteKit, treat `+page.server.ts` and `+layout.server.ts` as boundary controllers. Keep load functions pure: fetch, sanitize, and transfer clean JSON schemas (validated via schemas like Zod) to the client rather than exposing raw database objects.

### 3. Local-First Synchronization (e.g., Zero Sync Engine)
*   **Principle**: *Decouple user interaction response times from network request roundtrips by sync-replicating state to memory.*
*   *Application*: When using Zero, query local memory reactively instead of executing network calls. Mutate client-side state immediately (optimistic UI updates) and let the sync layer coordinate asynchronous background replication.

### 4. Unified Static Analysis (e.g., Biome)
*   **Principle**: *Maintain unified linting, formatting, and structural checks to block cyclical dependency chains before runtime.*
*   *Application*: Run unified tools (e.g., Biome) on save to guarantee module purity and consistent import rules.
