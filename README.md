# 🛡️ VAI - ISO 27001:2022 Compliance Gap Analysis Dashboard

> *15 controls assessed. 47% coverage. 6 critical gaps. Built from a real cybersecurity risk assessment for a cloud-hosted AWS learning platform.*

![Full Dashboard](Full%20dashboard.jpeg)

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)]()
[![Framework: ISO 27001](https://img.shields.io/badge/Framework-ISO%2027001:2022-blue)]()
[![Framework: NIST CSF](https://img.shields.io/badge/Framework-NIST%20CSF-darkblue)]()
[![Platform: AWS](https://img.shields.io/badge/Platform-AWS-orange)]()

---

## 👤 Author
**Taiwo Johnson** | GRC & Cybersecurity Risk Analyst
**Tools:** HTML · Chart.js · ISO 27001:2022 · NIST CSF
**Sector:** EdTech | Cloud Security | Compliance Assessment

---

## 📋 Executive Summary

Victor Akinode Initiatives (VAI) operates a digital learning platform hosted on AWS, serving learners, mentors, and paying customers across multiple regions. With international partner onboarding planned, VAI's leadership commissioned a cybersecurity risk and ISO 27001:2022 compliance gap assessment to determine organisational readiness.

This dashboard presents the findings of that assessment. **15 ISO 27001:2022 controls** were assessed across all 4 control themes. The assessment identified:

- **47% overall compliance coverage** - below the threshold required for partner onboarding
- **6 critical control gaps** requiring immediate remediation
- **4 high-priority gaps** that must be resolved before partner onboarding can proceed
- **Highest risk score: 20/25** - unauthorised access to the learner database

The overall finding is that VAI is **Not Ready** for partner onboarding in its current state. A structured remediation roadmap has been produced with three phases across 90 days. If Phase 1 is completed within 14 days and Phases 2 and 3 within 90 days, VAI can proceed to a formal ISO 27001:2022 certification readiness assessment.

---

## 🔭 Scope

| In Scope | Out of Scope |
|---|---|
| 15 ISO 27001:2022 controls selected as most material to VAI's risk profile | Full 93-control ISO 27001:2022 Annex A assessment |
| AWS cloud environment: EC2, RDS, S3, IAM, VPC, KMS, CloudTrail, GuardDuty | On-premises infrastructure (VAI has none) |
| Learner data, payment information, mentor records, and assessment results | Payment card processing systems (not operated by VAI directly) |
| Staff endpoint devices and remote working controls | Third-party platform security (external LMS components) |
| Vendor and partner data processing agreements | Physical security of AWS data centre (AWS responsibility under shared model) |
| Organisational security policies and governance documentation | Application code security review (separate engagement required) |

---

## 📐 Assumptions

1. The 15 controls assessed were selected based on materiality to VAI's risk profile - specifically the processing of learner PII, payment information, and the planned international partner onboarding
2. Assessment findings are based on documentation review, stakeholder interviews, and AWS configuration review - independent penetration testing was not conducted as part of this engagement
3. AWS infrastructure security (physical, network fabric, hypervisor) is the responsibility of AWS under the shared responsibility model and is not assessed here - VAI's responsibility begins at the OS and application layer
4. Compliance ratings reflect the control environment at the time of assessment - implementation of any new controls after the assessment date would improve coverage
5. The 47% coverage figure reflects the 15 controls assessed, not all 93 Annex A controls - overall coverage across the full control set would likely be lower
6. Risk scores reflect the combination of VAI's specific threat landscape (EdTech platform, learner PII, international expansion) and current control effectiveness
7. Partner onboarding readiness is assessed against a minimum security baseline - not against full ISO 27001:2022 certification requirements

---

## 📊 Risk Rating Criteria

All risks are scored using a **5×5 likelihood and impact matrix** producing a risk score between 1 and 25, consistent with ISO 27001:2022 risk assessment requirements.

### Likelihood Scale
| Score | Rating | Definition |
|---|---|---|
| 1 | Rare | Threat is theoretical - no known exploitation in similar environments |
| 2 | Unlikely | Threat exists but current controls make exploitation difficult |
| 3 | Possible | Threat is credible and controls provide only partial protection |
| 4 | Likely | Controls are insufficient - exploitation is probable given current threat landscape |
| 5 | Almost Certain | No effective controls in place - exploitation is expected |

### Impact Scale
| Score | Rating | Definition |
|---|---|---|
| 1 | Negligible | No meaningful impact on learners, operations, or regulatory position |
| 2 | Minor | Limited impact - internal resolution, minor reputational effect |
| 3 | Moderate | Significant impact - regulatory notification may be required, moderate data exposure |
| 4 | Major | Serious impact - NDPA/GDPR breach notification required, significant learner data exposure, partner onboarding blocked |
| 5 | Critical | Catastrophic - mass learner data breach, regulatory sanction, platform shutdown, irreversible reputational damage |

### Risk Rating Matrix
| Risk Score | Rating | Treatment Requirement |
|---|---|---|
| 20-25 | 🔴 Critical | Immediate remediation - partner onboarding blocked until resolved |
| 12-19 | 🟠 High | Treatment required before partner onboarding - 14-day maximum |
| 6-11 | 🟡 Medium | Treatment required within 60 days - monitor weekly |
| 1-5 | 🟢 Low | Accept or monitor - review quarterly |

### How Critical Risks Were Scored

| Risk | Likelihood | Impact | Score | Rationale |
|---|---|---|---|---|
| Unauthorised access to learner database (RDS) | 4 - Likely | 5 - Critical | 20 | No MFA on IAM accounts with database access; public RDS endpoint identified; learner PII and payment data directly exposed |
| No logging or monitoring across AWS regions | 5 - Almost Certain | 4 - Major | 20 | CloudTrail disabled in multiple regions; GuardDuty not enabled; breach would be undetectable - NDPA 72-hour notification obligation cannot be met |
| Unpatched EC2 instances with known CVEs | 4 - Likely | 5 - Critical | 20 | Patch cycle not documented; 3 EC2 instances running OS versions with publicly available exploit code; direct path to application compromise |
| No WAF on API endpoints | 4 - Likely | 4 - Major | 16 | API endpoints publicly accessible without WAF; OWASP Top 10 vulnerabilities including SQL injection and broken authentication untested and unmitigated |
| Staff laptops with no endpoint protection or MDM | 4 - Likely | 4 - Major | 16 | 100% of staff work remotely on unmanaged personal devices; no EDR, no MDM, no disk encryption verified - credential theft and data exfiltration risk |
| No vendor DPAs with third-party platform providers | 3 - Possible | 5 - Critical | 15 | International partner onboarding requires demonstration of adequate data protection controls for all processors; missing DPAs create immediate regulatory liability |

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

## 🗂️ Statement of Applicability (Assessed Controls)

| Control Ref | Control Name | Applicable | Current Status | Gap |
|---|---|---|---|---|
| A.5.1 | Policies for information security | Yes | Partial - policy exists but not reviewed in 18 months | Yes |
| A.5.15 | Access control | Yes | Partial - policy exists, MFA not enforced | Yes |
| A.5.19 | IS in supplier relationships | Yes | Gap - no vendor DPAs in place | Yes |
| A.5.24 | IS incident management planning | Yes | Gap - no incident response plan documented | Yes |
| A.5.34 | Privacy and protection of PII | Yes | Partial - privacy notice exists, DPIA not conducted | Yes |
| A.6.3 | IS awareness, education and training | Yes | Gap - no security awareness training program | Yes |
| A.6.7 | Remote working | Yes | Partial - remote working policy exists, not enforced | Yes |
| A.6.8 | IS event reporting | Yes | Gap - no formal reporting mechanism | Yes |
| A.7.9 | Security of assets off-premises | Yes | Gap - no MDM, no endpoint protection | Yes |
| A.7.14 | Secure disposal or re-use of equipment | Yes | Partial - no documented disposal procedure | Partial |
| A.8.2 | Privileged access rights | Yes | Gap - no privileged access management | Yes |
| A.8.8 | Management of technical vulnerabilities | Yes | Gap - no patch management process | Yes |
| A.8.13 | Information backup | Yes | Partial - S3 backups exist, not tested | Partial |
| A.8.15 | Logging | Yes | Gap - CloudTrail disabled in multiple regions | Yes |
| A.8.20 | Networks security | Yes | Partial - VPC configured, security groups overly permissive | Partial |

---

## 🔍 Key Findings

- 🚨 **6 control gaps** identified requiring immediate remediation
- ⚠️ **4 high-priority gaps** must be resolved before partner onboarding
- 🔴 Highest risk: Unauthorised access to learner database (Risk Score 20/25)
- 📭 No logging or monitoring enabled across AWS regions (A.8.15)
- 🔓 No WAF deployed on API endpoints (A.8.26)
- 💻 Staff laptops have no endpoint protection or MDM (A.7.9)

---

## 🗺️ Implementation Roadmap

### 🔴 Phase 1 - Immediate (0-14 days): Stop the Bleeding
*Partner onboarding cannot proceed until all Phase 1 items are complete.*

| Action | Control | Owner | Effort |
|---|---|---|---|
| Enable MFA on all IAM accounts - no exceptions | A.5.15, A.8.2 | IT Lead | Low - 1 day |
| Enable GuardDuty across all AWS regions | A.8.15, A.8.16 | IT Lead | Low - 1 day |
| Enable CloudTrail logging across all AWS regions | A.8.15 | IT Lead | Low - 1 day |
| Patch all EC2 instances - resolve known CVEs | A.8.8 | IT Lead | Medium - 3-5 days |
| Enable KMS encryption on RDS and S3 buckets containing PII | A.8.24 | IT Lead | Medium - 2-3 days |
| Deploy WAF on all public-facing API endpoints | A.8.20 | IT Lead | Medium - 3-5 days |
| Restrict RDS to private subnet - remove public endpoint | A.5.15 | IT Lead | Low - 1 day |

### 🟡 Phase 2 - Short Term (15-60 days): Build the Foundation
| Action | Control | Owner | Effort |
|---|---|---|---|
| Deploy endpoint protection and MDM on all staff devices | A.7.9 | IT Lead | Medium |
| Deploy CSPM tool for continuous AWS configuration monitoring | A.8.9 | IT Lead | Medium |
| Complete security awareness training for all staff | A.6.3 | HR / GRC | Medium |
| Document and test incident response plan | A.5.24, A.6.8 | GRC | Medium |
| Conduct DPIA for learner data processing | A.5.34 | GRC / Legal | Medium |
| Review and update information security policy | A.5.1 | GRC | Low |

### 🔵 Phase 3 - Medium Term (61-90 days): Close the Gaps
| Action | Control | Owner | Effort |
|---|---|---|---|
| Complete vendor DPAs with all third-party platform providers | A.5.19 | Legal / GRC | Medium |
| Appoint Data Protection Officer or designate DPO responsibility | A.5.34 | Leadership | Low |
| Complete security questionnaires for all material vendors | A.5.19 | GRC | Medium |
| Test S3 backup restoration - document results | A.8.13 | IT Lead | Low |
| Document secure device disposal procedure | A.7.14 | IT Lead | Low |
| Review and tighten all VPC security group rules | A.8.20 | IT Lead | Medium |

---

## 🖼️ Dashboard Visuals

| File | Description |
|---|---|
| `Full dashboard.jpeg` | Complete compliance gap dashboard overview |
| `Radar chart close-up.jpeg` | Coverage radar across all 4 ISO 27001:2022 themes |
| `Control table.jpeg` | Full 15-control gap assessment with findings and actions |
| `vai_iso27001_gap_analysis_dashboard.html` | Open in browser for interactive dashboard |

---

## 🚀 How to Use

1. Open `vai_iso27001_gap_analysis_dashboard.html` in any web browser
2. Use filters to view controls by theme, status, or priority
3. Review the radar chart for coverage across all 4 ISO 27001:2022 themes
4. Browse the control table for detailed findings and recommended actions
5. Use the implementation roadmap to sequence remediation activity

---

## ⚙️ Tech Stack

- **Tools:** HTML, Chart.js, GitHub
- **Frameworks:** ISO 27001:2022 (93 controls), NIST Cybersecurity Framework
- **Platform Assessed:** AWS (EC2, RDS, S3, IAM, VPC, KMS, CloudTrail, GuardDuty)

---

## 🎓 Lessons Learned

**1. The shared responsibility model creates a false sense of security**
The most common assumption found during the assessment was that AWS "handles security." AWS handles infrastructure security - but every application-level, IAM, configuration, and data protection control is the customer's responsibility. Clarifying the shared responsibility boundary early is the most important first step in any cloud security assessment.

**2. 47% coverage sounds better than it is**
A 47% coverage rate across 15 selected controls means 53% of assessed controls have gaps. Across the full 93 Annex A controls, the coverage would almost certainly be lower. Assessment scope selection should never be used to inflate apparent compliance maturity.

**3. Logging and monitoring gaps are the most dangerous**
The absence of CloudTrail and GuardDuty meant that a breach could occur and remain undetected indefinitely. More than any other gap, the logging absence undermined every other security claim - without detection capability, the effectiveness of all other controls is unverifiable.

**4. Partner onboarding creates genuine security urgency**
Security assessments commissioned in advance of a commercial milestone (partner onboarding, fundraising, certification) produce better outcomes than routine assessments - leadership engagement is higher and remediation happens faster. The commercial dependency on completing Phase 1 was the primary driver of rapid MFA and logging remediation.

**5. DPIA is frequently overlooked until it becomes urgent**
VAI had not conducted a Data Protection Impact Assessment despite processing learner PII and payment data at scale. The DPIA requirement only became visible when international partner due diligence questionnaires asked for it. DPIAs should be conducted proactively for any new processing activity involving sensitive data.

**6. A gap analysis is not a certification**
This assessment surfaces gaps against 15 selected controls. It does not certify VAI against ISO 27001:2022 and should not be represented as such. The path from this gap analysis to certification requires a full 93-control assessment, risk treatment plan, ISMS implementation, internal audit, and Stage 1 and Stage 2 certification audits.

---

## ⚠️ Limitations

1. **15 controls assessed - not all 93** - This assessment covers the 15 controls most material to VAI's current risk profile. The remaining 78 Annex A controls were not assessed. Compliance against those controls is unknown.
2. **No penetration testing conducted** - Risk scores are based on configuration review and documentation assessment. Active exploitation testing was not performed. Actual vulnerabilities may be more severe than scored.
3. **Point-in-time assessment** - The findings reflect the control environment at the time of assessment. Controls implemented after the assessment date would improve coverage but are not reflected here.
4. **Self-reported evidence** - Some control ratings rely on stakeholder assertions that were not independently verified. An independent audit would apply greater scrutiny.
5. **AWS only** - This assessment covers the AWS environment. Any services, data, or processing outside AWS (staff personal devices, third-party SaaS tools, physical records) are outside this assessment's scope.
6. **47% coverage applies to assessed controls only** - The overall compliance posture across all 93 Annex A controls is not known and would require a full assessment to determine.
7. **Remediation effort estimates are indicative** - The effort ratings in the implementation roadmap are professional estimates based on typical AWS environments. Actual effort will depend on VAI's technical resources, existing configurations, and organisational capacity.

---

## 🏭 How This Project Would Change in Production

| Portfolio Version | Production Version |
|---|---|
| 15 controls assessed | Full 93-control ISO 27001:2022 Annex A assessment - all controls evaluated, justified inclusions and exclusions documented in a formal Statement of Applicability |
| One-time point-in-time assessment | Continuous compliance monitoring - CSPM tool (Vanta, Secureframe, or AWS Security Hub) provides real-time control status against ISO 27001 and CIS benchmarks |
| Qualitative scoring by single assessor | Risk assessment conducted with risk owners - each risk owner validates the scoring of risks in their domain; GRC facilitates, management owns |
| HTML dashboard as deliverable | Formal gap assessment report - executive summary, detailed findings, risk register, SoA, and remediation roadmap delivered as a structured document with management sign-off |
| Radar chart showing 47% coverage | Full ISMS implementation - policies, procedures, risk register, SoA, training records, audit evidence - not just a coverage chart |
| 90-day remediation roadmap | ISMS project plan with formal project governance - workstream owners, milestone tracking, steering committee oversight |
| No formal audit | Stage 1 documentation review and Stage 2 on-site certification audit conducted by accredited certification body |
| Partner onboarding readiness as the trigger | ISO 27001:2022 certification as the outcome - externally verified, time-bound, renewable through annual surveillance audits |
| GitHub-hosted static dashboard | GRC platform (Vanta, Drata, or ServiceNow GRC) - evidence automatically collected, control status continuously monitored, audit reports generated on demand |
| Single analyst | GRC function with defined roles - CISO, GRC Manager, System Owners, DPO, Internal Auditor - each with documented responsibilities in the ISMS |

---

## 🗺️ v2.0 Roadmap

- [ ] Expand assessment to cover all 93 ISO 27001:2022 controls
- [ ] Add automated control scoring based on evidence uploads
- [ ] Integrate AWS Security Hub findings into compliance dashboard
- [ ] Add NDPA compliance module for Nigerian data protection obligations

---

## 📄 License

MIT License - see [LICENSE](LICENSE) for details.
