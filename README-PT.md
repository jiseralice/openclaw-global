# 🦞 OpenClaw — Assistente pessoal de IA

<p align="center">
    <picture>
        <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/openclaw/openclaw/main/docs/assets/openclaw-logo-text-dark.png">
        <img src="https://raw.githubusercontent.com/openclaw/openclaw/main/docs/assets/openclaw-logo-text.png" alt="OpenClaw" width="500">
    </picture>
</p>

<p align="center">
  <strong>Metamorfose! Metamorfose!</strong>
</p>

<p align="center">
  <a href="https://github.com/openclaw/openclaw/actions/workflows/ci.yml?branch=main"><img src="https://img.shields.io/github/actions/workflow/status/openclaw/openclaw/ci.yml?branch=main&style=for-the-badge" alt="Status CI"></a>
  <a href="https://github.com/openclaw/openclaw/releases"><img src="https://img.shields.io/github/v/release/openclaw/openclaw?include_prereleases&style=for-the-badge" alt="Versão GitHub"></a>
  <a href="https://discord.gg/clawd"><img src="https://img.shields.io/discord/1456350064065904867?label=Discord&logo=discord&logoColor=white&color=5865F2&style=for-the-badge" alt="Discord"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge" alt="Licença MIT"></a>
</p>

**OpenClaw** é um assistente de IA pessoal que executa em seus próprios dispositivos. Ele fornece suporte através de canais comuns (WhatsApp, Telegram, Slack, Discord, Google Chat, Signal, iMessage, Microsoft Teams, WebChat) bem como canais estendidos como BlueBubbles, Matrix, Zalo e Zalo Personal. É compatível com macOS/iOS/Android e pode renderizar interfaces Canvas em tempo real controladas por você. O gateway é apenas uma plataforma de controle, o produto em si é o verdadeiro assistente.
Se você está procurando por um assistente local, rápido e sempre online para um único usuário, este é o indicado.

