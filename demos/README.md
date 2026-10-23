# Runnable prototypes — TEDUH

Three single-file prototypes, extracted verbatim from the specification documents in `../docs/`.

| File | Runtime | Open it |
|---|---|---|
| `teduh-workflow-film.html` | 58 s auto-play, Three.js r128 (cdnjs) | double-click |
| `teduh-verification-simulator.html` | live calculation, zero CDN | double-click |
| `teduh-3d-digital-twin.html` | interactive 3D, Three.js r128 + OrbitControls (CDN) | double-click |

All three are self-contained: no build step, no server, no package install.

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

## `teduh-3d-digital-twin.html`

The spatial argument. So much of what goes wrong with shade is a geometry problem you can only see in three dimensions — trees planted in the road median, a west-facing boundary wall, terraces oriented north–south that shade the street without any trees at all.

- **Diurnal sun scrubber** (07:00–19:00) moves a directional light across real procedural geometry, so shadows lengthen and shift as you drag.
- **Layer 1 / Layer 2 toggle** — the same six corridors recoloured by design proxy (GIS canopy, SRI spec, ENVI-met) or by ground truth (walkable at 4 pm or not).
- **Weeks 1–2 vs Weeks 9–12** — switches on the retrofit assets: pergola over the school walk, cantilevered fins at the surau wall, awnings on the shop row, shade sails on the central spine, one cool-roof show unit.
- **Per-segment inspector** — drag dry-bulb, humidity, black-globe and shade continuity; WBGT and the audit score recompute live.
- **2.5-minute guided tour** — ten scenes that fly the camera, change the hour, switch layers and tabs on a timer.
- **Monte Carlo tab** — 10,000 seeded draws against the RP4 tariff, reported p10/p50/p90.
- **§3.5 panel** — the four standards myths the prototype refuses to repeat (MS 1525 for homes, SRI > 78, ENVI-met as statutory, MS ISO 37122:2019).

Camera presets: aerial overview, pedestrian eye level, GIS plan.

## Note on figures

Header numbers in the HTML are illustrative placeholders. Every KPI is recomputed from the segment dataset on load, so quote the live values, not the static ones.

The same applies to the narrative in the guided tour and the segment captions: those strings were written against an earlier, more optimistic dataset. Where the live ledger and the caption disagree, the ledger is what the code computes.
