---
description: when working on front-end pages, these are visual design guidelines
---

### 🗺️ Layout & Navigation

* Place key actions and value props above the fold.
* Align elements to a consistent grid for visual flow.
* Limit primary nav items to 5–7 choices.
* Use clear, descriptive labels in menus.
* Keep your logo linked to home in the same spot.
* Highlight the current page in your nav.

### 🎨 5 Principles of Visual Design in UX (NN/g)
Following these principles drives engagement and increases usability by creating well-rounded and thoughtful visuals.

1.  **Scale**: Using relative size to signal importance and rank.
    *   Use no more than 3 different sizes.
    *   The most important element should be the largest.
2.  **Visual Hierarchy**: Guiding the eye in order of importance.
    *   Use 2–3 typeface sizes to indicate content levels.
    *   Use bright colors for important items and muted colors for secondary ones.
    *   Include small, medium, and large components to establish variety.
3.  **Balance**: A satisfying arrangement or proportion of design elements.
    *   **Symmetrical**: Elements distributed equally relative to a central axis (stable).
    *   **Asymmetrical**: Elements distributed unequally relative to an axis (dynamic/energetic).
    *   **Radial**: Elements radiate from a central point (leads eye to center).
    *   Establish an imaginary axis to verify if one area draws the eye too much.
4.  **Contrast**: Juxtaposition of dissimilar elements to convey they are different.
    *   Use contrast (size, color, etc.) to emphasize distinct functions or categories.
    *   Always use a color-contrast checker to ensure accessibility/legibility.
5.  **Gestalt Principles**: Perceiving the whole as opposed to individual elements.
    *   **Proximity**: Items visually closer together are perceived as the same group.
    *   **Closure**: The brain fills in missing pieces to create a whole (common in logos).
    *   Includes: Similarity, Continuation, Common Region, Figure/Ground, and Symmetry.

### 🔍 Scanning & Visual Hierarchy

* Design in an “F” or “Z” scanning pattern.
* Use size, weight, and color to show importance.
* Break content with headings, subheadings, and bullets where natural. 
* Limit body text lines to 50–75 characters.
* Set body font ≥16 px and line-height 1.4–1.6×.
* Reserve bold/color for true emphasis.

### 📄 Content & Copy

* Write scannable sentences and short paragraphs.
* Use chunking: group related ideas under clear headers.
* Lead with your core value proposition.
* Use simple, familiar words—not jargon.
* Add microcopy to guide next steps.
* Preview link destinations with tooltips or labels.

### 🖋️ Forms & Inputs

* Place labels above fields, aligned left.
* Group related fields with clear boundaries or whitespace.
* Provide inline validation and real-time feedback.
* Pre-fill sensible defaults when possible.
* Use progressive disclosure for long or optional fields.
* Put the primary call-to-action button after the last field.

### ⚡ Feedback & Error Handling

* Show system status (spinners, progress bars) for loading.
* Use clear, polite, action-oriented error messages.
* Offer undo or confirm for destructive actions.

### 🧠 Norman's Principles of Interaction

*   **Discoverability & Affordances**: Make it obvious what users can do. Buttons should look clickable, sliders should look draggable. The design itself should suggest its function.
*   **Signifiers**: Use explicit cues like icons, labels, and consistent styling to signal where and how to interact. Don't make users guess.
*   **Feedback**: Acknowledge every user action with immediate and clear feedback. Use visual cues (highlights, spinners), sounds, or haptics to confirm the system is responding.
*   **Mapping**: Create a natural and logical connection between a control and its effect. Swiping up should move content up. Volume sliders should go from left (quiet) to right (loud).
*   **Constraints**: Guide users and prevent errors by limiting available actions. Disable buttons that aren't relevant, use dropdowns instead of free-text for specific choices.
*   **Conceptual Model**: Ensure the interface presents a consistent and understandable system. Users should be able to predict what will happen when they perform an action.

### ♿ Accessibility & Performance

* Ensure text-to-background contrast meets WCAG AA.
* Make touch targets at least 44 × 44 px on mobile.
* Write semantic HTML and use ARIA roles appropriately.
* Optimize images and lazy-load offscreen content.
* Aim for page load < 3 seconds on mobile networks.
* Test keyboard-only navigation and focus order.

### 🎨 Color: Using Color to Enhance Your Design

*   **Color Harmonies**: Use the color wheel to identify sets that work well together.
    *   **Monochromatic**: Tones and shades of a single hue (easiest to start).
    *   **Analogous**: Colors next to each other on the wheel (low contrast).
    *   **Complementary**: Colors opposite on the wheel (high contrast).
    *   **Split-complementary**: A color plus two on either side of its complement (softens contrast).
    *   **Triadic**: Three equidistant colors.
