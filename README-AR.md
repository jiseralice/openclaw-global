# 🦞 OpenClaw — مساعد الذكاء الاصطناعي الشخصي

<p align="center">
    <picture>
        <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/openclaw/openclaw/main/docs/assets/openclaw-logo-text-dark.png">
        <img src="https://raw.githubusercontent.com/openclaw/openclaw/main/docs/assets/openclaw-logo-text.png" alt="OpenClaw" width="500">
    </picture>
</p>

<p align="center">
  <strong>التحول! التحول!</strong>
</p>

<p align="center">
  <a href="https://github.com/openclaw/openclaw/actions/workflows/ci.yml?branch=main"><img src="https://img.shields.io/github/actions/workflow/status/openclaw/openclaw/ci.yml?branch=main&style=for-the-badge" alt="حالة CI"></a>
  <a href="https://github.com/openclaw/openclaw/releases"><img src="https://img.shields.io/github/v/release/openclaw/openclaw?include_prereleases&style=for-the-badge" alt="إصدار GitHub"></a>
  <a href="https://discord.gg/clawd"><img src="https://img.shields.io/discord/1456350064065904867?label=Discord&logo=discord&logoColor=white&color=5865F2&style=for-the-badge" alt="Discord"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge" alt="ترخيص MIT"></a>
</p>

**OpenClaw** هو مساعد ذكاء اصطناعي شخصي يعمل على أجهزتك الخاصة. يوفر الدعم من خلال القنوات الشائعة (WhatsApp و Telegram و Slack و Discord و Google Chat و Signal و iMessage و Microsoft Teams و WebChat) وكذلك من خلال قنوات ممتدة مثل BlueBubbles و Matrix و Zalo و Zalo Personal. وهو متوافق مع macOS/iOS/Android ويمكنه عرض واجهات Canvas في الوقت الفعلي تتحكم بها أنت. لا تعد بوابة الوصول سوى منصة تحكم، بل المنتج نفسه هو المساعد الحقيقي.
إذا كنت تبحث عن مساعد محلي وسريع ومتصل دائمًا لمستخدم واحد، فهو الخيار الأمثل.

