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
OpenClaw ist für mich nicht interessant, weil es „ein LLM mit Chatfenster“ ist —
sondern weil es <span class="accent">an echte Kanäle, lokale Daten und Workflows</span> andockt.
</div>

<div class="mt-12 text-sm opacity-60">
Claus Käpplinger · Kurzvorstellung / ZeitgAIst-Runde
</div>

<!--
Hook:
Ich will nicht noch einen Chatbot. Ich will einen Assistenten, der in meinem echten Alltag operieren kann.
-->

---
layout: center
class: text-center
---

# Die Kernidee

<div class="text-3xl leading-tight max-w-4xl mx-auto">
<span class="accent">Chat + Tools + lokale Daten + proaktive Ausführung</span><br>
statt nur <span class="opacity-60">Prompt rein, Text raus</span>
</div>

<div class="mt-10 grid grid-cols-4 gap-4 text-left text-sm max-w-5xl mx-auto">
  <div class="card">
    <div class="card-title">Input</div>
    WhatsApp, Webchat, Heartbeats, Cron, Dateien, Kalender, Mail
  </div>
  <div class="card">
    <div class="card-title">Kontext</div>
    Verlauf, Memory, lokale Files, Tageskontext, persönliche Regeln
  </div>
  <div class="card">
    <div class="card-title">Aktion</div>
    prüfen, priorisieren, erinnern, schreiben, triggern, zusammenfassen
  </div>
  <div class="card">
    <div class="card-title">Output</div>
    kurze Nachricht, Reminder, Tagesfokus, Report, Follow-up
  </div>
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
Bezug: lokaler Kalender via <b>vdirsyncer/khal</b>, Fokus auf echte Commitments.
</div>

<!--
Memory reference:
Source: memory/2026-03-23
-->

---
layout: two-cols
---

# Beispiel 2
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

<!--
Memory reference:
Source: memory/2026-03-23
-->

---
layout: two-cols
---

# Beispiel 3
## Proaktive Assistenz auf WhatsApp

<div class="mt-6 space-y-3 text-lg">

- tägliche <b>Check-ins</b>, <b>Shutdowns</b> und <b>Reminder</b>
- nicht nur auf Anfrage, sondern auch <b>zum richtigen Zeitpunkt</b>
- mit Guardrails: dedizierter Bot interaktiv, Hauptkanal kontrollierter
- dadurch wird AI zu einer <b>Assistenzschicht im Alltag</b>

</div>

<div class="note mt-8">
Das ist für mich der eigentliche Sprung:<br>
<b>von reaktivem Chat zu leicht proaktiver Handlungsunterstützung.</b>
</div>

::right::

<div class="mock-chat mt-4">
  <div class="msg bot">Daily check-in. Reply with 4 lines...</div>
  <div class="msg bot">Bedtime ramp (15 min). Goal: devices OFF at 21:00.</div>
  <div class="msg bot">Kurz-Check: Was machst du gerade? Bist du auf deinem BIG 1?</div>
</div>

<div class="source mt-6">
Bezug: WhatsApp-Rollenmodell + proaktive Check-ins / Heartbeats.
</div>

<!--
Memory reference:
Source: MEMORY.md
Source: sessions/35419351-cdc1-4c2d-b1ee-bd249efc829c#L49-L64
-->

---

# Technisch gesehen

<div class="mt-6 grid grid-cols-3 gap-5 text-left">
  <div class="card">
    <div class="card-title">Interfaces</div>
    <ul class="mt-3 text-sm leading-7">
      <li>WhatsApp</li>
      <li>Webchat</li>
      <li>Cron / Heartbeats</li>
      <li>Browser / lokale Files</li>
    </ul>
  </div>
  <div class="card">
    <div class="card-title">Reasoning Layer</div>
    <ul class="mt-3 text-sm leading-7">
      <li>Session-Kontext</li>
      <li>Memory / Regeln</li>
      <li>Entscheidung: antworten, schweigen oder handeln</li>
    </ul>
  </div>
  <div class="card">
    <div class="card-title">Execution Layer</div>
    <ul class="mt-3 text-sm leading-7">
      <li>lokale Scripts</li>
      <li>Dateioperationen</li>
      <li>Nachrichten / Reminder</li>
      <li>Berichte / Automationen</li>
    </ul>
  </div>
</div>

<div class="mt-10">

```mermaid
flowchart LR
    A[Channel / Trigger] --> B[OpenClaw Session]
    B --> C[Memory + Files + Context]
    B --> D[Tools + Scripts + Browser]
    C --> E[Decision]
    D --> E
    E --> F[Short reply / Reminder / Report / Action]
```

</div>

---
layout: center
class: text-center
---

# Warum ich das spannend finde

<div class="text-2xl max-w-4xl mx-auto leading-relaxed">
Ich bekomme nicht einfach nur <span class="opacity-70">„mehr AI“</span>,
sondern <span class="accent">mehr Handlungskraft bei weniger mentalem Overhead</span>.
</div>

<div class="mt-10 text-lg opacity-80">
Gerade bei Kalender, Mail, Priorisierung und Follow-ups ist das sofort praktisch.
</div>

---
layout: center
class: text-center
---

# Danke

### Wenn ihr wollt, zeige ich danach kurz den WhatsApp-/Workflow-Teil live.
