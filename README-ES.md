# 🦞 OpenClaw — Asistente personal de IA

<p align="center">
    <picture>
        <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/openclaw/openclaw/main/docs/assets/openclaw-logo-text-dark.png">
        <img src="https://raw.githubusercontent.com/openclaw/openclaw/main/docs/assets/openclaw-logo-text.png" alt="OpenClaw" width="500">
    </picture>
</p>

<p align="center">
  <strong>¡Metamorfosis! ¡Metamorfosis!</strong>
</p>

<p align="center">
  <a href="https://github.com/openclaw/openclaw/actions/workflows/ci.yml?branch=main"><img src="https://img.shields.io/github/actions/workflow/status/openclaw/openclaw/ci.yml?branch=main&style=for-the-badge" alt="Estado CI"></a>
  <a href="https://github.com/openclaw/openclaw/releases"><img src="https://img.shields.io/github/v/release/openclaw/openclaw?include_prereleases&style=for-the-badge" alt="Versión GitHub"></a>
  <a href="https://discord.gg/clawd"><img src="https://img.shields.io/discord/1456350064065904867?label=Discord&logo=discord&logoColor=white&color=5865F2&style=for-the-badge" alt="Discord"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge" alt="Licencia MIT"></a>
</p>

**OpenClaw** es un asistente de IA personal que se ejecuta en sus propios dispositivos. Proporciona soporte a través de canales habituales (WhatsApp, Telegram, Slack, Discord, Google Chat, Signal, iMessage, Microsoft Teams, WebChat) así como a través de canales extendidos como BlueBubbles, Matrix, Zalo y Zalo Personal. Compatible con macOS/iOS/Android y puede renderizar interfaces Canvas en tiempo real controladas por usted. La puerta de enlace es solo una plataforma de control, el producto en sí es el verdadero asistente.
Si busca un asistente local, rápido y siempre en línea para un solo usuario, este es el indicado.

