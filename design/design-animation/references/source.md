---
description: motion guidelines for modern UI animation (NN/g usability + O’Reilly tactical patterns) tuned for SvelteKit + Motion + OSS-first stacks
---

## ▣ Key takeaway
Animations feel “right” when they improve **comprehension** and **control** while staying **fast**, **subtle**, and **consistent**.

## ▸ What “right” means (practical definition)
- Users always know **what changed**, **why it changed**, and **what to do next**.
- Motion never blocks the task.
- Motion never surprises, distracts, or slows the interface.

---

## 0) ▦ Default workflow for this stack (Static Maximalist → Enhanced Motion)
1. **Ship the static HTML page first** (layout, hierarchy, states, copy, empty/loading/error).
2. Add **CSS transitions** for common state changes (hover, focus, pressed, expand/collapse).
3. Add **Mount/unmount transitions** for component presence (menus, dialogs, toasts).
4. Use **Motion (motion.dev)** only for:
   - choreography (sequencing, stagger, shared transitions),
   - gestures/drag,
   - layout transitions (FLIP-like behaviors),
   - complex interactive demos.
5. If Motion is removed, the UI must still work (progressive enhancement mindset).

---

## 1) ◈ NN/g intent rules (motion must be functional)
Animation is allowed only when it serves one of these purposes:
- **Feedback**: confirms an action happened (press, toggle, save).
- **State change**: clarifies before/after (filters applied, error shown).
- **Orientation**: preserves spatial/mental model (where did the panel come from?).
- **Attention**: directs focus to the right element at the right moment.
- **Continuity**: reduces “teleporting” by showing relationships.

If you can’t name the purpose in one sentence, remove the animation.

---

## ◈ High-Impact & Orchestrated Motion
* **One Great Moment**: Prioritize one well-orchestrated page load over scattered micro-interactions.
* **Staggered Reveals**: Use `animation-delay` to create depth and rhythm during entry.
* **Scroll-Triggered Narrative**: Use motion to reveal content as the user explores, creating a sense of discovery.
* **Surprise & Delight**: Design hover and active states that surprise the user—unexpected transitions or unique spatial shifts.

---

## 2) ⧈ Apply NN/g heuristics directly to motion (10 checks)
- **Visibility of system status**: show progress with motion (but keep it brief and non-looping unless loading).
- **Match to the real world**: motion should reflect “physical” expectations (fast start, gentle stop for arrivals).
- **User control & freedom**: users can interrupt/escape (close dialog mid-animation; no locked UI).
- **Consistency & standards**: reuse the same durations/easings across the product (tokens, not one-offs).
- **Error prevention**: don’t animate into destructive states accidentally (avoid “slide-to-delete” surprises).
- **Recognition over recall**: animate reveals to show where options came from (menus anchored to triggers).
- **Flexibility & efficiency**: motion supports power users (no slow flourishes on repeated tasks).
- **Aesthetic & minimalist**: motion is subtle; the content is the hero.
- **Help users recover**: errors animate in near the cause; successes resolve clearly.
- **Help & documentation**: if motion teaches a gesture, provide an alternate control (button + hint).

---

## 3) ⏱️ Timing standards (durations you can reuse)
### ▸ Global rule
Use a small, consistent duration palette. Avoid custom durations per component.

### ▸ Duration tiers (pick one)
- **micro** (hover/press/focus): 80–140ms
- **ui** (toggle/chip/icon/inline feedback): 120–200ms
- **panel** (dropdown/popover/accordion): 160–260ms
- **modal** (dialog/sheet): 220–360ms
- **navigation** (route/section): 300–600ms (only when it clarifies orientation)

### ▸ Distance ↔ duration coupling
- Small distance → shorter duration.
- Large distance → longer duration, but avoid sluggishness.
- If users can complete the task faster than the animation finishes, the animation is too long.

---

## 4) ∿ Easing standards (taste, but systemized)
### ▸ Easing should reflect intent
- **Enter / arrival**: fast start, soft landing (ease-out).
- **Exit / dismissal**: quick commitment (ease-in).
- **Attention nudge**: quick, tiny, and done (short ease-out).
- **Continuous / scrubbed** (scroll/drag): linear or near-linear.

### ▸ Easing palette (keep it small)
Define 2–3 easings and reuse them everywhere.
- `ease.standard` (general UI)
- `ease.emphasized` (rare, for hero moments)
- `ease.exit` (dismissals)

Avoid mixing 7 different easings across a UI. Consistency is the “feels right” multiplier.

---

## 5) ⚙︎ Motion tokens (single source of truth)
### ▸ CSS custom props (works with Vanilla CSS + Tailwind + Svelte)
:root {
  --motion-duration-micro: 120ms;
  --motion-duration-ui: 200ms;
  --motion-duration-modal: 320ms;

  --motion-ease-standard: cubic-bezier(0.2, 0.0, 0.0, 1.0);
  --motion-ease-exit: cubic-bezier(0.4, 0.0, 1.0, 1.0);

  --motion-distance-1: 4px;
  --motion-distance-2: 8px;
  --motion-distance-3: 16px;
}

