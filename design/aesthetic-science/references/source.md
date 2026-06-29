§ Foundations (human perception, cognition, ergonomics)
Rule: Treat interface design as signal-detection under noise → maximize discriminability, minimize false alarms (clear states, clear affordances).
Rule: Optimize for limited working memory → keep active choices per step low; externalize state via visible cues.
Rule: Prefer recognition over recall → show options, history, and defaults; don’t force memorization.
Rule: Use progressive disclosure → reveal complexity only when user intent is clear.
Rule: Maintain a stable “mental model” → consistent mapping between controls, labels, and outcomes.

§ Model Human Processor (MHP) baseline
Rule: Use the Human Processor Model (MHP) to evaluate usability by modeling how users perceive, think, remember, and act over time.
Rule: Treat perceptual, cognitive, and motor timings as hard design constraints when sizing interactions, pacing feedback, and sequencing tasks.
Rule: Respect capacity ceilings in visual, auditory, and working memory systems; when a flow approaches these limits, externalize state and reduce simultaneous demands.
Rule: Use decay half-life values to decide when information must remain visible, repeatable, or recoverable instead of assuming the user will remember it.
Rule: When designing dense interfaces, optimize for the lower end of the reported ranges rather than the mean to preserve usability under fatigue, stress, or divided attention.
Rule: MHP reference parameters:
Rule: Parameter | Mean | Range
Rule: Eye movement time | 230 ms | 70-700 ms
Rule: Decay half-life of visual image storage | 200 ms | 90-1000 ms
Rule: Visual capacity | 17 letters | 7-17 letters
Rule: Decay half-life of auditory storage | 1500 ms | 900-3500 ms
Rule: Auditory capacity | 5 letters | 4.4-6.2 letters
Rule: Perceptual processor cycle time | 100 ms | 50-200 ms
Rule: Cognitive processor cycle time | 70 ms | 25-170 ms
Rule: Motor processor cycle time | 70 ms | 30-100 ms
Rule: Effective working memory capacity | 7 chunks | 5-9 chunks
Rule: Pure working memory capacity | 3 chunks | 2.5-4.2 chunks
Rule: Decay half-life of working memory | 7 sec | 5-226 sec
Rule: Decay half-life of 1 chunk working memory | 73 sec | 73-226 sec
Rule: Decay half-life of 3 chunks working memory | 7 sec | 5-34 sec

§ Quantitative interaction laws (predictable performance)
Rule (Fitts): Target acquisition time grows with distance and shrinks with target size → MT = a + b·log2(D/W + 1).
Rule (Fitts): Make frequent targets bigger and closer to the pointer/finger (toolbars, sticky CTAs).
Rule (Fitts): Favor screen edges/corners for critical targets (effective W increases via boundary constraints).
Rule (Hick): Decision time grows with number of choices → T = a + b·log2(n + 1).
Rule (Hick): Reduce choice count; chunk options into labeled groups; use “top choices” defaults.
Rule (Steering): Path navigation time grows with path length/width → T ≈ a + b·(A/W) (menus, sliders, funnels).
Rule: Reduce pointing entropy → consistent placement lowers search/selection time via learned motor patterns.

§ Gestalt grouping (pattern perception)
Rule (Proximity): Elements closer together are perceived as a group; increase intra-group closeness vs inter-group spacing.
Rule (Similarity): Similar shape/color/size implies grouping; use similarity for categories, not decoration.
Rule (Common region): Put related elements inside a shared container/boundary to strengthen grouping.
Rule (Continuity): Align elements on clear axes; users follow smooth paths before they “jump.”
Rule (Figure–ground): Ensure foreground controls pop from background; avoid ambiguous layering.
Rule: Use grouping to replace labels where possible (structure does explanatory work).

§ Color science (mathematics-first)
Rule: Do color math in linear-light space (not gamma-compressed sRGB) when computing luminance or blending.
Rule: sRGB linearization: if c≤0.04045 then c_lin=c/12.92 else c_lin=((c+0.055)/1.055)^2.4.
Rule: Relative luminance (linear RGB): Y = 0.2126·R + 0.7152·G + 0.0722·B.
Rule: Use perceptually-uniform spaces (CIELAB/OKLab) for palette steps, gradients, and “equal” lightness.
Rule: Prefer OKLCH (L, C, h) for predictable gradients (constant L yields steadier perceived lightness).
Rule: Treat color difference as distance: ΔE*ab = sqrt((ΔL*)^2+(Δa*)^2+(Δb*)^2).
Rule: Use CIEDE2000 (ΔE00) when you need better perceptual agreement than ΔE*ab.
Rule: Build neutrals by controlling luminance steps first; add chroma only when meaning requires it.
Rule: Reserve high-chroma colors for semantics (status/intent), not background decoration.
Rule: Don’t encode meaning by hue alone; add redundant channels (icon, text, shape, position).

