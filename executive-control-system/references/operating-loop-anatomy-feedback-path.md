# Operating Loop Anatomy + Feedback Path

Use this when designing, auditing, or improving ECA/ECS operating loops. A real loop is more than a recurring reminder.

## 10-part loop anatomy

1. **Outcome** — What result are we protecting or improving?
2. **Trigger / cadence** — When does the loop run?
3. **Inputs** — What does the agent read?
4. **State** — Where does the loop remember open, done, waiting, or dropped items?
5. **Decision rules** — How does the agent decide what matters, what to ignore, what to escalate, and what to route?
6. **Output** — What does the loop produce?
7. **Owner / channel** — Who sees the output, where, and when?
8. **Approval boundary** — What can the agent do automatically vs. what needs human approval?
9. **Health signal** — How do we know the loop is working or failing?
10. **Feedback / improvement path** — How does the loop get better when the user corrects it?

## Teaching lines

- A loop without state is just a reminder.
- A loop without feedback is just a workflow.
- A loop without a health signal is a future silent failure.

## Recommended self-improvement loop

**Weekly ECA Self-Improvement Review**

- **Outcome:** reduce repeated friction; keep the assistant aligned; turn repeated workflows into skills/crons; keep memory clean.
- **Cadence:** weekly, plus after corrections, complex tasks, repeated workflows, or skill/cron failures.
- **Inputs:** recent sessions, corrections, failed assumptions, tool/cron errors, skill usage/failures, current memory, previous loop state.
- **State:** self-improvement ledger for open/waiting/done/dropped improvements; durable memory for preferences; skills for reusable procedures; crons for recurring checks.
- **Decision rules:** save durable facts to memory; patch/create skills for reusable workflows; propose crons only when recurrence reduces load; escalate external/high-stakes actions; skip temporary/noisy items.
- **Output:** concise review with Learned / Updated / Proposed / Needs approval / Skipped.
- **Approval boundary:** automatic drafting, recommendations, obvious skill patches, and clear durable memory updates are allowed; external sends/posts, client-facing records, high-stakes commitments, noisy recurring automations, and destructive restructures require approval.
- **Health:** dated review exists; corrections decrease; skills get patched after failures; crons report real workflow success; missing inputs are flagged; memory does not accumulate stale task noise.
