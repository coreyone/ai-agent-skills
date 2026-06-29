---
description:
globs:
alwaysApply: false
---
# Rule: Generating a Product Requirements Document (PRD)

## Goal

To guide an AI assistant in creating a detailed Product Requirements Document (PRD) in Markdown format, based on an initial user prompt. The PRD should be clear, actionable, and suitable for a junior developer to understand and implement the feature.

## Process

1.  **Receive Initial Prompt:** The user provides a brief description or request for a new feature or functionality.
2.  **Ask Clarifying Questions:** Before writing the PRD, the AI *must* ask clarifying questions to gather sufficient detail. The goal is to understand the "what" and "why" of the feature, not necessarily the "how" (which the developer will figure out).
3.  **Generate PRD:** Based on the initial prompt and the user's answers to the clarifying questions, generate a PRD using the structure outlined below.
4.  **Save PRD:** Save the generated document as `prd-[feature-name].md` inside the `/tasks` directory.

## Clarifying Questions (Examples)

The AI should adapt its questions based on the prompt, but here are some common areas to explore:

*   **Problem/Goal:** "What problem does this feature solve for the user?" or "What is the main goal we want to achieve with this feature?"
*   **Target User:** "Who is the primary user of this feature?"
*   **Core Functionality:** "Can you describe the key actions a user should be able to perform with this feature?"
*   **User Stories:** "Could you provide a few user stories? (e.g., As a [type of user], I want to [perform an action] so that [benefit].)"
*   **Acceptance Criteria:** "How will we know when this feature is successfully implemented? What are the key success criteria?"
*   **Scope/Boundaries:** "Are there any specific things this feature *should not* do (non-goals)?"
*   **Data Requirements:** "What kind of data does this feature need to display or manipulate?"
*   **Design/UI:** "Are there any existing design mockups or UI guidelines to follow?" or "Can you describe the desired look and feel?"
*   **Edge Cases:** "Are there any potential edge cases or error conditions we should consider?"

## PRD Structure

The generated PRD should include the following sections:

1.  **Introduction/Overview:** Briefly describe the feature and the problem it solves. State the goal.
2.  **Goals:** List the specific, measurable objectives for this feature.
3.  **User Stories:** Detail the user narratives describing feature usage and benefits.
4.  **Functional Requirements:** List the specific functionalities the feature must have. Use clear, concise language (e.g., "The system must allow users to upload a profile picture."). Number these requirements.
5.  **Technical Approach:** Detail the specific technical approach that best serves the functional requirements. Use clear, concise language (e.g., "The system must allow users to upload a profile picture."). 
6.  **Non-Goals (Out of Scope):** Clearly state what this feature will *not* include to manage scope.
7.  **Design Considerations (Optional):** Link to mockups, describe UI/UX requirements, or mention relevant components/styles if applicable.
8.  **Technical Considerations (Optional):** Mention any known technical constraints, dependencies, or suggestions (e.g., "Should integrate with the existing Auth module").
9.  **Open Questions:** List any remaining questions or areas needing further clarification.

## Target Audience

Assume the primary reader of the PRD is a **junior developer**. Therefore, requirements should be explicit, unambiguous, and avoid jargon where possible. Provide enough detail for them to understand the feature's purpose and core logic.

## Output

*   **Format:** Markdown (`.md`)
*   **Location:** `/task-god/tasks/`
*   **Filename:** `prd-[feature-name].md`

## Final instructions

1. Do NOT start implementing the PRD
2. Make sure to ask the user clarifying questions
3. Take the user's answers to the clarifying questions and improve the PRD

Knowledge-base: Where natural use ideas from these experts as inspiration —

Marty Cagan (product teams), Melissa Perri (product strategy), Nir Eyal (habit model), Ken Norton (product ops), Teresa Torres (discovery), Jeff Patton (story mapping), Ash Maurya (lean canvas), Eric Ries (lean startup), Clayton Christensen (JTBD), Don Norman (usability), Dan Olsen (lean product), Steve Krug (usability), Shishir Mehrotra (team rituals), Lenny Rachitsky (PM newsletter), Janna Bastow (roadmapping), Baymard Institute (e‑comm UX), Nielsen Norman (usability research), Edo van Royen (PRD templates), Shreyas Doshi (Product Management frameworks), Gibson Biddle (product strategy), John Cutler (North Star), Fareed Mosavat (growth loops),  Christina Wodtke (OKRs), Gokul Rajaram (prioritization), Adam Nash (growth), Andrew Chen (cold start), Brian Balfour (growth loops), Rahul Vohra (PMF engine), April Dunford (positioning), Jake Knapp (design sprint), Steve Blank (customer dev), Josh Elman (growth), Adam Thomas (one‑pager),Ian McAllister (backwards), Adam Waxman (PRD), Steve Morin (one‑pager), Hamilton Helmer (7 Powers), Annie Duke (thinking bets), Kunal Shah (CRED), Rory Sutherland (behavioral econ)
