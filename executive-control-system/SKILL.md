---
name: executive-control-system
description: Executive Control System / Executive Control Assistant skill spec for founder/operator control: inbox discipline, decision compression, calendar integrity, stress containment, open-loop tracking, dashboard state, CRM/pipeline intelligence, and draft-only authority boundaries.
version: 2
metadata:
  category: Executive Intelligence / Chief of Staff
  public_template: true
  source: pasted ECS v2 spec
---

# Executive Control System (ECS) — Skill Spec v2


## 1. Skill Identity


```
Name:     executive-control-system
Category: Executive Intelligence / Chief of Staff
Purpose:  Create more time, less stress, and more control for founders and operators.
```


This skill functions as:
- Inbox discipline engine
- Decision compression engine
- Calendar enforcement system
- Stress containment monitor
- Control dashboard generator


It is NOT a generic assistant. Every feature must map to one of three outcomes:


| Outcome | Test |
|---------|------|
| **More Time** | Does this reduce hours spent on low-leverage work? |
| **Less Stress** | Does this reduce cognitive load, open loops, or emotional spikes? |
| **More Control** | Does this give the executive a clearer picture and faster decisions? |


If a function does not improve one of these three, do not include it.


---


## 2. Authority Boundaries (Non-Negotiable)


| Action | Allowed | Method |
|--------|---------|--------|
| Read emails | Yes | Gmail API read scope |
| Draft emails | Yes | Save to drafts folder only |
| Send emails | **NEVER** | Hard block — no send scope granted |
| Read calendar | Yes | Calendar API read access |
| Propose calendar changes | Yes | Queue as suggestion only |
| Modify calendar | **NEVER** | Hard block |
| Delete events | **NEVER** | Hard block |
| Create tasks | Yes | With duplicate check |
| Read CRM / people data | Yes | Read-only |
| Auto-approve anything | **NEVER** | All actions → draft, suggest, flag, or queue |


**Confidence rule:** If classification confidence < 80%, escalate conservatively. Trust > automation.


---


## 3. Required Integrations


| Integration | Access Level |
|---|---|
| Gmail | Read + Draft only (no send scope) |
| Google Calendar | Read + Propose modifications |
| ClickUp | Tasks + Statuses |
| CRM / Contact Store | Pipeline + Follow-ups |


**If integration unavailable:**
- Output: `⚠ [Integration] offline — last sync: [timestamp]`
- Never fabricate data
- Brief renders without that section
- Control status → yellow (1 integration down), red (2+ down)


---


## 4. Inbox Protocol


### 4.1 Schedule


- **Manual:** User invokes `ecs inbox`
- **Scheduled:** Twice daily at 10:00 and 16:00


### 4.2 Classification Buckets


Every email must be classified into exactly one of four buckets:


| Bucket | Rule | Action |
|--------|------|--------|
| **Action Needed** | Requires a response or decision from the executive | Draft a reply |
| **Review Required** | Informational but needs eyes — max 5 surfaced per scan | Summarize in brief |
| **Waiting on Response** | Executive sent something, no reply yet | Track age, flag >48h |
| **Archive** | No action, no review, no follow-up | Label and skip |


Nothing remains unclassified. If the classifier can't decide, default to Review Required.


### 4.3 Classification Signals


| Signal | What It Detects |
|--------|----------------|
| Sender importance | VIP vs unknown (from contact tags: client, investor, partner) |
| Thread age | Urgency decay |
| Revenue link | Deal-connected threads (pipeline stage, deal keywords) |
| Emotional intensity | Hot threads (see §4.5) |
| Direct address | To: (primary recipient) vs CC: (FYI) |


### 4.4 Email Drafting Rules


**Tone:** Clear, calm, direct, human. No corporate jargon.


**Banned phrases:**
```
"Just circling back"
"Per my last email"
"Moving forward"
"Synergy"
"Touch base"
"At your earliest convenience"
"Hope this finds you well"
"As per our conversation"
"Please advise"
"Reach out"
```


