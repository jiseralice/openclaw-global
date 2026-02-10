# 🦞 OpenClaw — パーソナルAIアシスタント

<p align="center">
    <picture>
        <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/openclaw/openclaw/main/docs/assets/openclaw-logo-text-dark.png">
        <img src="https://raw.githubusercontent.com/openclaw/openclaw/main/docs/assets/openclaw-logo-text.png" alt="OpenClaw" width="500">
    </picture>
</p>

<p align="center">
  <strong>変態! 変態!</strong>
</p>

<p align="center">
  <a href="https://github.com/openclaw/openclaw/actions/workflows/ci.yml?branch=main"><img src="https://img.shields.io/github/actions/workflow/status/openclaw/openclaw/ci.yml?branch=main&style=for-the-badge" alt="CI status"></a>
  <a href="https://github.com/openclaw/openclaw/releases"><img src="https://img.shields.io/github/v/release/openclaw/openclaw?include_prereleases&style=for-the-badge" alt="GitHub release"></a>
  <a href="https://discord.gg/clawd"><img src="https://img.shields.io/discord/1456350064065904867?label=Discord&logo=discord&logoColor=white&color=5865F2&style=for-the-badge" alt="Discord"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge" alt="MIT License"></a>
</p>

**OpenClaw** は、あなたのデバイス上で動作するパーソナルAIアシスタントです。WhatsApp、Telegram、Slack、Discord、Google Chat、Signal、iMessage、Microsoft Teams、WebChatなどの一般的なチャネルや、BlueBubbles、Matrix、Zalo、Zalo Personalなどの拡張チャネルを通じてサポートを提供します。macOS/iOS/Androidをサポートし、ユーザーが制御可能なリアルタイムCanvasインターフェースをレンダリングできます。ゲートウェイは単なるコントロールプラットフォームであり、製品自体が真のアシスタントです。
ローカルで動作し、高速で、常時オンラインのシングルユーザー個人アシスタントをお探しであれば、それがこれです。

