# Scenario 03 - Smokescreen Attack

**Difficulty:** Advanced
**Estimated duration:** 45 minutes
**Best for:** Security-focused teams who want to test divided attention under pressure

---

## Background (Read aloud to the group)

*This scenario is based on a documented attack pattern: a DDoS used not as the primary objective, but as noise to distract the security team while the real attack - credential theft or data exfiltration - happens quietly in the logs.*

*This is the scenario that catches experienced teams off guard, because the instinct is to tunnel-vision on the loud problem. The lesson: when the alarm bells ring, someone always has to watch the rest of the house.*

---

## INJECT 1 - The Distraction Begins (T+0 minutes)

> 3:40 PM on a Friday. Large-scale UDP flood begins. 22 Gbps inbound. Your website goes down within 3 minutes. The entire security and engineering team is now focused on the DDoS - mitigation, escalation, customer communications, executive briefing. All hands on deck.

**Facilitator asks:**
1. With everyone focused on the DDoS, who - if anyone - is still watching the rest of your environment?
2. Do you have automated alerting that doesn't require a human to be actively watching?
3. Is there a designated role in your IR process for someone to specifically NOT work the primary incident?

---

## INJECT 2 - The Real Attack (T+15 minutes)

> DDoS mitigation is underway and partially working. While reviewing CDN logs, one engineer notices something odd: a series of authenticated API requests to your `/api/export` endpoint - a data export function normally used by admins - started 8 minutes ago. The volume is unusual: 4,200 export requests from a single authenticated session in 6 minutes.

**Facilitator asks:**
1. In the middle of an active DDoS response, how do you decide to prioritize this new signal?
2. Who makes the call to split resources between two simultaneous incidents?
3. What's the fastest way to determine whether those export requests are legitimate or malicious?
4. If those exports contain customer PII, what are your legal/notification obligations and timeline?

**Watch for:**
- Does anyone deprioritize the export signal because the DDoS feels more urgent?
- Does anyone recognize the smokescreen pattern?
- Is there a defined process for opening a second parallel incident track?

---

## INJECT 3 - Containment Decision (T+25 minutes)

> You confirm: the authenticated session belongs to a service account that should only run batch jobs overnight. It ran no jobs yesterday. The session was authenticated from an IP in Eastern Europe. The export requests have pulled 180,000 customer records - names, emails, and hashed passwords - in the last 14 minutes. The DDoS is still running at moderate intensity.

**Facilitator asks:**
1. Do you kill the session immediately - and does that tip off the attacker?
2. Who decides: legal, security, engineering, or executive leadership?
3. What does your breach notification obligation timeline look like from this moment?
4. Do you have the ability to determine what was exported, or just that exports happened?
5. Is there an attorney or legal contact you call right now?

**Watch for:**
- Does anyone know your specific breach notification timeframes (GDPR: 72 hours, various US state laws)?
- Is there a legal contact actually in anyone's phone right now?
- Does the team know whether to preserve or remediate first?

---

## INJECT 4 - Containment Aftermath (T+35 minutes)

> You've killed the compromised session, the DDoS has subsided (possibly because the data was extracted and the attacker achieved their goal), and you're now managing two simultaneous post-incident tracks: DDoS aftermath and potential data breach.

**Facilitator asks:**
1. How do you communicate with customers if a data breach is confirmed?
2. Who drafts the breach notification and in what timeframe?
3. How do you investigate how the service account credentials were compromised?
4. What do you preserve for forensics before you start remediating?

---

## Common Gaps Found in This Scenario

- No one was designated to watch non-DDoS activity during the incident
- The legal/breach notification process had never been discussed - nobody knew the clock started ticking
- Log retention was insufficient to reconstruct exactly what was exported
- The service account had far more permissions than it needed (violating least privilege)
- No legal contact was available - the process said "contact legal" but nobody had a number

---

## After the Exercise

This scenario almost always produces the most serious action items of any in the toolkit. Fill out the **[Exercise Scorecard](../templates/EXERCISE-SCORECARD.md)** carefully and treat legal/notification gaps as critical priority items.
