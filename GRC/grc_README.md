# GRC Portfolio — Risk & Compliance Artifacts

Sample governance, risk & compliance (GRC) work products, self-authored to demonstrate
hands-on methodology. They build directly on the
[Cloud Security Assessment](../README.md): *assess the environment → log the risks →
measure readiness against a framework.*

> All data is **illustrative**, based on a personal AWS lab environment. No real client,
> production, or confidential data is included.

---

## 📋 Information Security Risk Register
**File:** `GRC_Risk_Register.xlsx` · [PDF preview](./GRC_Risk_Register.pdf)

A scored, rated risk register covering 14 risks identified across identity, logging,
network, data protection, third-party, and AI governance.

- **Methodology:** each risk scored **Likelihood × Impact (1–25)** and rated Low → Critical, with a documented scoring key and 5×5 heat matrix.
- **Inherent vs residual:** every risk carries a treatment and a residual score, showing the effect of mitigation — the inherent profile of **3 Critical / 4 High** reduces to **0 Critical / 0 High** once planned controls are applied.
- **Auto-calculated summary** tab: risk profile and status roll-ups driven by formulas.

## ✅ SOC 2 Readiness Assessment
**File:** `SOC2_Readiness_Assessment.xlsx` · [PDF preview](./SOC2_Readiness_Assessment.pdf)

A control gap analysis against the **SOC 2 Trust Services Criteria** (Security Common
Criteria CC1–CC9, plus Availability and Confidentiality).

- **31 controls** assessed as Implemented / Partially / Not Implemented, each with evidence, gap notes, owner, and a remediation action.
- **Evidence cross-links** the rest of this portfolio (risk register, assessment report, Terraform landing zone) to the controls they satisfy.
- **Readiness scoring:** overall readiness is calculated automatically, with a readiness-by-criteria breakdown and chart. Strongest in Risk Assessment (CC3) and Monitoring (CC4); weakest in System Operations (CC7) and Risk Mitigation (CC9).

## 🛡️ Information Security Policy
**File:** `Information_Security_Policy.pdf`

A sample information security policy covering acceptable use, access control, data
protection, logging & monitoring, incident response, and third-party risk — the kind of
foundational document a SOC 2 or ISO 27001 programme requires (and which several of the
readiness gaps above call for).

---

## Skills demonstrated
Risk assessment & scoring · risk register maintenance · SOC 2 / Trust Services Criteria ·
control gap analysis · readiness measurement · remediation planning · policy writing ·
evidence mapping · clear GRC documentation

*Prepared by André Field — CompTIA Security+, AWS Certified Cloud Practitioner.*