[公式サイト](https://openclaw.ai) · [公式ドキュメント](https://docs.openclaw.ai) · [DeepWiki](https://deepwiki.com/openclaw/openclaw) · [スタートガイド](https://docs.openclaw.ai/start/getting-started) · [アップデート](https://docs.openclaw.ai/install/updating) · [ケーススタディ](https://docs.openclaw.ai/start/showcase) · [FAQ](https://docs.openclaw.ai/start/faq) · [ウィザード](https://docs.openclaw.ai/start/wizard) · [Nix](https://github.com/openclaw/nix-clawdbot) · [Docker](https://docs.openclaw.ai/install/docker) · [Discord](https://discord.gg/clawd)

推奨セットアップ：設定ウィザード(`openclaw onboard`)を実行してください。ゲートウェイ、ワークスペース、チャンネル、スキルの設定を案内します。コマンドラインウィザードは **macOS、Linux、およびWindows (WSL2経由; 強く推奨)** 上で実行することを推奨します。npm、pnpm、またはbunをサポートしています。新規インストールの場合は、ここから開始してください：[スタートガイド](https://docs.openclaw.ai/start/getting-started)

**サブスクリプション (OAuth):**

- **[Anthropic](https://www.anthropic.com/)** (Claude Pro/Max)
- **[OpenAI](https://openai.com/)** (ChatGPT/Codex)

モデルに関する注釈：すべてのモデルがサポートされていますが、より優れた長時間動作性能と干渉耐性を得るために、**Anthropic Pro/Max (100/200) + Opus 4.6** を強く推奨します。[オンラインガイド](https://docs.openclaw.ai/start/onboarding)を参照してください。

## モデル (選択 + 認証)

- モデル構成 + CLI: [モデル](https://docs.openclaw.ai/concepts/models)
- 認証プロファイル (OAuth vs APIキー) + フォールバック: [モデルフォールオーバー](https://docs.openclaw.ai/concepts/model-failover)

## インストール

実行環境: **Node ≥22**.

```bash
npm install -g openclaw@latest
# または: pnpm add -g openclaw@latest

openclaw onboard --install-daemon
```

ウィザードはGatewayデーモン(launchd/systemdユーザーサービス)をインストールし、実行状態を維持します。

## クイックスタート (TL;DR)

実行環境: **Node ≥22**.

完全な初心者ガイド(認証、ペアリング、チャネル)：Full beginner guide (auth, pairing, channels): [Getting started](https://docs.openclaw.ai/start/getting-started)

```bash
openclaw onboard --install-daemon

openclaw gateway --port 18789 --verbose

# メッセージ送信
openclaw message send --to +1234567890 --message "Hello from OpenClaw"

# アシスタントとチャット (接続されたチャネルに任意のメッセージを送信可能: WhatsApp/Telegram/Slack/Discord/Google Chat/Signal/iMessage/BlueBubbles/Microsoft Teams/Matrix/Zalo/Zalo Personal/WebChat)
openclaw agent --message "Ship checklist" --thinking high
```

アップグレード方法? [アップデートガイド](https://docs.openclaw.ai/install/updating) (`openclaw doctor`を実行してください)。

## 開発版ステータス説明

- **stable**: タグ付きリリース (`vYYYY.M.D` または `vYYYY.M.D-<patch>`), npm dist-tag `latest`.
- **beta**: プレリリースタグ (`vYYYY.M.D-beta.N`), npm dist-tag `beta` (macOSアプリが欠落している場合があります)。
- **dev**: `main`の先頭、npm dist-tag `dev` (公開されている場合)。

切り替え (git + npm): `openclaw update --channel stable|beta|dev`.
詳細: [開発版ステータス](https://docs.openclaw.ai/install/development-channels).

## ソース (開発)

ビルドには`pnpm`を推奨します。TypeScriptを直接実行する場合はBunも選択可能です。

```bash
git clone https://github.com/openclaw/openclaw.git
cd openclaw

pnpm install
pnpm ui:build # 初回実行時にUI依存関係を自動インストール
pnpm build

pnpm openclaw onboard --install-daemon

# 開発ループ (TS変更時に自動再読み込み)
pnpm gateway:watch
```

注意: `pnpm openclaw ...`はTypeScriptを直接実行します(`tsx`経由)。`pnpm build`はNode経由で実行/パッケージングするための`dist/`を生成します。

## セキュリティデフォルト設定（DMアクセス権）

OpenClawは実際のIMプラットフォームに接続します。受信したダイレクトメッセージは**信頼できない入力**として扱ってください。

完全なセキュリティガイド: [セキュリティガイド](https://docs.openclaw.ai/gateway/security)

Telegram/WhatsApp/Signal/iMessage/Microsoft Teams/Discord/Google Chat/Slackのデフォルト動作:

- **DMペアリング** (`dmPolicy="pairing"` / `channels.discord.dm.policy="pairing"` / `channels.slack.dm.policy="pairing"`): 不明な送信者は短いペアリングコードを受け取り、ボットはそのメッセージを処理しません。
- 承認: `openclaw pairing approve <channel> <code>` (その後、送信者をローカルストレージに追加)。
- 公開受信DMには明示的なオプトインが必要: `dmPolicy="open"`を設定し、チャネル許可リストに`"*"`を含めます(`allowFrom` / `channels.discord.dm.allowFrom` / `channels.slack.dm.allowFrom`)。

`openclaw doctor`を実行してリスクのある/誤ったDMポリシーを検出します。

## キーポイント

- **[ローカルファーストゲートウェイ](https://docs.openclaw.ai/gateway)** — セッション、チャネル、ツール、イベントの単一制御プレーン。
- **[マルチチャネルインボックス](https://docs.openclaw.ai/channels)** — WhatsApp、Telegram、Slack、Discord、Google Chat、Signal、BlueBubbles (iMessage)、iMessage (レガシー)、Microsoft Teams、Matrix、Zalo、Zalo Personal、WebChat、macOS、iOS/Android。
- **[マルチエージェントルーティング](https://docs.openclaw.ai/gateway/configuration)** — 受信チャネル/アカウント/ピアを分離されたエージェント(ワークスペース + 各エージェントのセッション)にルーティング。
- **[音声ウェイクアップ](https://docs.openclaw.ai/nodes/voicewake) + [トークモード](https://docs.openclaw.ai/nodes/talk)** — macOS/iOS/Android向けのElevenLabsによる常時オン音声機能。
- **[ライブCanvas](https://docs.openclaw.ai/platforms/mac/canvas)** — [A2UI](https://docs.openclaw.ai/platforms/mac/canvas#canvas-a2ui)を採用したエージェントベースのビジュアルワークスペース。
- **[一流のツール](https://docs.openclaw.ai/tools)** — ブラウザ、Canvas、ノード、cronジョブ、セッション、Discord/Slack操作。
- **[コンパニオンアプリ](https://docs.openclaw.ai/platforms/macos)** — macOSメニューバーアプリ + iOS/Android [ノード](https://docs.openclaw.ai/nodes)。
- **[ウィザード](https://docs.openclaw.ai/start/wizard) + [スキル](https://docs.openclaw.ai/tools/skills)** — ウィザードベースのセットアップ、バンドル/マネージド/ワークスペーススキル。

## スター履歴

[![Star History Chart](https://api.star-history.com/svg?repos=openclaw/openclaw&type=date&legend=top-left)](https://www.star-history.com/#openclaw/openclaw&type=date&legend=top-left)

## 私たちがこれまでに行ったこと

### コアプラットフォーム

- [ゲートウェイコントロールパネル](https://docs.openclaw.ai/gateway) セッション、状態、構成、cronジョブ、Webhooks、[インタラクティブUI](https://docs.openclaw.ai/web)、および[Canvasホスト](https://docs.openclaw.ai/platforms/mac/canvas#canvas-a2ui)を含む。
- [CLIインターフェース](https://docs.openclaw.ai/tools/agent-send): ゲートウェイ、エージェント、送信、[ウィザード](https://docs.openclaw.ai/start/wizard)、および[セキュリティ](https://docs.openclaw.ai/gateway/doctor)。
- [Piエージェントランタイム](https://docs.openclaw.ai/concepts/agent) RPCパターン、ツールストリーミング、チャンクストリーミング対応。
- [セッションモデル](https://docs.openclaw.ai/concepts/session): `main`は直接チャット、グループ分離、アクティベーションモード、キューイングモード、返信用。グループルール：[グループ](https://docs.openclaw.ai/concepts/groups)。
- [メディアチャネル](https://docs.openclaw.ai/nodes/images): 画像/音声/動画、トランスクリプションフック、サイズ制限、一時ファイルライフサイクル。音声の詳細：[音声](https://docs.openclaw.ai/nodes/audio)。

### チャネル

- [チャネル](https://docs.openclaw.ai/channels): [WhatsApp](https://docs.openclaw.ai/channels/whatsapp) (Baileys)、[Telegram](https://docs.openclaw.ai/channels/telegram) (grammY)、[Slack](https://docs.openclaw.ai/channels/slack) (Bolt)、[Discord](https://docs.openclaw.ai/channels/discord) (discord.js)、[Google Chat](https://docs.openclaw.ai/channels/googlechat) (Chat API)、[Signal](https://docs.openclaw.ai/channels/signal) (signal-cli)、[BlueBubbles](https://docs.openclaw.ai/channels/bluebubbles) (iMessage, 推奨)、[iMessage](https://docs.openclaw.ai/channels/imessage) (レガシーimsg)、[Microsoft Teams](https://docs.openclaw.ai/channels/msteams) (拡張機能)、[Matrix](https://docs.openclaw.ai/channels/matrix) (拡張機能)、[Zalo](https://docs.openclaw.ai/channels/zalo) (拡張機能)、[Zalo Personal](https://docs.openclaw.ai/channels/zalouser) (拡張機能)、[WebChat](https://docs.openclaw.ai/web/webchat)。
- [グループルーティング](https://docs.openclaw.ai/concepts/group-messages): メンションゲート、返信タグ、チャネル別チャンキングとルーティング。チャネルルール：[チャネル](https://docs.openclaw.ai/channels)。

### アプリ + ノード

- [macOSアプリ](https://docs.openclaw.ai/platforms/macos): メニューバー制御プレーン、[音声ウェイクアップ](https://docs.openclaw.ai/nodes/voicewake)/PTT、[トークモード](https://docs.openclaw.ai/nodes/talk)オーバーレイ、[WebChat](https://docs.openclaw.ai/web/webchat)、デバッグツール、[リモートゲートウェイ](https://docs.openclaw.ai/gateway/remote)制御。
- [iOSノード](https://docs.openclaw.ai/platforms/ios): [Canvas](https://docs.openclaw.ai/platforms/mac/canvas)、[音声ウェイクアップ](https://docs.openclaw.ai/nodes/voicewake)、[トークモード](https://docs.openclaw.ai/nodes/talk)、カメラ、画面録画、Bonjourペアリング。
- [Androidノード](https://docs.openclaw.ai/platforms/android): [Canvas](https://docs.openclaw.ai/platforms/mac/canvas)、[トークモード](https://docs.openclaw.ai/nodes/talk)、カメラ、画面録画、オプショナルSMS機能。
- [macOSノードモード](https://docs.openclaw.ai/nodes): システム実行/通知 + Canvas/カメラ露出。

### ツール + オートメーション

- [ブラウザコントロール](https://docs.openclaw.ai/tools/browser): 専用openclaw Chrome/Chromium、スナップショット、操作、アップロード、プロファイル。
- [Canvas](https://docs.openclaw.ai/platforms/mac/canvas): [A2UI](https://docs.openclaw.ai/platforms/mac/canvas#canvas-a2ui)プッシュ/リセット、評価、スナップショット。
- [ノード](https://docs.openclaw.ai/nodes): カメラスナップショット/クリップ、画面録画、[位置取得](https://docs.openclaw.ai/nodes/location-command)、通知
- [Cronジョブ + ウェイクアップ](https://docs.openclaw.ai/automation/cron-jobs); [webhooks](https://docs.openclaw.ai/automation/webhook); [Gmail Pub/Sub](https://docs.openclaw.ai/automation/gmail-pubsub)。
- [スキルプラットフォーム](https://docs.openclaw.ai/tools/skills)：バンドル、管理、ワークスペーススキル、インストール制限とUIあり。

### 運用 + セキュリティ

- [チャネルルーティング](https://docs.openclaw.ai/concepts/channel-routing)、[リトライポリシー](https://docs.openclaw.ai/concepts/retry)、および[ストリーミング/チャンキング](https://docs.openclaw.ai/concepts/streaming)。
- [プレゼンス](https://docs.openclaw.ai/concepts/presence)、[入力表示](https://docs.openclaw.ai/concepts/typing-indicators)、および[使用量追跡](https://docs.openclaw.ai/concepts/usage-tracking)。
- [モデル](https://docs.openclaw.ai/concepts/models)、[モデルフォールオーバー](https://docs.openclaw.ai/concepts/model-failover)、および[セッション](https://docs.openclaw.ai/concepts/session-pruning)。
- [セキュリティ](https://docs.openclaw.ai/gateway/security)および[トラブルシューティング](https://docs.openclaw.ai/channels/troubleshooting)。

### オプス + パッケージング

- [コントロールインターフェース](https://docs.openclaw.ai/web) + [WebChat](https://docs.openclaw.ai/web/webchat)はゲートウェイによって直接提供されます。
- [Tailscale Serve/Funnel](https://docs.openclaw.ai/gateway/tailscale)または[SSHトンネル](https://docs.openclaw.ai/gateway/remote)トークン/パスワード認証を使用
- [Nixモード](https://docs.openclaw.ai/install/nix)宣言的構成をサポート; [Docker](https://docs.openclaw.ai/install/docker)インストールベース
- [セキュリティ](https://docs.openclaw.ai/gateway/doctor)フォールバック、[ログ](https://docs.openclaw.ai/logging)。

## 仕組み（概要）

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

## 主要サブシステム

- **[Gateway WebSocket通信](https://docs.openclaw.ai/concepts/architecture)** — クライアント、ツール、イベントの単一WS制御プレーン（および操作：[Gatewayハンドブック](https://docs.openclaw.ai/gateway))。
- **[Tailscale露出](https://docs.openclaw.ai/gateway/tailscale)** — Gatewayダッシュボード用のServe/Funnel + WS（リモートアクセス：[リモートアクセス](https://docs.openclaw.ai/gateway/remote))。
- **[ブラウザコントロール](https://docs.openclaw.ai/tools/browser)** — CDP制御のopenclaw管理Chrome/Chromium。
- **[Canvas + A2UI](https://docs.openclaw.ai/platforms/mac/canvas)** — エージェント駆動ビジュアルワークスペース（A2UIホスト：[Canvas/A2UI](https://docs.openclaw.ai/platforms/mac/canvas#canvas-a2ui))。
- **[音声ウェイクアップ](https://docs.openclaw.ai/nodes/voicewake) + [トークモード](https://docs.openclaw.ai/nodes/talk)** — 常時オン音声機能、継続的会話の実現。
- **[ノード](https://docs.openclaw.ai/nodes)** — Canvas、カメラスナップショット/クリップ、画面録画、`location.get`、通知、およびmacOS専用`system.run`/`system.notify`。

## Tailscaleアクセス（ゲートウェイコントロールパネル）

OpenClawはTailscaleを自動構成できます **Serve** (tailnetのみ)または**Funnel** (パブリック)、ゲートウェイはループバックインターフェースにバインドされたままになります。`gateway.tailscale.mode`を設定:

- `off`: Tailscale自動化をオフ（デフォルト）。
- `serve`: tailnetのみHTTPS via `tailscale serve` (デフォルトでTailscaleヘッダー使用)。
- `funnel`: パブリックHTTPS via `tailscale funnel` (共有パスワード認証が必要)。

説明:

- `gateway.bind`はServe/Funnelが有効な場合は`loopback`のままにする必要があります（OpenClawはこの操作を強制します）。
- `gateway.auth.mode: "password"`または`gateway.auth.allowTailscale: false`を設定してサーバーパスワードを強制。
- `gateway.auth.mode: "password"`が設定されていない限り実行を拒否。
- オプション`gateway.tailscale.resetOnExit`はシャットダウン時にServe/Funnel操作を取り消すことができます。

詳細: [Tailscaleガイド](https://docs.openclaw.ai/gateway/tailscale) · [Webページ](https://docs.openclaw.ai/web)

## リモートゲートウェイ (Linux互換性向上)

小さなLinuxインスタンスでゲートウェイを実行するのは問題ありません。クライアント(macOSアプリ、CLI、WebChat)は**Tailscale Serve/Funnel**または**SSHトンネル**経由で接続でき、必要に応じてデバイスノード(macOS/iOS/Android)をペアリングしてデバイスローカル操作を実行できます。

- **ゲートウェイホスト** は通常、ツールを実行しチャネル接続を確立します。
- **デバイスノード** はデバイスローカル操作(`system.run`など、カメラ、画面録画、通知)を`node.invoke`経由で実行します。
  要するに：実行はゲートウェイがある場所で行われる；デバイス操作はデバイスがある場所で行われる。

詳細: [リモートアクセス](https://docs.openclaw.ai/gateway/remote) · [ノード](https://docs.openclaw.ai/nodes) · [セキュリティ](https://docs.openclaw.ai/gateway/security)

## macOS Gatewayプロトコル経由の権限

macOSアプリは**ノードモード**で実行され、ゲートウェイWebSocket(`node.list` / `node.describe`)経由で機能と権限マッピングをブロードキャストできます。クライアントはその後、ローカル操作を`node.invoke`経由で実行できます:

- `system.run` ローカルコマンドを実行しstdout/stderr/終了コードを返す；`needsScreenRecording: true`を設定して画面録画権限が必要な場合（さもなくば`PERMISSION_MISSING`エラーが発生）。
- `system.notify` ユーザーに通知を送信、通知が拒否された場合は失敗。
- `canvas.*`、`camera.*`、`screen.record`、および`location.get`は`node.invoke`経由でルーティングされ、TCC権限状態に従います。

昇格されたbash(ホスト権限)とmacOS TCCは別々です:

- `/elevated on|off`を使用して各セッションの昇格アクセスを切り替える（有効化+許可リストへの追加時）。
- ゲートウェイは(WSメソッド経由および`sessions.patch`経由で)各セッションの切り替えを永続化します。`thinkingLevel`、`verboseLevel`、`model`、`sendPolicy`、および`groupActivation`。

詳細: [ノード](https://docs.openclaw.ai/nodes) · [macOSアプリ](https://docs.openclaw.ai/platforms/macos) · [ゲートウェイプロトコル](https://docs.openclaw.ai/concepts/architecture)

## エージェント間通信 (sessions_* ツール)

- この機能を使用すると、チャットインターフェース間を切り替えることなくセッション間で作業を調整できます。
- `sessions_list` — アクティブなセッション(エージェント)とそのメタデータを検出。
- `sessions_history` — セッションの記録ログを取得。
- `sessions_send` — 他のセッションにメッセージを送信；オプショナル返信パドル + アナウンスステップ(REPLY_SKIP、ANNOUNCE_SKIP)。

詳細: [セッションツール](https://docs.openclaw.ai/concepts/session-tool)

## スキル登録 (ClawHub)

ClawHubは極小のスキル登録システムです。ClawHubが有効になると、エージェントは自動的にスキルを検索し、必要に応じて新しいスキルを追加できます。

[ClawHub](https://clawhub.com)

## チャットコマンド

WhatsApp/Telegram/Slack/Google Chat/Microsoft Teams/WebChat経由でこれらを送信してください（グループコマンドはグループ管理者のみ利用可能）：

- `/status` — 簡潔なセッション状態（モデル+tokens、利用可能な場合は料金）
- `/new` または `/reset` — セッションをリセット
- `/compact` — 簡潔なセッションコンテキスト（要約）
- `/think <level>` — off|minimal|low|medium|high|xhigh (GPT-5.2 + Codexモデルのみ)
- `/verbose on|off`
- `/usage off|tokens|full` — 各応答のトークン使用量
- `/restart` — ゲートウェイを再起動 (グループ管理者のみ)
- `/activation mention|always` — グループアクティベーションスイッチ（グループ限定）

## アプリ (オプション)

ゲートウェイ自体が素晴らしい体験を提供します。すべてのアプリケーションはオプションであり、追加機能を提供します。

コンパニオンアプリケーションの構築/実行を計画している場合は、以下のプラットフォームハンドブックに従ってください。

### macOS (OpenClaw.app) (オプション)

- ゲートウェイとヘルスチェックのメニューバー制御。
- 音声ウェイクアップ + ワンクリックトークオーバーレイ機能。
- WebChat + デバッグツール。
- SSH経由のリモートゲートウェイ制御。

注意：署名付きビルドを使用する必要があります。macOS権限は再構築後も維持されます（`docs/mac/permissions.md`を参照）。

### iOSノード (オプション)

- ブリッジ経由でペアリングされたノードとして機能。
- 音声トリガー転送 + Canvasサーフェス。
- `openclaw nodes …`経由での制御。

ハンドブック: [iOS接続](https://docs.openclaw.ai/platforms/ios)。

### Androidノード (オプション)

- iOSと同じブリッジ+ペアリングプロセス経由でペアリング。
- Canvas、Camera、Screen capture commands権限を許可。
- ハンドブック: [Android接続](https://docs.openclaw.ai/platforms/android)。

## エージェントワークスペース + スキル

- ワークスペースルート: `~/.openclaw/workspace` (`agents.defaults.workspace`経由で構成可能)。
- 注入されるプロンプトファイル: `AGENTS.md`、`SOUL.md`、`TOOLS.md`。
- スキル: `~/.openclaw/workspace/skills/<skill>/SKILL.md`。

## 設定

[完全な設定リファレンス (すべてのキーとサンプルはこちら).](https://docs.openclaw.ai/gateway/configuration)

## セーフモード (重要)

- **デフォルト設定:** ツールはホスト上でメインセッションとして実行されるため、あなただけが利用する場合、エージェントは完全なアクセス権を持ちます。
- **グループ/チャンネルチャネルセキュリティ:** 各セッションをサンドボックスおよびDocker内で `agents.defaults.sandbox.mode: "non-main"` を設定して **non‑main sessions** (グループ/チャンネルチャネル) として実行します。その後、Docker内でbashセッションとして実行します。
- **サンドボックスデフォルト:** `bash`, `process`, `read`, `write`, `edit`, `sessions_list`, `sessions_history`, `sessions_send`, `sessions_spawn` の実行を許可します。`browser`, `canvas`, `nodes`, `cron`, `discord`, `gateway` は禁止されています。

詳細: [セキュリティガイドライン](https://docs.openclaw.ai/gateway/security) · [Docker + サンドボックス](https://docs.openclaw.ai/install/docker) · [サンドボックス設定](https://docs.openclaw.ai/gateway/configuration)

### [WhatsApp](https://docs.openclaw.ai/channels/whatsapp)

- デバイスリンク: `pnpm openclaw channels login` (認証情報を `~/.openclaw/credentials` に保存)。
- `channels.whatsapp.allowFrom` を介して、アシスタントと会話できるユーザーをホワイトリストに追加できます。
- `channels.whatsapp.groups` が設定されている場合、これはグループの許可リストになります。`"*"` を含めると、すべてのユーザーを許可できます。

### [Telegram](https://docs.openclaw.ai/channels/telegram)

- `TELEGRAM_BOT_TOKEN` または `channels.telegram.botToken` を設定します (環境変数が優先されます)。
- オプション: `channels.telegram.groups` (`channels.telegram.groups."*".requireMention` 経由) を設定します。一度設定すると、許可リストが作成されます (`"*"` を含めるとすべてを許可)。必要に応じて `channels.telegram.allowFrom` または `channels.telegram.webhookUrl` + `channels.telegram.webhookSecret` を使用します。

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

- `SLACK_BOT_TOKEN` + `SLACK_APP_TOKEN` を設定するか、`channels.slack.botToken` + `channels.slack.appToken` を設定します。

### [Discord](https://docs.openclaw.ai/channels/discord)

- `DISCORD_BOT_TOKEN` または `channels.discord.token` を設定します (環境変数が優先されます)。
- オプション: 必要に応じて `commands.native`, `commands.text`, または `commands.useAccessGroups` および `channels.discord.dm.allowFrom`, `channels.discord.guilds`, または `channels.discord.mediaMaxMb` を設定します。

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

- `signal-cli` が必要で、`channels.signal` 設定を構成する必要があります。

### [BlueBubbles (iMessage)](https://docs.openclaw.ai/channels/bluebubbles)

- **推奨される** iMessage統合
- `channels.bluebubbles.serverUrl` + `channels.bluebubbles.password` および webhook (`channels.bluebubbles.webhookPath`) を設定します。
- BlueBubbles サーバーは macOS 上で実行されます。ゲートウェイは macOS または他のシステムで実行できます。

### [iMessage (レガシー)](https://docs.openclaw.ai/channels/imessage)

- レガシー macOS 統合のみ `imsg` ("メッセージ"アプリへのログインが必要)。
- `channels.imessage.groups` が設定されている場合、これは許可リストになります。`"*"` を含めるとすべてを許可します。

### [Microsoft Teams](https://docs.openclaw.ai/channels/msteams)

- Teams アプリ + Bot Framework を構成し、`msteams` 設定を追加します。
- 許可リスト `msteams.allowFrom`。グループは `msteams.groupAllowFrom` または `msteams.groupPolicy: "open"` を通じて設定されます。

### [Web Chat](https://docs.openclaw.ai/web/webchat)

- ゲートウェイ WebSocket を使用します。個別の WebChat ポート/設定はありません。

ブラウザコントロール (オプション):

```json5
{
  browser: {
    enabled: true,
    color: "#FF4500",
  },
}
```

## ドキュメント

セットアップ後、より深く参照できる資料が必要になる場合があります。

- [ドキュメントインデックスを最初に確認し、ナビゲーション方法と「コンテンツの場所」を確認してください。](https://docs.openclaw.ai)
- [ゲートウェイ+プロトコルモデルのアーキテクチャ概要を読む。](https://docs.openclaw.ai/concepts/architecture)
- [すべてのキーと例が必要な場合は、完全な設定リファレンスを使用してください。](https://docs.openclaw.ai/gateway/configuration)
- [ガイド付きのセットアッププロセスに従ってください。](https://docs.openclaw.ai/start/wizard)
- [Webhook インターフェース経由で外部トリガーを接続してください。](https://docs.openclaw.ai/automation/webhook)
- [Gmail Pub/Sub トリガーを設定してください。](https://docs.openclaw.ai/automation/gmail-pubsub)
- [macOS メニューバーアシスタントの詳細を確認してください。](https://docs.openclaw.ai/platforms/mac/menu-bar)
- [厳格な運用手順でゲートウェイを実行してください。](https://docs.openclaw.ai/gateway)
- [コントロール UI/Web インターフェースの動作方法と安全な公開方法を理解してください。](https://docs.openclaw.ai/web)
- [SSH トンネリングまたはテールネットによるリモートアクセスを理解してください。](https://docs.openclaw.ai/gateway/remote)
- [プラットフォームガイド: Windows (WSL2)](https://docs.openclaw.ai/platforms/windows), [Linux](https://docs.openclaw.ai/platforms/linux), [macOS](https://docs.openclaw.ai/platforms/macos), [iOS](https://docs.openclaw.ai/platforms/ios), [Android](https://docs.openclaw.ai/platforms/android)
- [一般的な問題のトラブルシューティングガイドを使用してください。](https://docs.openclaw.ai/channels/troubleshooting)
- [情報漏洩の前には、セキュリティガイドを必ずお読みください。](https://docs.openclaw.ai/gateway/security)

## 上級者向けドキュメント（発見 + 制御）

- [発見 + 変換](https://docs.openclaw.ai/gateway/discovery)
- [Bonjour/mDNS](https://docs.openclaw.ai/gateway/bonjour)
- [ゲートウェイペアリング](https://docs.openclaw.ai/gateway/pairing)
- [リモートゲートウェイ README](https://docs.openclaw.ai/gateway/remote-gateway-readme)
- [コントロールインターフェース](https://docs.openclaw.ai/web/control-ui)
- [ダッシュボード](https://docs.openclaw.ai/web/dashboard)

## 操作とトラブルシューティング

- [ヘルスチェック](https://docs.openclaw.ai/gateway/health)
- [ゲートウェイロック](https://docs.openclaw.ai/gateway/gateway-lock)
- [バックグラウンドプロセス](https://docs.openclaw.ai/gateway/background-process)
- [ブラウザトラブルシューティング (Linux)](https://docs.openclaw.ai/tools/browser-linux-troubleshooting)
- [ログ記録](https://docs.openclaw.ai/logging)

## 深層探求

- [エージェントループ](https://docs.openclaw.ai/concepts/agent-loop)
- [リアルタイムプレゼンス](https://docs.openclaw.ai/concepts/presence)
- [TypeBox スキーマ](https://docs.openclaw.ai/concepts/typebox)
- [RPC アダプター](https://docs.openclaw.ai/reference/rpc)
- [キュー](https://docs.openclaw.ai/concepts/queue)

## ワークスペースとスキル

- [スキル設定](https://docs.openclaw.ai/tools/skills-config)
- [デフォルトエージェント](https://docs.openclaw.ai/reference/AGENTS.default)
- [テンプレート: エージェント](https://docs.openclaw.ai/reference/templates/AGENTS)
- [テンプレート: BOOTSTRAP](https://docs.openclaw.ai/reference/templates/BOOTSTRAP)
- [テンプレート: IDENTITY](https://docs.openclaw.ai/reference/templates/IDENTITY)
- [テンプレート: SOUL](https://docs.openclaw.ai/reference/templates/SOUL)
- [テンプレート: TOOLS](https://docs.openclaw.ai/reference/templates/TOOLS)
- [テンプレート: USER](https://docs.openclaw.ai/reference/templates/USER)

## プラットフォーム内部構造

- [macOS 開発環境](https://docs.openclaw.ai/platforms/mac/dev-setup)
- [macOS メニューバー](https://docs.openclaw.ai/platforms/mac/menu-bar)
- [macOS 音声起動](https://docs.openclaw.ai/platforms/mac/voicewake)
- [iOS ノード](https://docs.openclaw.ai/platforms/ios)
- [Android ノード](https://docs.openclaw.ai/platforms/android)
- [Windows (WSL2)](https://docs.openclaw.ai/platforms/windows)
- [Linux アプリ](https://docs.openclaw.ai/platforms/linux)

## メールフック (Gmail)

- [docs.openclaw.ai/gmail-pubsub](https://docs.openclaw.ai/automation/gmail-pubsub)

## Molty

OpenClaw は **Molty** スペースロブスター AI アシスタント用に開発されました。🦞
Peter Steinberger とコミュニティによって作成されました。

- [openclaw.ai](https://openclaw.ai)
- [soul.md](https://soul.md)
- [steipete.me](https://steipete.me)
- [@openclaw](https://x.com/openclaw)

## コミュニティ

貢献ガイドライン、メンテナー、PR 提出方法については [CONTRIBUTING.md](CONTRIBUTING.md) を参照してください。AI/vibe コーディングの PR を歓迎します！🤖

特別な感謝 [Mario Zechner](https://mariozechner.at/) のサポートと彼が開発した
[pi-mono](https://github.com/badlogic/pi-mono) に。
また、lobster.bot の開発に尽力した Adam Doppelt にも特別な感謝を。

すべての貢献者に感謝します：

<p align="left">
  <a href="https://github.com/steipete"><img src="https://avatars.githubusercontent.com/u/58493?v=4&s=48" width="48" height="48" alt="steipete" title="steipete"/></a> <a href="https://github.com/joshp123"><img src="https://avatars.githubusercontent.com/u/1497361?v=4&s=48" width="48" height="48" alt="joshp123" title="joshp123"/></a> <a href="https://github.com/cpojer"><img src="https://avatars.githubusercontent.com/u/13352?v=4&s=48" width="48" height="48" alt="cpojer" title="cpojer"/></a> <a href="https://github.com/mbelinky"><img src="https://avatars.githubusercontent.com/u/132747814?v=4&s=48" width="48" height="48" alt="Mariano Belinky" title="Mariano Belinky"/></a> <a href="https://github.com/plum-dawg"><img src="https://avatars.githubusercontent.com/u/5909950?v=4&s=48" width="48" height="48" alt="plum-dawg" title="plum-dawg"/></a> <a href="https://github.com/bohdanpodvirnyi"><img src="https://avatars.githubusercontent.com/u/31819391?v=4&s=48" width="48" height="48" alt="bohdanpodvirnyi" title="bohdanpodvirnyi"/></a> <a href="https://github.com/iHildy"><img src="https://avatars.githubusercontent.com/u/25069719?v=4&s=48" width="48" height="48" alt="iHildy" title="iHildy"/></a> <a href="https://github.com/jaydenfyi"><img src="https://avatars.githubusercontent.com/u/213395523?v=4&s=48" width="48" height="48" alt="jaydenfyi" title="jaydenfyi"/></a> <a href="https://github.com/joaohlisboa"><img src="https://avatars.githubusercontent.com/u/8200873?v=4&s=48" width="48" height="48" alt="joaohlisboa" title="joaohlisboa"/></a> <a href="https://github.com/mneves75"><img src="https://avatars.githubusercontent.com/u/2423436?v=4&s=48" width="48" height="48" alt="mneves75" title="mneves75"/></a>
  <a href="https://github.com/adam91holt"><img src="https://avatars.githubusercontent.com/u/9592417?v=4&s=48" width="48" height="48" alt="adam91holt" title="adam91holt"/></a> <a href="https://github.com/hougangdev"><img src="https://avatars.githubusercontent.com/u/105773686?v=4&s=48" width="48" height="48" alt="hougangdev" title="hougangdev"/></a> <a href="https://github.com/gumadeiras"><img src="https://avatars.githubusercontent.com/u/5599352?v=4&s=48" width="48" height="48" alt="gumadeiras" title="gumadeiras"/></a> <a href="https://github.com/shakkernerd"><img src="https://avatars.githubusercontent.com/u/165377636?v=4&s=48" width="48" height="48" alt="shakkernerd" title="shakkernerd"/></a> <a href="https://github.com/mteam88"><img src="https://avatars.githubusercontent.com/u/84196639?v=4&s=48" width="48" height="48" alt="mteam88" title="mteam88"/></a> <a href="https://github.com/hirefrank"><img src="https://avatars.githubusercontent.com/u/183158?v=4&s=48" width="48" height="48" alt="hirefrank" title="hirefrank"/></a> <a href="https://github.com/joeynyc"><img src="https://avatars.githubusercontent.com/u/17919866?v=4&s=48" width="48" height="48" alt="joeynyc" title="joeynyc"/></a> <a href="https://github.com/orlyjamie"><img src="https://avatars.githubusercontent.com/u/6668807?v=4&s=48" width="48" height="48" alt="orlyjamie" title="orlyjamie"/></a> <a href="https://github.com/dbhurley"><img src="https://avatars.githubusercontent.com/u/5251425?v=4&s=48" width="48" height="48" alt="dbhurley" title="dbhurley"/></a> <a href="https://github.com/omniwired"><img src="https://avatars.githubusercontent.com/u/322761?v=4&s=48" width="48" height="48" alt="Eng. Juan Combetto" title="Eng. Juan Combetto"/></a>
  <a href="https://github.com/TSavo"><img src="https://avatars.githubusercontent.com/u/877990?v=4&s=48" width="48" height="48" alt="TSavo" title="TSavo"/></a> <a href="https://github.com/aerolalit"><img src="https://avatars.githubusercontent.com/u/17166039?v=4&s=48" width="48" height="48" alt="aerolalit" title="aerolalit"/></a> <a href="https://github.com/julianengel"><img src="https://avatars.githubusercontent.com/u/10634231?v=4&s=48" width="48" height="48" alt="julianengel" title="julianengel"/></a> <a href="https://github.com/bradleypriest"><img src="https://avatars.githubusercontent.com/u/167215?v=4&s=48" width="48" height="48" alt="bradleypriest" title="bradleypriest"/></a> <a href="https://github.com/benithors"><img src="https://avatars.githubusercontent.com/u/20652882?v=4&s=48" width="48" height="48" alt="benithors" title="benithors"/></a> <a href="https://github.com/rohannagpal"><img src="https://avatars.githubusercontent.com/u/4009239?v=4&s=48" width="48" height="48" alt="rohannagpal" title="rohannagpal"/></a> <a href="https://github.com/timolins"><img src="https://avatars.githubusercontent.com/u/1440854?v=4&s=48" width="48" height="48" alt="timolins" title="timolins"/></a> <a href="https://github.com/f-trycua"><img src="https://avatars.githubusercontent.com/u/195596869?v=4&s=48" width="48" height="48" alt="f-trycua" title="f-trycua"/></a> <a href="https://github.com/benostein"><img src="https://avatars.githubusercontent.com/u/31802821?v=4&s=48" width="48" height="48" alt="benostein" title="benostein"/></a> <a href="https://github.com/elliotsecops"><img src="https://avatars.githubusercontent.com/u/141947839?v=4&s=48" width="48" height="48" alt="elliotsecops" title="elliotsecops"/></a>
  <a href="https://github.com/Nachx639"><img src="https://avatars.githubusercontent.com/u/71144023?v=4&s=48" width="48" height="48" alt="nachx639" title="nachx639"/></a> <a href="https://github.com/pvoo"><img src="https://avatars.githubusercontent.com/u/20116814?v=4&s=48" width="48" height="48" alt="pvoo" title="pvoo"/></a> <a href="https://github.com/sreekaransrinath"><img src="https://avatars.githubusercontent.com/u/50989977?v=4&s=48" width="48" height="48" alt="sreekaransrinath" title="sreekaransrinath"/></a> <a href="https://github.com/gupsammy"><img src="https://avatars.githubusercontent.com/u/20296019?v=4&s=48" width="48" height="48" alt="gupsammy" title="gupsammy"/></a> <a href="https://github.com/cristip73"><img src="https://avatars.githubusercontent.com/u/24499421?v=4&s=48" width="48" height="48" alt="cristip73" title="cristip73"/></a> <a href="https://github.com/stefangalescu"><img src="https://avatars.githubusercontent.com/u/52995748?v=4&s=48" width="48" height="48" alt="stefangalescu" title="stefangalescu"/></a> <a href="https://github.com/nachoiacovino"><img src="https://avatars.githubusercontent.com/u/50103937?v=4&s=48" width="48" height="48" alt="nachoiacovino" title="nachoiacovino"/></a> <a href="https://github.com/vsabavat"><img src="https://avatars.githubusercontent.com/u/50385532?v=4&s=48" width="48" height="48" alt="Vasanth Rao Naik Sabavat" title="Vasanth Rao Naik Sabavat"/></a> <a href="https://github.com/petter-b"><img src="https://avatars.githubusercontent.com/u/62076402?v=4&s=48" width="48" height="48" alt="petter-b" title="petter-b"/></a> <a href="https://github.com/thewilloftheshadow"><img src="https://avatars.githubusercontent.com/u/35580099?v=4&s=48" width="48" height="48" alt="thewilloftheshadow" title="thewilloftheshadow"/></a>
  <a href="https://github.com/leszekszpunar"><img src="https://avatars.githubusercontent.com/u/13106764?v=4&s=48" width="48" height="48" alt="leszekszpunar" title="leszekszpunar"/></a> <a href="https://github.com/scald"><img src="https://avatars.githubusercontent.com/u/1215913?v=4&s=48" width="48" height="48" alt="scald" title="scald"/></a> <a href="https://github.com/andranik-sahakyan"><img src="https://avatars.githubusercontent.com/u/8908029?v=4&s=48" width="48" height="48" alt="andranik-sahakyan" title="andranik-sahakyan"/></a> <a href="https://github.com/davidguttman"><img src="https://avatars.githubusercontent.com/u/431694?v=4&s=48" width="48" height="48" alt="davidguttman" title="davidguttman"/></a> <a href="https://github.com/sleontenko"><img src="https://avatars.githubusercontent.com/u/7135949?v=4&s=48" width="48" height="48" alt="sleontenko" title="sleontenko"/></a> <a href="https://github.com/denysvitali"><img src="https://avatars.githubusercontent.com/u/4939519?v=4&s=48" width="48" height="48" alt="denysvitali" title="denysvitali"/></a> <a href="https://github.com/apps/clawdinator"><img src="https://avatars.githubusercontent.com/in/2607181?v=4&s=48" width="48" height="48" alt="clawdinator[bot]" title="clawdinator[bot]"/></a> <a href="https://github.com/sircrumpet"><img src="https://avatars.githubusercontent.com/u/4436535?v=4&s=48" width="48" height="48" alt="sircrumpet" title="sircrumpet"/></a> <a href="https://github.com/peschee"><img src="https://avatars.githubusercontent.com/u/63866?v=4&s=48" width="48" height="48" alt="peschee" title="peschee"/></a> <a href="https://github.com/davidiach"><img src="https://avatars.githubusercontent.com/u/28102235?v=4&s=48" width="48" height="48" alt="davidiach" title="davidiach"/></a>
  <a href="https://github.com/nonggialiang"><img src="https://avatars.githubusercontent.com/u/14367839?v=4&s=48" width="48" height="48" alt="nonggialiang" title="nonggialiang"/></a> <a href="https://github.com/rafaelreis-r"><img src="https://avatars.githubusercontent.com/u/57492577?v=4&s=48" width="48" height="48" alt="rafaelreis-r" title="rafaelreis-r"/></a> <a href="https://github.com/dominicnunez"><img src="https://avatars.githubusercontent.com/u/43616264?v=4&s=48" width="48" height="48" alt="dominicnunez" title="dominicnunez"/></a> <a href="https://github.com/lploc94"><img src="https://avatars.githubusercontent.com/u/28453843?v=4&s=48" width="48" height="48" alt="lploc94" title="lploc94"/></a> <a href="https://github.com/ratulsarna"><img src="https://avatars.githubusercontent.com/u/105903728?v=4&s=48" width="48" height="48" alt="ratulsarna" title="ratulsarna"/></a> <a href="https://github.com/sfo2001"><img src="https://avatars.githubusercontent.com/u/103369858?v=4&s=48" width="48" height="48" alt="sfo2001" title="sfo2001"/></a> <a href="https://github.com/lutr0"><img src="https://avatars.githubusercontent.com/u/76906369?v=4&s=48" width="48" height="48" alt="lutr0" title="lutr0"/></a> <a href="https://github.com/kiranjd"><img src="https://avatars.githubusercontent.com/u/25822851?v=4&s=48" width="48" height="48" alt="kiranjd" title="kiranjd"/></a> <a href="https://github.com/danielz1z"><img src="https://avatars.githubusercontent.com/u/235270390?v=4&s=48" width="48" height="48" alt="danielz1z" title="danielz1z"/></a> <a href="https://github.com/Iranb"><img src="https://avatars.githubusercontent.com/u/49674669?v=4&s=48" width="48" height="48" alt="Iranb" title="Iranb"/></a>
  <a href="https://github.com/AdeboyeDN"><img src="https://avatars.githubusercontent.com/u/65312338?v=4&s=48" width="48" height="48" alt="AdeboyeDN" title="AdeboyeDN"/></a> <a href="https://github.com/Alg0rix"><img src="https://avatars.githubusercontent.com/u/53804949?v=4&s=48" width="48" height="48" alt="Alg0rix" title="Alg0rix"/></a> <a href="https://github.com/obviyus"><img src="https://avatars.githubusercontent.com/u/22031114?v=4&s=48" width="48" height="48" alt="obviyus" title="obviyus"/></a> <a href="https://github.com/papago2355"><img src="https://avatars.githubusercontent.com/u/68721273?v=4&s=48" width="48" height="48" alt="papago2355" title="papago2355"/></a> <a href="https://github.com/emanuelst"><img src="https://avatars.githubusercontent.com/u/9994339?v=4&s=48" width="48" height="48" alt="emanuelst" title="emanuelst"/></a> <a href="https://github.com/evanotero"><img src="https://avatars.githubusercontent.com/u/13204105?v=4&s=48" width="48" height="48" alt="evanotero" title="evanotero"/></a> <a href="https://github.com/KristijanJovanovski"><img src="https://avatars.githubusercontent.com/u/8942284?v=4&s=48" width="48" height="48" alt="KristijanJovanovski" title="KristijanJovanovski"/></a> <a href="https://github.com/jlowin"><img src="https://avatars.githubusercontent.com/u/153965?v=4&s=48" width="48" height="48" alt="jlowin" title="jlowin"/></a> <a href="https://github.com/rdev"><img src="https://avatars.githubusercontent.com/u/8418866?v=4&s=48" width="48" height="48" alt="rdev" title="rdev"/></a> <a href="https://github.com/rhuanssauro"><img src="https://avatars.githubusercontent.com/u/164682191?v=4&s=48" width="48" height="48" alt="rhuanssauro" title="rhuanssauro"/></a>
  <a href="https://github.com/joshrad-dev"><img src="https://avatars.githubusercontent.com/u/62785552?v=4&s=48" width="48" height="48" alt="joshrad-dev" title="joshrad-dev"/></a> <a href="https://github.com/osolmaz"><img src="https://avatars.githubusercontent.com/u/2453968?v=4&s=48" width="48" height="48" alt="osolmaz" title="osolmaz"/></a> <a href="https://github.com/adityashaw2"><img src="https://avatars.githubusercontent.com/u/41204444?v=4&s=48" width="48" height="48" alt="adityashaw2" title="adityashaw2"/></a> <a href="https://github.com/CashWilliams"><img src="https://avatars.githubusercontent.com/u/613573?v=4&s=48" width="48" height="48" alt="CashWilliams" title="CashWilliams"/></a> <a href="https://github.com/search?q=sheeek"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="sheeek" title="sheeek"/></a> <a href="https://github.com/ryancontent"><img src="https://avatars.githubusercontent.com/u/39743613?v=4&s=48" width="48" height="48" alt="ryancontent" title="ryancontent"/></a> <a href="https://github.com/jasonsschin"><img src="https://avatars.githubusercontent.com/u/1456889?v=4&s=48" width="48" height="48" alt="jasonsschin" title="jasonsschin"/></a> <a href="https://github.com/artuskg"><img src="https://avatars.githubusercontent.com/u/11966157?v=4&s=48" width="48" height="48" alt="artuskg" title="artuskg"/></a> <a href="https://github.com/onutc"><img src="https://avatars.githubusercontent.com/u/152018508?v=4&s=48" width="48" height="48" alt="onutc" title="onutc"/></a> <a href="https://github.com/pauloportella"><img src="https://avatars.githubusercontent.com/u/22947229?v=4&s=48" width="48" height="48" alt="pauloportella" title="pauloportella"/></a>
  <a href="https://github.com/HirokiKobayashi-R"><img src="https://avatars.githubusercontent.com/u/37167840?v=4&s=48" width="48" height="48" alt="HirokiKobayashi-R" title="HirokiKobayashi-R"/></a> <a href="https://github.com/ThanhNguyxn"><img src="https://avatars.githubusercontent.com/u/74597207?v=4&s=48" width="48" height="48" alt="ThanhNguyxn" title="ThanhNguyxn"/></a> <a href="https://github.com/kimitaka"><img src="https://avatars.githubusercontent.com/u/167225?v=4&s=48" width="48" height="48" alt="kimitaka" title="kimitaka"/></a> <a href="https://github.com/yuting0624"><img src="https://avatars.githubusercontent.com/u/32728916?v=4&s=48" width="48" height="48" alt="yuting0624" title="yuting0624"/></a> <a href="https://github.com/neooriginal"><img src="https://avatars.githubusercontent.com/u/54811660?v=4&s=48" width="48" height="48" alt="neooriginal" title="neooriginal"/></a> <a href="https://github.com/ManuelHettich"><img src="https://avatars.githubusercontent.com/u/17690367?v=4&s=48" width="48" height="48" alt="manuelhettich" title="manuelhettich"/></a> <a href="https://github.com/minghinmatthewlam"><img src="https://avatars.githubusercontent.com/u/14224566?v=4&s=48" width="48" height="48" alt="minghinmatthewlam" title="minghinmatthewlam"/></a> <a href="https://github.com/baccula"><img src="https://avatars.githubusercontent.com/u/22080883?v=4&s=48" width="48" height="48" alt="baccula" title="baccula"/></a> <a href="https://github.com/manikv12"><img src="https://avatars.githubusercontent.com/u/49544491?v=4&s=48" width="48" height="48" alt="manikv12" title="manikv12"/></a> <a href="https://github.com/myfunc"><img src="https://avatars.githubusercontent.com/u/19294627?v=4&s=48" width="48" height="48" alt="myfunc" title="myfunc"/></a>
  <a href="https://github.com/travisirby"><img src="https://avatars.githubusercontent.com/u/5958376?v=4&s=48" width="48" height="48" alt="travisirby" title="travisirby"/></a> <a href="https://github.com/buddyh"><img src="https://avatars.githubusercontent.com/u/31752869?v=4&s=48" width="48" height="48" alt="buddyh" title="buddyh"/></a> <a href="https://github.com/connorshea"><img src="https://avatars.githubusercontent.com/u/2977353?v=4&s=48" width="48" height="48" alt="connorshea" title="connorshea"/></a> <a href="https://github.com/bjesuiter"><img src="https://avatars.githubusercontent.com/u/2365676?v=4&s=48" width="48" height="48" alt="bjesuiter" title="bjesuiter"/></a> <a href="https://github.com/kyleok"><img src="https://avatars.githubusercontent.com/u/58307870?v=4&s=48" width="48" height="48" alt="kyleok" title="kyleok"/></a> <a href="https://github.com/mcinteerj"><img src="https://avatars.githubusercontent.com/u/3613653?v=4&s=48" width="48" height="48" alt="mcinteerj" title="mcinteerj"/></a> <a href="https://github.com/badlogic"><img src="https://avatars.githubusercontent.com/u/514052?v=4&s=48" width="48" height="48" alt="badlogic" title="badlogic"/></a> <a href="https://github.com/apps/dependabot"><img src="https://avatars.githubusercontent.com/in/29110?v=4&s=48" width="48" height="48" alt="dependabot[bot]" title="dependabot[bot]"/></a> <a href="https://github.com/amitbiswal007"><img src="https://avatars.githubusercontent.com/u/108086198?v=4&s=48" width="48" height="48" alt="amitbiswal007" title="amitbiswal007"/></a> <a href="https://github.com/John-Rood"><img src="https://avatars.githubusercontent.com/u/62669593?v=4&s=48" width="48" height="48" alt="John-Rood" title="John-Rood"/></a>
  <a href="https://github.com/timkrase"><img src="https://avatars.githubusercontent.com/u/38947626?v=4&s=48" width="48" height="48" alt="timkrase" title="timkrase"/></a> <a href="https://github.com/uos-status"><img src="https://avatars.githubusercontent.com/u/255712580?v=4&s=48" width="48" height="48" alt="uos-status" title="uos-status"/></a> <a href="https://github.com/gerardward2007"><img src="https://avatars.githubusercontent.com/u/3002155?v=4&s=48" width="48" height="48" alt="gerardward2007" title="gerardward2007"/></a> <a href="https://github.com/roshanasingh4"><img src="https://avatars.githubusercontent.com/u/88576930?v=4&s=48" width="48" height="48" alt="roshanasingh4" title="roshanasingh4"/></a> <a href="https://github.com/tosh-hamburg"><img src="https://avatars.githubusercontent.com/u/58424326?v=4&s=48" width="48" height="48" alt="tosh-hamburg" title="tosh-hamburg"/></a> <a href="https://github.com/azade-c"><img src="https://avatars.githubusercontent.com/u/252790079?v=4&s=48" width="48" height="48" alt="azade-c" title="azade-c"/></a> <a href="https://github.com/dlauer"><img src="https://avatars.githubusercontent.com/u/757041?v=4&s=48" width="48" height="48" alt="dlauer" title="dlauer"/></a> <a href="https://github.com/JonUleis"><img src="https://avatars.githubusercontent.com/u/7644941?v=4&s=48" width="48" height="48" alt="JonUleis" title="JonUleis"/></a> <a href="https://github.com/shivamraut101"><img src="https://avatars.githubusercontent.com/u/110457469?v=4&s=48" width="48" height="48" alt="shivamraut101" title="shivamraut101"/></a> <a href="https://github.com/cheeeee"><img src="https://avatars.githubusercontent.com/u/21245729?v=4&s=48" width="48" height="48" alt="cheeeee" title="cheeeee"/></a>
  <a href="https://github.com/robbyczgw-cla"><img src="https://avatars.githubusercontent.com/u/239660374?v=4&s=48" width="48" height="48" alt="robbyczgw-cla" title="robbyczgw-cla"/></a> <a href="https://github.com/YuriNachos"><img src="https://avatars.githubusercontent.com/u/19365375?v=4&s=48" width="48" height="48" alt="YuriNachos" title="YuriNachos"/></a> <a href="https://github.com/j1philli"><img src="https://avatars.githubusercontent.com/u/3744255?v=4&s=48" width="48" height="48" alt="Josh Phillips" title="Josh Phillips"/></a> <a href="https://github.com/Wangnov"><img src="https://avatars.githubusercontent.com/u/48670012?v=4&s=48" width="48" height="48" alt="Wangnov" title="Wangnov"/></a> <a href="https://github.com/kaizen403"><img src="https://avatars.githubusercontent.com/u/134706404?v=4&s=48" width="48" height="48" alt="kaizen403" title="kaizen403"/></a> <a href="https://github.com/pookNast"><img src="https://avatars.githubusercontent.com/u/14242552?v=4&s=48" width="48" height="48" alt="pookNast" title="pookNast"/></a> <a href="https://github.com/Whoaa512"><img src="https://avatars.githubusercontent.com/u/1581943?v=4&s=48" width="48" height="48" alt="Whoaa512" title="Whoaa512"/></a> <a href="https://github.com/chriseidhof"><img src="https://avatars.githubusercontent.com/u/5382?v=4&s=48" width="48" height="48" alt="chriseidhof" title="chriseidhof"/></a> <a href="https://github.com/ngutman"><img src="https://avatars.githubusercontent.com/u/1540134?v=4&s=48" width="48" height="48" alt="ngutman" title="ngutman"/></a> <a href="https://github.com/ysqander"><img src="https://avatars.githubusercontent.com/u/80843820?v=4&s=48" width="48" height="48" alt="ysqander" title="ysqander"/></a>
  <a href="https://github.com/search?q=mac%20mimi"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="mac mimi" title="mac mimi"/></a> <a href="https://github.com/martinpucik"><img src="https://avatars.githubusercontent.com/u/5503097?v=4&s=48" width="48" height="48" alt="martinpucik" title="martinpucik"/></a> <a href="https://github.com/search?q=Matt%20mini"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Matt mini" title="Matt mini"/></a> <a href="https://github.com/mertcicekci0"><img src="https://avatars.githubusercontent.com/u/179321902?v=4&s=48" width="48" height="48" alt="mertcicekci0" title="mertcicekci0"/></a> <a href="https://github.com/search?q=Miles"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Miles" title="Miles"/></a> <a href="https://github.com/mrdbstn"><img src="https://avatars.githubusercontent.com/u/58957632?v=4&s=48" width="48" height="48" alt="mrdbstn" title="mrdbstn"/></a> <a href="https://github.com/MSch"><img src="https://avatars.githubusercontent.com/u/7475?v=4&s=48" width="48" height="48" alt="MSch" title="MSch"/></a> <a href="https://github.com/mudrii"><img src="https://avatars.githubusercontent.com/u/220262?v=4&s=48" width="48" height="48" alt="mudrii" title="mudrii"/></a> <a href="https://github.com/search?q=Mustafa%20Tag%20Eldeen"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Mustafa Tag Eldeen" title="Mustafa Tag Eldeen"/></a> <a href="https://github.com/mylukin"><img src="https://avatars.githubusercontent.com/u/1021019?v=4&s=48" width="48" height="48" alt="mylukin" title="mylukin"/></a>
  <a href="https://github.com/nathanbosse"><img src="https://avatars.githubusercontent.com/u/4040669?v=4&s=48" width="48" height="48" alt="nathanbosse" title="nathanbosse"/></a> <a href="https://github.com/ndraiman"><img src="https://avatars.githubusercontent.com/u/12609607?v=4&s=48" width="48" height="48" alt="ndraiman" title="ndraiman"/></a> <a href="https://github.com/nexty5870"><img src="https://avatars.githubusercontent.com/u/3869659?v=4&s=48" width="48" height="48" alt="nexty5870" title="nexty5870"/></a> <a href="https://github.com/Noctivoro"><img src="https://avatars.githubusercontent.com/u/183974570?v=4&s=48" width="48" height="48" alt="Noctivoro" title="Noctivoro"/></a> <a href="https://github.com/ozgur-polat"><img src="https://avatars.githubusercontent.com/u/26483942?v=4&s=48" width="48" height="48" alt="ozgur-polat" title="ozgur-polat"/></a> <a href="https://github.com/ppamment"><img src="https://avatars.githubusercontent.com/u/2122919?v=4&s=48" width="48" height="48" alt="ppamment" title="ppamment"/></a> <a href="https://github.com/prathamdby"><img src="https://avatars.githubusercontent.com/u/134331217?v=4&s=48" width="48" height="48" alt="prathamdby" title="prathamdby"/></a> <a href="https://github.com/ptn1411"><img src="https://avatars.githubusercontent.com/u/57529765?v=4&s=48" width="48" height="48" alt="ptn1411" title="ptn1411"/></a> <a href="https://github.com/reeltimeapps"><img src="https://avatars.githubusercontent.com/u/637338?v=4&s=48" width="48" height="48" alt="reeltimeapps" title="reeltimeapps"/></a> <a href="https://github.com/RLTCmpe"><img src="https://avatars.githubusercontent.com/u/10762242?v=4&s=48" width="48" height="48" alt="RLTCmpe" title="RLTCmpe"/></a>
  <a href="https://github.com/search?q=Rony%20Kelner"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Rony Kelner" title="Rony Kelner"/></a> <a href="https://github.com/ryancnelson"><img src="https://avatars.githubusercontent.com/u/347171?v=4&s=48" width="48" height="48" alt="ryancnelson" title="ryancnelson"/></a> <a href="https://github.com/search?q=Samrat%20Jha"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Samrat Jha" title="Samrat Jha"/></a> <a href="https://github.com/senoldogann"><img src="https://avatars.githubusercontent.com/u/45736551?v=4&s=48" width="48" height="48" alt="senoldogann" title="senoldogann"/></a> <a href="https://github.com/Seredeep"><img src="https://avatars.githubusercontent.com/u/22802816?v=4&s=48" width="48" height="48" alt="Seredeep" title="Seredeep"/></a> <a href="https://github.com/sergical"><img src="https://avatars.githubusercontent.com/u/3760543?v=4&s=48" width="48" height="48" alt="sergical" title="sergical"/></a> <a href="https://github.com/shiv19"><img src="https://avatars.githubusercontent.com/u/9407019?v=4&s=48" width="48" height="48" alt="shiv19" title="shiv19"/></a> <a href="https://github.com/shiyuanhai"><img src="https://avatars.githubusercontent.com/u/1187370?v=4&s=48" width="48" height="48" alt="shiyuanhai" title="shiyuanhai"/></a> <a href="https://github.com/siraht"><img src="https://avatars.githubusercontent.com/u/73152895?v=4&s=48" width="48" height="48" alt="siraht" title="siraht"/></a> <a href="https://github.com/snopoke"><img src="https://avatars.githubusercontent.com/u/249606?v=4&s=48" width="48" height="48" alt="snopoke" title="snopoke"/></a>
  <a href="https://github.com/stephenchen2025"><img src="https://avatars.githubusercontent.com/u/218387130?v=4&s=48" width="48" height="48" alt="stephenchen2025" title="stephenchen2025"/></a> <a href="https://github.com/search?q=techboss"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="techboss" title="techboss"/></a> <a href="https://github.com/testingabc321"><img src="https://avatars.githubusercontent.com/u/8577388?v=4&s=48" width="48" height="48" alt="testingabc321" title="testingabc321"/></a> <a href="https://github.com/search?q=The%20Admiral"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="The Admiral" title="The Admiral"/></a> <a href="https://github.com/thesash"><img src="https://avatars.githubusercontent.com/u/1166151?v=4&s=48" width="48" height="48" alt="thesash" title="thesash"/></a> <a href="https://github.com/search?q=Vibe%20Kanban"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Vibe Kanban" title="Vibe Kanban"/></a> <a href="https://github.com/voidserf"><img src="https://avatars.githubusercontent.com/u/477673?v=4&s=48" width="48" height="48" alt="voidserf" title="voidserf"/></a> <a href="https://github.com/search?q=Vultr-Clawd%20Admin"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Vultr-Clawd Admin" title="Vultr-Clawd Admin"/></a> <a href="https://github.com/search?q=Wimmie"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Wimmie" title="Wimmie"/></a> <a href="https://github.com/search?q=wolfred"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="wolfred" title="wolfred"/></a>
  <a href="https://github.com/wstock"><img src="https://avatars.githubusercontent.com/u/1394687?v=4&s=48" width="48" height="48" alt="wstock" title="wstock"/></a> <a href="https://github.com/wytheme"><img src="https://avatars.githubusercontent.com/u/5009358?v=4&s=48" width="48" height="48" alt="wytheme" title="wytheme"/></a> <a href="https://github.com/YangHuang2280"><img src="https://avatars.githubusercontent.com/u/201681634?v=4&s=48" width="48" height="48" alt="YangHuang2280" title="YangHuang2280"/></a> <a href="https://github.com/yazinsai"><img src="https://avatars.githubusercontent.com/u/1846034?v=4&s=48" width="48" height="48" alt="yazinsai" title="yazinsai"/></a> <a href="https://github.com/yevhen"><img src="https://avatars.githubusercontent.com/u/107726?v=4&s=48" width="48" height="48" alt="yevhen" title="yevhen"/></a> <a href="https://github.com/YiWang24"><img src="https://avatars.githubusercontent.com/u/176262341?v=4&s=48" width="48" height="48" alt="YiWang24" title="YiWang24"/></a> <a href="https://github.com/search?q=ymat19"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="ymat19" title="ymat19"/></a> <a href="https://github.com/search?q=Zach%20Knickerbocker"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Zach Knickerbocker" title="Zach Knickerbocker"/></a> <a href="https://github.com/zackerthescar"><img src="https://avatars.githubusercontent.com/u/38077284?v=4&s=48" width="48" height="48" alt="zackerthescar" title="zackerthescar"/></a> <a href="https://github.com/0xJonHoldsCrypto"><img src="https://avatars.githubusercontent.com/u/81202085?v=4&s=48" width="48" height="48" alt="0xJonHoldsCrypto" title="0xJonHoldsCrypto"/></a>
  <a href="https://github.com/aaronn"><img src="https://avatars.githubusercontent.com/u/1653630?v=4&s=48" width="48" height="48" alt="aaronn" title="aaronn"/></a> <a href="https://github.com/Alphonse-arianee"><img src="https://avatars.githubusercontent.com/u/254457365?v=4&s=48" width="48" height="48" alt="Alphonse-arianee" title="Alphonse-arianee"/></a> <a href="https://github.com/atalovesyou"><img src="https://avatars.githubusercontent.com/u/3534502?v=4&s=48" width="48" height="48" alt="atalovesyou" title="atalovesyou"/></a> <a href="https://github.com/search?q=Azade"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Azade" title="Azade"/></a> <a href="https://github.com/carlulsoe"><img src="https://avatars.githubusercontent.com/u/34673973?v=4&s=48" width="48" height="48" alt="carlulsoe" title="carlulsoe"/></a> <a href="https://github.com/search?q=ddyo"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="ddyo" title="ddyo"/></a> <a href="https://github.com/search?q=Erik"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Erik" title="Erik"/></a> <a href="https://github.com/jiulingyun"><img src="https://avatars.githubusercontent.com/u/126459548?v=4&s=48" width="48" height="48" alt="jiulingyun" title="jiulingyun"/></a> <a href="https://github.com/latitudeki5223"><img src="https://avatars.githubusercontent.com/u/119656367?v=4&s=48" width="48" height="48" alt="latitudeki5223" title="latitudeki5223"/></a> <a href="https://github.com/search?q=Manuel%20Maly"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Manuel Maly" title="Manuel Maly"/></a>
  <a href="https://github.com/search?q=Mourad%20Boustani"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Mourad Boustani" title="Mourad Boustani"/></a> <a href="https://github.com/odrobnik"><img src="https://avatars.githubusercontent.com/u/333270?v=4&s=48" width="48" height="48" alt="odrobnik" title="odrobnik"/></a> <a href="https://github.com/pcty-nextgen-ios-builder"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="pcty-nextgen-ios-builder" title="pcty-nextgen-ios-builder"/></a> <a href="https://github.com/search?q=Quentin"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Quentin" title="Quentin"/></a> <a href="https://github.com/search?q=Randy%20Torres"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Randy Torres" title="Randy Torres"/></a> <a href="https://github.com/rhjoh"><img src="https://avatars.githubusercontent.com/u/105699450?v=4&s=48" width="48" height="48" alt="rhjoh" title="rhjoh"/></a> <a href="https://github.com/search?q=Rolf%20Fredheim"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="Rolf Fredheim" title="Rolf Fredheim"/></a> <a href="https://github.com/ronak-guliani"><img src="https://avatars.githubusercontent.com/u/23518228?v=4&s=48" width="48" height="48" alt="ronak-guliani" title="ronak-guliani"/></a> <a href="https://github.com/search?q=William%20Stock"><img src="assets/avatar-placeholder.svg" width="48" height="48" alt="William Stock" title="William Stock"/></a>
</p>