*   **Creating a Palette**:
    *   **Limit to 3 Colors**: Fewer colors reduce distraction and reinforce visual hierarchy.
    *   **Follow Brand Guidelines**: Consistency across brand assets creates trust.
    *   **Iterate**: Swap colors in and out until the combination achieves the desired salience.
*   **The 60-30-10 Rule**:
    *   **60% Dominant color** (usually neutral).
    *   **30% Secondary color**.
    *   **10% Accent color** (reserved for primary CTAs and critical emphasis).
*   **Consistency is Key**: Use colors for the same purpose everywhere (e.g., if blue is for active links, use it only for active links).
*   **Cultural Context**: Color meanings (red for danger or luck) vary by culture; test with your specific audience.
*   **Legibility & Accessibility**:
    *   Test for contrast and color blindness (WCAG AA standards).
    *   Avoid "vibrating" color combinations (e.g., green text on an orange background).
    *   Use tools like `accessible-colors.com` to verify text-to-background combinations. Consider how text sits on the background color based on z-index.

### 🎨 BOLD Aesthetic Direction & Distinction

* **Commit to an Extreme**: Before coding, pick a bold aesthetic stance (brutally minimal, maximalist chaos, retro-futuristic, luxury/refined, etc.). Intentionality is the key to an unforgettable interface.
* **Avoid "AI Slop" Aesthetics**: Never default to generic AI-generated looks (e.g., Inter/Arial fonts, lilac gradients on white, typical Saas patterns). 
* **Creative Curation**: Use distinctive, characterful typography and unexpected layouts to separate from the sea of sameness.
* **Meticulous Refinement**: Production-grade quality comes from executing a singular vision with precision in every detail.

### 🧩 Don't Make Me Think (Steve Krug)

* Make navigation self-evident—users shouldn't have to puzzle over where to click.
* Eliminate unnecessary clicks and cognitive friction.
* Use familiar conventions (logo in top-left, search in top-right).
* Make it obvious what's clickable and what's not.
* Create clear, scannable visual hierarchies.
* Test with real users: if they hesitate, simplify.

### 🧠 Cognitive Psychology & Human Limits

