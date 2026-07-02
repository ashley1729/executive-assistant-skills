---
name: weekly-content-generation
trigger: cron
schedule: weekly tuesday 9am
persona: content-writer
taskType: creative
priority: normal
---

# Weekly Content Generation

Generate this week's content based on recent activity, meetings, and notes.

## Steps

1. Review the past 7 days of notes, meeting summaries, and shipped work.
2. Identify 3–5 interesting topics, insights, or lessons learned.
3. Create:
   - 5 short social posts
   - 1 blog post outline
   - 1 newsletter draft, if relevant
4. Make the content sound like the user, not like AI.
5. Reference specific events, meetings, lessons, or examples from the week.

## Output format

```markdown
# Weekly Content Pack — <date>

## Themes
1. ...

## Social posts
### Post 1
...

## Blog outline
...

## Newsletter draft
...
```

## Guardrails

- Do not invent accomplishments or metrics.
- If source context is thin, ask for a topic or produce topic prompts instead of fake posts.
- Keep claims grounded in actual notes or provided context.
