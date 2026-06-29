# Commerce Usability Rules (First Principles + Execution)
_Source spine: Baymard Checkout Usability for cart/checkout/form UX.  
_Note: Homepage/PLP/PDP guidance is generalized commerce UX (not the core focus of the Baymard checkout report), but aligned to the same first-principles logic.

---

## 0) North Star
### First-principles (why)
- People buy when **effort is low** and **certainty is high**.
- Every page must answer, fast: **What is this? Is it for me? What will it cost? What happens next?**
- Conversion is a system: upstream clarity reduces downstream form friction.

### Tactical (do)
- Establish 4 global invariants:
  - **Price truth**: no surprises; show totals early; show assumptions.
  - **Control**: users can edit without penalty (qty, variants, address, shipping, payment).
  - **Continuity**: state persists across steps, sessions, devices.
  - **Recovery**: errors are specific, local, and fixable.

---

## 1) Global UX Rules (sitewide)
### First-principles
- Reduce cognitive load via **hierarchy**, **predictability**, **recognition over recall**.
- Maintain trust via **consistency**, **transparency**, **reversibility**.
- Optimize for scanning; users don’t read, they **triage**.

### Tactical
- Layout
  - One primary task per view.
  - Clear H1 per page; align to user intent (Browse / Evaluate / Commit).
  - Consistent placement of navigation, search, cart, account.
- Performance
  - Fast first render; avoid layout shifts.
  - Defer non-critical scripts; lazy-load below-the-fold.
- Accessibility
  - Keyboard navigable; visible focus states.
  - Semantic headings; form labels bound to inputs.
  - Contrast meets WCAG; errors announced to screen readers.
- Content clarity
  - Avoid internal jargon; use user language.
  - Replace clever labels with explicit labels.
- Instrumentation (minimum viable analytics)
  - Pageview + key events (search, filter, add-to-cart, remove, checkout start, step completion, payment errors).
  - Track form error types, frequency, and abandon points.

---

## 2) Homepage & Category Navigation (Discovery)
### First-principles
- The homepage’s job is to route people to the **right aisle** with confidence.
- Category navigation must make the store model legible: “Where am I? What’s here? What’s next?”

### Tactical
- Global nav
  - Limit top-level categories; group by user mental model.
  - Use predictable patterns (mega-menu for breadth, left nav for depth).
- Trust blocks
  - Shipping/returns highlights in header or near primary CTAs (short, factual).
- Merchandising
  - Prioritize “best sellers / new / deals” entry points only if they help choice.
- Mobile
  - Sticky search and cart.
  - Thumb-reachable menu; avoid deep nested interactions.

---

## 3) Search, PLPs, and Filtering (Findability)
### First-principles
- Users want to “get to yes” with fewer comparisons.
- Filtering is a **decision tool**, not a feature list.

### Tactical
- Search
  - Typo tolerance; synonyms; “did you mean”.
  - Autocomplete with categories + products + recent searches.
  - Zero-results page with recovery paths (remove filters, broaden query, suggestions).
- PLP
  - Show what matters for decision: price, rating, key attribute, availability.
  - Keep filters persistent; show applied filters as removable chips.
  - Sort defaults to user intent (relevance) and provide price/rating/newness.
- Filtering
  - Make constraints obvious (count of results updates).
  - Avoid filter dead-ends; allow “clear all”.

---

## 4) PDPs (Evaluation → Add to Cart)
### First-principles
- PDP must close three gaps: **fit**, **risk**, **logistics**.
- Users need enough proof to commit without leaving the page.

### Tactical
- Core PDP content (above fold if possible)
  - Product name + price + primary value proposition.
  - Key options (size/color) with clear availability states.
  - Primary CTA: Add to Cart (and Buy Now only if safe).
- Proof & trust
  - Reviews summary with distribution; show recent reviews.
  - Returns policy summary; warranty if applicable.
  - Shipping ETA and costs (or estimator) near CTA if it impacts decision.
- Variant UX
  - Disable unavailable options; explain why.
  - Preserve selected variant in URL/state for shareability.
- Add-to-cart behavior
  - Confirm action immediately.
  - Present mini-cart with “Checkout” + “View cart” + ability to continue browsing.

---

## 5) Mini-Cart (Momentum)
### First-principles
- Mini-cart confirms progress and preserves browsing flow.
- Users must feel in control without context switching.