* **Working Memory**: Limit simultaneous choices to 5–7 items (Miller's Law).
* **Recognition over Recall**: Show options rather than requiring users to remember them.
* **Cognitive Load**: Minimize extraneous information; every element should serve a purpose.
* **Chunking**: Group related information into digestible blocks.
* **Primacy & Recency**: Place important items at the start or end of lists.
* **System 1 vs System 2**: Design for fast, intuitive decisions (Kahneman); save deliberate thinking for critical actions.

### 🎯 Goal-Directed Design (Cooper, Reimann, Cronin)

* Design around user goals, not just tasks or features.
* Reduce "excise"—work the interface forces users to do that doesn't accomplish their goal.
* Create  based on user behavior patterns, not demographics.
* Optimize for intermediate users—they're the largest group.
* Provide accelerators (shortcuts, keyboard commands) for experts.
* Every screen should clearly support a user goal.

### ✨ Microinteractions (Dan Saffer)

* **Triggers**: Make the starting point obvious (button, gesture, system event).
* **Rules**: Define what happens during the interaction (animation, state change).
* **Feedback**: Confirm the action happened (visual, auditory, haptic).
* **Loops & Modes**: Use sparingly; ensure users can exit easily.
* Details matter—small interactions create delight and trust.

### 🔁 Behavioral Design & Habit Formation (Nir Eyal)

* **Trigger**: External (notification, email) or internal (emotion, routine).
* **Action**: Make the desired action as easy as possible.
* **Variable Reward**: Provide unexpected positive outcomes to maintain interest.
* **Investment**: Ask users to put in effort (content, data) to increase return likelihood.
* Design ethical hooks—build positive habits, not addictions.

### 📐 Universal Design Principles (Lidwell, Holden, Butler)

* **Consistency**: Use patterns consistently across the interface.
* **Affordance**: Design elements should suggest their use.
* **Progressive Disclosure**: Reveal complexity gradually as users need it.
* **Fitts's Law**: Larger targets and shorter distances = faster interaction.
* **Hick's Law**: More choices = longer decision time; simplify when possible.
* **Aesthetic-Usability Effect**: Beautiful, distinctive designs feel more usable. Elegance comes from executing a bold vision well, not just avoiding errors.

### 🛤️ The Five Planes of UX (Jesse James Garrett)

* **Strategy**: Align product goals with user needs.
* **Scope**: Define features and content requirements.
* **Structure**: Organize information architecture and interaction design.
* **Skeleton**: Design navigation, interface, and information layout.
* **Surface**: Apply visual design, typography, and brand elements.
* Each plane builds on the previous; decisions should cascade upward.

### 🗂️ Information Architecture Fundamentals (Morville, Rosenfeld, Arango)

* **Findability**: Users should be able to find what they need quickly and intuitively.
* **Organization Systems**: Exact (alphabetical, chronological, geographic) or ambiguous (topic, task, audience).
* **Labeling**: Use clear, consistent, user-centered labels—avoid internal jargon.
* **Navigation**: Provide global, local, and contextual navigation options.
* **Search**: Complement browsing with robust search; support both strategies.
* **Controlled Vocabularies**: Use consistent terminology across the system.

### 📊 Making Information Understandable (Wurman, Tufte, Covert)

* **LATCH**: Organize by Location, Alphabet, Time, Category, or Hierarchy.
* **Data-Ink Ratio**: Maximize info, minimize decoration (Tufte).
* **Show Comparisons**: Present data in context for meaningful interpretation.
* **Clarity over Cleverness**: Remove chart junk; every visual element must serve a purpose.
* **Progressive Layering**: Start simple, reveal depth on demand.
* **Make Meaning Obvious**: Don't make users work to understand your information.

### 🏷️ Classification & Organization (Ranganathan, Svenonius, Brown)

* **Faceted Classification**: Allow users to filter by multiple attributes (size, color, price, etc.).
* **Taxonomies**: Create hierarchical structures that reflect user mental models.
* **Polyhierarchy**: Allow items to exist in multiple categories when appropriate.
* **Controlled Vocabularies**: Maintain consistent naming and tagging.
* **Five Laws of Library Science**: Books are for use, every reader their book, every book its reader, save the time of the reader, libraries are growing organisms (apply to digital content).

### 🧭 Wayfinding & Spatial Thinking (Lynch, Hinton)

* **Paths**: Clear routes through content (breadcrumbs, progress indicators).
* **Edges**: Boundaries between different areas or contexts.
* **Districts**: Themed areas with distinct character (dashboard, settings, content library).
* **Nodes**: Key decision points (homepages, hubs, intersections).
* **Landmarks**: Memorable reference points (logos, heroes, unique features).
* **You Are Here**: Always show users their current location in the system.

### ✏️ Sketching & Card Sorting (Buxton, Spencer)

* **Sketch First**: Low-fidelity exploration before high-fidelity design.
* **Rapid Iteration**: Generate many ideas quickly; refine later.
* **Card Sorting**: Let users organize content to inform IA.
* **Open vs Closed**: Open sorting reveals mental models; closed sorting validates structure.
* **Prototype to Think**: Use sketches and prototypes as thinking tools, not just deliverables.

### 🧠 Cognitive Limits & Bounded Rationality (Miller, Simon)

* **The Magical Number 7±2**: Working memory holds ~5-9 items; chunk information accordingly.
* **Satisficing**: Users choose the first acceptable option, not the optimal one.
* **Bounded Rationality**: People make decisions with limited info and cognitive capacity.
* **Reduce Cognitive Load**: Don't force users to hold too much in memory.
* **Recognition over Recall**: Show options instead of requiring memory.

### 🧩 Underrated

#### Transition Cost
* Great designers do not only optimize screens; they optimize the cost of moving between screens, states, and decisions.
* Every modal, redirect, accordion, tab, and step change has a comprehension cost. Spend that cost deliberately.
* Junior teams often count clicks; senior teams count mental resets.

#### Recovery Quality
* Usability is proven when the user is interrupted, confused, or wrong.
* Legendary designers obsess over how fast someone can recover from an error, backtrack, or resume after a pause.
* A flow that works only when nothing goes wrong is fragile, not usable.

#### Interaction Pace
* Not every action should feel equally urgent. The interface should slow users down for risky actions and speed them up for routine ones.
* Visual calm, confirmation patterns, and spacing all shape decision pace.
* Junior teams focus on efficiency everywhere; experts design for appropriate speed.

#### Choice Framing
* The order, grouping, and default presentation of choices often matters more than the number of choices.
* Strong designers remove false equivalence between primary, secondary, and destructive actions.
* Users should not have to decode which option is safest, fastest, or recommended.

#### Continuity of Context
* People navigate better when they can keep their place, compare options, and understand what changed.
* Preserve entered data, scroll position, selection state, and nearby context whenever possible.
* Forcing users to reconstruct context is a hidden usability tax.

#### Secondary Path Clarity
* Cancellation, dismissal, skip, edit later, save draft, and "not now" paths deserve explicit design.
* Senior designers know users feel trapped long before they complain.
* Freedom of movement increases trust in the primary path.

#### Label Precision
* Small wording changes can remove large amounts of hesitation.
* Legendary designers care whether a button says "Continue," "Review order," or "Pay now" because each one sets a different expectation.
* Vague labels make otherwise clean interfaces feel harder than they are.

### 💎 Gems

* **Hesitation Is a Signal**: If a user pauses, re-reads, or hovers without acting, the interface is asking them to think too hard.
* **The Best Default Is the One Users Would Have Chosen Anyway**: Smart defaults should reduce effort without creating fear of hidden consequences.
* **Users Need Closure at Every Step**: After each action, they should know what happened, what state they are in, and what they can do next.
* **A Good Flow Survives Interruption**: If someone is distracted for 10 minutes and returns lost, the flow was too brittle.
* **Warnings Should Be Rare Enough to Matter**: When everything is emphasized, nothing is credible.
* **The Interface Should Teach Itself**: The best products reduce the need for onboarding by making correct use feel obvious in context.
* **The Hardest Part Should Feel Shorter Than It Is**: Break effort into visible progress, smaller chunks, and reassuring checkpoints.
* **Users Judge Trust Through Edge Cases**: Empty results, failed payments, expired sessions, and permissions errors shape product credibility more than polished hero states.
* **The Exit Should Be as Clear as the Entrance**: People trust systems more when backing out, undoing, or changing their mind feels safe.
* **Clarity Beats Brevity When Stakes Are High**: Shorter copy is not always better; use enough words to remove ambiguity when the decision matters.


Whitespace isn’t empty—generous margins and spacing boost readability by easing cognitive load and speeding eye tracking.
**Key takeaway:** a clear grid plus typographic hierarchy with ample whitespace creates **balance**, **clarity**, and **scannability**.

Below, 25 NN/g–inspired rules for margins, spacing, headline sizing, font sizing, and whitespace.

### 🎯 Margin & Gutter

1. Frame content with ≥10% viewport margins to anchor and protect.
2. Align everything to an 8 px baseline grid for consistent rhythm.
3. Match column gutters to page margins for visual symmetry.
4. Signal new sections with whitespace at least as tall as the page margin.
5. Group form elements with 8 px between label and field, 16–24 px between groups.

### 🖋️ Spacing & Typography

6. Use body text ≥16 px for legibility across devices.
7. Set line height to 1.5–1.75 × font size for smooth reading.
8. Limit line length to 50–75 characters to aid focus.
9. Add 4–8 px tracking on uppercase headlines for glanceability.
10. Reserve all-caps for labels; use sentence case in paragraphs.
11. Stick to two typefaces and consistent weight/italic variants.
12. Space paragraphs by 1.5–2 × line height to group ideas.

### 📏 Headline & Font Sizing

13. Establish a modular scale (1.25–1.618 ratio) for harmonious sizing.
14. Make H1 ≥2 × base size, H2 ≈1.5 ×, H3 ≈1.25 × to guide the eye.
15. Limit to three heading sizes—small, medium, large—for clarity.
16. Use 24–32 px for primary headlines; 18–20 px for secondary.
17. Give each heading a top margin of 2 × line height to separate sections.
18. Align headings to the baseline grid for consistent vertical flow.

### ⚖️ Balance & Whitespace

19. Group related items tightly; separate unrelated ones generously.
20. Distribute whitespace symmetrically around focal elements.
21. Leverage the golden ratio for element sizing and gaps.
22. Ensure ≥8 px clear space around buttons and interactive controls.
23. Apply uniform padding inside cards and UI elements for stability.
24. Use a defined spacing scale (4, 8, 16, 24, 32 px) for predictability.
25. Test across breakpoints; tweak margins and font sizes to keep balance.


Key Style Pillars 
1. Typography-Led Design
Primary Font:Elegant, high contrast, often large and center-aligned
Secondary Font: Used for body copy, nav, labels — modest and clean
Typography is the hero — large headers, lots of whitespace, precise tracking
Embrace large type sizes for emotion and impact — hero headers should command space.

3. Use Editorial Layouts
Build with a modular, grid-based layout — lots of whitespace, visual rhythm, and breathing room. Center-align key content in hero sections and stack vertically on mobile. Big type, small captions. Mobile-first stacking.
Often structured like a magazine: wide gutters, generous margins. Use generous padding and margins (24–48px) — spacing is branding. Section blocks breathe — nothing cramped.

3. Use Deliberate Motion animations
Use subtle, elegant transitions — 0.2–0.3s ease-in-out fades or scaling. Never flashy. Micro-interactions only. Scroll reveals, slight fades. Smooth. 

---

### 📱 Device-Specific Usability (NN/g Standards)

#### **Mobile: The Context of Immediacy**
*   **Touch Targets**: Minimum 44x44 px (ideal 48x48 px or 1cm x 1cm) to prevent "fat-finger" errors.
*   **The Thumb Zone**: Place primary actions in the center and lower-left/right areas where thumbs naturally rest. Avoid critical actions in top corners.
*   **Minimize Input**: Use biometric auth, numeric keypads for numbers, and auto-complete to reduce the "typing tax."
*   **Content Prioritization**: Adopt a "mobile-first" approach—ruthlessly prioritize top-tier content and hide secondary "nice-to-haves" in menus.
*   **Avoid Interstitials**: Pop-ups and overlay "app-install" prompts disrupt the user's flow and hurt SEO.
*   **Single-Column Focus**: Stack elements vertically to avoid horizontal scrolling (the #1 mobile UX sin).

#### **Tablet: The Transition Zone**
*   **Orientation Agnostic**: Design for both Landscape (consumption) and Portrait (reading) modes. Users switch frequently.
*   **Fat Finger Problem**: While tablets have more space, they are still touch-based. Keep targets large and spacing generous—don't shrink desktop layouts.
*   **Ergonomic Zones**: Primary navigation should be on the sides (where hands hold the device) rather than top-center.
*   **Avoid Hover-Dependency**: Tablets don't have a cursor hover. Ensure all interactive cues are active and visible without a "mouse-over."
*   **Gestural Cues**: Support standard swipes and pinches, but always provide a visible alternative (e.g., a "Next" button).

#### **Desktop: Efficiency & Precision**
*   **Precision Interaction**: Leverage the mouse's high accuracy for smaller targets, but keep focal points clear to aid scanning.
*   **Information Density**: Use the horizontal real estate to show related information side-by-side, reducing the need for deep navigation.
*   **Keyboard Accelerators**: Provide shortcuts (Ctrl/Cmd + K) and Tab-order mapping for power users who value speed over clicking.
*   **Hover Affordances**: Use tooltips and subtle state changes (color, scale) to signal interactivity before a click happens.
*   **Multi-Window Context**: Desktop users often multitask. Ensure page titles and favicons are descriptive enough for users with 20+ tabs open.
*   **The "F" Pattern**: Align key information along the top and left margins, where desktop users spend 80% of their viewing time.

---

### 🛒 Commerce UX Philosophy (Baymard, Nielsen Norman, Google)

*   **The Low Effort/High Certainty Rule**: People buy only when the effort to purchase is low and the certainty of the outcome (fit, price, delivery) is high.
*   **Cost Truth**: No surprises. Show subtotals, shipping, and taxes as early as possible. If shipping is free, state "$0" explicitly.
*   **The Checkout Principle**: Checkout is for execution, not persuasion. Remove all distractions, headers, and secondary navigation once the user enters the funnel.
*   **Guest Checkout First**: Forced account creation is the #1 cause of abandonment. Always prioritize Guest Checkout; offer account creation *after* the order is confirmed.
*   **PDP "Fit, Risk, Logistics"**: A product page must answer three questions: 1) Will it fit my needs? (Details/Reviews) 2) What is my risk? (Returns/Warranty) 3) How do I get it? (Shipping ETA).
*   **Mobile-First Momentum**: On mobile, use sticky CTAs and one-column forms. Preserve state during errors so users never have to re-enter non-sensitive data.
*   **Friction is Cumulative**: Every unnecessary field, clever label, or generic error message adds weight. Reduce fields to the absolute minimum required for fulfillment.
*   **Confidence Indicators**: Use micro-copy like "You won't be charged yet" or "Securely processed by Stripe" near primary action buttons to lower anxiety.
Use subtle, elegant transitions — 0.2–0.3s ease-in-out fades or scaling. Never flashy. Micro-interactions only. Scroll reveals, slight fades. Smooth. 


