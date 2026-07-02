---
name: monthly-bill-review
trigger: cron
schedule: monthly 1st 9am
persona: finance-admin
taskType: analysis
priority: normal
---

# Monthly Bill Review

Review the past month's expenses and financial activity.

## Steps

1. Gather available financial data for the previous month.
2. Categorize expenses:
   - subscriptions
   - utilities
   - one-time purchases
   - business
   - personal
3. Flag:
   - charges significantly higher than usual
   - new subscriptions or recurring charges
   - duplicate or suspicious charges
   - subscriptions the user may have forgotten about
4. Compare total spend against the previous month and 3-month average.
5. Summarize in a clean table with categories, amounts, and month-over-month change.
6. End with action items: cancel, dispute, investigate, or keep.

## Output format

```markdown
# Monthly Bill Review — <month>

## Snapshot
| Category | This month | Previous month | Change | Notes |
|---|---:|---:|---:|---|

## Flags
- ...

## Action items
- [ ] ...
```

## Safety

- Read-only unless explicitly authorized.
- Do not cancel, dispute, or pay anything automatically.
- If data is incomplete, label the missing sources clearly.
