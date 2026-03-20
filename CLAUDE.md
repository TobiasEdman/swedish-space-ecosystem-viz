# Claude Code Instructions — swedish-space-ecosystem-viz

## RAG-system: des-agent

Detta repo indexeras av `des-agent`, ett RAG + multi-agent system som förstår hela Digital Earth Sweden-ekosystemet.

### Aktivera vid sessionsstart

```bash
source /Users/tobiasedman/developer/des-agent/resume.sh
```

### Använd vid kodändringar

```bash
des-agent query "hur fungerar [det du vill ändra]?"
```

### Efter commits — uppdatera index

```bash
des-agent ingest --repo space-ecosystem-viz
```

## Repo-identitet

- **Namn:** space-ecosystem-viz
- **Domän:** Publik visualisering (statisk HTML) av svenska rymdekosystemets kunskapsgraf
- **Nyckelgränssnitt:** `index.html` (8-vyig 3D-explorer med Three.js), `combined.html` (2D med React + D3)
- **Beroenden:**
  - **Upstream:** space-ecosystem-v2 exporterar `kg_core.json` + `kg_views.json` till `data/`

## Dataflöde

HTML-filerna laddar KG-data via `fetch()` vid runtime:
```
data/kg_core.json   — domänmeta, färger, labels, merged graph (588 noder, 733 kanter)
data/kg_views.json  — 7 vyspecifika datastrukturer (teman, institutioner, forskare, industri, intl)
```

Uppdatera data: kör `make deploy` i space-ecosystem-v2-repot.

## Arkitekturregler

- `var KG = {}` populeras via `fetch()` från `data/*.json` — redigera inte datablob manuellt
- HTML-filer kan redigeras fritt — de är källkod, inte genererade artefakter
- `data/` innehåller exporterad JSON från Neo4j — uppdateras av v2-repot
- Modifiera ALDRIG andra repos direkt härifrån
