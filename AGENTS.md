# AI-agentinstructies — Neon Arena 3D

## Projectdoel

Neon Arena 3D is een kleine first-person browser-shooter. De game draait in de browser met vanilla HTML, CSS, JavaScript, Three.js en WebGL.

## Belangrijke bestanden

- `index.html` — pagina-opbouw, HUD, overlay en gamecontainer.
- `style.css` — responsieve layout, HUD, crosshair en overlay-styling.
- `game.js` — Three.js-scène, renderloop, input, gameplay, vijanden, raycast-schieten, collisions en particles.
- `docs/README.md` — documentatie-index en gebruikersinformatie.
- `docs/DEVELOPMENT.md` — ontwikkelworkflow en technische richtlijnen.
- `docs/ROADMAP.md` — afgeronde onderdelen en geplande uitbreidingen.

Lees de relevante bestanden eerst voordat je wijzigingen maakt.

## Ontwikkelworkflow

Start de game vanuit de projectroot met:

```bash
python3 -m http.server 8000
```

Open daarna `http://localhost:8000` in een moderne browser. De game gebruikt een ES-module-import van Three.js vanaf een vaste CDN-versie en heeft momenteel geen npm-project of bundler.

## Architectuur- en gameplayregels

- Behoud de first-person ervaring, WASD-beweging, Pointer Lock, raycast-schieten en bestaande HUD-flow.
- Gebruik Three.js-geometrie en materialen die passen bij de bestaande neonstijl.
- Houd gameplay-state centraal in `state` en hergebruik bestaande functies waar dat logisch is.
- Houd arena-grenzen actief en voorkom dat de camera buiten de arena beweegt.
- Ruim verwijderde meshes, particles en materialen op uit de scene en bijbehorende arrays.
- Beperk schaduwen, geometrie en effecten wanneer een wijziging performance kan beïnvloeden.
- Voeg geen framework, buildproces, backend of externe service toe zonder expliciete opdracht.

## Wijzigingsregels

- Wijzig alleen bestanden die relevant zijn voor de opdracht.
- Behoud bestaande functionaliteit tenzij de opdracht expliciet om ander gedrag vraagt.
- Gebruik duidelijke, kleine wijzigingen en houd de huidige eenvoudige projectstructuur intact.
- Voer geen destructieve Git-acties uit, zoals `reset --hard` of ongeautoriseerde verwijderingen.
- Maak geen nieuwe Markdown-bestanden in de projectroot, behalve dit speciale `AGENTS.md`-bestand. Alle overige Markdown-documentatie hoort in `docs/`.
- Werk `docs/README.md` bij wanneer nieuwe documentatie wordt toegevoegd of de documentatiestructuur verandert.

## Verificatie na wijzigingen

Controleer minimaal:

- de game opent via een lokale HTTP-server;
- de 3D-scène zichtbaar rendert zonder consolefouten;
- WASD-beweging en muiskijken werken;
- schieten, vijandverwijdering en score werken;
- health, damage, pauze, game-over en opnieuw starten werken;
- responsive gedrag en arena-grenzen intact blijven.

Rapporteer duidelijk welke controles wel en niet zijn uitgevoerd.
