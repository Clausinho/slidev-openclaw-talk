# OpenClaw Talk (Slidev)

Kleines Slidev-Deck für die OpenClaw-/ZeitgAIst-Vorstellung.

## Live

- GitHub Repo: <https://github.com/Clausinho/slidev-openclaw-talk>
- GitHub Pages: `https://clausinho.github.io/slidev-openclaw-talk/` *(nach dem ersten erfolgreichen Pages-Deploy)*

## Start lokal

```bash
cd /home/clausi/openclaw/reports/slidev-openclaw-talk
npm install
npm run dev
```

## Build lokal

```bash
npm run build
```

## Build für GitHub Pages

```bash
npm run build:pages
```

## PDF exportieren

```bash
npm run export
```

## Inhalt

Das Deck basiert auf echten Beispielen aus dem Setup:
- WhatsApp -> Tagespriorisierung aus lokalem Kalenderkontext
- Mail-Triage über lokalen Runner
- Proaktive Check-ins / Reminder über OpenClaw
- Meta: Das Deck selbst wurde über das OpenClaw TUI erstellt, als PDF exportiert und in ein eigenes GitHub-Repo gepusht

## GitHub Actions

- `pages.yml` baut und veröffentlicht das Deck auf GitHub Pages
- `export-pdf.yml` exportiert optional ein PDF als Workflow-Artefakt
