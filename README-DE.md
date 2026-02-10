# 🦞 OpenClaw — Persönlicher KI-Assistent

<p align="center">
    <picture>
        <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/openclaw/openclaw/main/docs/assets/openclaw-logo-text-dark.png">
        <img src="https://raw.githubusercontent.com/openclaw/openclaw/main/docs/assets/openclaw-logo-text.png" alt="OpenClaw" width="500">
    </picture>
</p>

<p align="center">
  <strong>Metamorphose! Metamorphose!</strong>
</p>

<p align="center">
  <a href="https://github.com/openclaw/openclaw/actions/workflows/ci.yml?branch=main"><img src="https://img.shields.io/github/actions/workflow/status/openclaw/openclaw/ci.yml?branch=main&style=for-the-badge" alt="CI status"></a>
  <a href="https://github.com/openclaw/openclaw/releases"><img src="https://img.shields.io/github/v/release/openclaw/openclaw?include_prereleases&style=for-the-badge" alt="GitHub release"></a>
  <a href="https://discord.gg/clawd"><img src="https://img.shields.io/discord/1456350064065904867?label=Discord&logo=discord&logoColor=white&color=5865F2&style=for-the-badge" alt="Discord"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge" alt="MIT License"></a>
</p>

**OpenClaw** ist ein persönlicher KI-Assistent, der auf Ihren eigenen Geräten läuft. Es bietet Unterstützung über gängige Kanäle (WhatsApp, Telegram, Slack, Discord, Google Chat, Signal, iMessage, Microsoft Teams, WebChat) sowie über erweiterte Kanäle wie BlueBubbles, Matrix, Zalo und Zalo Personal. Es unterstützt macOS/iOS/Android und kann von Ihnen gesteuerte Live-Canvas-Oberflächen rendern. Das Gateway ist nur eine Kontrollplattform, das Produkt selbst ist der eigentliche Assistent.
Wenn Sie einen lokalen Assistenten wünschen, der schnell ist und ständig online ist, ist dies die richtige Wahl.

