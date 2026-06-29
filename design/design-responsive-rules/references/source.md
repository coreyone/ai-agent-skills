# Responsive Web Design (2025) — Guidelines for Design + Design Engineering

**Key idea:** Design **mobile-first** for flow and constraints, then scale up with **layout breakpoints** and **component container queries**.  
**Goal:** Consistent UX, minimal breakpoint debt, fast implementation, fewer regressions.

---

## 0) Outcomes we care about (definition of “done”)
✅ Works at all target widths without horizontal scroll  
✅ Core tasks are easy to find and complete at every breakpoint  
✅ Tap targets meet minimum size + spacing  
✅ Images are responsive and don’t cause layout shift  
✅ Components adapt to their container (not just the viewport)  
✅ Desktop doesn’t feel like a “blown-up mobile page” (no content dispersion)

---

## 1) Principles (what to optimize for)
1. **Content-first**: layout serves hierarchy and tasks, not device models.
2. **Fewer breakpoints, better designs**: every breakpoint adds design/dev/test cost.
3. **Components are portable**: a card should work in 1-column, 2-column, sidebar, and grid.
4. **Progressive enhancement**: baseline experience is excellent on small screens.
5. **Readable by default**: control line length, spacing, and hierarchy at every size.
6. **Touch-friendly interactions**: avoid tiny targets; prioritize forgiving UI.
7. **Performance is UX**: responsive images, avoid over-fetching, keep layouts stable.

---

## 2) Breakpoint strategy (page layout)
### 2.1 Default breakpoint set (start here)
Use these **viewport tiers** for *page-level* layout changes:
- **Phone:** 0–639
- **Tablet:** 640–1023
- **Desktop:** 1024–1279
- **Wide:** 1280–1535
- **XL Wide:** 1536+

> Rule: Start with **Phone / Tablet / Desktop** only. Add Wide/XL only if you have a real layout need.

### 2.2 What is allowed to change at viewport breakpoints
Use viewport breakpoints for:
- **Navigation pattern** (tabs ⇢ collapsible ⇢ full nav)
- **Column count** and **sidebar behavior**
- **Density** (cards per row, table vs list)
- **Hero layout** (stacked ⇢ split)
- **Global spacing scale** (padding/margins bump)

Avoid using viewport breakpoints for:
- Small component tweaks (use **container queries** instead)
- Device-specific rules (no “iPhone 14” targets)

### 2.3 Breakpoints are chosen by “design breaks”
Add/adjust breakpoints when:
- Nav labels wrap or truncate in a harmful way
- Cards collapse into awkward aspect ratios
- Important content drops below the fold unnecessarily
- Interaction becomes error-prone (tiny taps, crowded controls)

---

## 3) Container query strategy (component behavior)
### 3.1 When to use container queries
Use container queries for:
- Cards/tiles that appear in grids of varying columns
- Modules used in both main content and sidebars
- Buttons/toolbars that sometimes compress (filters, sort, actions)
- Media blocks (image + text) that reflow based on space

### 3.2 Component “size classes” (container widths)
Define these container-driven states (names can vary, keep consistent):
- **Compact**: single-column, narrow container
- **Standard**: typical content column
- **Expanded**: wide container / multi-column area

Each component must specify:
- Layout (stack vs split)
- Visible metadata (what shows/hides)
- Typography scale (minor adjustments only)
- Action placement (inline vs overflow)

---

## 4) Layout rules (design system expectations)
### 4.1 Grid + spacing
- Use a **fluid grid**; avoid fixed widths for columns/cards.
- Use **consistent spacing tokens** (e.g., 4/8/12/16/24/32).
- Cap reading width for text-heavy pages:
  - **Ideal line length:** ~60–80 characters per line.
  - Use a **max content width** to prevent “content dispersion” on large screens.

### 4.2 Type
- Use fluid type where appropriate (e.g., `clamp()` on headings).
- Maintain clear hierarchy:
  - H1/H2/H3 scaling should not collapse on mobile.
- Avoid giant desktop type that causes excessive scroll.

### 4.3 Page structure
- Prefer **single primary column** on mobile; avoid competing side rails.
- On tablet/desktop, add rails only if they add real value:
  - related content, filters, summary, actions.

---

## 5) Navigation and discoverability
### 5.1 Mobile nav (execution rules)
- Don’t hide *everything* behind a menu by default.
- If using a hamburger:
  - Keep key actions visible (e.g., Search, Cart, Primary CTA).
  - Keep the menu label clear (“Menu” + icon) if space permits.
- For tablet and up, consider surfacing top-level categories or persistent nav.