# Forms • Buttons • Navigation — Usability Rules (First Principles + Execution)
Goal: reduce user effort, prevent errors, preserve momentum, and make “what to do next” unmistakable.

---

## 0) First Principles (the “physics”)
- **Attention is scarce** → remove distractions, reduce scanning work, create clear visual hierarchy.
- **People avoid uncertainty** → show constraints, requirements, and outcomes *before* they commit.
- **Errors are expensive** → prevent first, detect early, recover fast, never punish with lost input.
- **Users follow scent** → labels and navigation must predict the destination and content accurately.
- **Control builds trust** → users must be able to undo, edit, and verify without starting over.
- **Consistency reduces load** → same patterns in the same places, every time.

---

# A) FORMS (any web form)

## A1) Form Structure & Layout
### First principles
- Users complete forms fastest when they can treat them as a **single linear task**.
- Grouping reduces cognitive load; long forms fail when users can’t build a mental model.

### Execution rules
- **One column** layout for most forms (especially mobile).
- **Logical grouping** with headings (e.g., “Contact”, “Shipping”, “Payment”).
- Put **easiest, confidence-building fields first**; keep “hard” fields later (payment, ID numbers).
- Keep form width readable (avoid ultra-wide forms).
- If multi-step, show:
  - **Step names** that match real tasks (Address → Delivery → Payment → Review).
  - **Progress indicator** + ability to go back without data loss.