### ▸ “One-liners” you can standardize
- hover/focus: transition: transform var(--motion-duration-micro) var(--motion-ease-standard), opacity var(--motion-duration-micro) var(--motion-ease-standard);
- enter panels:  transition: transform var(--motion-duration-ui) var(--motion-ease-standard), opacity var(--motion-duration-ui) var(--motion-ease-standard);
- exit panels:   transition: transform var(--motion-duration-ui) var(--motion-ease-exit), opacity var(--motion-duration-ui) var(--motion-ease-exit);

### ▸ Tailwind note
- Prefer Tailwind’s utilities for layout/typography.
- Prefer CSS variables for motion tokens so Motion + CSS + Svelte share the same values.

---

## 6) ⚡ Performance rules (what to animate, what not to animate)
### ▸ Animate “cheap” properties
- **transform** (translate/scale/rotate)
- **opacity**

### ▸ Avoid layout thrash (unless unavoidable)
Avoid animating: width, height, top, left, margin, padding, box-shadow on large areas.

### ▸ Use FLIP for reorders and layout transitions
- Measure first/last positions.
- Invert with transform.
- Play the transform back to 0.

### ▸ “Will-change” is a scalpel, not a lifestyle
- Apply it shortly before animation.
- Remove it afterward.
- Don’t blanket `will-change: transform` across a whole app.

---

## 7) ⊹ Practical patterns (O’Reilly-style reusable recipes)
### A) Button press (feedback)
Goal: instant confirmation without waiting for network.
- duration: micro
- properties: transform (scale 0.98–0.995), opacity (optional)
- rule: never delay the pressed state; ensure the release feels snappy and distinctive.

### B) Dropdown / popover (orientation)
Goal: show it is anchored to a trigger.
- origin: align to trigger (top-left/right depending on placement)
- enter: small translateY + fade
- exit: quicker than enter
- keep distance small (≤16px)

### C) Accordion / disclosure (comprehension)
Goal: reveal content without layout jank.
- prefer transform-based techniques when possible
- if animating height, keep it short and avoid heavy shadows

### D) Toast / inline success (status)
Goal: confirm, then get out of the way.
- enter: 160–220ms
- exit: 120–180ms
- auto-dismiss with pause-on-hover and clear close affordance

### E) Loading (status without anxiety)
Goal: show work is happening without “fake progress.”
- immediate: show skeleton or spinner quickly
- avoid long, decorative loops
- if load completes quickly, avoid flashing loaders (debounce show/hide)

### F) Route transitions (orientation, used sparingly)
Goal: preserve context between pages.
- only animate when it clarifies hierarchy (list → detail, tab switch)
- keep it subtle (fade + small translate)
- never slow down repeated navigation tasks

---

## 8) ♿ Reduced motion (must be first-class)
### ▸ Baseline policy
If `prefers-reduced-motion: reduce`:
- remove large transforms and parallax
- replace springs with simple fades
- keep essential feedback (state change) but minimize motion distance

### ▸ Implementation pattern
- Central toggle: `data-motion="off"` on <html> for debugging and QA parity with reduce-motion users.
- Provide motion fallbacks for:
  - dialogs,
  - route transitions,
  - gesture-driven UI.

---

## 9) ⟡ Motion + SvelteKit + Motion.dev (division of labor)
### ▸ Choose the simplest tool that fits
- **CSS transitions**: hover/press/focus, small state changes.
- **Svelte transitions**: mount/unmount, presence changes.
- **Motion**: gesture + layout transitions + orchestrated sequences.

### ▸ Keep orchestration explicit
- Define variants / states (idle → hover → pressed → loading → success).
- Keep state charts small.
- Prefer declarative timelines over scattered imperative calls.

---

## 10) ▤ Testing & QA gates (modern, practical)
### ▸ “Feels right” review (fast checklist)
- Purpose is explicit (feedback, orientation, status, attention).
- Duration matches distance.
- Easing matches intent (enter vs exit).
- Animation never blocks input.
- Interruptions behave (escape closes, click-away cancels).
- Works with reduced motion.

### ▸ Automated checks (Playwright)
- Run tests with reduced motion enabled.
- Assert critical UI is visible and interactive without waiting for animations.
- Assert no layout shift explosions during transitions (especially on slow devices).

### ▸ Instrumentation (PostHog / Plausible / Umami)
Track regressions motion can cause:
- rage clicks (repeated taps while UI is “busy”)
- time-to-interactive
- drop-off at multi-step flows where transitions exist

---

## 11) ⛔ Do-not-ship list (high-frequency failures)
- Purpose unclear (“because it looks cool”).
- 400ms+ on common repeated interactions.
- Multiple unique easings across the UI.
- Animating layout-heavy properties on large containers.
- Motion that steals focus or moves controls away from the cursor.
- No reduced-motion support.
- Spinners that loop forever without clear next state.

---

## 12) ▣ Copy-paste starter presets (edit once, reuse everywhere)
motion.duration = { micro: 120, ui: 200, modal: 320 }
motion.ease = { standard: [0.2, 0.0, 0.0, 1.0], exit: [0.4, 0.0, 1.0, 1.0] }
motion.distance = { 1: 4, 2: 8, 3: 16 }

Rule: ship tokens first. Then tune per component only when you can prove a usability reason.
