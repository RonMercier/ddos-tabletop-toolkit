# Exercise Facilitator Guide

**How to run a DDoS tabletop exercise — even if you've never facilitated one before.**

---

## Before the Exercise

### Choose the right scenario

| If the team is... | Start with... |
|---|---|
| New to tabletops | Scenario 01 (Volumetric) |
| Has CDN in place | Scenario 02 (Layer 7) |
| Security-mature | Scenario 03 (Smokescreen) |
| Cloud infrastructure | Scenario 04 (Economic DoS) |
| Annual full exercise | Scenario 05 (Multi-Vector) |

### Invite the right people

Minimum viable group:
- The person who would be Incident Commander in a real attack
- The person with credentials to the CDN/scrubbing dashboard
- The person who handles customer communications

Ideal group (3-6 people):
- Add: engineering lead, security lead, a non-technical stakeholder

Do NOT invite observers above the exercise level. A CTO watching a beginner team stumble creates the wrong dynamic. Keep it safe to fail.

### Set up a shared document

Create a live document before you start. During the exercise this captures:
- Timeline of decisions
- Questions that couldn't be answered ("I don't know who handles that")
- Gaps identified in real time

This document becomes the source for the post-exercise report.

---

## During the Exercise

### Your role as facilitator

You are NOT a participant. You are:
- **The narrator** — you read the scenario and inject descriptions aloud
- **The clock** — you track time and keep things moving
- **The note-taker** — you (or a designated co-facilitator) document gaps
- **The challenger** — you probe assumptions without being adversarial

You are NOT:
- The person who gives the right answers
- An evaluator judging performance
- Someone who rescues the team when they get stuck

### How to handle "I don't know"

"I don't know" is the most valuable answer in a tabletop. When you hear it, say:

> "Great — write that down. Who would know that? What would we need to find out?"

Do not fill the gap yourself. The team finding the gap is the point.

### How to handle silence

If the team goes quiet after an inject, wait 10 seconds. Silence usually means they're thinking. If silence continues, use one of these prompts:

- "Walk me through your first instinct."
- "What information would you need before you could decide?"
- "If you had to act right now, what would you do?"

### Pacing

Each inject should take 5-10 minutes of discussion. If a team is going deep on a single inject, let them go — that's where the real gaps are. If they're moving too fast, probe harder.

Never skip the debrief. The 8-minute debrief at the end is where the team consolidates learning. It's the most important part.

---

## Inject Delivery Tips

Read the inject slowly and clearly. Pause for effect. If the scenario is going well, the team should feel genuinely uncertain about the right answer — that's correct.

After each inject, use this structure:
1. Read the inject
2. Wait 5 seconds (let it land)
3. Ask the primary facilitation question
4. Follow up with "why?" or "how?" probes
5. Document decisions and gaps in the live doc

---

## After the Exercise

### 8-minute debrief structure

1. **What went well?** (2 min) — Start positive. Something always went well.
2. **Where did we get stuck?** (3 min) — The real gaps. Be specific.
3. **Top 3 action items with owners** (3 min) — Name a person and a deadline before leaving the room.

### Assign owners before the room empties

The most common reason tabletop action items don't get done: no owner and no deadline were set before the meeting ended. Force the issue:

> "Before we leave — [GAP] needs an owner. Who takes it? And when is it done by?"

Do this for every significant gap. If something doesn't get an owner, it doesn't get done.

---

## Common Facilitator Mistakes

**Giving hints when the team struggles**
Resist. The struggle is where learning happens. If they can't answer "who has CDN access," that's a real gap — not a facilitator failure.

**Skipping injects because time is short**
Cut the number of injects, not the debrief. The debrief is non-negotiable.

**Letting one person dominate**
Directly address quieter participants: "What's your read on this?" Every perspective in the room has value, especially from non-technical stakeholders.

**Treating it like a test**
Explicitly say at the start: "There are no wrong answers here. We're here to find gaps, not grade performance." Say it more than once.

---

*Good luck. The exercise will feel messy. That's exactly right.*
