# TEDUH — neighbourhood comfort & shade verification

**Thesis:** a township can promise shade and outdoor comfort through its design. TEDUH checks whether those promises survive contact with the actual footpath people walk.

A design proxy — GIS canopy percentage, a roof SRI specification, a 400 m green-space radius — describes *intent*. It does not measure whether a mother pushing a pram to the surau at 1 pm is standing in sun. TEDUH keeps those two categories apart, scores them separately, and flags every segment where the gap between them exceeds 15 points as `PROXY_UNRELIABLE`.

---

## Runnable prototypes

| File | What it does | Needs |
|---|---|---|
| [`demos/teduh-workflow-film.html`](demos/teduh-workflow-film.html) | The 58-second auto-playing film: design intent → baseline → expectation vs. reality → gap prioritisation → intervention → re-measurement → Comfort & Shade Ledger. Camera choreography, simulated sun arc, spatially anchored callouts. | Internet (Three.js r128, cdnjs) |
| [`demos/teduh-verification-simulator.html`](demos/teduh-verification-simulator.html) | The audit instrument: 6-segment precinct ledger, live WBGT field simulator (ISO 7243 with the Stull 2011 wet-bulb approximation), diurnal thermal-exile clock, seeded 10,000-draw Monte Carlo household energy range, and per-stakeholder output views. | Nothing — no CDN |

Open either file directly in a browser. No build step, no server, no dependencies beyond the CDN noted above.

## Specifications

| File | What it specifies |
|---|---|
| [`docs/TEDUH_58s_Workflow_Animation_Specification.docx`](docs/TEDUH_58s_Workflow_Animation_Specification.docx) | The film: seven workflow transitions, timing, scene grammar, and the ledger artefact that closes it. |
| [`docs/TEDUH_Interactive_Heat_Verification_Simulator.docx`](docs/TEDUH_Interactive_Heat_Verification_Simulator.docx) | The audit loop across a multi-week pilot: baseline audit → gap diagnosis → surgical intervention → re-measurement, with proxy / measured / modelled / assumed values held visually separate. |
| [`docs/TEDUH_3D_WebGL_Digital_Twin_Microclimate_Audit.docx`](docs/TEDUH_3D_WebGL_Digital_Twin_Microclimate_Audit.docx) | The WebGL digital twin: scene construction, segment-level microclimate formulas, simulation engine, browser overlay. |

## Method

`WBGT = 0.7·T_nw + 0.2·T_g + 0.1·T_a` (ISO 7243 outdoor), with `T_nw` from Stull (2011). Walkability threshold is configurable and defaults to 28.0 °C.

A segment is flagged when `|proxy score − measured score| > 15` on a 0–100 scale. The flag is two-sided on purpose: a proxy can over-promise shade (the usual failure) or under-credit a route that is actually shaded by building massing rather than trees.

## Integrity note

The township data is a **simulated pilot, not field data** (§9.10 of the specification). GBI Township and LCCF are voluntary frameworks; GP024 is a planning guideline, not statute; residential provisions cite MS 2680, never MS 1525. No endorsement by Sime Darby Property, GBI, MGTC or PLANMalaysia is implied.

The verification simulator's header figures are illustrative placeholders — every KPI is recomputed from the segment data on page load, so the live numbers are the ones to quote.

## Status

- Specifications: complete as documents.
- Prototypes: runnable from `demos/`.
- No field measurements, no deployed sensors, no production backend.
