# Scenario 05 — Multi-Vector Escalation

**Difficulty:** Advanced
**Estimated duration:** 60 minutes
**Best for:** Experienced IR teams, annual full-team exercises

---

## Background (Read aloud to the group)

*Modern sophisticated DDoS campaigns don't throw one type of attack and hope. They probe your defenses, adapt when something gets blocked, and escalate. This scenario simulates that arc — starting with a manageable volumetric attack and escalating through multiple vectors as mitigation is applied.*

*This is the most realistic scenario in the toolkit. It's also the most uncomfortable, which is exactly the point.*

---

## INJECT 1 — Opening Salvo (T+0 minutes)

> 11:45 AM Tuesday. 31 Gbps UDP flood. Your CDN absorbs it. Website stays up. Mitigation is applied within 8 minutes. You brief your team: "We got hit, CDN handled it, watching for recurrence." Looks like a win.

**Facilitator asks:**
1. Do you stay at heightened alert, or does the team stand down?
2. Are you actively watching all other attack surfaces while monitoring the primary vector?

---

## INJECT 2 — Shift (T+25 minutes)

> Volumetric traffic stops. 18 minutes of quiet. Then: 15,000 requests/minute start hitting your login endpoint. Distributed across 800 source IPs. No single IP exceeds individual rate limits. Database CPU climbing.

**Facilitator asks:**
1. Did you see this coming — was there any indicator in the quiet period?
2. Your volumetric mitigation is active but not helping with L7. What do you reach for?
3. Who adjusts the WAF rules and how long does it take?

---

## INJECT 3 — Simultaneous Pressure (T+45 minutes)

> WAF rules are partially working. Login is degraded but not down. Then: a third vector activates. DNS query flood begins against your authoritative DNS servers — 2.4 million queries per second. Your DNS provider's infrastructure is struggling. Some users can't resolve your domain at all, even though the application itself is up.

**Facilitator asks:**
1. You now have three simultaneous attack vectors. How do you allocate people across them?
2. Do you have a secondary DNS provider configured for failover?
3. Who on your team knows how to interact with your DNS provider's abuse/DDoS team?
4. At what point do you consider this a coordinated, targeted attack rather than opportunistic?

---

## INJECT 4 — Resource Exhaustion (T+55 minutes)

> It's been 55 minutes. Your team is fatigued. You've partially mitigated all three vectors but none are fully resolved. A new alert: your SSL certificate renewal failed during the attack window and cert expiry is in 4 hours. A non-attack problem has been amplified by the attack conditions.

**Facilitator asks:**
1. How do you prioritize cert renewal vs. continuing attack mitigation?
2. Who handles the cert — is it automated, and did the automation fail?
3. At 55 minutes in, do you have enough people to handle everything? What's your mutual aid plan?
4. When does this become a major incident requiring executive and board-level visibility?

---

## INJECT 5 — Resolution and Lessons (T+60 minutes — debrief)

**Facilitator asks:**
1. What was the most important decision made during this exercise?
2. What was the most important decision that didn't get made fast enough?
3. If this was real and lasted 4 more hours, what would break?
4. What's the single highest-priority change before the next exercise?

---

## Common Gaps Found in This Scenario

- Teams had practiced one vector but not multi-vector coordination
- No secondary DNS provider — single point of failure discovered during exercise
- SSL certificate automation had a dependency on availability that failed under attack conditions
- Escalation thresholds were never defined — "when is this board-level?" was never answered
- Team fatigue was underestimated — nobody had defined shift rotation for extended incidents

---

## After the Exercise

This scenario reliably produces 8-12 action items. Use the **[Post-Exercise Report](../templates/POST-EXERCISE-REPORT.md)** template, not just the scorecard. Prioritize ruthlessly — 3 action items that get done beat 12 that sit in a backlog.
