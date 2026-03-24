---
theme: default
title: OpenClaw in My Daily Life
info: |
  A short practical talk about OpenClaw from a user perspective.
class: text-center
transition: slide-left
mdc: true
fonts:
  sans: Inter
  mono: Fira Code
colorSchema: auto
css: ./style.css
---

# OpenClaw in My Daily Life

### From chatbot to personal ops agent

<div class="mt-8 text-lg opacity-80 max-w-3xl mx-auto">
Not just <span class="accent">answering</span>, but <span class="accent">pulling context, prioritizing, reminding, and acting</span>.
</div>

<div class="mt-10 text-sm opacity-70 max-w-3xl mx-auto">
Meta-point: this deck was created with <b>OpenClaw</b> itself —
directly through the <b>OpenClaw TUI</b> in the live system.
</div>

<div class="mt-10 text-sm opacity-60">
Claus Käpplinger · short intro / ZeitgAIst round
</div>

<!--
Speaker notes:
- Keep the opening dry and practical: this is not a glossy product demo, but how I actually use OpenClaw.
- Set the meta-point early: the presentation itself was built through OpenClaw in the TUI.
- Goal: frame OpenClaw as an assistance layer, not just a chat window.
-->

---
layout: center
class: text-center
---

# The actual problem

<div class="text-3xl leading-tight max-w-4xl mx-auto">
Not too little AI.<br>
<span class="accent">Too many open loops across too many channels.</span>
</div>

<div class="mt-10 grid grid-cols-3 gap-5 text-left max-w-5xl mx-auto">
  <div class="card">
    <div class="card-title">Fragmentation</div>
    WhatsApp, email, calendar, files, browser, reminders — everything lives separately.
  </div>
  <div class="card">
    <div class="card-title">Overwhelm</div>
    The problem is often not missing information, but missing prioritization.
  </div>
  <div class="card">
    <div class="card-title">Friction</div>
    Even small next steps die from context switching and micro-coordination.
  </div>
</div>

<!--
Speaker notes:
- Don’t talk about AI yet. Talk about day-to-day coordination pain.
- My problem is not lack of tools, but too much coordination overhead.
-->

---
layout: two-cols
---

# Why I use it at all
## The personal version

<div class="mt-6 space-y-3 text-lg">
- I have many parallel topics and channels open at the same time.
- My setup is intentionally <b>local-first</b> and spread across files, calendar, email, and chat.
- So I do not need a “smart chat”; I need something that helps me see <b>the next meaningful step</b>.
</div>

<div class="note mt-8">
OpenClaw becomes interesting to me when it does not just sound smart,
but actually <b>removes mental load</b>.
</div>

::right::

<div class="card mt-6">
  <div class="card-title">What I want</div>
  <ul class="mt-3 text-sm leading-7">
    <li>less context switching</li>
    <li>a clearer focus for the day</li>
    <li>small proactive nudges instead of tool chaos</li>
    <li>local data that does not get scattered everywhere</li>
  </ul>
</div>

<div class="source mt-6">
Personal context: local-first knowledge system + focus on reducing overwhelm.
</div>

<!--
Speaker notes:
- This is the human reason.
- Don’t get overly personal; keep it pragmatic: too many projects, too many channels, not enough clear next steps.
-->

---
layout: center
class: text-center
---

# My thesis

<div class="text-3xl leading-tight max-w-4xl mx-auto">
OpenClaw becomes interesting when it sits<br>
<span class="accent">between channels and action</span>.
</div>

<div class="mt-10 text-xl opacity-85 max-w-4xl mx-auto">
So not just: <span class="opacity-60">“prompt in, text out”</span><br>
but: <span class="accent">chat + local data + tools + proactive execution</span>
</div>

<!--
Speaker notes:
- This is the core one-liner slide.
- If time is short, problem + personal story + this slide is already a solid mini-talk.
-->

---

# The architectural idea behind it

<div class="mt-6 grid grid-cols-4 gap-4 text-left text-sm max-w-6xl mx-auto">
  <div class="card">
    <div class="card-title">1. Interfaces</div>
    WhatsApp, Web UI, CLI, additional channels
  </div>
  <div class="card">
    <div class="card-title">2. Gateway</div>
    ingestion, access control, routing, delivery
  </div>
  <div class="card">
    <div class="card-title">3. Runtime</div>
    builds context, invokes the model, drives tools
  </div>
  <div class="card">
    <div class="card-title">4. State</div>
    sessions, memory, files, reports, cron, browser
  </div>
</div>

<div class="mt-8">

