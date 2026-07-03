# soapbox-cdp

CDP (Carbon Disclosure Project) Real Estate sector disclosure plugin — questionnaire
mapping, validation against CDP scoring levels, submission-ready export, and
year-over-year score tracking.

## Design

Skill-only plugin. CDP has no public submission API — responses go through CDP's portal —
so the deliverable is a validated, source-cited submission workbook plus copy-ready answer
blocks. The skill anchors to questionnaire *themes* (stable across CDP's periodic
restructures) and binds them to the current year's question refs at engagement start,
never from memory.

Feeds on other Soapbox plugins rather than duplicating them:

- **scope3-accounting** — Scope 1/2/3 inventory (PCAF Cat 13/15)
- **tcfd-reporting** — risk process and scenario analysis (CDP is TCFD-aligned)
- **bps-compliance** — quantified transition-risk penalty exposure
- **crrem** — targets and stranding analysis
- **audette** — transition plan / reduction initiatives evidence

## Install

- Soapbox: `soapbox install soapbox-cdp`
- Claude Code / opencode: add this repo as a plugin (skills in `skills/`)

## Contents

- `skills/cdp-disclosure/SKILL.md` — the workflow
- `skills/cdp-disclosure/references/data-map.md` — CDP theme → Soapbox data source map
