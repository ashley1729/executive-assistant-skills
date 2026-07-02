---
name: daily-standup-prep
description: Prepare concise morning standups and end-of-day closeouts from recent work signals, task state, and blockers.
trigger: cron
schedule: weekdays 8am
persona: meeting-prep
taskType: analysis
priority: normal
---

# Daily Standup Prep

Prepare a daily standup summary for the user's morning.

## Morning standup

1. Review yesterday's activity:
   - completed tasks and queue items
   - meeting notes and action items
   - commits, PRs, or shipped work
2. Review today's calendar for scheduled meetings and deadlines.
3. Check the task list for items due today or overdue.
4. Prepare a concise standup:
   - **Yesterday:** 3–5 bullets of what was accomplished
   - **Today:** 3–5 bullets of what is planned
   - **Blockers:** anything that needs attention or is stuck
5. Keep it tight. The user should be able to read it in 30 seconds.

## EOD closeout variant

Use the same evidence-gathering approach, but change the output shape:

- **What got done** — shipped/completed/verified work
- **What moved** — things that advanced materially even if not finished
- **Blockers** — exact blockers, not vague “still in progress” filler
- **Tomorrow's first priorities** — first 3–4 things to hit next
- **Needs follow-up** — anything the user should explicitly revisit

Preferred evidence sources:

1. latest automation summaries or state files from the day
2. assigned-task snapshots from the task system
3. meeting notes and action items
4. only then a lightweight user prompt

If task context is too thin or unreliable, do not invent a recap. Use:

`🧠 EOD check-in: what shipped today, what moved, what is blocked, and what should be first tomorrow?`
