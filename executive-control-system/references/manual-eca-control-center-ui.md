# Manual ECA Control Center UI Pattern

Use this reference when creating an interface for ECA / ECS / Executive Control Assistant.

## Correct framing

Center every artifact around ECS outcomes:

- More Time
- Less Stress
- More Control

The interface should feel like a control system / chief-of-staff surface, not a generic task app.

## Recommended manual front-end modules

1. **Control status**
   - Green / Yellow / Red status
   - Stress load points
   - Open control item count
   - Time reclaimed / loops closed

2. **Start-here strip**
   - Paste context
   - Add open loops
   - Mark stress
   - Compress decisions
   - Copy packet to ECA

3. **ECA mode selector**
   - Brief
   - Loops
   - Calendar
   - Inbox
   - Weekly

4. **Daily ECA brief generator**
   - Tier 1: Glance
   - Tier 2: Scan
   - Tier 3: Deep
   - Next Best Action

5. **Open loop dashboard**
   - Revenue impact
   - Relationship risk
   - Operational blockers
   - Waiting on response
   - Low-leverage distractions to ignore

6. **Stress containment**
   - Heavy meeting day
   - Hot thread / emotional escalation
   - Broken deep work
   - Aging revenue follow-up
   - Travel/buffer risk
   - Stale tasks/open loops

7. **Decision compression**
   - Each decision should become one approvable ask.
   - Buttons must be clearly labeled.

8. **Control radar: next 48h**
   - Protected time
   - Revenue risks
   - Relationship risks
   - Stale loops

9. **ECA packet builder**
   - Copy a structured packet into chat.
   - Restate hard boundaries: draft/suggest/queue only; never auto-send email; never create/modify/delete calendar events; never auto-approve.

## Design pitfalls

- Do not build a generic productivity dashboard if the user says they have ECA/ECS.
- Do not make the deliverable a show-and-tell artifact if the user asks for something to improve work.
- Add a visible “Start here” flow; ECA tools are often used when the user is overloaded.
- Avoid cramped or unlabeled controls; tired users need obvious affordances.
- Keep privacy/local-only caveats visible when making standalone local HTML tools.

## Good positioning line

“This is the manual front-end for the ECA brain: what needs attention, what can wait, what is causing stress, and what decision would unlock the most control?”