§ Contrast (legibility + accessibility, measurable)
Rule: Contrast ratio = (L1+0.05)/(L2+0.05), where L1 is lighter relative luminance and L2 is darker.
Rule: Body text contrast ≥ 4.5:1 against its background (typical minimum baseline).
Rule: Large text can use a lower contrast threshold (because stroke area increases).
Rule: Non-text UI components and focus indicators need sufficient contrast against adjacent colors.
Rule: Contrast must be evaluated for the actual rendered state (hover/pressed/disabled/focus).
Rule: If you add translucency/overlays, recompute final luminance/contrast post-composition.

§ Semantic color systems (error/warn/success/info)
Rule: Separate “semantic intent” from “brand hue” → map semantics to consistent tokens, then theme them.
Rule: Ensure semantic colors differ in luminance as well as hue (to survive grayscale/color-blind conditions).
Rule: Define a minimum ΔE (or minimum luminance step) between semantic states to prevent confusion.
Rule: Error states must be distinguishable from brand accents under low vision + low saturation.

§ Backgrounds, gradients, overlays, texture (signal-to-noise)
Rule: Background detail must stay below text’s spatial-frequency band → avoid fine patterns behind text.
Rule: Avoid moiré by preventing repetitive pattern frequencies near display sampling frequencies.
Rule: Use overlays to reduce background variance (lower RMS contrast) behind important text.
Rule: Gradients should be computed in perceptual spaces to reduce banding and “dirty” midtones.
Rule: Keep background luminance stable across a reading block; avoid hotspots behind text.

§ Typography (legibility: the physics of reading)
Rule: Legibility depends on visual angle; size text so x-height clears critical print size for your context.
Rule: For typical fluent reading, avoid sizes near acuity limits; keep body text comfortably above threshold.
Rule: Crowding is a core limit → increase letter spacing or reduce clutter around small text/icons.
Rule (Bouma/crowding): Critical spacing scales with eccentricity; don’t pack targets/text near focal periphery.
Rule: Use fonts with robust x-height, open counters, clear distinctions (I/l/1, O/0) for UI text.
Rule: Avoid ultra-light weights for body text; stroke contrast collapses on low-quality displays.
Rule: Use tabular numerals for tables/metrics to prevent jitter from proportional digits.
Rule: Use lining vs oldstyle numerals intentionally (UI metrics usually prefer lining for alignment).

§ Readability (paragraph-level, measurable)
Rule: Optimal line length is bounded; keep body text roughly in the 45–75 character range (per line).
Rule: Increase line-height as line length increases (more horizontal travel needs more vertical guidance).
Rule: Typical body line-height target: ~1.4–1.6× font size; tune by font metrics and line length.
Rule: Keep paragraph width consistent within a reading region; erratic measure increases regressions.
Rule: Avoid long all-caps passages; reduce word-shape cues and slow reading.
Rule: Use consistent heading hierarchy (H1–H6) → predictable scanning and information scent.
Rule: Apply clear typographic contrast (size/weight/spacing) to encode hierarchy, not random styling.

§ Type scales (math-driven hierarchy)
Rule: Use a modular scale (ratio-based) so sizes relate predictably (e.g., 1.125, 1.2, 1.25, 1.333).
Rule: Limit the number of sizes in a UI to reduce visual entropy; reuse tokens.
Rule: Tie scale steps to semantic roles (body, label, caption, title), not page-by-page improvisation.

§ Spacing & layout (geometry and rhythm)
Rule: Use a discrete spacing scale (e.g., multiples of 4 or 8) to reduce alignment error and increase consistency.
Rule: Establish a baseline grid for text so adjacent components align optically and rhythmically.
Rule: Use whitespace to signal grouping (distance encodes relationships more reliably than borders alone).
Rule: Align to a grid; break the grid only with explicit intent (focus, emphasis, or responsive necessity).
Rule: Balance dense and sparse regions; abrupt density changes create perceived “broken” sections.
Rule: Maintain consistent gutters and margins within a page type; inconsistencies look like bugs.

