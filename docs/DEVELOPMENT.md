# Ontwikkelaarsinstructies

## Documentatiebeleid

- Maak alle nieuwe Markdown-bestanden aan in `docs/`.
- `AGENTS.md` is de enige uitzondering en staat in de projectroot voor automatische detectie door AI-agents.
- Werk [README.md](README.md) bij wanneer de documentatiestructuur of een belangrijk ontwikkelproces verandert.
- Voeg nieuwe documenten toe aan de documentatie-index in `docs/README.md`.

De volledige agentwerkwijze staat in [AGENTS.md](../AGENTS.md).

## Lokale ontwikkeling

1. Start vanuit de projectmap een lokale HTTP-server:

   ```bash
   python3 -m http.server 8000
   ```

2. Open `http://localhost:8000` in een moderne browser.
3. Klik op `Start game` om Pointer Lock te activeren.

Er is geen npm-project of bundler ingesteld. Three.js wordt in `game.js` geïmporteerd vanaf een vaste CDN-versie.

## Architectuur

- `index.html` bevat de pagina-opbouw, HUD, levelmelding en game-overlay.
- `style.css` beheert de responsieve layout en visuele interface.
- `game.js` initialiseert de Three.js-scène en bevat de renderloop, spelerbesturing, zombie-opbouw, level-/wave-spawn, raycast-schieten, collisions, particles en game state.
- `docs/ROADMAP.md` beschrijft wat af is en wat nog gepland staat.

## Gameplay-aanpassingen

Belangrijke waarden staan centraal in `game.js`:

- `arena` — afmetingen van de arena
- `state` — score, levelvoortgang, health, ammo, reload-timers en camera-rotatie
- `materials` en `zombieGeometry` — kleuren, materialen en gedeelde geometrie voor zombies en wapen
- `spawnEnemy()` en `randomSpawn()` — zombie-aanmaak, minimale spawnafstand en spawnpositie
- `startNextLevel()` — levelprogressie; level `n` bevat `n × 5` zombies
- `update(delta)` — beweging, levelvertraging, moeilijkheid, damage, collisions, loopanimatie en particles

Gebruik bij nieuwe 3D-objecten bij voorkeur eenvoudige geometrie, zet `castShadow` of `receiveShadow` alleen aan waar nodig en ruim verwijderde objecten op uit de scene en arrays.
De raycast voor zombies moet recursief blijven omdat een zombie uit meerdere meshes bestaat. Gebruik de `enemyRoot`-verwijzing om bij een treffer de volledige zombie te verwijderen.

## Besturing en browsergedrag

De game gebruikt de Pointer Lock API. Muiskijk-input wordt alleen verwerkt wanneer de game actief is en de gamecontainer pointer lock heeft. Test daarom altijd starten, pauzeren, pointer lock verlaten en opnieuw starten.

## Verificatie

Controleer na wijzigingen minimaal:

- de game opent via een lokale HTTP-server;
- de scene zichtbaar rendert;
- WASD, muis en schieten werken;
- vijanden schade en score correct aanpassen;
- ammo, herladen met `R`, automatische reload en de herlaadanimatie werken;
- game-over en opnieuw starten werken;
- level 1 spawnt 5 zombies, volgende levels `level × 5`, en de levelmelding plus spawnpauze werken;
- zombies spawnen niet binnen de minimale afstand van de speler;
- de browserconsole geen Three.js- of runtimefouten toont.
