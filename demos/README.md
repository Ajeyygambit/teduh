# Runnable prototypes — TEDUH

Two single-file demos, extracted verbatim from the specification documents in `../docs/`.

| File | Runtime | Open it |
|---|---|---|
| `teduh-workflow-film.html` | 58 s auto-play, Three.js r128 (cdnjs) | double-click |
| `teduh-verification-simulator.html` | live calculation, zero CDN | double-click |

Both are self-contained: no build step, no server, no package install.

## `teduh-workflow-film.html`

Widescreen letterboxed film, no interactive UI — it plays 00:00 → 00:58 and loops. Seven transitions: design intent → baseline measurement → expectation vs. reality → gap prioritisation → physical intervention → re-measurement → the Comfort & Shade Ledger. Spatial callouts are anchored in 3D and carry provenance badges (`PROXY`, `MODELLED`, `MEASURED`, `PENDING`).

The ledger sheet in the final scene is stamped **ILLUSTRATIVE / SIMULATED ARTEFACT — NOT FIELD DATA**, deliberately.

## `teduh-verification-simulator.html`

The audit instrument. Six precinct segments, each with a design-proxy claim and a ground-truth check:

- **Ledger** — proxy score vs. measured score, gap, and a two-sided `PROXY_UNRELIABLE` flag at |gap| > 15.
- **WBGT field simulator** — drag dry-bulb, relative humidity and black-globe temperature; the page recomputes wet-bulb (Stull 2011) and outdoor WBGT (ISO 7243) live.
- **Diurnal thermal-exile clock** — 07:00–21:00 in one-hour cells, usable or in exile against the threshold.
- **Monte Carlo** — 10,000 deterministic seeded draws, reported as p10/p50/p90. Never a single point estimate.
- **Stakeholder views** — resident, developer, local authority (PBT), contractor worklist, and the open questions that only field work can answer.

The walkability threshold (default 28.0 °C WBGT) is a slider, because it is an assumption — and it is labelled as one.

## Note on figures

Header numbers in the HTML are illustrative placeholders. Every KPI is recomputed from the segment dataset on load, so quote the live values, not the static ones.
