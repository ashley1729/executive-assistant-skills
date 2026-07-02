# executive-assistant-skills

OpenClaw skills that replace routine executive assistant work and add an Executive Control Assistant (ECA/ECS) layer for founder/operator control.

After setting up these skills with [OpenClaw](https://docs.openclaw.ai/), I let go of my human EA and replaced her core recurring work with my Claw. This repo now includes the original EA operating skills plus the ECA / Executive Control System patterns for inbox discipline, decision compression, calendar integrity, open-loop control, and stress containment.

## What's included

### Core executive assistant skills

| Skill | What it replaces |
|-------|-----------------|
| `meeting-prep` | EA researching attendees, pulling email history, and briefing you before each call |
| `action-items-todoist` | EA reviewing meeting notes, creating follow-up tasks, and drafting emails you promised to send |
| `email-drafting` | EA drafting replies, intro emails, scheduling responses, and thank-you notes in your voice |
| `executive-digest` | EA giving you a morning status update: stalled threads, pending intros, overdue tasks, calendar conflicts |
| `todoist-due-drafts` | EA checking your task list each morning, drafting follow-up/ping emails for anything due today, and notifying you to review |
| `humanizer` | Making sure nothing your Claw writes sounds like AI wrote it (originally by [biostartechnology](https://clawhub.ai/biostartechnology/humanizer)) |

### ECA / chief-of-staff control skills

| Skill | What it does |
|-------|--------------|
| `executive-control-system` | ECA/ECS operating system for more time, less stress, and more control: inbox discipline, decision compression, calendar guardian, open-loop radar, and draft-only control surfaces |
| `daily-inbox-sweep` | Processes an assistant inbox, organizes new items, routes tasks, dedupes alerts, and flags human attention items |
| `daily-standup-prep` | Prepares concise morning standups and end-of-day closeouts from recent work signals, task state, and blockers |
| `weekly-life-admin` | Reviews upcoming personal logistics, appointments, renewals, errands, and week-ahead prep |
| `weekly-competitor-scan` | Scans the AI assistant / productivity market for moves, opportunities, and threats |
| `weekly-content-generation` | Turns recent work, meetings, and notes into weekly social/content drafts |
| `monthly-bill-review` | Reviews expenses and subscriptions, flags anomalies, and produces cancel/dispute/investigate action items |
| `quarterly-review` | Produces a one-page executive review of goals, metrics, wins, misses, patterns, and next-quarter priorities |

## ECA references

The `executive-control-system` skill includes reusable public reference patterns:

- `executive-control-system/references/simple-eca-draft-pad.md` — a simplified ECA draft-pad interface pattern
- `executive-control-system/references/manual-eca-control-center-ui.md` — a manual ECA control-center UI pattern
- `executive-control-system/references/operating-loop-anatomy-feedback-path.md` — the 10-part anatomy of real operating loops
- `executive-control-system/references/daily-brief-open-loop-vs-calendar-load.md` — how to detect when open-loop load matters more than meeting load

Private deployment-specific runtime notes were intentionally not included. This repo is public and should stay portable.

## How it works

Each skill is a markdown file (`SKILL.md`) that tells your Claw exactly how to do the job. Your Claw reads the skill, follows the instructions, and delivers results to WhatsApp, Slack, Telegram, or another configured channel.

Skills run on cron schedules — meeting prep fires before your first meeting, action items run after meetings, digests hit in the morning, and ECA/ECS can run as a daily/weekly control loop. You can also trigger any skill manually by asking your Claw.

All personal config (email accounts, timezone, work schedule, etc.) lives in a single `config/user.json` that's gitignored and never committed.

## Prerequisites

- [OpenClaw](https://docs.openclaw.ai/) running (local or server)
- Gmail / Google Calendar access, commonly through [gog](https://github.com/xhit/gog) CLI
- [Granola](https://granola.ai/) or [Grain](https://grain.com/) for meeting transcripts, commonly via mcporter MCP
- [Todoist CLI](https://github.com/joelhoelting/todoist-cli) or another task tool for task management
- A `style/` directory in your OpenClaw workspace with email style guides (see `docs/setup.md`)

---

## Quick setup

### 1. Clone the repo

```bash
git clone https://github.com/mgonto/executive-assistant-skills.git ~/executive-assistant-skills
```

### 2. Create your config

```bash
cp ~/executive-assistant-skills/config/user.example.json ~/executive-assistant-skills/config/user.json
# Edit user.json with your values — it's gitignored
```

### 3. Tell OpenClaw to load these skills

Edit `~/.openclaw/openclaw.json`:

```json
{
  "skills": {
    "load": {
      "extraDirs": ["~/executive-assistant-skills"]
    }
  }
}
```

### 4. Restart

```bash
openclaw gateway restart
```

### 5. Set up crons

See `docs/crons.md` for ready-to-paste cron job configs.

---

## Config fields

See `config/user.example.json` for the full template:

| Field | Example | Used for |
|-------|---------|----------|
| `name` | `"YourName"` | Meeting transcript queries, task attribution |
| `primary_email` | `"you@gmail.com"` | Gmail account 1 |
| `work_email` | `"you@company.com"` | Gmail account 2 |
| `whatsapp` | `"+123****7890"` | Digest and alert delivery |
| `timezone` | `"America/New_York"` | Meeting times, cron scheduling |
| `scheduling_cc` | `"assistant@company.com"` | CC on scheduling emails |
| `scheduling_silent_cc` | `"colleague@company.com"` | Silent CC (not mentioned in body) |
| `slack_username` | `"yourname"` | Slack DM for meeting briefs |
| `signature` | `"--yourname"` | Email sign-off |
| `workspace` | `"/home/user/.openclaw/workspace"` | Absolute path to your OpenClaw workspace |

---

## Full setup guide

- `docs/setup.md` — complete setup (mcporter, OAuth, gog, Todoist CLI)
- `docs/crons.md` — cron job templates for all skills

---

## Repository conventions

- `config/user.json` is **gitignored** — each person creates their own
- `config/user.example.json` is the committed template
- `state/` and `logs/` are gitignored (machine-local)
- Skills reference workspace files (`style/`, `state/`, `scripts/`) via `{user.workspace}/` prefix for portability
- Public templates should not include private client names, credentials, channel IDs, or deployment-specific runtime logs