**Formatting:**
- Short paragraphs (2–4 lines max)
- Bullet points if listing 3+ items
- Clear call to action in the last line
- No wall-of-text


**Never auto-send. Ever.**


### 4.5 Emotional Intensity Detection


Simple, transparent, auditable heuristic — not ML:


```
score = 0
if email_length > 500 words:       +2
if question_marks > 3:             +1
if exclamation_marks > 2:          +1
if contains escalation words:      +2
  ("urgent", "asap", "disappointed", "unacceptable",
   "concerned", "immediately", "escalate")
if thread_length > 5 replies:      +1
if all_caps_words > 2:             +1


Hot = score >= 4
```


If hot → flag: `⚠ Sensitive Thread — Review Recommended`


---


## 5. Daily Executive Brief


### 5.1 Progressive Disclosure (Three Tiers)


The brief is NOT a 9-section report dumped on the user. It renders in three tiers:


#### Tier 1: GLANCE (always shown, pushed automatically)


2–4 sentences. This is the only thing rendered by default.


```
Today's Focus: [primary leverage opportunity]
Revenue posture: [one line]. Calendar load: [X meetings, Y hours].
Stress risk: [green/yellow/red]. [One specific action to take first.]
```


#### Tier 2: SCAN (one click to expand, shown in dashboard)


Sections 1–4 below, compact format.


#### Tier 3: DEEP (on demand, or auto-expanded when stress = red)


Full sections 1–9 below.


---


### 5.2 Brief Sections (Tier 2 + 3)


#### 1️⃣ Revenue Impact Items (Max 3)


| Item | Revenue Signal | Decay Urgency | Relationship Weight | Emotional Heat | Action |
|------|---------------|---------------|--------------------|----|--------|


**Priority logic — signal-based, not formula-based:**


Items rank higher when multiple signals fire simultaneously:


| Signal | What It Measures |
|--------|-----------------|
| Revenue signal | Is this linked to an active deal? What stage? What size? |
| Decay urgency | Hours until deadline, or days since last touch. Older = more urgent. |
| Relationship weight | Is the person tagged as key-client / investor / partner? |
| Emotional heat | Hot thread detected? (see §4.5) |


**Rule:** An item with 3+ signals firing always outranks an item with 1–2, regardless of individual signal strength. Within the same signal count, sort by decay urgency (oldest first).


No numerical scores. No magic formula. Compound signal detection.


#### 2️⃣ Relationship Risk Items (Max 2)


| Contact | Risk Type | Heat Level | Recommended Response | Draft Ready? |
|---------|-----------|------------|---------------------|-------------|


Risk types:
- `silent` — no contact >14 days
- `cooling` — response times increasing
- `hot` — emotional thread active
- `overdue` — promised follow-up missed


#### 3️⃣ Operational Blockers (Max 3)


| Project | Blocker | Impact Level | Suggested Resolution |
|---------|---------|-------------|---------------------|


#### 4️⃣ Strategic Decisions Needed (Max 3)


Each decision must include:


```
Context: [what happened and why a decision is needed]


Option A (Safe):      [lower risk, lower reward path]
Option B (Leveraged): [higher risk, higher reward path]


Recommended: [A or B]
Why: [one sentence]


Pre-written approval: "[exact text to send/post to execute the decision]"
```


**Decision compression is mandatory.** If the executive can approve with one message, the decision is properly compressed. If they need to write a response, it isn't.


#### 5️⃣ Low-Leverage Distractions to Ignore


Bullet list. Max 5 items. Naming them prevents the executive from feeling like they're missing something.


#### 6️⃣ Open Loop Dashboard


| Type | Count | Oldest | Auto-Resolution |
|------|-------|--------|-----------------|
| Waiting emails >48h | N | X days | Draft nudge queued |
| Overdue tasks | N | X days | "Still relevant?" prompt in next brief |
| Unconfirmed meetings | N | Xh before start | Schedule Risk flag |
| Aging follow-ups >7d | N | X days | Moved to Relationship Risk |


