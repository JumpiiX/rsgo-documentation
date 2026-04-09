# Missing Files List für RSGO Dokumentation

## Ordner-Struktur zu erstellen:
```
/Users/jumpiix/Developer/davloio/rsgo-documentation/
├── docs/
│   └── images/
│       ├── [DIAGRAMME]
│       └── [SCREENSHOTS]
```

## Fehlende Diagramme:

### 1. SEUSAG-Diagramm
**Pfad:** `/Users/jumpiix/Developer/davloio/rsgo-documentation/docs/images/seusag-diagram.png`
**Inhalt:** System-Architektur Diagramm mit:
- Externe Umgebung: Spieler Browser, GitHub, Docker Hub, Hetzner
- Server/Docker Container: Rust Backend, WebSocket Server (6969), Game State Manager
- Client: Three.js, WebSocket Client, Input Handler
- Verbindungen zwischen allen Komponenten zeigen

### 2. Sprint Timeline 
**Pfad:** `/Users/jumpiix/Developer/davloio/rsgo-documentation/docs/images/sprint-timeline.png`
**Inhalt:** Zeitstrahl-Visualisierung:
- X-Achse: Februar 2026 → März 2026 → April 2026
- Sprint 1: 52 Story Points
- Sprint 2: 54 Story Points  
- Sprint 3: 34 Story Points
- Balken oder Timeline-Chart

### 3. Sprint 1 Retrospektive
**Pfad:** `/Users/jumpiix/Developer/davloio/rsgo-documentation/docs/images/sprint1-retrospective.png`
**Inhalt:** Retrospektive-Board mit 3 Spalten:
- Was lief gut: WebSockets schnell genug, Three.js Performance, 15 Spieler
- Challenges: Pointer Lock Sensitivity, ws:// vs wss://, Kollisionserkennung
- Learnings: Browser Power, 20Hz Tickrate, Client-Side Prediction

### 4. Sprint 2 Retrospektive
**Pfad:** `/Users/jumpiix/Developer/davloio/rsgo-documentation/docs/images/sprint2-retrospective.png`
**Inhalt:** Retrospektive-Board mit 3 Spalten:
- Was lief gut: Hit-Detection fair, Revolver-Model, Kill-Feed süchtig
- Challenges: Lag-Compensation, Death-Animation, Weapon-Balancing
- Learnings: Game-Feel > Simulation, Visual Feedback wichtig

### 5. Sprint 3 Retrospektive
**Pfad:** `/Users/jumpiix/Developer/davloio/rsgo-documentation/docs/images/sprint3-retrospective.png`
**Inhalt:** Retrospektive-Board mit 3 Spalten:
- Was lief gut: Docker Deployment easy, Message-Batching, 73 Spieler
- Challenges: Firewall vergessen, Message-Batching Refactoring
- Learnings: Profiling wichtig, Multi-Stage Builds, 5€ Server reicht

## Fehlende Screenshots:

### 6. Multiplayer First Test
**Pfad:** `/Users/jumpiix/Developer/davloio/rsgo-documentation/docs/images/multiplayer-first-test.png`
**Inhalt:** 
- In-Game Screenshot mit 3-5 Spielern
- Spieler als Kapseln mit Nametags
- Arena/Map sichtbar
- Debug-Info oder FPS-Counter

### 7. Revolver In-Game
**Pfad:** `/Users/jumpiix/Developer/davloio/rsgo-documentation/docs/images/revolver-ingame.png`
**Inhalt:**
- First-Person View
- Revolver-Model unten rechts sichtbar
- Crosshair in der Mitte
- HUD mit Health/Ammo Anzeige

### 8. Scoreboard
**Pfad:** `/Users/jumpiix/Developer/davloio/rsgo-documentation/docs/images/scoreboard.png`
**Inhalt:**
- TAB-Menu Overlay
- Tabelle mit: Player Name | Kills | Deaths | K/D Ratio | Ping
- Mindestens 5 Spieler in Liste
- Eigener Name highlighted

### 9. Performance Graph
**Pfad:** `/Users/jumpiix/Developer/davloio/rsgo-documentation/docs/images/performance-graph.png`
**Inhalt:**
- Graph/Chart mit CPU und RAM Usage
- X-Achse: Anzahl Spieler (0-50)
- Y-Achse: Usage in %
- Zeige dass bei 50 Spielern nur ~45% CPU

### 10. Kill-Feed
**Pfad:** `/Users/jumpiix/Developer/davloio/rsgo-documentation/docs/images/kill-feed.png`
**Inhalt:**
- Obere rechte Ecke UI
- 3-4 Kill-Messages: "Player1 killed Player2"
- Semi-transparent mit Fade-Out
- Verschiedene Farben für Killer/Victim

### 11. Arena Overview
**Pfad:** `/Users/jumpiix/Developer/davloio/rsgo-documentation/docs/images/arena-overview.png`
**Inhalt:**
- Top-Down oder Isometric View der Map
- Zeige Wände/Obstacles
- Spawn-Points markiert
- Map-Größe erkennbar (100x100 units)

## Befehle zum Erstellen der Ordner-Struktur:
```bash
cd /Users/jumpiix/Developer/davloio/rsgo-documentation
mkdir -p docs/images
```

## Placeholder-Images generieren (optional):
Falls du schnell Placeholder-Bilder brauchst:
```bash
# Erstelle graue Placeholder-Bilder mit ImageMagick
for file in seusag-diagram sprint-timeline sprint1-retrospective sprint2-retrospective sprint3-retrospective multiplayer-first-test revolver-ingame scoreboard performance-graph kill-feed arena-overview; do
    convert -size 800x600 xc:gray -pointsize 30 -draw "text 250,300 '${file}'" docs/images/${file}.png
done
```

## Priorität:
**Must-Have für Präsentation:**
1. SEUSAG-Diagramm
2. Screenshots vom Game (Revolver, Scoreboard, Multiplayer)
3. Performance Graph

**Nice-to-Have:**
- Sprint Retrospektiven
- Sprint Timeline
- Kill-Feed Details