§ Balance, symmetry, emphasis (quantifiable composition)
Rule: Visual balance approximates a center-of-mass problem → heavier (larger/darker) elements pull attention.
Rule: Use symmetry for stability; use controlled asymmetry to create directional emphasis.
Rule: Emphasis = controlled contrast in one variable at a time (size OR color OR motion), not all at once.
Rule: Create a single strongest focal point per screen state; multiple equals reduces clarity.

§ Shape, borders, elevation (depth cues)
Rule: Keep border widths on a small set of tokens (1px/2px, etc.) to maintain consistent edge contrast.
Rule: Use radius scales (e.g., 0/4/8/16) so rounding signals component families, not arbitrary decoration.
Rule: Elevation should encode interaction/state (modal > popover > dropdown > tooltip) consistently.
Rule: Don’t rely on shadow alone; combine with occlusion, blur, and background dimming for clear layering.

§ Iconography (perceptual + geometric consistency)
Rule: Snap strokes to the pixel grid to prevent blur (especially for 1px strokes).
Rule: Maintain consistent stroke weight across the icon set; weight drift reads as “different system.”
Rule: Use a shared icon grid (e.g., 24×24) and consistent keyline shapes for family resemblance.
Rule: Pair icons with labels when stakes are high; pictograms are ambiguous across cultures and domains.
Rule: Ensure minimum distinguishability between icons (shape distance) at target size.

§ Data density & tables (information design)
Rule: Use alignment to reduce cognitive load (numbers right-aligned, decimals aligned, text left-aligned).
Rule: Use row striping sparingly; excessive banding lowers signal-to-noise.
Rule: Prefer direct labeling over legends when space allows; reduces lookup cost.
Rule: Use color as a last-mile cue; primary encoding should be position/length (more accurately perceived).

§ Interaction states (measurable clarity)
Rule: Every interactive element must have visible states: default/hover/active/focus/disabled/loading/error.
Rule: State changes should be detectable in at least two channels (e.g., color + shape/underline + icon).
Rule: Disabled must remain legible; reduce emphasis without destroying contrast.
Rule: Focus indicators must be unmissable; keyboard users navigate by focus visibility.

§ Touch targets (motor-control constraints)
Rule: Set minimum target size; smaller targets increase error rate and selection time (Fitts).
Rule: Ensure sufficient spacing between targets; errors rise sharply when targets are tightly packed.
Rule: Prefer large hit-areas even if the visible control is small (padding as invisible affordance).

§ Web Form Field Usability (interaction cost mathematics)
Rule: Label-to-field saccade time ≈ 50ms for top-aligned vs. ~500ms for left-aligned; minimize vertical/horizontal eye travel distance (D).
Rule: Affordance width (W) must approximate data length (L) ±10%; mismatch (W >> L or W << L) increases cognitive friction and uncertainty.
Rule (Hick’s decision time): Use exposed options (radios/chips) for N < 6 to minimize interaction steps (T_decision < T_click_dropdown); use dropdowns only for N ≥ 6.
Rule (Fitts’s acquisition): Clickable/tappable areas for checkboxes/radios must include the label text; effective target width (W) = control + label length.
Rule: Validation timing T_val must be > T_typing_interarrival (debounce ~600ms or onBlur); immediate errors during entry increase frustration (false positives).
Rule: Error recovery cost: Position error messages within foveal view (approx. 2° visual angle) of the error locus; do not hide errors in summaries alone.
Rule: Field grouping: Chunk related inputs into sets of 3–5 (working memory limit) using whitespace or fieldsets to reduce cognitive load calculation.
Rule: Mark optional fields explicitly (e.g., “(optional)”) rather than required asterisks (*); removing visual noise improves signal-to-noise ratio for required tasks.

§ Web Form Components (micro-interactions with measurable constraints) — Expanded

