---
theme: default
title: OpenClaw in meinem Alltag
info: |
  Kurzer Praxis-Impuls zu OpenClaw aus Nutzerperspektive.
class: text-center
transition: slide-left
mdc: true
fonts:
  sans: Inter
  mono: Fira Code
colorSchema: auto
css: ./style.css
---

# OpenClaw in meinem Alltag

### Vom Chatbot zum persönlichen Ops-Agenten

<div class="mt-8 text-lg opacity-80 max-w-3xl mx-auto">
Nicht nur <span class="accent">antworten</span>, sondern <span class="accent">Kontext ziehen, priorisieren, erinnern und handeln</span>.
</div>

<div class="mt-10 text-sm opacity-70 max-w-3xl mx-auto">
Meta-Pointe: Dieses Deck wurde selbst mit <b>OpenClaw</b> erstellt —
und zwar direkt über das <b>OpenClaw TUI</b> im laufenden System.
</div>

<div class="mt-10 text-sm opacity-60">
Claus Käpplinger · Kurzvorstellung / ZeitgAIst-Runde
</div>

---
layout: center
class: text-center
---

# Das eigentliche Problem

<div class="text-3xl leading-tight max-w-4xl mx-auto">
Nicht zu wenig AI.<br>
<span class="accent">Zu viele offene Schleifen in zu vielen Kanälen.</span>
</div>

<div class="mt-10 grid grid-cols-3 gap-5 text-left max-w-5xl mx-auto">
  <div class="card">
    <div class="card-title">Fragmentierung</div>
    WhatsApp, Mail, Kalender, Dateien, Browser, Erinnerungen — alles lebt getrennt.
  </div>
  <div class="card">
    <div class="card-title">Overwhelm</div>
    Das Problem ist oft nicht fehlende Information, sondern fehlende Priorisierung.
  </div>
  <div class="card">
    <div class="card-title">Reibung</div>
    Selbst kleine nächste Schritte sterben an Kontextwechseln und Mikro-Orga.
  </div>
</div>

---
layout: center
class: text-center
---

# Meine These

<div class="text-3xl leading-tight max-w-4xl mx-auto">
OpenClaw wird spannend, wenn es<br>
<span class="accent">zwischen Kanälen und Handlung</span> sitzt.
</div>

<div class="mt-10 text-xl opacity-85 max-w-4xl mx-auto">
Also nicht nur: <span class="opacity-60">„Prompt rein, Text raus“</span><br>
sondern: <span class="accent">Chat + lokale Daten + Tools + proaktive Ausführung</span>
</div>

---

# Architektur-Idee dahinter

<div class="mt-6 grid grid-cols-4 gap-4 text-left text-sm max-w-6xl mx-auto">
  <div class="card">
    <div class="card-title">1. Interfaces</div>
    WhatsApp, Web UI, CLI, weitere Channels
  </div>
  <div class="card">
    <div class="card-title">2. Gateway</div>
    Ingestion, Access Control, Routing, Delivery
  </div>
  <div class="card">
    <div class="card-title">3. Runtime</div>
    Kontext bauen, Modell aufrufen, Tools steuern
  </div>
  <div class="card">
    <div class="card-title">4. State</div>
    Sessions, Memory, Files, Reports, Cron, Browser
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
Inspiriert von Paolo Perrotta, <i>OpenClaw Architecture, Explained: How It Works</i>, insb. Architekturüberblick und „Phase 2: Access Control & Routing“.
</div>

---
layout: two-cols
---

# Beispiel 1
## Tagessteuerung über WhatsApp

<div class="mt-6 space-y-3 text-lg">

- Ich kann einfach schreiben: <span class="pill">„Was ist heute wichtig?“</span>
- OpenClaw zieht dazu <b>lokalen Kalender-Kontext</b>
- bei mir läuft das über <b>vdirsyncer + khal</b>
- Ziel ist nicht nur Terminanzeige, sondern: <b>ein echter Fokus für den Tag</b>

</div>

<div class="note mt-8">
Nicht: „Hier sind deine Termine.“<br>
Sondern eher: „Du hast 3 feste Blöcke — dazwischen genau ein sinnvolles Arbeitsziel.“
</div>

::right::

<div class="mock-chat mt-4">
  <div class="msg user">Was ist heute wichtig?</div>
  <div class="msg bot">14:00 Hochschulwahlen mit IT<br>15:00 ZeitgAIst: Open Claw<br>20:30 Kennenlerntermin THW<br><br>Dazwischen nur ein echtes Arbeitsziel, nicht fünf.</div>
</div>

<div class="source mt-6">
Quelle (eigene Praxis): lokaler Kalender via <b>vdirsyncer/khal</b>; Fokus auf echte Commitments.
</div>

