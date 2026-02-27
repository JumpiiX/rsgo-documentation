# RSGO - Real-Time Multiplayer FPS Game
## Semesterarbeit ITCNE24 - David Unterguggenberger

## Projektübersicht

RSGO ist ein browserbasiertes Multiplayer First-Person Shooter Spiel, inspiriert von CS:GO. Das Projekt nutzt moderne Web-Technologien mit einem Rust-Backend für optimale Performance und einem Three.js-Frontend für 3D-Grafik im Browser.

### Projektziele (SMART formuliert)

1. WebSocket-Kommunikation: Bis Ende Sprint 1 eine stabile, bidirektionale Echtzeit-Kommunikation zwischen Client und Server mit unter 50ms Latenz implementieren
2. Multiplayer-Synchronisation: Bis Ende Sprint 2 mindestens 10 Spieler gleichzeitig mit synchronisierten Positionen und Aktionen unterstützen
3. Game Mechanics: Bis Ende Sprint 3 vollständige FPS-Mechaniken (Movement, Shooting, Health/Shield, Respawn) implementieren
4. Cloud Deployment: Bis Sprint 4 das Spiel auf Docker mit CI/CD Pipeline deployen und live demonstrieren (15.04.2026)

### Technologie-Stack

Backend:
- Rust mit Tokio (Async Runtime)
- WebSocket Server (tokio-tungstenite)
- Docker Container

Frontend:
- JavaScript ES6 Modules
- Three.js für 3D-Grafik
- WebSocket Client
- Docker/Nginx

## Definition of Done (DoD)

Eine User Story/Task gilt als abgeschlossen, wenn:

- [ ] Code funktioniert: Alle Akzeptanzkriterien sind erfüllt und getestet
- [ ] Git Integration: Code ist committed und gepusht mit aussagekräftiger Commit-Message
- [ ] Dokumentation: Relevante Dokumentation wurde erstellt oder aktualisiert
- [ ] Testing: Funktionalität wurde manuell getestet mit Testprotokoll
- [ ] Peer Review: Code wurde von mir selbst nochmals überprüft
- [ ] Deployment Ready: Code läuft in Docker-Container ohne Fehler
- [ ] Keine kritischen Bugs: Keine bekannten Breaking-Bugs oder Sicherheitslücken

## Sprint 1: Grundlegende Spielmechaniken (Februar - März 2026)

### Sprint Goal
Spieler können sich in einer 3D-Welt bewegen und die Client-Server-Kommunikation funktioniert zuverlässig über WebSockets.

### User Stories

#### User Story 1: WebSocket-Verbindung
Als Spieler möchte ich mich automatisch mit dem Game-Server verbinden, damit ich ohne technisches Wissen direkt spielen kann.

Story Points: 5

Akzeptanzkriterien:
- [ ] WebSocket-Server startet auf Port 6969
- [ ] Client verbindet sich beim Laden der Seite automatisch
- [ ] Reconnect-Mechanismus bei Verbindungsabbruch (3s Delay)
- [ ] Connection-Status wird in der Konsole geloggt
- [ ] Server sendet Welcome-Message mit eindeutiger Player-ID
- [ ] Fehlerbehandlung bei Verbindungsproblemen

#### User Story 2: 3D-Spielwelt
Als Spieler möchte ich eine 3D-Arena mit Hindernissen sehen, damit ich eine immersive Spielumgebung erlebe.

Story Points: 8

Akzeptanzkriterien:
- [ ] Three.js Scene mit Renderer initialisiert
- [ ] Spielfeld mit Boden und Wänden generiert
- [ ] Mindestens 5 Hindernisse/Deckungen platziert
- [ ] Beleuchtung (Ambient + Directional Light) konfiguriert
- [ ] Skybox oder Hintergrundfarbe gesetzt
- [ ] Performance: 60 FPS auf Standard-Hardware

#### User Story 3: First-Person-Kamera
Als Spieler möchte ich mit der Maus meine Blickrichtung steuern, damit ich mich wie in einem echten FPS-Spiel umsehen kann.

Story Points: 5

Akzeptanzkriterien:
- [ ] Pointer-Lock bei Klick ins Spiel aktiviert
- [ ] Mausbewegung steuert Kamera-Rotation
- [ ] Sensitivität einstellbar (Config-Variable)
- [ ] Vertikale Rotation begrenzt (-90° bis +90°)
- [ ] ESC-Taste gibt Mauszeiger frei
- [ ] Smooth Camera Movement ohne Ruckeln

#### User Story 4: Spielerbewegung (WASD)
Als Spieler möchte ich meinen Charakter mit WASD-Tasten bewegen, damit ich mich in der Spielwelt fortbewegen kann.