[الموقع الرسمي](https://openclaw.ai) · [التوثيق الرسمي](https://docs.openclaw.ai) · [ديب ويكي](https://deepwiki.com/openclaw/openclaw) · [دليل البدء](https://docs.openclaw.ai/start/getting-started) · [التحديثات](https://docs.openclaw.ai/install/updating) · [العروض](https://docs.openclaw.ai/start/showcase) · [الأسئلة الشائعة](https://docs.openclaw.ai/start/faq) · [المساعد](https://docs.openclaw.ai/start/wizard) · [Nix](https://github.com/openclaw/nix-clawdbot) · [Docker](https://docs.openclaw.ai/install/docker) · [Discord](https://discord.gg/clawd)

الإعداد الموصى به: قم بتشغيل مساعد الإعداد (`openclaw onboard`). سيوجهك هذا عبر إعدادات البوابة ومنطقة العمل والقنوات والمهارات. يعد مساعد سطر الأوامر هو المسار الموصى به ويعمل على **macOS و Linux و Windows (عبر WSL2 ؛ يُوصى به بشدة)**.
يدعم npm أو pnpm أو bun. هل هذه تثبيت جديد؟ ابدأ من هنا: [دليل البدء](https://docs.openclaw.ai/start/getting-started)

**الاشتراك (OAuth):**

- **[Anthropic](https://www.anthropic.com/)** (Claude Pro/Max)
- **[OpenAI](https://openai.com/)** (ChatGPT/Codex)

ملاحظات حول النماذج: على الرغم من دعم جميع النماذج، فإنني أوصي بشدة باستخدام **Anthropic Pro/Max (100/200) + Opus 4.6** للحصول على أداء أفضل على المدى الطويل ومقاومة أفضل للتداخل. راجع [الدليل عبر الإنترنت](https://docs.openclaw.ai/start/onboarding).

## النماذج (الاختيار + المصادقة)

- تكوين النموذج + CLI: [النماذج](https://docs.openclaw.ai/concepts/models)
- ملفات تعريف المصادقة (OAuth مقابل مفاتيح API) + الاسترداد الاحتياطي: [استرداد النموذج](https://docs.openclaw.ai/concepts/model-failover)

## التثبيت

بيئة التشغيل: **Node ≥22**.

```bash
npm install -g openclaw@latest
# أو: pnpm add -g openclaw@latest

openclaw onboard --install-daemon
```

يقوم المساعد بتثبيت خدمة البوابة (خدمة المستخدم launchd/systemd) للحفاظ على تشغيلها.

## البدء السريع (الملخص)

بيئة التشغيل: **Node ≥22**.

الدليل الكامل للمبتدئين (المصادقة، والاقتران، والقنوات): [البدء](https://docs.openclaw.ai/start/getting-started)

```bash
openclaw onboard --install-daemon

openclaw gateway --port 18789 --verbose

# إرسال رسالة
openclaw message send --to +1234567890 --message "مرحبًا من OpenClaw"

# الدردشة مع المساعد (يمكنك إرسال أي رسالة إلى القنوات المتصلة: WhatsApp/Telegram/Slack/Discord/Google Chat/Signal/iMessage/BlueBubbles/Microsoft Teams/Matrix/Zalo/Zalo Personal/WebChat)
openclaw agent --message "قائمة تفتيش السفينة" --thinking high
```

كيفية التحديث؟ [دليل التحديث](https://docs.openclaw.ai/install/updating) (قم بتشغيل `openclaw doctor`).

## شرح حالة إصدار التطوير

- **stable**: إصدارات موسومة (`vYYYY.M.D` أو `vYYYY.M.D-<patch>`)، npm dist-tag `latest`.
- **beta**: إصدارات ما قبل الإطلاق (`vYYYY.M.D-beta.N`)، npm dist-tag `beta` (قد يكون تطبيق macOS مفقودًا).
- **dev**: تطور مستمر لـ `main`، npm dist-tag `dev` (عند النشر).

التبديل (git + npm): `openclaw update --channel stable|beta|dev`.
التفاصيل: [حالة إصدار التطوير](https://docs.openclaw.ai/install/development-channels).

## المصدر (التطوير)

يُوصى باستخدام `pnpm` للبناء من المصدر. Bun اختياري لتشغيل TypeScript مباشرة.

```bash
git clone https://github.com/openclaw/openclaw.git
cd openclaw

pnpm install
pnpm ui:build # يقوم بتثبيت تبعيات واجهة المستخدم تلقائيًا عند التشغيل الأول
pnpm build

pnpm openclaw onboard --install-daemon

# حلقة التطوير (إعادة التحميل التلقائي عند تغيير TS)
pnpm gateway:watch
```

ملاحظة: `pnpm openclaw ...` يقوم بتشغيل TypeScript مباشرة (من خلال `tsx`). `pnpm build` يولد `dist/` لتشغيل/تجميع ثنائي `openclaw` عبر Node.

## إعدادات الأمان الافتراضية (أذونات DM)

يتصل OpenClaw بمنصات المراسلة الفورية الحقيقية. اعتبر الرسائل المباشرة المستلمة **مدخلات غير موثوقة**.

الدليل الشامل للأمان: [دليل الأمان](https://docs.openclaw.ai/gateway/security)

السلوك الافتراضي لـ Telegram/WhatsApp/Signal/iMessage/Microsoft Teams/Discord/Google Chat/Slack:

- **اقتران DM** (`dmPolicy="pairing"` / `channels.discord.dm.policy="pairing"` / `channels.slack.dm.policy="pairing"`): يتلقى المرسلون غير المعروفون رمز اقتران قصير، ولا يعالج الروبوت رسائلهم.
- الموافقة: `openclaw pairing approve <channel> <code>` (ثم يضيف المرسل إلى التخزين المحلي).
- تتطلب الرسائل المباشرة العامة المستلمة موافقة صريحة: قم بتعيين `dmPolicy="open"` وقم بتضمين `"*"` في قائمة السماح بالقناة (`allowFrom` / `channels.discord.dm.allowFrom` / `channels.slack.dm.allowFrom`).

قم بتشغيل `openclaw doctor` لاكتشاف سياسات DM عالية المخاطر/السيئة التكوين.

## النقاط الأساسية

- **[البوابة المحلية المفضلة](https://docs.openclaw.ai/gateway)** — مستوى التحكم الوحيد للجلسات والقنوات والأدوات والأحداث.
- **[صندوق الوارد متعدد القنوات](https://docs.openclaw.ai/channels)** — WhatsApp و Telegram و Slack و Discord و Google Chat و Signal و BlueBubbles (iMessage) و iMessage (قديم) و Microsoft Teams و Matrix و Zalo و Zalo Personal و WebChat و macOS و iOS/Android.
- **[التوجيه متعدد الوكلاء](https://docs.openclaw.ai/gateway/configuration)** — توجيه القنوات/الحسابات/الأقران الداخلة إلى وكلاء معزولين (منطقة عمل + جلسة لكل وكيل).
- **[تنبيه الصوت](https://docs.openclaw.ai/nodes/voicewake) + [وضع المحادثة](https://docs.openclaw.ai/nodes/talk)** — ميزة الصوت الدائم من ElevenLabs لـ macOS/iOS/Android.
- **[Canvas مباشر](https://docs.openclaw.ai/platforms/mac/canvas)** — مساحة عمل مرئية تعتمد على الوكيل باستخدام [A2UI](https://docs.openclaw.ai/platforms/mac/canvas#canvas-a2ui).
- **[أدوات ممتازة](https://docs.openclaw.ai/tools)** — المتصفح وCanvas والعقد ومهمات cron والجلسات وإجراءات Discord/Slack.
- **[تطبيقات مرافقة](https://docs.openclaw.ai/platforms/macos)** — تطبيق شريط القوائم macOS + [العقد](https://docs.openclaw.ai/nodes) iOS/Android.
- **[المساعد](https://docs.openclaw.ai/start/wizard) + [المهارات](https://docs.openclaw.ai/tools/skills)** — إعداد موجه مع المهارات المجمعة/المدارة/منطقة العمل.

## تاريخ النجوم

[![مخطط تاريخ النجوم](https://api.star-history.com/svg?repos=openclaw/openclaw&type=date&legend=top-left)](https://www.star-history.com/#openclaw/openclaw&type=date&legend=top-left)

## ما قمنا به حتى الآن

### المنصة الأساسية

- [لوحة التحكم في البوابة](https://docs.openclaw.ai/gateway) بما في ذلك الجلسات والحالة والتكوين ومهمات cron و webhooks، و[واجهة المستخدم التفاعلية](https://docs.openclaw.ai/web) و[مضيف Canvas](https://docs.openclaw.ai/platforms/mac/canvas#canvas-a2ui).
- [واجهة CLI](https://docs.openclaw.ai/tools/agent-send): البوابة، والوكيل، والإرسال، و[المساعد](https://docs.openclaw.ai/start/wizard) و[الأمن](https://docs.openclaw.ai/gateway/doctor).
- [وقت تشغيل وكيل Pi](https://docs.openclaw.ai/concepts/agent) بنمط RPC، ويدعم بث الأدوات والبث المجزأ.
- [نموذج الجلسة](https://docs.openclaw.ai/concepts/session): `main` للدردشة المباشرة، وفصل المجموعة، ووضع التنشيط، ووضع الطابور، والاستجابات. قواعد المجموعة: [المجموعات](https://docs.openclaw.ai/concepts/groups).
- [قنوات الوسائط](https://docs.openclaw.ai/nodes/images): الصور/الصوت/الفيديو، وخطافات النسخ، وقيود الحجم، ودورة حياة الملفات المؤقتة. تفاصيل الصوت: [الصوت](https://docs.openclaw.ai/nodes/audio).

### القنوات

- [القنوات](https://docs.openclaw.ai/channels): [WhatsApp](https://docs.openclaw.ai/channels/whatsapp) (Baileys)، [Telegram](https://docs.openclaw.ai/channels/telegram) (grammY)، [Slack](https://docs.openclaw.ai/channels/slack) (Bolt)، [Discord](https://docs.openclaw.ai/channels/discord) (discord.js)، [Google Chat](https://docs.openclaw.ai/channels/googlechat) (API المحادثة)، [Signal](https://docs.openclaw.ai/channels/signal) (signal-cli)، [BlueBubbles](https://docs.openclaw.ai/channels/bluebubbles) (iMessage، موصى به)، [iMessage](https://docs.openclaw.ai/channels/imessage) (imsg قديم)، [Microsoft Teams](https://docs.openclaw.ai/channels/msteams) (امتداد)، [Matrix](https://docs.openclaw.ai/channels/matrix) (امتداد)، [Zalo](https://docs.openclaw.ai/channels/zalo) (امتداد)، [Zalo Personal](https://docs.openclaw.ai/channels/zalouser) (امتداد)، [WebChat](https://docs.openclaw.ai/web/webchat).
- [توجيه المجموعة](https://docs.openclaw.ai/concepts/group-messages): تفعيل الإشارة، وعلامات الرد، والتقطيع والتوجيه حسب القناة. قواعد القناة: [القنوات](https://docs.openclaw.ai/channels).

### التطبيقات + العقد

- [تطبيق macOS](https://docs.openclaw.ai/platforms/macos): لوحة التحكم في شريط القوائم، [تنبيه الصوت](https://docs.openclaw.ai/nodes/voicewake)/PTT، [وضع المحادثة](https://docs.openclaw.ai/nodes/talk) تراكب، [WebChat](https://docs.openclaw.ai/web/webchat)، أدوات التصحيح، [البوابة عن بعد](https://docs.openclaw.ai/gateway/remote) التحكم.
- [العقد iOS](https://docs.openclaw.ai/platforms/ios): [Canvas](https://docs.openclaw.ai/platforms/mac/canvas)، [تنبيه الصوت](https://docs.openclaw.ai/nodes/voicewake)، [وضع المحادثة](https://docs.openclaw.ai/nodes/talk)، الكاميرا، تسجيل الشاشة، الاقتران Bonjour.
- [العقد Android](https://docs.openclaw.ai/platforms/android): [Canvas](https://docs.openclaw.ai/platforms/mac/canvas)، [وضع المحادثة](https://docs.openclaw.ai/nodes/talk)، الكاميرا، تسجيل الشاشة، ميزات الرسائل القصيرة الاختيارية.
- [وضع العقدة macOS](https://docs.openclaw.ai/nodes): تشغيل النظام/الإشعارات + تعرية الكاميرا/Canvas.

### الأدوات + الأتمتة

- [التحكم في المتصفح](https://docs.openclaw.ai/tools/browser): Chrome/Chromium مخصص لـ openclaw، لقطات الشاشة، الإجراءات، التحميلات، الملفات الشخصية.
- [Canvas](https://docs.openclaw.ai/platforms/mac/canvas): [A2UI](https://docs.openclaw.ai/platforms/mac/canvas#canvas-a2ui) دفع/إعادة تعيين، التقييم، لقطات الشاشة.
- [العقد](https://docs.openclaw.ai/nodes): لقطات/تسجيلات الكاميرا، تسجيل الشاشة، [الحصول على الموقع](https://docs.openclaw.ai/nodes/location-command)، الإشعارات
- [مهمات Cron + التنبيه](https://docs.openclaw.ai/automation/cron-jobs); [webhooks](https://docs.openclaw.ai/automation/webhook); [Gmail Pub/Sub](https://docs.openclaw.ai/automation/gmail-pubsub).
- [منصة المهارات](https://docs.openclaw.ai/tools/skills): المهارات المجمعة، والمدارة، ومنطقة العمل مع قيود التثبيت وواجهة المستخدم.

### العمليات + الأمان

- [توجيه القناة](https://docs.openclaw.ai/concepts/channel-routing)، [سياسة إعادة المحاولة](https://docs.openclaw.ai/concepts/retry)، و[البث/التقطيع](https://docs.openclaw.ai/concepts/streaming).
- [الوجود](https://docs.openclaw.ai/concepts/presence)، [مؤشرات الكتابة](https://docs.openclaw.ai/concepts/typing-indicators)، و[تتبع الاستخدام](https://docs.openclaw.ai/concepts/usage-tracking).
- [النماذج](https://docs.openclaw.ai/concepts/models)، [استرداد النموذج](https://docs.openclaw.ai/concepts/model-failover)، و[الجلسات](https://docs.openclaw.ai/concepts/session-pruning).
- [الأمن](https://docs.openclaw.ai/gateway/security) و[استكشاف الأخطاء وإصلاحها](https://docs.openclaw.ai/channels/troubleshooting).

### العمليات + التعبئة

- [واجهة التحكم](https://docs.openclaw.ai/web) + [WebChat](https://docs.openclaw.ai/web/webchat) تُقدم مباشرة من قبل البوابة.
- [Tailscale Serve/Funnel](https://docs.openclaw.ai/gateway/tailscale) أو [أنفاق SSH](https://docs.openclaw.ai/gateway/remote) مع مصادقة رمز/كلمة مرور
- [وضع Nix](https://docs.openclaw.ai/install/nix) يدعم التكوين التصريحي؛ التثبيت القائم على [Docker](https://docs.openclaw.ai/install/docker)
- [الأمن](https://docs.openclaw.ai/gateway/doctor) استرداد أمني، [التسجيل](https://docs.openclaw.ai/logging).

## كيف يعمل (ملخص مبسط)

```
WhatsApp / Telegram / Slack / Discord / Google Chat / Signal / iMessage / BlueBubbles / Microsoft Teams / Matrix / Zalo / Zalo Personal / WebChat
               │
               ▼
┌───────────────────────────────┐
│            Gateway            │
│       (plane of control)      │
│     ws://127.0.0.1:18789      │
└──────────────┬────────────────┘
               │
               ├─ Pi agent (RPC)
               ├─ CLI (openclaw …)
               ├─ WebChat UI
               ├─ macOS app
               └─ iOS / Android nodes
```

## الأنظمة الفرعية الرئيسية

- **[اتصال Gateway WebSocket](https://docs.openclaw.ai/concepts/architecture)** — مستوى تحكم WS وحيد للعملاء والأدوات والأحداث (و العمليات: [دليل Gateway](https://docs.openclaw.ai/gateway)).
- **[تعرض Tailscale](https://docs.openclaw.ai/gateway/tailscale)** — Serve/Funnel + WS ل لوحة تحكم Gateway (الوصول عن بعد: [الوصول عن بعد](https://docs.openclaw.ai/gateway/remote)).
- **[التحكم في المتصفح](https://docs.openclaw.ai/tools/browser)** — Chrome/Chromium المُدار من قبل openclaw مع التحكم بـ CDP.
- **[Canvas + A2UI](https://docs.openclaw.ai/platforms/mac/canvas)** — مساحة عمل بصرية تعتمد على الوكيل (مضيف A2UI: [Canvas/A2UI](https://docs.openclaw.ai/platforms/mac/canvas#canvas-a2ui)).
- **[تنبيه الصوت](https://docs.openclaw.ai/nodes/voicewake) + [وضع المحادثة](https://docs.openclaw.ai/nodes/talk)** — ميزة الصوت دائمًا مفتوحة للمحادثات المستمرة.
- **[العقد](https://docs.openclaw.ai/nodes)** — Canvas، لقطات/تسجيلات الكاميرا، تسجيل الشاشة، `location.get`، الإشعارات، بالإضافة إلى وظائف macOS المحددة `system.run`/`system.notify`.

## الوصول إلى Tailscale (لوحة تحكم Gateway)

يمكن لـ OpenClaw تكوين Tailscale تلقائيًا **Serve** (tailnet فقط) أو **Funnel** (عام) أثناء بقاء Gateway مربوطًا بواجهة loopback. قم بتكوين `gateway.tailscale.mode`:

- `off`: لا توجد أتمتة Tailscale (الافتراضي).
- `serve`: HTTPS tailnet فقط عبر `tailscale serve` (يستخدم رؤوس Tailscale بشكل افتراضي).
- `funnel`: HTTPS عام عبر `tailscale funnel` (يتطلب مصادقة كلمة المرور المشتركة).

الشرح:

- يجب أن يبقى `gateway.bind` كـ `loopback` عند تمكين Serve/Funnel (يفرض OpenClaw هذا).
- فرض كلمة مرور الخادم عن طريق تعيين `gateway.auth.mode: "password"` أو `gateway.auth.allowTailscale: false`.
- رفض التشغيل ما لم يتم تعيين `gateway.auth.mode: "password"` مسبقًا.
- اختياري `gateway.tailscale.resetOnExit` يلغي عمليات Serve/Funnel عند الإيقاف.

التفاصيل: [دليل Tailscale](https://docs.openclaw.ai/gateway/tailscale) · [صفحة الويب](https://docs.openclaw.ai/web)

## Gateway عن بعد (توافق Linux أفضل)

من المقبول تمامًا تشغيل Gateway على مثيل Linux صغير. يمكن للعملاء (تطبيق macOS، CLI، WebChat) الاتصال عبر **Tailscale Serve/Funnel** أو **أنفاق SSH**، ويمكنك لا يزال إقران عقد الأجهزة (macOS/iOS/Android) حسب الحاجة لتنفيذ عمليات محلية على الجهاز.

- **مضيف Gateway** ينفذ الأدوات ويبقي اتصالات القناة مثبتة.
- **عقد الجهاز** تنفذ عمليات محلية على الجهاز عبر `node.invoke`.
  باختصار: التنفيذ يحدث حيث يوجد Gateway؛ تحدث عمليات الجهاز حيث يوجد الجهاز.

التفاصيل: [الوصول عن بعد](https://docs.openclaw.ai/gateway/remote) · [العقد](https://docs.openclaw.ai/nodes) · [الأمن](https://docs.openclaw.ai/gateway/security)

## أذونات macOS عبر بروتوكول Gateway

يمكن لتطبيق macOS العمل في **وضع العقدة** ونشر إمكاناته وخرائط الأذونات عبر WebSocket لـ Gateway (`node.list` / `node.describe`). يمكن للعملاء بعد ذلك تنفيذ العمليات المحلية عبر `node.invoke`:

- `system.run` ينفذ أوامر محلية ويعيد stdout/stderr/رمز الخروج؛ قم بتعيين `needsScreenRecording: true` للحصول على إذن تسجيل الشاشة (وإلا ستحصل على خطأ `PERMISSION_MISSING`).
- `system.notify` يرسل إشعارًا للمستخدم، يفشل إذا تم رفض الإشعار.
- `canvas.*`, `camera.*`, `screen.record`, و `location.get` يتم توجيهها عبر `node.invoke` واتباع حالة إذن TCC.

أذونات bash المرتفعة (أذونات المضيف) و TCC على macOS منفصلة:

- استخدم `/elevated on|off` لتبديل الوصول المرتفع لكل جلسة عند التمكين + الإضافة إلى قائمة السماح.
- يحتفظ Gateway بكل تبديل جلسة عبر (أساليب WS) وكذلك `sessions.patch` و `thinkingLevel` و `verboseLevel` و `model` و `sendPolicy` و `groupActivation`.

التفاصيل: [العقد](https://docs.openclaw.ai/nodes) · [تطبيق macOS](https://docs.openclaw.ai/platforms/macos) · [بروتوكول Gateway](https://docs.openclaw.ai/concepts/architecture)

## وكيل إلى وكيل (أدوات sessions_*)

- تسمح هذه الميزة بتنسيق العمل عبر الجلسات دون التبديل بين واجهات الدردشة.
- `sessions_list` — اكتشاف الجلسات (الوكلاء) النشطة وبياناتها الوصفية.
- `sessions_history` — استرداد سجلات الجلسة المسجلة.
- `sessions_send` — إرسال رسالة إلى جلسة أخرى؛ خطوات الاستجابة الاختيارية بنمط ping-pong + الإعلان (REPLY_SKIP، ANNOUNCE_SKIP).

التفاصيل: [أدوات الجلسة](https://docs.openclaw.ai/concepts/session-tool)

## تسجيل المهارات (ClawHub)

ClawHub هو نظام تسجيل مهارات أدنى حد. بمجرد تمكين ClawHub، يمكن للوكيل البحث عن المهارات تلقائيًا وإضافتها حسب الحاجة.

[ClawHub](https://clawhub.com)

## أوامر الدردشة

أرسل هذه عبر WhatsApp/Telegram/Slack/Google Chat/Microsoft Teams/WebChat (أوامر المجموعة فقط لمديري المجموعة):

- `/status` — حالة الجلسة المختصرة (النموذج + الرموز، والتكاليف عند التوفر)
- `/new` أو `/reset` — إعادة تعيين الجلسة
- `/compact` — سياق الجلسة المختصر (ملخص)
- `/think <level>` — off|minimal|low|medium|high|xhigh (نماذج GPT-5.2 + Codex فقط)
- `/verbose on|off`
- `/usage off|tokens|full` — استخدام الرموز لكل رد
- `/restart` — إعادة تشغيل البوابة (مديري المجموعة فقط)
- `/activation mention|always` — تبديل تنشيط المجموعة (للمجموعات فقط)

## التطبيقات (اختياري)

توفر البوابة نفسها تجربة ممتازة. جميع التطبيقات اختيارية وتضيف وظائف إضافية.

إذا كنت تخطط لبناء/تشغيل تطبيقات مصاحبة، فاتبع أدلة النظام المقابلة.

### macOS (OpenClaw.app) (اختياري)

- عناصر التحكم في شريط القوائم للبوابة والصحة.
- تنبيه الصوت + تراكب المكالمة بنقرة واحدة.
- WebChat + أدوات التصحيح.
- التحكم في البوابة عن بعد عبر SSH.

ملاحظة: يتطلب بنية موقعة حتى تظل أذونات macOS سارية بعد إعادة البناء (انظر `docs/mac/permissions.md`).

### عقدة iOS (اختياري)

- إقران العقدة كجسر للجهاز.
- توجيه مشغل الصوت + سطح Canvas.
- التحكم عبر `openclaw nodes …`.

الدليل: [توصيل iOS](https://docs.openclaw.ai/platforms/ios).

### عقدة Android (اختياري)

- الإقران عبر نفس عملية الجسر + الإقران لـ iOS.
- يسمح بأوامر Canvas والكاميرا وتسجيل الشاشة.
- الدليل: [توصيل Android](https://docs.openclaw.ai/platforms/android).

## مساحة عمل الوكيل + المهارات

- دليل جذر مساحة العمل: `~/.openclaw/workspace` (يمكن تكوينه عبر `agents.defaults.workspace`).
- ملفات المطالبات المحقونة: `AGENTS.md`, `SOUL.md`, `TOOLS.md`.
- المهارات: `~/.openclaw/workspace/skills/<skill>/SKILL.md`.

## التكوين

الحد الأدنى من التكوين `~/.openclaw/openclaw.json` (النموذج + القيم الافتراضية):

```json5
{
  agent: {
    model: "anthropic/claude-opus-4-6",
  },
}
```

[مرجع التكوين الكامل (جميع المفاتيح والأمثلة).](https://docs.openclaw.ai/gateway/configuration)

## وضع الأمان (مهم)

- **افتراضيًا:** تُشغل الأدوات على المضيف كجلسة رئيسية، لذلك عند استخدامك وحدك، يكون للوكيل وصول كامل.
- **الأمان للقنوات/المجموعات:** شغّل كل جلسة كبيئة معزولة داخل Docker مع `agents.defaults.sandbox.mode: "non-main"` كـ **جلسات غير رئيسية** (قنوات/مجموعات)؛ ثم شغّلها كجلسة bash داخل Docker.
- **البيئة المعزولة الافتراضية:** تسمح بتشغيل `bash` و `process` و `read` و `write` و `edit` و `sessions_list` و `sessions_history` و `sessions_send` و `sessions_spawn`؛ تمنع `browser` و `canvas` و `nodes` و `cron` و `discord` و `gateway`.

التفاصيل: [إرشادات الأمان](https://docs.openclaw.ai/gateway/security) · [Docker + بيئة معزولة](https://docs.openclaw.ai/install/docker) · [تكوين البيئة المعزولة](https://docs.openclaw.ai/gateway/configuration)

### [WhatsApp](https://docs.openclaw.ai/channels/whatsapp)

- ربط الجهاز: `pnpm openclaw channels login` (تخزين بيانات الاعتماد في `~/.openclaw/credentials`).
- السماح للمستخدمين المضافين إلى القائمة البيضاء بالدردشة مع المساعد عبر `channels.whatsapp.allowFrom`.
- إذا تم تعيين `channels.whatsapp.groups`، فسيصبح قائمة بيضاء للمجموعات؛ تضمين `"*"` سيسمح لجميع المجموعات.

### [Telegram](https://docs.openclaw.ai/channels/telegram)

- قم بتعيين `TELEGRAM_BOT_TOKEN` أو `channels.telegram.botToken` (تُعطى الأولوية لمتغيرات البيئة).
- اختياري: قم بتعيين `channels.telegram.groups` (مع `channels.telegram.groups."*".requireMention`)؛ بمجرد التعيين، يُنشأ قائمة بيضاء (تضمين `"*"` يسمح للجميع)؛ استخدم `channels.telegram.allowFrom` أو `channels.telegram.webhookUrl` + `channels.telegram.webhookSecret` عند الحاجة.

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

- قم بتعيين `SLACK_BOT_TOKEN` + `SLACK_APP_TOKEN` (أو `channels.slack.botToken` + `channels.slack.appToken`).

### [Discord](https://docs.openclaw.ai/channels/discord)

- قم بتعيين `DISCORD_BOT_TOKEN` أو `channels.discord.token` (تُعطى الأولوية لمتغيرات البيئة).
- اختياري: قم بتعيين `commands.native` أو `commands.text` أو `commands.useAccessGroups`، و `channels.discord.dm.allowFrom` أو `channels.discord.guilds` أو `channels.discord.mediaMaxMb` عند الحاجة.

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

- يتطلب `signal-cli` وتكوين `channels.signal`.

### [BlueBubbles (iMessage)](https://docs.openclaw.ai/channels/bluebubbles)

- **مُوصى به** حل تكامل iMessage
- قم بتكوين `channels.bluebubbles.serverUrl` + `channels.bluebubbles.password` و Webhook (`channels.bluebubbles.webhookPath`).
- يُشغل خادم BlueBubbles على macOS؛ يمكن أن يُشغل البوابة على macOS أو أنظمة أخرى.

### [iMessage (قديم)](https://docs.openclaw.ai/channels/imessage)

- تكامل macOS قديم فقط لـ `imsg` (يجب تسجيل الدخول إلى تطبيق الرسائل).
- إذا تم تعيين `channels.imessage.groups`، فسيصبح قائمة بيضاء؛ تضمين `"*"` سيسمح للجميع.

### [Microsoft Teams](https://docs.openclaw.ai/channels/msteams)

- قم بتكوين تطبيق Teams + Bot Framework، ثم أضف تكوين `msteams`.
- قائمة السماح `msteams.allowFrom`؛ المجموعات عبر `msteams.groupAllowFrom` أو `msteams.groupPolicy: "open"`.

### [WebChat](https://docs.openclaw.ai/web/webchat)

- يستخدم WebSocket للبوابة؛ لا توجد منفذ/تكوين WebChat منفصل.

التحكم في المتصفح (اختياري):

```json5
{
  browser: {
    enabled: true,
    color: "#FF4500",
  },
}
```

## التوثيق

عند انتهائك من عملية الإعداد واحتياجك إلى مراجع أعمق، تكون هذه متاحة.

- [أولاً، راجع فهرس التوثيق للتنقل و"أين يوجد المحتوى".](https://docs.openclaw.ai)
- [اقرأ نظرة عامة على بنية البوابة + نموذج البروتوكول.](https://docs.openclaw.ai/concepts/architecture)
- [استخدم مرجع التكوين الكامل عند احتياجاتك لكل المفاتيح والأمثلة.](https://docs.openclaw.ai/gateway/configuration)
- [اتبع دليل تشغيل البوابة بدقة.](https://docs.openclaw.ai/gateway)
- [افهم كيفية عمل واجهة التحكم/الويب وكيفية عرضها بأمان.](https://docs.openclaw.ai/web)
- [افهم الوصول عن بعد عبر أنفاق SSH أو tailnet.](https://docs.openclaw.ai/gateway/remote)
- [اتبع عملية الإعداد الموجهة.](https://docs.openclaw.ai/start/wizard)
- [اتصل بمشغلات خارجية عبر واجهة webhook.](https://docs.openclaw.ai/automation/webhook)
- [قم بتكوين مشغلات Gmail Pub/Sub.](https://docs.openclaw.ai/automation/gmail-pubsub)
- [افهم المزيد عن مساعد شريط القوائم macOS.](https://docs.openclaw.ai/platforms/mac/menu-bar)
- [أدلة النظام: Windows (WSL2)](https://docs.openclaw.ai/platforms/windows), [Linux](https://docs.openclaw.ai/platforms/linux), [macOS](https://docs.openclaw.ai/platforms/macos), [iOS](https://docs.openclaw.ai/platforms/ios), [Android](https://docs.openclaw.ai/platforms/android)
- [استخدم دليل استكشاف الأخطاء وإصلاحها لتشخيص الأعطال الشائعة.](https://docs.openclaw.ai/channels/troubleshooting)
- [اقرأ إرشادات الأمان قبل تسريب أي معلومات.](https://docs.openclaw.ai/gateway/security)

## التوثيق المتقدم (الاكتشاف + التحكم)

- [الاكتشاف + التحويل](https://docs.openclaw.ai/gateway/discovery)
- [Bonjour/mDNS](https://docs.openclaw.ai/gateway/bonjour)
- [إقران البوابة](https://docs.openclaw.ai/gateway/pairing)
- [README البوابة عن بعد](https://docs.openclaw.ai/gateway/remote-gateway-readme)
- [واجهة التحكم](https://docs.openclaw.ai/web/control-ui)
- [لوحة المعلومات](https://docs.openclaw.ai/web/dashboard)

## التشغيل واستكشاف الأخطاء

- [فحص الصحة](https://docs.openclaw.ai/gateway/health)
- [قفل البوابة](https://docs.openclaw.ai/gateway/gateway-lock)
- [العملية في الخلفية](https://docs.openclaw.ai/gateway/background-process)
- [استكشاف أخطاء المتصفح (Linux)](https://docs.openclaw.ai/tools/browser-linux-troubleshooting)
- [التسجيل](https://docs.openclaw.ai/logging)

## الاستكشاف العميق

- [حلقة الوكيل](https://docs.openclaw.ai/concepts/agent-loop)
- [الوجود في الوقت الفعلي](https://docs.openclaw.ai/concepts/presence)
- [مخطط TypeBox](https://docs.openclaw.ai/concepts/typebox)
- [محولات RPC](https://docs.openclaw.ai/reference/rpc)
- [القوائم الانتظارية](https://docs.openclaw.ai/concepts/queue)

## مساحة العمل والمهارات

- [تكوين المهارات](https://docs.openclaw.ai/tools/skills-config)
- [الوكيل الافتراضي](https://docs.openclaw.ai/reference/AGENTS.default)
- [قوالب: الوكيل](https://docs.openclaw.ai/reference/templates/AGENTS)
- [قوالب: BOOTSTRAP](https://docs.openclaw.ai/reference/templates/BOOTSTRAP)
- [قوالب: الهوية](https://docs.openclaw.ai/reference/templates/IDENTITY)
- [قوالب: الروح](https://docs.openclaw.ai/reference/templates/SOUL)
- [قوالب: الأدوات](https://docs.openclaw.ai/reference/templates/TOOLS)
- [قوالب: المستخدم](https://docs.openclaw.ai/reference/templates/USER)

## أجزاء النظام الداخلية

- [بيئة تطوير macOS](https://docs.openclaw.ai/platforms/mac/dev-setup)
- [شريط قوائم macOS](https://docs.openclaw.ai/platforms/mac/menu-bar)
- [تنبيه الصوت macOS](https://docs.openclaw.ai/platforms/mac/voicewake)
- [العقد iOS](https://docs.openclaw.ai/platforms/ios)
- [العقد Android](https://docs.openclaw.ai/platforms/android)
- [Windows (WSL2)](https://docs.openclaw.ai/platforms/windows)
- [تطبيقات Linux](https://docs.openclaw.ai/platforms/linux)

## خطافات البريد الإلكتروني (Gmail)

- [docs.openclaw.ai/gmail-pubsub](https://docs.openclaw.ai/automation/gmail-pubsub)

## Molty

تم تطوير OpenClaw لمساعد الذكاء الاصطناعي **Molty** سرطان البحر. 🦞
تم إنشاؤه من قبل Peter Steinberger والمجتمع.

- [openclaw.ai](https://openclaw.ai)
- [soul.md](https://soul.md)
- [steipete.me](https://steipete.me)
- [@openclaw](https://x.com/openclaw)

## المجتمع

راجع ملف [CONTRIBUTING.md](CONTRIBUTING.md) للحصول على إرشادات المساهمة ومعلومات المشرفين وكيفية إرسال طلبات السحب. مشاريع ترميز AI/vibe مرحب بها! 🤖

شكر خاص إلى [Mario Zechner](https://mariozechner.at/) لدعمه ولتطويره
[pi-mono](https://github.com/badlogic/pi-mono).
شكر خاص إلى Adam Doppelt لتطويره lobster.bot.

نشكر جميع المساهمين:

<p align="left">
  <a href="https://github.com/steipete"><img src="https://avatars.githubusercontent.com/u/58493?v=4&s=48" width="48" height="48" alt="steipete" title="steipete"/></a> <a href="https://github.com/joshp123"><img src="https://avatars.githubusercontent.com/u/1497361?v=4&s=48" width="48" height="48" alt="joshp123" title="joshp123"/></a> <a href="https://github.com/cpojer"><img src="https://avatars.githubusercontent.com/u/13352?v=4&s=48" width="48" height="48" alt="cpojer" title="cpojer"/></a> <a href="https://github.com/mbelinky"><img src="https://avatars.githubusercontent.com/u/132747814?v=4&s=48" width="48" height="48" alt="Mariano Belinky" title="Mariano Belinky"/></a> <a href="https://github.com/plum-dawg"><img src="https://avatars.githubusercontent.com/u/5909950?v=4&s=48" width="48" height="48" alt="plum-dawg" title="plum-dawg"/></a> <a href="https://github.com/bohdanpodvirnyi"><img src="https://avatars.githubusercontent.com/u/31819391?v=4&s=48" width="48" height="48" alt="bohdanpodvirnyi" title="bohdanpodvirnyi"/></a> <a href="https://github.com/iHildy"><img src="https://avatars.githubusercontent.com/u/25069719?v=4&s=48" width="48" height="48" alt="iHildy" title="iHildy"/></a> <a href="https://github.com/jaydenfyi"><img src="https://avatars.githubusercontent.com/u/213395523?v=4&s=48" width="48" height="48" alt="jaydenfyi" title="jaydenfyi"/></a> <a href="https://github.com/joaohlisboa"><img src="https://avatars.githubusercontent.com/u/8200873?v=4&s=48" width="48" height="48" alt="joaohlisboa" title="joaohlisboa"/></a> <a href="https://github.com/mneves75"><img src="https://avatars.githubusercontent.com/u/2423436?v=4&s=48" width="48" height="48" alt="mneves75" title="mneves75"/></a>
  <a href="https://github.com/MatthieuBizien"><img src="https://avatars.githubusercontent.com/u/173090?v=4&s=48" width="48" height="48" alt="MatthieuBizien" title="MatthieuBizien"/></a> <a href="https://github.com/MaudeBot"><img src="https://avatars.githubusercontent.com/u/255777700?v=4&s=48" width="48" height="48" alt="MaudeBot" title="MaudeBot"/></a> <a href="https://github.com/sebslight"><img src="https://avatars.githubusercontent.com/u/19554889?v=4&s=48" width="48" height="48" alt="sebslight" title="sebslight"/></a> <a href="https://github.com/Glucksberg"><img src="https://avatars.githubusercontent.com/u/80581902?v=4&s=48" width="48" height="48" alt="Glucksberg" title="Glucksberg"/></a> <a href="https://github.com/rahthakor"><img src="https://avatars.githubusercontent.com/u/8470553?v=4&s=48" width="48" height="48" alt="rahthakor" title="rahthakor"/></a> <a href="https://github.com/vrknetha"><img src="https://avatars.githubusercontent.com/u/20596261?v=4&s=48" width="48" height="48" alt="vrknetha" title="vrknetha"/></a> <a href="https://github.com/tyler6204"><img src="https://avatars.githubusercontent.com/u/64381258?v=4&s=48" width="48" height="48" alt="tyler6204" title="tyler6204"/></a> <a href="https://github.com/vignesh07"><img src="https://avatars.githubusercontent.com/u/1436853?v=4&s=48" width="48" height="48" alt="vignesh07" title="vignesh07"/></a> <a href="https://github.com/radek-paclt"><img src="https://avatars.githubusercontent.com/u/50451445?v=4&s=48" width="48" height="48" alt="radek-paclt" title="radek-paclt"/></a> <a href="https://github.com/tobiasbischoff"><img src="https://avatars.githubusercontent.com/u/711564?v=4&s=48" width="48" height="48" alt="Tobias Bischoff" title="Tobias Bischoff"/></a>
  <a href="https://github.com/czekaj"><img src="https://avatars.githubusercontent.com/u/1464539?v=4&s=48" width="48" height="48" alt="czekaj" title="czekaj"/></a> <a href="https://github.com/ethanpalm"><img src="https://avatars.githubusercontent.com/u/56270045?v=4&s=48" width="48" height="48" alt="ethanpalm" title="ethanpalm"/></a> <a href="https://github.com/mukhtharcm"><img src="https://avatars.githubusercontent.com/u/56378562?v=4&s=48" width="48" height="48" alt="mukhtharcm" title="mukhtharcm"/></a> <a href="https://github.com/maxsumrall"><img src="https://avatars.githubusercontent.com/u/628843?v=4&s=48" width="48" height="48" alt="maxsumrall" title="maxsumrall"/></a> <a href="https://github.com/xadenryan"><img src="https://avatars.githubusercontent.com/u/165437834?v=4&s=48" width="48" height="48" alt="xadenryan" title="xadenryan"/></a> <a href="https://github.com/VACInc"><img src="https://avatars.githubusercontent.com/u/3279061?v=4&s=48" width="48" height="48" alt="VACInc" title="VACInc"/></a> <a href="https://github.com/rodrigouroz"><img src="https://avatars.githubusercontent.com/u/384037?v=4&s=48" width="48" height="48" alt="rodrigouroz" title="rodrigouroz"/></a> <a href="https://github.com/juanpablodlc"><img src="https://avatars.githubusercontent.com/u/92012363?v=4&s=48" width="48" height="48" alt="juanpablodlc" title="juanpablodlc"/></a> <a href="https://github.com/conroywhitney"><img src="https://avatars.githubusercontent.com/u/249891?v=4&s=48" width="48" height="48" alt="conroywhitney" title="conroywhitney"/></a> <a href="https://github.com/hsrvc"><img src="https://avatars.githubusercontent.com/u/129702169?v=4&s=48" width="48" height="48" alt="hsrvc" title="hsrvc"/></a>
  <a href="https://github.com/christianklotz"><img src="https://avatars.githubusercontent.com/u/69443?v=4&s=48" width="48" height="48" alt="christianklotz" title="christianklotz"/></a> <a href="https://github.com/magimetal"><img src="https://avatars.githubusercontent.com/u/36491250?v=4&s=48" width="48" height="48" alt="magimetal" title="magimetal"/></a> <a href="https://github.com/zerone0x"><img src="https://avatars.githubusercontent.com/u/39543393?v=4&s=48" width="48" height="48" alt="zerone0x" title="zerone0x"/></a> <a href="https://github.com/meaningfool"><img src="https://avatars.githubusercontent.com/u/2862331?v=4&s=48" width="48" height="48" alt="meaningfool" title="meaningfool"/></a> <a href="https://github.com/Takhoffman"><img src="https://avatars.githubusercontent.com/u/781889?v=4&s=48" width="48" height="48" alt="Takhoffman" title="Takhoffman"/></a> <a href="https://github.com/patelhiren"><img src="https://avatars.githubusercontent.com/u/172098?v=4&s=48" width="48" height="48" alt="patelhiren" title="patelhiren"/></a> <a href="https://github.com/NicholasSpisak"><img src="https://avatars.githubusercontent.com/u/129075147?v=4&s=48" width="48" height="48" alt="NicholasSpisak" title="NicholasSpisak"/></a> <a href="https://github.com/jonisjongithub"><img src="https://avatars.githubusercontent.com/u/86072337?v=4&s=48" width="48" height="48" alt="jonisjongithub" title="jonisjongithub"/></a> <a href="https://github.com/AbhisekBasu1"><img src="https://avatars.githubusercontent.com/u/40645221?v=4&s=48" width="48" height="48" alt="abhisekbasu1" title="abhisekbasu1"/></a> <a href="https://github.com/jamesgroat"><img src="https://avatars.githubusercontent.com/u/2634024?v=4&s=48" width="48" height="48" alt="jamesgroat" title="jamesgroat"/></a>
  <a href="https://github.com/BunsDev"><img src="https://avatars.githubusercontent.com/u/68980965?v=4&s=48" width="48" height="48" alt="BunsDev" title="BunsDev"/></a> <a href="https://github.com/claude"><img src="https://avatars.githubusercontent.com/u/81847?v=4&s=48" width="48" height="48" alt="claude" title="claude"/></a> <a href="https://github.com/JustYannicc"><img src="https://avatars.githubusercontent.com/u/52761674?v=4&s=48" width="48" height="48" alt="JustYannicc" title="JustYannicc"/></a> <a href="https://github.com/Hyaxia"><img src="https://avatars.githubusercontent.com/u/36747317?v=4&s=48" width="48" height="48" alt="Hyaxia" title="Hyaxia"/></a> <a href="https://github.com/dantelex"><img src="https://avatars.githubusercontent.com/u/631543?v=4&s=48" width="48" height="48" alt="dantelex" title="dantelex"/></a> <a href="https://github.com/SocialNerd42069"><img src="https://avatars.githubusercontent.com/u/118244303?v=4&s=48" width="48" height="48" alt="SocialNerd42069" title="SocialNerd42069"/></a> <a href="https://github.com/daveonkels"><img src="https://avatars.githubusercontent.com/u/533642?v=4&s=48" width="48" height="48" alt="daveonkels" title="daveonkels"/></a> <a href="https://github.com/apps/google-labs-jules"><img src="https://avatars.githubusercontent.com/in/842251?v=4&s=48" width="48" height="48" alt="google-labs-jules[bot]" title="google-labs-jules[bot]"/></a> <a href="https://github.com/lc0rp"><img src="https://avatars.githubusercontent.com/u/2609441?v=4&s=48" width="48" height="48" alt="lc0rp" title="lc0rp"/></a> <a href="https://github.com/mousberg"><img src="https://avatars.githubusercontent.com/u/57605064?v=4&s=48" width="48" height="48" alt="mousberg" title="mousberg"/></a>
  <a href="https://github.com/adam91holt"><img src="https://avatars.githubusercontent.com/u/9592417?v=4&s=48" width="48" height="48" alt="adam91holt" title="adam91holt"/></a> <a href="https://github.com/hougangdev"><img src="https://avatars.githubusercontent.com/u/105773686?v=4&s=48" width="48" height="48" alt="hougangdev" title="hougangdev"/></a> <a href="https://github.com/gumadeiras"><img src="https://avatars.githubusercontent.com/u/5599352?v=4&s=48" width="48" height="48" alt="gumadeiras" title="gumadeiras"/></a> <a href="https://github.com/shakkernerd"><img src="https://avatars.githubusercontent.com/u/165377636?v=4&s=48" width="48" height="48" alt="shakkernerd" title="shakkernerd"/></a> <a href="https://github.com/mteam88"><img src="https://avatars.githubusercontent.com/u/84196639?v=4&s=48" width="48" height="48" alt="mteam88" title="mteam88"/></a> <a href="https://github.com/hirefrank"><img src="https://avatars.githubusercontent.com/u/183158?v=4&s=48" width="48" height="48" alt="hirefrank" title="hirefrank"/></a> <a href="https://github.com/joeynyc"><img src="https://avatars.githubusercontent.com/u/17919866?v=4&s=48" width="48" height="48" alt="joeynyc" title="joeynyc"/></a> <a href="https://github.com/orlyjamie"><img src="https://avatars.githubusercontent.com/u/6668807?v=4&s=48" width="48" height="48" alt="orlyjamie" title="orlyjamie"/></a> <a href="https://github.com/dbhurley"><img src="https://avatars.githubusercontent.com/u/5251425?v=4&s=48" width="48" height="48" alt="dbhurley" title="dbhurley"/></a> <a href="https://github.com/omniwired"><img src="https://avatars.githubusercontent.com/u/322761?v=4&s=48" width="48" height="48" alt="Eng. Juan Combetto" title="Eng. Juan Combetto"/></a>
  <a href="https://github.com/TSavo"><img src="https://avatars.githubusercontent.com/u/877990?v=4&s=48" width="48" height="48" alt="TSavo" title="TSavo"/></a> <a href="https://github.com/aerolalit"><img src="https://avatars.githubusercontent.com/u/17166039?v=4&s=48" width="48" height="48" alt="aerolalit" title="aerolalit"/></a> <a href="https://github.com/julianengel"><img src="https://avatars.githubusercontent.com/u/10634231?v=4&s=48" width="48" height="48" alt="julianengel" title="julianengel"/></a> <a href="https://github.com/bradleypriest"><img src="https://avatars.githubusercontent.com/u/167215?v=4&s=48" width="48" height="48" alt="bradleypriest" title="bradleypriest"/></a> <a href="https://github.com/benithors"><img src="https://avatars.githubusercontent.com/u/20652882?v=4&s=48" width="48" height="48" alt="benithors" title="benithors"/></a> <a href="https://github.com/rohannagpal"><img src="https://avatars.githubusercontent.com/u/4009239?v=4&s=48" width="48" height="48" alt="rohannagpal" title="rohannagpal"/></a> <a href="https://github.com/timolins"><img src="https://avatars.githubusercontent.com/u/1440854?v=4&s=48" width="48" height="48" alt="timolins" title="timolins"/></a> <a href="https://github.com/f-trycua"><img src="https://avatars.githubusercontent.com/u/195596869?v=4&s=48" width="48" height="48" alt="f-trycua" title="f-trycua"/></a> <a href="https://github.com/benostein"><img src="https://avatars.githubusercontent.com/u/31802821?v=4&s=48" width="48" height="48" alt="benostein" title="benostein"/></a> <a href="https://github.com/elliotsecops"><img src="https://avatars.githubusercontent.com/u/141947839?v=4&s=48" width="48" height="48" alt="elliotsecops" title="elliotsecops"/></a>
</p>
- **عقد الجهاز** تنفذ عمليات محلية على الجهاز (مثل `system.run`، الكاميرا، تسجيل الشاشة، الإشعارات) عبر `node.invoke`.
  باختصار: يتم التنفيذ حيث يوجد Gateway؛ تحدث عمليات الجهاز حيث يوجد الجهاز.

التفاصيل: [الوصول عن بعد](https://docs.openclaw.ai/gateway/remote) · [العقد](https://docs.openclaw.ai/nodes) · [الأمن](https://docs.openclaw.ai/gateway/security)

## أذونات macOS عبر بروتوكول Gateway

يمكن لتطبيق macOS العمل في **وضع العقدة** ونشر قدراته وخرائط الأذونات عبر Gateway WebSocket (`node.list` / `node.describe`). يمكن للعملاء بعد ذلك تنفيذ العمليات المحلية عبر `node.invoke`:

- `system.run` ينفذ أوامر محلية ويعيد stdout/stderr/رمز الخروج؛ قم بتعيين `needsScreenRecording: true` لأذونات تسجيل الشاشة (وإلا ستتلقى خطأ `PERMISSION_MISSING`).
- `system.notify` يرسل إشعارًا للمستخدم، يفشل إذا تم رفض الإشعار.
- `canvas.*`، `camera.*`، `screen.record`، و `location.get` يتم توجيهها عبر `node.invoke` وتلتزم بحالة أذونات TCC.

أذونات bash المعززة (أذونات المضيف) و TCC macOS منفصلة:

- استخدم `/elevated on|off` لتبديل الوصول المعزز لكل جلسة عند التمكين + الإضافة إلى قائمة الأذونات.
- Gateway يستمر في كل تبديل جلسة عبر (أساليب WS) وكذلك `sessions.patch`، `thinkingLevel`، `verboseLevel`، `model`، `sendPolicy`، و `groupActivation`.

التفاصيل: [العقد](https://docs.openclaw.ai/nodes) · [تطبيق macOS](https://docs.openclaw.ai/platforms/macos) · [بروتوكول Gateway](https://docs.openclaw.ai/concepts/architecture)

## وكيل إلى وكيل (أدوات sessions_*)

- تسمح هذه الميزة بتنسيق العمل بين الجلسات دون التبديل بين واجهات الدردشة.
- `sessions_list` — يكتشف الجلسات (الوكلاء) النشطة وبياناتها التعريفية.
- `sessions_history` — يسترجع سجلات الجلسة المسجلة.
- `sessions_send` — يرسل رسالة إلى جلسة أخرى؛ خطوات الرد ping-pong + الإعلان الاختيارية (REPLY_SKIP، ANNOUNCE_SKIP).

التفاصيل: [أدوات الجلسة](https://docs.openclaw.ai/concepts/session-tool)

## تسجيل المهارات (ClawHub)

ClawHub هو نظام تسجيل مهارات مبسط. بمجرد تمكين ClawHub، يمكن للوكيل البحث تلقائيًا عن المهارات وإضافة جديدة حسب الحاجة.

[ClawHub](https://clawhub.com)

## أوامر الدردشة

أرسل هذه عبر WhatsApp/Telegram/Slack/Google Chat/Microsoft Teams/WebChat (أوامر المجموعة فقط لمديري المجموعة):

- `/status` — حالة الجلسة المختصرة (النموذج + الرموز، و التكاليف عندما تكون متاحة)
- `/new` أو `/reset` — إعادة تعيين الجلسة
- `/compact` — سياق الجلسة المختصر (ملخص)
- `/think <level>` — off|minimal|low|medium|high|xhigh (نماذج GPT-5.2 + Codex فقط)
- `/verbose on|off`
- `/usage off|tokens|full` — استخدام الرموز في كل رد
- `/restart` — إعادة تشغيل البوابة (مديري المجموعة فقط)
- `/activation mention|always` — مفتاح تنشيط المجموعة (المجموعات فقط)

## التطبيقات (اختياري)

تقدم البوابة نفسها تجربة رائعة. جميع التطبيقات اختيارية وتضيف وظائف إضافية.

إذا كنت تخطط لبناء/تشغيل تطبيقات مرافقة، يرجى اتباع أدلة النظام التالية.

### macOS (OpenClaw.app) (اختياري)

- التحكم في شريط القوائم للبوابة والصحة.
- تنبيه الصوت + تراكب وضع المحادثة بنقرة واحدة.
- WebChat + أدوات التصحيح.
- التحكم في البوابة عن بعد عبر SSH.

ملاحظة: يجب استخدام إصدار موقع ليبقى أذونات macOS بعد إعادة البناء (انظر `docs/mac/permissions.md`).

### عقد iOS (اختياري)

- تعمل كعقد عبر الجسر.
- إعادة توجيه محفز الصوت + سطح Canvas.
- التحكم عبر `openclaw nodes …`.

الدليل: [اتصال iOS](https://docs.openclaw.ai/platforms/ios).

### عقد Android (اختياري)

- مقترنة عبر نفس عملية الجسر + الإقران مثل iOS.
- السماح لأوامر Canvas والكاميرا وتسجيل الشاشة.
- الدليل: [اتصال Android](https://docs.openclaw.ai/platforms/android).

## مساحة عمل الوكيل + المهارات

- جذر مساحة العمل: `~/.openclaw/workspace` (قابل للتهيئة عبر `agents.defaults.workspace`).
- ملفات المطالبات المحقونة: `AGENTS.md`، `SOUL.md`، `TOOLS.md`.
- المهارات: `~/.openclaw/workspace/skills/<skill>/SKILL.md`.

## التكوين