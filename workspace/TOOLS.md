# TOOLS.md - Local Notes

Skills define _how_ tools work. This file is for _your_ specifics — the stuff that's unique to your setup.

## Political Discussion Bot

**Trigger:** When user says "Diskussion: <Thema>" or similar
**Action:** Run: `bash -c "cd /root && node trigger-discussion.js '<Thema>'"`

This starts a political discussion in #ai-discussion with three agents:
- [Thomas] - Neutral moderator
- [Markus] - Conservative perspective  
- [Sarah] - Progressive perspective

Example: If user says "Diskussion: Klimaschutz", execute:
```bash
bash -c "cd /root && node trigger-discussion.js 'Klimaschutz'"
```

**Important:** Always acknowledge with "🎭 Starte Diskussion: <Thema>" before executing.

## What Goes Here

Things like:

- Camera names and locations
- SSH hosts and aliases
- Preferred voices for TTS
- Speaker/room names
- Device nicknames
- Anything environment-specific

## Examples

```markdown
### Cameras

- living-room → Main area, 180° wide angle
- front-door → Entrance, motion-triggered

### SSH

- home-server → 192.168.1.100, user: admin

### TTS

- Preferred voice: "Nova" (warm, slightly British)
- Default speaker: Kitchen HomePod
```

## Why Separate?

Skills are shared. Your setup is yours. Keeping them apart means you can update skills without losing your notes, and share skills without leaking your infrastructure.

---

Add whatever helps you do your job. This is your cheat sheet.