[Website](https://openclaw.ai) · [Offizielle Dokumentation](https://docs.openclaw.ai) · [DeepWiki](https://deepwiki.com/openclaw/openclaw) · [Erste Schritte](https://docs.openclaw.ai/start/getting-started) · [Aktualisierungen](https://docs.openclaw.ai/install/updating) · [Beispiele](https://docs.openclaw.ai/start/showcase) · [Häufige Fragen](https://docs.openclaw.ai/start/faq) · [Assistent](https://docs.openclaw.ai/start/wizard) · [Nix](https://github.com/openclaw/nix-clawdbot) · [Docker](https://docs.openclaw.ai/install/docker) · [Discord](https://discord.gg/clawd)

Empfohlene Einrichtung: Führen Sie den Setup-Assistenten aus (`openclaw onboard`). Dieser führt Sie durch die Einrichtung von Gateway, Arbeitsbereichen, Kanälen und Fähigkeiten. Der Befehlszeilenassistent ist der empfohlene Weg und läuft unter **macOS, Linux und Windows (über WSL2; stark empfohlen)**.
Unterstützt npm, pnpm oder bun. Neuinstallation? Beginnen Sie hier: [Erste Schritte](https://docs.openclaw.ai/start/getting-started)

**Abonnement (OAuth):**

- **[Anthropic](https://www.anthropic.com/)** (Claude Pro/Max)
- **[OpenAI](https://openai.com/)** (ChatGPT/Codex)

Modellhinweise: Obwohl alle Modelle unterstützt werden, empfehle ich dringend **Anthropic Pro/Max (100/200) + Opus 4.6**, um bessere Langzeit-Leistung und höhere Störfestigkeit zu erhalten. Siehe [Online-Anleitung](https://docs.openclaw.ai/start/onboarding).

## Modelle (Auswahl + Authentifizierung)

- Modellkonfiguration + CLI: [Modelle](https://docs.openclaw.ai/concepts/models)
- Authentifizierungsprofile (OAuth vs. API-Schlüssel) + Fallback: [Modell-Ausfallsicherheit](https://docs.openclaw.ai/concepts/model-failover)

## Installation

Laufzeitumgebung: **Node ≥22**.

```bash
npm install -g openclaw@latest
# oder: pnpm add -g openclaw@latest

openclaw onboard --install-daemon
```

Der Assistent installiert den Gateway-Dienst (launchd/systemd Benutzerdienst), damit dieser dauerhaft läuft.

## Schnellstart (Kurzfassung)

Laufzeitumgebung: **Node ≥22**.

Vollständige Anleitung für Anfänger (Authentifizierung, Verknüpfung, Kanäle): [Erste Schritte](https://docs.openclaw.ai/start/getting-started)

```bash
openclaw onboard --install-daemon

openclaw gateway --port 18789 --verbose

# Nachricht senden
openclaw message send --to +1234567890 --message "Hello from OpenClaw"

# Mit dem Assistenten chatten (beliebige Nachrichten können an verbundene Kanäle gesendet werden: WhatsApp/Telegram/Slack/Discord/Google Chat/Signal/iMessage/BlueBubbles/Microsoft Teams/Matrix/Zalo/Zalo Personal/WebChat)
openclaw agent --message "Ship checklist" --thinking high
```

Wie aktualisiert man? [Aktualisierungsanleitung](https://docs.openclaw.ai/install/updating) (führen Sie `openclaw doctor` aus).

## Entwicklerversion-Status-Erklärung

- **stable**: Getaggte Versionen (`vYYYY.M.D` oder `vYYYY.M.D-<patch>`), npm dist-tag `latest`.
- **beta**: Vorabversionen (`vYYYY.M.D-beta.N`), npm dist-tag `beta` (macOS App kann fehlen).
- **dev**: Aktuelle Hauptentwicklungsversion, npm dist-tag `dev` (wenn veröffentlicht).

Wechseln (git + npm): `openclaw update --channel stable|beta|dev`.
Details: [Entwicklerversionen-Status](https://docs.openclaw.ai/install/development-channels).

## Quelle (Entwicklung)

Empfohlen wird `pnpm` für Builds aus der Quelle. Bun ist optional für direktes Ausführen von TypeScript.

```bash
git clone https://github.com/openclaw/openclaw.git
cd openclaw

pnpm install
pnpm ui:build # Installiert automatisch UI-Abhängigkeiten beim ersten Start
pnpm build

pnpm openclaw onboard --install-daemon

# Entwicklungszyklus (automatisches Neuladen bei TS-Änderungen)
pnpm gateway:watch
```

Hinweis: `pnpm openclaw ...` führt direkt TypeScript aus (über `tsx`). `pnpm build` generiert `dist/` zum Ausführen/Packen der `openclaw` Binärdatei über Node.

## Sicherheitsstandardeinstellungen (DM-Zugriffsberechtigungen)

OpenClaw verbindet sich mit echten Sofortnachrichten-Plattformen. Behandeln Sie eingehende Direktnachrichten als **nicht vertrauenswürdige Eingaben**.

Vollständiger Sicherheitsleitfaden: [Sicherheitsleitfaden](https://docs.openclaw.ai/gateway/security)

Standardverhalten für Telegram/WhatsApp/Signal/iMessage/Microsoft Teams/Discord/Google Chat/Slack:

- **DM-Verknüpfung** (`dmPolicy="pairing"` / `channels.discord.dm.policy="pairing"` / `channels.slack.dm.policy="pairing"`): Unbekannte Absender erhalten einen kurzen Verknüpfungscode, der Bot verarbeitet ihre Nachrichten nicht.
- Genehmigung: `openclaw pairing approve <channel> <code>` (danach wird der Absender zum lokalen Speicher hinzugefügt).
- Öffentliche eingehende Direktnachrichten benötigen explizite Zustimmung: Setzen Sie `dmPolicy="open"` und fügen Sie `"*"` zur Kanalzulassungsliste hinzu (`allowFrom` / `channels.discord.dm.allowFrom` / `channels.slack.dm.allowFrom`).

Führen Sie `openclaw doctor` aus, um riskante/konfigurationsfehlerhafte DM-Richtlinien zu entdecken.

## Wesentliche Punkte

- **[Lokale Gateway-Priorität](https://docs.openclaw.ai/gateway)** — Einheitliche Kontrollfläche für Sitzungen, Kanäle, Tools und Ereignisse.
- **[Mehrkanal-Inbox](https://docs.openclaw.ai/channels)** — WhatsApp, Telegram, Slack, Discord, Google Chat, Signal, BlueBubbles (iMessage), iMessage (veraltet), Microsoft Teams, Matrix, Zalo, Zalo Personal, WebChat, macOS, iOS/Android.
- **[Multi-Agenten-Routing](https://docs.openclaw.ai/gateway/configuration)** — Weiterleitung eingehender Kanäle/Konten/Peers zu isolierten Agenten (Arbeitsbereich + Sitzung pro Agent).
- **[Sprachaktivierung](https://docs.openclaw.ai/nodes/voicewake) + [Sprechmodus](https://docs.openclaw.ai/nodes/talk)** — Dauerhaft aktive Sprachfunktion von ElevenLabs für macOS/iOS/Android.
- **[Live-Canvas](https://docs.openclaw.ai/platforms/mac/canvas)** — Agentengeführter visueller Arbeitsbereich mit [A2UI](https://docs.openclaw.ai/platforms/mac/canvas#canvas-a2ui).
- **[Erstklassige Tools](https://docs.openclaw.ai/tools)** — Browser, Canvas, Knoten, Cron-Jobs, Sitzungen und Discord/Slack-Aktionen.
- **[Begleit-Apps](https://docs.openclaw.ai/platforms/macos)** — macOS-Menüleisten-App + iOS/Android [Knoten](https://docs.openclaw.ai/nodes).
- **[Assistent](https://docs.openclaw.ai/start/wizard) + [Fähigkeiten](https://docs.openclaw.ai/tools/skills)** — Assistentengesteuerte Einrichtung mit gebündelten/verwalteten/Arbeitsbereich-Fähigkeiten.

## Sternverlauf

[![Star History Chart](https://api.star-history.com/svg?repos=openclaw/openclaw&type=date&legend=top-left)](https://www.star-history.com/#openclaw/openclaw&type=date&legend=top-left)

## Was wir bisher erreicht haben

### Kernplattform

- [Gateway-Kontrollpanel](https://docs.openclaw.ai/gateway) mit Sitzungen, Status, Konfiguration, Cron-Jobs, Webhooks, [Interaktive Steuerungsoberfläche](https://docs.openclaw.ai/web) und [Canvas-Host](https://docs.openclaw.ai/platforms/mac/canvas#canvas-a2ui).
- [CLI-Schnittstelle](https://docs.openclaw.ai/tools/agent-send): Gateway, Agent, Senden, [Assistent](https://docs.openclaw.ai/start/wizard) und [Sicherheit](https://docs.openclaw.ai/gateway/doctor).
- [Pi-Agent-Laufzeitumgebung](https://docs.openclaw.ai/concepts/agent) mit RPC-Muster, unterstützt Werkzeug-Streaming und Block-Streaming.
- [Sitzungsmodell](https://docs.openclaw.ai/concepts/session): `main` für direktes Chatten, Gruppentrennung, Aktivierungsmodus, Warteschlangenmodus, Antworten. Gruppenregeln: [Gruppen](https://docs.openclaw.ai/concepts/groups).
- [Medienkanäle](https://docs.openclaw.ai/nodes/images): Bilder/Audio/Video, Transkriptions-Hooks, Größenbeschränkungen, Lebenszyklus temporärer Dateien. Audio-Details: [Audio](https://docs.openclaw.ai/nodes/audio).

### Kanäle

- [Kanäle](https://docs.openclaw.ai/channels): [WhatsApp](https://docs.openclaw.ai/channels/whatsapp) (Baileys), [Telegram](https://docs.openclaw.ai/channels/telegram) (grammY), [Slack](https://docs.openclaw.ai/channels/slack) (Bolt), [Discord](https://docs.openclaw.ai/channels/discord) (discord.js), [Google Chat](https://docs.openclaw.ai/channels/googlechat) (Chat API), [Signal](https://docs.openclaw.ai/channels/signal) (signal-cli), [BlueBubbles](https://docs.openclaw.ai/channels/bluebubbles) (iMessage, empfohlen), [iMessage](https://docs.openclaw.ai/channels/imessage) (veraltetes imsg), [Microsoft Teams](https://docs.openclaw.ai/channels/msteams) (Erweiterung), [Matrix](https://docs.openclaw.ai/channels/matrix) (Erweiterung), [Zalo](https://docs.openclaw.ai/channels/zalo) (Erweiterung), [Zalo Personal](https://docs.openclaw.ai/channels/zalouser) (Erweiterung), [WebChat](https://docs.openclaw.ai/web/webchat).
- [Gruppen-Routing](https://docs.openclaw.ai/concepts/group-messages): Erwähnungs-Gating, Antwort-Tags, Kanalbasiertes Aufteilen und Routing. Kanalregeln: [Kanäle](https://docs.openclaw.ai/channels).

### Apps + Knoten

- [macOS App](https://docs.openclaw.ai/platforms/macos): Menüleisten-Kontrollfläche, [Sprachaktivierung](https://docs.openclaw.ai/nodes/voicewake)/PTT, [Sprechmodus](https://docs.openclaw.ai/nodes/talk) Overlay, [WebChat](https://docs.openclaw.ai/web/webchat), Debugging-Tools, [Remote-Gateway](https://docs.openclaw.ai/gateway/remote) Steuerung.
- [iOS-Knoten](https://docs.openclaw.ai/platforms/ios): [Canvas](https://docs.openclaw.ai/platforms/mac/canvas), [Sprachaktivierung](https://docs.openclaw.ai/nodes/voicewake), [Sprechmodus](https://docs.openclaw.ai/nodes/talk), Kamera, Bildschirmaufnahme, Bonjour-Verknüpfung.
- [Android-Knoten](https://docs.openclaw.ai/platforms/android): [Canvas](https://docs.openclaw.ai/platforms/mac/canvas), [Sprechmodus](https://docs.openclaw.ai/nodes/talk), Kamera, Bildschirmaufnahme, optionale SMS-Funktion.
- [macOS-Knotenmodus](https://docs.openclaw.ai/nodes): Systemausführung/Benachrichtigungen + Canvas/Kamera-Zugriff.

### Tools + Automatisierung

- [Browser-Steuerung](https://docs.openclaw.ai/tools/browser): Dedizierter openclaw Chrome/Chromium, Screenshots, Aktionen, Uploads, Profile.
- [Canvas](https://docs.openclaw.ai/platforms/mac/canvas): [A2UI](https://docs.openclaw.ai/platforms/mac/canvas#canvas-a2ui) Push/Reset, Bewertung, Screenshots.
- [Knoten](https://docs.openclaw.ai/nodes): Kamera-Screenshots/Aufnahmen, Bildschirmaufnahme, [Standortabruf](https://docs.openclaw.ai/nodes/location-command), Benachrichtigungen
- [Cron-Jobs + Wecker](https://docs.openclaw.ai/automation/cron-jobs); [Webhooks](https://docs.openclaw.ai/automation/webhook); [Gmail Pub/Sub](https://docs.openclaw.ai/automation/gmail-pubsub).
- [Fähigkeiten-Plattform](https://docs.openclaw.ai/tools/skills): Gebündelte, verwaltete und Arbeitsbereich-Fähigkeiten mit Installationsbeschränkungen und Benutzeroberfläche.

### Betrieb + Sicherheit

- [Kanal-Routing](https://docs.openclaw.ai/concepts/channel-routing), [Wiederholungsstrategie](https://docs.openclaw.ai/concepts/retry) und [Streaming/Aufteilung](https://docs.openclaw.ai/concepts/streaming).
- [Anwesenheit](https://docs.openclaw.ai/concepts/presence), [Tippindikatoren](https://docs.openclaw.ai/concepts/typing-indicators) und [Nutzungsverfolgung](https://docs.openclaw.ai/concepts/usage-tracking).
- [Modelle](https://docs.openclaw.ai/concepts/models), [Modell-Ausfallsicherheit](https://docs.openclaw.ai/concepts/model-failover) und [Sitzungen](https://docs.openclaw.ai/concepts/session-pruning).
- [Sicherheit](https://docs.openclaw.ai/gateway/security) und [Problembehandlung](https://docs.openclaw.ai/channels/troubleshooting).

### Betrieb + Paketierung

- [Steuerungsoberfläche](https://docs.openclaw.ai/web) + [WebChat](https://docs.openclaw.ai/web/webchat) direkt vom Gateway bereitgestellt.
- [Tailscale Serve/Funnel](https://docs.openclaw.ai/gateway/tailscale) oder [SSH-Tunnel](https://docs.openclaw.ai/gateway/remote) mit Token/Passwort-Authentifizierung
- [Nix-Modus](https://docs.openclaw.ai/install/nix) unterstützt deklarative Konfiguration; Docker-basierte Installation
- [Sicherheit](https://docs.openclaw.ai/gateway/doctor) Fallback, [Protokollierung](https://docs.openclaw.ai/logging).

## Funktionsweise (kurze Erklärung)

```
WhatsApp / Telegram / Slack / Discord / Google Chat / Signal / iMessage / BlueBubbles / Microsoft Teams / Matrix / Zalo / Zalo Personal / WebChat
               │
               ▼
┌───────────────────────────────┐
│            Gateway            │
│       (control plane)         │
│     ws://127.0.0.1:18789      │
└──────────────┬────────────────┘
               │
               ├─ Pi agent (RPC)
               ├─ CLI (openclaw …)
               ├─ WebChat UI
               ├─ macOS app
               └─ iOS / Android nodes
```

## Wesentliche Subsysteme

- **[Gateway WebSocket-Kommunikation](https://docs.openclaw.ai/concepts/architecture)** — Einheitliche WS-Kontrollfläche für Clients, Tools und Ereignisse (und Operationen: [Gateway-Handbuch](https://docs.openclaw.ai/gateway)).
- **[Tailscale-Freigabe](https://docs.openclaw.ai/gateway/tailscale)** — Serve/Funnel + WS für Gateway-Dashboard (Fernzugriff: [Fernzugriff](https://docs.openclaw.ai/gateway/remote)).
- **[Browser-Steuerung](https://docs.openclaw.ai/tools/browser)** — CDP-gesteuerter openclaw-verwalteter Chrome/Chromium.
- **[Canvas + A2UI](https://docs.openclaw.ai/platforms/mac/canvas)** — Agentengeführter visueller Arbeitsbereich (A2UI-Host: [Canvas/A2UI](https://docs.openclaw.ai/platforms/mac/canvas#canvas-a2ui)).
- **[Sprachaktivierung](https://docs.openclaw.ai/nodes/voicewake) + [Sprechmodus](https://docs.openclaw.ai/nodes/talk)** — Dauerhaft aktive Sprachfunktion für kontinuierliches Gespräch.
- **[Knoten](https://docs.openclaw.ai/nodes)** — Canvas, Kamera-Screenshots/Aufnahmen, Bildschirmaufnahme, `location.get`, Benachrichtigungen sowie macOS-spezifische Funktionen `system.run`/`system.notify`.

## Tailscale-Zugriff (Gateway-Kontrollpanel)

OpenClaw kann Tailscale automatisch konfigurieren **Serve** (nur Tailnet) oder **Funnel** (öffentlich), während das Gateway weiterhin an die Loopback-Schnittstelle gebunden bleibt. Konfigurieren Sie `gateway.tailscale.mode`:

- `off`: Keine Tailscale-Automatisierung (Standard).
- `serve`: Nur Tailnet-HTTPS über `tailscale serve` (standardmäßig mit Tailscale-Headers).
- `funnel`: Öffentliches HTTPS über `tailscale funnel` (benötigt gemeinsames Passwort für Authentifizierung).

Erläuterungen:

- `gateway.bind` muss `loopback` bleiben, wenn Serve/Funnel aktiviert ist (OpenClaw erzwingt dies).
- Erzwingen Sie ein Server-Passwort durch Festlegen von `gateway.auth.mode: "password"` oder `gateway.auth.allowTailscale: false`.
- Verweigert die Ausführung, es sei denn, `gateway.auth.mode: "password"` wurde bereits festgelegt.
- Optional `gateway.tailscale.resetOnExit` hebt Serve/Funnel-Operation beim Herunterfahren auf.

Details: [Tailscale-Leitfaden](https://docs.openclaw.ai/gateway/tailscale) · [Webseite](https://docs.openclaw.ai/web)

## Remote-Gateway (bessere Linux-Kompatibilität)

Es ist völlig in Ordnung, das Gateway auf einer kleinen Linux-Instanz auszuführen. Clients (macOS App, CLI, WebChat) können sich über **Tailscale Serve/Funnel** oder **SSH-Tunnel** verbinden, und Sie können nach Bedarf Geräteknoten (macOS/iOS/Android) koppeln, um gerätespezifische Vorgänge auszuführen.

- **Gateway-Host** führt standardmäßig Tools aus und stellt Kanalverbindungen her.
- **Geräteknoten** führen gerätespezifische Vorgänge (z.B. `system.run`, Kamera, Bildschirmaufnahme, Benachrichtigungen) über `node.invoke` aus.
  Kurz gesagt: Ausführung erfolgt dort, wo sich das Gateway befindet; Geräteoperationen erfolgen dort, wo sich das Gerät befindet.

Details: [Fernzugriff](https://docs.openclaw.ai/gateway/remote) · [Knoten](https://docs.openclaw.ai/nodes) · [Sicherheit](https://docs.openclaw.ai/gateway/security)

## macOS-Berechtigungen über Gateway-Protokoll

Die macOS-App kann im **Knotenmodus** laufen und ihre Funktionen und Berechtigungszuordnungen über das Gateway-WebSocket (`node.list` / `node.describe`) bekanntgeben. Clients können dann lokale Vorgänge über `node.invoke` ausführen:

- `system.run` führt lokale Befehle aus und gibt stdout/stderr/Exit-Code zurück; setzen Sie `needsScreenRecording: true` für Bildschirmaufnahme-Berechtigung (ansonsten erhalten Sie den Fehler `PERMISSION_MISSING`).
- `system.notify` sendet eine Benachrichtigung an den Benutzer, schlägt fehl, wenn die Benachrichtigung abgelehnt wird.
- `canvas.*`, `camera.*`, `screen.record` und `location.get` werden über `node.invoke` geleitet und folgen dem TCC-Berechtigungsstatus.

Erweiterte bash-Berechtigungen (Host-Berechtigungen) und macOS TCC sind separat:

- Verwenden Sie `/elevated on|off`, um den Zugriff mit erhöhten Rechten pro Sitzung zu wechseln, wenn aktiviert + zur Genehmigungsliste hinzugefügt.
- Das Gateway persistiert jeden Sitzungs-Wechsel über (WS-Methoden) sowie `sessions.patch`, `thinkingLevel`, `verboseLevel`, `model`, `sendPolicy` und `groupActivation`.

Details: [Knoten](https://docs.openclaw.ai/nodes) · [macOS App](https://docs.openclaw.ai/platforms/macos) · [Gateway-Protokoll](https://docs.openclaw.ai/concepts/architecture)

## Agent-zu-Agent-Kommunikation (sessions_*-Tools)

- Mit dieser Funktion können Sie zwischen Sitzungen zusammenarbeiten, ohne zwischen Chat-Oberflächen wechseln zu müssen.
- `sessions_list` — Aktive Sitzungen (Agenten) und deren Metadaten entdecken.
- `sessions_history` — Protokollierte Sitzungsprotokolle abrufen.
- `sessions_send` — Eine Nachricht an eine andere Sitzung senden; optionale Antwort-Ping-Pong + Ankündigungs-Schritte (REPLY_SKIP, ANNOUNCE_SKIP).

Details: [Sitzungs-Tools](https://docs.openclaw.ai/concepts/session-tool)

## Fähigkeiten-Registrierung (ClawHub)

ClawHub ist ein minimalistisches Fähigkeiten-Registrierungssystem. Nach Aktivierung von ClawHub kann der Agent automatisch nach Fähigkeiten suchen und bei Bedarf neue Fähigkeiten hinzufügen.

[ClawHub](https://clawhub.com)

## Chat-Befehle

Senden Sie diese über WhatsApp/Telegram/Slack/Google Chat/Microsoft Teams/WebChat (Gruppenbefehle nur für Gruppenadministratoren):

- `/status` — Kompakter Sitzungsstatus (Modell + Tokens, und Kosten falls verfügbar)
- `/new` oder `/reset` — Sitzung zurücksetzen
- `/compact` — Kompakter Sitzungskontext (Zusammenfassung)
- `/think <level>` — off|minimal|low|medium|high|xhigh (nur GPT-5.2 + Codex-Modelle)
- `/verbose on|off`
- `/usage off|tokens|full` — Token-Nutzung bei jeder Antwort
- `/restart` — Gateway neu starten (nur Gruppenadministratoren)
- `/activation mention|always` — Gruppenaktivierungsschalter (nur für Gruppen)

## Anwendungen (optional)

Das Gateway selbst bietet eine hervorragende Erfahrung. Alle Anwendungen sind optional und fügen zusätzliche Funktionen hinzu.

Wenn Sie planen, Begleit-Anwendungen zu erstellen/auszuführen, befolgen Sie bitte die folgenden Plattform-Handbücher.

### macOS (OpenClaw.app) (optional)

- Menüleisten-Steuerung für Gateway und Integritätsprüfungen.
- Sprachaktivierung + One-Tap Talk-Overlay.
- WebChat + Debugging-Tools.
- Fernsteuerung des Gateways über SSH.

Hinweis: Für signierte Builds ist macOS-Berechtigung erforderlich, damit sie nach dem Neuaufbau erhalten bleiben (siehe `docs/mac/permissions.md`).

### iOS-Knoten (optional)

- Paarung als Knoten über den Bridge.
- Weiterleitung von Sprachauslösern + Canvas-Oberfläche.
- Steuerung über `openclaw nodes …`.

Handbuch: [iOS-Verbindung](https://docs.openclaw.ai/platforms/ios).

### Android-Knoten (optional)

- Pairing über denselben Bridge + Pairing-Workflow wie iOS.
- Erlauben Sie Canvas-, Kamera- und Bildschirmaufnahmen-Befehle.
- Handbuch: [Android-Verbindung](https://docs.openclaw.ai/platforms/android).

## Agent-Arbeitsbereich + Fähigkeiten

- Arbeitsbereich-Stammverzeichnis: `~/.openclaw/workspace` (konfigurierbar über `agents.defaults.workspace`).
- Eingespeiste Prompt-Dateien: `AGENTS.md`, `SOUL.md`, `TOOLS.md`.
- Fähigkeiten: `~/.openclaw/workspace/skills/<skill>/SKILL.md`.

## Konfiguration

Standardkonfigurationspfad: `~/.openclaw/config.json`.

## Sicherheitsmodus (wichtig)

- **Standardmäßig:** Tools werden auf dem Host im Haupt-Sitzungsmodus ausgeführt, daher wenn Sie alleine benutzen, hat der Agent vollen Zugriff.
- **Sicherheit für Gruppen-/Kanal-Sitzungen:** Führen Sie jeden Sitzung als Sandkasten innerhalb von Docker mit der Einstellung `agents.defaults.sandbox.mode: "non-main"` als **Nicht-Haupt-Sitzungen** (Gruppen-/Kanal-Kanäle) aus. Führen Sie anschließend als bash-Sitzung innerhalb von Docker aus.
- **Standard-Sandbox:** Erlaubt die Ausführung von `bash`, `process`, `read`, `write`, `edit`, `sessions_list`, `sessions_history`, `sessions_send`, `sessions_spawn`. Verbietet `browser`, `canvas`, `nodes`, `cron`, `discord`, `gateway`.

Details: [Sicherheitsrichtlinien](https://docs.openclaw.ai/gateway/security) · [Docker + Sandbox](https://docs.openclaw.ai/install/docker) · [Sandbox-Konfiguration](https://docs.openclaw.ai/gateway/configuration)

## Dokumentation

Nach der Einrichtung benötigen Sie möglicherweise tiefere Referenzmaterialien.

- [Überprüfen Sie zuerst den Dokumentationsindex, um zu erfahren, wie man navigiert und wo Inhalte zu finden sind.](https://docs.openclaw.ai)
- [Lesen Sie die Architekturübersicht zu Gateway+Protokollmodell.](https://docs.openclaw.ai/concepts/architecture)
- [Nutzen Sie die vollständige Konfigurationsreferenz, wenn Sie alle Schlüssel und Beispiele benötigen.](https://docs.openclaw.ai/gateway/configuration)
- [Entwickler-Setup](https://docs.openclaw.ai/start/development)
- [Gateway-Protokollreferenz](https://docs.openclaw.ai/concepts/architecture)
- [CLI-Referenz](https://docs.openclaw.ai/tools/agent-send)

## Fortgeschrittene Dokumentation

- [Sicherheitsrichtlinien](https://docs.openclaw.ai/gateway/security)
- [Sicherheitsmodus](https://docs.openclaw.ai/gateway/security)
- [Docker + Sandbox](https://docs.openclaw.ai/install/docker)
- [Sandbox-Konfiguration](https://docs.openclaw.ai/gateway/configuration)
- [Gateway-Konfiguration](https://docs.openclaw.ai/gateway/configuration)
- [Kanal-Konfiguration](https://docs.openclaw.ai/channels)
- [Modell-Konfiguration](https://docs.openclaw.ai/concepts/models)

## Betrieb und Problembehandlung

- [Problembehandlung](https://docs.openclaw.ai/channels/troubleshooting)
- [Integritätsprüfungen](https://docs.openclaw.ai/gateway/doctor)
- [Gateway-Integritätsprüfungen](https://docs.openclaw.ai/gateway/doctor)
- [Kanal-Problembehandlung](https://docs.openclaw.ai/channels/troubleshooting)
- [Entwicklerversionen-Status](https://docs.openclaw.ai/install/development-channels)
- [Aktualisierungsanleitung](https://docs.openclaw.ai/install/updating)

## Tiefgehende Analyse

- [Gateway-Protokoll](https://docs.openclaw.ai/concepts/architecture)
- [Architekturübersicht](https://docs.openclaw.ai/concepts/architecture)
- [Session-Modell](https://docs.openclaw.ai/concepts/session)
- [Tool-Streaming](https://docs.openclaw.ai/concepts/streaming)
- [Block-Streaming](https://docs.openclaw.ai/concepts/streaming)
- [Kanal-Routing](https://docs.openclaw.ai/concepts/channel-routing)
- [Wiederholungsstrategie](https://docs.openclaw.ai/concepts/retry)
- [Streaming/Aufteilung](https://docs.openclaw.ai/concepts/streaming)

## Arbeitsbereich und Fähigkeiten

- [Fähigkeiten-Plattform](https://docs.openclaw.ai/tools/skills)
- [Fähigkeiten-Installation](https://docs.openclaw.ai/tools/skills)
- [Fähigkeiten-Management](https://docs.openclaw.ai/tools/skills)
- [Arbeitsbereich-Konfiguration](https://docs.openclaw.ai/tools/skills)
- [Fähigkeiten-Integration](https://docs.openclaw.ai/tools/skills)

## Plattform-Internas

- [macOS-Plattform](https://docs.openclaw.ai/platforms/macos)
- [iOS-Plattform](https://docs.openclaw.ai/platforms/ios)
- [Android-Plattform](https://docs.openclaw.ai/platforms/android)
- [Canvas-Implementierung](https://docs.openclaw.ai/platforms/mac/canvas)
- [A2UI-Host](https://docs.openclaw.ai/platforms/mac/canvas#canvas-a2ui)
- [Knoten-Implementierung](https://docs.openclaw.ai/nodes)

## Mail-Hooks

- [Gmail Pub/Sub](https://docs.openclaw.ai/automation/gmail-pubsub)
- [Mail-Integration](https://docs.openclaw.ai/automation/webhook)
- [Webhooks](https://docs.openclaw.ai/automation/webhook)

## Molty

Molty ist ein experimentelles Feature für Multi-Agenten-Interaktionen.

## Community

Siehe [CONTRIBUTING.md](CONTRIBUTING.md) für Leitlinien zur Mitarbeit, Betreuer und wie man PRs einreicht. PRs für AI/vibe-Coding sind willkommen! 🤖

Besonderer Dank an [Mario Zechner](https://mariozechner.at/) für die Unterstützung und die Entwicklung von
[pi-mono](https://github.com/badlogic/pi-mono).
Besonderer Dank an Adam Doppelt für die Entwicklung von lobster.bot.

Vielen Dank an alle Mitwirkenden:

<p align="left">
  <a href="https://github.com/steipete"><img src="https://avatars.githubusercontent.com/u/58493?v=4&s=48" width="48" height="48" alt="steipete" title="steipete"/></a> <a href="https://github.com/joshp123"><img src="https://avatars.githubusercontent.com/u/1497361?v=4&s=48" width="48" height="48" alt="joshp123" title="joshp123"/></a> <a href="https://github.com/cpojer"><img src="https://avatars.githubusercontent.com/u/13352?v=4&s=48" width="48" height="48" alt="cpojer" title="cpojer"/></a> <a href="https://github.com/mbelinky"><img src="https://avatars.githubusercontent.com/u/132747814?v=4&s=48" width="48" height="48" alt="Mariano Belinky" title="Mariano Belinky"/></a> <a href="https://github.com/plum-dawg"><img src="https://avatars.githubusercontent.com/u/5909950?v=4&s=48" width="48" height="48" alt="plum-dawg" title="plum-dawg"/></a> <a href="https://github.com/bohdanpodvirnyi"><img src="https://avatars.githubusercontent.com/u/31819391?v=4&s=48" width="48" height="48" alt="bohdanpodvirnyi" title="bohdanpodvirnyi"/></a> <a href="https://github.com/iHildy"><img src="https://avatars.githubusercontent.com/u/25069719?v=4&s=48" width="48" height="48" alt="iHildy" title="iHildy"/></a> <a href="https://github.com/jaydenfyi"><img src="https://avatars.githubusercontent.com/u/213395523?v=4&s=48" width="48" height="48" alt="jaydenfyi" title="jaydenfyi"/></a> <a href="https://github.com/joaohlisboa"><img src="https://avatars.githubusercontent.com/u/8200873?v=4&s=48" width="48" height="48" alt="joaohlisboa" title="joaohlisboa"/></a> <a href="https://github.com/mneves75"><img src="https://avatars.githubusercontent.com/u/2423436?v=4&s=48" width="48" height="48" alt="mneves75" title="mneves75"/></a>
  <a href="https://github.com/adam91holt"><img src="https://avatars.githubusercontent.com/u/9592417?v=4&s=48" width="48" height="48" alt="adam91holt" title="adam91holt"/></a> <a href="https://github.com/hougangdev"><img src="https://avatars.githubusercontent.com/u/105773686?v=4&s=48" width="48" height="48" alt="hougangdev" title="hougangdev"/></a> <a href="https://github.com/gumadeiras"><img src="https://avatars.githubusercontent.com/u/5599352?v=4&s=48" width="48" height="48" alt="gumadeiras" title="gumadeiras"/></a> <a href="https://github.com/shakkernerd"><img src="https://avatars.githubusercontent.com/u/165377636?v=4&s=48" width="48" height="48" alt="shakkernerd" title="shakkernerd"/></a> <a href="https://github.com/mteam88"><img src="https://avatars.githubusercontent.com/u/84196639?v=4&s=48" width="48" height="48" alt="mteam88" title="mteam88"/></a> <a href="https://github.com/hirefrank"><img src="https://avatars.githubusercontent.com/u/183158?v=4&s=48" width="48" height="48" alt="hirefrank" title="hirefrank"/></a> <a href="https://github.com/joeynyc"><img src="https://avatars.githubusercontent.com/u/17919866?v=4&s=48" width="48" height="48" alt="joeynyc" title="joeynyc"/></a> <a href="https://github.com/orlyjamie"><img src="https://avatars.githubusercontent.com/u/6668807?v=4&s=48" width="48" height="48" alt="orlyjamie" title="orlyjamie"/></a> <a href="https://github.com/dbhurley"><img src="https://avatars.githubusercontent.com/u/5251425?v=4&s=48" width="48" height="48" alt="dbhurley" title="dbhurley"/></a> <a href="https://github.com/omniwired"><img src="https://avatars.githubusercontent.com/u/322761?v=4&s=48" width="48" height="48" alt="Eng. Juan Combetto" title="Eng. Juan Combetto"/></a>
  <a href="https://github.com/parlarjb"><img src="https://avatars.githubusercontent.com/u/2484250?v=4&s=48" width="48" height="48" alt="parlarjb" title="parlarjb"/></a> <a href="https://github.com/davidknaack"><img src="https://avatars.githubusercontent.com/u/20398473?v=4&s=48" width="48" height="48" alt="davidknaack" title="davidknaack"/></a> <a href="https://github.com/jeffkowalski"><img src="https://avatars.githubusercontent.com/u/1094451?v=4&s=48" width="48" height="48" alt="jeffkowalski" title="jeffkowalski"/></a> <a href="https://github.com/alexander-lazarov"><img src="https://avatars.githubusercontent.com/u/7658574?v=4&s=48" width="48" height="48" alt="alexander-lazarov" title="alexander-lazarov"/></a> <a href="https://github.com/damphat"><img src="https://avatars.githubusercontent.com/u/125825?v=4&s=48" width="48" height="48" alt="damphat" title="damphat"/></a> <a href="https://github.com/groundedin"><img src="https://avatars.githubusercontent.com/u/15155604?v=4&s=48" width="48" height="48" alt="groundedin" title="groundedin"/></a> <a href="https://github.com/justinhamlett"><img src="https://avatars.githubusercontent.com/u/3242003?v=4&s=48" width="48" height="48" alt="justinhamlett" title="justinhamlett"/></a> <a href="https://github.com/kevincennis"><img src="https://avatars.githubusercontent.com/u/3960606?v=4&s=48" width="48" height="48" alt="kevincennis" title="kevincennis"/></a> <a href="https://github.com/nilp0inter"><img src="https://avatars.githubusercontent.com/u/1157367?v=4&s=48" width="48" height="48" alt="nilp0inter" title="nilp0inter"/></a> <a href="https://github.com/mkermani144"><img src="https://avatars.githubusercontent.com/u/35563852?v=4&s=48" width="48" height="48" alt="mkermani144" title="mkermani144"/></a>
  <a href="https://github.com/bradjones1"><img src="https://avatars.githubusercontent.com/u/127797?v=4&s=48" width="48" height="48" alt="bradjones1" title="bradjones1"/></a> <a href="https://github.com/damphat"><img src="https://avatars.githubusercontent.com/u/125825?v=4&s=48" width="48" height="48" alt="damphat" title="damphat"/></a> <a href="https://github.com/groundedin"><img src="https://avatars.githubusercontent.com/u/15155604?v=4&s=48" width="48" height="48" alt="groundedin" title="groundedin"/></a> <a href="https://github.com/justinhamlett"><img src="https://avatars.githubusercontent.com/u/3242003?v=4&s=48" width="48" height="48" alt="justinhamlett" title="justinhamlett"/></a> <a href="https://github.com/kevincennis"><img src="https://avatars.githubusercontent.com/u/3960606?v=4&s=48" width="48" height="48" alt="kevincennis" title="kevincennis"/></a> <a href="https://github.com/nilp0inter"><img src="https://avatars.githubusercontent.com/u/1157367?v=4&s=48" width="48" height="48" alt="nilp0inter" title="nilp0inter"/></a> <a href="https://github.com/mkermani144"><img src="https://avatars.githubusercontent.com/u/35563852?v=4&s=48" width="48" height="48" alt="mkermani144" title="mkermani144"/></a> <a href="https://github.com/wolfred"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="wolfred" title="wolfred"/></a>
  <a href="https://github.com/wstock"><img src="https://avatars.githubusercontent.com/u/1394687?v=4&s=48" width="48" height="48" alt="wstock" title="wstock"/></a> <a href="https://github.com/wytheme"><img src="https://avatars.githubusercontent.com/u/5009358?v=4&s=48" width="48" height="48" alt="wytheme" title="wytheme"/></a> <a href="https://github.com/YangHuang2280"><img src="https://avatars.githubusercontent.com/u/201681634?v=4&s=48" width="48" height="48" alt="YangHuang2280" title="YangHuang2280"/></a> <a href="https://github.com/yazinsai"><img src="https://avatars.githubusercontent.com/u/1846034?v=4&s=48" width="48" height="48" 
alt="yazinsai" title="yazinsai"/></a> <a href="https://github.com/yevhen"><img src="https://avatars.githubusercontent.com/u/107726?v=4&s=48" width="48" height="48" alt="yevhen" title="yevhen"/></a> <a href="https://github.com/YiWang24"><img src="https://avatars.githubusercontent.com/u/176262341?v=4&s=48" width="48" height="48" alt="YiWang24" title="YiWang24"/></a> <a href="https://github.com/search?q=ymat19"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="ymat19" title="ymat19"/></a> <a href="https://github.com/search?q=Zach%20Knickerbocker"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Zach Knickerbocker" title="Zach Knickerbocker"/></a> <a href="https://github.com/zackerthescar"><img src="https://avatars.githubusercontent.com/u/38077284?v=4&s=48" width="48" height="48" alt="zackerthescar" title="zackerthescar"/></a> <a href="https://github.com/0xJonHoldsCrypto"><img src="https://avatars.githubusercontent.com/u/81202085?v=4&s=48" width="48" height="48" alt="0xJonHoldsCrypto" title="0xJonHoldsCrypto"/></a>
  <a href="https://github.com/aaronn"><img src="https://avatars.githubusercontent.com/u/1653630?v=4&s=48" width="48" height="48" alt="aaronn" title="aaronn"/></a> <a href="https://github.com/Alphonse-arianee"><img src="https://avatars.githubusercontent.com/u/254457365?v=4&s=48" width="48" height="48" alt="Alphonse-arianee" title="Alphonse-arianee"/></a> <a href="https://github.com/atalovesyou"><img src="https://avatars.githubusercontent.com/u/3534502?v=4&s=48" width="48" height="48" alt="atalovesyou" title="atalovesyou"/></a> <a href="https://github.com/search?q=Azade"><img src="assets/avatar-placeholder.svg" width="48" height="48" 
alt="Azade" title="Azade"/></a> <a href="https://github.com/carlulsoe"><img src="https://avatars.githubusercontent.com/u/34673973?v=4&s=48" width="48" height="48" alt="carlulsoe" title="carlulsoe"/></a> <a href="https://github.com/search?q=ddyo"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="ddyo" title="ddyo"/></a> <a href="https://github.com/search?q=Erik"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Erik" title="Erik"/></a> <a 
href="https://github.com/jiulingyun"><img src="https://avatars.githubusercontent.com/u/126459548?v=4&s=48" width="48" height="48" alt="jiulingyun" title="jiulingyun"/></a> <a href="https://github.com/latitudeki5223"><img src="https://avatars.githubusercontent.com/u/119656367?v=4&s=48" width="48" height="48" alt="latitudeki5223" title="latitudeki5223"/></a> <a href="https://github.com/search?q=Manuel%20Maly"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Manuel Maly" title="Manuel Maly"/></a>
  <a href="https://github.com/search?q=Mourad%20Boustani"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Mourad Boustani" title="Mourad Boustani"/></a> <a href="https://github.com/odrobnik"><img src="https://avatars.githubusercontent.com/u/333270?v=4&s=48" width="48" height="48" alt="odrobnik" title="odrobnik"/></a> <a href="https://github.com/pcty-nextgen-ios-builder"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="pcty-nextgen-ios-builder" title="pcty-nextgen-ios-builder"/></a> <a href="https://github.com/search?q=Quentin"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Quentin" title="Quentin"/></a> <a href="https://github.com/search?q=Randy%20Torres"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Randy Torres" title="Randy Torres"/></a> <a href="https://github.com/rhjoh"><img src="https://avatars.githubusercontent.com/u/105699450?v=4&s=48" width="48" height="48" alt="rhjoh" title="rhjoh"/></a> <a href="https://github.com/search?q=Rolf%20Fredheim"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Rolf Fredheim" title="Rolf Fredheim"/></a> <a href="https://github.com/ronak-guliani"><img src="https://avatars.githubusercontent.com/u/23518228?v=4&s=48" width="48" height="48" alt="ronak-guliani" title="ronak-guliani"/></a> <a href="https://github.com/search?q=William%20Stock"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="William Stock" title="William Stock"/></a>
</p>
