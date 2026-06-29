# Forms + Wizards - Checkout Rules (First Principles + Execution)
_Source spine: Nielsen Norman Group + Baymard Institute checkout and form usability research._
_Note: Single-page and multi-step checkout can both perform well. Quality of execution drives outcomes, not step count alone._

---

## 0) North Star
### First-principles (why)
- Small UX improvements compound into large growth effects:
  - fewer drop-offs
  - higher conversion
  - faster task completion
  - better user confidence
  - fewer support issues
- People complete checkout when effort is low and certainty is high.

### Tactical (do)
- Optimize this system equation:
  - Completion Rate = Momentum + Clarity + Error Prevention + Visible Progress + Trust - Cognitive Load - Uncertainty - Effort
- Keep four global invariants in every flow:
  - Price truth
  - User control
  - Continuity of state
  - Error recovery

---

## 1) Why These Rules Work (Science)
### First-principles
- Cognitive Load Theory: people can actively process about 4 chunks at once. Large visible forms overload working memory.
- Hick's Law: more visible options increase decision time.
- Goal Gradient Effect: motivation rises as users perceive progress toward completion.

### Tactical
- Chunk inputs into short groups with clear boundaries.
- Reduce visible choices at each moment.
- Show progress indicators, completion states, and clear next actions.

---

## 2) Checkout Architecture (Single vs Multi-Step)
### First-principles
- Architecture choice is secondary to clarity and predictability.
- Users need to know where they are, what is left, and what happens next.

### Tactical
- Use single-page checkout when complexity is low and validation can stay local.
- Use multi-step checkout when grouping reduces overload and enables stronger error containment.
- In both models:
  - keep one primary action per view
  - preserve entered data
  - avoid hidden cost surprises late in the flow

---

## 3) Information Chunking and Field Scope
### First-principles
- Ask only for information required to fulfill the order.
- Large field sets feel harder even when actual completion time is similar.

### Tactical
- Group by user mental model:
  - Contact
  - Shipping
  - Billing
  - Payment
  - Review and Confirm
- Remove non-essential fields.
- Hide minority-use fields behind "Add ..." patterns.

---

## 4) Decision Reduction and Action Clarity
### First-principles
- Every extra decision creates hesitation.
- Recognition is faster than recall.

### Tactical
- Provide intelligent defaults where risk is low.
- Use explicit outcome labels for CTA text (example: "Continue to Payment" not "Next").
- Keep secondary actions visually quieter than the primary action.
- Use familiar controls and common field conventions.

---

## 5) Input Speed and Friction Reduction
### First-principles
- Typing is costly and error-prone, especially on mobile.
- Time-to-complete decreases when systems reduce manual entry.

### Tactical
- Enable address autocomplete and browser autofill.
- Use correct mobile keyboards by field type.
- Apply formatting assistance for structured inputs where it helps correction.
- Prefill known values only when accuracy and consent are clear.

---

## 6) Validation, Errors, and Recovery
### First-principles
- Users abandon when they cannot understand or recover from errors quickly.
- Recovery quality is a conversion lever.

### Tactical
- Validate inline after blur and at submit.
- Place error copy next to the field with exact fix guidance.
- Never clear completed non-sensitive fields on error.
- Support easy edits without restarting the flow.
- Prevent irreversible mistakes with confirmation or undo where possible.

---

## 7) Progress, Momentum, and Motivation
### First-principles
- Visible progress increases motivation and completion.
- Transitions and interruptions break momentum.

### Tactical
- Show clear step indicators or completion milestones.
- Keep page transitions minimal and purposeful.
- Save progress automatically and support resume behavior.
- Maintain linear navigation unless branching is required by user intent.

---

## 8) Trust, Certainty, and Commitment Moments
### First-principles
- Checkout failure often comes from uncertainty, not inability.
- Users need reassurance near high-commitment actions.

### Tactical
- Keep order summary visible while entering critical details.
- Reveal shipping, taxes, discounts, and total early.
- Avoid forced account creation.
- Show concise policy clarity near commitment points:
  - returns
  - privacy and security
  - support access

---

## 9) Performance and Visual Stability
### First-principles
- Slow or unstable interfaces increase perceived complexity.
- Layout shifts break attention and trust.

### Tactical
- Reduce load time and script overhead in checkout steps.
- Prevent layout shifts around fields, errors, and totals.
- Keep action placement stable across states.

---

## 10) Responsive and Mobile Execution
### First-principles
- Mobile constraints amplify friction from poor form design.
- Touch ergonomics and readability directly affect completion.

### Tactical
- Prefer one-column forms on small screens.
- Keep tap targets at least 44x44.
- Ensure sticky or consistently reachable primary action in long forms.
- Preserve scroll position and context after validation.

---

## 11) Accessibility Requirements
### First-principles
- Accessible checkout reduces failure for all users, not only assistive-tech users.
- Ambiguous labels and hidden state create avoidable errors.

### Tactical
- Use persistent labels (not placeholder-only labels).
- Ensure clear focus states and keyboard navigability.
- Announce errors programmatically and keep messages actionable.
- Meet WCAG contrast and readable type standards.

---

## 12) Measurement and Iteration Loop
### First-principles
- Checkout optimization is continuous, not one-time.
- Small high-frequency issues create large aggregate loss.

### Tactical
- Instrument step funnel and field-level error events.
- Track:
  - step abandonment rate
  - error frequency by field
  - time per step
  - retry loops
  - support-contact themes
- Prioritize fixes by impact on certainty and effort, then re-measure.

---

## 13) Do Not Ship List
- Forced account creation before purchase.
- Hidden mandatory fields or ambiguous required/optional status.
- Generic error messages without recovery instructions.
- Data loss after validation or payment errors.
- Late surprise costs at final confirmation.
- Broken keyboard flow or inaccessible focus order.
- CTA labels that do not communicate outcome.
