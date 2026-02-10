# 🦞 OpenClaw — Assistant personnel IA

<p align="center">
    <picture>
        <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/openclaw/openclaw/main/docs/assets/openclaw-logo-text-dark.png">
        <img src="https://raw.githubusercontent.com/openclaw/openclaw/main/docs/assets/openclaw-logo-text.png" alt="OpenClaw" width="500">
    </picture>
</p>

<p align="center">
  <strong>Métamorphose ! Métamorphose !</strong>
</p>

<p align="center">
  <a href="https://github.com/openclaw/openclaw/actions/workflows/ci.yml?branch=main"><img src="https://img.shields.io/github/actions/workflow/status/openclaw/openclaw/ci.yml?branch=main&style=for-the-badge" alt="Statut CI"></a>
  <a href="https://github.com/openclaw/openclaw/releases"><img src="https://img.shields.io/github/v/release/openclaw/openclaw?include_prereleases&style=for-the-badge" alt="Version GitHub"></a>
  <a href="https://discord.gg/clawd"><img src="https://img.shields.io/discord/1456350064065904867?label=Discord&logo=discord&logoColor=white&color=5865F2&style=for-the-badge" alt="Discord"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge" alt="Licence MIT"></a>
</p>

**OpenClaw** est un assistant IA personnel qui s'exécute sur vos propres appareils. Il fournit un soutien via les canaux habituels (WhatsApp, Telegram, Slack, Discord, Google Chat, Signal, iMessage, Microsoft Teams, WebChat) ainsi que via des canaux étendus comme BlueBubbles, Matrix, Zalo et Zalo Personnel. Il prend en charge macOS/iOS/Android et peut afficher des interfaces Canvas en temps réel contrôlées par vous. La passerelle n'est qu'une plateforme de contrôle, le produit lui-même est le véritable assistant.
Si vous recherchez un assistant local, rapide et toujours en ligne pour un seul utilisateur, c'est exactement cela.

