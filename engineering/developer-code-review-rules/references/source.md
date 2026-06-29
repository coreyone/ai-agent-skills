---
description: Philosophy, values, and tactics for the legendary code reviewer. A guide from a senior architect to a junior developer.
---

# 🔍 The Architect's Guide to Code Review: Philosophy & Tactics

*Listen closely. Code review isn't a gateway; it's a lighthouse. Your job isn't to say "no"—it's to ensure that the developer who inherits this code two years from now (who might be you) doesn't want to burn the building down.*

---

## �️ The Prime Directive
**"The primary purpose of code review is to maintain the long-term health of the codebase."**
Functional correctness is for your test suite. Code review is for the *humans*. We review to ensure the design is sound, the complexity is managed, and the knowledge is shared. 

> "Any fool can write code that a computer can understand. Good programmers write code that humans can understand." — *Martin Fowler*

---

## 🧠 The Legendary Philosophy

### 1. The Standard: "Is it Better?"
Don't wait for perfection. Perfection is the enemy of progress. If a PR improves the overall health of the codebase, even if it’s not exactly how *you* would have written it, **approve it**.
*   **Google's Rule**: Technical facts and data overrule personal preference. If the author's choice is valid, don't block it just because you prefer a different color shed.

### 2. Egoless Engineering
You are not your code. When you review, you are critiquing a shared asset, not the person.
*   **Tactics**: Use "we" instead of "you." Instead of "You forgot the error handler," try "We should probably catch this exception here to prevent a crash."

### 3. Review the Forest, Then the Trees
Never start with nits (naming, whitespace, formatting). Start with the **Design**.
*   **The Ousterhout Rule**: If the underlying architecture is flawed, the variable names don't matter. Ask: "Should this code even exist?" "Is this the right place for this logic?"
*   **The Feathers Rule**: Look for "Seams." Is this code easy to test in isolation? If not, the abstraction is likely leaky.

---

## � Core Values & Values-Driven Tactics

### 📖 Clarity Over Cleverness
If a reader tells you something isn't obvious, **it isn't obvious**. Don't argue. Refactor.
*   **Uncle Bob’s Naming**: Names should be as carefully chosen as a first-born child. A variable name should reveal intent. If you need a comment to explain a variable, the name has failed.
*   **The "Huh?" Test**: If you have to tilt your head and squint to understand a "clever" one-liner, it’s technical debt.

### 🛡️ Complexity is the Enemy
Our job is to manage cognitive load. 
*   **Deep Modules**: (Ousterhout) Aim for powerful functionality behind simple interfaces. If a PR makes a module "shallower" (more interface for the same logic), question it.
*   **The Boy Scout Rule**: Always leave the code slightly cleaner than you found it. If you see a small refactor that simplifies the surrounding context, do it (or suggest it).

### ⚡ Speed and Momentum
A pending PR is a frozen asset. Review quickly or get out of the way. 
*   **Google's Speed Principle**: Common wisdom says "fast reviews prevent developer frustration." If you can't review it within 24 hours, communicate why.

---

## 🛠️ The Execution: Reviewer Tactics

### The Hierarchy of Review (Top-Down)
1.  **Correctness & Security**: Will this break the system or leak data?
2.  **Architecture & Design**: Is the logic in the right place? Is it composable?
3.  **Readability & Maintainability**: Can I understand this in 5 seconds?
4.  **Style & Nits**: (Automate this away). If it's not caught by the linter, it's rarely worth blocking over.

### Phrasing for Mentorship
*   **Instead of Demanding, Ask Questions**: "I noticed we're using a loop here; would a map-reduce approach make the data transformation more explicit?"
*   **Explain the "Why"**: Don't just give the solution; give the principle. "Using `const` here tells the next developer this value is immutable, which reduces the surface area for bugs."
*   **Call out the Wins**: If you see a particularly elegant solution, say so. Positive reinforcement builds elite developers faster than criticism.

### The "Must-Fix" vs "Nit" Distinction
Clearly label your feedback so the junior knows what is a blocker and what is a suggestion.
*   `[CRITICAL]`: Security risk or logic error. Must be fixed.
*   `[RFC]`: Request for Comment. I'm unsure about this design; let's discuss.
*   `[NIT]`: Stylistic preference. Please consider, but won't block.

---

## 🧐 The Common Sense Check (First Principles)

Beyond architecture and style, apply these common-sense filters derived from our tech stack values:

### 1. Dependency Skepticism
*   **The Question**: "Do we actually need this library, or can we write these 10 lines of code ourselves?"
*   **The Principle**: Every dependency is a potential vulnerability, a performance cost, and a maintenance burden. Prefer standard library solutions over 3rd party packages for trivial tasks.
*   **Red Flag**: Importing a massive utility library just to format a date or deep-clone an object.

### 2. The "Native" Test
*   **The Question**: "Could this be done with just HTML and CSS?"
*   **The Principle**: The browser platform is powerful. Native solutions are faster, more accessible, and future-proof.
*   **Red Flag**: Using complex JavaScript state management to toggle a modal or accordion that `<details>`/`<summary>` or CSS `:target` could handle.

### 3. Type Reality
*   **The Question**: "Do these types actually match what happens at runtime?"
*   **The Principle**: TypeScript is a lie we tell ourselves to sleep better. Ensure boundaries (API responses, user input) are validated at runtime, not just assumed correct by the compiler.
*   **Red Flag**: Casting `as Any` or `as Unknown` without a very specific, commented reason.

---

## 🏆 The "Elite Reviewer" Checklist

- [ ] **Design First**: Does this change fit the system architecture?
- [ ] **Simplicity**: Has the author introduced unnecessary abstractions or "speculative" code?
- [ ] **Clarity**: Could a junior dev on another team understand this without a walkthrough?
- [ ] **Testability**: Is the logic decoupled enough to be verified without the entire world being mocked?
- [ ] **The "Why"**: Does the PR description explain *why* the change was made, and does the code reflect it?
- [ ] **Empathy**: Is my tone helpful, constructive, and aimed at shared growth?

---

*Remember: You aren't just checking code; you're building a culture. Every review is a brick in the foundation of the team's engineering excellence.*
