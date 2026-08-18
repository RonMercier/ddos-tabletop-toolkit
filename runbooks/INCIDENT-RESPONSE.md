# DDoS Incident Response Runbook

**Version:** 1.0 | **Last reviewed:** [DATE] | **Owner:** [NAME]

> Customize: Replace all bracketed fields with your actual contacts, tools, and thresholds.
> Store a copy somewhere accessible when your primary systems are down (printed copy, offline doc, phone photo).

---

## Quick Reference - First 5 Minutes

```
1. Confirm it's an attack (not a traffic spike or bad deployment)
2. Declare the incident - assign an Incident Commander
3. Enable CDN/scrubbing protection
4. Open incident communication channel
5. Start the clock and document everything
```

---

## Phase 1 - Detection and Confirmation (T+0 to T+5 min)

### Confirm it's a DDoS (not a deployment or spike)

| Check | How | DDoS indicator |
|---|---|---|
| Traffic volume | CDN/network dashboard | Sudden spike, not gradual |
| Traffic pattern | Source IP distribution | Many IPs, low per-IP volume |
| Request pattern | Web server / WAF logs | Repetitive, automated requests |
| Time correlation | Deployment log | No recent deployments |
| Business context | Marketing/sales | No expected traffic event |

### Declare the incident

- **Incident Commander:** [NAME / ROLE]
- **Backup IC:** [NAME / ROLE]
- **Communication lead:** [NAME / ROLE]
- Open the incident channel: [Slack #incident / Bridge line / etc.]
- Start a live document for notes and timeline

---

## Phase 2 - Immediate Mitigation (T+5 to T+15 min)

### Layer 1 - CDN / Scrubbing

**Provider:** [Cloudflare / AWS Shield / Other]
**Dashboard URL:** [URL]
**Login:** [Where credentials are stored - NOT in this document]

Steps:
- [ ] Log into CDN dashboard
- [ ] Identify if attack is being absorbed or passing through
- [ ] Enable "Under Attack Mode" or equivalent
- [ ] Verify origin IP is NOT reachable directly (test: `curl -v [origin IP]`)
- [ ] Note: CDN IP ranges to allow in firewall: [LIST OR LINK]

### Layer 2 - Cloud provider DDoS protection

**Provider:** [AWS / Azure / GCP / Other]
**Console URL:** [URL]

Steps:
- [ ] Verify native DDoS protection is active
- [ ] Check if protection tier covers current attack volume
- [ ] Enable advanced protection if available and not already on
- [ ] Set or verify billing alert threshold: $[AMOUNT]
- [ ] Verify auto-scaling limits: max [NUMBER] instances

### Layer 3 - WAF / Rate limiting

- [ ] Review WAF logs for attack pattern
- [ ] Apply endpoint-specific rate limiting if L7 attack
- [ ] Block ASNs or countries if concentrated (note legitimate traffic risk)
- [ ] Rule syntax reference: [LINK TO WAF DOCS]

### Layer 4 - Origin server (last resort)

- [ ] Rate limiting at Nginx: `limit_req_zone` / `limit_conn_zone`
- [ ] Block known bad IPs: `deny [IP];`
- [ ] Nginx config location: `/etc/nginx/sites-available/[SITE]`
- [ ] Reload after changes: `sudo nginx -t && sudo systemctl reload nginx`

---

## Phase 3 - Communication (Parallel to mitigation)

### Internal - first 10 minutes

| Who | What | How |
|---|---|---|
| Immediate team | Incident declared, channel open | [Slack/Teams/etc.] |
| Engineering lead | Status + mitigation in progress | [Direct message] |
| Executive on-call | Site is down / degraded | [Phone call - not text] |

### Customer-facing communication

**Template 1 - Initial (within 15 min):**
```
We are currently experiencing a service disruption affecting [PRODUCT/SITE].
Our team is actively working to resolve this. We will provide an update
in [30/60] minutes. We apologize for the inconvenience.
```

**Template 2 - Update (every 30 min):**
```
Update on the service disruption: [CURRENT STATUS]. Our team continues to
work on resolution. Estimated restoration: [TIME or "We will update in 30 min"].
```

**Template 3 - Resolution:**
```
The service disruption affecting [PRODUCT/SITE] has been resolved.
Service is fully restored as of [TIME]. We are conducting a post-incident
review and will share findings. Thank you for your patience.
```

---

## Phase 4 - Monitoring and Escalation

### Escalation thresholds

| Duration | Impact | Action |
|---|---|---|
| 15 minutes | Site degraded | Engineering lead notified |
| 30 minutes | Site down | VP/Director notified |
| 60 minutes | Site down | C-suite notified |
| 2 hours | Site down | Board notification consideration |
| Any duration | Data access suspected | Legal + CISO immediately |

### Vendor emergency contacts

| Vendor | Contact type | Number / URL |
|---|---|---|
| [CDN Provider] | DDoS response team | [NUMBER] |
| [Cloud Provider] | Enterprise support | [NUMBER] |
| [ISP/Transit] | Abuse/DDoS team | [NUMBER] |
| [Cyber insurance] | Incident line | [NUMBER] |
| [Legal counsel] | Emergency contact | [NUMBER] |

---

## Phase 5 - Resolution and Post-Incident

### Declaring resolution

Do not declare resolution until:
- [ ] Traffic has returned to normal for at least 30 consecutive minutes
- [ ] Application response times are back within normal range
- [ ] No active alerts on any monitoring system
- [ ] IC and Engineering lead have agreed

### Post-incident documentation (within 24 hours)

- [ ] Attack timeline documented (start, vectors, mitigations applied, resolution)
- [ ] Peak traffic volume recorded
- [ ] Downtime duration recorded
- [ ] Customer impact documented
- [ ] Action items identified and owners assigned
- [ ] Post-incident review scheduled (within 5 business days)

---

*This is a template. Customize every bracketed field before your first real incident.*
*Review and update this runbook after every incident and every tabletop exercise.*