§ Responsive form layout (math-driven, device-driven)
Rule: Treat layout as an optimization under constraints → minimize errors + time given viewport (Vw,Vh), input modality, and density budget.
Rule: Define breakpoints by content-fit, not device names → choose bp where label+field+help no longer satisfy min readable widths.
Rule: Use character-based widths for fields → set min field width in ch: W_min_ch = ceil(μ_chars + k·σ_chars), k≈1–2 for 68–95% coverage.
Rule: Clamp field widths to avoid extremes → W = clamp(W_min, α·Vw, W_max); typical α ≈ 0.9 for single-column mobile forms.
Rule: Ensure minimum tappable hit areas on touch → target ≥ 44×44 px (or equivalent CSS px), including label hit region.
Rule: Ensure min inter-target gap on touch → gap ≥ 8–12 px to reduce accidental activation (especially near edges).
Rule: Convert “visual width” to “touch width” → W_touch = W_visual + 2·padding; set padding to meet target size.
Rule: One-column forms on small viewports → enforce label top-aligned when Vw < (label_col + field_col + gutters).
Rule: Two-column only when each column satisfies field minimums → 2col if (Vw - gutters) / 2 ≥ W_min_field.
Rule: Prevent line-length overload in help/error text → keep help/error measure in 35–65 chars; reflow to 1–2 lines max.
Rule: Avoid layout shift (CLS) from validation → reserve vertical space S_err for 1 line error; S_err ≈ lineHeight.
Rule: Sticky CTAs: place primary CTA in reachable zone on mobile → increase effective target frequency advantage (Fitts).
Rule: Keyboard-aware layout: when virtual keyboard opens, pin active field into view with margin M ≈ 16–24 px above keyboard.
Rule: Ensure focus ring visibility across backgrounds → focus indicator contrast must remain sufficient in all responsive themes/states.
Rule: Density modes as discrete tokens → compact/comfortable; avoid continuous resizing that breaks learned motor patterns.
Rule: Responsive spacing scale should be piecewise constant → keep spacing tokens stable across bps to reduce re-learning.
Rule: Use container queries when form lives in panels/modals → base rules on container width Cw not viewport Vw.

§ Data type handling inside inputs (interactive input taxonomy)
Rule: Every field declares a data contract → (type, domain, formatting, validation, serialization) explicitly.
Rule: Use specialized controls per data domain → reduce cognitive load and error recovery cost.

§ Text (freeform string)
Rule: Provide example formatting in help text, not placeholder; placeholder must not carry essential constraints.
Rule: Autocomplete hints: enable browser autofill when safe → set autocomplete tokens (name, email, tel, address-line1, etc.).
Rule: For multi-word names/addresses, do not over-validate → strict validation increases false negatives.

§ Email
Rule: Validate minimally at entry → “contains @ and domain-ish” locally; deep validation server-side.
Rule: Allow +aliases and uncommon TLDs; reject only impossible patterns to avoid false alarms.

§ Phone numbers
Rule: Use E.164 normalization internally → store as +<country><number>.
Rule: Collect country separately only if needed; otherwise infer by locale + allow override.
Rule: Keypad optimization: inputmode="tel" and allow spaces/dashes during entry; strip on serialize.

§ Numbers (integers/decimals)
Rule: Use numeric input mode not spinner UI → spinners increase interaction steps unless true stepper.
Rule: Define rounding/precision contract → (scale s, rounding mode) and show it near the field if non-obvious.
Rule: Prevent “format fights” → allow commas/spaces in entry; normalize to canonical numeric representation.
Rule: For bounded integers, show range constraints → min/max shown reduces trial-and-error loops.

§ Currency
Rule: Store as integer minor units when possible → cents to avoid floating error.
Rule: Display with locale formatting; accept both “1234.56” and “1,234.56”.
Rule: Put currency symbol outside the editable text when possible → reduces selection/edit friction.

§ Percent
Rule: Represent as fraction internally (0–1) or percent (0–100) but be consistent and explicit.
Rule: Show suffix “%” outside input; allow user to type with or without percent sign.

§ Dates and times
Rule: If date is near-term selection, use a calendar picker; if user knows the date, allow typed entry with flexible parsing.
Rule: Always show expected format (e.g., YYYY-MM-DD) and accept common local variants.
Rule: Store as ISO 8601; display localized.
Rule: For time zones: store UTC + tz; display local; make tz explicit for scheduling tasks.

§ Addresses
Rule: Prefer fewer fields where possible → combine street lines; do not force “state” for non-US.
Rule: Use address autocomplete cautiously; always allow manual override.
Rule: Validate postal codes by country when available; otherwise avoid strict validation.