[Sitio web](https://openclaw.ai) · [Documentación oficial](https://docs.openclaw.ai) · [DeepWiki](https://deepwiki.com/openclaw/openclaw) · [Guía de inicio](https://docs.openclaw.ai/start/getting-started) · [Actualizaciones](https://docs.openclaw.ai/install/updating) · [Casos de uso](https://docs.openclaw.ai/start/showcase) · [Preguntas frecuentes](https://docs.openclaw.ai/start/faq) · [Asistente](https://docs.openclaw.ai/start/wizard) · [Nix](https://github.com/openclaw/nix-clawdbot) · [Docker](https://docs.openclaw.ai/install/docker) · [Discord](https://discord.gg/clawd)

Configuración recomendada: Ejecute el asistente de configuración (`openclaw onboard`). Este le guiará a través de la configuración de la puerta de enlace, espacio de trabajo, canales y habilidades. El asistente de línea de comandos es la ruta recomendada y funciona en **macOS, Linux y Windows (mediante WSL2; muy recomendado)**.
Compatible con npm, pnpm o bun. ¿Instalación nueva? Comience aquí: [Guía de inicio](https://docs.openclaw.ai/start/getting-started)

**Suscripción (OAuth):**

- **[Anthropic](https://www.anthropic.com/)** (Claude Pro/Max)
- **[OpenAI](https://openai.com/)** (ChatGPT/Codex)

Notas sobre modelos: Aunque todos los modelos son compatibles, recomiendo encarecidamente **Anthropic Pro/Max (100/200) + Opus 4.6** para obtener un mejor rendimiento a largo plazo y mayor resistencia a interferencias. Consulte la [Guía en línea](https://docs.openclaw.ai/start/onboarding).

## Modelos (Selección + Autenticación)

- Configuración de modelos + CLI: [Modelos](https://docs.openclaw.ai/concepts/models)
- Perfiles de autenticación (OAuth vs claves API) + alternativas: [Alternancia de modelos](https://docs.openclaw.ai/concepts/model-failover)

## Instalación

Entorno de ejecución: **Node ≥22**.

```bash
npm install -g openclaw@latest
# o: pnpm add -g openclaw@latest

openclaw onboard --install-daemon
```

El asistente instala el demonio de la puerta de enlace (servicio de usuario launchd/systemd) para mantenerlo en ejecución.

## Inicio rápido (Resumen)

Entorno de ejecución: **Node ≥22**.

Guía completa para principiantes (autenticación, emparejamiento, canales): [Guía de inicio](https://docs.openclaw.ai/start/getting-started)

```bash
openclaw onboard --install-daemon

openclaw gateway --port 18789 --verbose

# Enviar mensaje
openclaw message send --to +1234567890 --message "Hola desde OpenClaw"

# Chatear con el asistente (puede enviar cualquier mensaje a los canales conectados: WhatsApp/Telegram/Slack/Discord/Google Chat/Signal/iMessage/BlueBubbles/Microsoft Teams/Matrix/Zalo/Zalo Personal/WebChat)
openclaw agent --message "Lista de verificación del barco" --thinking high
```

¿Cómo actualizar? [Guía de actualización](https://docs.openclaw.ai/install/updating) (ejecute `openclaw doctor`).

## Explicación del estado de la versión de desarrollo

- **stable**: versiones etiquetadas (`vYYYY.M.D` o `vYYYY.M.D-<patch>`), npm dist-tag `latest`.
- **beta**: versiones preliminares (`vYYYY.M.D-beta.N`), npm dist-tag `beta` (la aplicación de macOS puede estar ausente).
- **dev**: cabeza móvil de `main`, npm dist-tag `dev` (cuando se publica).

Cambiar (git + npm): `openclaw update --channel stable|beta|dev`.
Detalles: [Estado de las versiones de desarrollo](https://docs.openclaw.ai/install/development-channels).

## Fuente (Desarrollo)

Se recomienda `pnpm` para compilaciones desde la fuente. Bun es opcional para ejecutar TypeScript directamente.

```bash
git clone https://github.com/openclaw/openclaw.git
cd openclaw

pnpm install
pnpm ui:build # instala automáticamente dependencias de IU en la primera ejecución
pnpm build

pnpm openclaw onboard --install-daemon

# Bucle de desarrollo (recarga automática al cambiar TS)
pnpm gateway:watch
```

Nota: `pnpm openclaw ...` ejecuta directamente TypeScript (mediante `tsx`). `pnpm build` genera `dist/` para ejecutar/empaquetar el binario `openclaw` mediante Node.

## Configuración de seguridad predeterminada (Permisos DM)

OpenClaw se conecta a plataformas reales de mensajería instantánea. Trate los mensajes directos recibidos como **entradas no confiables**.

Guía de seguridad completa: [Guía de seguridad](https://docs.openclaw.ai/gateway/security)

Comportamiento predeterminado para Telegram/WhatsApp/Signal/iMessage/Microsoft Teams/Discord/Google Chat/Slack:

- **Emparejamiento DM** (`dmPolicy="pairing"` / `channels.discord.dm.policy="pairing"` / `channels.slack.dm.policy="pairing"`): Los remitentes desconocidos reciben un código de emparejamiento corto, el bot no procesa sus mensajes.
- Aprobación: `openclaw pairing approve <channel> <code>` (luego agrega el remitente al almacenamiento local).
- Los mensajes directos entrantes públicos requieren consentimiento explícito: Establezca `dmPolicy="open"` e incluya `"*"` en la lista de permitidos del canal (`allowFrom` / `channels.discord.dm.allowFrom` / `channels.slack.dm.allowFrom`).

Ejecute `openclaw doctor` para descubrir políticas de DM con riesgos/configuración incorrecta.

## Puntos clave

- **[Puerta de enlace prioritaria local](https://docs.openclaw.ai/gateway)** — Plano de control único para sesiones, canales, herramientas y eventos.
- **[Buzón de entrada multicanal](https://docs.openclaw.ai/channels)** — WhatsApp, Telegram, Slack, Discord, Google Chat, Signal, BlueBubbles (iMessage), iMessage (heredado), Microsoft Teams, Matrix, Zalo, Zalo Personal, WebChat, macOS, iOS/Android.
- **[Enrutamiento multiagente](https://docs.openclaw.ai/gateway/configuration)** — Enrutamiento de canales/cuentas/pares entrantes a agentes aislados (espacio de trabajo + sesión por agente).
- **[Activación por voz](https://docs.openclaw.ai/nodes/voicewake) + [Modo conversación](https://docs.openclaw.ai/nodes/talk)** — Funcionalidad de voz siempre activa de ElevenLabs para macOS/iOS/Android.
- **[Canvas en vivo](https://docs.openclaw.ai/platforms/mac/canvas)** — Espacio de trabajo visual basado en agentes que utiliza [A2UI](https://docs.openclaw.ai/platforms/mac/canvas#canvas-a2ui).
- **[Herramientas de primera clase](https://docs.openclaw.ai/tools)** — Navegador, Canvas, Nodos, tareas programadas, Sesiones y operaciones de Discord/Slack.
- **[Aplicaciones complementarias](https://docs.openclaw.ai/platforms/macos)** — Aplicación de barra de menú de macOS + [Nodos](https://docs.openclaw.ai/nodes) iOS/Android.
- **[Asistente](https://docs.openclaw.ai/start/wizard) + [Habilidades](https://docs.openclaw.ai/tools/skills)** — Configuración guiada con habilidades agrupadas/administradas/de espacio de trabajo.

## Historial de estrellas

[![Gráfico histórico de estrellas](https://api.star-history.com/svg?repos=openclaw/openclaw&type=date&legend=top-left)](https://www.star-history.com/#openclaw/openclaw&type=date&legend=top-left)

## Lo que hemos hecho hasta ahora

### Plataforma central

- [Panel de control de la puerta de enlace](https://docs.openclaw.ai/gateway) que incluye sesiones, estado, configuración, tareas programadas, webhooks, [IU interactiva](https://docs.openclaw.ai/web) y [Host de Canvas](https://docs.openclaw.ai/platforms/mac/canvas#canvas-a2ui).
- [Interfaz CLI](https://docs.openclaw.ai/tools/agent-send): Puerta de enlace, Agente, Enviar, [Asistente](https://docs.openclaw.ai/start/wizard) y [Seguridad](https://docs.openclaw.ai/gateway/doctor).
- [Tiempo de ejecución del agente Pi](https://docs.openclaw.ai/concepts/agent) con patrón RPC, admite transmisión de herramientas y transmisión por fragmentos.
- [Modelo de sesión](https://docs.openclaw.ai/concepts/session): `main` para chat directo, aislamiento de grupo, modo de activación, modo de cola, respuestas. Reglas de grupo: [Grupos](https://docs.openclaw.ai/concepts/groups).
- [Canales multimedia](https://docs.openclaw.ai/nodes/images): Imágenes/Audio/Vídeo, ganchos de transcripción, límites de tamaño, ciclo de vida de archivos temporales. Detalles de audio: [Audio](https://docs.openclaw.ai/nodes/audio).

### Canales

- [Canales](https://docs.openclaw.ai/channels): [WhatsApp](https://docs.openclaw.ai/channels/whatsapp) (Baileys), [Telegram](https://docs.openclaw.ai/channels/telegram) (grammY), [Slack](https://docs.openclaw.ai/channels/slack) (Bolt), [Discord](https://docs.openclaw.ai/channels/discord) (discord.js), [Google Chat](https://docs.openclaw.ai/channels/googlechat) (API de Chat), [Signal](https://docs.openclaw.ai/channels/signal) (signal-cli), [BlueBubbles](https://docs.openclaw.ai/channels/bluebubbles) (iMessage, recomendado), [iMessage](https://docs.openclaw.ai/channels/imessage) (imsg heredado), [Microsoft Teams](https://docs.openclaw.ai/channels/msteams) (extensión), [Matrix](https://docs.openclaw.ai/channels/matrix) (extensión), [Zalo](https://docs.openclaw.ai/channels/zalo) (extensión), [Zalo Personal](https://docs.openclaw.ai/channels/zalouser) (extensión), [WebChat](https://docs.openclaw.ai/web/webchat).
- [Enrutamiento de grupo](https://docs.openclaw.ai/concepts/group-messages): Control por menciones, etiquetas de respuesta, fragmentación y enrutamiento por canal. Reglas de canal: [Canales](https://docs.openclaw.ai/channels).

### Aplicaciones + Nodos

- [Aplicación de macOS](https://docs.openclaw.ai/platforms/macos): Panel de control de la barra de menús, [Activación por voz](https://docs.openclaw.ai/nodes/voicewake)/PTT, superposición de [Modo conversación](https://docs.openclaw.ai/nodes/talk), [WebChat](https://docs.openclaw.ai/web/webchat), herramientas de depuración, control de [Puerta de enlace remota](https://docs.openclaw.ai/gateway/remote).
- [Nodos iOS](https://docs.openclaw.ai/platforms/ios): [Canvas](https://docs.openclaw.ai/platforms/mac/canvas), [Activación por voz](https://docs.openclaw.ai/nodes/voicewake), [Modo conversación](https://docs.openclaw.ai/nodes/talk), cámara, grabación de pantalla, emparejamiento Bonjour.
- [Nodos Android](https://docs.openclaw.ai/platforms/android): [Canvas](https://docs.openclaw.ai/platforms/mac/canvas), [Modo conversación](https://docs.openclaw.ai/nodes/talk), cámara, grabación de pantalla, funciones opcionales de SMS.
- [Modo nodo de macOS](https://docs.openclaw.ai/nodes): Ejecución del sistema/notificaciones + exposición de cámara/canvas.

### Herramientas + Automatización

- [Control del navegador](https://docs.openclaw.ai/tools/browser): Chrome/Chromium dedicado a openclaw, capturas de pantalla, acciones, subidas, perfiles.
- [Canvas](https://docs.openclaw.ai/platforms/mac/canvas): [A2UI](https://docs.openclaw.ai/platforms/mac/canvas#canvas-a2ui) Envío/Reinicio, evaluación, capturas de pantalla.
- [Nodos](https://docs.openclaw.ai/nodes): Capturas/grabaciones de cámara, grabación de pantalla, [obtención de ubicación](https://docs.openclaw.ai/nodes/location-command), notificaciones
- [Tareas programadas + Activación](https://docs.openclaw.ai/automation/cron-jobs); [webhooks](https://docs.openclaw.ai/automation/webhook); [Gmail Pub/Sub](https://docs.openclaw.ai/automation/gmail-pubsub).
- [Plataforma de habilidades](https://docs.openclaw.ai/tools/skills): Habilidades agrupadas, gestionadas y de espacio de trabajo con restricciones de instalación e interfaz de usuario.

### Operaciones + Seguridad

- [Enrutamiento de canal](https://docs.openclaw.ai/concepts/channel-routing), [Política de reintento](https://docs.openclaw.ai/concepts/retry) y [Transmisión/fraccionamiento](https://docs.openclaw.ai/concepts/streaming).
- [Presencia](https://docs.openclaw.ai/concepts/presence), [Indicadores de escritura](https://docs.openclaw.ai/concepts/typing-indicators) y [Seguimiento de uso](https://docs.openclaw.ai/concepts/usage-tracking).
- [Modelos](https://docs.openclaw.ai/concepts/models), [Alternancia de modelo](https://docs.openclaw.ai/concepts/model-failover) y [Sesiones](https://docs.openclaw.ai/concepts/session-pruning).
- [Seguridad](https://docs.openclaw.ai/gateway/security) y [Solución de problemas](https://docs.openclaw.ai/channels/troubleshooting).

### Operaciones + Empaquetado

- [Interfaz de control](https://docs.openclaw.ai/web) + [WebChat](https://docs.openclaw.ai/web/webchat) proporcionados directamente por la puerta de enlace.
- [Tailscale Serve/Funnel](https://docs.openclaw.ai/gateway/tailscale) o [Túneles SSH](https://docs.openclaw.ai/gateway/remote) con autenticación por token/contraseña
- [Modo Nix](https://docs.openclaw.ai/install/nix) admite configuración declarativa; instalación basada en [Docker](https://docs.openclaw.ai/install/docker)
- [Seguridad](https://docs.openclaw.ai/gateway/doctor) alternancia de seguridad, [Registro](https://docs.openclaw.ai/logging).

## Cómo funciona (breve resumen)

```
WhatsApp / Telegram / Slack / Discord / Google Chat / Signal / iMessage / BlueBubbles / Microsoft Teams / Matrix / Zalo / Zalo Personal / WebChat
               │
               ▼
┌───────────────────────────────┐
│            Puerta de enlace           │
│       (plano de control)         │
│     ws://127.0.0.1:18789      │
└──────────────┬────────────────┘
               │
               ├─ agente Pi (RPC)
               ├─ CLI (openclaw …)
               ├─ Interfaz WebChat
               ├─ aplicación macOS
               └─ nodos iOS / Android
```

## Subsistemas clave

- **[Comunicación WebSocket de la puerta de enlace](https://docs.openclaw.ai/concepts/architecture)** — Plano de control WS único para clientes, herramientas y eventos (y operaciones: [Manual de la puerta de enlace](https://docs.openclaw.ai/gateway)).
- **[Exposición de Tailscale](https://docs.openclaw.ai/gateway/tailscale)** — Serve/Funnel + WS para panel de control de la puerta de enlace (acceso remoto: [Acceso remoto](https://docs.openclaw.ai/gateway/remote)).
- **[Control del navegador](https://docs.openclaw.ai/tools/browser)** — Chrome/Chromium gestionado por openclaw con control CDP.
- **[Canvas + A2UI](https://docs.openclaw.ai/platforms/mac/canvas)** — Espacio de trabajo visual basado en agentes (host A2UI: [Canvas/A2UI](https://docs.openclaw.ai/platforms/mac/canvas#canvas-a2ui)).
- **[Activación por voz](https://docs.openclaw.ai/nodes/voicewake) + [Modo conversación](https://docs.openclaw.ai/nodes/talk)** — Funcionalidad de voz siempre activa para conversaciones continuas.
- **[Nodos](https://docs.openclaw.ai/nodes)** — Canvas, capturas/grabaciones de cámara, grabación de pantalla, `location.get`, notificaciones, así como funciones específicas de macOS `system.run`/`system.notify`.

## Acceso Tailscale (panel de control de la puerta de enlace)

OpenClaw puede configurar automáticamente Tailscale **Serve** (solo red local) o **Funnel** (público) manteniendo la puerta de enlace vinculada a la interfaz de bucle local. Configure `gateway.tailscale.mode`:

- `off`: Sin automatización de Tailscale (predeterminado).
- `serve`: Solo HTTPS de red local mediante `tailscale serve` (usa encabezados de Tailscale de forma predeterminada).
- `funnel`: HTTPS público mediante `tailscale funnel` (requiere autenticación con contraseña compartida).

Explicaciones:

- `gateway.bind` debe permanecer como `loopback` cuando Serve/Funnel está habilitado (OpenClaw aplica esta regla).
- Obligue una contraseña de servidor estableciendo `gateway.auth.mode: "password"` o `gateway.auth.allowTailscale: false`.
- Niega la ejecución a menos que `gateway.auth.mode: "password"` ya haya sido establecido.
- Opcional `gateway.tailscale.resetOnExit` revoca las operaciones de Serve/Funnel al apagar.

Detalles: [Guía de Tailscale](https://docs.openclaw.ai/gateway/tailscale) · [Página web](https://docs.openclaw.ai/web)

## Puerta de enlace remota (mejor compatibilidad con Linux)

Está perfectamente bien ejecutar la puerta de enlace en una instancia pequeña de Linux. Los clientes (aplicación de macOS, CLI, WebChat) pueden conectarse mediante **Tailscale Serve/Funnel** o **túneles SSH**, y aún puede emparejar nodos de dispositivo (macOS/iOS/Android) según sea necesario para realizar operaciones locales en el dispositivo.

- **Host de la puerta de enlace** normalmente ejecuta herramientas y establece conexiones de canal.
- **Nodos de dispositivo** ejecutan operaciones locales en el dispositivo (como `system.run`, cámara, grabación de pantalla, notificaciones) mediante `node.invoke`.
  En resumen: la ejecución ocurre donde está la puerta de enlace; las operaciones del dispositivo ocurren donde está el dispositivo.

Detalles: [Acceso remoto](https://docs.openclaw.ai/gateway/remote) · [Nodos](https://docs.openclaw.ai/nodes) · [Seguridad](https://docs.openclaw.ai/gateway/security)

## Permisos de macOS a través del protocolo de puerta de enlace

La aplicación de macOS puede ejecutarse en **modo nodo** y difundir sus capacidades y asignaciones de permisos a través del WebSocket de la puerta de enlace (`node.list` / `node.describe`). Los clientes pueden entonces ejecutar operaciones locales mediante `node.invoke`:

- `system.run` ejecuta comandos locales y devuelve stdout/stderr/código de salida; configure `needsScreenRecording: true` para permisos de grabación de pantalla (de lo contrario recibirá el error `PERMISSION_MISSING`).
- `system.notify` envía una notificación al usuario, falla si la notificación es rechazada.
- `canvas.*`, `camera.*`, `screen.record` y `location.get` se enrutan mediante `node.invoke` y siguen el estado de permisos TCC.

Los permisos elevados de bash (permisos de host) y TCC de macOS son independientes:

- Use `/elevated on|off` para alternar el acceso elevado por sesión cuando esté habilitado + agregado a la lista de permisos.
- La puerta de enlace persiste cada cambio de sesión a través de (métodos WS) así como `sessions.patch`, `thinkingLevel`, `verboseLevel`, `model`, `sendPolicy` y `groupActivation`.

Detalles: [Nodos](https://docs.openclaw.ai/nodes) · [Aplicación de macOS](https://docs.openclaw.ai/platforms/macos) · [Protocolo de puerta de enlace](https://docs.openclaw.ai/concepts/architecture)

## Agente a agente (herramientas de sesión_*)

- Esta función le permite coordinar el trabajo entre sesiones sin cambiar entre interfaces de chat.
- `sessions_list` — Descubre sesiones (agentes) activas y sus metadatos.
- `sessions_history` — Recupera registros históricos de la sesión.
- `sessions_send` — Envía un mensaje a otra sesión.
- `sessions_spawn` — Crea una nueva sesión (agente) con un perfil predefinido.

## Requisitos del sistema

- **macOS 13+** (recomendado), **Linux** (varias distribuciones), **Windows 10/11** (WSL2)
- **Node.js 22+**, **npm**/**pnpm**/**bun**
- **Chrome/Chromium** para herramientas del navegador
- **Docker** para contenedores de herramientas sandbox (opcional)

## Permisos de la plataforma

- **macOS**: Se requieren permisos de accesibilidad para `openclaw` para usar `system.run` (bash). Para grabación de pantalla/cámara, conceda permisos a la aplicación o ejecute en modo nodo.
- **Android**: Se requieren permisos de grabación de pantalla/cámara y opcionalmente SMS.
- **iOS**: Se requieren permisos de grabación de pantalla/cámara.

## Configuración

Configuración mínima `~/.openclaw/openclaw.json` (modelo + valores predeterminados):

```json5
{
  agent: {
    model: "anthropic/claude-opus-4-6",
  },
}
```

[Referencia de configuración completa (todas las claves y ejemplos).](https://docs.openclaw.ai/gateway/configuration)

## Modo seguro (importante)

- **Por defecto:** Las herramientas se ejecutan en el host para la sesión principal, por lo tanto, cuando usted es el único usuario, el agente tiene acceso completo.
- **Seguridad para canales/grupos:** Ejecute cada sesión como entorno aislado dentro de Docker con `agents.defaults.sandbox.mode: "non-main"` como **sesiones no principales** (canales de grupo/canal); luego ejecútelo como sesión bash dentro de Docker.
- **Sandbox predeterminado:** Permite ejecutar `bash`, `process`, `read`, `write`, `edit`, `sessions_list`, `sessions_history`, `sessions_send`, `sessions_spawn`. Prohíbe `browser`, `canvas`, `nodes`, `cron`, `discord`, `gateway`.

Detalles: [Directrices de seguridad](https://docs.openclaw.ai/gateway/security) · [Docker + Sandbox](https://docs.openclaw.ai/install/docker) · [Configuración de sandbox](https://docs.openclaw.ai/gateway/configuration)

### [WhatsApp](https://docs.openclaw.ai/channels/whatsapp)

- Vincular dispositivo: `pnpm openclaw channels login` (credenciales almacenadas en `~/.openclaw/credentials`).
- Permitir usuarios que pueden chatear con el asistente agregándolos a `channels.whatsapp.allowFrom`.
- Si `channels.whatsapp.groups` está configurado, se convierte en una lista blanca de grupos; incluir `"*"` permite todos los grupos.

### [Telegram](https://docs.openclaw.ai/channels/telegram)

- Configure `TELEGRAM_BOT_TOKEN` o `channels.telegram.botToken` (variable de entorno tiene prioridad).
- Opcional: Configure `channels.telegram.groups` (a través de `channels.telegram.groups."*".requireMention`); una vez configurado, se convierte en una lista blanca (incluir `"*"` permite todos); y `channels.telegram.allowFrom` o `channels.telegram.webhookUrl` + `channels.telegram.webhookSecret` según sea necesario.

```json5
{
  channels: {
    telegram: {
      botToken: "123456:ABCDEF",
    },
  },
}
```

### [Slack](https://docs.openclaw.ai/channels/slack)

- Configure `SLACK_BOT_TOKEN` + `SLACK_APP_TOKEN` (o `channels.slack.botToken` + `channels.slack.appToken`).

### [Discord](https://docs.openclaw.ai/channels/discord)

- Configure `DISCORD_BOT_TOKEN` o `channels.discord.token` (variable de entorno tiene prioridad).
- Opcional: Configure `commands.native`, `commands.text`, o `commands.useAccessGroups`, y `channels.discord.dm.allowFrom`, `channels.discord.guilds`, o `channels.discord.mediaMaxMb` según sea necesario.

```json5
{
  channels: {
    discord: {
      token: "1234abcd",
    },
  },
}
```

### [Signal](https://docs.openclaw.ai/channels/signal)

- Requiere `signal-cli` y una configuración `channels.signal`.

### [BlueBubbles (iMessage)](https://docs.openclaw.ai/channels/bluebubbles)

- **Recomendado** para integración de iMessage
- Configure `channels.bluebubbles.serverUrl` + `channels.bluebubbles.password` y un webhook (`channels.bluebubbles.webhookPath`).
- Servidor BlueBubbles ejecutándose en macOS; la puerta de enlace puede ejecutarse en macOS u otros sistemas.

### [iMessage (heredado)](https://docs.openclaw.ai/channels/imessage)

- Integración heredada de macOS solo para `imsg` (debe haber iniciado sesión en la aplicación Mensajes).
- Si se configura `channels.imessage.groups`, se convierte en una lista blanca; incluir `"*"` permite todos los grupos.

### [Microsoft Teams](https://docs.openclaw.ai/channels/msteams)

- Configure la aplicación Teams + Bot Framework, luego agregue la configuración `msteams`.
- Lista blanca `msteams.allowFrom`; grupos a través de `msteams.groupAllowFrom` o `msteams.groupPolicy: "open"`.

### [WebChat](https://docs.openclaw.ai/web/webchat)

- Utiliza WebSocket de la puerta de enlace; no hay puerto/configuración separada de WebChat.

Control del navegador (opcional):

```json5
{
  browser: {
    enabled: true,
    color: "#FF4500",
  },
}
```

## Documentación

Después de la configuración, es posible que necesite materiales de referencia más profundos.

- [Primero consulte el índice de documentación para aprender cómo navegar y dónde encontrar contenido.](https://docs.openclaw.ai)
- [Lea la descripción general de la arquitectura modelo pasarela+protocolo.](https://docs.openclaw.ai/concepts/architecture)
- [Use la referencia completa de configuración si necesita todas las claves y ejemplos.](https://docs.openclaw.ai/gateway/configuration)
- [Configuración del desarrollador](https://docs.openclaw.ai/start/development)
- [Referencia del protocolo de la pasarela](https://docs.openclaw.ai/concepts/architecture)
- [Referencia CLI](https://docs.openclaw.ai/tools/agent-send)

## Operación y solución de problemas

- [Verificar estado](https://docs.openclaw.ai/gateway/health)
- [Bloqueo de la pasarela](https://docs.openclaw.ai/gateway/gateway-lock)
- [Procesos en segundo plano](https://docs.openclaw.ai/gateway/background-process)
- [Solución de problemas del navegador (Linux)](https://docs.openclaw.ai/tools/browser-linux-troubleshooting)
- [Registro](https://docs.openclaw.ai/logging)

## Exploración profunda

- [Bucle del agente](https://docs.openclaw.ai/concepts/agent-loop)
- [Estado en tiempo real](https://docs.openclaw.ai/concepts/presence)
- [Esquema TypeBox](https://docs.openclaw.ai/concepts/typebox)
- [Adaptadores RPC](https://docs.openclaw.ai/reference/rpc)
- [Colas](https://docs.openclaw.ai/concepts/queue)

## Espacio de trabajo y habilidades

- [Configuración de habilidades](https://docs.openclaw.ai/tools/skills-config)
- [Agentes predeterminados](https://docs.openclaw.ai/reference/AGENTS.default)
- [Plantillas: Agentes](https://docs.openclaw.ai/reference/templates/AGENTS)
- [Plantillas: BOOTSTRAP](https://docs.openclaw.ai/reference/templates/BOOTSTRAP)
- [Plantillas: Identidad](https://docs.openclaw.ai/reference/templates/IDENTITY)
- [Plantillas: Alma](https://docs.openclaw.ai/reference/templates/SOUL)
- [Plantillas: Herramientas](https://docs.openclaw.ai/reference/templates/TOOLS)
- [Plantillas: Usuario](https://docs.openclaw.ai/reference/templates/USER)

## Internos de la plataforma

- [Configuración de desarrollo de macOS](https://docs.openclaw.ai/platforms/mac/dev-setup)
- [Barra de menú de macOS](https://docs.openclaw.ai/platforms/mac/menu-bar)
- [Activación de voz de macOS](https://docs.openclaw.ai/platforms/mac/voicewake)
- [Nodos iOS](https://docs.openclaw.ai/platforms/ios)
- [Nodos Android](https://docs.openclaw.ai/platforms/android)
- [Windows (WSL2)](https://docs.openclaw.ai/platforms/windows)
- [Aplicaciones Linux](https://docs.openclaw.ai/platforms/linux)

## Hooks de correo electrónico (Gmail)

- [docs.openclaw.ai/gmail-pubsub](https://docs.openclaw.ai/automation/gmail-pubsub)

## Molty

OpenClaw fue desarrollado para el cangrejo espacial de IA **Molty**. 🦞
Construido por Peter Steinberger y la comunidad.

- [openclaw.ai](https://openclaw.ai)
- [soul.md](https://soul.md)
- [steipete.me](https://steipete.me)
- [@openclaw](https://x.com/openclaw)

## Comunidad

Consulte el archivo [CONTRIBUTING.md](CONTRIBUTING.md) para conocer las pautas de contribución, información del mantenedor y cómo enviar PR. ¡PR de codificación de IA/vibe son bienvenidas! 🤖

Agradecimientos especiales a [Mario Zechner](https://mariozechner.at/) por su apoyo y su
[pi-mono](https://github.com/badlogic/pi-mono).
Agradecimientos especiales a Adam Doppelt por desarrollar lobster.bot.

Gracias a todos los contribuyentes:

<p align="left">
  <a href="https://github.com/steipete"><img src="https://avatars.githubusercontent.com/u/58493?v=4&s=48" width="48" height="48" alt="steipete" title="steipete"/></a> <a href="https://github.com/joshp123"><img src="https://avatars.githubusercontent.com/u/1497361?v=4&s=48" width="48" height="48" alt="joshp123" title="joshp123"/></a> <a href="https://github.com/cpojer"><img src="https://avatars.githubusercontent.com/u/13352?v=4&s=48" width="48" height="48" alt="cpojer" title="cpojer"/></a> <a href="https://github.com/mbelinky"><img src="https://avatars.githubusercontent.com/u/132747814?v=4&s=48" width="48" height="48" alt="Mariano Belinky" title="Mariano Belinky"/></a> <a href="https://github.com/plum-dawg"><img src="https://avatars.githubusercontent.com/u/5909950?v=4&s=48" width="48" height="48" alt="plum-dawg" title="plum-dawg"/></a> <a href="https://github.com/bohdanpodvirnyi"><img src="https://avatars.githubusercontent.com/u/31819391?v=4&s=48" width="48" height="48" alt="bohdanpodvirnyi" title="bohdanpodvirnyi"/></a> <a href="https://github.com/iHildy"><img src="https://avatars.githubusercontent.com/u/25069719?v=4&s=48" width="48" height="48" alt="iHildy" title="iHildy"/></a> <a href="https://github.com/jaydenfyi"><img src="https://avatars.githubusercontent.com/u/213395523?v=4&s=48" width="48" height="48" alt="jaydenfyi" title="jaydenfyi"/></a> <a href="https://github.com/joaohlisboa"><img src="https://avatars.githubusercontent.com/u/8200873?v=4&s=48" width="48" height="48" alt="joaohlisboa" title="joaohlisboa"/></a> <a href="https://github.com/mneves75"><img src="https://avatars.githubusercontent.com/u/2423436?v=4&s=48" width="48" height="48" alt="mneves75" title="mneves75"/></a>
  <a href="https://github.com/MatthieuBizien"><img src="https://avatars.githubusercontent.com/u/173090?v=4&s=48" width="48" height="48" alt="MatthieuBizien" title="MatthieuBizien"/></a> <a href="https://github.com/MaudeBot"><img src="https://avatars.githubusercontent.com/u/255777700?v=4&s=48" width="48" height="48" alt="MaudeBot" title="MaudeBot"/></a> <a href="https://github.com/sebslight"><img src="https://avatars.githubusercontent.com/u/19554889?v=4&s=48" width="48" height="48" alt="sebslight" title="sebslight"/></a> <a href="https://github.com/Glucksberg"><img src="https://avatars.githubusercontent.com/u/80581902?v=4&s=48" width="48" height="48" alt="Glucksberg" title="Glucksberg"/></a> <a href="https://github.com/rahthakor"><img src="https://avatars.githubusercontent.com/u/8470553?v=4&s=48" width="48" height="48" alt="rahthakor" title="rahthakor"/></a> <a href="https://github.com/vrknetha"><img src="https://avatars.githubusercontent.com/u/20596261?v=4&s=48" width="48" height="48" alt="vrknetha" title="vrknetha"/></a> <a href="https://github.com/tyler6204"><img src="https://avatars.githubusercontent.com/u/64381258?v=4&s=48" width="48" height="48" alt="tyler6204" title="tyler6204"/></a> <a href="https://github.com/vignesh07"><img src="https://avatars.githubusercontent.com/u/1436853?v=4&s=48" width="48" height="48" alt="vignesh07" title="vignesh07"/></a> <a href="https://github.com/radek-paclt"><img src="https://avatars.githubusercontent.com/u/50451445?v=4&s=48" width="48" height="48" alt="radek-paclt" title="radek-paclt"/></a> <a href="https://github.com/tobiasbischoff"><img src="https://avatars.githubusercontent.com/u/711564?v=4&s=48" width="48" height="48" alt="Tobias Bischoff" title="Tobias Bischoff"/></a>
  <a href="https://github.com/czekaj"><img src="https://avatars.githubusercontent.com/u/1464539?v=4&s=48" width="48" height="48" alt="czekaj" title="czekaj"/></a> <a href="https://github.com/ethanpalm"><img src="https://avatars.githubusercontent.com/u/56270045?v=4&s=48" width="48" height="48" alt="ethanpalm" title="ethanpalm"/></a> <a href="https://github.com/mukhtharcm"><img src="https://avatars.githubusercontent.com/u/56378562?v=4&s=48" width="48" height="48" alt="mukhtharcm" title="mukhtharcm"/></a> <a href="https://github.com/maxsumrall"><img src="https://avatars.githubusercontent.com/u/628843?v=4&s=48" width="48" height="48" alt="maxsumrall" title="maxsumrall"/></a> <a href="https://github.com/xadenryan"><img src="https://avatars.githubusercontent.com/u/165437834?v=4&s=48" width="48" height="48" alt="xadenryan" title="xadenryan"/></a> <a href="https://github.com/VACInc"><img src="https://avatars.githubusercontent.com/u/3279061?v=4&s=48" width="48" height="48" alt="VACInc" title="VACInc"/></a> <a href="https://github.com/rodrigouroz"><img src="https://avatars.githubusercontent.com/u/384037?v=4&s=48" width="48" height="48" alt="rodrigouroz" title="rodrigouroz"/></a> <a href="https://github.com/juanpablodlc"><img src="https://avatars.githubusercontent.com/u/92012363?v=4&s=48" width="48" height="48" alt="juanpablodlc" title="juanpablodlc"/></a> <a href="https://github.com/conroywhitney"><img src="https://avatars.githubusercontent.com/u/249891?v=4&s=48" width="48" height="48" alt="conroywhitney" title="conroywhitney"/></a> <a href="https://github.com/hsrvc"><img src="https://avatars.githubusercontent.com/u/129702169?v=4&s=48" width="48" height="48" alt="hsrvc" title="hsrvc"/></a>
  <a href="https://github.com/christianklotz"><img src="https://avatars.githubusercontent.com/u/69443?v=4&s=48" width="48" height="48" alt="christianklotz" title="christianklotz"/></a> <a href="https://github.com/magimetal"><img src="https://avatars.githubusercontent.com/u/36491250?v=4&s=48" width="48" height="48" alt="magimetal" title="magimetal"/></a> <a href="https://github.com/zerone0x"><img src="https://avatars.githubusercontent.com/u/39543393?v=4&s=48" width="48" height="48" alt="zerone0x" title="zerone0x"/></a> <a href="https://github.com/meaningfool"><img src="https://avatars.githubusercontent.com/u/2862331?v=4&s=48" width="48" height="48" alt="meaningfool" title="meaningfool"/></a> <a href="https://github.com/Takhoffman"><img src="https://avatars.githubusercontent.com/u/781889?v=4&s=48" width="48" height="48" alt="Takhoffman" title="Takhoffman"/></a> <a href="https://github.com/patelhiren"><img src="https://avatars.githubusercontent.com/u/172098?v=4&s=48" width="48" height="48" alt="patelhiren" title="patelhiren"/></a> <a href="https://github.com/NicholasSpisak"><img src="https://avatars.githubusercontent.com/u/129075147?v=4&s=48" width="48" height="48" alt="NicholasSpisak" title="NicholasSpisak"/></a> <a href="https://github.com/jonisjongithub"><img src="https://avatars.githubusercontent.com/u/86072337?v=4&s=48" width="48" height="48" alt="jonisjongithub" title="jonisjongithub"/></a> <a href="https://github.com/AbhisekBasu1"><img src="https://avatars.githubusercontent.com/u/40645221?v=4&s=48" width="48" height="48" alt="abhisekbasu1" title="abhisekbasu1"/></a> <a href="https://github.com/jamesgroat"><img src="https://avatars.githubusercontent.com/u/2634024?v=4&s=48" width="48" height="48" alt="jamesgroat" title="jamesgroat"/></a>
  <a href="https://github.com/BunsDev"><img src="https://avatars.githubusercontent.com/u/68980965?v=4&s=48" width="48" height="48" alt="BunsDev" title="BunsDev"/></a> <a href="https://github.com/claude"><img src="https://avatars.githubusercontent.com/u/81847?v=4&s=48" width="48" height="48" alt="claude" title="claude"/></a> <a href="https://github.com/JustYannicc"><img src="https://avatars.githubusercontent.com/u/52761674?v=4&s=48" width="48" height="48" alt="JustYannicc" title="JustYannicc"/></a> <a href="https://github.com/Hyaxia"><img src="https://avatars.githubusercontent.com/u/36747317?v=4&s=48" width="48" height="48" alt="Hyaxia" title="Hyaxia"/></a> <a href="https://github.com/dantelex"><img src="https://avatars.githubusercontent.com/u/631543?v=4&s=48" width="48" height="48" alt="dantelex" title="dantelex"/></a> <a href="https://github.com/SocialNerd42069"><img src="https://avatars.githubusercontent.com/u/118244303?v=4&s=48" width="48" height="48" alt="SocialNerd42069" title="SocialNerd42069"/></a> <a href="https://github.com/daveonkels"><img src="https://avatars.githubusercontent.com/u/533642?v=4&s=48" width="48" height="48" alt="daveonkels" title="daveonkels"/></a> <a href="https://github.com/apps/google-labs-jules"><img src="https://avatars.githubusercontent.com/in/842251?v=4&s=48" width="48" height="48" alt="google-labs-jules[bot]" title="google-labs-jules[bot]"/></a> <a href="https://github.com/lc0rp"><img src="https://avatars.githubusercontent.com/u/2609441?v=4&s=48" width="48" height="48" alt="lc0rp" title="lc0rp"/></a> <a href="https://github.com/mousberg"><img src="https://avatars.githubusercontent.com/u/57605064?v=4&s=48" width="48" height="48" alt="mousberg" title="mousberg"/></a>
  <a href="https://github.com/adam91holt"><img src="https://avatars.githubusercontent.com/u/9592417?v=4&s=48" width="48" height="48" alt="adam91holt" title="adam91holt"/></a> <a href="https://github.com/hougangdev"><img src="https://avatars.githubusercontent.com/u/105773686?v=4&s=48" width="48" height="48" alt="hougangdev" title="hougangdev"/></a> <a href="https://github.com/gumadeiras"><img src="https://avatars.githubusercontent.com/u/5599352?v=4&s=48" width="48" height="48" alt="gumadeiras" title="gumadeiras"/></a> <a href="https://github.com/shakkernerd"><img src="https://avatars.githubusercontent.com/u/165377636?v=4&s=48" width="48" height="48" alt="shakkernerd" title="shakkernerd"/></a> <a href="https://github.com/mteam88"><img src="https://avatars.githubusercontent.com/u/84196639?v=4&s=48" width="48" height="48" alt="mteam88" title="mteam88"/></a> <a href="https://github.com/hirefrank"><img src="https://avatars.githubusercontent.com/u/183158?v=4&s=48" width="48" height="48" alt="hirefrank" title="hirefrank"/></a> <a href="https://github.com/joeynyc"><img src="https://avatars.githubusercontent.com/u/17919866?v=4&s=48" width="48" height="48" alt="joeynyc" title="joeynyc"/></a> <a href="https://github.com/orlyjamie"><img src="https://avatars.githubusercontent.com/u/6668807?v=4&s=48" width="48" height="48" alt="orlyjamie" title="orlyjamie"/></a> <a href="https://github.com/dbhurley"><img src="https://avatars.githubusercontent.com/u/5251425?v=4&s=48" width="48" height="48" alt="dbhurley" title="dbhurley"/></a> <a href="https://github.com/omniwired"><img src="https://avatars.githubusercontent.com/u/322761?v=4&s=48" width="48" height="48" alt="Eng. Juan Combetto" title="Eng. Juan Combetto"/></a>
  <a href="https://github.com/TSavo"><img src="https://avatars.githubusercontent.com/u/877990?v=4&s=48" width="48" height="48" alt="TSavo" title="TSavo"/></a> <a href="https://github.com/aerolalit"><img src="https://avatars.githubusercontent.com/u/17166039?v=4&s=48" width="48" height="48" alt="aerolalit" title="aerolalit"/></a> <a href="https://github.com/julianengel"><img src="https://avatars.githubusercontent.com/u/10634231?v=4&s=48" width="48" height="48" alt="julianengel" title="julianengel"/></a> <a href="https://github.com/bradleypriest"><img src="https://avatars.githubusercontent.com/u/167215?v=4&s=48" width="48" height="48" alt="bradleypriest" title="bradleypriest"/></a> <a href="https://github.com/benithors"><img src="https://avatars.githubusercontent.com/u/20652882?v=4&s=48" width="48" height="48" alt="benithors" title="benithors"/></a> <a href="https://github.com/rohannagpal"><img src="https://avatars.githubusercontent.com/u/4009239?v=4&s=48" width="48" height="48" alt="rohannagpal" title="rohannagpal"/></a> <a href="https://github.com/timolins"><img src="https://avatars.githubusercontent.com/u/1440854?v=4&s=48" width="48" height="48" alt="timolins" title="timolins"/></a> <a href="https://github.com/f-trycua"><img src="https://avatars.githubusercontent.com/u/195596869?v=4&s=48" width="48" height="48" alt="f-trycua" title="f-trycua"/></a> <a href="https://github.com/benostein"><img src="https://avatars.githubusercontent.com/u/31802821?v=4&s=48" width="48" height="48" alt="benostein" title="benostein"/></a> <a href="https://github.com/elliotsecops"><img src="https://avatars.githubusercontent.com/u/141947839?v=4&s=48" width="48" height="48" alt="elliotsecops" title="elliotsecops"/></a>
  <a href="https://github.com/Nachx639"><img src="https://avatars.githubusercontent.com/u/71144023?v=4&s=48" width="48" height="48" alt="nachx639" title="nachx639"/></a> <a href="https://github.com/pvoo"><img src="https://avatars.githubusercontent.com/u/20116814?v=4&s=48" width="48" height="48" alt="pvoo" title="pvoo"/></a> <a href="https://github.com/sreekaransrinath"><img src="https://avatars.githubusercontent.com/u/50989977?v=4&s=48" width="48" height="48" alt="sreekaransrinath" title="sreekaransrinath"/></a> <a href="https://github.com/gupsammy"><img src="https://avatars.githubusercontent.com/u/20296019?v=4&s=48" width="48" height="48" alt="gupsammy" title="gupsammy"/></a> <a href="https://github.com/cristip73"><img src="https://avatars.githubusercontent.com/u/24499421?v=4&s=48" width="48" height="48" alt="cristip73" title="cristip73"/></a> <a href="https://github.com/stefangalescu"><img src="https://avatars.githubusercontent.com/u/52995748?v=4&s=48" width="48" height="48" alt="stefangalescu" title="stefangalescu"/></a> <a href="https://github.com/nachoiacovino"><img src="https://avatars.githubusercontent.com/u/50103937?v=4&s=48" width="48" height="48" alt="nachoiacovino" title="nachoiacovino"/></a> <a href="https://github.com/vsabavat"><img src="https://avatars.githubusercontent.com/u/50385532?v=4&s=48" width="48" height="48" alt="Vasanth Rao Naik Sabavat" title="Vasanth Rao Naik Sabavat"/></a> <a href="https://github.com/petter-b"><img src="https://avatars.githubusercontent.com/u/62076402?v=4&s=48" width="48" height="48" alt="petter-b" title="petter-b"/></a> <a href="https://github.com/thewilloftheshadow"><img src="https://avatars.githubusercontent.com/u/35580099?v=4&s=48" width="48" height="48" alt="thewilloftheshadow" title="thewilloftheshadow"/></a>
  <a href="https://github.com/leszekszpunar"><img src="https://avatars.githubusercontent.com/u/13106764?v=4&s=48" width="48" height="48" alt="leszekszpunar" title="leszekszpunar"/></a> <a href="https://github.com/scald"><img src="https://avatars.githubusercontent.com/u/1215913?v=4&s=48" width="48" height="48" alt="scald" title="scald"/></a> <a href="https://github.com/andranik-sahakyan"><img src="https://avatars.githubusercontent.com/u/8908029?v=4&s=48" width="48" height="48" alt="andranik-sahakyan" title="andranik-sahakyan"/></a> <a href="https://github.com/davidguttman"><img src="https://avatars.githubusercontent.com/u/431696?v=4&s=48" width="48" height="48" alt="davidguttman" title="davidguttman"/></a> <a href="https://github.com/sleontenko"><img src="https://avatars.githubusercontent.com/u/7135949?v=4&s=48" width="48" height="48" alt="sleontenko" title="sleontenko"/></a> <a href="https://github.com/denysvitali"><img src="https://avatars.githubusercontent.com/u/4939519?v=4&s=48" width="48" height="48" alt="denysvitali" title="denysvitali"/></a> <a href="https://github.com/apps/clawdinator"><img src="https://avatars.githubusercontent.com/in/2607181?v=4&s=48" width="48" height="48" alt="clawdinator[bot]" title="clawdinator[bot]"/></a> <a href="https://github.com/sircrumpet"><img src="https://avatars.githubusercontent.com/u/4436535?v=4&s=48" width="48" height="48" alt="sircrumpet" title="sircrumpet"/></a> <a href="https://github.com/peschee"><img src="https://avatars.githubusercontent.com/u/63866?v=4&s=48" width="48" height="48" alt="peschee" title="peschee"/></a> <a href="https://github.com/davidiach"><img src="https://avatars.githubusercontent.com/u/28102235?v=4&s=48" width="48" height="48" alt="davidiach" title="davidiach"/></a>
  <a href="https://github.com/nonggialiang"><img src="https://avatars.githubusercontent.com/u/14367839?v=4&s=48" width="48" height="48" alt="nonggialiang" title="nonggialiang"/></a> <a href="https://github.com/rafaelreis-r"><img src="https://avatars.githubusercontent.com/u/57492577?v=4&s=48" width="48" height="48" alt="rafaelreis-r" title="rafaelreis-r"/></a> <a href="https://github.com/dominicnunez"><img src="https://avatars.githubusercontent.com/u/43616264?v=4&s=48" width="48" height="48" alt="dominicnunez" title="dominicnunez"/></a> <a href="https://github.com/lploc94"><img src="https://avatars.githubusercontent.com/u/28453843?v=4&s=48" width="48" height="48" alt="lploc94" title="lploc94"/></a> <a href="https://github.com/ratulsarna"><img src="https://avatars.githubusercontent.com/u/105903728?v=4&s=48" width="48" height="48" alt="ratulsarna" title="ratulsarna"/></a> <a href="https://github.com/sfo2001"><img src="https://avatars.githubusercontent.com/u/103369858?v=4&s=48" width="48" height="48" alt="sfo2001" title="sfo2001"/></a> <a href="https://github.com/lutr0"><img src="https://avatars.githubusercontent.com/u/76906369?v=4&s=48" width="48" height="48" alt="lutr0" title="lutr0"/></a> <a href="https://github.com/kiranjd"><img src="https://avatars.githubusercontent.com/u/25822851?v=4&s=48" width="48" height="48" alt="kiranjd" title="kiranjd"/></a> <a href="https://github.com/danielz1z"><img src="https://avatars.githubusercontent.com/u/235270390?v=4&s=48" width="48" height="48" alt="danielz1z" title="danielz1z"/></a> <a href="https://github.com/Iranb"><img src="https://avatars.githubusercontent.com/u/49674669?v=4&s=48" width="48" height="48" alt="Iranb" title="Iranb"/></a>
  <a href="https://github.com/AdeboyeDN"><img src="https://avatars.githubusercontent.com/u/65312338?v=4&s=48" width="48" height="48" alt="AdeboyeDN" title="AdeboyeDN"/></a> <a href="https://github.com/Alg0rix"><img src="https://avatars.githubusercontent.com/u/53804949?v=4&s=48" width="48" height="48" alt="Alg0rix" title="Alg0rix"/></a> <a href="https://github.com/obviyus"><img src="https://avatars.githubusercontent.com/u/22031114?v=4&s=48" width="48" height="48" alt="obviyus" title="obviyus"/></a> <a href="https://github.com/papago2355"><img src="https://avatars.githubusercontent.com/u/68721273?v=4&s=48" width="48" height="48" alt="papago2355" title="papago2355"/></a> <a href="https://github.com/emanuelst"><img src="https://avatars.githubusercontent.com/u/9994339?v=4&s=48" width="48" height="48" alt="emanuelst" title="emanuelst"/></a> <a href="https://github.com/evanotero"><img src="https://avatars.githubusercontent.com/u/13204105?v=4&s=48" width="48" height="48" alt="evanotero" title="evanotero"/></a> <a href="https://github.com/KristijanJovanovski"><img src="https://avatars.githubusercontent.com/u/8942284?v=4&s=48" width="48" height="48" alt="KristijanJovanovski" title="KristijanJovanovski"/></a> <a href="https://github.com/jlowin"><img src="https://avatars.githubusercontent.com/u/153965?v=4&s=48" width="48" height="48" alt="jlowin" title="jlowin"/></a> <a href="https://github.com/rdev"><img src="https://avatars.githubusercontent.com/u/8418866?v=4&s=48" width="48" height="48" alt="rdev" title="rdev"/></a> <a href="https://github.com/rhuanssauro"><img src="https://avatars.githubusercontent.com/u/164682191?v=4&s=48" width="48" height="48" alt="rhuanssauro" title="rhuanssauro"/></a>
  <a href="https://github.com/joshrad-dev"><img src="https://avatars.githubusercontent.com/u/62785552?v=4&s=48" width="48" height="48" alt="joshrad-dev" title="joshrad-dev"/></a> <a href="https://github.com/osolmaz"><img src="https://avatars.githubusercontent.com/u/2453968?v=4&s=48" width="48" height="48" alt="osolmaz" title="osolmaz"/></a> <a href="https://github.com/adityashaw2"><img src="https://avatars.githubusercontent.com/u/41204444?v=4&s=48" width="48" height="48" alt="adityashaw2" title="adityashaw2"/></a> <a href="https://github.com/CashWilliams"><img src="https://avatars.githubusercontent.com/u/613573?v=4&s=48" width="48" height="48" alt="CashWilliams" title="CashWilliams"/></a> <a href="https://github.com/search?q=sheeek"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="sheeek" title="sheeek"/></a> <a href="https://github.com/ryancontent"><img src="https://avatars.githubusercontent.com/u/39743613?v=4&s=48" width="48" height="48" alt="ryancontent" title="ryancontent"/></a> <a href="https://github.com/jasonsschin"><img src="https://avatars.githubusercontent.com/u/1456889?v=4&s=48" width="48" height="48" alt="jasonsschin" title="jasonsschin"/></a> <a href="https://github.com/artuskg"><img src="https://avatars.githubusercontent.com/u/11966157?v=4&s=48" width="48" height="48" alt="artuskg" title="artuskg"/></a> <a href="https://github.com/onutc"><img src="https://avatars.githubusercontent.com/u/152018508?v=4&s=48" width="48" height="48" alt="onutc" title="onutc"/></a> <a href="https://github.com/pauloportella"><img src="https://avatars.githubusercontent.com/u/22947229?v=4&s=48" width="48" height="48" alt="pauloportella" title="pauloportella"/></a>
  <a href="https://github.com/HirokiKobayashi-R"><img src="https://avatars.githubusercontent.com/u/37167840?v=4&s=48" width="48" height="48" alt="HirokiKobayashi-R" title="HirokiKobayashi-R"/></a> <a href="https://github.com/ThanhNguyxn"><img src="https://avatars.githubusercontent.com/u/8474903?v=4&s=48" width="48" height="48" alt="ThanhNguyxn" title="ThanhNguyxn"/></a> <a href="https://github.com/24601"><img src="https://avatars.githubusercontent.com/u/1157207?v=4&s=48" width="48" height="48" alt="24601" title="24601"/></a> <a href="https://github.com/ameno-"><img src="https://avatars.githubusercontent.com/u/2416135?v=4&s=48" width="48" height="48" alt="ameno-" title="ameno-"/></a> <a href="https://github.com/bonald"><img src="https://avatars.githubusercontent.com/u/12394874?v=4&s=48" width="48" height="48" alt="bonald" title="bonald"/></a> <a href="https://github.com/bravostation"><img src="https://avatars.githubusercontent.com/u/257991910?v=4&s=48" width="48" height="48" alt="bravostation" title="bravostation"/></a> <a href="https://github.com/search?q=Chris%20Taylor"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Chris Taylor" title="Chris Taylor"/></a> <a href="https://github.com/dguido"><img src="https://avatars.githubusercontent.com/u/294844?v=4&s=48" width="48" height="48" alt="dguido" title="dguido"/></a> <a href="https://github.com/djangonavarro220"><img src="https://avatars.githubusercontent.com/u/251162586?v=4&s=48" width="48" height="48" alt="Django Navarro" title="Django Navarro"/></a> <a href="https://github.com/evalexpr"><img src="https://avatars.githubusercontent.com/u/23485511?v=4&s=48" width="48" height="48" alt="evalexpr" title="evalexpr"/></a> <a href="https://github.com/henrino3"><img src="https://avatars.githubusercontent.com/u/4260288?v=4&s=48" width="48" height="48" alt="henrino3" title="henrino3"/></a> <a href="https://github.com/humanwritten"><img src="https://avatars.githubusercontent.com/u/206531610?v=4&s=48" width="48" height="48" alt="humanwritten" title="humanwritten"/></a>
  <a href="https://github.com/larlyssa"><img src="https://avatars.githubusercontent.com/u/13128869?v=4&s=48" width="48" height="48" alt="larlyssa" title="larlyssa"/></a> <a href="https://github.com/odysseus0"><img src="https://avatars.githubusercontent.com/u/8635094?v=4&s=48" width="48" height="48" alt="odysseus0" title="odysseus0"/></a> <a href="https://github.com/oswalpalash"><img src="https://avatars.githubusercontent.com/u/6431196?v=4&s=48" width="48" height="48" alt="oswalpalash" title="oswalpalash"/></a> <a href="https://github.com/pcty-nextgen-service-account"><img src="https://avatars.githubusercontent.com/u/112553441?v=4&s=48" width="48" height="48" alt="pcty-nextgen-service-account" title="pcty-nextgen-service-account"/></a> <a href="https://github.com/pi0"><img src="https://avatars.githubusercontent.com/u/5158436?v=4&s=48" width="48" height="48" alt="pi0" title="pi0"/></a> <a href="https://github.com/rmorse"><img src="https://avatars.githubusercontent.com/u/853547?v=4&s=48" width="48" height="48" alt="rmorse" title="rmorse"/></a> <a href="https://github.com/search?q=Roopak%20Nijhara"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Roopak Nijhara" title="Roopak Nijhara"/></a> <a href="https://github.com/Syhids"><img src="https://avatars.githubusercontent.com/u/671202?v=4&s=48" width="48" height="48" alt="Syhids" title="Syhids"/></a> <a href="https://github.com/search?q=Ubuntu"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Ubuntu" title="Ubuntu"/></a> <a href="https://github.com/search?q=xiaose"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="xiaose" title="xiaose"/></a>
  <a href="https://github.com/search?q=Aaron%20Konyer"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Aaron Konyer" title="Aaron Konyer"/></a> <a href="https://github.com/aaronveklabs"><img src="https://avatars.githubusercontent.com/u/225997528?v=4&s=48" width="48" height="48" alt="aaronveklabs" title="aaronveklabs"/></a> <a href="https://github.com/aldoeliacim"><img src="https://avatars.githubusercontent.com/u/17973757?v=4&s=48" width="48" height="48" alt="aldoeliacim" title="aldoeliacim"/></a> <a href="https://github.com/andreabadesso"><img src="https://avatars.githubusercontent.com/u/3586068?v=4&s=48" width="48" height="48" alt="andreabadesso" title="andreabadesso"/></a> <a href="https://github.com/search?q=Andrii"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Andrii" title="Andrii"/></a> <a href="https://github.com/BinaryMuse"><img src="https://avatars.githubusercontent.com/u/189606?v=4&s=48" width="48" height="48" alt="BinaryMuse" title="BinaryMuse"/></a> <a href="https://github.com/bqcfjwhz85-arch"><img src="https://avatars.githubusercontent.com/u/239267175?v=4&s=48" width="48" height="48" alt="bqcfjwhz85-arch" title="bqcfjwhz85-arch"/></a> <a href="https://github.com/cash-echo-bot"><img src="https://avatars.githubusercontent.com/u/252747386?v=4&s=48" width="48" height="48" alt="cash-echo-bot" title="cash-echo-bot"/></a> <a href="https://github.com/search?q=Clawd"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Clawd" title="Clawd"/></a> <a href="https://github.com/search?q=ClawdFx"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="ClawdFx" title="ClawdFx"/></a>
  <a href="https://github.com/search?q=damaozi"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="damaozi" title="damaozi"/></a> <a href="https://github.com/danballance"><img src="https://avatars.githubusercontent.com/u/13839912?v=4&s=48" width="48" height="48" alt="danballance" title="danballance"/></a> <a href="https://github.com/Elarwei001"><img src="https://avatars.githubusercontent.com/u/168552401?v=4&s=48" width="48" height="48" alt="Elarwei001" title="Elarwei001"/></a> <a href="https://github.com/EnzeD"><img src="https://avatars.githubusercontent.com/u/9866900?v=4&s=48" width="48" height="48" alt="EnzeD" title="EnzeD"/></a> <a href="https://github.com/erik-agens"><img src="https://avatars.githubusercontent.com/u/80908960?v=4&s=48" width="48" height="48" alt="erik-agens" title="erik-agens"/></a> <a href="https://github.com/Evizero"><img src="https://avatars.githubusercontent.com/u/10854026?v=4&s=48" width="48" height="48" alt="Evizero" title="Evizero"/></a> <a href="https://github.com/fcatuhe"><img src="https://avatars.githubusercontent.com/u/17382215?v=4&s=48" width="48" height="48" alt="fcatuhe" title="fcatuhe"/></a> <a href="https://github.com/gildo"><img src="https://avatars.githubusercontent.com/u/133645?v=4&s=48" width="48" height="48" alt="gildo" title="gildo"/></a> <a href="https://github.com/hclsys"><img src="https://avatars.githubusercontent.com/u/7755017?v=4&s=48" width="48" height="48" alt="hclsys" title="hclsys"/></a> <a href="https://github.com/itsjaydesu"><img src="https://avatars.githubusercontent.com/u/220390?v=4&s=48" width="48" height="48" alt="itsjaydesu" title="itsjaydesu"/></a>
  <a href="https://github.com/ivancasco"><img src="https://avatars.githubusercontent.com/u/2452858?v=4&s=48" width="48" height="48" alt="ivancasco" title="ivancasco"/></a> <a href="https://github.com/ivanrvpereira"><img src="https://avatars.githubusercontent.com/u/183991?v=4&s=48" width="48" height="48" alt="ivanrvpereira" title="ivanrvpereira"/></a> <a href="https://github.com/search?q=Jarvis"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Jarvis" title="Jarvis"/></a> <a href="https://github.com/jayhickey"><img src="https://avatars.githubusercontent.com/u/1676460?v=4&s=48" width="48" height="48" alt="jayhickey" title="jayhickey"/></a> <a href="https://github.com/jeffersonwarrior"><img src="https://avatars.githubusercontent.com/u/89030989?v=4&s=48" width="48" height="48" alt="jeffersonwarrior" title="jeffersonwarrior"/></a> <a href="https://github.com/search?q=jeffersonwarrior"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="jeffersonwarrior" title="jeffersonwarrior"/></a> <a href="https://github.com/jverdi"><img src="https://avatars.githubusercontent.com/u/345050?v=4&s=48" width="48" height="48" alt="jverdi" title="jverdi"/></a> <a href="https://github.com/longmaba"><img src="https://avatars.githubusercontent.com/u/9361500?v=4&s=48" width="48" height="48" alt="longmaba" title="longmaba"/></a> <a href="https://github.com/search?q=Marco%20Marandiz"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Marco Marandiz" title="Marco Marandiz"/></a> <a href="https://github.com/MarvinCui"><img src="https://avatars.githubusercontent.com/u/130876763?v=4&s=48" width="48" height="48" alt="MarvinCui" title="MarvinCui"/></a>
  <a href="https://github.com/mjrussell"><img src="https://avatars.githubusercontent.com/u/1641895?v=4&s=48" width="48" height="48" alt="mjrussell" title="mjrussell"/></a> <a href="https://github.com/odnxe"><img src="https://avatars.githubusercontent.com/u/403141?v=4&s=48" width="48" height="48" alt="odnxe" title="odnxe"/></a> <a href="https://github.com/optimikelabs"><img src="https://avatars.githubusercontent.com/u/31423109?v=4&s=48" width="48" height="48" alt="optimikelabs" title="optimikelabs"/></a> <a href="https://github.com/p6l-richard"><img src="https://avatars.githubusercontent.com/u/18185649?v=4&s=48" width="48" height="48" alt="p6l-richard" title="p6l-richard"/></a> <a href="https://github.com/philipp-spiess"><img src="https://avatars.githubusercontent.com/u/458591?v=4&s=48" width="48" height="48" alt="philipp-spiess" title="philipp-spiess"/></a> <a href="https://github.com/search?q=Pocke%20Clawd"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Pocket Clawd" title="Pocket Clawd"/></a> <a href="https://github.com/robaxelsen"><img src="https://avatars.githubusercontent.com/u/13132899?v=4&s=48" width="48" height="48" alt="robaxelsen" title="robaxelsen"/></a> <a href="https://github.com/search?q=Sash%20Catanzarite"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Sash Catanzarite" title="Sash Catanzarite"/></a> <a href="https://github.com/Suksham-sharma"><img src="https://avatars.githubusercontent.com/u/94667656?v=4&s=48" width="48" height="48" alt="Suksham-sharma" title="Suksham-sharma"/></a> <a href="https://github.com/T5-AndyML"><img src="https://avatars.githubusercontent.com/u/22801233?v=4&s=48" width="48" height="48" alt="T5-AndyML" title="T5-AndyML"/></a>
  <a href="https://github.com/tewatia"><img src="https://avatars.githubusercontent.com/u/22875334?v=4&s=48" width="48" height="48" alt="tewatia" title="tewatia"/></a> <a href="https://github.com/thejhinvirtuoso"><img src="https://avatars.githubusercontent.com/u/258521837?v=4&s=48" width="48" height="48" alt="thejhinvirtuoso" title="thejhinvirtuoso"/></a> <a href="https://github.com/travisp"><img src="https://avatars.githubusercontent.com/u/165698?v=4&s=48" width="48" height="48" alt="travisp" title="travisp"/></a> <a href="https://github.com/search?q=VAC"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="VAC" title="VAC"/></a> <a href="https://github.com/search?q=william%20arzt"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="william arzt" title="william arzt"/></a> <a href="https://github.com/yudshj"><img src="https://avatars.githubusercontent.com/u/16971372?v=4&s=48" width="48" height="48" alt="yudshj" title="yudshj"/></a> <a href="https://github.com/zknicker"><img src="https://avatars.githubusercontent.com/u/1164085?v=4&s=48" width="48" height="48" alt="zknicker" title="zknicker"/></a> <a href="https://github.com/0oAstro"><img src="https://avatars.githubusercontent.com/u/79555780?v=4&s=48" width="48" height="48" alt="0oAstro" title="0oAstro"/></a> <a href="https://github.com/abhaymundhara"><img src="https://avatars.githubusercontent.com/u/62872231?v=4&s=48" width="48" height="48" alt="abhaymundhara" title="abhaymundhara"/></a> <a href="https://github.com/aduk059"><img src="https://avatars.githubusercontent.com/u/257603478?v=4&s=48" width="48" height="48" alt="aduk059" title="aduk059"/></a>
  <a href="https://github.com/akramcodez"><img src="https://avatars.githubusercontent.com/u/179671552?v=4&s=48" width="48" height="48" alt="akramcodez" title="akramcodez"/></a> <a href="https://github.com/search?q=alejandro%20maza"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="alejandro maza" title="alejandro maza"/></a> <a href="https://github.com/Alex-Alaniz"><img src="https://avatars.githubusercontent.com/u/88956822?v=4&s=48" width="48" height="48" alt="Alex-Alaniz" title="Alex-Alaniz"/></a> <a href="https://github.com/alexanderatallah"><img src="https://avatars.githubusercontent.com/u/1011391?v=4&s=48" width="48" height="48" alt="alexanderatallah" title="alexanderatallah"/></a> <a href="https://github.com/alexstyl"><img src="https://avatars.githubusercontent.com/u/1665273?v=4&s=48" width="48" height="48" alt="alexstyl" title="alexstyl"/></a> <a href="https://github.com/AlexZhangji"><img src="https://avatars.githubusercontent.com/u/3280924?v=4&s=48" width="48" height="48" alt="AlexZhangji" title="AlexZhangji"/></a> <a href="https://github.com/andrewting19"><img src="https://avatars.githubusercontent.com/u/10536704?v=4&s=48" width="48" height="48" alt="andrewting19" title="andrewting19"/></a> <a href="https://github.com/anpoirier"><img src="https://avatars.githubusercontent.com/u/1245729?v=4&s=48" width="48" height="48" alt="anpoirier" title="anpoirier"/></a> <a href="https://github.com/araa47"><img src="https://avatars.githubusercontent.com/u/22760261?v=4&s=48" width="48" height="48" alt="araa47" title="araa47"/></a> <a href="https://github.com/arthyn"><img src="https://avatars.githubusercontent.com/u/5466421?v=4&s=48" width="48" height="48" alt="arthyn" title="arthyn"/></a>
  <a href="https://github.com/Asleep123"><img src="https://avatars.githubusercontent.com/u/122379135?v=4&s=48" width="48" height="48" alt="Asleep123" title="Asleep123"/></a> <a href="https://github.com/search?q=Ayush%20Ojha"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Ayush Ojha" title="Ayush Ojha"/></a> <a href="https://github.com/Ayush10"><img src="https://avatars.githubusercontent.com/u/7945279?v=4&s=48" width="48" height="48" alt="Ayush10" title="Ayush10"/></a> <a href="https://github.com/bguidolim"><img src="https://avatars.githubusercontent.com/u/987360?v=4&s=48" width="48" height="48" alt="bguidolim" title="bguidolim"/></a> <a href="https://github.com/bolismauro"><img src="https://avatars.githubusercontent.com/u/771999?v=4&s=48" width="48" height="48" alt="bolismauro" title="bolismauro"/></a> <a href="https://github.com/championswimmer"><img src="https://avatars.githubusercontent.com/u/1327050?v=4&s=48" width="48" height="48" alt="championswimmer" title="championswimmer"/></a> <a href="https://github.com/chenyuan99"><img src="https://avatars.githubusercontent.com/u/25518100?v=4&s=48" width="48" height="48" alt="chenyuan99" title="chenyuan99"/></a> <a href="https://github.com/Chloe-VP"><img src="https://avatars.githubusercontent.com/u/257371598?v=4&s=48" width="48" height="48" alt="Chloe-VP" title="Chloe-VP"/></a> <a href="https://github.com/search?q=Clawdbot%20Maintainers"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Clawdbot Maintainers" title="Clawdbot Maintainers"/></a> <a href="https://github.com/conhecendoia"><img src="https://avatars.githubusercontent.com/u/82890727?v=4&s=48" width="48" height="48" alt="conhecendoia" title="conhecendoia"/></a>
  <a href="https://github.com/dasilva333"><img src="https://avatars.githubusercontent.com/u/947827?v=4&s=48" width="48" height="48" alt="dasilva333" title="dasilva333"/></a> <a href="https://github.com/David-Marsh-Photo"><img src="https://avatars.githubusercontent.com/u/228404527?v=4&s=48" width="48" height="48" alt="David-Marsh-Photo" title="David-Marsh-Photo"/></a> <a href="https://github.com/deepsoumya617"><img src="https://avatars.githubusercontent.com/u/80877391?v=4&s=48" width="48" height="48" alt="deepsoumya617" title="deepsoumya617"/></a> <a href="https://github.com/search?q=Developer"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Developer" title="Developer"/></a> <a href="https://github.com/search?q=Dimitrios%20Ploutarchos"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Dimitrios Ploutarchos" title="Dimitrios Ploutarchos"/></a> <a href="https://github.com/search?q=Drake%20Thomsen"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Drake Thomsen" title="Drake Thomsen"/></a> <a href="https://github.com/dylanneve1"><img src="https://avatars.githubusercontent.com/u/31746704?v=4&s=48" width="48" height="48" alt="dylanneve1" title="dylanneve1"/></a> <a href="https://github.com/search?q=Felix%20Krause"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Felix Krause" title="Felix Krause"/></a> <a href="https://github.com/foeken"><img src="https://avatars.githubusercontent.com/u/13864?v=4&s=48" width="48" height="48" alt="foeken" title="foeken"/></a> <a href="https://github.com/frankekn"><img src="https://avatars.githubusercontent.com/u/4488090?v=4&s=48" width="48" height="48" alt="frankekn" title="frankekn"/></a>
  <a href="https://github.com/fredheir"><img src="https://avatars.githubusercontent.com/u/3304869?v=4&s=48" width="48" height="48" alt="fredheir" title="fredheir"/></a> <a href="https://github.com/search?q=ganghyun%20kim"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="ganghyun kim" title="ganghyun kim"/></a> <a href="https://github.com/grrowl"><img src="https://avatars.githubusercontent.com/u/907140?v=4&s=48" width="48" height="48" alt="grrowl" title="grrowl"/></a> <a href="https://github.com/gtsifrikas"><img src="https://avatars.githubusercontent.com/u/8904378?v=4&s=48" width="48" height="48" alt="gtsifrikas" title="gtsifrikas"/></a> <a href="https://github.com/HassanFleyah"><img src="https://avatars.githubusercontent.com/u/228002017?v=4&s=48" width="48" height="48" alt="HassanFleyah" title="HassanFleyah"/></a> <a href="https://github.com/HazAT"><img src="https://avatars.githubusercontent.com/u/363802?v=4&s=48" width="48" height="48" alt="HazAT" title="HazAT"/></a> <a href="https://github.com/hrdwdmrbl"><img src="https://avatars.githubusercontent.com/u/554881?v=4&s=48" width="48" height="48" alt="hrdwdmrbl" title="hrdwdmrbl"/></a> <a href="https://github.com/hugobarauna"><img src="https://avatars.githubusercontent.com/u/2719?v=4&s=48" width="48" height="48" alt="hugobarauna" title="hugobarauna"/></a> <a href="https://github.com/hyf0-agent"><img src="https://avatars.githubusercontent.com/u/258783736?v=4&s=48" width="48" height="48" alt="hyf0-agent" title="hyf0-agent"/></a> <a href="https://github.com/iamEvanYT"><img src="https://avatars.githubusercontent.com/u/47493765?v=4&s=48" width="48" height="48" alt="iamEvanYT" title="iamEvanYT"/></a>
  <a href="https://github.com/ichbinlucaskim"><img src="https://avatars.githubusercontent.com/u/125564751?v=4&s=48" width="48" height="48" alt="ichbinlucaskim" title="ichbinlucaskim"/></a> <a href="https://github.com/search?q=Jamie%20Openshaw"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Jamie Openshaw" title="Jamie Openshaw"/></a> <a href="https://github.com/search?q=Jane"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Jane" title="Jane"/></a> <a href="https://github.com/search?q=Jarvis%20Deploy"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Jarvis Deploy" title="Jarvis Deploy"/></a> <a href="https://github.com/search?q=Jefferson%20Nunn"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Jefferson Nunn" title="Jefferson Nunn"/></a> <a href="https://github.com/jogi47"><img src="https://avatars.githubusercontent.com/u/1710139?v=4&s=48" width="48" height="48" alt="jogi47" title="jogi47"/></a> <a href="https://github.com/kentaro"><img src="https://avatars.githubusercontent.com/u/3458?v=4&s=48" width="48" height="48" alt="kentaro" title="kentaro"/></a> <a href="https://github.com/search?q=Kevin%20Lin"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Kevin Lin" title="Kevin Lin"/></a> <a href="https://github.com/kira-ariaki"><img src="https://avatars.githubusercontent.com/u/257352493?v=4&s=48" width="48" height="48" alt="kira-ariaki" title="kira-ariaki"/></a> <a href="https://github.com/kitze"><img src="https://avatars.githubusercontent.com/u/1160594?v=4&s=48" width="48" height="48" alt="kitze" title="kitze"/></a> <a href="https://github.com/search?q=Mourad%20Boustani"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Mourad Boustani" title="Mourad Boustani"/></a> <a href="https://github.com/odrobnik"><img src="https://avatars.githubusercontent.com/u/333270?v=4&s=48" width="48" height="48" alt="odrobnik" title="odrobnik"/></a> <a href="https://github.com/pcty-nextgen-ios-builder"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="pcty-nextgen-ios-builder" title="pcty-nextgen-ios-builder"/></a> <a href="https://github.com/search?q=Quentin"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Quentin" title="Quentin"/></a> <a href="https://github.com/search?q=Randy%20Torres"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Randy Torres" title="Randy Torres"/></a> <a href="https://github.com/rhjoh"><img src="https://avatars.githubusercontent.com/u/105699450?v=4&s=48" width="48" height="48" alt="rhjoh" title="rhjoh"/></a> <a href="https://github.com/search?q=Rolf%20Fredheim"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Rolf Fredheim" title="Rolf Fredheim"/></a> <a href="https://github.com/ronak-guliani"><img src="https://avatars.githubusercontent.com/u/23518228?v=4&s=48" width="48" height="48" alt="ronak-guliani" title="ronak-guliani"/></a> <a href="https://github.com/search?q=William%20Stock"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="William Stock" title="William Stock"/></a>
</p>