- Provide **summary** (read-only) before final submit for high-stakes forms.

## A2) Labels, Help, and Microcopy
### First principles
- Users should never have to remember what a field was after they start typing.
- Labels must be **always visible** to preserve context.

### Execution rules
- Use **persistent labels** (not placeholders as labels).
- Labels go **above inputs** (best for scan + responsive).
- Use placeholders only for **examples/format hints** (e.g., “name@domain.com”).
- Add short “helper text” only when it prevents common mistakes.
- Avoid internal jargon; use user language (plain, specific).

## A3) Required vs Optional (and “minimalism that actually works”)
### First principles
- Users cannot reliably infer what’s required across sites; ambiguity causes avoidable errors and abandonment.

### Execution rules
- Explicitly mark **both**:
  - Required (e.g., “*” + legend OR “Required”)
  - Optional (“Optional” text)
- Avoid global statements like “All fields required” unless you ALSO ensure users will see it.
- Remove optional fields unless they enable a clear user benefit.
- If a minority needs a field (e.g., Address Line 2, delivery instructions):
  - Hide behind “+ Add … (optional)” to reduce intimidation.

## A4) Input Types, Defaults, and Autocomplete
### First principles
- Typing is slow and error-prone; selection can be faster but can also hide options and increase hunting.

### Execution rules
- Use the right control:
  - **Radio** for ≤6 mutually exclusive options.
  - **Select** only when options are long or standardized (e.g., State).
  - **Typeahead** for large sets (City, Airport, Company).
