# 🦞 OpenClaw — 개인 인공지능 어시스턴트

<p align="center">
    <picture>
        <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/openclaw/openclaw/main/docs/assets/openclaw-logo-text-dark.png">
        <img src="https://raw.githubusercontent.com/openclaw/openclaw/main/docs/assets/openclaw-logo-text.png" alt="OpenClaw" width="500">
    </picture>
</p>

<p align="center">
  <strong>변태! 변태!</strong>
</p>

<p align="center">
  <a href="https://github.com/openclaw/openclaw/actions/workflows/ci.yml?branch=main"><img src="https://img.shields.io/github/actions/workflow/status/openclaw/openclaw/ci.yml?branch=main&style=for-the-badge" alt="CI 상태"></a>
  <a href="https://github.com/openclaw/openclaw/releases"><img src="https://img.shields.io/github/v/release/openclaw/openclaw?include_prereleases&style=for-the-badge" alt="깃허브 릴리스"></a>
  <a href="https://discord.gg/clawd"><img src="https://img.shields.io/discord/1456350064065904867?label=Discord&logo=discord&logoColor=white&color=5865F2&style=for-the-badge" alt="디스코드"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge" alt="MIT 라이선스"></a>
</p>

**OpenClaw**는 사용자의 장치에서 실행되는 개인 AI 어시스턴트입니다. 일반적인 채널(WhatsApp, Telegram, Slack, Discord, Google Chat, Signal, iMessage, Microsoft Teams, WebChat) 및 BlueBubbles, Matrix, Zalo, Zalo Personal과 같은 확장 채널을 통해 지원을 제공합니다. macOS/iOS/Android를 지원하며 사용자가 제어하는 실시간 Canvas 인터페이스를 렌더링할 수 있습니다. 게이트웨이는 단지 제어 플랫폼일 뿐이며 제품 자체가 진정한 어시스턴트입니다.
로컬 어시스턴트처럼 느껴지고 속도가 빠르며 항상 온라인 상태인 싱글 유저 개인 어시스턴트를 원하신다면 바로 이겁니다.