§ IDs / codes (OTP, postal, coupon)
Rule: OTP: split boxes only if it measurably reduces error; always support paste.
Rule: Coupon codes: auto-uppercase is acceptable; do not block lowercase entry.

§ Long text (textarea)
Rule: Set min height to show 3–5 lines; auto-grow within a max to avoid scroll traps.
Rule: For structured long text, provide templates/examples; do not over-constrain.

§ Choice sets (categorical)
Rule: Expose choices when N small; collapse when N large; add search when N very large.
Rule: For N>20, searchable select reduces decision time more than scrolling lists.
Rule: For hierarchical categories, use typeahead + breadcrumbs rather than deep nested dropdowns.

§ Multi-select (tags)
Rule: Show selected items as removable chips; cap visible chips with “+N more” to prevent layout explosion.
Rule: Search should prioritize prefix matches; highlight matches to reduce scanning cost.

§ File uploads
Rule: Show accepted types + max size; errors must be near uploader.
Rule: Provide progress + ability to cancel; failure states must allow retry without losing prior form state.

§ Sliders / steppers (continuous values)
Rule: Use sliders only when approximate value acceptable; otherwise prefer numeric input + stepper.
Rule: If slider used, show current value label near thumb; allow keyboard entry for precision.

§ Toggles
Rule: Use toggles for immediate on/off state; use checkbox for “select to include” semantics.
Rule: Toggle labels must be state-descriptive (“Enable notifications”) and show current state.

§ Search inputs (typeahead)
Rule: Debounce search requests ~150–300ms; show loading state; keep results list stable to avoid flicker.
Rule: Always allow “no results” path and manual entry if applicable.

§ Formatting and parsing (input as language)
Rule: Separate “display format” from “storage format” → parse flexible, store canonical.
Rule: Parse should be permissive; validation should be precise; messaging should be actionable.
Rule: Normalization pipeline: raw → trimmed → locale parse → canonical serialize → validate domain constraints.
Rule: Never silently change meaning; if normalization changes value, show it (e.g., rounding).

§ Masking (when to constrain entry)
Rule: Input masks reduce errors for fixed formats but increase friction for paste/edit; prefer formatting-on-blur.
Rule: If masking, allow paste and backspace behaviors that match user expectations (no cursor traps).

§ Accessibility for typed data
Rule: Do not rely on placeholders for labels; associate labels via for/id or aria-labelledby.
Rule: Error state must be announced; ensure aria-describedby includes help+error.
Rule: For complex widgets (combobox), follow ARIA authoring practices and test with screen readers.

§ Keyboard and focus management (navigation costs)
Rule: Tab order equals visual order; violations increase cognitive remapping cost.
Rule: On submit with errors: focus first invalid field; provide summary for context but never summary-only.
Rule: Provide Enter/Return behavior consistent with user intent → Enter submits only when form is ready.
Rule: Use escape to close popovers/menus without losing typed input.

§ Interaction states (stable, redundant, measurable)
Rule: Every control defines states: default, hover, active, focus, disabled, loading, error, success.
Rule: State changes must be detectable via ≥2 channels → e.g., color + outline + icon + text.
Rule: Disabled must remain legible; do not drop contrast below readability thresholds.

§ Dropdowns, accordions, popovers (steering + occlusion)
Rule: Dropdown list max height should avoid full-screen occlusion; enable internal scroll with clear affordance.
Rule: Keep dropdown anchor stable; list appears aligned and predictable to reduce pointing entropy.
Rule: For nested menus, minimize path length A and maximize path width W (Steering Law) → avoid skinny hover tunnels.
Rule: Accordions must preserve state and error visibility; never hide errors inside collapsed panels.
Rule: Popovers must trap focus when modal-like; must return focus to trigger on close.

§ Data entry friction budget (quantitative model)
Rule: Total cost T_total approximates:
T_total = Σ_i (T_search(i) + T_decide(i) + T_point(i) + T_type(i) + T_wait(i) + T_recover(i))
Rule: Optimize by removing the largest term first; usually T_type and T_recover dominate conversion forms.

§ Field-level observability (instrumentation, numbers)
Rule: Track per-field metrics:
- t_focus_to_blur(i) (fill time)
- p_error(i) (validation fail)
- n_attempts(i) (retries)
- p_abandon_after(i) (drop hazard)
- p_backtrack(i) (navigation reversals)
Rule: Identify friction hotspots via hazard:
h(i) = p_abandon_after(i) / t_focus_to_blur(i)
Rule: Optimize fields with highest h(i) first.