- Use correct HTML attributes:
  - `type=email/tel/number` as appropriate
  - `autocomplete` tokens (name, email, street-address, postal-code, cc-number, etc.)
- Use safe defaults only when they’re correct for most users.
- Don’t over-format inputs while typing (avoid “cursor jump”).
- Accept common variants (spaces in card numbers, hyphens in phone numbers) and normalize on submit.

## A5) Validation Timing (when to show errors)
### First principles
- Too-early errors feel hostile and distract; too-late errors create rework.

### Execution rules
- Validate:
  - **On blur** (when user leaves field) for format constraints.
  - **On submit** for cross-field logic (e.g., shipping methods depend on address).
- Do **not** show “invalid” while the user is mid-entry unless it’s unquestionably wrong (e.g., letters in a numeric-only field).
- Show constraints upfront (password rules, min/max length, required formats).

## A6) Error Messages (tone, placement, and recovery)
### First principles
- Errors should be *diagnostic*, not accusatory.
- Recovery must be local, specific, and fast.

### Execution rules
- Place error message:
  - **Inline near the field**, and
  - Provide a **top summary** only for long forms (with anchor links to fields).
- Error message formula:
  - **What happened** + **how to fix** + **example**
  - “ZIP code must be 5 digits. Example: 94110.”
- Preserve user input after errors (especially in long forms).
- Use one strong visual indicator for errors (avoid piling on: red border + icon + banner + toast).
- Focus management:
  - On submit with errors → move focus to the first error; keep context.
- For server-side errors:
  - Don’t wipe fields.
  - Provide a retry path and keep form state intact.

## A7) Primary Submit UX (prevent double-submit + uncertainty)
### First principles
- Users need clear system status during submission; ambiguous “nothing happened” causes rage clicks.

### Execution rules
- On submit:
  - Button becomes **loading** (“Submitting…”) and temporarily disables.
  - Keep page stable (no layout jump).
- If submission is slow:
  - Show progress or reassure (“This can take up to 10 seconds.”).
- Confirm success with a clear success state + next step (“Saved”, “Order confirmed”, “We emailed you”).

## A8) Accessibility Baselines for Forms
### Execution rules
- Every input has a programmatic label (`<label for=…>`).
- Error messages are announced to screen readers (ARIA live region or described-by).
- Keyboard navigation works end-to-end; focus states visible.
- Touch targets are large enough and spaced (avoid mis-taps).

## A9) Form QA Checklist (ship gates)
- Required/optional unambiguous on every step.
- Tab order logical; Enter submits only when safe.
- Data persists across refresh/back navigation where expected.
- Errors are specific; examples included.
- Inline validation doesn’t fire prematurely.
- Mobile keyboards correct (email keypad for email, numeric for ZIP).
- Autocomplete works for common browsers.
- Screen reader flow tested for: label reading, error announcements, success confirmation.

---

# B) BUTTONS (CTAs, hierarchy, placement)

## B1) Button Hierarchy
### First principles
- Users choose based on *visual prominence* first, text second.
- Too many equal-weight buttons force slow reading and mistakes.

### Execution rules
- Define tiers:
  - **Primary** (1 per view) — the main “continue/submit”
  - **Secondary** — alternative action
  - **Tertiary** — low emphasis (links / subtle buttons)
