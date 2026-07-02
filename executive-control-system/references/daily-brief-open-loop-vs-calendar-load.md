# Daily Brief Runtime Note — Open-loop Load Can Outrank Calendar Load

Use this when `ecs brief` shows a calm calendar but the founder still feels underwater.

## Proven pattern

1. Pull the primary calendar for the next 48 hours and compute:
   - meeting count
   - meeting hours
   - back-to-back transitions under 15 minutes
   - protected/focus block coverage

2. Pull a bounded inbox window with high-volume noreply exclusions first, then hydrate only priority human threads.

3. Pull assigned tasks and separate:
   - due next 48h
   - overdue
   - no due date
   - stale 7d+ since last update

4. If CRM/contact data is unavailable, explicitly mark it offline and infer relationship risk from inbox + tasks only. Do not overstate confidence.

## Control-status heuristic

A light calendar does not imply control.

If meetings are manageable but all of the following are true, control can still be red:

- multiple active trust / relationship-risk threads
- heavy overdue or due-soon task load
- large stale-task backlog
- compliance / finance items drifting without dates

Also flag immediate friction separately when the primary calendar contains same-time overlaps even if total meeting hours are low. That is a scheduling-integrity problem, not a calendar-volume problem.

## Good executive-facing wording

- “Calendar pressure is light, but open-loop pressure is not.”
- “The bottleneck is spillover from task load, not meetings.”
- “Best leverage move: close one client-trust package, one renewal decision, and one reporting batch before taking on anything new.”

## Why this matters

Without this distinction, the brief can incorrectly reassure the user because the calendar looks clean while the real stressor is unresolved delivery, reporting, and relationship-confidence work.