### Tactical
- Contents
  - Added item thumbnail, name, variant, price, qty.
  - Subtotal and item count.
- Controls
  - Qty adjust; remove.
  - Primary: Checkout.
  - Secondary: View cart.
- Guardrails
  - Don’t hide View Cart next to Checkout.
  - Avoid nudging users to skip cart review by misleading button labels (“Continue…”).

---

## 6) Cart (Commitment + Cost Truth)
### First-principles
- Cart is the decision checkpoint: “Is this correct, and what will it cost, all-in?”
- Lack of cost clarity creates abandonment before checkout begins.

### Tactical (Baymard-aligned)
- Order summary must include
  - Items subtotal.
  - Shipping cost or estimate (with basis).
  - Tax cost or estimate (with basis).
  - Discounts.
  - Full order total.
- Shipping transparency
  - If free shipping: show Shipping = $0 in the summary.
  - If free shipping tiers: show progress and update instantly when threshold reached.
- Editing
  - Qty, remove, save-for-later, change variant (where feasible).
  - Preserve cart state reliably across sessions.
- Comparison behavior support
  - Expect some users treat cart as a compare/hold area.
  - Keep item details scannable for comparison (variant, key attribute, returnability).

---

## 7) Checkout Architecture (Friction Minimization)
### First-principles
- Checkout is not persuasion; it’s execution.
- Every extra decision, field, or surprise increases drop-off.

### Tactical (Baymard-aligned)
- Account selection
  - Always allow guest checkout.
  - Make guest checkout the most prominent option.
  - Prefer delayed account creation after purchase confirmation.
- Step design
  - Keep steps predictable; show progress.
  - Consider persistent order summary on most steps.
- Cost and logistics
  - Keep shipping choices clear; show delivery dates where possible.
  - Don’t withhold total cost until late.

---

## 8) Checkout Forms (Field UX)
### First-principles
- Forms fail when users must guess what’s required or how to fix mistakes.
- Error recovery quality can be the difference between completion and abandonment.

### Tactical (Baymard-aligned)
- Required vs optional
  - Mark both required and optional fields explicitly.
  - Avoid “optional sections” as a single disclaimer; users miss them.
- Labels and microcopy
  - Keep labels visible at all times (don’t rely on placeholders).
  - Place labels above fields for scan speed and long label support.
  - Avoid jargon and internal brand terms in checkout instructions.
  - Optimize microcopy for skimming (short, specific).
- Optional inputs
  - Remove optional inputs unless they are truly necessary.
  - When needed for a minority, hide behind “Add …” links (reduce intimidation).
- Validation and errors
  - Use adaptive error messages that match the specific sub-issue.
  - Prefer inline validation after blur; don’t spam errors while typing.
  - Preserve user-entered data after errors (especially non-sensitive fields).
  - Check non-card fields first; reduce card re-entry risk.
- Payment specifics
  - Use live Luhn validation for credit card number typo reduction.
  - Consider asynchronous payment request patterns that avoid clearing inputs on unrelated errors.

---

## 9) Address, Shipping, and Delivery
### First-principles
- Address entry is high-error and high-abandon risk.
- Shipping is both a cost decision and a timing decision.

### Tactical
- Address UX
  - Accept common formatting; avoid over-restrictive masks.
  - Use address validation carefully; always allow override with clear consequences.
- Shipping method selection
  - Make options comparable (price + ETA + carrier where useful).
  - Default to the best “value” option if appropriate, but keep control obvious.
- Delivery instructions
  - Hide behind “Add delivery instructions” link unless most users need it.

---

## 10) Promotions, Coupons, and Gift Cards
### First-principles
- Promos can both increase conversion and derail it (coupon hunting, distrust).
- The best promo UX reduces anxiety without creating distraction.

### Tactical
- Promo entry
  - Collapsible “Add promo code” link to reduce visual noise.
  - Apply/remove easily; show impact in summary immediately.
- Pricing integrity
  - Keep discounts transparent; show line-item discount or summary discount consistently.

---

## 11) Trust, Risk, and Policy Communication
### First-principles
- Users fear being trapped: unclear returns, unclear support, unclear delivery.
- Trust is built through specifics, not slogans.

### Tactical
- Show concise policies near decision points
  - PDP: returns summary + warranty summary.
  - Cart/checkout: returns + shipping + support link.