- Primary must be:
  - **Uniquely styled**
  - **Most prominent**
  - **Consistently placed**
- Avoid styling multiple actions as “primary” in the same view.

## B2) Placement & Predictability
### First principles
- Users build muscle memory; moving the primary action causes misses and abandonment.

### Execution rules
- Place primary CTA where users expect it:
  - Often **bottom-right** of the relevant form section (desktop)
  - Sticky bottom CTA (mobile) when forms are long
- Keep placement consistent across steps in flows.
- Keep CTA near any critical reassuring microcopy it references.

## B3) Button Copy (microcopy that prevents errors)
### First principles
- Buttons are commitments. Users need to know whether they are *advancing*, *saving*, or *finalizing*.

### Execution rules
- Use verb + outcome:
  - “Continue to delivery”
  - “Save changes”
  - “Place order” (only when final)
- Avoid jargon and brand terms.
- If action is irreversible, say so (“Delete”, not “Confirm”).

## B4) Button States
### Execution rules
- States: default / hover / focus / pressed / disabled / loading.
- Disabled state must still be legible and explain how to enable (e.g., “Select a shipping method to continue”).
- Loading state:
  - Keep label stable; avoid layout shifts.
  - Prevent double-submit.

## B5) Destructive Actions
### Execution rules
- Use **clear destructive styling** distinct from primary.
- Require confirmation when irreversible or high-impact.
- Prefer “Undo” patterns for reversible destructive actions.

## B6) Button Groups and Multiple Actions
### Execution rules
- If multiple related actions:
  - Visually group them; ensure primary is dominant.
- Avoid “Reset” buttons.
- If a secondary action opens a side flow (edit address, apply promo), ensure it cannot be mistaken as primary.

## B7) Buttons QA Checklist
- One unmistakable primary per view.
- Primary CTA consistent across flow steps.
- Copy matches stage (continue vs finalize).
- No “equal-weight” clusters.
- Keyboard focus visible.
- Touch targets and spacing prevent mis-taps.

---

# C) NAVIGATION (menus, links, wayfinding)

## C1) Information Scent and Labeling
### First principles
- Navigation is prediction: labels should let users forecast what they’ll find.

### Execution rules
- Use **descriptive labels** (user language; avoid internal taxonomy).
- Avoid ambiguous buckets (“Solutions”, “Products”) unless submenus clarify immediately.
- Make current location visible:
  - Highlight active nav item
  - Use page title that matches nav label
- Provide a reliable escape hatch (Home, Search, Help).

## C2) Menu Design (desktop + mobile)
### First principles
- Navigation fails when it’s hard to access, hard to scan, or easy to trigger accidentally.

### Execution rules
- Prefer **click/tap-activated** menus over hover-only.
- Clearly indicate submenus with affordances (caret/arrow).
- Make menu targets large and well-spaced (especially on touch).
- For deep hierarchies:
  - Use mega menus or category landing pages rather than fragile multi-level cascades.
- For long pages:
  - Consider sticky nav when it improves access without stealing content space.

## C3) Utility Navigation (Search, Account, Cart, Help)
### Execution rules
- Keep utility actions in consistent locations.
- Search:
  - Prominent, predictable placement.
  - Supports misspellings and suggestions.
- Help:
  - Accessible without losing progress (drawer/modal).

## C4) Wayfinding Patterns
### Execution rules
- Breadcrumbs for deep hierarchies.
- Clear “back” paths that don’t reset state.
- Site map only if complexity warrants; keep it standard and easy to find.

## C5) Navigation in Task Flows (checkout / onboarding / payments)
### First principles
- In high-focus flows, full site navigation becomes a distraction and a data-loss risk.

### Execution rules
- Use an **enclosed flow**:
  - Remove dominant global nav and cross-sells.
  - Keep only flow-relevant links (support, policy, order summary).
- Avoid hover-activated nav that can overlay and obscure form content.
- Ensure any “leave flow” actions are intentional and confirm when data loss is possible.

## C6) Navigation Accessibility
### Execution rules
- Menus usable via keyboard (open/close, arrow through items).
- Focus doesn’t get trapped; escape closes menus/modals.
- Sufficient contrast; link styling recognizable.
- Avoid tiny link clusters; add spacing.

## C7) Navigation QA Checklist
- Labels predict destinations; no jargon buckets without clarification.
- Menus work on touch + keyboard (no hover dependency).
- Targets large enough; spacing prevents mis-click.
- Active location indicated.
- In task flows: nav minimized; no accidental overlays; no data loss on stray clicks.

---

