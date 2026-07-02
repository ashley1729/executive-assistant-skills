---
name: weekly-life-admin
trigger: cron
schedule: weekly sunday 7pm
persona: life-admin
taskType: task
priority: normal
---

# Weekly Life Admin Review

Review the upcoming week and flag personal logistics that need attention.

## Steps

1. Check the calendar for the next 7 days:
   - appointments that need preparation
   - documents, directions, or items to bring
   - scheduling conflicts or tight transitions
2. Review recurring obligations:
   - bills due this week
   - subscriptions renewing
   - registrations or licenses expiring within 30 days
3. Check upcoming dates:
   - birthdays or anniversaries in the next 14 days
   - holidays or closures that affect scheduling
4. Review pending errands or tasks from the previous week.
5. Summarize as a checklist organized by day, with the most time-sensitive items first.

## Output format

```markdown
# Weekly Life Admin — <week>

## Time-sensitive
- <item> — <deadline> — <next action>

## By day
### Monday
- ...

## Prep needed
- ...

## Can wait
- ...
```