[공식 사이트](https://openclaw.ai) · [공식 문서](https://docs.openclaw.ai) · [딥위키](https://deepwiki.com/openclaw/openclaw) · [시작 가이드](https://docs.openclaw.ai/start/getting-started) · [업데이트](https://docs.openclaw.ai/install/updating) · [사례](https://docs.openclaw.ai/start/showcase) · [FAQ](https://docs.openclaw.ai/start/faq) · [마법사](https://docs.openclaw.ai/start/wizard) · [Nix](https://github.com/openclaw/nix-clawdbot) · [도커](https://docs.openclaw.ai/install/docker) · [디스코드](https://discord.gg/clawd)

권장 설정: 설정 마법사(`openclaw onboard`)를 실행하십시오. 게이트웨이, 워크스페이스, 채널 및 스킬 설정을 안내해줍니다. 명령줄 마법사는 추천 경로이며 **macOS, Linux 및 Windows(WSL2를 통한; 강력히 권장)** 에서 작동합니다.
npm, pnpm 또는 bun을 지원합니다. 처음 설치하시나요? 여기서 시작하세요: [시작 가이드](https://docs.openclaw.ai/start/getting-started)

**구독(OAuth):**

- **[Anthropic](https://www.anthropic.com/)** (Claude Pro/Max)
- **[OpenAI](https://openai.com/)** (ChatGPT/Codex)

모델 참고 사항: 모든 모델이 지원되지만, 더 나은 장기 성능과 간섭 저항성을 위해 **Anthropic Pro/Max (100/200) + Opus 4.6** 을 적극 권장합니다. [온라인 가이드](https://docs.openclaw.ai/start/onboarding)를 참조하십시오.

## 모델(선택 + 인증)

- 모델 구성 + CLI: [모델](https://docs.openclaw.ai/concepts/models)
- 인증 프로필(OAuth 대 API 키) + 폴백: [모델 폴백](https://docs.openclaw.ai/concepts/model-failover)

## 설치

실행 환경: **Node ≥22**.

```bash
npm install -g openclaw@latest
# 또는: pnpm add -g openclaw@latest

openclaw onboard --install-daemon
```

이 마법사는 게이트웨이 데몬(launchd/systemd 사용자 서비스)을 설치하여 계속 실행되도록 합니다.

## 빠른 시작 (TL;DR)

실행 환경: **Node ≥22**.

완전한 초보자 가이드(인증, 페어링, 채널): [시작하기](https://docs.openclaw.ai/start/getting-started)

```bash
openclaw onboard --install-daemon

openclaw gateway --port 18789 --verbose

# 메시지 보내기
openclaw message send --to +1234567890 --message "Hello from OpenClaw"

# 에이전트와 대화 (선택적으로 연결된 채널에 모든 메시지를 보낼 수 있음: WhatsApp/Telegram/Slack/Discord/Google Chat/Signal/iMessage/BlueBubbles/Microsoft Teams/Matrix/Zalo/Zalo Personal/WebChat)
openclaw agent --message "Ship checklist" --thinking high
```

업그레이드 방법? [업데이트 가이드](https://docs.openclaw.ai/install/updating) (`openclaw doctor` 실행).

## 개발 채널 상태

- **stable**: 태그된 릴리스 (`vYYYY.M.D` 또는 `vYYYY.M.D-<patch>`), npm 배포 태그 `latest`.
- **beta**: 사전 릴리스 태그 (`vYYYY.M.D-beta.N`), npm 배포 태그 `beta` (macOS 앱이 누락될 수 있음).
- **dev**: `main`의 최신 상태, npm 배포 태그 `dev` (게시될 때).

전환(git + npm): `openclaw update --channel stable|beta|dev`.
자세한 정보: [개발 채널](https://docs.openclaw.ai/install/development-channels).

## 소스(개발)

빌드에는 `pnpm`을 권장합니다. Bun은 TypeScript를 직접 실행하는 데 선택적으로 사용됩니다.

```bash
git clone https://github.com/openclaw/openclaw.git
cd openclaw

pnpm install
pnpm ui:build # 첫 실행 시 UI 종속성 자동 설치
pnpm build

pnpm openclaw onboard --install-daemon

# 개발 루프(TS 변경 시 자동 리로드)
pnpm gateway:watch
```

참고: `pnpm openclaw ...`은 TypeScript를 직접 실행합니다(`tsx`를 통해). `pnpm build`는 `openclaw` 바이너리를 Node를 통해 실행/번들링하기 위한 `dist/`를 생성합니다.

## 보안 기본값(DM 액세스)

OpenClaw는 실제 IM 플랫폼에 연결됩니다. 수신한 DM을 **신뢰할 수 없는 입력**으로 간주하십시오.

전체 보안 가이드: [보안 지침](https://docs.openclaw.ai/gateway/security)

Telegram/WhatsApp/Signal/iMessage/Microsoft Teams/Discord/Google Chat/Slack의 기본 동작:

- **DM 페어링** (`dmPolicy="pairing"` / `channels.discord.dm.policy="pairing"` / `channels.slack.dm.policy="pairing"`): 알 수 없는 발신자는 간단한 페어링 코드를 받으며, 봇은 해당 메시지를 처리하지 않습니다.
- 승인: `openclaw pairing approve <channel> <code>` (그런 다음 발신자를 로컬 저장소에 추가).
- 공개 수신 DM은 명시적 옵트인 필요: `dmPolicy="open"` 설정 및 채널 허용 목록(`allowFrom` / `channels.discord.dm.allowFrom` / `channels.slack.dm.allowFrom`)에 `"*"` 포함.

위험/잘못 구성된 DM 정책을 발견하려면 `openclaw doctor`를 실행하십시오.

## 핵심 기능

- **[로컬 우선 게이트웨이](https://docs.openclaw.ai/gateway)** — 세션, 채널, 도구 및 이벤트에 대한 단일 제어 플레인.
- **[다중 채널 인박스](https://docs.openclaw.ai/channels)** — WhatsApp, Telegram, Slack, Discord, Google Chat, Signal, BlueBubbles (iMessage), iMessage (레거시), Microsoft Teams, Matrix, Zalo, Zalo Personal, WebChat, macOS, iOS/Android.
- **[다중 에이전트 라우팅](https://docs.openclaw.ai/gateway/configuration)** — 수신 채널/계정/피어를 격리된 에이전트(워크스페이스 + 에이전트당 세션)로 라우팅.
- **[음성 활성화](https://docs.openclaw.ai/nodes/voicewake) + [통화 모드](https://docs.openclaw.ai/nodes/talk)** — macOS/iOS/Android를 위한 ElevenLabs의 상시 대기 음성 기능.
- **[라이브 캔버스](https://docs.openclaw.ai/platforms/mac/canvas)** — [A2UI](https://docs.openclaw.ai/platforms/mac/canvas#canvas-a2ui) 기반의 에이전트 중심 시각적 작업 공간.
- **[일류 도구](https://docs.openclaw.ai/tools)** — 브라우저, 캔버스, 노드, 크론, 세션 및 Discord/Slack 조작.
- **[보조 앱](https://docs.openclaw.ai/platforms/macos)** — macOS 메뉴바 앱 + iOS/Android [노드](https://docs.openclaw.ai/nodes).
- **[마법사](https://docs.openclaw.ai/start/wizard) + [스킬](https://docs.openclaw.ai/tools/skills)** — 마법사 설정, 번들/관리/워크스페이스 스킬 포함.

## 스타 기록

[![Star History Chart](https://api.star-history.com/svg?repos=openclaw/openclaw&type=date&legend=top-left)](https://www.star-history.com/#openclaw/openclaw&type=date&legend=top-left)

## 지금까지 우리가 해온 일

### 핵심 플랫폼

- [게이트웨이 대시보드](https://docs.openclaw.ai/gateway)에는 세션, 상태, 구성, 크론, 웹후크, [대화형 제어 UI](https://docs.openclaw.ai/web), 및 [캔버스 호스트](https://docs.openclaw.ai/platforms/mac/canvas#canvas-a2ui)가 포함됩니다.
- [CLI 인터페이스](https://docs.openclaw.ai/tools/agent-send): 게이트웨이, 에이전트, 전송, [마법사](https://docs.openclaw.ai/start/wizard), 및 [보안](https://docs.openclaw.ai/gateway/doctor).
- [Pi 에이전트 런타임](https://docs.openclaw.ai/concepts/agent)은 RPC 패턴을 사용하고, 도구 스트리밍 및 블록 스트리밍을 지원합니다.
- [세션 모델](https://docs.openclaw.ai/concepts/session): `main`은 직접 채팅, 그룹 격리, 활성화 모드, 큐 모드, 회신을 위한 것입니다. 그룹 규칙: [그룹](https://docs.openclaw.ai/concepts/groups).
- [미디어 채널](https://docs.openclaw.ai/nodes/images): 이미지/오디오/비디오, 트랜스크립션 후크, 크기 제한, 임시 파일 수명 주기. 오디오 세부 정보: [오디오](https://docs.openclaw.ai/nodes/audio).

### 채널

- [채널](https://docs.openclaw.ai/channels): [WhatsApp](https://docs.openclaw.ai/channels/whatsapp) (Baileys), [Telegram](https://docs.openclaw.ai/channels/telegram) (grammY), [Slack](https://docs.openclaw.ai/channels/slack) (Bolt), [Discord](https://docs.openclaw.ai/channels/discord) (discord.js), [Google Chat](https://docs.openclaw.ai/channels/googlechat) (Chat API), [Signal](https://docs.openclaw.ai/channels/signal) (signal-cli), [BlueBubbles](https://docs.openclaw.ai/channels/bluebubbles) (iMessage, 권장), [iMessage](https://docs.openclaw.ai/channels/imessage) (레거시 imsg), [Microsoft Teams](https://docs.openclaw.ai/channels/msteams) (확장), [Matrix](https://docs.openclaw.ai/channels/matrix) (확장), [Zalo](https://docs.openclaw.ai/channels/zalo) (확장), [Zalo Personal](https://docs.openclaw.ai/channels/zalouser) (확장), [WebChat](https://docs.openclaw.ai/web/webchat).
- [그룹 라우팅](https://docs.openclaw.ai/concepts/group-messages): 멘션 게이팅, 회신 태깅, 채널별 청킹 및 라우팅. 채널 규칙: [채널](https://docs.openclaw.ai/channels).

### 앱 + 노드

- [macOS 앱](https://docs.openclaw.ai/platforms/macos): 메뉴바 제어 플레인, [음성 활성화](https://docs.openclaw.ai/nodes/voicewake)/PTT, [통화 모드](https://docs.openclaw.ai/nodes/talk) 오버레이, [WebChat](https://docs.openclaw.ai/web/webchat), 디버깅 도구, [원격 게이트웨이](https://docs.openclaw.ai/gateway/remote) 제어.
- [iOS 노드](https://docs.openclaw.ai/platforms/ios): [캔버스](https://docs.openclaw.ai/platforms/mac/canvas), [음성 활성화](https://docs.openclaw.ai/nodes/voicewake), [통화 모드](https://docs.openclaw.ai/nodes/talk), 카메라, 화면 녹화, Bonjour 페어링.
- [Android 노드](https://docs.openclaw.ai/platforms/android): [캔버스](https://docs.openclaw.ai/platforms/mac/canvas), [통화 모드](https://docs.openclaw.ai/nodes/talk), 카메라, 화면 녹화, 선택적 SMS 기능.
- [macOS 노드 모드](https://docs.openclaw.ai/nodes): 시스템 실행/알림 + 캔버스/카메라 노출.

### 도구 + 자동화

- [브라우저 제어](https://docs.openclaw.ai/tools/browser): 전용 openclaw Chrome/Chromium, 스냅샷, 조작, 업로드, 프로필.
- [캔버스](https://docs.openclaw.ai/platforms/mac/canvas): [A2UI](https://docs.openclaw.ai/platforms/mac/canvas#canvas-a2ui) 푸시/리셋, 평가, 스냅샷.
- [노드](https://docs.openclaw.ai/nodes): 카메라 스냅샷/클립, 화면 녹화, [위치 가져오기](https://docs.openclaw.ai/nodes/location-command), 알림
- [크론 + 알림](https://docs.openclaw.ai/automation/cron-jobs); [웹후크](https://docs.openclaw.ai/automation/webhook); [Gmail Pub/Sub](https://docs.openclaw.ai/automation/gmail-pubsub).
- [스킬 플랫폼](https://docs.openclaw.ai/tools/skills): 번들, 관리, 워크스페이스 스킬, 설치 제한 및 UI 포함.

### 운영 + 보안

- [채널 라우팅](https://docs.openclaw.ai/concepts/channel-routing), [재시도 정책](https://docs.openclaw.ai/concepts/retry), 및 [스트리밍/청킹](https://docs.openclaw.ai/concepts/streaming).
- [Presence](https://docs.openclaw.ai/concepts/presence), [입력 표시기](https://docs.openclaw.ai/concepts/typing-indicators), 및 [사용량 추적](https://docs.openclaw.ai/concepts/usage-tracking).
- [모델](https://docs.openclaw.ai/concepts/models), [모델 폴백](https://docs.openclaw.ai/concepts/model-failover), 및 [세션](https://docs.openclaw.ai/concepts/session-pruning).
- [보안](https://docs.openclaw.ai/gateway/security) 및 [문제 해결](https://docs.openclaw.ai/channels/troubleshooting).

### 운영 + 패키징

- [제어 인터페이스](https://docs.openclaw.ai/web) + [WebChat](https://docs.openclaw.ai/web/webchat)는 게이트웨이에서 직접 제공됩니다.
- [Tailscale Serve/Funnel](https://docs.openclaw.ai/gateway/tailscale) 또는 [SSH 터널](https://docs.openclaw.ai/gateway/remote) 토큰/암호 인증 사용
- [Nix 모드](https://docs.openclaw.ai/install/nix)는 선언적 구성 지원; [도커](https://docs.openclaw.ai/install/docker) 기반 설치.
- [보안](https://docs.openclaw.ai/gateway/doctor) 하드닝, [로깅](https://docs.openclaw.ai/logging).

## 작동 방식(간략)

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

## 핵심 하위 시스템

- **[게이트웨이 WebSocket 커뮤니케이션](https://docs.openclaw.ai/concepts/architecture)** — 클라이언트, 도구 및 이벤트에 대한 단일 WS 제어 플레인(및 오퍼레이션: [게이트웨이 운영](https://docs.openclaw.ai/gateway)).
- **[Tailscale 노출](https://docs.openclaw.ai/gateway/tailscale)** — 게이트웨이 대시보드를 위한 Serve/Funnel + WS(원격 액세스: [원격 액세스](https://docs.openclaw.ai/gateway/remote)).
- **[브라우저 제어](https://docs.openclaw.ai/tools/browser)** — CDP를 사용하여 제어되는 openclaw 관리 Chrome/Chromium.
- **[캔버스 + A2UI](https://docs.openclaw.ai/platforms/mac/canvas)** — 에이전트 기반 시각적 작업 공간(A2UI 호스트: [캔버스/A2UI](https://docs.openclaw.ai/platforms/mac/canvas#canvas-a2ui)).
- **[음성 활성화](https://docs.openclaw.ai/nodes/voicewake) + [통화 모드](https://docs.openclaw.ai/nodes/talk)** — 지속적인 대화를 위한 상시 대기 음성 기능.
- **[노드](https://docs.openclaw.ai/nodes)** — 캔버스, 카메라 스냅샷/클립, 화면 녹화, `location.get`, 알림, 그리고 macOS 전용 `system.run`/`system.notify`.

## Tailscale 액세스(게이트웨이 대시보드)

OpenClaw는 게이트웨이가 루프백 인터페이스에 바인딩된 상태로 Tailscale **Serve**(테일넷 전용) 또는 **Funnel**(공개)을 자동으로 구성할 수 있습니다. `gateway.tailscale.mode` 구성:

- `off`: Tailscale 자동화 비활성화(기본값).
- `serve`: `tailscale serve`를 통한 테일넷 전용 HTTPS(기본적으로 Tailscale 헤더 사용).
- `funnel`: 공개 HTTPS `tailscale funnel`(공유 암호 인증 필요).

설명:

- Serve/Funnel을 사용할 때 `gateway.bind`는 루프백 상태를 유지해야 합니다(OpenClaw는 이를 강제로 적용함).
- `gateway.auth.mode: "password"` 설정 또는 `gateway.auth.allowTailscale: false`를 통해 서버 암호를 강제 적용할 수 있습니다.
- `gateway.auth.mode: "password"`가 설정되지 않으면 실행을 거부합니다.
- 선택적으로 `gateway.tailscale.resetOnExit`를 사용하면 종료 시 Serve/Funnel을 취소합니다.

자세한 정보: [Tailscale 가이드](https://docs.openclaw.ai/gateway/tailscale) · [웹 페이지](https://docs.openclaw.ai/web)

## 원격 게이트웨이(Linux 친화적)

소규모 Linux 인스턴스에서 게이트웨이를 실행하는 것은 완전히 괜찮습니다. 클라이언트(macOS 앱, CLI, WebChat)는 **Tailscale Serve/Funnel** 또는 **SSH 터널**을 통해 연결할 수 있으며, 여전히 필요에 따라 장치 노드(macOS/iOS/Android)를 페어링하여 장치 로컬 작업을 수행할 수 있습니다.

- **게이트웨이 호스트**는 기본적으로 도구 실행 및 채널 연결을 담당합니다.
- **장치 노드**는 `node.invoke`를 통해 장치 로컬 작업(`system.run` 등, 카메라, 화면 녹화, 알림)을 실행합니다.
  간단히 말해: exec는 게이트웨이 위치에서 실행되고, 장치 작업은 장치 위치에서 실행됩니다.

자세한 정보: [원격 액세스](https://docs.openclaw.ai/gateway/remote) · [노드](https://docs.openclaw.ai/nodes) · [보안](https://docs.openclaw.ai/gateway/security)

## macOS 권한(Gateway 프로토콜을 통한)

macOS 앱은 **노드 모드**에서 실행되어 게이트웨이 WebSocket(`node.list` / `node.describe`)을 통해 기능 및 권한 매핑을 브로드캐스트할 수 있습니다. 클라이언트는 이후 `node.invoke`를 통해 로컬 작업을 실행할 수 있습니다:

- `system.run`은 로컬 명령을 실행하고 stdout/stderr/exit 코드를 반환합니다; 화면 녹화 권한이 필요한 경우 `needsScreenRecording: true`를 설정하십시오(그렇지 않으면 `PERMISSION_MISSING` 오류가 발생합니다).
- `system.notify`는 사용자에게 알림을 보내며, 알림이 거부되면 실패를 반환합니다.
- `canvas.*`, `camera.*`, `screen.record`, 및 `location.get`은 `node.invoke`를 통해 라우팅되며 TCC 권한 상태를 따릅니다.

권한 상승 bash(호스트 권한)와 macOS TCC는 별개입니다:

- 활성화 및 허용 목록에 추가되었을 때 `/elevated on|off`를 사용하여 각 세션의 권한 상승 액세스를 전환합니다.
- 게이트웨이는 (WS 메서드를 통해) `sessions.patch`를 통해 `thinkingLevel`, `verboseLevel`, `model`, `sendPolicy`, 및 `groupActivation`을 통해 각 세션의 전환을 유지합니다.

자세한 정보: [노드](https://docs.openclaw.ai/nodes) · [macOS 앱](https://docs.openclaw.ai/platforms/macos) · [게이트웨이 프로토콜](https://docs.openclaw.ai/concepts/architecture)

## 에이전트 간 통신(sessions_* 도구)

- 채팅 인터페이스 간 전환 없이 세션 간 작업을 조정할 수 있습니다.
- `sessions_list` — 활성 세션(에이전트) 및 해당 메타데이터 검색.
- `sessions_history` — 세션의 기록 로그 가져오기.
- `sessions_send` — 다른 세션에 메시지 전송; 선택적 회신 핑퐁 + 발표 단계(REPLY_SKIP, ANNOUNCE_SKIP).

자세한 정보: [세션 도구](https://docs.openclaw.ai/concepts/session-tool)

## 스킬 등록(ClawHub)

ClawHub는 최소한의 스킬 레지스트리 시스템입니다. ClawHub가 활성화되면 에이전트는 필요에 따라 자동으로 스킬을 검색하고 새 스킬을 추가할 수 있습니다.

[ClawHub](https://clawhub.com)

## 채팅 명령

WhatsApp/Telegram/Slack/Google Chat/Microsoft Teams/WebChat을 통해 다음을 전송하십시오(그룹 명령은 그룹 관리자만 사용 가능):

- `/status` — 간결한 세션 상태(모델 + 토큰, 사용 가능한 경우 비용 포함)
- `/new` 또는 `/reset` — 세션 재설정
- `/compact` — 간결한 세션 컨텍스트(요약)
- `/think <level>` — off|minimal|low|medium|high|xhigh (GPT-5.2 + Codex 모델 전용)
- `/verbose on|off`
- `/usage off|tokens|full` — 응답당 토큰 사용량
- `/restart` — 게이트웨이 재시작(그룹 관리자 전용)
- `/activation mention|always` — 그룹 활성화 스위치(그룹 전용)

## 앱(선택 사항)

게이트웨이 자체만으로도 훌륭한 경험을 제공합니다. 모든 앱은 선택적이며 추가 기능을 제공합니다.

보조 앱을 빌드/실행할 계획이라면 아래 플랫폼 운영 가이드를 따르십시오.

### macOS (OpenClaw.app) (선택 사항)

- 게이트웨이 및 상태에 대한 메뉴바 제어.
- 음성 활성화 + 원클릭 통화 오버레이.
- WebChat + 디버깅 도구.
- SSH를 통한 원격 게이트웨이 제어.

참고: 다시 빌드한 후에도 macOS 권한을 유지하려면 서명된 빌드가 필요합니다(`docs/mac/permissions.md` 참조).

### iOS 노드(선택 사항)

- 브리지에서 페어링된 피어를 노드로 사용.
- 음성 트리거 포워딩 + 캔버스 표면.
- `openclaw nodes …`를 통한 제어.

운영 가이드: [iOS 연결](https://docs.openclaw.ai/platforms/ios).

### Android 노드(선택 사항)

- iOS와 동일한 브리지 + 페어링 흐름을 통해 페어링.
- 캔버스, 카메라 및 화면 캡처 명령 권한 허용.
- 운영 가이드: [Android 연결](https://docs.openclaw.ai/platforms/android).

## 에이전트 워크스페이스 + 스킬

- 워크스페이스 루트: `~/.openclaw/workspace` (`agents.defaults.workspace`를 통해 구성 가능).
- 주입된 프롬프트 파일: `AGENTS.md`, `SOUL.md`, `TOOLS.md`.
- 스킬: `~/.openclaw/workspace/skills/<skill>/SKILL.md`.

## 구성

## 보안 모드(중요)

- **기본적으로:** 도구는 메인 세션으로 호스트에서 실행되므로 혼자 사용하는 경우 에이전트는 전체 액세스 권한을 갖습니다.
- **그룹/채널 보안:** 각 세션을 도커 내 샌드박스로 실행하려면 `agents.defaults.sandbox.mode: "non-main"`을 **비메인 세션**(그룹/채널)으로 설정하십시오; 그런 다음 도커 내 bash 세션으로 실행하십시오.
- **기본 샌드박스:** `bash`, `process`, `read`, `write`, `edit`, `sessions_list`, `sessions_history`, `sessions_send`, `sessions_spawn` 실행을 허용합니다; `browser`, `canvas`, `nodes`, `cron`, `discord`, `gateway`는 금지합니다.

자세한 내용: [보안 지침](https://docs.openclaw.ai/gateway/security) · [도커 + 샌드박스](https://docs.openclaw.ai/install/docker) · [샌드박스 구성](https://docs.openclaw.ai/gateway/configuration)

## 문서

[공식 문서](https://docs.openclaw.ai)에는 설치, 구성, 운영, 문제 해결에 대한 자세한 정보가 포함되어 있습니다.

## 고급 문서

- [모델 구성](https://docs.openclaw.ai/concepts/models)
- [보안 설정](https://docs.openclaw.ai/gateway/security)
- [채널 구성](https://docs.openclaw.ai/channels)
- [도구 개발](https://docs.openclaw.ai/tools)

## 운영 및 문제 해결

- [게이트웨이 운영](https://docs.openclaw.ai/gateway)
- [문제 해결 가이드](https://docs.openclaw.ai/channels/troubleshooting)
- [보안 하드닝](https://docs.openclaw.ai/gateway/security)
- [성능 모니터링](https://docs.openclaw.ai/concepts/usage-tracking)

## 심층 탐색

- [아키텍처 개요](https://docs.openclaw.ai/concepts/architecture)
- [게이트웨이 프로토콜](https://docs.openclaw.ai/concepts/architecture)
- [에이전트 런타임](https://docs.openclaw.ai/concepts/agent)
- [세션 관리](https://docs.openclaw.ai/concepts/session)

## 워크스페이스 및 스킬

- [워크스페이스 구성](https://docs.openclaw.ai/gateway/configuration)
- [스킬 개발](https://docs.openclaw.ai/tools/skills)
- [에이전트 프로필](https://docs.openclaw.ai/concepts/agent)
- [툴 정의](https://docs.openclaw.ai/tools)

## 플랫폼 내부 구조

- [게이트웨이 아키텍처](https://docs.openclaw.ai/concepts/architecture)
- [채널 프로토콜](https://docs.openclaw.ai/channels)
- [도구 시스템](https://docs.openclaw.ai/tools)
- [노드 시스템](https://docs.openclaw.ai/nodes)

## 메일 후크

OpenClaw는 다양한 메시징 플랫폼과 통합되어 있습니다:

- [WhatsApp 통합](https://docs.openclaw.ai/channels/whatsapp)
- [Telegram 통합](https://docs.openclaw.ai/channels/telegram)
- [Discord 통합](https://docs.openclaw.ai/channels/discord)
- [Slack 통합](https://docs.openclaw.ai/channels/slack)

## 몰티

Molty는 OpenClaw의 내부 구성 요소 중 하나로, 다양한 기능을 제공합니다. 자세한 내용은 [Molty 문서](https://docs.openclaw.ai/tools/molty)를 참조하십시오.

## 커뮤니티

[CONTRIBUTING.md](CONTRIBUTING.md) 파일을 참조하여 기여 지침, 유지 관리자 정보 및 PR 제출 방법을 확인하십시오. AI/vibe 코딩 PR을 환영합니다! 🤖

[Mario Zechner](https://mariozechner.at/)의 지원과 그가 개발한 [pi-mono](https://github.com/badlogic/pi-mono)에 특별히 감사드립니다.
Adam Doppelt이 개발한 lobster.bot에 특별히 감사드립니다.

모든 기여자들에게 감사드립니다:

<p align="left">
  <a href="https://github.com/steipete"><img src="https://avatars.githubusercontent.com/u/58493?v=4&s=48" width="48" height="48" alt="steipete" title="steipete"/></a> <a href="https://github.com/joshp123"><img src="https://avatars.githubusercontent.com/u/1497361?v=4&s=48" width="48" height="48" alt="joshp123" title="joshp123"/></a> <a href="https://github.com/cpojer"><img src="https://avatars.githubusercontent.com/u/13352?v=4&s=48" width="48" height="48" alt="cpojer" title="cpojer"/></a> <a href="https://github.com/mbelinky"><img src="https://avatars.githubusercontent.com/u/132747814?v=4&s=48" width="48" height="48" alt="Mariano Belinky" title="Mariano Belinky"/></a> <a href="https://github.com/plum-dawg"><img src="https://avatars.githubusercontent.com/u/5909950?v=4&s=48" width="48" height="48" alt="plum-dawg" title="plum-dawg"/></a> <a href="https://github.com/bohdanpodvirnyi"><img src="https://avatars.githubusercontent.com/u/31819391?v=4&s=48" width="48" height="48" alt="bohdanpodvirnyi" title="bohdanpodvirnyi"/></a> <a href="https://github.com/iHildy"><img src="https://avatars.githubusercontent.com/u/25069719?v=4&s=48" width="48" height="48" alt="iHildy" title="iHildy"/></a> <a href="https://github.com/jaydenfyi"><img src="https://avatars.githubusercontent.com/u/213395523?v=4&s=48" width="48" height="48" alt="jaydenfyi" title="jaydenfyi"/></a> <a href="https://github.com/joaohlisboa"><img src="https://avatars.githubusercontent.com/u/8200873?v=4&s=48" width="48" height="48" alt="joaohlisboa" title="joaohlisboa"/></a> <a href="https://github.com/mneves75"><img src="https://avatars.githubusercontent.com/u/2423436?v=4&s=48" width="48" height="48" alt="mneves75" title="mneves75"/></a>
  <a href="https://github.com/alexandruast"><img src="https://avatars.githubusercontent.com/u/18248527?v=4&s=48" width="48" height="48" alt="alexandruast" title="alexandruast"/></a> <a href="https://github.com/amitlevy8"><img src="https://avatars.githubusercontent.com/u/11261714?v=4&s=48" width="48" height="48" alt="amitlevy8" title="amitlevy8"/></a> <a href="https://github.com/AndrewTron"><img src="https://avatars.githubusercontent.com/u/12884645?v=4&s=48" width="48" height="48" alt="AndrewTron" title="AndrewTron"/></a> <a href="https://github.com/antony1060"><img src="https://avatars.githubusercontent.com/u/17360792?v=4&s=48" width="48" height="48" alt="antony1060" title="antony1060"/></a> <a href="https://github.com/aravindvnair99"><img src="https://avatars.githubusercontent.com/u/19519564?v=4&s=48" width="48" height="48" alt="aravindvnair99" title="aravindvnair99"/></a> <a href="https://github.com/Arkanosis"><img src="https://avatars.githubusercontent.com/u/9467617?v=4&s=48" width="48" height="48" alt="Jérémie Lesage" title="Jérémie Lesage"/></a> <a href="https://github.com/Artwalk"><img src="https://avatars.githubusercontent.com/u/52018749?v=4&s=48" width="48" height="48" alt="Artwalk" title="Artwalk"/></a> <a href="https://github.com/ArtskydJ"><img src="https://avatars.githubusercontent.com/u/10906415?v=4&s=48" width="48" height="48" alt="Arseniy" title="Arseniy"/></a> <a href="https://github.com/ascendedgreg"><img src="https://avatars.githubusercontent.com/u/6111562?v=4&s=48" width="48" height="48" alt="ascendedgreg" title="ascendedgreg"/></a> <a href="https://github.com/Ashish-Nagpal"><img src="https://avatars.githubusercontent.com/u/43886029?v=4&s=48" width="48" height="48" alt="Ashish-Nagpal" title="Ashish-Nagpal"/></a>
  <a href="https://github.com/Atarity"><img src="https://avatars.githubusercontent.com/u/23156549?v=4&s=48" width="48" height="48" alt="Atarity" title="Atarity"/></a> <a href="https://github.com/avdv"><img src="https://avatars.githubusercontent.com/u/6375919?v=4&s=48" width="48" height="48" alt="avdv" title="avdv"/></a> <a href="https://github.com/baptistejamin"><img src="https://avatars.githubusercontent.com/u/15995930?v=4&s=48" width="48" height="48" alt="baptistejamin" title="baptistejamin"/></a> <a href="https://github.com/BastiHz"><img src="https://avatars.githubusercontent.com/u/1397415?v=4&s=48" width="48" height="48" alt="BastiHz" title="BastiHz"/></a> <a href="https://github.com/bclifton"><img src="https://avatars.githubusercontent.com/u/796623?v=4&s=48" width="48" height="48" alt="bclifton" title="bclifton"/></a> <a href="https://github.com/beatware"><img src="https://avatars.githubusercontent.com/u/2062494?v=4&s=48" width="48" height="48" alt="beatware" title="beatware"/></a> <a href="https://github.com/beaulyddon"><img src="https://avatars.githubusercontent.com/u/174470?v=4&s=48" width="48" height="48" alt="Beau Lyddon" title="Beau Lyddon"/></a> <a href="https://github.com/bedekelly"><img src="https://avatars.githubusercontent.com/u/1783781?v=4&s=48" width="48" height="48" alt="bedekelly" title="bedekelly"/></a> <a href="https://github.com/bedkowski"><img src="https://avatars.githubusercontent.com/u/6933928?v=4&s=48" width="48" height="48" alt="Stanisław Bedkowski" title="Stanisław Bedkowski"/></a> <a href="https://github.com/benbrignell"><img src="https://avatars.githubusercontent.com/u/1196891?v=4&s=48" width="48" height="48" alt="benbrignell" title="benbrignell"/></a>
  <a href="https://github.com/benmccann"><img src="https://avatars.githubusercontent.com/u/3253920?v=4&s=48" width="48" height="48" alt="benmccann" title="benmccann"/></a> <a href="https://github.com/bentheprotagonist"><img src="https://avatars.githubusercontent.com/u/26491099?v=4&s=48" width="48" height="48" alt="bentheprotagonist" title="bentheprotagonist"/></a> <a href="https://github.com/bjia56"><img src="https://avatars.githubusercontent.com/u/1858479?v=4&s=48" width="48" height="48" alt="bjia56" title="bjia56"/></a> <a href="https://github.com/bluov"><img src="https://avatars.githubusercontent.com/u/3334769?v=4&s=48" width="48" height="48" alt="bluov" title="bluov"/></a> <a href="https://github.com/BobRazowsky"><img src="https://avatars.githubusercontent.com/u/5454388?v=4&s=48" width="48" height="48" alt="BobRazowsky" title="BobRazowsky"/></a> <a href="https://github.com/boonkerz"><img src="https://avatars.githubusercontent.com/u/12484946?v=4&s=48" width="48" height="48" alt="boonkerz" title="boonkerz"/></a> <a href="https://github.com/boredland"><img src="https://avatars.githubusercontent.com/u/48156889?v=4&s=48" width="48" height="48" alt="boredland" title="boredland"/></a> <a href="https://github.com/brandongarner"><img src="https://avatars.githubusercontent.com/u/1402521?v=4&s=48" width="48" height="48" alt="brandongarner" title="brandongarner"/></a> <a href="https://github.com/briansunter"><img src="https://avatars.githubusercontent.com/u/1682188?v=4&s=48" width="48" height="48" alt="briansunter" title="briansunter"/></a> <a href="https://github.com/Buckeyefoobar"><img src="https://avatars.githubusercontent.com/u/5948599?v=4&s=48" width="48" height="48" alt="Buckeyefoobar" title="Buckeyefoobar"/></a>
  <a href="https://github.com/buger"><img src="https://avatars.githubusercontent.com/u/359382?v=4&s=48" width="48" height="48" alt="Greg V" title="Greg V"/></a> <a href="https://github.com/caioavidal"><img src="https://avatars.githubusercontent.com/u/4788787?v=4&s=48" width="48" height="48" alt="caioavidal" title="caioavidal"/></a> <a href="https://github.com/capnmidnight"><img src="https://avatars.githubusercontent.com/u/147986?v=4&s=48" width="48" height="48" alt="capnmidnight" title="capnmidnight"/></a> <a href="https://github.com/castarco"><img src="https://avatars.githubusercontent.com/u/3974596?v=4&s=48" width="48" height="48" alt="castarco" title="castarco"/></a> <a href="https://github.com/cburschka"><img src="https://avatars.githubusercontent.com/u/2071748?v=4&s=48" width="48" height="48" alt="Christian Burschka" title="Christian Burschka"/></a> <a href="https://github.com/cead22"><img src="https://avatars.githubusercontent.com/u/152510?v=4&s=48" width="48" height="48" alt="cead22" title="cead22"/></a> <a href="https://github.com/cjlarose"><img src="https://avatars.githubusercontent.com/u/344776?v=4&s=48" width="48" height="48" alt="Chris LaRose" title="Chris LaRose"/></a> <a href="https://github.com/cjlarose"><img src="https://avatars.githubusercontent.com/u/344776?v=4&s=48" width="48" height="48" alt="cjlarose" title="cjlarose"/></a> <a href="https://github.com/clem109"><img src="https://avatars.githubusercontent.com/u/13732758?v=4&s=48" width="48" height="48" alt="clem109" title="clem109"/></a> <a href="https://github.com/clemera"><img src="https://avatars.githubusercontent.com/u/17934823?v=4&s=48" width="48" height="48" alt="clemens.ramersthofer" title="clemens.ramersthofer"/></a> <a href="https://github.com/codekitchen"><img src="https://avatars.githubusercontent.com/u/143380?v=4&s=48" width="48" height="48" alt="codekitchen" title="codekitchen"/></a>
  <a href="https://github.com/codemac"><img src="https://avatars.githubusercontent.com/u/2451260?v=4&s=48" width="48" height="48" alt="codemac" title="codemac"/></a> <a href="https://github.com/codingdoug"><img src="https://avatars.githubusercontent.com/u/11843493?v=4&s=48" width="48" height="48" alt="codingdoug" title="codingdoug"/></a> <a href="https://github.com/connorads"><img src="https://avatars.githubusercontent.com/u/12412393?v=4&s=48" width="48" height="48" alt="connorads" title="connorads"/></a> <a href="https://github.com/crdnn"><img src="https://avatars.githubusercontent.com/u/2500222?v=4&s=48" width="48" height="48" alt="Corentin Delcourt" title="Corentin Delcourt"/></a> <a href="https://github.com/crutchcorn"><img src="https://avatars.githubusercontent.com/u/23148612?v=4&s=48" width="48" height="48" alt="crutchcorn" title="crutchcorn"/></a> <a href="https://github.com/cyphase"><img src="https://avatars.githubusercontent.com/u/14978010?v=4&s=48" width="48" height="48" alt="cyphase" title="cyphase"/></a> <a href="https://github.com/daniel-hauser"><img src="https://avatars.githubusercontent.com/u/17959753?v=4&s=48" width="48" height="48" alt="Daniel Hauser" title="Daniel Hauser"/></a> <a href="https://github.com/DanielKilgallon"><img src="https://avatars.githubusercontent.com/u/47895351?v=4&s=48" width="48" height="48" alt="DanielKilgallon" title="DanielKilgallon"/></a> <a href="https://github.com/danscan"><img src="https://avatars.githubusercontent.com/u/3114081?v=4&s=48" width="48" height="48" alt="danscan" title="danscan"/></a> <a href="https://github.com/davidak"><img src="https://avatars.githubusercontent.com/u/1155472?v=4&s=48" width="48" height="48" alt="davidak" title="davidak"/></a>
  <a href="https://github.com/davidmreed"><img src="https://avatars.githubusercontent.com/u/4956566?v=4&s=48" width="48" height="48" alt="David Reed" title="David Reed"/></a> <a href="https://github.com/davidpeach"><img src="https://avatars.githubusercontent.com/u/12449787?v=4&s=48" width="48" height="48" alt="davidpeach" title="davidpeach"/></a> <a href="https://github.com/daxgames"><img src="https://avatars.githubusercontent.com/u/6410873?v=4&s=48" width="48" height="48" alt="daxgames" title="daxgames"/></a> <a href="https://github.com/deathbeam"><img src="https://avatars.githubusercontent.com/u/1796133?v=4&s=48" width="48" height="48" alt="deathbeam" title="deathbeam"/></a> <a href="https://github.com/derekcollison"><img src="https://avatars.githubusercontent.com/u/2797030?v=4&s=48" width="48" height="48" alt="Derek Collison" title="Derek Collison"/></a> <a href="https://github.com/derrickstaten"><img src="https://avatars.githubusercontent.com/u/6860433?v=4&s=48" width="48" height="48" alt="derrickstaten" title="derrickstaten"/></a> <a href="https://github.com/devninja"><img src="https://avatars.githubusercontent.com/u/1319754?v=4&s=48" width="48" height="48" alt="devninja" title="devninja"/></a> <a href="https://github.com/digitalbuddha"><img src="https://avatars.githubusercontent.com/u/13731713?v=4&s=48" width="48" height="48" alt="digitalbuddha" title="digitalbuddha"/></a> <a href="https://github.com/digitros"><img src="https://avatars.githubusercontent.com/u/17506103?v=4&s=48" width="48" height="48" alt="digitros" title="digitros"/></a> <a href="https://github.com/dimaguy"><img src="https://avatars.githubusercontent.com/u/22128016?v=4&s=48" width="48" height="48" alt="dimaguy" title="dimaguy"/></a>
  <a href="https://github.com/directhex"><img src="https://avatars.githubusercontent.com/u/7823044?v=4&s=48" width="48" height="48" alt="Ian Ward" title="Ian Ward"/></a> <a href="https://github.com/dogtopus"><img src="https://avatars.githubusercontent.com/u/10386163?v=4&s=48" width="48" height="48" alt="dogtopus" title="dogtopus"/></a> <a href="https://github.com/donaldali"><img src="https://avatars.githubusercontent.com/u/4582465?v=4&s=48" width="48" height="48" alt="Donald Ali" title="Donald Ali"/></a> <a href="https://github.com/dougmolineux"><img src="https://avatars.githubusercontent.com/u/14894863?v=4&s=48" width="48" height="48" alt="Doug Molineux" title="Doug Molineux"/></a> <a href="https://github.com/drboku"><img src="https://avatars.githubusercontent.com/u/6350185?v=4&s=48" width="48" height="48" alt="drboku" title="drboku"/></a> <a href="https://github.com/dshanske"><img src="https://avatars.githubusercontent.com/u/342183?v=4&s=48" width="48" height="48" alt="dshanske" title="dshanske"/></a> <a href="https://github.com/dylanhitt"><img src="https://avatars.githubusercontent.com/u/10382329?v=4&s=48" width="48" height="48" alt="dylanhitt" title="dylanhitt"/></a> <a href="https://github.com/e11i0t23"><img src="https://avatars.githubusercontent.com/u/22355321?v=4&s=48" width="48" height="48" alt="e11i0t23" title="e11i0t23"/></a> <a href="https://github.com/earthiverse"><img src="https://avatars.githubusercontent.com/u/11514317?v=4&s=48" width="48" height="48" alt="earthiverse" title="earthiverse"/></a> <a href="https://github.com/EdOverflow"><img src="https://avatars.githubusercontent.com/u/14177947?v=4&s=48" width="48" height="48" alt="EdOverflow" title="EdOverflow"/></a>
  <a href="https://github.com/edwardjhu"><img src="https://avatars.githubusercontent.com/u/17933335?v=4&s=48" width="48" height="48" alt="edwardjhu" title="edwardjhu"/></a> <a href="https://github.com/eggplants"><img src="https://avatars.githubusercontent.com/u/46424128?v=4&s=48" width="48" height="48" alt="eggplants" title="eggplants"/></a> <a href="https://github.com/ekzhang"><img src="https://avatars.githubusercontent.com/u/14998623?v=4&s=48" width="48" height="48" alt="ekzhang" title="ekzhang"/></a> <a href="https://github.com/eliquious"><img src="https://avatars.githubusercontent.com/u/6037791?v=4&s=48" width="48" height="48" alt="Eliquis Oliveira" title="Eliquis Oliveira"/></a> <a href="https://github.com/embik"><img src="https://avatars.githubusercontent.com/u/1329313?v=4&s=48" width="48" height="48" alt="Marcus Weiner" title="Marcus Weiner"/></a> <a href="https://github.com/enesanbar"><img src="https://avatars.githubusercontent.com/u/16278996?v=4&s=48" width="48" height="48" alt="enesanbar" title="enesanbar"/></a> <a href="https://github.com/ericwbailey"><img src="https://avatars.githubusercontent.com/u/6915079?v=4&s=48" width="48" height="48" alt="Eric Bailey" title="Eric Bailey"/></a> <a href="https://github.com/eropple"><img src="https://avatars.githubusercontent.com/u/5894881?v=4&s=48" width="48" height="48" alt="eropple" title="eropple"/></a> <a href="https://github.com/erriez"><img src="https://avatars.githubusercontent.com/u/4984441?v=4&s=48" width="48" height="48" alt="erriez" title="erriez"/></a> <a href="https://github.com/eschnett"><img src="https://avatars.githubusercontent.com/u/7503767?v=4&s=48" width="48" height="48" alt="Erik Schnetter" title="Erik Schnetter"/></a>
  <a href="https://github.com/ethanwillis"><img src="https://avatars.githubusercontent.com/u/13518409?v=4&s=48" width="48" height="48" alt="ethanwillis" title="ethanwillis"/></a> <a href="https://github.com/evansneath"><img src="https://avatars.githubusercontent.com/u/967319?v=4&s=48" width="48" height="48" alt="evansneath" title="evansneath"/></a> <a href="https://github.com/evilham"><img src="https://avatars.githubusercontent.com/u/3517620?v=4&s=48" width="48" height="48" alt="evilham" title="evilham"/></a> <a href="https://github.com/ewized"><img src="https://avatars.githubusercontent.com/u/11804441?v=4&s=48" width="48" height="48" alt="ewized" title="ewized"/></a> <a href="https://github.com/exussum12"><img src="https://avatars.githubusercontent.com/u/10433564?v=4&s=48" width="48" height="48" alt="exussum12" title="exussum12"/></a> <a href="https://github.com/ezekiiel"><img src="https://avatars.githubusercontent.com/u/32284851?v=4&s=48" width="48" height="48" alt="ezekiiel" title="ezekiiel"/></a> <a href="https://github.com/fabasoad"><img src="https://avatars.githubusercontent.com/u/13461970?v=4&s=48" width="48" height="48" alt="Yaroslav Polyakov" title="Yaroslav Polyakov"/></a> <a href="https://github.com/fatihacet"><img src="https://avatars.githubusercontent.com/u/2738428?v=4&s=48" width="48" height="48" alt="fatihacet" title="fatihacet"/></a> <a href="https://github.com/fcady"><img src="https://avatars.githubusercontent.com/u/1591536?v=4&s=48" width="48" height="48" alt="fcady" title="fcady"/></a> <a href="https://github.com/fer22f"><img src="https://avatars.githubusercontent.com/u/3045459?v=4&s=48" width="48" height="48" alt="Fernando Paredes" title="Fernando Paredes"/></a>
  <a href="https://github.com/feross"><img src="https://avatars.githubusercontent.com/u/1217681?v=4&s=48" width="48" height="48" alt="Feross Aboukhadijeh" title="Feross Aboukhadijeh"/></a> <a href="https://github.com/filcab"><img src="https://avatars.githubusercontent.com/u/2453956?v=4&s=48" width="48" height="48" alt="Filipe Cabecinhas" title="Filipe Cabecinhas"/></a> <a href="https://github.com/finnp"><img src="https://avatars.githubusercontent.com/u/77217?v=4&s=48" width="48" height="48" alt="Finn Pauls" title="Finn Pauls"/></a> <a href="https://github.com/fivefilters"><img src="https://avatars.githubusercontent.com/u/678189?v=4&s=48" width="48" height="48" alt="fivefilters" title="fivefilters"/></a> <a href="https://github.com/fizker"><img src="https://avatars.githubusercontent.com/u/2059048?v=4&s=48" width="48" height="48" alt="fizker" title="fizker"/></a> <a href="https://github.com/flackbash"><img src="https://avatars.githubusercontent.com/u/6530328?v=4&s=48" width="48" height="48" alt="flackbash" title="flackbash"/></a> <a href="https://github.com/FlammableLemons"><img src="https://avatars.githubusercontent.com/u/68391329?v=4&s=48" width="48" height="48" alt="FlammableLemons" title="FlammableLemons"/></a> <a href="https://github.com/fletcher91"><img src="https://avatars.githubusercontent.com/u/514981?v=4&s=48" width="48" height="48" alt="fletcher91" title="fletcher91"/></a> <a href="https://github.com/flying-sheep"><img src="https://avatars.githubusercontent.com/u/1138433?v=4&s=48" width="48" height="48" alt="flying-sheep" title="flying-sheep"/></a> <a href="https://github.com/franciscocpg"><img src="https://avatars.githubusercontent.com/u/26282252?v=4&s=48" width="48" height="48" alt="franciscocpg" title="franciscocpg"/></a>
  <a href="https://github.com/franklsf95"><img src="https://avatars.githubusercontent.com/u/31685443?v=4&s=48" width="48" height="48" alt="franklsf95" title="franklsf95"/></a> <a href="https://github.com/freddierice"><img src="https://avatars.githubusercontent.com/u/4224413?v=4&s=48" width="48" height="48" alt="freddierice" title="freddierice"/></a> <a href="https://github.com/fredericguilbert"><img src="https://avatars.githubusercontent.com/u/22576950?v=4&s=48" width="48" height="48" alt="Frédéric Guilbert" title="Frédéric Guilbert"/></a> <a href="https://github.com/frewsxcv"><img src="https://avatars.githubusercontent.com/u/552400?v=4&s=48" width="48" height="48" alt="Corey Farwell" title="Corey Farwell"/></a> <a href="https://github.com/frodeborli"><img src="https://avatars.githubusercontent.com/u/1955408?v=4&s=48" width="48" height="48" alt="frodeborli" title="frodeborli"/></a> <a href="https://github.com/g-k"><img src="https://avatars.githubusercontent.com/u/1520530?v=4&s=48" width="48" height="48" alt="g-k" title="g-k"/></a> <a href="https://github.com/gabek"><img src="https://avatars.githubusercontent.com/u/922927?v=4&s=48" width="48" height="48" alt="Gabe Koss" title="Gabe Koss"/></a> <a href="https://github.com/garymathews"><img src="https://avatars.githubusercontent.com/u/1056055?v=4&s=48" width="48" height="48" alt="garymathews" title="garymathews"/></a> <a href="https://github.com/garyttierney"><img src="https://avatars.githubusercontent.com/u/3869295?v=4&s=48" width="48" height="48" alt="Gary Tierney" title="Gary Tierney"/></a> <a href="https://github.com/gavinmn"><img src="https://avatars.githubusercontent.com/u/42442905?v=4&s=48" width="48" height="48" alt="gavinmn" title="gavinmn"/></a>
  <a href="https://github.com/geek1011"><img src="https://avatars.githubusercontent.com/u/15333294?v=4&s=48" width="48" height="48" alt="geek1011" title="geek1011"/></a> <a href="https://github.com/georgyo"><img src="https://avatars.githubusercontent.com/u/180741?v=4&s=48" width="48" height="48" alt="georgyo" title="georgyo"/></a> <a href="https://github.com/ggiamarchi"><img src="https://avatars.githubusercontent.com/u/399644?v=4&s=48" width="48" height="48" alt="ggiamarchi" title="ggiamarchi"/></a> <a href="https://github.com/ghuntley"><img src="https://avatars.githubusercontent.com/u/4672627?v=4&s=48" width="48" height="48" alt="Geoffrey Huntley" title="Geoffrey Huntley"/></a> <a href="https://github.com/ghuseynov"><img src="https://avatars.githubusercontent.com/u/3964411?v=4&s=48" width="48" height="48" alt="ghuseynov" title="ghuseynov"/></a> <a href="https://github.com/gilliek"><img src="https://avatars.githubusercontent.com/u/2542110?v=4&s=48" width="48" height="48" alt="Julien Gilli" title="Julien Gilli"/></a> <a href="https://github.com/gkze">
