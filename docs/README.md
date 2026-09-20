# Neon Arena 3D

Neon Arena is een kleine first-person browser-shooter. De game gebruikt Three.js, WebGL en eenvoudige geometrie om een 3D-arena met zombies, raycast-schieten, levels, score, health en ammo te maken.

## Documentatie-index

- [AI-agentinstructies](../AGENTS.md) — projectregels voor AI-agents
- [Ontwikkelaarsinstructies](DEVELOPMENT.md) — lokaal starten, architectuur en wijzigingsrichtlijnen
- [Roadmap](ROADMAP.md) — afgeronde onderdelen en geplande uitbreidingen

Alle algemene Markdown-documentatie hoort in deze `docs/`-map. `AGENTS.md` is de enige bewuste uitzondering: dit speciale bestand staat in de projectroot zodat AI-agents het automatisch kunnen vinden.

## Starten

De game importeert Three.js als ES-module vanaf een CDN. Gebruik daarom een lokale HTTP-server in plaats van het HTML-bestand direct met `file://` te openen.

```bash
python3 -m http.server 8000
```

Open daarna [http://localhost:8000](http://localhost:8000).

## Bestanden

| Bestand | Doel |
| --- | --- |
| `index.html` | Pagina, HUD, overlay en gamecontainer |
| `style.css` | Layout, HUD, crosshair en overlay-styling |
| `game.js` | Three.js-scène, besturing, gameplay en renderloop |
| `docs/` | Alle projectdocumentatie in Markdown |

## Besturing

- `WASD` — bewegen
- Muis — rondkijken na Pointer Lock
- Muisklik of spatie — schieten
- `R` — herladen
- `P` — pauzeren

De HUD toont score, levelvoortgang, health als hartjes en ammo als magazijnteller. Elk level bevat `level × 5` zombies; tussen levels verschijnt een levelmelding en wacht de volgende wave drie seconden voordat de spawn begint.

De game heeft momenteel geen buildstap, package manager of backend nodig.
