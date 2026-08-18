# Scenario 02 - Layer 7 Application Attack

**Difficulty:** Intermediate
**Estimated duration:** 30 minutes
**Best for:** Teams that have CDN/WAF in place and passed Scenario 01

---

## Background (Read aloud to the group)

*Unlike a volumetric flood, this attack doesn't fill your pipe. The total traffic volume looks almost normal - maybe 20% above baseline. Your CDN isn't triggering any volumetric alerts. But your application is buckling, your database is at 100% CPU, and real customers can't log in.*

*This is the attack that gets past the first layer of protection and hits your application directly - exactly where it's most expensive to absorb.*

---

## INJECT 1 - Subtle Discovery (T+0 minutes)

> It's 10:15 AM on a Thursday. Your application monitoring shows response times climbing - login is taking 8 seconds instead of the usual 400ms. Database CPU has been at 95%+ for 12 minutes. No volumetric alerts have fired. A customer just tweeted that they can't log in.

**Facilitator asks:**
1. Is your monitoring even set up to catch this - or only volumetric attacks?
2. How do you differentiate a bad code deployment from an application-layer attack?
3. Do you look at the CDN/WAF logs for this, or somewhere else?
4. At what point does this escalate from "performance issue" to "incident"?

**Watch for:**
- Does the team know to look at request patterns rather than bandwidth?
- Does anyone know how to pull per-endpoint traffic breakdown?
- Is there confusion about whether this is a security incident or an engineering incident?

---

## INJECT 2 - Identifying the Pattern (T+10 minutes)

> You pull the WAF logs. You're seeing 40,000 requests per minute to your `/api/login` endpoint. Normal peak is 800 requests per minute. The source IPs are distributed across 200+ addresses, all sending requests at nearly identical intervals. The User-Agent strings look legitimate. No single IP exceeds your rate limit threshold.

**Facilitator asks:**
1. Your rate limiter isn't triggering because no single IP hits the threshold. What do you do?
2. Do you have the ability to apply endpoint-specific rate limiting right now - and who knows how to do it?
3. How do you block the attack without blocking real users trying to log in?
4. What's the collateral damage risk if you apply aggressive mitigation?

**Watch for:**
- Does anyone know the WAF rule interface well enough to make changes under pressure?
- Is there a change management process that would slow down emergency mitigation?
- Does anyone consider reducing functionality (e.g., CAPTCHA on login) as a mitigation?

---

## INJECT 3 - Escalation and Tradeoffs (T+20 minutes)

> You've applied a global CAPTCHA to the login endpoint. Bot traffic drops 80%. But your legitimate mobile app users are now failing CAPTCHA at a high rate - the app wasn't built to handle it. Customer support is being flooded. The attack is still running at 20% of its previous intensity.

**Facilitator asks:**
1. Do you leave the CAPTCHA in place, remove it, or find a middle path?
2. Who owns the decision to accept business impact in exchange for security mitigation?
3. How do you communicate this to customers whose app is broken?
4. Is this a "normal business hours" decision or does it require executive sign-off?

**Watch for:**
- Decision authority gap (who can authorize a business impact tradeoff?)
- Customer communication lag - how long does it take to get messaging out?
- Does anyone look at whether the attack has shifted to a different endpoint?

---

## INJECT 4 - Persistence (T+25 minutes)

> Two hours into mitigation, the attack shifts. The login endpoint is now manageable, but the same pattern has appeared on your `/api/search` endpoint. This one is harder to CAPTCHA. The attacker appears to be probing for endpoints you haven't protected yet.

**Facilitator asks:**
1. How do you know which endpoints are next - do you have visibility into that?
2. At what point do you consider taking the application offline entirely vs. keeping it degraded?
3. Do you have an emergency contact at your WAF/CDN vendor for rule assistance?
4. What would a "nuclear option" look like - and have you ever discussed what would trigger it?

---

## Common Gaps Found in This Scenario

- Teams that had excellent volumetric protection had never tested their L7/WAF capabilities
- Nobody knew the WAF rule syntax well enough to write a new rule under pressure
- The change management process required a ticket and approval - creating a 2-hour delay on emergency mitigation
- Executive decision authority for business-impacting mitigations was never defined
- No vendor emergency contact number was on file

---

## After the Exercise

Fill out the **[Exercise Scorecard](../templates/EXERCISE-SCORECARD.md)**.

**Next step:** **[Scenario 03 - Smokescreen Attack](03-smokescreen-attack.md)** adds data exfiltration to the mix. Run it when you want to test your team's ability to handle two simultaneous incidents.
