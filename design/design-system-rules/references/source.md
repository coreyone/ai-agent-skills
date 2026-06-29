# Design System Audit Checklist ✅
Purpose: Quickly assess what a design system includes, how mature it is, and how easy it is to adopt.

---

## 1) Principles & Philosophy
- [ ] Design principles (short, memorable, actionable)
- [ ] UX principles (clarity, speed, error prevention, etc.)
- [ ] Accessibility stance (WCAG target, keyboard-first, reduced motion, contrast)
- [ ] Consistency strategy (what must be consistent vs customizable)
- [ ] Product voice & tone principles
- [ ] Cohesive Aesthetic Point-of-View (Commitment to a bold conceptual direction)
- [ ] Distinctive Character (Avoidance of generic "AI slop" aesthetics)

---

## 2) Foundations (Tokens / Style)
### 2.1 Design Tokens
- [ ] Tokens exist (yes/no)
- [ ] Token categories:
  - [ ] Color (semantic + scale)
  - [ ] Typography (font families, sizes, weights, line heights; distinctive pairings)
  - [ ] Spacing (scale; asymmetric possibilities)
  - [ ] Radii
  - [ ] Elevation / shadow (multi-layered / dramatic)
  - [ ] Borders / strokes (custom/decorative)
  - [ ] Motion (duration, easing; staggered reveals, scroll-triggering)
  - [ ] Backgrounds (gradient meshes, noise textures, grain overlays)
  - [ ] Breakpoints / responsive
  - [ ] Z-index / layering
  - [ ] Opacity
  - [ ] Focus rings
- [ ] Token formats: (CSS vars / JSON / Sass / TS)
- [ ] Token naming system documented
- [ ] Light + Dark modes
- [ ] Theming model (multi-brand / tenant themes / per-app overrides)
- [ ] Token governance (how changes are proposed + approved)

### 2.2 Visual Language
- [ ] Color system guidance (semantic meaning, do/don’t)
- [ ] Typography rules (hierarchy, line length, spacing)
- [ ] Layout guidance (grid, rhythm, spacing rules)
- [ ] Iconography (set + usage rules)
- [ ] Illustration style (if applicable)
- [ ] Data visualization style (charts, colors, accessibility rules)
- [ ] Imagery / photography rules (if applicable)

---

## 3) Components Library
### 3.1 Coverage (Catalog)
- [ ] Foundations: Button, Link, Text, Icon, Spinner
- [ ] Form inputs: TextInput, TextArea, Select, Checkbox, Radio, Switch, Slider
- [ ] Form structure: Label, HelpText, ErrorText, Field, Form layout
- [ ] Feedback: Toast, Alert, Banner, Inline validation, Empty states
- [ ] Overlays: Modal, Drawer, Popover, Tooltip, Menu
- [ ] Navigation: Tabs, Breadcrumbs, Side nav, Top nav, Pagination
- [ ] Layout: Grid, Stack, Box,
