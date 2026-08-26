# porcelain-map

**Uncertainty in Motion: Visualising Historical Incompleteness in the Provenance of East Asian Porcelain**

MA Digital Arts & Humanities dissertation project, University College Cork.
**Author:** Yuhan Yang · July 2026
**Supervisor:** Shawn Day

**Live artefact:** https://yserena60-yyy.github.io/porcelain-map/

## Overview

Interactive map visualising the circulation of early modern East Asian porcelain and the epistemic uncertainty of its digital provenance.

This project traces the circulation of East Asian export porcelain across early modern Eurasia, while treating the historical *uncertainty* surrounding that circulation as a primary subject of analysis rather than a limitation to be filtered out before mapping. The dataset comprises 60 curated records drawn from museum collections across Europe (Rijksmuseum, British Museum, MAK Vienna, SKD Dresden, Museum of the East India Company Lorient, Pitti Palace, Náprstek Museum, and others), each coded with three custom epistemic fields alongside standard spatial and temporal attributes:

- **`Data_Status`** — classifies the type of documentary incompleteness affecting a record (Extant / Contextual / Structural_Silence / Documented_Loss)
- **`Certainty_Score`** — a three-tier confidence rating (1–3) reflecting the strength of provenance evidence
- **`Social_Life`** — the object's social/institutional function at its European destination (e.g. Commercial Commodity, Diplomatic Currency, Scientific Curiosity, Aristocratic Collection), operationalising Appadurai's (1986) concept of the social life of things

## Repository Contents

| File | Description |
|---|---|
| `QGIS DATA.csv` | The 60-record master dataset, including all spatial, temporal, and epistemic fields |
| `QGIS PORCELAIN.qgz` | The original QGIS project file, in which the dataset's geometry, opacity rules, and TPQ/TAQ temporal logic were first prototyped and tested |
| `index.html` | The final web-based interactive map (Leaflet.js + D3), rebuilt from the QGIS prototype for public, browser-based access |

## Technical Pipeline

1. **Data collection** — individual museum records consulted directly; Rijksmuseum holdings harvested in bulk via its OAI-PMH API; cleaned in OpenRefine.
2. **Spatial prototyping** (`QGIS PORCELAIN.qgz`) — geometry, opacity rules, and temporal logic (TPQ/TAQ) built and tested in QGIS, using the Geometry Generator to render curved flow lines.
3. **Web deployment** (`index.html`) — the QGIS prototype was rebuilt as a standalone web map. Flow-line geometries were recomputed in Python as quadratic Bézier curves and exported as GeoJSON; the final interface is rendered in the browser with Leaflet.js, with D3 driving the interactive temporal slider.

Full methodological detail is provided in Chapter 3 of the dissertation (Sections 3.4–3.6).

## Reading the Map

- **Opacity** encodes `Certainty_Score`: full opacity = high confidence, near-transparent = low confidence or inaccessible.
- **Colour** encodes `Social_Life` category for porcelain-typology records; grey marks the six contextual, non-porcelain records retained in the dataset.
- **Dashed outlines** mark `Documented_Loss` records (Type C: physical object lost, documentary evidence survives).
- **Ghost nodes** (e.g. Munich) mark `Structural_Silence` records (Type A: object survives, provenance was never recorded) and appear without an originating flow line.
- Click or hover any route or node to view the full record, including — where applicable — the discrepancy between an object's institutionally recorded acquisition date and its historically corrected `Arrival_TAQ`.

## Citation

> Yang, Y. (2026) *Uncertainty in Motion: Visualising Historical Incompleteness in the Provenance of East Asian Porcelain*. MA dissertation, University College Cork.