Story Points: 8

Akzeptanzkriterien:
- [ ] W/S für Vorwärts/Rückwärts-Bewegung
- [ ] A/D für Seitwärts-Bewegung (Strafe)
- [ ] Bewegung relativ zur Blickrichtung
- [ ] Kollisionserkennung mit Wänden
- [ ] Sprint mit Shift-Taste (1.5x Geschwindigkeit)
- [ ] Smooth Movement mit Beschleunigung/Abbremsung

#### User Story 5: Netzwerk-Synchronisation
Als Spieler möchte ich meine Position an den Server senden, damit andere Spieler meine Bewegungen sehen können.

Story Points: 13

Akzeptanzkriterien:
- [ ] Position wird alle 50ms an Server gesendet
- [ ] Server empfängt und verarbeitet Move-Messages
- [ ] Message-Format: {type: "move", x, y, z, rotation_x, rotation_y}
- [ ] Server broadcast Position an alle anderen Spieler
- [ ] Bandbreiten-Optimierung: Nur bei Änderungen senden
- [ ] Latenz-Messung implementiert

#### User Story 6: Spieler-Spawning
Als Spieler möchte ich beim Beitritt an einem zufälligen Spawn-Punkt erscheinen, damit ich direkt ins Spiel einsteigen kann.

Story Points: 5

Akzeptanzkriterien:
- [ ] Mindestens 8 Spawn-Punkte definiert
- [ ] Zufällige Spawn-Point-Auswahl
- [ ] Spieler erscheint mit voller Gesundheit (100 HP)
- [ ] Initial-Position wird an alle Clients gesendet
- [ ] Spawn-Protection für 2 Sekunden
- [ ] Visueller Spawn-Effekt (optional)

#### User Story 7: Andere Spieler anzeigen
Als Spieler möchte ich andere Spieler als 3D-Modelle sehen, damit ich mit ihnen interagieren kann.

Story Points: 8

Akzeptanzkriterien:
- [ ] Placeholder-Modell für andere Spieler (Capsule/Box)
- [ ] Spieler-Positionen werden empfangen und aktualisiert
- [ ] Smooth Interpolation zwischen Positionen
- [ ] Spieler-Rotation wird korrekt dargestellt
- [ ] Spielername über dem Modell anzeigen
- [ ] Spieler verschwinden bei Disconnect

### Sprint 1 Metriken

- Total Story Points: 52
- Velocity Target: 50-60 Points
- Sprint Dauer: 4 Wochen
- Release: MVP (Minimum Viable Product)

### MVP Definition
Das MVP nach Sprint 1 umfasst:
- Funktionierender WebSocket Server/Client
- 3D-Spielwelt mit First-Person-Steuerung
- Grundlegende Multiplayer-Synchronisation
- Spieler können sich sehen und bewegen

## Sprint Planning

### Technische Tasks (Breakdown)

Backend-Setup:
- Rust-Projekt mit Cargo initialisieren
- WebSocket-Server Grundstruktur
- Message-Types definieren (Serde)
- Player-Management System
- Docker Container erstellen

Frontend-Setup:
- Three.js Integration
- Modular ES6 Architektur
- Input-System (Keyboard/Mouse)
- Network-Client Klasse
- Asset-Loading System

### Risikomatrix Sprint 1

| Risiko | Wahrscheinlichkeit | Impact | Mitigation |
|--------|-------------------|--------|------------|
| WebSocket-Latenz zu hoch | Mittel | Hoch | Message-Batching, Binary Protocol evaluieren |
| Three.js Performance | Niedrig | Mittel | LOD-System, Frustum Culling |
| Browser-Kompatibilität | Niedrig | Niedrig | Feature-Detection, Polyfills |

### Test-Szenarien

1. Connection-Test: 10 Clients gleichzeitig verbinden
2. Movement-Test: Smooth Movement
3. Stress-Test: 20 Spieler in einer Map
4. Browser-Test: Chrome, Firefox, Safari

## Sprint Review und Retrospektive

### Review-Kriterien
- [ ] Alle User Stories completed
- [ ] Performance-Ziele erreicht (<50ms Latenz)
- [ ] Dokumentation aktualisiert

### Retrospektive-Template (Mad/Sad/Glad)
- Mad (Was hat nicht funktioniert?)
- Sad (Was war enttäuschend?)
- Glad (Was lief gut?)



## Links und Ressourcen

- Three.js Documentation: https://threejs.org/docs/
- Rust Async Book: https://rust-lang.github.io/async-book/
- WebSocket Protocol RFC: https://tools.ietf.org/html/rfc6455
- Game Networking Resources: https://gafferongames.com/
