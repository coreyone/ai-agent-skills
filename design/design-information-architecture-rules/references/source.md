```md
# Information Architecture (IA) Rules — First Principles + Execution Playbook
North Star: Help users **find**, **understand**, and **act** with minimal effort and maximal confidence.

---

## 0) First Principles (the “laws”)
- **Structure beats polish**: a beautiful UI cannot fix a confusing model.
- **People scan, then decide**: optimize for *recognition*, not memory.
- **Every label is a promise**: if the destination doesn’t match expectation, trust drops.
- **Ambiguity is the real enemy**: reduce “information anxiety” by making sense-making easy.
- **Users bring mental maps**: align structure to how users think, not how org charts look.
- **Choices have costs**: reduce branching, chunk complexity, and show progressive disclosure.
- **Findability is a system**: navigation + search + metadata + content design must cohere.

---

## 1) What “Good IA” Delivers (success criteria)
### Outcomes
- Users can answer, quickly:
  - **Where am I?**
  - **What’s here?**
  - **What can I do next?**
  - **How do I get back?**
- Users succeed via **two paths**:
  - **Browse** (navigation / categories / hubs)
  - **Search** (query + facets + results)

### KPIs (minimum)
- Task success rate (find X; complete Y)
- Time to find (TTF)
- Backtrack rate (pogo-sticking)
- On-site search: zero-results rate, refinement rate, success-after-search
- Navigation drop-offs by level (L1 → L2 → L3)
- Content “dead-end” rate (pages with no onward path)

---

## 2) IA Deliverables (what to produce)
- **IA Brief**: goals, audiences, content scope, constraints, success metrics
- **Sitemap / Structure map** (visual)
- **Navigation model**: global + local + utility + contextual links
- **Labeling system**: controlled vocabulary + naming rules + examples
- **Taxonomy**: categories + facets + relationships
- **Metadata schema**: fields, types, rules, governance
- **Content model**: content types + attributes + reusable components
- **Search model**: indexing rules, ranking signals, synonyms, facets, zero-state behavior
- **Wayfinding spec**: breadcrumbs, “you are here”, crosslinks, hub pages, related content logic
- **Governance**: ownership, change process, review cadence, deprecation rules

---

## 3) IA Process (execution sequence you can run every time)
### Step 1 — Frame the problem
- Define top tasks (5–15) and top user intents.
- Identify constraints: CMS limits, legal, SEO, localization, analytics tooling.

### Step 2 — Inventory + audit (content reality check)
- Build a content inventory (at least: URL, title, type, owner, traffic, freshness, purpose).
- Tag each item:
  - Keep / merge / rewrite / retire
  - Primary audience + primary task supported
  - Required metadata gaps

### Step 3 — Model before you organize
- Define content types (e.g., Product, Category, Guide, Policy, Tool, Location, Profile).
- Define attributes per type (fields + allowed values + relationships).
- Identify reusable components (hero, summary, steps, specs, FAQs, related links).

### Step 4 — Design taxonomy + facets (browse + filter)
- Create:
  - **Hierarchies** (categories)
  - **Facets** (orthogonal filters)
  - **Relationships** (related, substitutes, prerequisites)

### Step 5 — Labeling + navigation
- Draft labels and test comprehension.
- Design navigation patterns (global/local/contextual) aligned to tasks.

### Step 6 — Search design (the second navigation)
- Define synonyms, stemming rules, typo tolerance, result templates, and facets.
- Design zero results recovery and “best bets” for common intents.

### Step 7 — Test structure and labels
- Run:
  - Tree testing (structure)
  - First-click testing (wayfinding)
  - Card sorts (when domain is unknown/contested)

### Step 8 — Ship + govern
- Instrument.
- Set governance rules (who can add categories, create new content types, change labels).
- Run quarterly IA hygiene: prune, merge, retire.

---

## 4) Classification Rules (taxonomy, facets, and the “library science” spine)
### First principles
- A taxonomy is a **meaning system**: it must support retrieval, not internal reporting.
- Users search by **multiple dimensions** → build **faceted classification**.

### Execution rules
#### 4.1 Categories (hierarchy)
- Keep depth reasonable:
  - Prefer **2–3 levels** for most sites; justify deeper levels with clear need.
- Ensure siblings are mutually distinct:
  - Avoid “Other”, “Misc”, “More”.
- Create categories based on:
  - User goals (jobs-to-be-done), not org structure.
- Avoid mixing classification bases at same level:
  - Don’t mix **audience** with **topic** with **format** in the same sibling set.

#### 4.2 Facets (filters)
- Use facets for orthogonal properties:
  - Price, size, topic, location, time, format, audience, difficulty, availability.
- Facet values must be:
  - **Consistent**, **complete**, **non-overlapping**, and **maintainable**.
- Prioritize facets by frequency and decision power.
- Provide “All” and “Clear” patterns; show selected facets as removable chips.

#### 4.3 Controlled vocabularies (labels + metadata values)
- Define:
  - Preferred term
  - Synonyms
  - Disallowed/legacy terms
  - Notes/examples
- Governance: someone owns the vocabulary and approves changes.

#### 4.4 Ranganathan-inspired utility checks (practical translation)
- **Save the user’s time**: reduce steps to find.
- **Every item its user**: ensure each content type has a discoverable path.
- **Every user their item**: support multiple entry paths (browse + search + related).
- **Library is a growing organism**: build for change; don’t hardcode brittle structures.

---

## 5) Labeling System (words that work)
### First principles
- Labels must be **predictive** and **testable**.
- Ambiguous labels create the highest navigation failure rates.

### Execution rules
- Use user language:
  - Gather from: support tickets, search logs, reviews, interviews.
- Make labels concrete:
  - Prefer “Pricing” over “Plans”; “Help Center” over “Support Solutions”.
- Keep parallel structure in sibling labels:
  - All nouns OR all verbs. Don’t mix.
- Avoid:
  - Clever brand terms, acronyms, internal team names.
- Write label specs:
  - Capitalization rules
  - Singular/plural rules
  - Length limits (nav truncation thresholds)
- Add “micro-definitions” only when needed:
  - Short explainer under category title to reduce ambiguity.

---

## 6) Navigation Architecture (global, local, utility, contextual)
### First principles
- Navigation is **wayfinding**: users need consistent signals to build a mental map.
- Multiple systems must coordinate:
  - Global nav (site-level)
  - Local nav (section-level)
  - Utility nav (account/search/help)
  - Contextual nav (related links within content)

### Execution rules
#### 6.1 Global navigation
- Reflect the primary top tasks and major content domains.
- Keep stable over time; changes are expensive (muscle memory + SEO).
- Use mega menus only when:
  - Many destinations must be visible at once
  - Labels remain scannable
- Ensure the global nav supports:
  - Browsing by domain
  - Quick access to search
  - Clear entry to help/support

#### 6.2 Local navigation
- Show within-section structure; keep it consistent across that section.
- Provide “overview/hub” pages as anchors.

#### 6.3 Utility navigation
- Always consistent placement for:
  - Search
  - Account
  - Cart / Saved
  - Help

#### 6.4 Contextual navigation (the “web of meaning”)
- Add links that reflect relationships:
  - Related topics, prerequisites, next steps, alternatives, popular paths.
- Standardize related-content logic per type:
  - Example: Guide → “Related Guides”, “Required Tools”, “Next Step”
- Ensure every page has a non-dead-end onward path.

---

## 7) Wayfinding & Mental Maps (make navigation “legible”)
### First principles
- Users form mental maps from repeated cues.
- A “legible” environment reduces anxiety and backtracking.

### Execution rules
- Always provide “You are here” cues:
  - Active nav state
  - Page title that matches nav label
  - Breadcrumbs for deep hierarchies
- Use hubs as landmarks:
  - Category landing pages that summarize and route to sub-areas.
- Provide edges and districts (practical patterns):
  - Clearly separated sections with distinct templates, headings, and nav.
- Avoid disorientation triggers:
  - Changing navigation patterns across pages without clear reason
  - Inconsistent naming across nav, headings, and links

---

## 8) Information Design (structure of pages, not just site)
### First principles
- Good pages compress complexity using **hierarchy**, **comparison**, and **context**.
- Visual structure should clarify relationships, not decorate.

### Execution rules
- Use “layered” information:
  - Summary first, details later (progressive disclosure).
- Use comparison tables sparingly and correctly:
  - Clear row/column labels
  - Consistent units and scales
  - Avoid chartjunk; show what changes decisions
- Use strong headings:
  - Headings should be meaningful out of context (scan-friendly).
- Provide context:
  - Dates, source, scope, last updated for content that ages.

---

## 9) Search Architecture (treat search as core IA, not a feature)
### First principles
- Search behavior reveals user intent; it’s also a primary navigation path.
- Good search reduces the need to perfectly predict taxonomy.

### Execution rules
- Index strategy:
  - Define which content types are searchable.
  - Normalize titles, summaries, keywords, and synonyms.
- Query handling:
  - Typo tolerance, stemming/lemmatization as needed
  - Synonym dictionary (from logs)
- Results design:
  - Different result templates per content type (title + type + key metadata)
  - Highlight matching terms
- Facets in results:
  - Offer the highest-value filters first
- Zero results:
  - Recovery paths: remove filters, broaden query, suggest alternatives, show popular content
- “Best bets”:
  - For high-frequency intents (pricing, returns, contact, tracking)

---

## 10) Content Modeling (how IA becomes buildable)
### First principles
- IA fails when it can’t be maintained in the CMS and understood by authors.

### Execution rules
- Define for each content type:
  - Purpose (why it exists)
  - Required fields (minimum)
  - Optional fields (rare)
  - Relationships (links to other types)
  - Templates (page structure)
- Build “content patterns”:
  - Example: Policy page pattern: summary → key rules → exceptions → FAQs → contact.
- Enforce metadata rules:
  - Required tags, categories, and audiences where needed.
- Make authoring foolproof:
  - Provide examples, validation, and defaults in the CMS UI.

---

## 11) Decision Limits (cognitive load controls)
### First principles
- Humans chunk information; too many choices increase decision time and error probability.

### Execution rules
- Navigation label count guidance:
  - Global nav: keep top-level small; test comprehension.
  - Mega menu: chunk into groups with clear headings.
- If you must have many options:
  - Use progressive disclosure (show top options, reveal more)
  - Use search within lists (typeahead)
  - Use facets to narrow sets

---

## 12) IA Testing (fast, cheap, decisive)
### Methods (when to use)
- **Tree testing**: validate structure + labels without UI.
- **Card sorting**:
  - Open sort for discovering mental models
  - Closed sort for validating a proposed taxonomy
- **First-click testing**: validate where users expect to find things.
- **Search log analysis**: build synonyms, identify missing categories, spot mislabeled areas.

### Execution rules
- Test with real tasks:
  - “Find the return policy for sale items”
  - “Find how to cancel a subscription”
  - “Find a beginner guide for X”
- Success criteria:
  - ≥70–80% tree-test success for critical tasks (adjust per domain complexity)
- Use results to:
  - Rename labels
  - Re-group categories
  - Add crosslinks and best bets

---

## 13) Governance (so IA doesn’t rot)
### First principles
- The site changes; IA must evolve without becoming a junk drawer.

### Execution rules
- Ownership:
  - Name a taxonomy owner and a content model owner.
- Change control:
  - Require a short “IA change request”:
    - Why change
    - Impacted pages/content types
    - Label implications
    - Migration plan
- Hygiene cadence:
  - Quarterly pruning: retire dead content, merge duplicates, fix orphaned pages.
- Deprecation policy:
  - Redirect rules
  - URL strategy
  - Sunsetting metadata values

---

## 14) IA Ship Checklist (definition of done)
- ✅ Top tasks mapped to clear entry points (browse + search)
- ✅ Sitemap reflects user mental models, not org structure
- ✅ Labels tested (tree test + first click) and consistent with headings
- ✅ Taxonomy + facets are maintainable (governed vocab, no overlaps)
- ✅ Metadata schema implemented in CMS with validation
- ✅ Every page has: purpose, audience, next-step links (no dead ends)
- ✅ Search supports: synonyms, typo tolerance, facets, and zero-results recovery
- ✅ Analytics in place to detect findability failures

---

## 15) “Do Not Ship” List (classic IA anti-patterns)
- “Misc / Other / More” as a real category
- Mixing classification bases at the same level (topic + audience + format siblings)
- Labels that require insider knowledge (“Solutions”, “Platform”, “Ecosystem”)
- Deep hierarchies built to mirror org charts
- No hub pages / no landmarks; users fall into page-to-page tunnels
- Search without synonyms or zero-results recovery
- Taxonomy with no governance; tags become a junk drawer
- Content types without models; authors improvise structures inconsistently
```
