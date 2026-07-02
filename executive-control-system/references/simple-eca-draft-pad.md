# Simple ECA Draft Pad Pattern

Use this when the ECA system should improve work in the moment, especially when a dashboard would be too heavy.

## Preferred interaction model

Keep the app to two panels:

1. **Input**
   - `What is the main thing?`
   - `Paste the mess`
   - `What do you need from ECA?` selector
   - optional `Tone` and `Pressure` selectors
   - primary button: `Make ECA draft`

2. **ECA Draft**
   - one large editable output box labelled `ECA Draft`
   - nearby buttons: `Copy ECA draft`, `Turn into prompt`
   - a short note: “This is where your draft goes. Edit it here, then copy it into chat, email draft, Slack draft, ClickUp comment, or your daily brief. Nothing is sent automatically.”

## Avoid

- full dashboard as the first artifact
- many metrics or cards
- radar/mode tabs unless explicitly requested
- duplicate copy buttons far away from the draft output
- terminal-like or overly technical aesthetics if the user asked for calm/simple
- over-explaining in long blocks

## Draft output template

```text
ECA DRAFT

MAIN FOCUS
{main}

WHAT MATTERS
- Pull out the work with real impact.
- Separate urgent noise from actual priority.
- Protect time for the highest-leverage action.

CONTEXT
{messy_context}

CONTROL CHECK
Pressure: {pressure}
Tone: {tone}

NEXT 3 ACTIONS
1. Identify the one item with revenue, client, or deadline impact.
2. Move or draft the smallest visible next step.
3. Defer anything that does not improve time, stress, or control.

DRAFT-ONLY RULE
Do not send anything automatically. Draft, suggest, or queue only.
```

## Verification checklist

- The page has a clear headline and draft-only reassurance.
- The input flow can be completed in under one minute.
- The output is an editable draft box, not a hidden generated field.
- Draft copy/export controls are adjacent to the draft box.
- The user can answer “where does my draft go?” by looking at the page.
