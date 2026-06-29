# 🛑 Failure States and Empty States Guidelines

> "An error is a microinteraction that went wrong. The way you handle it can either rescue the user experience or destroy it." — Dan Saffer (Microinteractions)
> "Products must have personality. Even during a failure, a thoughtful, human message creates a connection that builds long-term user trust." — Aarron Walter (Designing for Emotion)

---

## 📜 Core Philosophy
Software is imperfect, and networks fail. A premium user experience is defined by how gracefully it handles these non-happy paths. We treat loaders, empty states, and errors as critical design elements, not edge cases. We design error messages that are human-readable and action-oriented, isolate UI crashes using localized error boundaries, and use skeleton mockups to optimize perceived load times.

---

## 🚨 The Anatomy of a Great Error Message
Never show raw system traces, server codes, or generic text like "An error occurred." Every error interface must follow the four-step protocol:
1.  **Human Language**: Use simple, conversational words. Avoid jargon (e.g., say "We are having trouble connecting to our payment partner" instead of "Transaction failed with status 503 Service Unavailable").
2.  **Explain the Situation**: State clearly *what* failed (e.g., "We couldn't save your shipping address").
3.  **Provide the Reason**: Tell the user *why* it happened (if known), without being overly technical (e.g., "Your internet connection appears to be offline").
4.  **Offer a Recovery Path**: Give the user a clear button or link to resolve the issue (e.g., a "Retry Payment" button, or an automatic redirect to input fields).

---

## 🖼️ Loading State Design: Skeletons vs. Spinners
*   **Perceived Wait Time**: Traditional spinning circles draw focus to the duration of the wait, making the app feel slower.
*   **Skeleton Screens**: Skeletons match the geometry and layout structure of the expected data cards or lists. They reduce perceived load times by preparing the eye for the oncoming content.
    *   *Rule*: Skeleton elements should match the height, width, and border-radius of active elements. Apply a subtle pulsing animation (`animate-pulse`) using HSL-based gray gradients.

---

## 📭 High-Conversion Empty States
An empty screen is not a blank canvas; it is a critical user onboarding opportunity. Every empty state layout must include:
1.  **Clarity**: Explain why the screen is empty (e.g., "You don't have any active projects yet").
2.  **Motivation**: Explain the value of taking action (e.g., "Creating a project allows you to collaborate with team members and track tasks in real-time").
3.  **Action**: Provide a prominent Call to Action (CTA) button that initiates the task immediately (e.g., a primary button labeled "Create Your First Project").

---

## 🛡️ Error Boundaries and Offline Recovery

### 1. UI Crash Containment (Error Boundaries)
*   **Decouple Components**: Do not let a crash in a secondary widget (e.g., a sidebar feed, a user profile badge) crash the entire application screen.
*   **Localized Fallbacks**: Wrap distinct component groups in error boundary wrappers. On error, catch the exception, log it to telemetry, and render a localized fallback layout (e.g., "This section is temporarily unavailable. [Retry]") while keeping the rest of the application fully interactive.

### 2. Offline Synchronization Loops
*   **Input Caching**: If the device loses internet connection during input (form edits, typing text), cache the data locally in memory or temporary local storage.
*   **Connectivity Indicators**: Display a non-blocking toast or banner indicating the offline state.
*   **Auto-Retry**: Listen for the browser's `online` event or mobile connection triggers. When connection returns, automatically flush cached updates to the API in the background and dismiss the offline indicator.

---

## 🛠️ First-Principles Application Examples (Illustrative Stack: SvelteKit, React, Tailwind, Bits UI)

> [!IMPORTANT]
> **DO NOT FORCE A TECH STACK CHANGE**: You must detect the project's existing UI tools (e.g., React/Next.js, SwiftUI, Tailwind, Material UI, Bootstrap) and map these principles directly to those tools. Under no circumstances should you attempt to rewrite, migrate, or propose changing a codebase to SvelteKit or Tailwind unless explicitly requested by the user. The stack below is purely illustrative.

### 1. React Component boundaries (e.g., React ErrorBoundary)
*   **Principle**: *Isolate client runtime rendering crashes using declarative component wrappers.*
*   *Application*: Wrap widgets in a class-based or helper-based `ErrorBoundary` component that overrides `componentDidCatch` to render a fallback layout, preserving the surrounding layout.

### 2. Layout Skeletons (e.g., Tailwind CSS)
*   **Principle**: *Build matching, low-contrast placeholder shapes to pre-layout UI geometry.*
*   *Application*: Use Tailwind's `bg-neutral-200 dark:bg-neutral-800 animate-pulse` utility classes on empty text and image shapes to mimic the actual typography and content heights.

### 3. Accessible Dialogs & Alerts (e.g., Bits UI / Melt UI)
*   **Principle**: *Ensure dialog-based alerts are accessible, keyboard navigable, and announced correctly by screen readers (ARIA).*
*   *Application*: Use unstyled accessible library primitives (such as Svelte's Bits UI Dialog or Melt UI Builder) to ensure keyboard focus trap and screen-reader announcements function correctly during critical error modals.
