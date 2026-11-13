# AWS-Security-Assessment
# Cloud Security Assessment — AWS (CIS Benchmark)

A security configuration assessment of an AWS account, scanned with **Prowler** and
triaged into a prioritised, risk-rated report mapped to the **CIS AWS Foundations
Benchmark** — the kind of deliverable a GRC/security analyst produces on the job.

> Authorised self-assessment of my own AWS lab account, for professional development.
> No third-party systems were tested.

---

## 🛠️ Tools & methodology
| | |
|---|---|
| **Tool** | Prowler v5.48 (open-source AWS security scanner) |
| **Baseline** | CIS AWS Foundations Benchmark + AWS best practices |
| **Scope** | Single AWS account, all enabled regions, 303 resources |
| **Access** | Read-only (SecurityAudit-equivalent) — nothing created or modified |

**Reproduce it:**
```bash
brew install prowler
prowler aws            # read-only scan; outputs HTML/CSV/JSON to ./output
```

## 📊 Results at a glance
**451 checks evaluated — 323 failed, 128 passed** (10 manual review), across 303 resources.

| Severity | Failed |
|---|---|
| 🔴 Critical | 1 |
| 🟠 High | 95 |
| 🟡 Medium | 119 |
| ⚪ Low | 108 |

> **Analyst note:** many findings repeat *once per region* (CloudTrail, GuardDuty and
> Security Hub each failed ~17 times — once per region). The 323 raw findings therefore
> collapse to roughly a dozen **logical issues**, each fixable with a single account-wide
> control. Reading findings this way is central to prioritising remediation.

## 🔑 Top findings (mapped to CIS)
| Finding | Severity | CIS | Fix |
|---|---|---|---|
| `AdministratorAccess` (`*:*`) attached directly | Critical | 1.16 | Least-privilege roles + MFA |
| No multi-region CloudTrail (API logging off) | High | 3.1 | Enable multi-region trail |
| GuardDuty disabled in all regions | High | 4.16 | Enable threat detection |
| Security Hub not enabled | High | — | Enable with CIS/FSBP standards |
| MFA not enforced / long-lived keys / root usage | High | 1.5–1.14 | Enforce MFA, short-lived creds |
| NACLs allow `0.0.0.0/0` incl. SSH/RDP | High | 5.1–5.3 | Restrict ingress |
| AWS Config disabled | Medium | 3.5 | Enable config recording |
| No CloudWatch alarms for critical changes | Medium | 4.x | Add metric-filter alarms |
| AI/ML governance gaps (Bedrock guardrails/logging) | Medium | — | Guardrails + invocation logging |

👉 **Full report with risk analysis & remediation roadmap:
[Cloud_Security_Assessment_Report.pdf](./Cloud_Security_Assessment_Report.pdf)**

## 🧭 Remediation roadmap (summary)
- **Phase 1 (immediate):** least-privilege IAM, enforce MFA, enable CloudTrail, close exposed ports.
- **Phase 2 (detective):** enable GuardDuty, Security Hub, Config, Inspector, Access Analyzer + alarms.
- **Phase 3 (governance):** Organizations SCPs, AI-service governance, recurring Prowler scans.

## 🔗 Related work
- **[Secure AWS Landing Zone (Terraform)](#)** — remediates several of these findings *as code* (CloudTrail, GuardDuty, least-privilege IAM, encryption). *Assess here → remediate there.*
- **[flaws.cloud labs](https://github.com/thiswasdre/AWS---Security---Labs)** — hands-on exploitation of the kinds of misconfigurations this assessment detects.

## 💡 Skills demonstrated
Cloud security assessment · Prowler · CIS AWS Foundations Benchmark · risk triage & rating ·
remediation planning · security reporting · GRC documentation · AWS (IAM, CloudTrail, GuardDuty, Config)

---
*Prepared by André Field — CompTIA Security+, AWS Certified Cloud Practitioner.*
