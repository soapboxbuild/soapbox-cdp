---
name: cdp-disclosure
version: 0.1.0
description: >
  CDP (Carbon Disclosure Project) disclosure for real estate — guide completion of the CDP
  corporate questionnaire with the real estate sector lens, map portfolio data (energy,
  Scope 1/2/3 emissions, water, targets, governance) to questionnaire modules, validate
  completeness against CDP scoring levels (Disclosure → Awareness → Management →
  Leadership), export submission-ready responses, and track year-over-year scores.
  Triggers on: "CDP", "Carbon Disclosure Project", "CDP questionnaire", "CDP submission",
  "CDP score", "CDP real estate", "climate disclosure to investors", "CDP deadline".
---

# CDP Real Estate Disclosure

Help an institutional real estate owner complete and improve their CDP response using
data already in the Soapbox platform.

## Version discipline — read first

CDP restructures its questionnaire periodically (the 2024 reform merged climate, water,
and forests into one integrated corporate questionnaire with numbered modules and
sector-specific questions). **Do not rely on memorized question IDs.** At the start of
any engagement:

1. Ask which reporting year and questionnaire track applies (full corporate vs SME).
2. Fetch the current year's questionnaire structure and real-estate sector questions —
   from the user's CDP portal export if available, else web-search CDP's published
   questionnaire and scoring methodology for that year, and cite what you used.
3. Anchor all mapping to the *themes* in `references/data-map.md`, then bind them to the
   current year's actual question numbers.

## Workflow

### 1. Scope the response

- Reporting boundary: which entities/funds/portfolios; operational vs equity control
  (align with the boundary used in GHG accounting — cross-check the `scope3-accounting`
  skill's output if present).
- Prior submissions: last year's response and score if available (baseline for YoY).
- Deadline and track (investor-requested vs voluntary; full vs SME).

### 2. Map platform data to questionnaire themes

Work through `references/data-map.md` theme by theme. For each theme record:
`{ theme, current-year question refs, answer draft, data source, confidence, gaps }`.
Key mappings:

- **Emissions inventory** → scope3-accounting skill (Scope 1/2/3, PCAF Category 13/15)
- **Energy** → ESPM / Arcadia / utility data; portfolio EUI and fuel mix
- **Targets & transition plan** → CRREM pathway alignment, committed decarb plans
  (Audette roadmaps), interim targets
- **Risks & opportunities** → physical risk MCPs + TCFD/ISSB work (CDP is TCFD-aligned;
  reuse the tcfd-reporting skill's scenario analysis if present)
- **Governance, strategy, engagement** → user-provided; draft from org documents on file
- **Water/waste (real estate sector)** → utility data where metered; else flag as gap

### 3. Validate against scoring levels

For each answered theme, assess which CDP scoring level the draft supports:
**Disclosure** (question answered) → **Awareness** (impacts assessed) → **Management**
(actions, targets, governance in place) → **Leadership** (best practice: verified data,
science-based targets, value-chain engagement). Produce a gap table: what one concrete
addition moves each theme up a level. Flag hard blockers for high scores (e.g. third-party
verification of emissions data is required for top bands — Soapbox's verifier findings
ledger is supporting evidence, not a substitute for external assurance).

### 4. Export

CDP submissions go through CDP's own portal — there is no public write API. Export as:

- A **submission workbook**: one row per question — question ref, drafted answer,
  source citation, confidence, reviewer sign-off column (XLSX via mila/report tooling,
  or markdown table).
- Copy-paste-ready answer blocks per module, respecting CDP's character limits where the
  current questionnaire specifies them.

### 5. Year-over-year tracking

Store (in the portfolio memory / asset files): reporting year, submitted answers export,
score received, and the gap table. On the next cycle, diff against it and lead with
"what changed since last year" — CDP scoring rewards trajectory and consistency.

## Rules

- Never invent question IDs, character limits, or scoring weights — bind to the current
  year's published questionnaire and cite it.
- Every quantitative answer carries source + method (same discipline as GRESB/TCFD skills).
- Emissions numbers must reconcile with the scope3-accounting output — if they diverge,
  stop and resolve before drafting.
- Recommend external verification early if the user targets Management/Leadership bands.