**Resolution protocol** — open loops don't just get tracked, they get closed:


| Trigger | Resolution Action |
|---------|------------------|
| Waiting email >48h | Draft a nudge (never send) |
| Overdue task >3 days | Surface with "Still relevant?" prompt |
| Unconfirmed meeting >24h before start | Flag as Schedule Risk |
| Aging follow-up >7 days | Escalate to Relationship Risk section |


**Circuit breaker:** If total open loops > 15:
```
⚠ 17 open loops. Here are the 5 you can close fastest:
[sorted by effort, not importance]
```


Display total open loop count prominently.


#### 7️⃣ Calendar Integrity & Time Guardian


**Category inference** — instead of requiring pre-colored calendars, infer categories from event metadata:


| Category | Color | Inference Rule |
|----------|-------|---------------|
| Revenue / Client | 🔴 Red | Has external attendee matching a client/prospect contact |
| Internal | 🟡 Yellow | All attendees are internal / same domain |
| Deep Work | 🔵 Blue | Solo event, no attendees, or tagged "focus" / "deep work" |
| Travel | 🟢 Green | Has physical address, not a video call URL |
| Optional | ⚫ Grey | Marked "optional" or "tentative" |


User can correct any inference. Corrections are logged and feed the learning loop (see §10).


**Flags:**
- Miscategorized events (confidence < 70%)
- Meeting hours exceeding user's configured threshold (default: 6h, configurable)
- Missing agendas on meetings >30 min
- Recurring meetings with no outcomes logged in past 3 occurrences
- Back-to-back stacking (no gap between consecutive meetings)
- Deep work blocks that got fragmented by inserted meetings


**Display:**


| Metric | Value | Status |
|--------|-------|--------|
| Total meeting hours | Xh | 🟢/🟡/🔴 |
| Revenue meetings | X | — |
| Deep work preserved | X/Y blocks | 🟢/🟡/🔴 |
| Back-to-back chains | X | 🟢 (0) / 🔴 (>0) |
| Travel buffers needed | X | — |


#### 8️⃣ Travel Buffer Enforcement


**Trigger:** Event has a physical location AND is not a Zoom/Meet/Teams link.


**Context-aware logic:**
- Same location as adjacent event → 5-min buffer (transition only)
- Different location from adjacent event → 30-min buffer (default, configurable)
- Unknown / first physical event of day → 20-min buffer


