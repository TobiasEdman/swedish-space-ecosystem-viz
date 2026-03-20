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
- **Domän:** Publik visualisering (statisk HTML-distribution)
- **Nyckelgränssnitt:** `index.html` (8-vyig 3D-explorer), `combined.html` (2D-karta)
- **Beroenden:**
  - **Upstream:** Tar emot byggda HTML-filer från v1/v2

## Arkitekturregler

- Filer här är BYGGDA artefakter — redigera inte HTML manuellt
- Ändringar ska göras i v1 (`build_viz.py`) eller v2 (`export/`) och sedan byggas om
- `var KG = {...}` innehåller hela knowledge graph:en — ändra inte formatet
- Modifiera ALDRIG andra repos direkt härifrån