```mermaid
flowchart LR
    A[Channels / UI / CLI] --> B[Gateway]
    B --> C[Access Control & Routing]
    C --> D[Agent Runtime]
    D --> E[Context Assembly]
    D --> F[Model Invocation]
    D --> G[Tool Execution]
    E --> H[Sessions / Memory / Files]
    G --> I[Browser / Scripts / Cron / Messaging]
    F --> J[Response Delivery]
    I --> J
```

</div>

<div class="source mt-5">
Inspired by Paolo Perrotta, <i>OpenClaw Architecture, Explained: How It Works</i>, especially the architecture overview and “Phase 2: Access Control & Routing”.
</div>

<!--
Speaker notes:
- Don’t go too deep here.
- The point is the separation of interface, control, runtime, and state.
- The model is only one piece; OpenClaw is the orchestration around it.
-->

---
layout: two-cols
---

# What I discovered during the research
## And want to try next

<div class="mt-5 space-y-3 text-base leading-7">
- While building this deck, it became clear to me that OpenClaw does not stop at personal assistance.
- Two patterns immediately felt relevant because they fit my setup directly.
</div>

<div class="note mt-5">
That makes OpenClaw feel less like a single bot and more like a <b>platform for personal infrastructure</b>.
</div>

::right::

<div class="card mt-2">
  <div class="card-title">1. Self-Healing Home Server</div>
  An agent monitors the home server, notices problems, and helps repair them instead of only screaming in alerts.
</div>

<div class="card mt-4">
  <div class="card-title">2. Multi-Agent Team</div>
  Multiple specialized agents — for example strategy, dev, and marketing — with shared context and central coordination.
</div>

<div class="source mt-5 text-xs leading-5">
Further reading:<br>
<a href="https://github.com/hesamsheikh/awesome-openclaw-usecases/blob/main/usecases/self-healing-home-server.md" target="_blank">self-healing-home-server.md</a><br>
<a href="https://github.com/hesamsheikh/awesome-openclaw-usecases/blob/main/usecases/multi-agent-team.md" target="_blank">multi-agent-team.md</a>
</div>

<!--
Speaker notes:
- This is your “there is much more here” slide.
- Good phrasing: while building the presentation, I realized I do not just want an assistant; I probably also want an agentic home server and later a small agent team.
-->

---
layout: two-cols
---

# Example 1
## Daily steering through WhatsApp

<div class="mt-6 space-y-3 text-lg">

- I can simply write: <span class="pill">“What matters today?”</span>
- OpenClaw pulls <b>local calendar context</b>
- in my setup that runs through <b>vdirsyncer + khal</b>
- the goal is not just listing events, but giving me <b>one real focus for the day</b>

</div>

<div class="note mt-8">
Not: “Here are your appointments.”<br>
But rather: “You have 3 fixed blocks — in between, exactly one meaningful work goal.”
</div>

::right::

<div class="mock-chat mt-4">
  <div class="msg user">What matters today?</div>
  <div class="msg bot">2:00 PM university elections with IT<br>3:00 PM ZeitgAIst: Open Claw<br>8:30 PM introductory THW meeting<br><br>In between: one real work goal, not five.</div>
</div>

<div class="source mt-6">
Source (own practice): local calendar via <b>vdirsyncer/khal</b>; focus on real commitments.
</div>

<!--
Speaker notes:
- This is a real small everyday moment.
- Important framing: not “the bot lists appointments”, but “it helps me prioritize”.
-->

---
layout: two-cols
---

# Example 2
## Proactive assistance on WhatsApp

<div class="mt-6 space-y-3 text-lg">

- daily <b>check-ins</b>, <b>shutdowns</b>, and <b>reminders</b>
- not only on request, but also <b>at the right time</b>
- with guardrails: a dedicated bot account is interactive, the main channel is more controlled
- that turns AI into an <b>assistance layer in daily life</b>

</div>

<div class="note mt-8">
This is the actual jump for me:<br>
<b>from reactive chat to light proactive support for action.</b>
</div>

::right::

<div class="mock-chat mt-4">
  <div class="msg bot">Daily check-in. Reply with 4 lines...</div>
  <div class="msg bot">Bedtime ramp (15 min). Goal: devices OFF at 9:00 PM.</div>
  <div class="msg bot">Quick check: what are you doing right now? Are you on your BIG 1?</div>
</div>

<div class="source mt-6">
Source (own practice): WhatsApp role model + daily cron/heartbeat check-ins.
</div>

<!--
Speaker notes:
- Use the examples instead of overusing the word “proactive”.
- Good phrasing: light support for action instead of annoying bot spam.
-->

---
layout: two-cols
---

# Example 3
## Email triage with a local pipeline