[Site oficial](https://openclaw.ai) · [Documentação oficial](https://docs.openclaw.ai) · [DeepWiki](https://deepwiki.com/openclaw/openclaw) · [Guia de início](https://docs.openclaw.ai/start/getting-started) · [Atualizações](https://docs.openclaw.ai/install/updating) · [Exemplos](https://docs.openclaw.ai/start/showcase) · [Perguntas frequentes](https://docs.openclaw.ai/start/faq) · [Assistente](https://docs.openclaw.ai/start/wizard) · [Nix](https://github.com/openclaw/nix-clawdbot) · [Docker](https://docs.openclaw.ai/install/docker) · [Discord](https://discord.gg/clawd)

Configuração recomendada: Execute o assistente de configuração (`openclaw onboard`). Ele irá guiá-lo pela configuração do gateway, workspace, canais e habilidades. O assistente de linha de comando é o caminho recomendado e funciona em **macOS, Linux e Windows (via WSL2; fortemente recomendado)**.
Compatível com npm, pnpm ou bun. Nova instalação? Comece aqui: [Guia de início](https://docs.openclaw.ai/start/getting-started)

**Assinatura (OAuth):**

- **[Anthropic](https://www.anthropic.com/)** (Claude Pro/Max)
- **[OpenAI](https://openai.com/)** (ChatGPT/Codex)

Observações sobre modelos: Embora todos os modelos sejam suportados, eu fortemente recomendo **Anthropic Pro/Max (100/200) + Opus 4.6** para obter melhor desempenho de longa duração e maior resistência a interferências. Veja [Guia online](https://docs.openclaw.ai/start/onboarding).

## Modelos (Seleção + Autenticação)

- Configuração de modelos + CLI: [Modelos](https://docs.openclaw.ai/concepts/models)
- Perfis de autenticação (OAuth vs chaves de API) + fallback: [Fallback de modelo](https://docs.openclaw.ai/concepts/model-failover)

## Instalação

Ambiente de execução: **Node ≥22**.

```bash
npm install -g openclaw@latest
# ou: pnpm add -g openclaw@latest

openclaw onboard --install-daemon
```

O assistente instala o daemon do gateway (serviço de usuário launchd/systemd) para mantê-lo em execução.

## Início rápido (Resumo)

Ambiente de execução: **Node ≥22**.

Guia completo para iniciantes (autenticação, pareamento, canais): [Guia de início](https://docs.openclaw.ai/start/getting-started)

```bash
openclaw onboard --install-daemon

openclaw gateway --port 18789 --verbose

# Enviar mensagem
openclaw message send --to +1234567890 --message "Olá do OpenClaw"

# Conversar com o assistente (você pode enviar qualquer mensagem aos canais conectados: WhatsApp/Telegram/Slack/Discord/Google Chat/Signal/iMessage/BlueBubbles/Microsoft Teams/Matrix/Zalo/Zalo Personal/WebChat)
openclaw agent --message "Lista de verificação do navio" --thinking high
```

Como atualizar? [Guia de atualização](https://docs.openclaw.ai/install/updating) (execute `openclaw doctor`).

## Explicação do status da versão de desenvolvimento

- **stable**: versões com tag (`vYYYY.M.D` ou `vYYYY.M.D-<patch>`), npm dist-tag `latest`.
- **beta**: versões pré-lançamento (`vYYYY.M.D-beta.N`), npm dist-tag `beta` (o aplicativo macOS pode estar ausente).
- **dev**: cabeça móvel do `main`, npm dist-tag `dev` (quando publicado).

Alternar (git + npm): `openclaw update --channel stable|beta|dev`.
Detalhes: [Status das versões de desenvolvimento](https://docs.openclaw.ai/install/development-channels).

## Fonte (Desenvolvimento)

Recomenda-se `pnpm` para builds a partir do código-fonte. Bun é opcional para executar TypeScript diretamente.

```bash
git clone https://github.com/openclaw/openclaw.git
cd openclaw

pnpm install
pnpm ui:build # instala automaticamente dependências de UI na primeira execução
pnpm build

pnpm openclaw onboard --install-daemon

# Loop de desenvolvimento (recarga automática nas alterações do TS)
pnpm gateway:watch
```

Nota: `pnpm openclaw ...` executa diretamente TypeScript (através do `tsx`). `pnpm build` gera `dist/` para executar/empacotar o binário `openclaw` via Node.

## Configurações de segurança padrão (Permissões de DM)

OpenClaw se conecta a plataformas reais de mensagens instantâneas. Trate mensagens diretas recebidas como **entradas não confiáveis**.

Guia completo de segurança: [Guia de segurança](https://docs.openclaw.ai/gateway/security)

Comportamento padrão para Telegram/WhatsApp/Signal/iMessage/Microsoft Teams/Discord/Google Chat/Slack:

- **Pareamento de DM** (`dmPolicy="pairing"` / `channels.discord.dm.policy="pairing"` / `channels.slack.dm.policy="pairing"`): Remetentes desconhecidos recebem um código curto de pareamento, o bot não processa suas mensagens.
- Aprovação: `openclaw pairing approve <channel> <code>` (então adiciona o remetente ao armazenamento local).
- Mensagens diretas públicas recebidas exigem adesão explícita: Defina `dmPolicy="open"` e inclua `"*"` na lista de permissão do canal (`allowFrom` / `channels.discord.dm.allowFrom` / `channels.slack.dm.allowFrom`).

Execute `openclaw doctor` para descobrir políticas de DM com risco/configuração incorreta.

## Pontos principais

- **[Gateway com prioridade local](https://docs.openclaw.ai/gateway)** — Plano de controle único para sessões, canais, ferramentas e eventos.
- **[Caixa de entrada multicanal](https://docs.openclaw.ai/channels)** — WhatsApp, Telegram, Slack, Discord, Google Chat, Signal, BlueBubbles (iMessage), iMessage (legado), Microsoft Teams, Matrix, Zalo, Zalo Personal, WebChat, macOS, iOS/Android.
- **[Roteamento multiagente](https://docs.openclaw.ai/gateway/configuration)** — Roteamento de canais/contas/pares recebidos para agentes isolados (workspace + sessão por agente).
- **[Ativação por voz](https://docs.openclaw.ai/nodes/voicewake) + [Modo conversa](https://docs.openclaw.ai/nodes/talk)** — Funcionalidade de voz sempre ativa da ElevenLabs para macOS/iOS/Android.
- **[Canvas ao vivo](https://docs.openclaw.ai/platforms/mac/canvas)** — Workspace visual baseado em agente usando [A2UI](https://docs.openclaw.ai/platforms/mac/canvas#canvas-a2ui).
- **[Ferramentas de primeira classe](https://docs.openclaw.ai/tools)** — Navegador, Canvas, Nós, tarefas cron, Sessões e operações do Discord/Slack.
- **[Aplicativos companheiros](https://docs.openclaw.ai/platforms/macos)** — Aplicativo da barra de menu do macOS + [Nós](https://docs.openclaw.ai/nodes) iOS/Android.
- **[Assistente](https://docs.openclaw.ai/start/wizard) + [Habilidades](https://docs.openclaw.ai/tools/skills)** — Configuração assistida com habilidades agrupadas/gerenciadas/do workspace.

## Histórico de estrelas

[![Gráfico histórico de estrelas](https://api.star-history.com/svg?repos=openclaw/openclaw&type=date&legend=top-left)](https://www.star-history.com/#openclaw/openclaw&type=date&legend=top-left)

## O que fizemos até agora

### Plataforma central

- [Painel de controle do gateway](https://docs.openclaw.ai/gateway) incluindo sessões, status, configuração, tarefas cron, webhooks, [IU interativa](https://docs.openclaw.ai/web) e [Host do Canvas](https://docs.openclaw.ai/platforms/mac/canvas#canvas-a2ui).
- [Interface CLI](https://docs.openclaw.ai/tools/agent-send): Gateway, Agente, Enviar, [Assistente](https://docs.openclaw.ai/start/wizard) e [Segurança](https://docs.openclaw.ai/gateway/doctor).
- [Tempo de execução do agente Pi](https://docs.openclaw.ai/concepts/agent) com padrão RPC, suporte a streaming de ferramentas e streaming em blocos.
- [Modelo de sessão](https://docs.openclaw.ai/concepts/session): `main` para bate-papo direto, isolamento de grupo, modo de ativação, modo de fila, respostas. Regras de grupo: [Grupos](https://docs.openclaw.ai/concepts/groups).
- [Canais multimídia](https://docs.openclaw.ai/nodes/images): Imagens/Áudio/Vídeo, ganchos de transcrição, limites de tamanho, ciclo de vida de arquivos temporários. Detalhes de áudio: [Áudio](https://docs.openclaw.ai/nodes/audio).

### Canais

- [Canais](https://docs.openclaw.ai/channels): [WhatsApp](https://docs.openclaw.ai/channels/whatsapp) (Baileys), [Telegram](https://docs.openclaw.ai/channels/telegram) (grammY), [Slack](https://docs.openclaw.ai/channels/slack) (Bolt), [Discord](https://docs.openclaw.ai/channels/discord) (discord.js), [Google Chat](https://docs.openclaw.ai/channels/googlechat) (API de Chat), [Signal](https://docs.openclaw.ai/channels/signal) (signal-cli), [BlueBubbles](https://docs.openclaw.ai/channels/bluebubbles) (iMessage, recomendado), [iMessage](https://docs.openclaw.ai/channels/imessage) (imsg legado), [Microsoft Teams](https://docs.openclaw.ai/channels/msteams) (extensão), [Matrix](https://docs.openclaw.ai/channels/matrix) (extensão), [Zalo](https://docs.openclaw.ai/channels/zalo) (extensão), [Zalo Personal](https://docs.openclaw.ai/channels/zalouser) (extensão), [WebChat](https://docs.openclaw.ai/web/webchat).
- [Roteamento de grupo](https://docs.openclaw.ai/concepts/group-messages): Controle por menções, tags de resposta, fragmentação e roteamento por canal. Regras de canal: [Canais](https://docs.openclaw.ai/channels).

### Aplicativos + Nós

- [Aplicativo macOS](https://docs.openclaw.ai/platforms/macos): Painel de controle da barra de menu, [Ativação por voz](https://docs.openclaw.ai/nodes/voicewake)/PTT, sobreposição do [Modo conversa](https://docs.openclaw.ai/nodes/talk), [WebChat](https://docs.openclaw.ai/web/webchat), ferramentas de depuração, controle [Gateway remoto](https://docs.openclaw.ai/gateway/remote).
- [Nós iOS](https://docs.openclaw.ai/platforms/ios): [Canvas](https://docs.openclaw.ai/platforms/mac/canvas), [Ativação por voz](https://docs.openclaw.ai/nodes/voicewake), [Modo conversa](https://docs.openclaw.ai/nodes/talk), câmera, gravação de tela, pareamento Bonjour.
- [Nós Android](https://docs.openclaw.ai/platforms/android): [Canvas](https://docs.openclaw.ai/platforms/mac/canvas), [Modo conversa](https://docs.openclaw.ai/nodes/talk), câmera, gravação de tela, recursos opcionais de SMS.
- [Modo nó macOS](https://docs.openclaw.ai/nodes): Execução do sistema/notificações + exposição de câmera/canvas.

### Ferramentas + Automação

- [Controle do navegador](https://docs.openclaw.ai/tools/browser): Chrome/Chromium dedicado ao openclaw, capturas de tela, ações, uploads, perfis.
- [Canvas](https://docs.openclaw.ai/platforms/mac/canvas): [A2UI](https://docs.openclaw.ai/platforms/mac/canvas#canvas-a2ui) Push/Reset, avaliação, capturas de tela.
- [Nós](https://docs.openclaw.ai/nodes): Capturas/gravações da câmera, gravação de tela, [obtenção de localização](https://docs.openclaw.ai/nodes/location-command), notificações
- [Tarefas Cron + Ativação](https://docs.openclaw.ai/automation/cron-jobs); [webhooks](https://docs.openclaw.ai/automation/webhook); [Gmail Pub/Sub](https://docs.openclaw.ai/automation/gmail-pubsub).
- [Plataforma de habilidades](https://docs.openclaw.ai/tools/skills): Habilidades agrupadas, gerenciadas e do workspace com restrições de instalação e interface de usuário.

### Operações + Segurança

- [Roteamento de canal](https://docs.openclaw.ai/concepts/channel-routing), [Política de repetição](https://docs.openclaw.ai/concepts/retry) e [Streaming/fragmentação](https://docs.openclaw.ai/concepts/streaming).
- [Presença](https://docs.openclaw.ai/concepts/presence), [Indicadores de digitação](https://docs.openclaw.ai/concepts/typing-indicators) e [Rastreamento de uso](https://docs.openclaw.ai/concepts/usage-tracking).
- [Modelos](https://docs.openclaw.ai/concepts/models), [Fallback de modelo](https://docs.openclaw.ai/concepts/model-failover) e [Sessões](https://docs.openclaw.ai/concepts/session-pruning).
- [Segurança](https://docs.openclaw.ai/gateway/security) e [Solução de problemas](https://docs.openclaw.ai/channels/troubleshooting).

### Operações + Pacotes

- [Interface de controle](https://docs.openclaw.ai/web) + [WebChat](https://docs.openclaw.ai/web/webchat) fornecidos diretamente pelo gateway.
- [Tailscale Serve/Funnel](https://docs.openclaw.ai/gateway/tailscale) ou [Túneis SSH](https://docs.openclaw.ai/gateway/remote) com autenticação por token/senha
- [Modo Nix](https://docs.openclaw.ai/install/nix) suporta configuração declarativa; instalação baseada em [Docker](https://docs.openclaw.ai/install/docker)
- [Segurança](https://docs.openclaw.ai/gateway/doctor) fallback de segurança, [Logging](https://docs.openclaw.ai/logging).

## Como funciona (resumo breve)

```
WhatsApp / Telegram / Slack / Discord / Google Chat / Signal / iMessage / BlueBubbles / Microsoft Teams / Matrix / Zalo / Zalo Personal / WebChat
               │
               ▼
┌───────────────────────────────┐
│            Gateway            │
│       (plano de controle)     │
│     ws://127.0.0.1:18789     │
└──────────────┬────────────────┘
               │
               ├─ agente Pi (RPC)
               ├─ CLI (openclaw …)
               ├─ IU WebChat
               ├─ aplicativo macOS
               └─ nós iOS / Android
```

## Subsistemas principais

- **[Comunicação WebSocket do Gateway](https://docs.openclaw.ai/concepts/architecture)** — Plano de controle WS único para clientes, ferramentas e eventos (e operações: [Manual do Gateway](https://docs.openclaw.ai/gateway)).
- **[Exposição Tailscale](https://docs.openclaw.ai/gateway/tailscale)** — Serve/Funnel + WS para painel de controle do Gateway (acesso remoto: [Acesso remoto](https://docs.openclaw.ai/gateway/remote)).
- **[Controle do navegador](https://docs.openclaw.ai/tools/browser)** — Chrome/Chromium gerenciado pelo openclaw com controle CDP.
- **[Canvas + A2UI](https://docs.openclaw.ai/platforms/mac/canvas)** — Workspace visual baseado em agente (host A2UI: [Canvas/A2UI](https://docs.openclaw.ai/platforms/mac/canvas#canvas-a2ui)).
- **[Ativação por voz](https://docs.openclaw.ai/nodes/voicewake) + [Modo conversa](https://docs.openclaw.ai/nodes/talk)** — Funcionalidade de voz sempre ativa para conversas contínuas.
- **[Nós](https://docs.openclaw.ai/nodes)** — Canvas, capturas/gravações da câmera, gravação de tela, `location.get`, notificações, bem como funções específicas do macOS `system.run`/`system.notify`.

## Acesso Tailscale (painel de controle do Gateway)

OpenClaw pode configurar automaticamente o Tailscale **Serve** (somente tailnet) ou **Funnel** (público) enquanto mantém o gateway vinculado à interface de loopback. Configure `gateway.tailscale.mode`:

- `off`: Sem automação Tailscale (padrão).
- `serve`: Somente HTTPS tailnet via `tailscale serve` (usa cabeçalhos Tailscale por padrão).
- `funnel`: HTTPS público via `tailscale funnel` (requer autenticação com senha compartilhada).

Explicações:

- `gateway.bind` deve permanecer `loopback` quando Serve/Funnel estiver ativado (OpenClaw impõe isso).
- Force uma senha de servidor definindo `gateway.auth.mode: "password"` ou `gateway.auth.allowTailscale: false`.
- Negue a execução a menos que `gateway.auth.mode: "password"` já tenha sido definido.
- Opcional `gateway.tailscale.resetOnExit` revoga as operações Serve/Funnel na desativação.

Detalhes: [Guia Tailscale](https://docs.openclaw.ai/gateway/tailscale) · [Página Web](https://docs.openclaw.ai/web)

## Gateway remoto (melhor compatibilidade Linux)

É perfeitamente aceitável executar o gateway em uma pequena instância Linux. Clientes (aplicativo macOS, CLI, WebChat) podem se conectar via **Tailscale Serve/Funnel** ou **túneis SSH**, e você ainda pode emparelhar nós de dispositivo (macOS/iOS/Android) conforme necessário para executar operações locais no dispositivo.

- **Host do Gateway** normalmente executa ferramentas e estabelece conexões de canal.
- **Nós de dispositivo** executam operações locais no dispositivo (como `system.run`, câmera, gravação de tela, notificações) via `node.invoke`.
  Em resumo: execução ocorre onde o gateway está; operações do dispositivo ocorrem onde o dispositivo está.

Detalhes: [Acesso remoto](https://docs.openclaw.ai/gateway/remote) · [Nós](https://docs.openclaw.ai/nodes) · [Segurança](https://docs.openclaw.ai/gateway/security)

## Permissões do macOS via protocolo de Gateway

O aplicativo macOS pode executar em **modo nó** e transmitir suas capacidades e mapeamentos de permissão via WebSocket do Gateway (`node.list` / `node.describe`). Clientes podem então executar operações locais via `node.invoke`:

- `system.run` executa comandos locais e retorna stdout/stderr/código de saída; defina `needsScreenRecording: true` para permissões de gravação de tela (caso contrário você receberá o erro `PERMISSION_MISSING`).
- `system.notify` envia uma notificação ao usuário, falha se a notificação for recusada.
- `canvas.*`, `camera.*`, `screen.record` e `location.get` são roteados via `node.invoke` e seguem o estado de permissões TCC.

Permissões elevadas de bash (permissões de host) e TCC do macOS são separadas:

- Use `/elevated on|off` para alternar acesso elevado por sessão quando ativado + adicionado à lista de permissão.
- O Gateway persiste cada troca de sessão via (métodos WS) bem como `sessions.patch`, `thinkingLevel`, `verboseLevel`, `model`, `sendPolicy` e `groupActivation`.

Detalhes: [Nós](https://docs.openclaw.ai/nodes) · [Aplicativo macOS](https://docs.openclaw.ai/platforms/macos) · [Protocolo de Gateway](https://docs.openclaw.ai/concepts/architecture)

## Agente para Agente (ferramentas sessions_*)

- Este recurso permite coordenar trabalho entre sessões sem alternar entre interfaces de bate-papo.
- `sessions_list` — Descobre sessões (agentes) ativas e seus metadados.
- `sessions_history` — Recupera logs registrados da sessão.
- `sessions_send` — Envia uma mensagem para outra sessão; etapas opcionais de resposta ping-pong + anúncio (REPLY_SKIP, ANNOUNCE_SKIP).

Detalhes: [Ferramentas de sessão](https://docs.openclaw.ai/concepts/session-tool)

## Registro de habilidades (ClawHub)

ClawHub é um sistema mínimo de registro de habilidades. Uma vez ativado o ClawHub, o agente pode pesquisar automaticamente habilidades e adicionar novas conforme necessário.

[ClawHub](https://clawhub.com)

## Comandos de bate-papo

Envie estes via WhatsApp/Telegram/Slack/Google Chat/Microsoft Teams/WebChat (comandos de grupo apenas para administradores de grupo):

- `/status` — Status de sessão conciso (modelo + tokens, e custos quando disponíveis)
- `/new` ou `/reset` — Redefinir sessão
- `/compact` — Contexto de sessão conciso (resumo)
- `/think <level>` — off|minimal|low|medium|high|xhigh (apenas para modelos GPT-5.2 + Codex)
- `/verbose on|off`
- `/usage off|tokens|full` — Uso de tokens por resposta
- `/restart` — Reiniciar gateway (apenas para administradores de grupo)
- `/activation mention|always` — Alternar ativação em grupo (apenas para grupos)

## Aplicativos (Opcional)

O gateway em si fornece uma experiência excelente. Todos os aplicativos são opcionais e adicionam funcionalidades extras.

Se você pretende construir/executar aplicativos complementares, siga os manuais específicos da plataforma.

### macOS (OpenClaw.app) (Opcional)

- Controles da barra de menu para gateway e saúde.
- Ativação por voz + sobreposição de chamada com um clique.
- WebChat + ferramentas de depuração.
- Controle remoto do gateway via SSH.

Nota: Requer uma compilação assinada para que as permissões do macOS permaneçam após a reconstrução (veja `docs/mac/permissions.md`).

### Nó iOS (Opcional)

- Emparelhar nó como um dispositivo de ponte.
- Encaminhamento de gatilho por voz + superfície Canvas.
- Controlado via `openclaw nodes …`.

Manual: [Conexão iOS](https://docs.openclaw.ai/platforms/ios).

### Nó Android (Opcional)

- Emparelhamento via o mesmo fluxo de Ponte + Emparelhamento do iOS.
- Permite comandos Canvas, Câmera e Captura de tela.
- Manual: [Conexão Android](https://docs.openclaw.ai/platforms/android).

## Espaço de trabalho e Habilidades do Agente

- Diretório raiz do espaço de trabalho: `~/.openclaw/workspace` (configurável via `agents.defaults.workspace`).
- Arquivos de prompt injetados: `AGENTS.md`, `SOUL.md`, `TOOLS.md`.
- Habilidades: `~/.openclaw/workspace/skills/<skill>/SKILL.md`.

## Configuração

Configuração mínima `~/.openclaw/openclaw.json` (modelo + padrões):

```json5
{
  agent: {
    model: "anthropic/claude-opus-4-6",
  },
}
```

[Referência completa de configuração (todas as chaves e exemplos).](https://docs.openclaw.ai/gateway/configuration)

## Modo seguro (importante)

- **Por padrão:** As ferramentas são executadas no host como sessão principal, portanto, quando você é o único usuário, o agente tem acesso total.
- **Segurança para canais/grupos:** Execute cada sessão como ambiente isolado dentro do Docker com `agents.defaults.sandbox.mode: "non-main"` como **sessões não principais** (canais/grupos); em seguida, execute-as como sessão bash dentro do Docker.
- **Ambiente isolado padrão:** Permite a execução de `bash`, `process`, `read`, `write`, `edit`, `sessions_list`, `sessions_history`, `sessions_send`, `sessions_spawn`; proíbe `browser`, `canvas`, `nodes`, `cron`, `discord`, `gateway`.

Detalhes: [Diretrizes de segurança](https://docs.openclaw.ai/gateway/security) · [Docker + Ambiente isolado](https://docs.openclaw.ai/install/docker) · [Configuração do ambiente isolado](https://docs.openclaw.ai/gateway/configuration)

### [WhatsApp](https://docs.openclaw.ai/channels/whatsapp)

- Vincular dispositivo: `pnpm openclaw channels login` (credenciais armazenadas em `~/.openclaw/credentials`).
- Permitir que usuários adicionados à lista de permissões conversem com o assistente via `channels.whatsapp.allowFrom`.
- Se `channels.whatsapp.groups` estiver definido, ele se tornará uma lista de permissão de grupos; incluir `"*"` permitirá todos os grupos.

### [Telegram](https://docs.openclaw.ai/channels/telegram)

- Defina `TELEGRAM_BOT_TOKEN` ou `channels.telegram.botToken` (variáveis de ambiente têm precedência).
- Opcional: Defina `channels.telegram.groups` (com `channels.telegram.groups."*".requireMention`); uma vez definido, cria uma lista de permissão (incluir `"*"` permitirá todos); use `channels.telegram.allowFrom` ou `channels.telegram.webhookUrl` + `channels.telegram.webhookSecret` quando necessário.

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

- Defina `SLACK_BOT_TOKEN` + `SLACK_APP_TOKEN` (ou `channels.slack.botToken` + `channels.slack.appToken`).

### [Discord](https://docs.openclaw.ai/channels/discord)

- Defina `DISCORD_BOT_TOKEN` ou `channels.discord.token` (variáveis de ambiente têm precedência).
- Opcional: Defina `commands.native`, `commands.text`, ou `commands.useAccessGroups`, e `channels.discord.dm.allowFrom`, `channels.discord.guilds`, ou `channels.discord.mediaMaxMb` quando necessário.

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

- Requer `signal-cli` e uma configuração `channels.signal`.

### [BlueBubbles (iMessage)](https://docs.openclaw.ai/channels/bluebubbles)

- Solução **recomendada** para integração iMessage
- Configure `channels.bluebubbles.serverUrl` + `channels.bluebubbles.password` e um webhook (`channels.bluebubbles.webhookPath`).
- Servidor BlueBubbles executa no macOS; gateway pode executar no macOS ou em outros sistemas.

### [iMessage (legado)](https://docs.openclaw.ai/channels/imessage)

- Integração legada macOS apenas para `imsg` (deve estar logado no aplicativo Mensagens).
- Se `channels.imessage.groups` estiver definido, ele se tornará uma lista de permissão; incluir `"*"` permitirá todos.

### [Microsoft Teams](https://docs.openclaw.ai/channels/msteams)

- Configure o aplicativo Teams + Bot Framework, depois adicione a configuração `msteams`.
- Lista de permissão `msteams.allowFrom`; grupos via `msteams.groupAllowFrom` ou `msteams.groupPolicy: "open"`.

### [WebChat](https://docs.openclaw.ai/web/webchat)

- Usa o WebSocket do gateway; nenhuma porta/configuração separada do WebChat.

Controle do navegador (opcional):

```json5
{
  browser: {
    enabled: true,
    color: "#FF4500",
  },
}
```

## Documentação

Quando você terminar o processo de integração e precisar de referências mais profundas, estas estão disponíveis.

- [Primeiro, veja o índice da documentação para navegação e "onde está o conteúdo".](https://docs.openclaw.ai)
- [Leia a visão geral da arquitetura do gateway + modelo de protocolo.](https://docs.openclaw.ai/concepts/architecture)
- [Use a referência completa de configuração quando precisar de todas as chaves e exemplos.](https://docs.openclaw.ai/gateway/configuration)
- [Siga o manual de operação do gateway à risca.](https://docs.openclaw.ai/gateway)
- [Entenda como a UI de controle/Web funciona e como expô-las com segurança.](https://docs.openclaw.ai/web)
- [Entenda o acesso remoto via túneis SSH ou tailnet.](https://docs.openclaw.ai/gateway/remote)
- [Siga o processo de configuração assistida.](https://docs.openclaw.ai/start/wizard)
- [Conecte gatilhos externos via interface webhook.](https://docs.openclaw.ai/automation/webhook)
- [Configure gatilhos Gmail Pub/Sub.](https://docs.openclaw.ai/automation/gmail-pubsub)
- [Entenda mais sobre o assistente da barra de menu do macOS.](https://docs.openclaw.ai/platforms/mac/menu-bar)
- [Guias da plataforma: Windows (WSL2)](https://docs.openclaw.ai/platforms/windows), [Linux](https://docs.openclaw.ai/platforms/linux), [macOS](https://docs.openclaw.ai/platforms/macos), [iOS](https://docs.openclaw.ai/platforms/ios), [Android](https://docs.openclaw.ai/platforms/android)
- [Use o guia de solução de problemas para diagnosticar falhas comuns.](https://docs.openclaw.ai/channels/troubleshooting)
- [Leia as diretrizes de segurança antes de divulgar qualquer informação.](https://docs.openclaw.ai/gateway/security)

## Documentação avançada (descoberta + controle)

- [Descoberta + transformação](https://docs.openclaw.ai/gateway/discovery)
- [Bonjour/mDNS](https://docs.openclaw.ai/gateway/bonjour)
- [Emparelhamento do gateway](https://docs.openclaw.ai/gateway/pairing)
- [README do gateway remoto](https://docs.openclaw.ai/gateway/remote-gateway-readme)
- [Interface de controle](https://docs.openclaw.ai/web/control-ui)
- [Dashboard](https://docs.openclaw.ai/web/dashboard)

## Operação e solução de problemas

- [Verificação de integridade](https://docs.openclaw.ai/gateway/health)
- [Bloqueio do gateway](https://docs.openclaw.ai/gateway/gateway-lock)
- [Processo em segundo plano](https://docs.openclaw.ai/gateway/background-process)
- [Solução de problemas do navegador (Linux)](https://docs.openclaw.ai/tools/browser-linux-troubleshooting)
- [Registro](https://docs.openclaw.ai/logging)

## Exploração profunda

- [Loop do agente](https://docs.openclaw.ai/concepts/agent-loop)
- [Presença em tempo real](https://docs.openclaw.ai/concepts/presence)
- [Esquema TypeBox](https://docs.openclaw.ai/concepts/typebox)
- [Adaptadores RPC](https://docs.openclaw.ai/reference/rpc)
- [Filas](https://docs.openclaw.ai/concepts/queue)

## Espaço de trabalho e habilidades

- [Configuração de habilidades](https://docs.openclaw.ai/tools/skills-config)
- [Agente padrão](https://docs.openclaw.ai/reference/AGENTS.default)
- [Modelos: Agente](https://docs.openclaw.ai/reference/templates/AGENTS)
- [Modelos: BOOTSTRAP](https://docs.openclaw.ai/reference/templates/BOOTSTRAP)
- [Modelos: IDENTIDADE](https://docs.openclaw.ai/reference/templates/IDENTITY)
- [Modelos: ALMA](https://docs.openclaw.ai/reference/templates/SOUL)
- [Modelos: FERRAMENTAS](https://docs.openclaw.ai/reference/templates/TOOLS)
- [Modelos: USUÁRIO](https://docs.openclaw.ai/reference/templates/USER)

## Internos da plataforma

- [Ambiente de desenvolvimento macOS](https://docs.openclaw.ai/platforms/mac/dev-setup)
- [Barra de menu macOS](https://docs.openclaw.ai/platforms/mac/menu-bar)
- [Ativação por voz macOS](https://docs.openclaw.ai/platforms/mac/voicewake)
- [Nós iOS](https://docs.openclaw.ai/platforms/ios)
- [Nós Android](https://docs.openclaw.ai/platforms/android)
- [Windows (WSL2)](https://docs.openclaw.ai/platforms/windows)
- [Aplicativos Linux](https://docs.openclaw.ai/platforms/linux)

## Hooks de e-mail (Gmail)

- [docs.openclaw.ai/gmail-pubsub](https://docs.openclaw.ai/automation/gmail-pubsub)

## Molty

OpenClaw foi desenvolvido para o assistente de IA **Molty** caranguejo espacial. 🦞
Criado por Peter Steinberger e comunidade.

- [openclaw.ai](https://openclaw.ai)
- [soul.md](https://soul.md)
- [steipete.me](https://steipete.me)
- [@openclaw](https://x.com/openclaw)

## Comunidade

Consulte o arquivo [CONTRIBUTING.md](CONTRIBUTING.md) para diretrizes de contribuição, informações sobre mantenedores e como enviar PRs. PRs de codificação AI/vibe são bem-vindos! 🤖

Agradecimento especial a [Mario Zechner](https://mariozechner.at/) por seu apoio e por desenvolver o
[pi-mono](https://github.com/badlogic/pi-mono).
Agradecimento especial a Adam Doppelt por desenvolver o lobster.bot.

Agradecemos a todos os colaboradores:

<p align="left">
  <a href="https://github.com/steipete"><img src="https://avatars.githubusercontent.com/u/58493?v=4&s=48" width="48" height="48" alt="steipete" title="steipete"/></a> <a href="https://github.com/joshp123"><img src="https://avatars.githubusercontent.com/u/1497361?v=4&s=48" width="48" height="48" alt="joshp123" title="joshp123"/></a> <a href="https://github.com/cpojer"><img src="https://avatars.githubusercontent.com/u/13352?v=4&s=48" width="48" height="48" alt="cpojer" title="cpojer"/></a> <a href="https://github.com/mbelinky"><img src="https://avatars.githubusercontent.com/u/132747814?v=4&s=48" width="48" height="48" alt="Mariano Belinky" title="Mariano Belinky"/></a> <a href="https://github.com/plum-dawg"><img src="https://avatars.githubusercontent.com/u/5909950?v=4&s=48" width="48" height="48" alt="plum-dawg" title="plum-dawg"/></a> <a href="https://github.com/bohdanpodvirnyi"><img src="https://avatars.githubusercontent.com/u/31819391?v=4&s=48" width="48" height="48" alt="bohdanpodvirnyi" title="bohdanpodvirnyi"/></a> <a href="https://github.com/iHildy"><img src="https://avatars.githubusercontent.com/u/25069719?v=4&s=48" width="48" height="48" alt="iHildy" title="iHildy"/></a> <a href="https://github.com/jaydenfyi"><img src="https://avatars.githubusercontent.com/u/213395523?v=4&s=48" width="48" height="48" alt="jaydenfyi" title="jaydenfyi"/></a> <a href="https://github.com/joaohlisboa"><img src="https://avatars.githubusercontent.com/u/8200873?v=4&s=48" width="48" height="48" alt="joaohlisboa" title="joaohlisboa"/></a> <a href="https://github.com/mneves75"><img src="https://avatars.githubusercontent.com/u/2423436?v=4&s=48" width="48" height="48" alt="mneves75" title="mneves75"/></a>
  <a href="https://github.com/MatthieuBizien"><img src="https://avatars.githubusercontent.com/u/173090?v=4&s=48" width="48" height="48" alt="MatthieuBizien" title="MatthieuBizien"/></a> <a href="https://github.com/MaudeBot"><img src="https://avatars.githubusercontent.com/u/255777700?v=4&s=48" width="48" height="48" alt="MaudeBot" title="MaudeBot"/></a> <a href="https://github.com/sebslight"><img src="https://avatars.githubusercontent.com/u/19554889?v=4&s=48" width="48" height="48" alt="sebslight" title="sebslight"/></a> <a href="https://github.com/Glucksberg"><img src="https://avatars.githubusercontent.com/u/80581902?v=4&s=48" width="48" height="48" alt="Glucksberg" title="Glucksberg"/></a> <a href="https://github.com/rahthakor"><img src="https://avatars.githubusercontent.com/u/8470553?v=4&s=48" width="48" height="48" alt="rahthakor" title="rahthakor"/></a> <a href="https://github.com/vrknetha"><img src="https://avatars.githubusercontent.com/u/20596261?v=4&s=48" width="48" height="48" alt="vrknetha" title="vrknetha"/></a> <a href="https://github.com/tyler6204"><img src="https://avatars.githubusercontent.com/u/64381258?v=4&s=48" width="48" height="48" alt="tyler6204" title="tyler6204"/></a> <a href="https://github.com/vignesh07"><img src="https://avatars.githubusercontent.com/u/1436853?v=4&s=48" width="48" height="48" alt="vignesh07" title="vignesh07"/></a> <a href="https://github.com/radek-paclt"><img src="https://avatars.githubusercontent.com/u/50451445?v=4&s=48" width="48" height="48" alt="radek-paclt" title="radek-paclt"/></a> <a href="https://github.com/tobiasbischoff"><img src="https://avatars.githubusercontent.com/u/711564?v=4&s=48" width="48" height="48" alt="Tobias Bischoff" title="Tobias Bischoff"/></a>
  <a href="https://github.com/czekaj"><img src="https://avatars.githubusercontent.com/u/1464539?v=4&s=48" width="48" height="48" alt="czekaj" title="czekaj"/></a> <a href="https://github.com/ethanpalm"><img src="https://avatars.githubusercontent.com/u/56270045?v=4&s=48" width="48" height="48" alt="ethanpalm" title="ethanpalm"/></a> <a href="https://github.com/mukhtharcm"><img src="https://avatars.githubusercontent.com/u/56378562?v=4&s=48" width="48" height="48" alt="mukhtharcm" title="mukhtharcm"/></a> <a href="https://github.com/maxsumrall"><img src="https://avatars.githubusercontent.com/u/628843?v=4&s=48" width="48" height="48" alt="maxsumrall" title="maxsumrall"/></a> <a href="https://github.com/xadenryan"><img src="https://avatars.githubusercontent.com/u/165437834?v=4&s=48" width="48" height="48" alt="xadenryan" title="xadenryan"/></a> <a href="https://github.com/VACInc"><img src="https://avatars.githubusercontent.com/u/3279061?v=4&s=48" width="48" height="48" alt="VACInc" title="VACInc"/></a> <a href="https://github.com/rodrigouroz"><img src="https://avatars.githubusercontent.com/u/384037?v=4&s=48" width="48" height="48" alt="rodrigouroz" title="rodrigouroz"/></a> <a href="https://github.com/juanpablodlc"><img src="https://avatars.githubusercontent.com/u/92012363?v=4&s=48" width="48" height="48" alt="juanpablodlc" title="juanpablodlc"/></a> <a href="https://github.com/conroywhitney"><img src="https://avatars.githubusercontent.com/u/249891?v=4&s=48" width="48" height="48" alt="conroywhitney" title="conroywhitney"/></a> <a href="https://github.com/hsrvc"><img src="https://avatars.githubusercontent.com/u/129702169?v=4&s=48" width="48" height="48" alt="hsrvc" title="hsrvc"/></a>
  <a href="https://github.com/christianklotz"><img src="https://avatars.githubusercontent.com/u/69443?v=4&s=48" width="48" height="48" alt="christianklotz" title="christianklotz"/></a> <a href="https://github.com/magimetal"><img src="https://avatars.githubusercontent.com/u/36491250?v=4&s=48" width="48" height="48" alt="magimetal" title="magimetal"/></a> <a href="https://github.com/zerone0x"><img src="https://avatars.githubusercontent.com/u/39543393?v=4&s=48" width="48" height="48" alt="zerone0x" title="zerone0x"/></a> <a href="https://github.com/meaningfool"><img src="https://avatars.githubusercontent.com/u/2862331?v=4&s=48" width="48" height="48" alt="meaningfool" title="meaningfool"/></a> <a href="https://github.com/Takhoffman"><img src="https://avatars.githubusercontent.com/u/781889?v=4&s=48" width="48" height="48" alt="Takhoffman" title="Takhoffman"/></a> <a href="https://github.com/patelhiren"><img src="https://avatars.githubusercontent.com/u/172098?v=4&s=48" width="48" height="48" alt="patelhiren" title="patelhiren"/></a> <a href="https://github.com/NicholasSpisak"><img src="https://avatars.githubusercontent.com/u/129075147?v=4&s=48" width="48" height="48" alt="NicholasSpisak" title="NicholasSpisak"/></a> <a href="https://github.com/jonisjongithub"><img src="https://avatars.githubusercontent.com/u/86072337?v=4&s=48" width="48" height="48" alt="jonisjongithub" title="jonisjongithub"/></a> <a href="https://github.com/AbhisekBasu1"><img src="https://avatars.githubusercontent.com/u/40645221?v=4&s=48" width="48" height="48" alt="abhisekbasu1" title="abhisekbasu1"/></a> <a href="https://github.com/jamesgroat"><img src="https://avatars.githubusercontent.com/u/2634024?v=4&s=48" width="48" height="48" alt="jamesgroat" title="jamesgroat"/></a>
  <a href="https://github.com/BunsDev"><img src="https://avatars.githubusercontent.com/u/68980965?v=4&s=48" width="48" height="48" alt="BunsDev" title="BunsDev"/></a> <a href="https://github.com/claude"><img src="https://avatars.githubusercontent.com/u/81847?v=4&s=48" width="48" height="48" alt="claude" title="claude"/></a> <a href="https://github.com/JustYannicc"><img src="https://avatars.githubusercontent.com/u/52761674?v=4&s=48" width="48" height="48" alt="JustYannicc" title="JustYannicc"/></a> <a href="https://github.com/Hyaxia"><img src="https://avatars.githubusercontent.com/u/36747317?v=4&s=48" width="48" height="48" alt="Hyaxia" title="Hyaxia"/></a> <a href="https://github.com/dantelex"><img src="https://avatars.githubusercontent.com/u/631543?v=4&s=48" width="48" height="48" alt="dantelex" title="dantelex"/></a> <a href="https://github.com/SocialNerd42069"><img src="https://avatars.githubusercontent.com/u/118244303?v=4&s=48" width="48" height="48" alt="SocialNerd42069" title="SocialNerd42069"/></a> <a href="https://github.com/daveonkels"><img src="https://avatars.githubusercontent.com/u/533642?v=4&s=48" width="48" height="48" alt="daveonkels" title="daveonkels"/></a> <a href="https://github.com/apps/google-labs-jules"><img src="https://avatars.githubusercontent.com/in/842251?v=4&s=48" width="48" height="48" alt="google-labs-jules[bot]" title="google-labs-jules[bot]"/></a> <a href="https://github.com/lc0rp"><img src="https://avatars.githubusercontent.com/u/2609441?v=4&s=48" width="48" height="48" alt="lc0rp" title="lc0rp"/></a> <a href="https://github.com/mousberg"><img src="https://avatars.githubusercontent.com/u/57605064?v=4&s=48" width="48" height="48" alt="mousberg" title="mousberg"/></a>
  <a href="https://github.com/adam91holt"><img src="https://avatars.githubusercontent.com/u/9592417?v=4&s=48" width="48" height="48" alt="adam91holt" title="adam91holt"/></a> <a href="https://github.com/hougangdev"><img src="https://avatars.githubusercontent.com/u/105773686?v=4&s=48" width="48" height="48" alt="hougangdev" title="hougangdev"/></a> <a href="https://github.com/gumadeiras"><img src="https://avatars.githubusercontent.com/u/5599352?v=4&s=48" width="48" height="48" alt="gumadeiras" title="gumadeiras"/></a> <a href="https://github.com/shakkernerd"><img src="https://avatars.githubusercontent.com/u/165377636?v=4&s=48" width="48" height="48" alt="shakkernerd" title="shakkernerd"/></a> <a href="https://github.com/mteam88"><img src="https://avatars.githubusercontent.com/u/84196639?v=4&s=48" width="48" height="48" alt="mteam88" title="mteam88"/></a> <a href="https://github.com/hirefrank"><img src="https://avatars.githubusercontent.com/u/183158?v=4&s=48" width="48" height="48" alt="hirefrank" title="hirefrank"/></a> <a href="https://github.com/joeynyc"><img src="https://avatars.githubusercontent.com/u/17919866?v=4&s=48" width="48" height="48" alt="joeynyc" title="joeynyc"/></a> <a href="https://github.com/orlyjamie"><img src="https://avatars.githubusercontent.com/u/6668807?v=4&s=48" width="48" height="48" alt="orlyjamie" title="orlyjamie"/></a> <a href="https://github.com/dbhurley"><img src="https://avatars.githubusercontent.com/u/5251425?v=4&s=48" width="48" height="48" alt="dbhurley" title="dbhurley"/></a> <a href="https://github.com/omniwired"><img src="https://avatars.githubusercontent.com/u/322761?v=4&s=48" width="48" height="48" alt="Eng. Juan Combetto" title="Eng. Juan Combetto"/></a>
  <a href="https://github.com/TSavo"><img src="https://avatars.githubusercontent.com/u/877990?v=4&s=48" width="48" height="48" alt="TSavo" title="TSavo"/></a> <a href="https://github.com/aerolalit"><img src="https://avatars.githubusercontent.com/u/17166039?v=4&s=48" width="48" height="48" alt="aerolalit" title="aerolalit"/></a> <a href="https://github.com/julianengel"><img src="https://avatars.githubusercontent.com/u/10634231?v=4&s=48" width="48" height="48" alt="julianengel" title="julianengel"/></a> <a href="https://github.com/bradleypriest"><img src="https://avatars.githubusercontent.com/u/167215?v=4&s=48" width="48" height="48" alt="bradleypriest" title="bradleypriest"/></a> <a href="https://github.com/benithors"><img src="https://avatars.githubusercontent.com/u/20652882?v=4&s=48" width="48" height="48" alt="benithors" title="benithors"/></a> <a href="https://github.com/rohannagpal"><img src="https://avatars.githubusercontent.com/u/4009239?v=4&s=48" width="48" height="48" alt="rohannagpal" title="rohannagpal"/></a> <a href="https://github.com/timolins"><img src="https://avatars.githubusercontent.com/u/1440854?v=4&s=48" width="48" height="48" alt="timolins" title="timolins"/></a> <a href="https://github.com/f-trycua"><img src="https://avatars.githubusercontent.com/u/195596869?v=4&s=48" width="48" height="48" alt="f-trycua" title="f-trycua"/></a> <a href="https://github.com/benostein"><img src="https://avatars.githubusercontent.com/u/31802821?v=4&s=48" width="48" height="48" alt="benostein" title="benostein"/></a> <a href="https://github.com/elliotsecops"><img src="https://avatars.githubusercontent.com/u/141947839?v=4&s=48" width="48" height="48" alt="elliotsecops" title="elliotsecops"/></a>
</p>
- `/compact` — Contexto de sessão conciso (resumo)
- `/think <level>` — off|minimal|low|medium|high|xhigh (apenas para modelos GPT-5.2 + Codex)
- `/verbose on|off`
- `/usage off|tokens|full` — Uso de tokens em cada resposta
- `/restart` — Reiniciar gateway (apenas administradores de grupo)
- `/activation mention|always` — Interruptor de ativação de grupo (apenas para grupos)

## Aplicativos (opcional)

O próprio gateway fornece uma excelente experiência. Todos os aplicativos são opcionais e adicionam funcionalidades extras.

Se você planeja construir/executar aplicativos companheiros, siga os manuais de plataforma abaixo.

### macOS (OpenClaw.app) (opcional)

- Controle da barra de menu para gateway e saúde.
- Ativação por voz + sobreposição de modo conversa com um clique.
- WebChat + ferramentas de depuração.
- Controle remoto do gateway via SSH.

Nota: Você deve usar uma compilação assinada para que as permissões do macOS persistam após reconstrução (veja `docs/mac/permissions.md`).

### Nós iOS (opcional)

- Atuam como nós via bridge.
- Encaminhamento de gatilho por voz + superfície Canvas.
- Controle via `openclaw nodes …`.

Manual: [Conexão iOS](https://docs.openclaw.ai/platforms/ios).

### Nós Android (opcional)

- Emparelhados via mesmo processo de bridge + emparelhamento do iOS.
- Permita comandos de Canvas, Câmera e Captura de tela.
- Manual: [Conexão Android](https://docs.openclaw.ai/platforms/android).

## Workspace do Agente + Habilidades

- Pasta raiz do workspace: `~/.openclaw/workspace` (configurável via `agents.defaults.workspace`).
- Arquivos de prompt injetados: `AGENTS.md`, `SOUL.md`, `TOOLS.md`.
- Habilidades: `~/.openclaw/workspace/skills/<skill>/SKILL.md`.

## Configuração
