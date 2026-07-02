---
name: daily-inbox-sweep
description: Process an assistant inbox, organize new items, route tasks, and flag anything that needs human attention.
trigger: cron
schedule: daily 7am
persona: ops-runner
taskType: ops
priority: normal
---

# Daily Inbox Sweep

Process the assistant inbox and organize new items.

## Steps

1. Check the configured inbox directory or inbox integration for new items.
2. For each item:
   - Read the content.
   - Categorize it as agent output, note, task, reference, alert, or unknown.
   - If it is an agent output, check whether it has a corresponding queue item and summarize the result.
   - If it is a note, move or suggest moving it to the appropriate knowledge/vault folder.
   - If it is a task, verify owner, due date, and duplicate status before creating or updating anything.
   - If it is an alert, dedupe against existing tasks and route only one clear follow-up item.
3. Create a brief summary of what was processed.
4. Flag items that need user attention.

## Dedupe rule

Never create multiple tasks for the same underlying issue. Search the task system first, match by client/person/topic/date, and update the existing item when possible.

## Output format

```markdown
# Daily Inbox Sweep — <date>

## Processed
- <item> — <category> — <action taken>

## Needs attention
- <item> — <why it matters> — <recommended next step>

## Skipped / duplicates
- <item> — <reason>
```

## Safety

- Do not send external messages automatically.
- Do not delete source items unless explicitly configured.
- If categorization confidence is low, put the item in `Review Required`.