<div class="mt-4 space-y-2 text-base leading-7">

- there is a <b>local runner</b> for email triage
- results land in <b>reports</b>, not in some black box
- relevant emails are filtered and surfaced back briefly
- the goal is <b>less overwhelm and fewer context switches</b>

</div>

<div class="note mt-5">
Not: “AI reads email.”<br>
But: <b>I can see faster what I actually need to react to.</b>
</div>

::right::

<div class="card mt-3">
  <div class="card-title">Local flow</div>
  <div class="text-sm mt-2 leading-6">
    Inbox → triage runner → relevance schema → report → short feedback loop
  </div>
</div>

<div class="mt-4 rounded-2xl border border-gray-300 p-3 bg-gray-50 dark:bg-zinc-900 text-xs leading-5">
  <div><b>Concrete in my setup:</b></div>
  <div class="mt-2 font-mono">~/openclaw/scripts/mail_triage_runner.py</div>
  <div class="font-mono">~/openclaw/reports/mail-triage/</div>
</div>

<div class="source mt-4">
Source (own practice): local mail-triage runner in the OpenClaw workspace.
</div>

<!--
Speaker notes:
- Bridge this back to “AI as infrastructure”.
- Email triage is not LLM magic; it is pipeline + files + reports + return channel.
-->

---

# The meta layer: this deck was built with OpenClaw

<div class="mt-6 grid grid-cols-5 gap-4 text-left text-sm max-w-6xl mx-auto">
  <div class="card">
    <div class="card-title">1. Briefing</div>
    idea and audience clarified in chat
  </div>
  <div class="card">
    <div class="card-title">2. Recall</div>
    searched my personal memory DB for real examples
  </div>
  <div class="card">
    <div class="card-title">3. TUI</div>
    created and iterated on the deck directly via the <b>OpenClaw TUI</b>
  </div>
  <div class="card">
    <div class="card-title">4. Build</div>
    built it locally as a Slidev deck and exported a PDF
  </div>
  <div class="card">
    <div class="card-title">5. Delivery</div>
    created a dedicated GitHub repo and pushed it
  </div>
</div>

<div class="note mt-10 max-w-5xl mx-auto">
The nicest demo is almost the meta-demo: OpenClaw is not only being explained here — it was also the tool used to build, export, and publish this presentation through the TUI.
</div>

<div class="source mt-6">
Repo: <a href="https://github.com/Clausinho/slidev-openclaw-talk" target="_blank">github.com/Clausinho/slidev-openclaw-talk</a>
</div>

<!--
Speaker notes:
- This is the mic-drop moment.
- If there is time, mention that the repo setup, PDF export, and Pages deployment were triggered out of the same workflow.
-->

---
layout: center
class: text-center
---

# My narrative in one sentence

<div class="text-3xl max-w-4xl mx-auto leading-relaxed">
OpenClaw is not just another smart chatbot for me,
but <span class="accent">a personal runtime sitting between my channels and my next meaningful actions</span>.
</div>

<!--
Speaker notes:
- This is your closing sentence.
- If anything in the talk gets wobbly, land here and close cleanly.
-->

---
layout: two-cols
---

# Links to take away
## Live + repo via QR

<div class="mt-6 space-y-4 text-base leading-7">
  <div class="card">
    <div class="card-title">Live deck</div>
    <div><b>Link:</b> clausinho.github.io/slidev-openclaw-talk/</div>
  </div>
  <div class="card">
    <div class="card-title">Repo</div>
    <div><b>Link:</b> github.com/Clausinho/slidev-openclaw-talk</div>
  </div>
</div>

<div class="note mt-6">
QR is simply the pragmatic exit — nobody wants to type long URLs at the end.
</div>

::right::

<div class="grid grid-cols-2 gap-4 mt-4">
  <div class="card text-center">
    <div class="card-title mb-2">Live deck</div>
    <img src="./live-qr.svg" alt="QR code for live deck" style="width: 100%; max-width: 220px; margin: 0 auto;" />
  </div>
  <div class="card text-center">
    <div class="card-title mb-2">Repo</div>
    <img src="./repo-qr.svg" alt="QR code for repo" style="width: 100%; max-width: 220px; margin: 0 auto;" />
  </div>
</div>

<!--
Speaker notes:
- Don’t sell here.
- Just say: if you want, you can open the live deck or grab the repo directly.
-->

---
layout: center
class: text-center
---

# Thanks

### If you want, I can show the WhatsApp / TUI / workflow part live afterwards.

<!--
Speaker notes:
- Calm ending.
- Good spoken last line: I’m happy to show a 2-minute live feel for how this works in practice.
-->