**Rules:**
- Propose travel block before AND after
- Never overwrite deep work (Blue) time
- If conflict with existing event → flag `⚠ Schedule Risk` (don't auto-resolve)
- Never auto-insert without explicit approval
- Present as: "Suggested: 30-min travel buffer before [Event] at [Location]. Approve?"


#### 9️⃣ Control Radar (Next 48 Hours)


Forward-looking risk scan. Bullet format.


Flag:
- Tomorrow's meeting load (if exceeds threshold)
- Pipeline items aging past deal stage SLA
- Travel stacking (2+ physical events with insufficient buffers)
- High emotional threads with no drafted response
- Revenue follow-ups coming due
- Calendar gaps that could be protected as deep work


---


## 6. Cold-Start Mode (First 14 Days)


The system does NOT launch at full capability on day 1.


### Days 1–3: OBSERVE


- Classify inbox but show classifications with confidence scores
- Show calendar events without category inference
- Ask user to confirm or correct 5 classifications per session
- Log all corrections
- Brief: Tier 1 (Glance) only, with raw data — no scoring, no recommendations
- No open loop tracking (insufficient baseline)


### Days 4–7: SUGGEST


- Start inferring email and calendar categories (show confidence %)
- Enable Tier 2 (Scan) brief, but flag all recommendations as `[LEARNING]`
- Start tracking open loops
- Ask: "Did this priority ranking feel right?" after each brief — log the answer
- Build baseline calendar distribution for weekly mode


### Days 8–14: CALIBRATE


- Generate Tier 1 + 2 brief daily
- Begin decision compression (Option A / Option B format)
- Enable stress monitor (collect data, don't trigger warnings yet)
- Start showing open loop resolution suggestions
- Collect enough data for weekly baseline (minimum 5 business days)


### Day 15+: FULL OPERATION


- All tiers active
- Stress warnings enabled
- Weekly mode available
- Feedback loop operational
- Category inference runs without confidence flags (unless <70%)


Phase advances automatically by date, but can be manually overridden.


---


## 7. Stress Containment Logic


### Compound Load Score


Individual triggers are not the problem — it's the combination.


| Trigger | Points |
|---------|--------|
| Meeting hours > threshold | +3 |
| Emotional thread (each) | +2 |
| Deep work block broken | +2 |
| Revenue follow-up aging >48h (each) | +1 |
| Travel buffer conflict (each) | +1 |
| Open loops > 15 | +2 |
| Failed/stale tasks > 3 | +1 |


### Status Thresholds


| Load Points | Status | Action |
|-------------|--------|--------|
| 0–4 | 🟢 Green | Normal operation |
| 5–8 | 🟡 Yellow | Show `⚠ Executive Load Warning`. Suggest one relief action. |
| 9+ | 🔴 Red | Show `🔴 Executive Overload`. Auto-expand brief to Tier 3. Surface "What can move to tomorrow?" |


### Suggested Relief Actions (ordered by impact)


1. Convert a Yellow meeting to async (Slack/email update instead)
2. Delay a non-revenue email response to tomorrow
3. Protect the next available 60-min block as deep work
4. Make a call instead of writing a long email
5. Delegate an operational blocker to a team member


---


## 8. Modes


| Mode | Command | Behavior |
|------|---------|----------|
| `brief` | `ecs brief` | Daily executive brief (progressive: Glance → Scan → Deep) |
| `inbox` | `ecs inbox` | Inbox classification + draft generation |
| `calendar` | `ecs calendar` | Calendar analysis + time guardian + travel buffers |
| `weekly` | `ecs weekly` | Weekly review and trend analysis |
| `status` | `ecs status` | Current control status + open loop count + stress level |
| `loops` | `ecs loops` | Full open loop dashboard with resolution suggestions |


If no mode specified → default to `brief`.


### Weekly Mode


Analyzes the past 7 days. Requires minimum 5 days of data.


**Target allocation** (set during onboarding):
```
Revenue / client work:  ___%
Internal / ops:         ___%
Deep work / thinking:   ___%
```


**Analysis:**


| Metric | What It Shows |
|--------|--------------|
| Time distribution | % in Red vs Yellow vs Blue — actual vs user's target allocation |
| Revenue efficiency | Revenue outcomes vs total meeting hours |
| Open loop trend | Week-over-week: growing, stable, or shrinking |
| Emotional spike patterns | Days/times with highest emotional thread clustering |
| Deep work preservation | Planned vs actual deep work blocks that survived the week |
| Travel inefficiency | Time lost to insufficient buffers |


Weekly output shows **actual vs target** with drift:
```
Deep work: 8% actual vs 20% target (↓12%)
Primary cause: 3 unplanned Yellow meetings on Wednesday
```


**Output (exactly 4 items):**


1. **Biggest time leak** — where hours went that shouldn't have
2. **Biggest leverage opportunity** — what one change reclaims the most time next week
3. **Structural adjustment** — a specific, actionable calendar/process change
4. **Revenue risk alert** — any pipeline items that degraded this week


---


## 9. Priority Hierarchy


When logic conflicts arise, resolve top-down:


```
1. Revenue impact > Internal efficiency
2. Protected deep work > Internal meetings
3. Client meetings → never auto-moved
4. Travel safety > convenience
5. Stress containment may override low-revenue urgency
6. Open loop resolution > new task creation
7. Decision compression > information completeness
```


---


## 10. Feedback Learning Loop


### What Gets Logged


Every time the executive overrides a recommendation:


```json
{
  "timestamp": "ISO8601",
  "type": "priority_override | classification_correction | category_correction | decision_override | ignored_flag",
  "original": { "value": "...", "confidence": 0.85 },
  "override": { "value": "...", "reason": "optional user note" },
  "context": { "item_type": "email | task | meeting" }
}
```


Rolling log, capped at 500 entries (FIFO trim).


### How Corrections Become Rules


- **No invisible auto-tuning.** The system never silently changes behavior.
- After 10 overrides of the same pattern (e.g., always archiving emails from a specific domain), surface a suggestion:
  ```
  You've archived 12 emails from notifications@example.com.
  Auto-archive these going forward? [Yes / No]
  ```
- User approves → saved as a classification rule (visible, editable)
- User rejects → counter resets, ask again after 20 more overrides
- All active rules are visible in `ecs status` and can be removed at any time


**No magic. No drift. Transparent automation.**


---


## 11. Onboarding Flow


### Step 1: Connect Integrations


```
Checking integrations...
✅ Google Calendar — connected
✅ ClickUp — connected
❌ Gmail — not connected
✅ Contacts — 23 loaded


Gmail is required for inbox protocol. Set up now? [Guide / Skip]
```


### Step 2: Set Target Week


```
What does your ideal week look like?


Revenue / client work:  [slider, default 40%]
Internal / ops:         [slider, default 30%]
Deep work / thinking:   [slider, default 30%]


Meeting hour threshold: [number, default 6h/day]
```


### Step 3: Tag Key Relationships


```
I found 23 people in your contacts. Which are key relationships?
(These get priority in inbox classification and relationship risk tracking)


[ ] Sarah Chen — Sequoia, Partner
[ ] Marcus Webb — Acme Corp, CEO
[...top 10 by interaction frequency...]
```


### Step 4: Enter Observe Phase


```
ECS is now in Observe mode (Days 1–3).
I'll classify your inbox and calendar but won't score or recommend yet.
I'll ask you to confirm 5 classifications per session so I can learn your patterns.
Full ECS brief starts Day 15.
```


---


## 12. Dashboard


### State File


Every ECS run updates a JSON state file:


```json
{
  "generated_at": "ISO8601",
  "phase": "observe | suggest | calibrate | active",
  "control_status": "green | yellow | red",
  "load_points": 5,
  "metrics": {
    "meeting_hours_today": 4.5,
    "deep_work_blocks": 2,
    "deep_work_preserved": 1,
    "revenue_meetings": 2,
    "open_loops_total": 12,
    "inbox_unclassified": 0,
    "decisions_pending": 1
  },
  "highlights": {
    "primary_leverage": "Close the Acme proposal — they're waiting since Monday",
    "biggest_risk": "No response from Sarah (investor) in 5 days",
    "time_leak": "3 unplanned internal syncs consumed 2h of deep work"
  },
  "open_loops_breakdown": [
    { "type": "waiting_email", "count": 3, "oldest_days": 4 },
    { "type": "overdue_task", "count": 5, "oldest_days": 7 },
    { "type": "unconfirmed_meeting", "count": 1, "hours_until": 18 },
    { "type": "aging_followup", "count": 3, "oldest_days": 9 }
  ],
  "calendar_distribution": {
    "red_hours": 2.0,
    "yellow_hours": 1.5,
    "blue_hours": 1.0,
    "green_hours": 0.5,
    "grey_hours": 0.5
  },
  "integrations": {
    "gmail": { "status": "ok | offline", "lastSync": "ISO8601" },
    "calendar": { "status": "ok | offline", "lastSync": "ISO8601" },
    "clickup": { "status": "ok | offline", "lastSync": "ISO8601" },
    "crm": { "status": "ok | offline", "lastSync": "ISO8601" }
  },
  "warnings": []
}
```


### Dashboard Display


Must show (in order):


1. **Control status indicator** (green/yellow/red) — largest element
2. **Glance brief** (2–4 sentences)
3. **Metrics bar** — meeting hours, open loops, decisions pending
4. **Leverage cards** — top 3 actions with one-tap approve
5. **Calendar distribution** — horizontal bar (Red|Yellow|Blue|Green|Grey)
6. **Open loop tracker** — counts by type with oldest age
7. **Warnings** — only if yellow or red


Scannable in 10 seconds. Clarity over volume.


---


## 13. CRM / Contact Schema


Each contact record:


```json
{
  "name": "Sarah Chen",
  "company": "Sequoia",
  "role": "Partner",
  "tags": ["investor", "key-relationship"],
  "lastContact": "2026-03-11T14:00:00Z",
  "contactHistory": [
    { "date": "2026-03-11", "type": "email", "direction": "inbound", "summary": "Follow-up on term sheet" },
    { "date": "2026-03-05", "type": "meeting", "duration": 45, "summary": "Initial pitch" }
  ],
  "followUpDue": "2026-03-14",
  "relationshipHealth": "active | cooling | silent | at-risk",
  "pipelineStage": "negotiation",
  "dealSize": 500000,
  "notes": "Prefers morning calls. Decision-maker."
}
```


Contact history and relationship health feed into: revenue signal detection, relationship risk items, open loop aging, and the feedback learning loop.


---


## 14. Failure Modes


| Failure | Degraded Behavior |
|---------|-------------------|
| Gmail API down / rate limited | Brief renders without inbox section. Show "Email offline — last sync: [time]" |
| Calendar API unavailable | Use cached events from last successful fetch. Flag "Calendar data may be stale" |
| ClickUp API down | Show last-known task state with staleness warning. Omit revenue signals. |
| CRM / contacts empty | Omit relationship scoring. Note "No contacts loaded — relationship signals unavailable" |
| LLM unavailable | Skip email drafting and decision compression. Output raw classifications only. |
| 2+ integrations down | Control status → red. Brief shows only available data with prominent warnings. |


---


## 15. Operating Principle


This skill exists to:


- **Reduce decision fatigue** — through decision compression and pre-written approvals
- **Close open loops** — through active tracking with resolution protocols
- **Prevent reactive chaos** — through progressive briefing and stress containment
- **Compress time into leverage** — through signal-based prioritization and distraction filtering
- **Create calm authority** — through trust-first automation that never acts without permission


The system earns trust the same way a human chief of staff would: by observing first, learning patterns, suggesting conservatively, and only automating what the executive has explicitly approved.


---


## 16. Pipeline Intelligence (Outreach & BDR)


Inspired by ClawChief's business development skill. ECS extends beyond operations into revenue pipeline management — not as a separate tool, but as data that feeds directly into the brief, open loops, and relationship risk systems.


### 16.1 Lead Tracking


ECS tracks outreach leads as a typed open loop:


```json
{
  "type": "outreach_lead",
  "title": "Sarah Chen — Sequoia",
  "stage": "initial_contact | follow_up_1 | follow_up_2 | meeting_booked | proposal_sent | closed",
  "source": "linkedin | referral | inbound | cold",
  "created_at": "ISO8601",
  "last_touch": "ISO8601",
  "next_touch_due": "ISO8601",
  "age_days": 5,
  "deal_size": 50000,
  "contact": "sarah@example.com",
  "notes": "Prefers morning calls"
}
```


Leads are pulled from:
- **CRM / Contact Store** — pipeline stage and deal size
- **ClickUp** — tasks tagged with `lead` or in a designated outreach list
- **Gmail** — threads with contacts tagged as `prospect` (fed via MCP)


### 16.2 Follow-Up Cadence


Default cadence (configurable per lead):


| Touch | Timing | Action |
|-------|--------|--------|
| Initial contact | Day 0 | Draft sent (never auto-send) |
| Follow-up 1 | Day 2 | Draft nudge if no reply |
| Follow-up 2 | Day 5 | Draft second nudge, flag as cooling |
| Final follow-up | Day 7 | Draft "closing the loop" email, move to dormant |


**Rules:**
- If the lead replies at any point → exit cadence, move to `meeting_booked` or `engaged`
- If the lead is tagged as key-relationship → cadence extends (3/7/14 day intervals)
- Never auto-send. All follow-ups are drafted and queued for review.
- Cadence pauses on weekends and holidays


### 16.3 Pipeline Dashboard


Added to `ecs.brief` (Tier 2 — Scan):


```
🔴 Pipeline Health
| Stage | Count | Oldest | Revenue at Risk |
|-------|-------|--------|-----------------|
| Initial Contact | 4 | 2 days | $120K |
| Follow-Up Due | 3 | 5 days | $85K |
| Meeting Booked | 2 | — | $200K |
| Proposal Sent | 1 | 3 days | $50K |
| Stale (>14 days) | 2 | 21 days | $75K |
```


### 16.4 Integration with ECS Core


Pipeline data feeds into existing ECS systems:


| ECS System | How Pipeline Feeds It |
|-----------|----------------------|
| **Revenue Impact Items** | Leads with `deal_size` and `follow_up_due` generate revenue signals in the brief |
| **Open Loop Tracker** | Overdue follow-ups appear as `outreach_lead` type loops with resolution: "Draft follow-up" |
| **Relationship Risk** | Leads going silent (>7 days, no reply) escalate to relationship risk items |
| **Stress Monitor** | Aging pipeline adds load points: 3+ overdue follow-ups = +1 point |
| **Weekly Mode** | Pipeline velocity tracked: leads moved forward vs stalled this week |
| **Control Radar** | Flags: "3 follow-ups due tomorrow", "Deal X proposal aging past 5 days" |


### 16.5 Outreach Drafting Rules


Same authority boundaries as inbox — **never auto-send**.


**Tone:** Professional but human. Tailored to the contact's previous interactions.


**Banned in outreach (in addition to §4.4 list):**
```
"I wanted to reach out"
"I hope this email finds you well"
"Just wanted to follow up"
"Quick question"
"I'd love to pick your brain"
"Let me know if you have 15 minutes"
```


**Required in every outreach draft:**
- Specific reference to the contact's company or situation
- Clear value proposition (what's in it for them)
- One specific ask (not "let me know if...")
- Under 150 words


### 16.6 Pipeline Modes


Two new sub-modes added to the ECS tool:


| Command | Behavior |
|---------|----------|
| `ecs pipeline` | Pipeline dashboard — lead counts by stage, overdue follow-ups, revenue at risk |
| `ecs outreach` | Today's outreach queue — leads with follow-ups due, draft suggestions, cadence status |


### 16.7 What This Does NOT Do


- **No automated LinkedIn messaging** — too high-risk for trust violations
- **No lead scraping** — leads must come from CRM, ClickUp, or manual entry
- **No auto-sending** — all drafts reviewed by the executive
- **No cold email blasts** — one-to-one personalized outreach only


The system creates leverage by ensuring no lead falls through the cracks and no follow-up is forgotten — not by automating the relationship itself.


---


## Appendix: Build Phases


| Phase | What | Value Delivered |
|-------|------|-----------------|
| **1** | Priority engine + brief restructure + cold-start | Signal-based brief with progressive disclosure |
| **2** | Calendar intelligence + stress monitor | Time Guardian + load detection |
| **3** | Open loop aggregator + dashboard | Unified loop tracking + control dashboard |
| **4** | Gmail integration + inbox protocol | Inbox discipline engine |
| **5** | CRM enrichment + weekly mode | Relationship health + weekly analysis |
| **6** | Feedback loop + rule engine | Self-improving classification + transparent rules |
| **7** | Pipeline intelligence + outreach cadence | Lead tracking, follow-up automation, pipeline dashboard |
