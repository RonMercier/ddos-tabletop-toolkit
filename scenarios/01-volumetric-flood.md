# Scenario 01 - Volumetric Flood

**Difficulty:** Beginner
**Estimated duration:** 20 minutes
**Best for:** First tabletop exercise, any team size

---

## Background (Read aloud to the group)

*Your company runs a web application that serves customers across North America. It's a Tuesday afternoon - normal business hours, normal traffic. The monitoring dashboard shows green across the board.*

*Then at 2:47 PM, everything changes.*

---

## INJECT 1 - Discovery (T+0 minutes)

> The network operations team receives automated alerts. Inbound traffic to your primary web server has spiked from a normal 400 Mbps to over 18 Gbps in the last 4 minutes. The website is loading slowly for some users and returning errors for others. The alerts say "bandwidth threshold exceeded."

**Facilitator asks:**
1. Who on this team gets notified first - and how? (phone, Slack, PagerDuty, email?)
2. Is this a DDoS attack or could it be a legitimate traffic spike? How do you tell the difference?
3. Who has the authority to declare this an incident?
4. What's the first thing you actually do in the next 5 minutes?

**Watch for:**
- Does anyone know the on-call rotation off the top of their head?
- Does anyone immediately check the CDN/upstream dashboard?
- Does anyone reach for the runbook - and do they know where it is?

---

## INJECT 2 - Escalation (T+8 minutes)

> You've confirmed it's not a legitimate spike - the traffic pattern is clearly automated. Source IPs are distributed across 40+ countries. Your server's CPU is at 98% and the site is down for most users. Your CEO has just pinged the engineering lead asking "what's happening?"

**Facilitator asks:**
1. What mitigation do you reach for first - and does anyone know the steps to enable it?
2. Who responds to the CEO, with what message, and in what timeframe?
3. Is customer-facing communication your responsibility, or someone else's?
4. Do you have the login credentials for your CDN or upstream scrubbing service right now?

**Watch for:**
- Credential access confusion (who has the CDN login?)
- Ownership gap between engineering and communications
- Does anyone think to check if origin IP is exposed and being targeted directly?

---

## INJECT 3 - Mitigation Attempt (T+18 minutes)

> Your team has enabled "under attack mode" on your CDN. Traffic scrubbing is active. After 10 minutes, volumetric traffic drops significantly - but the site is still slower than normal, and you're still getting some error reports from customers.

**Facilitator asks:**
1. Is the attack over or paused? How do you tell?
2. What do you do about the residual performance impact?
3. When and how do you communicate "we think it's over" to customers?
4. What's the first thing you change or improve after this?

**Watch for:**
- Does anyone consider that residual impact might be a different attack type (L7)?
- Is there a defined "all clear" process or does it just drift to resolved?

---

## INJECT 4 - After Action (T+30 minutes - debrief)

> The attack lasted 47 minutes. The site was fully down for 22 minutes and degraded for 25. You've drafted a customer communication and the CEO has been briefed. What happens now?

**Facilitator asks:**
1. What documentation do you create, and who owns it?
2. What were the top 3 things that slowed your response?
3. What one technical change would most improve your response next time?
4. What one process change would most improve your response next time?

---

## Common Gaps Found in This Scenario

- Nobody knew where the CDN "under attack mode" toggle was before the exercise
- The on-call rotation wasn't documented - people were calling around during the incident
- Customer communication ownership was assumed by someone other than the person who assumed it
- Origin IP was reachable directly, bypassing CDN protection entirely
- No billing alert was set - the bandwidth overage wasn't caught until the bill arrived

---

## After the Exercise

Fill out the **[Exercise Scorecard](../templates/EXERCISE-SCORECARD.md)** and assign an owner and deadline to every gap found.

**Next step:** Run **[Scenario 02 - Layer 7 Application Attack](02-layer7-application.md)** once you've addressed the gaps from this one.