[Site officiel](https://openclaw.ai) · [Documentation officielle](https://docs.openclaw.ai) · [DeepWiki](https://deepwiki.com/openclaw/openclaw) · [Guide de démarrage](https://docs.openclaw.ai/start/getting-started) · [Mises à jour](https://docs.openclaw.ai/install/updating) · [Exemples](https://docs.openclaw.ai/start/showcase) · [FAQ](https://docs.openclaw.ai/start/faq) · [Assistant](https://docs.openclaw.ai/start/wizard) · [Nix](https://github.com/openclaw/nix-clawdbot) · [Docker](https://docs.openclaw.ai/install/docker) · [Discord](https://discord.gg/clawd)

Configuration recommandée : Exécutez l'assistant de configuration (`openclaw onboard`). Celui-ci vous guidera dans la configuration de la passerelle, de l'espace de travail, des canaux et des compétences. L'assistant en ligne de commande est la méthode recommandée et fonctionne sur **macOS, Linux et Windows (via WSL2 ; fortement recommandé)**.
Prend en charge npm, pnpm ou bun. Nouvelle installation ? Commencez ici : [Guide de démarrage](https://docs.openclaw.ai/start/getting-started)

**Abonnement (OAuth) :**

- **[Anthropic](https://www.anthropic.com/)** (Claude Pro/Max)
- **[OpenAI](https://openai.com/)** (ChatGPT/Codex)

Remarques sur les modèles : Bien que tous les modèles soient pris en charge, je recommande vivement **Anthropic Pro/Max (100/200) + Opus 4.6** pour de meilleures performances à long terme et une meilleure résistance aux interférences. Voir [Guide en ligne](https://docs.openclaw.ai/start/onboarding).

## Modèles (Sélection + Authentification)

- Configuration des modèles + CLI : [Modèles](https://docs.openclaw.ai/concepts/models)
- Profils d'authentification (OAuth vs clés API) + solution de secours : [Reprise de modèle](https://docs.openclaw.ai/concepts/model-failover)

## Installation

Environnement d'exécution : **Node ≥22**.

```bash
npm install -g openclaw@latest
# ou : pnpm add -g openclaw@latest

openclaw onboard --install-daemon
```

L'assistant installe le démon de la passerelle (service utilisateur launchd/systemd) pour le maintenir en cours d'exécution.

## Démarrage rapide (Résumé)

Environnement d'exécution : **Node ≥22**.

Guide complet pour débutants (authentification, appairage, canaux) : [Guide de démarrage](https://docs.openclaw.ai/start/getting-started)

```bash
openclaw onboard --install-daemon

openclaw gateway --port 18789 --verbose

# Envoyer un message
openclaw message send --to +1234567890 --message "Hello from OpenClaw"

# Discuter avec l'assistant (vous pouvez envoyer n'importe quel message aux canaux connectés : WhatsApp/Telegram/Slack/Discord/Google Chat/Signal/iMessage/BlueBubbles/Microsoft Teams/Matrix/Zalo/Zalo Personal/WebChat)
openclaw agent --message "Ship checklist" --thinking high
```

Comment mettre à jour ? [Guide de mise à jour](https://docs.openclaw.ai/install/updating) (exécutez `openclaw doctor`).

## Explication du statut de la version de développement

- **stable** : versions taguées (`vYYYY.M.D` ou `vYYYY.M.D-<patch>`), npm dist-tag `latest`.
- **beta** : versions préliminaires (`vYYYY.M.D-beta.N`), npm dist-tag `beta` (l'application macOS peut être absente).
- **dev** : tête mobile de `main`, npm dist-tag `dev` (lorsqu'elle est publiée).

Basculer (git + npm) : `openclaw update --channel stable|beta|dev`.
Détails : [Statut des versions de développement](https://docs.openclaw.ai/install/development-channels).

## Source (Développement)

`pnpm` est recommandé pour les builds à partir de la source. Bun est facultatif pour exécuter directement TypeScript.

```bash
git clone https://github.com/openclaw/openclaw.git
cd openclaw

pnpm install
pnpm ui:build # installe automatiquement les dépendances de l'interface utilisateur lors de la première exécution
pnpm build

pnpm openclaw onboard --install-daemon

# Boucle de développement (rechargement automatique lors des modifications TS)
pnpm gateway:watch
```

Remarque : `pnpm openclaw ...` exécute directement TypeScript (via `tsx`). `pnpm build` génère `dist/` pour exécuter/empaqueter le binaire `openclaw` via Node.

## Paramètres de sécurité par défaut (Autorisations DM)

OpenClaw se connecte à des plateformes de messagerie instantanée réelles. Considérez les messages privés reçus comme des **entrées non fiables**.

Guide de sécurité complet : [Guide de sécurité](https://docs.openclaw.ai/gateway/security)

Comportement par défaut pour Telegram/WhatsApp/Signal/iMessage/Microsoft Teams/Discord/Google Chat/Slack :

- **Appairage DM** (`dmPolicy="pairing"` / `channels.discord.dm.policy="pairing"` / `channels.slack.dm.policy="pairing"`) : Les expéditeurs inconnus reçoivent un court code d'appairage, le bot ne traite pas leurs messages.
- Approbation : `openclaw pairing approve <channel> <code>` (puis ajoute l'expéditeur au stockage local).
- Les messages privés entrants publics nécessitent une adhésion explicite : Définissez `dmPolicy="open"` et incluez `"*"` dans la liste d'autorisation des canaux (`allowFrom` / `channels.discord.dm.allowFrom` / `channels.slack.dm.allowFrom`).

Exécutez `openclaw doctor` pour découvrir les stratégies DM risquées/mal configurées.

## Points clés

- **[Passerelle prioritaire locale](https://docs.openclaw.ai/gateway)** — Plan de contrôle unique pour les sessions, canaux, outils et événements.
- **[Boîte de réception multi-canaux](https://docs.openclaw.ai/channels)** — WhatsApp, Telegram, Slack, Discord, Google Chat, Signal, BlueBubbles (iMessage), iMessage (hérité), Microsoft Teams, Matrix, Zalo, Zalo Personnel, WebChat, macOS, iOS/Android.
- **[Routage multi-agent](https://docs.openclaw.ai/gateway/configuration)** — Acheminement des canaux/contes/pairs entrants vers des agents isolés (espace de travail + session par agent).
- **[Activation vocale](https://docs.openclaw.ai/nodes/voicewake) + [Mode conversation](https://docs.openclaw.ai/nodes/talk)** — Fonctionnalité vocale toujours active d'ElevenLabs pour macOS/iOS/Android.
- **[Canvas en live](https://docs.openclaw.ai/platforms/mac/canvas)** — Espace de travail visuel piloté par l'agent utilisant [A2UI](https://docs.openclaw.ai/platforms/mac/canvas#canvas-a2ui).
- **[Outils de premier plan](https://docs.openclaw.ai/tools)** — Navigateur, Canvas, Nœuds, tâches Cron, Sessions et opérations Discord/Slack.
- **[Applications compagnon](https://docs.openclaw.ai/platforms/macos)** — Application barre de menus macOS + [Nœuds](https://docs.openclaw.ai/nodes) iOS/Android.
- **[Assistant](https://docs.openclaw.ai/start/wizard) + [Compétences](https://docs.openclaw.ai/tools/skills)** — Configuration assistée avec compétences groupées/gérées/espace de travail.

## Historique des étoiles

[![Graphique historique des étoiles](https://api.star-history.com/svg?repos=openclaw/openclaw&type=date&legend=top-left)](https://www.star-history.com/#openclaw/openclaw&type=date&legend=top-left)

## Ce que nous avons fait jusqu'à présent

### Plateforme centrale

- [Panneau de contrôle de la passerelle](https://docs.openclaw.ai/gateway) comprenant les sessions, l'état, la configuration, les tâches cron, les webhooks, [Interface utilisateur interactive](https://docs.openclaw.ai/web) et [Hôte Canvas](https://docs.openclaw.ai/platforms/mac/canvas#canvas-a2ui).
- [Interface CLI](https://docs.openclaw.ai/tools/agent-send) : Passerelle, Agent, Envoi, [Assistant](https://docs.openclaw.ai/start/wizard) et [Sécurité](https://docs.openclaw.ai/gateway/doctor).
- [Runtime Agent Pi](https://docs.openclaw.ai/concepts/agent) avec modèle RPC, prenant en charge le streaming d'outils et le streaming par morceaux.
- [Modèle de session](https://docs.openclaw.ai/concepts/session) : `main` pour discussion directe, isolement des groupes, mode activation, mode file d'attente, réponses. Règles de groupe : [Groupes](https://docs.openclaw.ai/concepts/groups).
- [Canaux multimédia](https://docs.openclaw.ai/nodes/images) : Images/Audio/Vidéo, hooks de transcription, limitations de taille, cycle de vie des fichiers temporaires. Détails audio : [Audio](https://docs.openclaw.ai/nodes/audio).

### Canaux

- [Canaux](https://docs.openclaw.ai/channels) : [WhatsApp](https://docs.openclaw.ai/channels/whatsapp) (Baileys), [Telegram](https://docs.openclaw.ai/channels/telegram) (grammY), [Slack](https://docs.openclaw.ai/channels/slack) (Bolt), [Discord](https://docs.openclaw.ai/channels/discord) (discord.js), [Google Chat](https://docs.openclaw.ai/channels/googlechat) (API Chat), [Signal](https://docs.openclaw.ai/channels/signal) (signal-cli), [BlueBubbles](https://docs.openclaw.ai/channels/bluebubbles) (iMessage, recommandé), [iMessage](https://docs.openclaw.ai/channels/imessage) (imsg obsolète), [Microsoft Teams](https://docs.openclaw.ai/channels/msteams) (extension), [Matrix](https://docs.openclaw.ai/channels/matrix) (extension), [Zalo](https://docs.openclaw.ai/channels/zalo) (extension), [Zalo Personnel](https://docs.openclaw.ai/channels/zalouser) (extension), [WebChat](https://docs.openclaw.ai/web/webchat).
- [Routage de groupe](https://docs.openclaw.ai/concepts/group-messages) : Contrôle par mention, balises de réponse, fractionnement et routage par canal. Règles de canal : [Canaux](https://docs.openclaw.ai/channels).

### Applications + Nœuds

- [Application macOS](https://docs.openclaw.ai/platforms/macos) : Panneau de contrôle de la barre de menus, [Activation vocale](https://docs.openclaw.ai/nodes/voicewake)/PTT, superposition [Mode conversation](https://docs.openclaw.ai/nodes/talk), [WebChat](https://docs.openclaw.ai/web/webchat), outils de débogage, contrôle [Passerelle distante](https://docs.openclaw.ai/gateway/remote).
- [Nœuds iOS](https://docs.openclaw.ai/platforms/ios) : [Canvas](https://docs.openclaw.ai/platforms/mac/canvas), [Activation vocale](https://docs.openclaw.ai/nodes/voicewake), [Mode conversation](https://docs.openclaw.ai/nodes/talk), caméra, enregistrement d'écran, appairage Bonjour.
- [Nœuds Android](https://docs.openclaw.ai/platforms/android) : [Canvas](https://docs.openclaw.ai/platforms/mac/canvas), [Mode conversation](https://docs.openclaw.ai/nodes/talk), caméra, enregistrement d'écran, fonctionnalité SMS facultative.
- [Mode nœud macOS](https://docs.openclaw.ai/nodes) : Exécution système/notifications + exposition de la caméra/canvas.

### Outils + Automatisation

- [Contrôle du navigateur](https://docs.openclaw.ai/tools/browser) : Chrome/Chromium dédié openclaw, captures d'écran, actions, téléchargements, profils.
- [Canvas](https://docs.openclaw.ai/platforms/mac/canvas) : [A2UI](https://docs.openclaw.ai/platforms/mac/canvas#canvas-a2ui) Push/Réinitialisation, évaluation, captures d'écran.
- [Nœuds](https://docs.openclaw.ai/nodes) : Captures/vidéos de la caméra, enregistrement d'écran, [obtention de la localisation](https://docs.openclaw.ai/nodes/location-command), notifications
- [Tâches Cron + Activation](https://docs.openclaw.ai/automation/cron-jobs) ; [webhooks](https://docs.openclaw.ai/automation/webhook) ; [Gmail Pub/Sub](https://docs.openclaw.ai/automation/gmail-pubsub).
- [Plateforme de compétences](https://docs.openclaw.ai/tools/skills) : Compétences groupées, gérées et d'espace de travail avec restrictions d'installation et interface utilisateur.

### Exploitation + Sécurité

- [Routage de canal](https://docs.openclaw.ai/concepts/channel-routing), [Stratégie de nouvelle tentative](https://docs.openclaw.ai/concepts/retry) et [Streaming/traitement par blocs](https://docs.openclaw.ai/concepts/streaming).
- [Présence](https://docs.openclaw.ai/concepts/presence), [Indicateurs de frappe](https://docs.openclaw.ai/concepts/typing-indicators) et [Suivi d'utilisation](https://docs.openclaw.ai/concepts/usage-tracking).
- [Modèles](https://docs.openclaw.ai/concepts/models), [Reprise de modèle](https://docs.openclaw.ai/concepts/model-failover) et [Sessions](https://docs.openclaw.ai/concepts/session-pruning).
- [Sécurité](https://docs.openclaw.ai/gateway/security) et [Dépannage](https://docs.openclaw.ai/channels/troubleshooting).

### Exploitation + Empaquetage

- [Interface de contrôle](https://docs.openclaw.ai/web) + [WebChat](https://docs.openclaw.ai/web/webchat) servis directement par la passerelle.
- [Tailscale Serve/Funnel](https://docs.openclaw.ai/gateway/tailscale) ou [Tunnels SSH](https://docs.openclaw.ai/gateway/remote) avec authentification par jeton/mot de passe
- [Mode Nix](https://docs.openclaw.ai/install/nix) prend en charge la configuration déclarative ; installation basée sur [Docker](https://docs.openclaw.ai/install/docker)
- [Sécurité](https://docs.openclaw.ai/gateway/doctor) solution de repli, [Journalisation](https://docs.openclaw.ai/logging).

## Comment ça marche (résumé)

```
WhatsApp / Telegram / Slack / Discord / Google Chat / Signal / iMessage / BlueBubbles / Microsoft Teams / Matrix / Zalo / Zalo Personnel / WebChat
               │
               ▼
┌───────────────────────────────┐
│            Passerelle          │
│       (plan de contrôle)       │
│     ws://127.0.0.1:18789      │
└──────────────┬────────────────┘
               │
               ├─ agent Pi (RPC)
               ├─ CLI (openclaw …)
               ├─ Interface WebChat
               ├─ application macOS
               └─ nœuds iOS / Android
```

## Sous-systèmes clés

- **[Communication WebSocket de la passerelle](https://docs.openclaw.ai/concepts/architecture)** — Plan de contrôle WS unique pour les clients, outils et événements (et opérations : [Manuel de la passerelle](https://docs.openclaw.ai/gateway)).
- **[Exposition Tailscale](https://docs.openclaw.ai/gateway/tailscale)** — Serve/Funnel + WS pour le tableau de bord de la passerelle (accès distant : [Accès distant](https://docs.openclaw.ai/gateway/remote)).
- **[Contrôle du navigateur](https://docs.openclaw.ai/tools/browser)** — Chrome/Chromium géré par openclaw avec contrôle CDP.
- **[Canvas + A2UI](https://docs.openclaw.ai/platforms/mac/canvas)** — Espace de travail visuel piloté par l'agent (hôte A2UI : [Canvas/A2UI](https://docs.openclaw.ai/platforms/mac/canvas#canvas-a2ui)).
- **[Activation vocale](https://docs.openclaw.ai/nodes/voicewake) + [Mode conversation](https://docs.openclaw.ai/nodes/talk)** — Fonctionnalité vocale toujours active pour conversations continues.
- **[Nœuds](https://docs.openclaw.ai/nodes)** — Canvas, captures/vidéos de la caméra, enregistrement d'écran, `location.get`, notifications, ainsi que les fonctions spécifiques à macOS `system.run`/`system.notify`.

## Accès Tailscale (panneau de contrôle de la passerelle)

OpenClaw peut configurer automatiquement Tailscale **Serve** (seulement tailnet) ou **Funnel** (public) tout en maintenant la liaison de la passerelle à l'interface de bouclage. Configurez `gateway.tailscale.mode` :

- `off` : Aucune automatisation Tailscale (par défaut).
- `serve` : HTTPS seulement tailnet via `tailscale serve` (utilise par défaut les en-têtes Tailscale).
- `funnel` : HTTPS public via `tailscale funnel` (nécessite une authentification par mot de passe partagé).

Explications :

- `gateway.bind` doit rester `loopback` lorsque Serve/Funnel est activé (OpenClaw applique cette règle).
- Forcez un mot de passe serveur en définissant `gateway.auth.mode: "password"` ou `gateway.auth.allowTailscale: false`.
- Refuse l'exécution sauf si `gateway.auth.mode: "password"` a déjà été défini.
- Optionnel `gateway.tailscale.resetOnExit` annule les opérations Serve/Funnel lors de l'arrêt.

Détails : [Guide Tailscale](https://docs.openclaw.ai/gateway/tailscale) · [Page Web](https://docs.openclaw.ai/web)

## Passerelle distante (meilleure compatibilité Linux)

Il est tout à fait acceptable d'exécuter la passerelle sur une petite instance Linux. Les clients (application macOS, CLI, WebChat) peuvent se connecter via **Tailscale Serve/Funnel** ou **tunnels SSH**, et vous pouvez toujours associer des nœuds d'appareil (macOS/iOS/Android) selon vos besoins pour effectuer des opérations locales.

- **Hôte de la passerelle** exécute normalement les outils et établit les connexions aux canaux.
- **Nœuds d'appareil** exécutent des opérations locales (comme `system.run`, caméra, enregistrement d'écran, notifications) via `node.invoke`.
  En résumé : l'exécution se fait là où se trouve la passerelle ; les opérations de l'appareil se font là où se trouve l'appareil.

Détails : [Accès distant](https://docs.openclaw.ai/gateway/remote) · [Nœuds](https://docs.openclaw.ai/nodes) · [Sécurité](https://docs.openclaw.ai/gateway/security)

## Autorisations macOS via protocole de passerelle

L'application macOS peut fonctionner en **mode nœud** et diffuser ses capacités et mappages d'autorisations via le WebSocket de la passerelle (`node.list` / `node.describe`). Les clients peuvent ensuite exécuter des opérations locales via `node.invoke` :

- `system.run` exécute des commandes locales et renvoie stdout/stderr/code de sortie ; définissez `needsScreenRecording: true` pour les autorisations d'enregistrement d'écran (sinon vous obtiendrez l'erreur `PERMISSION_MISSING`).
- `system.notify` envoie une notification à l'utilisateur, échoue si la notification est refusée.
- `canvas.*`, `camera.*`, `screen.record` et `location.get` sont acheminés via `node.invoke` et suivent l'état des autorisations TCC.

Les autorisations bash élevées (autorisations hôtes) et TCC macOS sont séparées :

- Utilisez `/elevated on|off` pour basculer l'accès privilégié par session lorsque activé + ajouté à la liste d'autorisation.
- La passerelle rend persistants les changements de chaque session via (méthodes WS) ainsi que `sessions.patch`, `thinkingLevel`, `verboseLevel`, `model`, `sendPolicy` et `groupActivation`.

Détails : [Nœuds](https://docs.openclaw.ai/nodes) · [Application macOS](https://docs.openclaw.ai/platforms/macos) · [Protocole de la passerelle](https://docs.openclaw.ai/concepts/architecture)

## Agent à agent (outils sessions_*)

- Cette fonctionnalité vous permet de coordonner le travail entre les sessions sans basculer entre les interfaces de discussion.
- `sessions_list` — Découvrir les sessions (agents) actives et leurs métadonnées.
- `sessions_history` — Récupérer les journaux de session enregistrés.
- `sessions_send` — Envoyer un message à une autre session ; étapes de réponse ping-pong + annonce facultatives (REPLY_SKIP, ANNOUNCE_SKIP).

Détails : [Outils de session](https://docs.openclaw.ai/concepts/session-tool)

## Enregistrement de compétences (ClawHub)

ClawHub est un système d'enregistrement de compétences minimaliste. Une fois ClawHub activé, l'agent peut rechercher automatiquement des compétences et en ajouter de nouvelles selon les besoins.

[ClawHub](https://clawhub.com)

## Commandes de discussion

Envoyez celles-ci via WhatsApp/Telegram/Slack/Google Chat/Microsoft Teams/WebChat (commandes de groupe uniquement pour les administrateurs de groupe) :

- `/status` — État de session compact (modèle + jetons, et coûts si disponibles)
- `/new` ou `/reset` — Réinitialiser la session
- `/compact` — Contexte de session compact (résumé)
- `/think <level>` — off|minimal|low|medium|high|xhigh (modèles GPT-5.2 + Codex uniquement)
- `/verbose on|off`
- `/usage off|tokens|full` — Utilisation des jetons à chaque réponse
- `/restart` — Redémarrer la passerelle (administrateurs de groupe uniquement)
- `/activation mention|always` — Interrupteur d'activation de groupe (pour groupes uniquement)

## Applications (facultatif)

La passerelle elle-même offre une excellente expérience. Toutes les applications sont facultatives et ajoutent des fonctionnalités supplémentaires.

Si vous prévoyez de créer/exécuter des applications compagnon, veuillez suivre les manuels de plateforme ci-dessous.

### macOS (OpenClaw.app) (facultatif)

- Contrôle de la barre de menus pour la passerelle et l'intégrité.
- Activation vocale + superposition Talk en un clic.
- WebChat + outils de débogage.
- Contrôle de la passerelle distante via SSH.

Remarque : Des builds signés sont requis pour les autorisations macOS afin qu'elles persistent après reconstruction (voir `docs/mac/permissions.md`).

### Nœuds iOS (facultatif)

- Jumelage en tant que nœud via le pont.
- Transmission des déclencheurs vocaux + surface Canvas.
- Contrôle via `openclaw nodes …`.

Manuel : [Connexion iOS](https://docs.openclaw.ai/platforms/ios).

### Nœuds Android (facultatif)

- Appairage via le même flux de pont + appairage que iOS.
- Autoriser les commandes Canvas, Caméra et Capture d'écran.
- Manuel : [Connexion Android](https://docs.openclaw.ai/platforms/android).

## Espace de travail de l'agent + Compétences

- Répertoire racine de l'espace de travail : `~/.openclaw/workspace` (configurable via `agents.defaults.workspace`).
- Fichiers de prompt injectés : `AGENTS.md`, `SOUL.md`, `TOOLS.md`.
- Compétences : `~/.openclaw/workspace/skills/<skill>/SKILL.md`.

## Configuration

Chemin de configuration par défaut : `~/.openclaw/config.json`.

## Mode sécurisé (important)

- **Par défaut :** Les outils s'exécutent sur l'hôte en tant que session principale, donc si vous êtes seul à l'utiliser, l'agent dispose d'un accès complet.
- **Sécurité pour les canaux/groupes :** Exécutez chaque session en bac à sable dans Docker avec `agents.defaults.sandbox.mode: "non-main"` en tant que **sessions non principales** (canaux de groupe/canal). Exécutez ensuite en tant que session bash dans Docker.
- **Bac à sable par défaut :** Autorise l'exécution de `bash`, `process`, `read`, `write`, `edit`, `sessions_list`, `sessions_history`, `sessions_send`, `sessions_spawn`. Interdit `browser`, `canvas`, `nodes`, `cron`, `discord`, `gateway`.

Détails : [Lignes directrices de sécurité](https://docs.openclaw.ai/gateway/security) · [Docker + Bac à sable](https://docs.openclaw.ai/install/docker) · [Configuration du bac à sable](https://docs.openclaw.ai/gateway/configuration)

## Documentation

Après la configuration, vous aurez peut-être besoin de matériaux de référence plus approfondis.

- [Consultez d'abord l'index de documentation pour apprendre à naviguer et où trouver le contenu.](https://docs.openclaw.ai)
- [Lisez la vue d'ensemble de l'architecture modèle passerelle+protocole.](https://docs.openclaw.ai/concepts/architecture)
- [Utilisez la référence complète de configuration si vous avez besoin de toutes les clés et exemples.](https://docs.openclaw.ai/gateway/configuration)
- [Configuration du développeur](https://docs.openclaw.ai/start/development)
- [Référence du protocole de la passerelle](https://docs.openclaw.ai/concepts/architecture)
- [Référence CLI](https://docs.openclaw.ai/tools/agent-send)

## Documentation avancée

- [Lignes directrices de sécurité](https://docs.openclaw.ai/gateway/security)
- [Mode sécurisé](https://docs.openclaw.ai/gateway/security)
- [Docker + Bac à sable](https://docs.openclaw.ai/install/docker)
- [Configuration du bac à sable](https://docs.openclaw.ai/gateway/configuration)
- [Configuration de la passerelle](https://docs.openclaw.ai/gateway/configuration)
- [Configuration des canaux](https://docs.openclaw.ai/channels)
- [Configuration des modèles](https://docs.openclaw.ai/concepts/models)

## Exploitation et dépannage

- [Dépannage](https://docs.openclaw.ai/channels/troubleshooting)
- [Contrôles d'intégrité](https://docs.openclaw.ai/gateway/doctor)
- [Contrôles d'intégrité de la passerelle](https://docs.openclaw.ai/gateway/doctor)
- [Dépannage des canaux](https://docs.openclaw.ai/channels/troubleshooting)
- [Statut des versions de développement](https://docs.openclaw.ai/install/development-channels)
- [Guide de mise à jour](https://docs.openclaw.ai/install/updating)

## Exploration approfondie

- [Protocole de la passerelle](https://docs.openclaw.ai/concepts/architecture)
- [Vue d'ensemble de l'architecture](https://docs.openclaw.ai/concepts/architecture)
- [Modèle de session](https://docs.openclaw.ai/concepts/session)
- [Streaming d'outils](https://docs.openclaw.ai/concepts/streaming)
- [Streaming par blocs](https://docs.openclaw.ai/concepts/streaming)
- [Routage de canal](https://docs.openclaw.ai/concepts/channel-routing)
- [Stratégie de nouvelle tentative](https://docs.openclaw.ai/concepts/retry)
- [Streaming/traitement par blocs](https://docs.openclaw.ai/concepts/streaming)

## Espace de travail et compétences

- [Plateforme de compétences](https://docs.openclaw.ai/tools/skills)
- [Installation de compétences](https://docs.openclaw.ai/tools/skills)
- [Gestion des compétences](https://docs.openclaw.ai/tools/skills)
- [Configuration de l'espace de travail](https://docs.openclaw.ai/tools/skills)
- [Intégration des compétences](https://docs.openclaw.ai/tools/skills)

## Internes de la plateforme

- [Plateforme macOS](https://docs.openclaw.ai/platforms/macos)
- [Plateforme iOS](https://docs.openclaw.ai/platforms/ios)
- [Plateforme Android](https://docs.openclaw.ai/platforms/android)
- [Implémentation Canvas](https://docs.openclaw.ai/platforms/mac/canvas)
- [Hôte A2UI](https://docs.openclaw.ai/platforms/mac/canvas#canvas-a2ui)
- [Implémentation des nœuds](https://docs.openclaw.ai/nodes)

## Hooks de courrier

- [Gmail Pub/Sub](https://docs.openclaw.ai/automation/gmail-pubsub)
- [Intégration de courrier](https://docs.openclaw.ai/automation/webhook)
- [Webhooks](https://docs.openclaw.ai/automation/webhook)

## Molty

Molty est une fonctionnalité expérimentale pour les interactions multi-agents.

## Communauté

Voir [CONTRIBUTING.md](CONTRIBUTING.md) pour les lignes directrices de contribution, les responsables et comment soumettre des PR. Les PR pour le codage IA/vibe sont les bienvenues ! 🤖

Remerciements spéciaux à [Mario Zechner](https://mariozechner.at/) pour son soutien et son développement de
[pi-mono](https://github.com/badlogic/pi-mono).
Remerciements spéciaux à Adam Doppelt pour le développement de lobster.bot.

Merci à tous les contributeurs :

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
