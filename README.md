# 🛡️ VAI - ISO 27001:2022 Compliance Gap Analysis Dashboard

> 15 controls assessed. 47% coverage. Built from a real cybersecurity risk assessment for a cloud-hosted AWS learning platform.

![Full Dashboard](Full%20dashboard.jpeg)

---

## 👤 Author
**Taiwo Johnson** | GRC & Cybersecurity Risk Analyst  
**Tools:** HTML | Chart.js | ISO 27001:2022 | NIST CSF  
**Sector:** EdTech | Cloud Security | Compliance Assessment

---

## 📋 Overview

Victor Akinode Initiatives (VAI) operates a digital learning platform hosted on AWS, storing learner data, payment information, mentor records, and assessment results. Before onboarding new international partners, leadership commissioned a cybersecurity risk and compliance assessment.

This dashboard presents the findings of that assessment, mapping 15 ISO 27001:2022 controls across all 4 control themes against VAI's current security posture. The analysis identified a 47% overall compliance coverage rate and 6 critical control gaps requiring immediate remediation before partner onboarding can proceed.

---

## 📊 Compliance Summary

| Theme | Controls Assessed | Coverage | Status |
|---|---|---|---|
| 🟣 Organisational (A.5) | 5 | 42% | Partial |
| 🔵 People (A.6) | 4 | 60% | Partial |
| 🟡 Physical (A.7) | 2 | 33% | Gap |
| 🔷 Technological (A.8) | 4 | 50% | Partial |
| **Overall** | **15** | **47%** | **❌ Not Ready** |

---

## 🖼️ Dashboard Visuals

| File | Description |
|---|---|
| `Full dashboard.jpeg` | 📈 Complete compliance gap dashboard overview |
| `Radar chart close-up.jpeg` | 🕸️ Coverage radar across all 4 ISO 27001:2022 themes |
| `Control table.jpeg` | 📋 Full 15-control gap assessment with findings and actions |
| `vai_iso27001_gap_analysis_dashboard.html` | 🌐 Open in browser for interactive dashboard |

---

## 🔍 Key Findings

- 🚨 **6 control gaps** identified requiring immediate remediation
- ⚠️ **4 high-priority gaps** must be resolved before partner onboarding
- 🔴 Highest risk: Unauthorised access to learner database (Risk Score 20/25)
- 📭 No logging or monitoring enabled across AWS regions (A.8.15)
- 🔓 No WAF deployed on API endpoints (A.8.26)
- 💻 Staff laptops have no endpoint protection or MDM (A.7.9)

---

## 🛠️ Remediation Phases

**🔴 Phase 1 (0–14 days):** Enable MFA, activate GuardDuty, patch EC2, enable KMS encryption, deploy WAF  
**🟡 Phase 2 (30–60 days):** Enable CloudTrail logging, deploy CSPM, complete endpoint protection  
**🔵 Phase 3 (60–90 days):** Complete vendor DPAs, security questionnaires, appoint DPO  

⚠️ Partner onboarding is paused pending completion of all Phase 1 items.

---

## 🚀 How to Use

1. Open `vai_iso27001_gap_analysis_dashboard.html` in any web browser
2. Use filters to view controls by theme, status, or priority
3. Review the radar chart for coverage across all 4 ISO 27001:2022 themes
4. Browse the control table for detailed findings and recommended actions

---

## ⚙️ Tech Stack

- **Tools:** HTML, Chart.js, GitHub
- **Frameworks:** ISO 27001:2022 (93 controls), NIST Cybersecurity Framework
- **Platform assessed:** AWS (EC2, RDS, S3, IAM, VPC, KMS)

---

## 🗺️ v2.0 Roadmap

- [ ] Expand assessment to cover all 93 ISO 27001:2022 controls
- [ ] Add automated control scoring based on evidence uploads

---

## 📄 License

MIT License - see [LICENSE](LICENSE) for details.