# D) “Do Not Ship” List (high-frequency UX failures)
- Placeholders used as labels in multi-field forms.
- Required/optional ambiguity.
- Premature error messages while typing.
- Generic errors (“Invalid input”) with no fix instruction.
- Losing user-entered data after an error.
- Multiple “primary-looking” buttons competing for attention.
- Primary CTA moves position across a flow.
- Hover-activated navigation overlaying critical content.
- Full global navigation in a high-focus flow where users can accidentally exit.

---

# E) Minimum Instrumentation (to catch usability regressions)
- Form analytics:
  - Field error rate by field + error type
  - Abandon rate by step
  - Time-to-complete
- Button analytics:
  - Primary CTA click-through
  - Rage clicks / repeated taps
- Navigation analytics:
  - Menu open rate, submenu selection rate
  - On-site search usage + zero-results rate
- Session replay sampling for:
  - Mis-clicks, backtracking, repeated validation failures


# F) Contrast Ratio 
WCAG 2.0 level AA requires a contrast ratio of at least 4.5:1 for normal text and 3:1 for large text. WCAG 2.1 requires a contrast ratio of at least 3:1 for graphics and user interface components (such as form input borders). WCAG Level AAA requires a contrast ratio of at least 7:1 for normal text and 4.5:1 for large text.

Large text is defined as 14 point (typically 18.66px) and bold or larger, or 18 point (typically 24px) or larger.

Contrast Checker API and Bookmarklet
This tool also functions as a basic API. Simply append &api to any permalink to get a JSON object with the contrast ratio and the AA/AAA pass/fail states. For example: https://webaim.org/resources/contrastchecker/?fcolor=0000FF&bcolor=FFFFFF&api.

# G) Design UI elements

alert/banner/toast/snackbar/notification → feedback
modal/dialog/popover/sheet/drawer/lightbox → overlay
checkbox/radio/switch/dropdown/combobox/listbox → selection
table/datagrid/datatable → table
skeleton/spinner/loader/progressbar → loading
emptystate/blankstate → empty
topnav/sidebar/tabbar/breadcrumb/navrail/menu → navigation
textfield/textarea/numberfield/datepicker/filepicker → field
tag/chip/badge/pill/statusdot → tag
card/tile/listitem/row/slat → card
tooltip/helpertext/hint/inlinehelp → guidance
hover/active/disabled/error/loading/success → state
search/filter/sort/pagination → retrieval
drag/drop/reorder/resize → manipulation
theme/token/semanticcolor/typescale/spacing → token
component/variant/instance/slot → component
journey/taskflow/userflow/storymap → journey
metric/kpi/signal/telemetry/instrumentation → analytics
conversion/activation/retention/upsell → growth
cart/checkout/payment/refund/subscription → commerce

1. FOUNDATIONS
accessibility
affordance
alignment
architecture
clarity
consistency
constraint
content
context
contrast
density
focus
hierarchy
language
layout
legibility
motion
pattern
rhythm
semantics
spacing
structure
theme
typography
whitespace

2. COMPONENTS
accordion
alert
appbar
avatar
badge
banner
bottomsheet
breadcrumb
button
card
carousel
chart
checkbox
chip
datatable
datepicker
dialog
divider
drawer
dropdown
emptystate
field
filter
footer
header
icon
image
input
link
list
menu
modal
navigation
notification
panel
picker
popover
progress
radio
search
section
selector
sheet
sidebar
skeleton
slider
spinner
stepper
switch
table
tabbar
tag
textlink
tile
toast
toolbar
tooltip
upload
widget
wizard

3. INTERACTION
activation
automation
confirmation
default
disclosure
dismissal
dragging
editing
enablement
error
feedback
filtering
gesture
hover
inlineedit
loading
navigation
onboarding
pagination
personalization
preview
reorder
scroll
search
selection
sorting
submission
targeting
tracking
transition
validation

4. ACCESSIBILITY
alttext
announcement
caption
contrast
focus
hint
keyboard
label
landmark
legibility
readability
reducedmotion
region
semantics
separator
skiplink
subtitle
touchtarget
transparency
warning

5. RESEARCH
analytics
benchmark
bias
discovery
evidence
experiment
feedback
friction
goal
heatmap
heuristic
hypothesis
insight
interview
journey
metric
observation
opportunity
outcome
persona
prototype
query
research
scenario
scope
signal
survey
target
tradeoff
value

6. GROWTH
activation
audience
campaign
channel
conversion
crosssell
engagement
experiment
funnel
habit
impact
incentive
loop
onboarding
opportunity
personalization
ranking
recommendation
retention
reward
target
upsell
urgency
value

7. COMMERCE
addtocart
basket
bundling
buybox
catalog
cart
checkout
coupon
currency
delivery
discount
fulfillment
inventory
merchandising
offer
order
payment
pricing
promotion
receipt
refund
replacement
reorder
shipping
sku
stockout
subscription
tax
transaction
wishlist
