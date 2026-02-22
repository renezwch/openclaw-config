# Copilot Instructions

This is the workspace for an [OpenClaw](https://github.com/openclaw) AI agent. It is not a traditional software project — there are no build/test commands. The "code" here is a set of markdown files that define the agent's identity, memory, and behavior.

## Workspace Architecture

```
workspace/
├── AGENTS.md      # Operating instructions: session startup, memory protocol, safety rules
├── SOUL.md        # Core personality and behavioral principles
├── IDENTITY.md    # Name, creature type, vibe, emoji, avatar
├── USER.md        # Info about the human this agent assists (René)
├── MEMORY.md      # Long-term curated memory — PRIVATE, main session only
├── HEARTBEAT.md   # Checklist for periodic background tasks (keep minimal)
├── TOOLS.md       # Local environment-specific notes (SSH hosts, devices, etc.)
├── memory/        # Daily raw session logs: memory/YYYY-MM-DD.md
└── <Projects>/    # Project subdirectories (e.g., Meteo/)
```

The agent runtime lives at `/root/.openclaw/`. Agent-wide config (channels, models, auth) is in `/root/.openclaw/openclaw.json`.

## Session Startup Convention

Every session, the agent reads these files in order before doing anything:
1. `SOUL.md`
2. `USER.md`
3. `memory/YYYY-MM-DD.md` for today and yesterday
4. `MEMORY.md` — **only in main/direct sessions**, never in group chats (privacy)

## Memory System

- **Daily logs** (`memory/YYYY-MM-DD.md`): raw notes from each session — create `memory/` if it doesn't exist
- **Long-term memory** (`MEMORY.md`): curated, distilled insights updated periodically from daily logs
- When asked to "remember" something, write it to the appropriate file — mental notes don't survive restarts
- `MEMORY.md` contains personal context about René and must not be shared in group/shared chat contexts

## Key Conventions

- **Safety**: Ask before any external action (emails, tweets, public posts). `trash` over `rm`.
- **Group chats**: Don't respond to every message. Respond when directly mentioned, when you can add genuine value, or to correct misinformation. One reaction per message max.
- **HEARTBEAT.md**: Keep it small (token cost). Add only active periodic tasks; clear when done.
- **TOOLS.md**: Environment-specific notes go here (device names, SSH aliases, preferred TTS voices), not in skill files.
- **Projects** live as subdirectories (e.g., `Meteo/`) with their own `README.md` and standard subfolders (`docs/`, `data/`, `scripts/`, `research/`).
- The agent may freely read, organize, and commit changes to this workspace without asking permission.

## Roadmap: Ausbau zum umfangreichen persönlichen Assistenten

### 🔴 Priorität 1 — Basis vervollständigen
Diese Dateien sind noch weitgehend leer und limitieren die Qualität des Agenten stark:
- **`IDENTITY.md`** — Name, Persönlichkeit, Vibe, Emoji noch nicht definiert
- **`USER.md`** — René's Timezone, Interessen, Kontext, Vorlieben fehlen
- **`MEMORY.md`** — Kaum befüllt; je mehr Kontext über René, desto besser der Agent
- **`HEARTBEAT.md`** — Leer; proaktive Checks (E-Mail, Kalender, Wetter) hier eintragen

### 🟡 Priorität 2 — Integrationen
| Integration | Nutzen | Einstieg |
|---|---|---|
| **E-Mail** (Gmail/IMAP) | Lesen, zusammenfassen, beantworten | OpenClaw skill oder IMAP-Script |
| **Google Calendar** | Termine kennen, erinnern, planen | Google API OAuth |
| **GitHub** | PRs, Issues, Notifications | PAT bereits vorhanden |
| **Home Assistant** | Smarthome steuern | Long-lived access token + REST API |
| **ElevenLabs TTS** | Sprach-Antworten (in AGENTS.md erwähnt) | API Key in openclaw.json |
| **Spotify / Plex** | Musik steuern | OAuth / Plex Token |

### 🟢 Priorität 3 — Proaktivität & Automatisierung
- **Morgen-Briefing** als Cron-Job: Wetter + Kalender + wichtige News zusammengefasst
- **Wöchentliche Zusammenfassung** (Freitag): Was lief diese Woche?
- **HEARTBEAT.md** mit rotierenden Checks: E-Mail → Kalender → GitHub → Wetter
- **Weitere Sub-Agents** für spezifische Domänen (analog zum Diskussions-Bot)
- **Memory-Maintenance**: Heartbeat nutzen um `MEMORY.md` aus Daily-Logs zu destillieren

### Aktuell laufende Cron-Jobs
- Daily AI & Coding News → Slack #ai-news (09:00)
- Daily Swiss Politics & Economy News → Slack (09:00)
- Auto Update Check → announce (09:00)