§ Responsive measurement rules (type + spacing + control sizing)
Rule: Ensure minimum readable label size → choose font size so x-height clears legibility threshold for typical viewing distance.
Rule: Use line-height scaling with measure:
LH = baseLH + k·(charsPerLine - targetChars); k small; keep body ~1.4–1.6 baseline.
Rule: Use fluid type carefully: font-size = clamp(min, vw-based, max); ensure smallest size still meets legibility.
Rule: Maintain “tap target invariant” across density modes → when text shrinks, padding must not shrink below min target.
Rule: Ensure contrast invariants across themes/responsive → re-check actual composed colors (hover/focus/disabled).

§ Responsive patterns for complex data in inputs
Rule: On narrow screens, replace wide dropdowns/tables with full-screen pickers that preserve search + context.
Rule: For address/date pickers, prefer modal sheet patterns on mobile to increase target sizes and reduce occlusion.
Rule: For multi-column forms, collapse to single column and preserve field order priority (critical first).
Rule: Use inline summaries for collapsed sections (accordion headers show chosen values) to externalize memory.

§ Data-in-input display (mixed content)
Rule: If input must show rich data (icons, chips, units), keep editing caret behavior predictable.
Rule: Use affixes (prefix/suffix) outside the editable area when possible to avoid cursor confusion.
Rule: For unit-aware inputs, keep unit fixed and store value in canonical base units.

§ Safe defaults for component selection (numeric heuristics)
Rule: N ≤ 6 → radios/chips; 7–20 → dropdown; >20 → searchable select; >200 → typeahead with ranking + filters.
Rule: If user must compare attributes → cards/table view, not a dropdown.
Rule: If selection repeats frequently → show recents/favorites; default to last used when safe.

§ Layout anti-patterns (quantified failure modes)
Rule: Do not place labels far from fields; increasing D increases search time and errors.
Rule: Avoid tiny checkboxes; small W increases MT (Fitts) and increases misclicks.
Rule: Avoid over-validation; false alarms increase abandonment even when correctness increases marginally.
Rule: Avoid multi-step without progress; uncertainty increases drop hazard.

§ Done definition (for a form system)
Rule: A form component is not “done” until it ships with:
- states, keyboard, screen reader support
- responsive behavior
- instrumentation hooks
- error recovery path
- clear data contract (parse/serialize/validate)


§ Motion & animation (time perception + comfort)
Rule: Use animation only when it adds information: causality, continuity, hierarchy, or feedback.
Rule: Keep micro-interactions short; long animations read as latency.
Rule: For most UI transitions, keep durations in a narrow band; tune by distance moved and element size.
Rule: Use easing that matches physical expectations (fast-out, slow-in) to reduce perceived jerk.
Rule: Avoid large parallax/zoom on interaction; can trigger vestibular discomfort for some users.
Rule: Respect reduced-motion preferences; provide a non-animated equivalent for critical actions.
Rule: Never use motion as the sole indicator of state; it must be readable when motion is removed.

§ Response time (system performance as UX)
Rule: <100ms feels “instant” for direct manipulation; preserve the illusion of control.
Rule: ~1s is the upper bound for uninterrupted flow on common tasks; beyond that, show progress.
Rule: >10s requires strong feedback, chunking, or alternative paths; attention and context decay.

§ Pattern libraries (scalable consistency)
Rule: Components must define anatomy (parts/slots) so variants don’t fork into bespoke one-offs.
Rule: Variants should be orthogonal (size × intent × density) to prevent combinatorial explosion.
Rule: Tokens (color/type/spacing) must be the only source of truth; no hard-coded “special cases.”
Rule: Each pattern must state: problem, when to use, when not to use, edge cases, accessibility notes.

§ Accessibility constraints (hard requirements, not aesthetics)
Rule: Provide sufficient text contrast, component contrast, and focus visibility for low-vision users.
Rule: Don’t rely on color alone to convey meaning; add redundant encoding.
Rule: Provide keyboard access and visible focus for all interactive controls.
Rule: Ensure minimum interactive target size (with exceptions clearly justified by layout constraints).
Rule: Avoid interaction-triggered animation unless it can be disabled or reduced.
