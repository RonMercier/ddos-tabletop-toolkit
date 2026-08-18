# Scenario 04 - Economic Denial of Service

**Difficulty:** Intermediate
**Estimated duration:** 25 minutes
**Best for:** Teams running cloud-hosted infrastructure with auto-scaling

---

## Background (Read aloud to the group)

*This attack doesn't take your site down. It's worse. Your application stays up - because your auto-scaling keeps pace with the traffic. But when the AWS bill arrives, you're looking at $47,000 in charges for a 6-hour window that should have cost $200.*

*The Economic Denial of Service is the modern DDoS that most cloud teams haven't prepared for. The goal isn't downtime - it's bankruptcy.*

---

## INJECT 1 - Silent Attack (T+0 minutes)

> It's 2 AM Saturday. A sustained traffic flood begins against your cloud-hosted application. Auto-scaling kicks in exactly as designed. Your application is performing normally - zero user impact. No alerts fire. The attack runs undetected for 4 hours.

**Facilitator asks:**
1. Do you have billing alerts configured? At what threshold? Who do they notify at 2 AM?
2. Do you have scaling limits - a ceiling on how many instances can spin up?
3. If this ran for 8 hours, what would the cost be? Has anyone modeled this?
4. Is "application is up and fast" a sufficient monitoring signal - or is something missing?

**Watch for:**
- Does anyone know the current auto-scaling max limits off the top of their head?
- Are billing alerts acknowledged as a security control, or just a finance tool?

---

## INJECT 2 - Discovery (T+4 hours into the attack)

> An engineer on the east coast starts work at 8 AM and notices the infrastructure dashboard. 340 instances are running. Normal Monday morning is 12. The auto-scaling logs show a steady ramp starting at 2:04 AM. Estimated cost at current burn rate: $8,200 per hour.

**Facilitator asks:**
1. Do you scale down immediately - and what happens to real user traffic if you do?
2. Who has the authority to make a decision that could take down the application for real users?
3. How do you tell the difference between attack traffic and legitimate early-morning traffic?
4. Who do you call at your cloud provider, and do you have that number?

---

## INJECT 3 - Mitigation Tradeoffs (T+4h 15min)

> You've confirmed it's automated attack traffic - the request pattern is clearly non-human. You implement aggressive rate limiting, which cuts the attack traffic by 90%. 30 instances now running. Cost stopped. But your cloud provider's billing system shows $31,000 in charges already accrued for the 4-hour window.

**Facilitator asks:**
1. Can you dispute these charges with your cloud provider - and does anyone know the process?
2. Does your cyber insurance cover economic denial of service, or only downtime?
3. What's the retroactive fix: scaling limits, WAF rate limiting, billing alerts?
4. How do you prevent this from happening again at 2 AM next Saturday?

---

## Common Gaps Found in This Scenario

- No billing alerts were configured - or they were set to a threshold never expected to trigger in 4 hours
- Scaling limits existed but were set to a high number as a "just in case" safety margin - effectively no ceiling
- No cloud provider emergency contact was on file (most providers have DDoS response teams accessible via support)
- Cyber insurance policy had never been reviewed for economic DoS coverage
- No one had modeled "what does an 8-hour attack cost at auto-scale max?"

---

## After the Exercise

Fill out the **[Exercise Scorecard](../templates/EXERCISE-SCORECARD.md)**.

**Immediate action item everyone leaves with:** Set a billing alert today. It takes 5 minutes and is the single highest-leverage change from this exercise.