---
layout: two-cols
---

# Beispiel 2
## Proaktive Assistenz auf WhatsApp

<div class="mt-6 space-y-3 text-lg">

- tägliche <b>Check-ins</b>, <b>Shutdowns</b> und <b>Reminder</b>
- nicht nur auf Anfrage, sondern auch <b>zum richtigen Zeitpunkt</b>
- mit Guardrails: dedizierter Bot interaktiv, Hauptkanal kontrollierter
- dadurch wird AI zu einer <b>Assistenzschicht im Alltag</b>

</div>

<div class="note mt-8">
Das ist für mich der eigentliche Sprung:<br>
<b>von reaktivem Chat zu leichter proaktiver Handlungsunterstützung.</b>
</div>

::right::

<div class="mock-chat mt-4">
  <div class="msg bot">Daily check-in. Reply with 4 lines...</div>
  <div class="msg bot">Bedtime ramp (15 min). Goal: devices OFF at 21:00.</div>
  <div class="msg bot">Kurz-Check: Was machst du gerade? Bist du auf deinem BIG 1?</div>
</div>

<div class="source mt-6">
Quelle (eigene Praxis): WhatsApp-Rollenmodell + tägliche Cron-/Heartbeat-Check-ins.
</div>

---
layout: two-cols
---

# Beispiel 3
## Mail-Triage mit lokaler Pipeline

<div class="mt-6 space-y-3 text-lg">

- Für Mail-Triage gibt es bei mir einen <b>lokalen Runner</b>
- Ergebnisse landen als <b>Reports</b>, nicht in irgendeiner Blackbox
- Relevante Mails können gefiltert, gebündelt und kurz zurückgespielt werden
- Das ist vor allem ein <b>Overwhelm-Problem</b>, nicht nur ein NLP-Problem

</div>

<div class="note mt-8">
Der Mehrwert ist nicht „AI liest Mails“.<br>
Der Mehrwert ist: <b>Ich sehe schneller, worauf ich wirklich reagieren muss.</b>
</div>

::right::

<div class="card mt-5">
  <div class="card-title">Lokaler Flow</div>
  <div class="text-sm mt-3 leading-6">
    Inbox → Mail-Triage-Runner → Relevanzschema → Report → kurze Rückmeldung
  </div>
</div>

<div class="mt-6 rounded-2xl border border-gray-300 p-4 bg-gray-50 dark:bg-zinc-900 text-sm">
  <div><b>Konkret im Setup:</b></div>
  <div class="mt-2 font-mono">~/openclaw/scripts/mail_triage_runner.py</div>
  <div class="font-mono">~/openclaw/reports/mail-triage/</div>
</div>

<div class="source mt-6">
Quelle (eigene Praxis): lokaler Mail-Triage-Runner im OpenClaw-Workspace.
</div>

---

# Die Meta-Ebene: Dieses Deck wurde mit OpenClaw gebaut

<div class="mt-6 grid grid-cols-5 gap-4 text-left text-sm max-w-6xl mx-auto">
  <div class="card">
    <div class="card-title">1. Briefing</div>
    Idee und Zielgruppe per Chat geklärt
  </div>
  <div class="card">
    <div class="card-title">2. Recall</div>
    persönliche Memory DB nach echten Beispielen durchsucht
  </div>
  <div class="card">
    <div class="card-title">3. TUI</div>
    das Deck direkt über das <b>OpenClaw TUI</b> erzeugt und iteriert
  </div>
  <div class="card">
    <div class="card-title">4. Build</div>
    lokal als Slidev-Deck gebaut und als PDF exportiert
  </div>
  <div class="card">
    <div class="card-title">5. Delivery</div>
    eigenes GitHub-Repo angelegt und gepusht
  </div>
</div>

<div class="note mt-10 max-w-5xl mx-auto">
Die schönste Demo ist fast die Meta-Demo: OpenClaw erklärt hier nicht nur sich selbst — es war auch das Werkzeug, mit dem diese Präsentation über das TUI gebaut, exportiert und veröffentlicht wurde.
</div>

<div class="source mt-6">
Repo: <https://github.com/Clausinho/slidev-openclaw-talk>
</div>

---
layout: center
class: text-center
---

# Meine Narrative in einem Satz

<div class="text-3xl max-w-4xl mx-auto leading-relaxed">
OpenClaw ist für mich kein weiterer smarter Chatbot,
sondern <span class="accent">eine persönliche Runtime, die zwischen meinen Kanälen und meinen nächsten sinnvollen Handlungen sitzt</span>.
</div>

---
layout: center
class: text-center
---

# Danke

### Wenn ihr wollt, zeige ich danach kurz den WhatsApp-/TUI-/Workflow-Teil live.
