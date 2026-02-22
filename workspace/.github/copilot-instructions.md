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
