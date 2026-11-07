# Repo-roll och arbetsregler — swedish-space-ecosystem-viz

`AGENTS.md` och det hanterade blocket i `CLAUDE.md` underhålls av `agentic-task`
(samordning mellan runtimes) och ska vara byteidentiska med dess
installationsmanifest. Repots egen roll och arbetsregler står här och gäller
tillsammans med dem.

## Repo-identitet

- **Domän:** Publik, statisk visualisering av det svenska rymdekosystemets
  kunskapsgraf.
- **Gränssnitt:** `index.html` är skalet; `2d.html` och `3d.html` är
  visualiseringsramar som laddar `data/kg_core.json` och
  `data/kg_views.json` via `fetch()`.
- **Producent:** Syskonrepot `swedish-space-ecosystem-v2` äger exportkontrakt
  och datagenerering. Detta repo äger endast konsumentkod och publicerad kopia.

## Arbetsregler

- Handredigera aldrig `data/*.json`; kopiera endast en Pydantic-validerad,
  integritetskontrollerad export från producentens dokumenterade flöde.
- Kräv unika och casefold-unika node-ID:n, noll dangling edge-endpoints,
  korrekta `content_hash`/record counts och byteidentiska producentkopior.
- Kontrollera `index.html`, `2d.html` och `3d.html` efter varje datauppdatering.
- HTML-filerna är källkod och får redigeras här; ändra inte producentrepot
  från denna arbetsyta.
- Tomma international-system-arrayer är en känd datatäckningslucka, inte
  bevis för att internationella relationer saknas.
- Commita inte hemligheter, personliga runtimefiler eller lokala sökvägar.
- Kör producentens `scripts/build_viz.py --verify` och en graf-
  integritetskontroll före commit. Ingen push eller publicering ingår i en
  lokal datauppdatering.