- Support access
  - Provide help without losing progress (drawer/modal/inline).

---

## 12) Post-Purchase (Confirmation, Account, Retention)
### First-principles
- The order confirmation is the moment of maximum trust and openness.
- Ask for account creation only after value is delivered.

### Tactical
- Confirmation page
  - Clear order ID, items, total, delivery details, next steps.
  - Easy access to modify/cancel (if supported) and support.
- Delayed account creation
  - Offer “Create password” after purchase, tied to order email.
  - Explain benefits succinctly (tracking, faster checkout, returns).

---

## 13) Mobile-First Execution Rules
### First-principles
- Mobile punishes complexity; thumb + attention are limited resources.

### Tactical
- Sticky primary CTA (PDP, cart, checkout).
- Reduce field count; use correct keyboard types.
- Avoid multi-column forms; prefer single column.
- Preserve scroll position on updates; prevent reloads.

---

## 14) Measurement, QA, and “Definition of Done”
### First-principles
- If you can’t see friction, you can’t remove it.
- UX quality is an operational discipline.

### Tactical (checklists)
- Analytics events
  - Add-to-cart, view cart, begin checkout, step complete, payment attempt, payment failure reason, order complete.
  - Field error taxonomy (field name + error type + step).
- QA scenarios (minimum)
  - Guest checkout end-to-end.
  - Coupon applied/removed.
  - Free shipping threshold reached mid-cart.
  - Address validation edge cases and override.
  - Payment errors (invalid card, expired, AVS mismatch) with preserved non-sensitive data.
- KPI guardrails
  - Cart → checkout start rate.
  - Step-to-step drop-off.
  - Payment error rate by type.
  - Time-to-complete checkout.
  - Support contacts per 1k checkouts.

---

# General Usability UX Rules (Any Website / Any Form)

## A) Universal First Principles
- Make the system state visible.
- Prefer recognition over recall.
- Reduce choice overload by prioritizing and chunking.
- Preserve user control and reversibility.
- Prevent errors; when errors happen, make recovery obvious and fast.
- Communicate in the user’s language.
- Design for scanning; highlight what matters.

---

## B) Universal Execution Rules (Web + Forms)
### Information architecture
- Use clear navigation labels; avoid clever terms.
- Provide breadcrumbs or “you are here” cues for deep structures.
- Keep URLs meaningful where feasible.

### Content and readability
- One primary message per section.
- Use descriptive headings; front-load key words.
- Prefer short sentences; remove filler.
- Use bullets for lists; keep list items parallel.

### Forms (works everywhere)
- Labels
  - Always visible labels (don’t rely on placeholders).
  - Labels above fields for scanability and long labels.
  - Mark required and optional explicitly.
- Inputs
  - Minimize fields; justify every field.
  - Use appropriate input types and keyboards (email, tel, number).
  - Accept flexible formatting; don’t over-restrict user input.
- Validation
  - Validate early enough to prevent compounding errors.
  - Error messages must be specific to the sub-issue.
  - Place errors near the field; preserve user input.
- Flow
  - Show progress for multi-step forms.
  - Don’t reset data on error or refresh.
  - Provide save-and-resume for long processes when possible.

### Feedback and system status
- Confirm actions immediately (“Saved”, “Added”, “Updated”).
- Provide loading states; avoid silent failures.
- Make destructive actions reversible (undo) or confirm clearly.

### Accessibility (baseline)
- Keyboard support for all interactions.
- Proper focus management for modals/drawers.
- ARIA live regions for error summaries and status updates.

---

## C) Practical Templates (copy/paste)
### Error message pattern
- What happened: “Card number is too short.”
- How to fix: “Enter 16 digits.”
- If constrained: “Numbers only.”

### Optional-field pattern
- Inline: “Company (optional)”
- Expand: “+ Add company name” (reveals field)

### Cost estimate pattern
- “Estimated shipping (CA): $5”
- “Estimated tax (CA): $2.30”
- “Total (est.): $27.30”

---

## D) Final “Do Not Ship” List
- Hidden fees revealed late.
- Guest checkout missing or hard to find.
- Generic errors (“Invalid input”) without specifics.
- Required/optional ambiguity.
- Data loss on validation errors.
- Promo code UI that dominates the page.
- Checkout that forces account creation before completion.
