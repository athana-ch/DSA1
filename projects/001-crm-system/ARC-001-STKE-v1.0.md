# Stakeholder Drivers & Goals Analysis: CRM System

> **Template Status**: Live | **Version**: 1.0 | **Command**: `/arckit:stakeholders`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-001-STKE-v1.0 |
| **Document Type** | Stakeholder Drivers & Goals Analysis |
| **Project** | CRM System (Project 001) |
| **Classification** | OFFICIAL |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-03-01 |
| **Last Modified** | 2026-03-01 |
| **Review Cycle** | Quarterly |
| **Next Review Date** | 2026-06-01 |
| **Owner** | Enterprise Architect |
| **Reviewed By** | PENDING |
| **Approved By** | PENDING |
| **Distribution** | Project Board, Business Unit Leaders, IT Leadership |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-03-01 | ArcKit AI | Initial creation from `/arckit:stakeholders` command | PENDING | PENDING |

---

## Executive Summary

### Purpose

This document identifies key stakeholders for the enterprise CRM system implementation, their underlying drivers (motivations, concerns, and pressures), how these drivers manifest into SMART goals, and the measurable outcomes that will prove those goals are achieved. The analysis provides the foundation for requirements prioritization, design trade-off decisions, communication planning, and change management.

### Key Findings

The CRM initiative has strong executive sponsorship and near-universal agreement that a unified customer view is needed, creating favourable conditions for alignment. The most significant tension exists between the **Finance Director's drive for cost discipline and proven ROI** and the **VP Sales's desire for rapid deployment** — a phased rollout strategy with early-win metrics is the recommended resolution. A secondary conflict exists between **Sales Representatives' preference for simplicity** and the **DPO's need for comprehensive data capture and audit trails**, which will require careful UX investment to resolve without compromising compliance.

### Critical Success Factors

- Unified customer data model delivered before go-live — a fragmented data migration will undermine every business case metric
- Sales Representative adoption rate reaching 80%+ within 60 days of go-live — adoption is the lead indicator for all revenue outcomes
- GDPR-compliant consent and data retention flows in place before processing any personal data in the new system
- Executive Sponsor maintaining visible championing through the change resistance period (months 2–4 post-go-live)
- Integration with the existing ERP and marketing automation platform completed on time — these are the critical dependencies for the 360-degree customer view

### Stakeholder Alignment Score

**Overall Alignment**: MEDIUM-HIGH

Strong strategic alignment across all senior stakeholders on the need for a CRM system. Moderate conflicts on pace, scope, and data governance controls. These conflicts are resolvable with a phased delivery approach and clear prioritization of user experience alongside compliance requirements.

---

## Stakeholder Identification

### Internal Stakeholders

| Stakeholder | Role/Department | Influence | Interest | Engagement Strategy |
|-------------|----------------|-----------|----------|---------------------|
| Chief Executive Officer | Executive Sponsor | HIGH | HIGH | Active involvement, steering board chair, monthly programme review |
| VP Sales | Sales Leadership | HIGH | HIGH | Weekly updates, requirements sign-off, pilot leadership |
| VP Marketing | Marketing Leadership | HIGH | HIGH | Requirements input, campaign integration design workshops |
| Head of Customer Service | Customer Service Leadership | HIGH | HIGH | Process redesign co-owner, agent training lead |
| IT Director / CTO | Technology Leadership | HIGH | HIGH | Architecture approval authority, integration design |
| Finance Director | Finance | HIGH | MEDIUM | Budget gate approvals, ROI milestone reviews |
| Data Protection Officer | Legal / Compliance | HIGH | MEDIUM | GDPR compliance sign-off, data processing review |
| Enterprise Architect | Architecture Team | MEDIUM | HIGH | Day-to-day technical governance, design decisions |
| Sales Representatives (100+) | Sales Operations | LOW | HIGH | User testing, feedback sessions, change ambassador network |
| Customer Service Agents (60+) | Customer Service | LOW | HIGH | UAT, training, feedback sessions |
| Marketing Team (25) | Marketing Operations | LOW | HIGH | Campaign integration testing, data quality review |
| IT Operations / Support | IT | MEDIUM | MEDIUM | Transition planning, runbooks, on-call readiness |
| HR Director | HR | LOW | LOW | Change management communications, training resource approval |

### External Stakeholders

| Stakeholder | Organization | Relationship | Influence | Interest |
|-------------|--------------|--------------|-----------|----------|
| CRM Platform Vendor | TBD (post-procurement) | Supplier / Implementation Partner | MEDIUM | HIGH |
| Systems Integration Partner | TBD (post-procurement) | Delivery Partner | MEDIUM | HIGH |
| ICO (Information Commissioner's Office) | Regulatory Body | Regulatory Oversight | HIGH | LOW |
| Customers (B2B and B2C) | External | Service Beneficiary | LOW | HIGH |
| ERP Vendor (existing) | External | Integration Dependency | MEDIUM | MEDIUM |

### Stakeholder Power-Interest Grid

```text
                          INTEREST
              Low                         High
        ┌─────────────────────┬─────────────────────┐
        │                     │                     │
        │   KEEP SATISFIED    │   MANAGE CLOSELY    │
   High │                     │                     │
        │  • Finance Director │  • CEO              │
        │  • DPO / Legal      │  • VP Sales         │
        │  • ICO (Regulator)  │  • VP Marketing     │
 P      │                     │  • Head Cust. Svc   │
 O      │                     │  • IT Director/CTO  │
 W      ├─────────────────────┼─────────────────────┤
 E      │                     │                     │
 R      │      MONITOR        │    KEEP INFORMED    │
        │                     │                     │
   Low  │  • HR Director      │  • Sales Reps       │
        │  • Industry Bodies  │  • CS Agents        │
        │                     │  • Marketing Team   │
        │                     │  • IT Operations    │
        └─────────────────────┴─────────────────────┘
```

| Stakeholder | Power | Interest | Quadrant | Engagement Strategy |
|-------------|-------|----------|----------|---------------------|
| CEO | HIGH | HIGH | Manage Closely | Monthly steering board, exception escalation |
| VP Sales | HIGH | HIGH | Manage Closely | Weekly status, co-lead pilot |
| VP Marketing | HIGH | HIGH | Manage Closely | Weekly status, design workshops |
| Head of Customer Service | HIGH | HIGH | Manage Closely | Weekly status, process redesign workshops |
| IT Director / CTO | HIGH | HIGH | Manage Closely | Architecture reviews, integration design |
| Finance Director | HIGH | MEDIUM | Keep Satisfied | Budget checkpoints, ROI milestone reports |
| DPO / Legal | HIGH | MEDIUM | Keep Satisfied | GDPR review gates, data processing sign-offs |
| ICO | HIGH | LOW | Keep Satisfied | No direct engagement unless breach; maintain audit trail |
| Sales Representatives | LOW | HIGH | Keep Informed | Demos, feedback surveys, ambassador network |
| Customer Service Agents | LOW | HIGH | Keep Informed | UAT sessions, training previews, feedback |
| Marketing Team | LOW | HIGH | Keep Informed | Sprint reviews, integration testing invitations |
| IT Operations | MEDIUM | MEDIUM | Keep Informed | Release notifications, runbook reviews |
| HR Director | LOW | LOW | Monitor | Quarterly updates via programme newsletter |

**Quadrant Interpretation:**
- **Manage Closely** (High Power, High Interest): Key decision-makers requiring active engagement
- **Keep Satisfied** (High Power, Low Interest): Influential stakeholders needing periodic updates
- **Keep Informed** (Low Power, High Interest): Engaged stakeholders needing regular communication
- **Monitor** (Low Power, Low Interest): Minimal engagement required

---

## Stakeholder Drivers Analysis

### SD-1: CEO / Executive Sponsor — Competitive Differentiation Through Customer Intelligence

**Stakeholder**: Chief Executive Officer

**Driver Category**: STRATEGIC

**Driver Statement**: The CEO needs the organization to move from a fragmented, spreadsheet-driven approach to customer management toward a data-led competitive capability. Board-level pressure exists to demonstrate growth in customer lifetime value and market share, and the CEO has personally committed to a "customer-first transformation" as a strategic pillar for 2026–2028.

**Context & Background**: The current inability to produce a single view of the customer means sales, marketing, and service teams operate in silos. Key accounts are being managed across 4–5 separate tools with no shared context. Competitor intelligence suggests at least two direct competitors have deployed modern CRM platforms in the past 18 months, creating a risk of capability gap in account management and upsell.

**Driver Intensity**: CRITICAL

**Enablers** (What would help):
- A compelling business case that connects CRM investment directly to revenue growth metrics the board tracks
- Early wins (quick deployments of high-value use cases) that demonstrate momentum

**Blockers** (What would hinder):
- A prolonged discovery/procurement phase with no visible early delivery
- Internal political friction between VP Sales and VP Marketing over CRM ownership

**Related Stakeholders**: VP Sales (aligned — revenue growth), VP Marketing (aligned — market intelligence), Finance Director (partially aligned — needs ROI evidence)

---

### SD-2: VP Sales — Increase Revenue and Improve Pipeline Visibility

**Stakeholder**: VP Sales

**Driver Category**: FINANCIAL / OPERATIONAL

**Driver Statement**: The VP Sales needs accurate, real-time pipeline visibility to forecast revenue reliably, identify deals at risk, and coach the sales team. Currently, pipeline data is maintained in individual spreadsheets and updated inconsistently, leading to 30–40% forecast variance. The VP Sales also needs to reduce time spent in management reporting and increase time the team spends in front of customers.

**Context & Background**: The CEO has set a 15% revenue growth target for FY2026/27. The VP Sales has committed to this target but cannot manage toward it without a reliable pipeline system. Monthly forecast meetings are currently preceded by a 2-day manual consolidation effort from 12 regional sales managers.

**Driver Intensity**: CRITICAL

**Enablers** (What would help):
- Mobile-accessible CRM that sales reps can update immediately after customer meetings
- Integration with email and calendar to auto-capture activity without manual logging
- Pipeline dashboards visible to regional managers without requiring IT assistance

**Blockers** (What would hinder):
- A complex system that increases admin burden rather than reducing it (will kill adoption)
- Poor data migration that leaves historical deal data unavailable at go-live
- A long rollout timeline that delays pipeline visibility improvements

**Related Stakeholders**: Sales Representatives (SD-8 — must adopt for data to be reliable), Finance Director (SD-6 — forecast accuracy has direct financial planning implications), CEO (SD-1 — aligned on revenue growth)

---

### SD-3: VP Marketing — Improve Lead Quality and Demonstrate Campaign ROI

**Stakeholder**: VP Marketing

**Driver Category**: OPERATIONAL / FINANCIAL

**Driver Statement**: Marketing currently generates leads that are passed to sales with no closed-loop feedback — the team has no visibility into which campaigns produce revenue, not just pipeline. The VP Marketing needs to demonstrate campaign ROI to justify the £1.2M annual marketing budget and shift budget allocation toward high-performing channels.

**Context & Background**: The Finance Director has signalled that marketing budget will face scrutiny in the next budget cycle unless attribution data improves. The VP Marketing also wants to implement account-based marketing (ABM) for the top 50 enterprise accounts, which requires CRM data on account penetration and relationship strength.

**Driver Intensity**: HIGH

**Enablers** (What would help):
- Bi-directional integration between CRM and the existing marketing automation platform (HubSpot)
- Closed-loop reporting from lead creation through to closed deal, attributed to campaign source
- Account-level data visible to marketing team to enable ABM targeting

**Blockers** (What would hinder):
- CRM deployed as a sales-only tool without marketing integration
- Poor lead data quality due to inconsistent data entry standards
- GDPR consent not captured at lead stage, preventing email nurture campaigns

**Related Stakeholders**: VP Sales (SD-2 — lead handoff quality), DPO (SD-7 — consent management), Finance Director (SD-6 — budget justification)

---

### SD-4: Head of Customer Service — Reduce Resolution Time and Improve Agent Experience

**Stakeholder**: Head of Customer Service

**Driver Category**: OPERATIONAL / CUSTOMER

**Driver Statement**: Customer service agents currently switch between 3–4 systems to answer a single customer query — the ticketing system, the billing platform, the order management system, and email. Average handle time is 8.5 minutes per interaction. The Head of Customer Service needs agents to have a single, consolidated view of the customer to reduce handle time, reduce escalations, and improve first-call resolution.

**Context & Background**: The most recent customer satisfaction survey scored the service team at 68 NPS. Exit interview analysis shows "having to repeat myself to agents" as the top customer frustration. Staff turnover in the customer service team is at 28% annually, with "frustrating systems" cited in 40% of exit interviews. There is a direct business case for CRM investment in reducing churn (cost of replacing a CS agent is estimated at £8,000 including recruitment and training).

**Driver Intensity**: HIGH

**Enablers** (What would help):
- CRM integration with the ticketing system and billing platform to provide a unified customer timeline
- Screen-pop capability linking incoming calls (via telephony CTI) to the customer's CRM record
- Case management workflow that routes and escalates automatically, reducing manual triage

**Blockers** (What would hinder):
- CRM deployed as a sales-only system with no service module or case management
- Integration with telephony (CTI) deprioritized or descoped
- Agents not involved in UAT — system designed without frontline input

**Related Stakeholders**: Customers (SD-10 — satisfaction and retention), Sales Representatives (SD-8 — shared customer data), IT Director (SD-5 — integration complexity)

---

### SD-5: IT Director / CTO — Consolidate Technical Debt and Establish Scalable Architecture

**Stakeholder**: IT Director / CTO

**Driver Category**: STRATEGIC / OPERATIONAL

**Driver Statement**: The current customer-facing technology landscape spans 11 separate systems with point-to-point integrations that are brittle, poorly documented, and expensive to maintain. The IT Director needs the CRM to serve as a system-of-record for customer data, reducing the number of systems and integration touchpoints, and to establish a stable integration foundation (API-first) that can support future capabilities.

**Context & Background**: IT operations currently spends approximately 35% of its time supporting integrations between the existing fragmented systems. There have been 3 data incidents in the past 18 months caused by synchronization failures between the sales CRM (Salesforce starter edition), the CS ticketing tool (Zendesk), and the billing system (custom). The annual cost of these integration maintenance activities is estimated at £180,000.

**Driver Intensity**: HIGH

**Enablers** (What would help):
- An API-first CRM platform with documented REST/GraphQL APIs and webhook support
- Integration platform (iPaaS) deployed alongside CRM to manage all integration flows centrally
- Vendor commitment to a managed SaaS model, reducing on-premise infrastructure footprint

**Blockers** (What would hinder):
- Business pressure to replicate the exact behaviour of legacy systems rather than redesigning processes
- Insufficient time allocated for data cleansing before migration
- Shadow IT — business units procuring additional tools outside the CRM ecosystem

**Related Stakeholders**: Head of Customer Service (SD-4 — integration dependencies), Enterprise Architect (design authority), Finance Director (SD-6 — infrastructure cost reduction)

---

### SD-6: Finance Director — Demonstrate ROI and Control Programme Cost

**Stakeholder**: Finance Director

**Driver Category**: FINANCIAL / RISK

**Driver Statement**: The Finance Director needs to see a credible, time-bound return on the CRM investment before approving full programme funding. The total budget envelope is £850,000 over 18 months. The Finance Director will release funds in tranches tied to milestone evidence, and expects a full ROI breakeven within 24 months of go-live.

**Context & Background**: The organization has had two previous technology programmes that overran budget and underdelivered benefits. The Finance Director is risk-averse about technology investment and requires independent validation of benefits realization at each major milestone. The CFO has specifically requested that benefits be quantified in hard cash terms (revenue increase or cost reduction), not "strategic value" or "efficiency improvements" without monetary quantification.

**Driver Intensity**: HIGH

**Enablers** (What would help):
- A detailed benefits realization plan with named benefit owners, baseline measurements, and target dates
- Monthly benefits tracking report included in programme governance from day one
- Phased funding release tied to measurable milestones (rather than a single upfront commitment)

**Blockers** (What would hinder):
- Scope creep that increases costs without proportional benefit
- Benefit realisation delayed by slow adoption or integration issues
- Inability to isolate CRM contribution from other revenue-growth activities

**Related Stakeholders**: CEO (SD-1 — strategic investment justification), VP Sales (SD-2 — revenue outcomes), IT Director (SD-5 — cost reduction through consolidation)

---

### SD-7: Data Protection Officer — GDPR Compliance and Data Governance

**Stakeholder**: Data Protection Officer (DPO)

**Driver Category**: COMPLIANCE / RISK

**Driver Statement**: The DPO needs to ensure that the CRM system processes personal data lawfully, with appropriate consent, retention controls, and subject access request (SAR) capabilities. The current system has no automated data retention enforcement, and responding to SARs currently takes 12–18 hours of manual effort per request. A data breach or ICO enforcement action would carry reputational and financial penalties of up to 4% of global annual turnover.

**Context & Background**: The organization received an ICO advisory notice 14 months ago following a data subject complaint about marketing emails sent without valid consent. The DPO has been under board-level scrutiny since and needs visible, auditable compliance controls built into the CRM from the outset. The CRM will hold personal data for both B2B contacts and B2C customers, including purchase history, communication preferences, and service interaction records.

**Driver Intensity**: CRITICAL

**Enablers** (What would help):
- CRM platform with built-in consent management, data retention rules, and automated deletion workflows
- Full audit log of all data access and modifications, exportable for SAR/regulatory response
- Data processing agreement (DPA) with the CRM vendor reviewed and signed before go-live
- Privacy impact assessment completed before data migration

**Blockers** (What would hinder):
- CRM vendor unable to commit to EU/UK data residency
- Data migration that imports legacy contacts without validated consent records
- Marketing team bypassing consent controls to maximise campaign reach

**Related Stakeholders**: VP Marketing (SD-3 — consent at lead capture), IT Director (SD-5 — data architecture), ICO (external regulatory oversight)

---

### SD-8: Sales Representatives — Reduce Admin Burden and Get More Selling Time

**Stakeholder**: Sales Representatives (100+ users)

**Driver Category**: PERSONAL / OPERATIONAL

**Driver Statement**: Sales representatives want a system that makes their job easier, not harder. They currently spend approximately 2.5 hours per day on CRM-related admin across multiple tools. They want a single place to log activity, see customer history, manage their pipeline, and get reminders — ideally without duplicating data entry from email or calendar. Their personal driver is maximizing commission-earning selling time.

**Context & Background**: Two previous attempts to enforce CRM usage (a Salesforce starter edition rollout in 2022 and a spreadsheet-based approach before that) both failed due to poor adoption — compliance was under 40% after 6 months. Sales representatives have significant informal power: if they don't adopt the CRM, the entire business case collapses. The VP Sales has acknowledged that the new system "must win the hearts and minds of the sales team" and has agreed to co-lead a pilot group of 10 enthusiastic reps.

**Driver Intensity**: CRITICAL (adoption risk is existential to the programme)

**Enablers** (What would help):
- Mobile app with offline sync for reps who travel frequently
- Email/calendar integration (Gmail or O365) that auto-logs activities without manual entry
- Visible personal benefit: each rep sees their own pipeline, forecast, and next-best-action recommendations
- Change champion network: 10 pilot reps who shape the configuration before company-wide rollout

**Blockers** (What would hinder):
- A complex, form-heavy interface that takes longer to use than a spreadsheet
- Mandatory fields that feel irrelevant to the rep's day-to-day selling activity
- No mobile access or a poor mobile experience
- Rollout without adequate training or with insufficient time in the schedule

**Related Stakeholders**: VP Sales (SD-2 — pipeline data quality depends on rep adoption), Head of Customer Service (SD-4 — shared customer data), DPO (SD-7 — compliance requirements add fields reps find burdensome)

---

### SD-9: Customer Service Agents — Single View of Customer and Faster Case Resolution

**Stakeholder**: Customer Service Agents (60+ users)

**Driver Category**: OPERATIONAL / PERSONAL

**Driver Statement**: Customer service agents need to see the full customer history — purchases, past cases, account status, communication preferences — in a single screen without switching systems. Their personal driver is reducing the stress and embarrassment of asking customers to repeat themselves, and reducing the frequency of escalations that reflect poorly on individual performance metrics.

**Context & Background**: The current average handle time of 8.5 minutes is significantly above the 5-minute industry benchmark. Agents have raised complaints through the employee engagement survey about "system switching" and "not having the right information." The introduction of a unified CRM with integrated case management and a customer 360 view is expected to reduce handle time by 30–40%.

**Driver Intensity**: HIGH

**Enablers** (What would help):
- Unified customer timeline showing all interactions across sales, marketing, and service
- Case templates and knowledge base integration reducing time to find solutions
- CTI (computer telephony integration) screen-pop linking caller ID to customer record

**Blockers** (What would hinder):
- CRM deployed without service/case management module
- Poor data migration that shows incomplete customer history at go-live
- Agents excluded from UAT — system configured by IT without frontline input

**Related Stakeholders**: Head of Customer Service (SD-4), Customers (SD-10), IT Director (SD-5 — integration delivery)

---

### SD-10: Customers — Faster, More Personalised Service Experience

**Stakeholder**: End Customers (B2B and B2C)

**Driver Category**: CUSTOMER

**Driver Statement**: Customers want to be known and understood by the organization — not asked to repeat information they have already provided, not transferred between agents with no context, and not sent irrelevant marketing communications. They want fast resolution of issues and proactive communication about their account.

**Context & Background**: The most recent NPS survey scored 51, down from 58 two years ago. The decline correlates with growth in customer base outpacing the capacity of manual coordination between sales and service teams. B2B customers (who represent 70% of revenue) specifically cite "disjointed account management" as a frustration. B2C customers cite "slow complaint resolution" as the top dissatisfier.

**Driver Intensity**: HIGH

**Enablers** (What would help):
- Agents and sales reps with full context before a customer interaction starts
- Proactive outreach when accounts are at risk or renewals are approaching
- Self-service options (customer portal) for case status and account management

**Blockers** (What would hinder):
- CRM implemented as an internal tool with no customer-facing touchpoints
- Poor data quality meaning the "360 view" contains outdated or incorrect information

**Related Stakeholders**: Head of Customer Service (SD-4), VP Sales (SD-2 — retention and upsell), VP Marketing (SD-3 — segmentation and personalisation)

---

## Driver-to-Goal Mapping

### Goal G-1: Increase Annual Revenue by 15% Within 12 Months of Go-Live

**Derived From Drivers**: SD-1, SD-2, SD-10

**Goal Owner**: VP Sales (accountable), CEO (sponsor)

**Goal Statement**: Achieve 15% growth in annual recurring revenue (ARR) within 12 months of CRM go-live, measured against the pre-go-live 12-month baseline, attributable to improved pipeline management, faster deal closure, and reduced churn.

**Why This Matters**: The CEO's strategic commitment to customer-first transformation is only credible if it produces measurable revenue growth. The VP Sales has personally committed to 15% growth and needs the CRM as the primary enabling tool. Revenue growth also satisfies the Finance Director's demand for hard financial returns.

**Success Metrics**:
- **Primary Metric**: Annual Recurring Revenue (ARR) growth percentage
- **Secondary Metrics**:
  - Pipeline conversion rate (leads to closed deals)
  - Average deal cycle duration (days)
  - Revenue at risk (deals in pipeline past expected close date)

**Baseline**: Current ARR = £8.4M; current pipeline conversion rate = 18%; average deal cycle = 62 days

**Target**: ARR = £9.66M (+15%); pipeline conversion rate = 23%; average deal cycle = 45 days

**Measurement Method**: CRM revenue reporting dashboard, validated against finance system monthly close figures

**Dependencies**:
- Sales team adoption rate reaches 80%+ within 60 days of go-live
- Historical deal data successfully migrated to populate pipeline baseline
- Integration with finance/billing system to capture actual closed revenue

**Risks to Achievement**:
- Low CRM adoption by sales reps undermines pipeline data quality, making revenue tracking unreliable
- 15% target assumes market conditions stable — macro-economic downturn could suppress results independent of CRM

---

### Goal G-2: Reduce Average Deal Cycle from 62 Days to 45 Days by Q4 2026

**Derived From Drivers**: SD-2, SD-8

**Goal Owner**: VP Sales

**Goal Statement**: Reduce the average time from opportunity creation to closed-won deal from 62 days to 45 days by Q4 2026 (October 2026), by automating next-best-action prompts, improving stakeholder mapping within accounts, and removing manual handoff delays.

**Why This Matters**: A shorter deal cycle means faster revenue recognition, lower cost of sale, and higher rep capacity (each rep can manage more deals simultaneously). For the VP Sales, this is a direct leverage point on revenue without increasing headcount.

**Success Metrics**:
- **Primary Metric**: Average opportunity age at close (days)
- **Secondary Metrics**:
  - Number of overdue stage-progression activities per week
  - Rep response time to inbound leads (minutes to first contact)

**Baseline**: Average deal cycle = 62 days; overdue activities = estimated 140/week across team; lead response time = unknown (untracked)

**Target**: Average deal cycle = 45 days; overdue activities = fewer than 30/week; lead response time = under 15 minutes for hot leads

**Measurement Method**: CRM opportunity pipeline analytics, measured weekly and reported monthly to VP Sales

**Dependencies**:
- CRM workflow automation configured for stage-progression alerts
- Email and calendar integration capturing actual activity without manual logging
- Sales process standardisation across all 12 regional teams (process workshop required pre-go-live)

**Risks to Achievement**:
- Regional sales managers resist standardised sales process, maintaining local variations
- Email/calendar integration technically complex to configure for all rep devices

---

### Goal G-3: Achieve GDPR-Compliant Data Governance Before Processing Personal Data

**Derived From Drivers**: SD-7, SD-5

**Goal Owner**: DPO (accountable), IT Director (responsible for technical controls)

**Goal Statement**: Before any personal data is migrated into or processed by the new CRM system, implement and verify: (a) consent management covering all B2C contact records, (b) automated data retention rules aligned to the organization's data retention schedule, (c) SAR response capability reducing manual effort from 18 hours to under 2 hours, and (d) a signed Data Processing Agreement with the CRM vendor.

**Why This Matters**: GDPR non-compliance carries penalties up to 4% of global annual turnover. The organization already has an ICO advisory notice on its record. The DPO requires this goal to be met as a go/no-go condition for migration sign-off. Meeting this goal also builds customer trust and reduces reputational risk.

**Success Metrics**:
- **Primary Metric**: 100% of migrated contact records have a documented lawful basis for processing
- **Secondary Metrics**:
  - SAR response time (hours of manual effort per request)
  - Percentage of contacts with verified consent status (where consent is the lawful basis)
  - Audit log coverage (100% of data access events logged)

**Baseline**: Current consent coverage = unknown (estimated 45% have valid documented consent); SAR response time = 12–18 hours; audit log = non-existent

**Target**: Consent coverage = 100% (all records with documented lawful basis); SAR response time = under 2 hours; audit log = 100% of access events

**Measurement Method**: CRM compliance dashboard, quarterly review by DPO with IT audit support

**Dependencies**:
- CRM vendor provides UK/EU data residency and a compliant Data Processing Agreement
- Data migration includes a pre-migration consent validation exercise (cleanse before migrate)
- Legal team completes updated Privacy Notice and consent capture language before go-live

**Risks to Achievement**:
- Large volume of legacy contact records with no consent documentation may require opt-in re-permission campaign
- CRM vendor data residency options may not fully satisfy UK GDPR post-Brexit requirements

---

### Goal G-4: Reduce Customer Case Average Handle Time from 8.5 to 5.5 Minutes by Q3 2026

**Derived From Drivers**: SD-4, SD-9, SD-10

**Goal Owner**: Head of Customer Service

**Goal Statement**: Reduce the average handle time per customer service interaction from 8.5 minutes to 5.5 minutes by Q3 2026 (July 2026), by providing agents with a unified customer 360 view, automated case routing, and a knowledge base integration — reducing system-switching time and manual triage effort.

**Why This Matters**: Each minute saved per interaction represents approximately £42,000 in annual labour cost savings across the 60-agent team. Beyond cost, reducing handle time directly improves customer experience (fewer transfers, less repetition), and reduces agent stress and turnover — addressing the 28% annual attrition rate that costs £480,000 per year in recruitment and training.

**Success Metrics**:
- **Primary Metric**: Average handle time per interaction (minutes)
- **Secondary Metrics**:
  - First contact resolution (FCR) rate
  - Number of system logins required per interaction
  - Customer effort score (CES) from post-interaction survey

**Baseline**: Average handle time = 8.5 minutes; FCR = 61%; system logins per interaction = 3.8; CES = 5.2/10

**Target**: Average handle time = 5.5 minutes; FCR = 75%; system logins per interaction = 1 (CRM only); CES = 7.5/10

**Measurement Method**: ACD (Automatic Call Distribution) system reports, monthly CS performance dashboard

**Dependencies**:
- CRM service module deployed with case management and customer 360 view
- CTI integration with telephony platform delivering screen-pop to CRM record
- Integration with billing and order management systems to populate customer history

**Risks to Achievement**:
- CTI integration technically complex — if descoped, handle time reduction will be partial
- Incomplete data migration means agents still have to switch to legacy systems for historical data

---

### Goal G-5: Achieve Measurable ROI Breakeven Within 24 Months of Go-Live

**Derived From Drivers**: SD-6, SD-1

**Goal Owner**: Finance Director (accountable), Programme Director (responsible)

**Goal Statement**: Demonstrate full ROI breakeven (cumulative benefits exceeding cumulative costs including implementation and ongoing licences) within 24 months of CRM go-live, with hard financial evidence validated by the Finance team.

**Why This Matters**: The Finance Director will release the final tranche of the £850,000 budget only on confidence that the investment will break even within 24 months. Achieving this goal is also the primary metric by which the CEO will judge the programme's success at board level.

**Success Metrics**:
- **Primary Metric**: Cumulative net benefit (£) — total benefits realised minus total costs incurred, measured monthly
- **Secondary Metrics**:
  - Revenue attributable to CRM (incremental vs baseline)
  - Cost savings from reduced CS handling and legacy system decommissioning
  - IT integration maintenance cost reduction

**Baseline**: Programme cost = £850,000 (implementation) + approximately £180,000/year ongoing; current IT integration maintenance = £180,000/year; current CS agent turnover cost = £480,000/year

**Target**: Cumulative net benefit positive by month 24 post-go-live; target 3-year total benefit = £1.8M (2.1x ROI)

**Measurement Method**: Monthly benefits realisation report, signed off by Finance Director and Programme Director

**Dependencies**:
- Goals G-1 (revenue growth), G-4 (CS cost reduction), and G-5 (IT consolidation savings) all delivering to target
- Legacy system decommissioning plan executed within 12 months of go-live to release licence savings

**Risks to Achievement**:
- Revenue growth targets miss due to low adoption or market conditions
- Legacy system decommissioning delayed, preventing cost savings from materialising
- Hidden implementation costs (data migration, customisation) exceeding budget contingency

---

### Goal G-6: Consolidate from 11 Customer-Facing Systems to 3 by Month 18 Post-Go-Live

**Derived From Drivers**: SD-5, SD-6

**Goal Owner**: IT Director

**Goal Statement**: Reduce the number of distinct systems in the customer-facing technology landscape from 11 to 3 (CRM, ERP/billing integration, marketing automation) within 18 months of go-live, by migrating data, decommissioning redundant licences, and eliminating all point-to-point integrations in favour of the new integration layer.

**Why This Matters**: The current 11-system estate costs £180,000/year in integration maintenance and generates data inconsistency incidents. System consolidation directly reduces IT operational cost, reduces incident risk, and enables the unified customer data model that all other goals depend on.

**Success Metrics**:
- **Primary Metric**: Number of active customer-facing systems
- **Secondary Metrics**:
  - Number of active point-to-point integrations
  - Annual integration maintenance cost
  - Number of data inconsistency incidents per quarter

**Baseline**: 11 systems; estimated 17 point-to-point integrations; £180,000/year maintenance cost; 3 data incidents in 18 months

**Target**: 3 systems; 0 point-to-point integrations; under £60,000/year maintenance; 0 data incidents per year

**Measurement Method**: IT asset register, integration inventory audit, incident log

**Dependencies**:
- CRM platform selected with sufficient functionality to replace sales, service, and light marketing use cases
- IT operations capacity to execute parallel decommissioning workstreams alongside CRM implementation
- Business agreement to standardise on CRM workflows rather than maintaining legacy tool workarounds

**Risks to Achievement**:
- Individual teams resist decommissioning tools they are comfortable with (shadow IT risk)
- Data migration complexity causes decommissioning to be delayed beyond 18-month target
- New integration layer introduces its own complexity or instability during early operation

---

## Goal-to-Outcome Mapping

### Outcome O-1: 15% Increase in Annual Recurring Revenue Within 12 Months of Go-Live

**Supported Goals**: G-1, G-2

**Outcome Statement**: Annual Recurring Revenue grows from £8.4M to £9.66M (increase of £1.26M) within 12 months of CRM go-live, driven by improved pipeline management, reduced deal cycle, and lower churn.

**Measurement Details**:
- **KPI**: Annual Recurring Revenue (ARR)
- **Current Value**: £8.4M (12-month trailing baseline at CRM go-live)
- **Target Value**: £9.66M at month 12 post-go-live
- **Measurement Frequency**: Monthly
- **Data Source**: Finance system (ERP billing), reconciled against CRM closed-won pipeline
- **Report Owner**: Finance Director, with input from VP Sales

**Business Value**:
- **Financial Impact**: £1.26M incremental annual revenue; additional gross margin approximately £630,000 at 50% margin
- **Strategic Impact**: Demonstrates board-level digital transformation programme is delivering; supports continued investment in customer capability
- **Operational Impact**: Enables sales team to scale without proportional headcount increase
- **Customer Impact**: Faster deal cycles mean customers can access solutions sooner; proactive account management reduces churn

**Timeline**:
- **Phase 1 (Months 1–3 post go-live)**: Pipeline data quality improving; lead tracking active; target 3% ARR growth — £8.65M
- **Phase 2 (Months 4–6)**: Automated workflows reducing deal cycle; first upsell campaigns active — target 8% ARR growth — £9.07M
- **Phase 3 (Months 7–12)**: Full pipeline management operational; ABM campaigns running — target 15% ARR growth — £9.66M
- **Sustainment (Year 2+)**: Maintain 12–15% annual growth with CRM as core sales operating system

**Stakeholder Benefits**:
- **CEO**: Evidence of strategic investment return; board-level KPI achieved
- **VP Sales**: Team performance against target; personal credibility protected
- **Finance Director**: Hard financial return justifying programme investment
- **Sales Representatives**: Commission earnings growth from larger, faster-closing deals

**Leading Indicators** (early signals of success):
- CRM adoption rate among sales reps (target 80%+ by day 60)
- Pipeline data completeness score (% of active opportunities with all required fields populated)
- Lead response time (target under 15 minutes for inbound hot leads)

**Lagging Indicators** (final proof of success):
- Closed-won revenue month 12 vs baseline
- Pipeline conversion rate at 12-month mark
- Average deal cycle duration at 12-month mark

---

### Outcome O-2: Customer CSAT Score Increases from 68 to 82 NPS by Month 12 Post-Go-Live

**Supported Goals**: G-4, G-1

**Outcome Statement**: Net Promoter Score (NPS) for the service and sales experience increases from 51 to 68 within 12 months of go-live, measured through quarterly customer satisfaction surveys, driven by faster case resolution, reduced customer effort, and more personalised engagement.

**Measurement Details**:
- **KPI**: Net Promoter Score (NPS)
- **Current Value**: NPS = 51 (most recent quarterly survey)
- **Target Value**: NPS = 68 at 12-month post-go-live survey
- **Measurement Frequency**: Quarterly survey (n = 400+ respondents)
- **Data Source**: Customer satisfaction survey platform, triggered post-interaction and quarterly relationship survey
- **Report Owner**: Head of Customer Service (service NPS), VP Sales (relationship NPS)

**Business Value**:
- **Financial Impact**: Each 1-point NPS improvement is correlated with approximately 0.5% reduction in B2B churn; target NPS improvement of 17 points represents an estimated £290,000 in protected recurring revenue annually
- **Strategic Impact**: NPS improvement supports renewal and upsell conversations; customers who are Promoters generate 2.5x referral value
- **Operational Impact**: Reduced churn reduces the volume of recovery work required from sales and service teams
- **Customer Impact**: Measurably better service experience — faster resolution, less effort, better personalisation

**Timeline**:
- **Phase 1 (Months 1–3)**: Service module live; agents have customer 360 — target NPS improvement +3 points (NPS 54)
- **Phase 2 (Months 4–6)**: CTI screen-pop active; FCR improving — target NPS improvement +7 points (NPS 58)
- **Phase 3 (Months 7–12)**: Proactive account management, ABM, and renewal tracking active — target NPS 68
- **Sustainment (Year 2+)**: Maintain NPS above 70 through continuous improvement cycle

**Stakeholder Benefits**:
- **Head of Customer Service**: Departmental KPI achieved; reduction in escalations and complaints
- **CEO**: Customer satisfaction is a board metric; improvement supports brand reputation
- **Customers**: Directly experience faster, more personalised service
- **Sales Representatives**: Satisfied customers are easier renewal conversations

**Leading Indicators** (early signals of success):
- Agent average handle time reduction (target 5.5 minutes within 6 months)
- First contact resolution rate (target 75% within 6 months)
- Customer effort score post-interaction (target 7.5/10 within 6 months)

**Lagging Indicators** (final proof of success):
- NPS at quarterly survey post-12 months
- Customer churn rate at 12-month mark vs pre-CRM baseline
- Renewal rate for B2B accounts within the first post-CRM renewal cycle

---

### Outcome O-3: Full GDPR Compliance with Zero ICO Enforcement Actions

**Supported Goals**: G-3

**Outcome Statement**: Zero data subject complaints escalated to the ICO within 24 months of go-live, and zero enforcement actions or advisory notices issued. 100% of contact records processed under a documented and verified lawful basis. SAR response time under 2 hours for 95% of requests.

**Measurement Details**:
- **KPI**: Number of ICO complaints / enforcement actions; SAR response time; consent coverage percentage
- **Current Value**: 1 advisory notice in last 14 months; SAR response time = 12–18 hours; consent coverage = estimated 45%
- **Target Value**: 0 enforcement actions; SAR response time = under 2 hours (95th percentile); consent coverage = 100%
- **Measurement Frequency**: Monthly (compliance dashboard); annual external audit
- **Data Source**: CRM compliance module; DPO audit log; ICO correspondence register
- **Report Owner**: DPO

**Business Value**:
- **Financial Impact**: Avoidance of ICO fine (maximum 4% global annual turnover = up to £420,000 at current revenue); avoidance of reputational damage
- **Strategic Impact**: GDPR compliance enables marketing campaigns without legal risk; builds customer trust
- **Operational Impact**: Automated retention and consent management reduces manual DPO workload by an estimated 60%
- **Customer Impact**: Customers receive only communications they have consented to; data handled with transparency

**Timeline**:
- **Phase 1 (Months 1–3 pre-go-live)**: DPA signed; privacy notice updated; consent validation exercise completed
- **Phase 2 (Go-live)**: 100% of migrated records have documented lawful basis; SAR workflow active
- **Phase 3 (Months 1–6 post go-live)**: Automated retention rules enforced; first SAR under 2-hour SLA completed
- **Sustainment (Year 2+)**: Annual GDPR audit with CRM compliance dashboard as primary evidence

**Stakeholder Benefits**:
- **DPO**: Board-level confidence in compliance posture; reduced manual workload
- **CEO**: Reduced regulatory and reputational risk
- **VP Marketing**: Legal foundation for email marketing campaigns
- **Customers**: Transparent, consent-based data management

**Leading Indicators** (early signals of success):
- Percentage of migrated records with documented lawful basis (target 100% at migration)
- DPA signed with vendor (target before migration start)
- First SAR completed under 2-hour SLA within 30 days of go-live

**Lagging Indicators** (final proof of success):
- Zero ICO complaints in 12 months post-go-live
- Zero enforcement notices in 24 months
- Annual external privacy audit rating: compliant

---

### Outcome O-4: Positive ROI Demonstrated Within 24 Months — Cumulative Benefit of £1.8M

**Supported Goals**: G-5, G-6, G-1, G-4

**Outcome Statement**: The CRM programme delivers cumulative financial benefit of £1.8M within 24 months of go-live against a total investment of £850,000 (implementation) plus £360,000 (2 years ongoing licence and support), representing a net benefit of £590,000 and a 2.1x return on investment.

**Measurement Details**:
- **KPI**: Cumulative net benefit (£)
- **Current Value**: £0 (pre-programme baseline)
- **Target Value**: £1.8M cumulative by month 24
- **Measurement Frequency**: Monthly (benefits realisation report)
- **Data Source**: Finance system (revenue), IT cost reports, CS operations cost reports
- **Report Owner**: Finance Director, Programme Director

**Business Value Composition**:

| Benefit Stream | Annual Value | Source |
|----------------|-------------|--------|
| Revenue growth (G-1) | £630,000 | 50% margin on £1.26M ARR increase |
| CS handle time reduction (G-4) | £210,000 | 3 minutes saved x 60 agents x 30,000 calls/month |
| Agent turnover reduction (G-4) | £190,000 | 10% improvement in 28% attrition rate x £8,000 cost/agent |
| IT integration maintenance reduction (G-6) | £120,000 | Legacy system decommissioning |
| Churn reduction / NPS improvement (O-2) | £145,000 | 0.5% churn reduction on £8.4M ARR |
| **Total Annual Benefit** | **£1,295,000** | |

**Timeline**:
- **Phase 1 (Months 1–3 post go-live)**: Minimal benefit realisation (stabilisation period) — cumulative benefit approximately £100,000
- **Phase 2 (Months 4–12)**: Revenue growth kicking in; CS improvements measurable — cumulative benefit approximately £700,000
- **Phase 3 (Months 13–24)**: Full benefit run-rate; legacy systems decommissioned — cumulative benefit approximately £1.8M
- **Sustainment (Year 3+)**: Annual net benefit approximately £1.3M with ongoing licence costs of £180,000/year

**Leading Indicators** (early signals of success):
- Sales rep adoption rate (proxy for future revenue benefit)
- CS handle time trend (proxy for cost saving)
- Legacy system decommissioning milestones hit on schedule

**Lagging Indicators** (final proof of success):
- Month 24 benefits realisation report signed off by Finance Director
- IT asset register confirming legacy system count at 3

---

## Complete Traceability Matrix

### Stakeholder → Driver → Goal → Outcome

| Stakeholder | Driver ID | Driver Summary | Goal ID | Goal Summary | Outcome ID | Outcome Summary |
|-------------|-----------|----------------|---------|--------------|------------|-----------------|
| CEO | SD-1 | Strategic competitive differentiation | G-1 | 15% ARR growth in 12 months | O-1 | £1.26M revenue increase |
| CEO | SD-1 | Strategic competitive differentiation | G-5 | ROI breakeven in 24 months | O-4 | £1.8M cumulative benefit |
| VP Sales | SD-2 | Revenue growth and pipeline visibility | G-1 | 15% ARR growth in 12 months | O-1 | £1.26M revenue increase |
| VP Sales | SD-2 | Revenue growth and pipeline visibility | G-2 | Deal cycle 62 to 45 days | O-1 | £1.26M revenue increase |
| VP Marketing | SD-3 | Lead quality and campaign ROI | G-1 | 15% ARR growth in 12 months | O-1 | £1.26M revenue increase |
| VP Marketing | SD-3 | Lead quality and campaign ROI | G-3 | GDPR compliance before go-live | O-3 | Zero ICO enforcement |
| Head of Customer Service | SD-4 | Reduce handle time and improve agent experience | G-4 | Handle time 8.5 to 5.5 minutes | O-2 | NPS 51 to 68 |
| Head of Customer Service | SD-4 | Reduce handle time and improve agent experience | G-4 | Handle time 8.5 to 5.5 minutes | O-4 | £1.8M ROI |
| IT Director | SD-5 | Consolidate technical debt | G-6 | 11 systems to 3 in 18 months | O-4 | £1.8M ROI |
| Finance Director | SD-6 | Demonstrate ROI and control costs | G-5 | ROI breakeven in 24 months | O-4 | £1.8M cumulative benefit |
| DPO | SD-7 | GDPR compliance and data governance | G-3 | GDPR compliance before go-live | O-3 | Zero ICO enforcement |
| Sales Representatives | SD-8 | Reduce admin burden | G-2 | Deal cycle 62 to 45 days | O-1 | £1.26M revenue increase |
| CS Agents | SD-9 | Single view of customer | G-4 | Handle time 8.5 to 5.5 minutes | O-2 | NPS 51 to 68 |
| Customers | SD-10 | Faster, more personalised service | G-4 | Handle time 8.5 to 5.5 minutes | O-2 | NPS 51 to 68 |

### Conflict Analysis

**Competing Drivers**:

- **Conflict 1**: VP Sales (SD-2) wants rapid deployment to start capturing pipeline data quickly. Finance Director (SD-6) wants a phased release of budget tied to milestone evidence, which creates pressure for a longer, more cautious programme timeline.
  - **Resolution Strategy**: Adopt a two-phase approach — Phase 1 (months 1–6) deploys core sales pipeline functionality with minimal customisation to demonstrate early value. Phase 1 success metrics (adoption rate, pipeline completeness, early deal cycle data) unlock Phase 2 budget. This gives the VP Sales an early win while giving the Finance Director milestone-based confidence.

- **Conflict 2**: Sales Representatives (SD-8) want minimum mandatory fields and maximum simplicity. DPO (SD-7) requires comprehensive data capture for GDPR compliance, including lawful basis, consent status, and communication preferences — adding form complexity.
  - **Resolution Strategy**: Work with the DPO and sales enablement team to agree the minimum viable compliance data set. Use CRM configuration to make compliance fields contextual (shown only when relevant) rather than appearing on every record. Consider auto-population from web forms and consent capture at lead entry rather than requiring reps to retrospectively capture consent.

- **Conflict 3**: Head of Customer Service (SD-4) needs CTI telephony integration as a critical dependency for handle time reduction. IT Director (SD-5) has limited integration resource and may need to deprioritise CTI in favour of ERP and marketing automation integrations.
  - **Resolution Strategy**: Create a formal integration priority matrix as part of technical design phase. CS handle time and NPS goals should be quantified in cost terms (£210,000/year saving) and presented to the IT Director to inform prioritisation. If CTI integration cannot be delivered in Phase 1, define a partial benefit case for Phase 1 and commit to CTI in Phase 2 with a firm delivery date.

**Synergies**:

- **Synergy 1**: CEO (SD-1), VP Sales (SD-2), and Customers (SD-10) all benefit from the same outcome — faster deal cycles and better service quality. Achieving G-1 and G-4 satisfies all three simultaneously, creating a natural alignment across the most powerful stakeholders.
- **Synergy 2**: IT Director (SD-5) and Finance Director (SD-6) are both served by the system consolidation goal (G-6). Decommissioning 8 legacy systems reduces IT maintenance costs directly (satisfying IT) while producing the quantified cost savings that the Finance Director needs to validate ROI.
- **Synergy 3**: DPO (SD-7) and VP Marketing (SD-3) have an apparent conflict but a deeper synergy — properly captured consent records (G-3) actually enable marketing to run larger, higher-quality campaigns with less legal risk, improving the marketing ROI that SD-3 demands.

---

## Communication & Engagement Plan

### CEO / Executive Sponsor

**Primary Message**: The CRM programme is on track to deliver the customer-first transformation commitment — pipeline visibility is improving, the CS experience is measurably better, and the ROI case is being validated in real time.

**Key Talking Points**:
- "In month X, pipeline coverage has increased by Y% — we now have real-time confidence in the revenue forecast for the first time"
- "Customer NPS is tracking up — agents now have the context they need before each call"
- "We are ahead of the ROI curve — cumulative benefit is tracking above the business case projection"

**Communication Frequency**: Monthly steering board (15-minute programme update); exception escalations as required

**Preferred Channel**: Steering board dashboard; brief written exception report if required

**Success Story**: "Board can now see live pipeline forecast with 95% confidence in revenue projection — no more manual consolidation."

---

### VP Sales

**Primary Message**: The CRM is delivering what was promised — reps have less admin, managers have better pipeline visibility, and the deal cycle is shortening.

**Key Talking Points**:
- "Your team's admin time per rep is down from 2.5 hours to under 1 hour per day — that's an extra 7 hours per week per rep in front of customers"
- "Pipeline forecast variance is down from 35% to under 10% — you now go into forecast meetings with confidence"
- "The pilot group has already closed 3 deals they would have missed without the automated next-best-action prompts"

**Communication Frequency**: Weekly status update; bi-weekly pipeline review with programme team

**Preferred Channel**: CRM dashboard (self-serve); weekly email summary; direct Slack channel with Programme Director

**Success Story**: "Sales team adoption at 87% — the system is being used voluntarily, not just mandated."

---

### Finance Director

**Primary Message**: The investment is performing against the business case. Benefits are being tracked, quantified, and validated against real financial data — not projections.

**Key Talking Points**:
- "Month X benefits realisation: £Y realised vs £Z projected — tracking ahead/behind plan"
- "Legacy system decommissioning on schedule — £120,000 annual saving confirmed from month 18"
- "Revenue attribution shows £X of ARR growth traceable to CRM-enabled pipeline improvements"

**Communication Frequency**: Monthly benefits realisation report; quarterly finance review

**Preferred Channel**: Formal written report; Finance Director monthly pack

**Success Story**: "Benefits realisation confirms positive ROI achieved at month 21 — 3 months ahead of the 24-month business case commitment."

---

### DPO / Legal

**Primary Message**: GDPR controls are in place before any personal data is processed. The compliance architecture gives us full audit trail, consent management, and SAR automation.

**Key Talking Points**:
- "All migrated records have documented lawful basis — we did not migrate without validating consent"
- "SAR response time is now under 2 hours — we are well within the 30-day statutory deadline"
- "The DPA with the vendor is signed and covers UK GDPR requirements including data residency"

**Communication Frequency**: Pre-go-live: weekly compliance checkpoints. Post-go-live: monthly compliance dashboard review

**Preferred Channel**: Formal compliance gate sign-offs; monthly DPO review meeting

**Success Story**: "First SAR received post-go-live responded to in 1 hour 40 minutes with complete audit-trail export."

---

### Sales Representatives

**Primary Message**: This system is built around making your job easier — less admin, fewer tools, more selling time. You shaped it. Here's what's coming and how it helps you.

**Key Talking Points**:
- "Your email and calendar automatically logs your activities — no more duplicate entry"
- "You can see your full pipeline on mobile — update deals from the car park after a client visit"
- "The pilot group told us what to fix. We listened. Here are the 5 changes we made based on your feedback."

**Communication Frequency**: Pre-launch: bi-weekly CRM preview sessions; post-launch: weekly "what's new" email for first 90 days

**Preferred Channel**: Team meetings; Slack/Teams channel (peer-to-peer adoption community); short video walkthroughs

**Success Story**: "Pilot rep closed a £45,000 deal they would have lost — the automated follow-up reminder caught it before the customer went to a competitor."

---

### Customer Service Agents

**Primary Message**: You told us the system-switching was exhausting and embarrassing. We heard you. The new CRM gives you everything in one place before the customer says a word.

**Key Talking Points**:
- "Screen-pop shows you the customer's full history before you even say hello"
- "You log in once — no more switching between 4 tools per call"
- "You shaped this system in UAT. The case routing you asked for is live."

**Communication Frequency**: Pre-launch: 3 training sessions; post-launch: weekly feedback survey for 60 days; monthly CS town hall

**Preferred Channel**: Team briefings; short training videos; in-system guidance tooltips

**Success Story**: "Agent handle time is down 3 minutes per call — that's 3 minutes back in every conversation to actually help the customer."

---

## Change Impact Assessment

### Impact on Stakeholders

| Stakeholder | Current State | Future State | Change Magnitude | Resistance Risk | Mitigation Strategy |
|-------------|---------------|--------------|------------------|-----------------|---------------------|
| Sales Representatives | 4 tools, 2.5hr daily admin, spreadsheet pipeline | 1 CRM, auto-logging, mobile app | HIGH | HIGH | Pilot group co-design; change champions; mobile-first UX |
| CS Agents | 4 system logins per call, manual triage | 1 CRM screen, auto screen-pop, case routing | HIGH | MEDIUM | UAT involvement; training programme; quick-reference guides |
| VP Sales | Manual forecast consolidation (2 days/month) | Real-time pipeline dashboard, automated alerts | MEDIUM | LOW | Early pilot access; personal dashboard configuration session |
| VP Marketing | No closed-loop reporting | Full attribution from lead to revenue | MEDIUM | LOW | Involve in data model design; early access to campaign reporting |
| IT Operations | 11 systems, 17 integrations to maintain | 3 systems, centralised iPaaS layer | HIGH | MEDIUM | Dedicated IT transition workstream; runbook development support |
| Finance Director | Ad-hoc ROI tracking, manual benefits reports | Monthly automated benefits dashboard | LOW | LOW | Review and approve benefits tracking methodology before go-live |
| DPO | Manual SAR responses, incomplete consent records | Automated SAR export, full consent audit trail | MEDIUM | LOW | Early involvement in data model; compliance gate sign-offs |

### Change Readiness

**Champions** (Enthusiastic supporters):
- **VP Sales** — personal stake in improved pipeline visibility; agreed to co-lead the pilot programme
- **Head of Customer Service** — has been requesting a unified customer view for 18 months; will be a vocal advocate
- **10 Pilot Sales Representatives** — self-selected; have already experienced benefits in early configuration sessions; will serve as peer change advocates
- **IT Director** — motivated by consolidation goal; views the CRM as a route to reducing operational complexity

**Fence-sitters** (Neutral, need convincing):
- **Wider Sales Team** — will wait to see whether the pilot reps endorse the system before committing; peer advocacy from pilot group is the key unlock
- **Marketing Team** — not opposed, but campaign integration is a Phase 2 commitment; needs visible short-term wins to stay engaged
- **Finance Director** — cautious rather than resistant; milestone-based funding approach addresses their core concern

**Resisters** (Opposed or skeptical):
- **Some Regional Sales Managers** — may resist sales process standardisation required for CRM consistency; feel local autonomy is threatened. Strategy: involve 2 regional managers in the configuration design process; frame standardisation as giving them better visibility rather than removing control.
- **Some CS Team Leaders** — concerned that reduced handle time targets will feel like surveillance. Strategy: frame metrics as team-level and improvement-focused, not individual surveillance; involve team leaders in defining what "good" looks like.

---

## Risk Register (Stakeholder-Related)

### Risk R-1: Low Sales Representative Adoption Undermines All Revenue Goals

**Related Stakeholders**: Sales Representatives (SD-8), VP Sales (SD-2), Finance Director (SD-6)

**Risk Description**: If sales representatives do not adopt the CRM consistently (below 70% regular usage within 90 days of go-live), the pipeline data will be unreliable, revenue forecasting will remain broken, and the ROI case will fail to materialise. This was the failure mode of both previous CRM attempts.

**Impact on Goals**: G-1 (revenue growth), G-2 (deal cycle reduction), G-5 (ROI breakeven) — all at risk

**Probability**: HIGH (given the history of two previous failed CRM rollouts)

**Impact**: CRITICAL

**Mitigation Strategy**: (1) Pilot programme with 10 self-selected reps to validate UX and generate peer advocacy before company-wide launch; (2) Email/calendar auto-logging to minimise manual data entry burden; (3) Gamification of adoption — pipeline completeness league table visible to all reps; (4) VP Sales personally endorses and uses the system publicly from day one; (5) 90-day adoption KPI reviewed weekly by VP Sales with named consequence for teams below 60% compliance.

**Contingency Plan**: If adoption below 60% at day 60 post-go-live, trigger emergency UX review with a rep focus group and a 2-week sprint to remove the top 3 friction points before wider rollout to remaining regions.

---

### Risk R-2: Data Migration Quality Failure Undermines Trust at Go-Live

**Related Stakeholders**: IT Director (SD-5), Sales Representatives (SD-8), CS Agents (SD-9), DPO (SD-7)

**Risk Description**: If historical customer and opportunity data is migrated with errors, duplicates, or missing records, agents and reps will revert to legacy tools, adoption will stall, and the DPO will not sign off on the go-live.

**Impact on Goals**: G-1 (pipeline baseline corrupted), G-3 (GDPR compliance at risk), G-4 (CS unified view unreliable)

**Probability**: MEDIUM (data migration is consistently the highest-risk workstream in CRM implementations)

**Impact**: HIGH

**Mitigation Strategy**: (1) Dedicate a standalone data migration workstream with a named data migration lead; (2) Three migration test runs against a full data copy before production migration; (3) Define data quality acceptance criteria (< 0.5% duplicate rate; 100% of key account records validated by account owners) as a go/no-go gate; (4) DPO signs off on consent validation before migration; (5) 30-day parallel running period where key accounts validated against both old and new system.

**Contingency Plan**: If data quality fails go-live acceptance criteria, delay go-live by 4 weeks and re-run migration with targeted remediation. Do not go live with known data quality issues — the trust damage from a bad migration is harder to recover from than a delayed launch.

---

### Risk R-3: CTI Integration Descoped, Preventing Customer Service Handle Time Reduction

**Related Stakeholders**: Head of Customer Service (SD-4), CS Agents (SD-9), IT Director (SD-5)

**Risk Description**: Computer Telephony Integration (CTI) is technically complex and may be deprioritised in favour of ERP and marketing automation integrations under IT resource pressure. Without CTI, the screen-pop capability that drives the majority of the handle time reduction will not be delivered in Phase 1.

**Impact on Goals**: G-4 (handle time target missed or delayed), O-2 (NPS improvement slower), O-4 (ROI benefit from CS savings delayed)

**Probability**: MEDIUM

**Impact**: MEDIUM

**Mitigation Strategy**: (1) Quantify CTI benefit in financial terms (£210,000/year cost saving) for the IT Director's prioritisation matrix; (2) Include CTI as a named Phase 1 integration in the contract with the systems integration partner; (3) Assess native CTI connectors from the CRM vendor as lower-complexity alternatives to bespoke integration.

**Contingency Plan**: If CTI cannot be delivered in Phase 1, rebase the handle time target for Phase 1 (target 7 minutes rather than 5.5), commit to CTI as a named Phase 2 deliverable with a firm date, and update the benefits realisation plan accordingly to reflect the timing shift.

---

### Risk R-4: GDPR Advisory Notice or Enforcement Action During Implementation

**Related Stakeholders**: DPO (SD-7), VP Marketing (SD-3), CEO (SD-1)

**Risk Description**: The organisation currently has an active ICO advisory notice. If a data subject complaint is raised during the CRM implementation period (particularly if legacy data practices continue in parallel), the ICO may escalate to a formal investigation, which could delay the programme and consume significant management time.

**Impact on Goals**: G-3 (GDPR compliance — already at risk from current advisory notice), G-1 (reputational damage could impact revenue)

**Probability**: LOW-MEDIUM

**Impact**: HIGH

**Mitigation Strategy**: (1) DPO-led interim review of current data practices to identify and remediate the highest-risk activities before CRM migration; (2) Marketing team to suspend all email campaigns without verified consent until consent management is in place; (3) Legal team to ensure ICO advisory notice remediation actions are completed and documented before migration begins.

**Contingency Plan**: If an ICO investigation is opened during the programme, pause data migration pending legal advice. Engage ICO proactively to demonstrate the CRM programme is the remediation mechanism for the outstanding advisory notice.

---

## Governance & Decision Rights

### Decision Authority Matrix (RACI)

| Decision Type | Responsible | Accountable | Consulted | Informed |
|---------------|-------------|-------------|-----------|----------|
| Programme budget approval | Programme Director | Finance Director | CEO, IT Director | All stakeholders |
| CRM platform vendor selection | Enterprise Architect | IT Director | VP Sales, VP Marketing, Head CS | Finance Director, DPO |
| Requirements prioritisation | Product Owner | VP Sales, VP Marketing, Head CS | Sales Reps, CS Agents | IT Director |
| Data migration go/no-go | IT Director | DPO, Programme Director | Enterprise Architect | All stakeholders |
| GDPR compliance sign-off | DPO | DPO | IT Director, Legal | CEO, IT Director |
| Architecture decisions | Enterprise Architect | IT Director | Security, IT Operations | Business Leads |
| Go/no-go for go-live | Programme Director | CEO | All Business Leads, DPO | All |
| Integration scope and prioritisation | IT Director | IT Director | Head CS, VP Sales | VP Marketing |
| Change champion programme design | HR / Change Lead | Programme Director | VP Sales, Head CS | Sales Reps, CS Agents |
| Benefits realisation sign-off | Finance Director | Finance Director | Programme Director | CEO, Board |

### Escalation Path

1. **Level 1 — Programme Team** (Programme Director / Product Owner): Day-to-day scope, configuration, and delivery decisions; sprint-level trade-offs
2. **Level 2 — Steering Committee** (CEO, VP Sales, VP Marketing, Head CS, IT Director, Finance Director, DPO): Programme scope changes, timeline variances > 2 weeks, budget variances > 10%, integration priority conflicts
3. **Level 3 — CEO** (Direct escalation): Strategic direction changes, major vendor disputes, board-level reporting, ICO regulatory issues

---

## Validation & Sign-off

### Stakeholder Review

| Stakeholder | Review Date | Comments | Status |
|-------------|-------------|----------|--------|
| CEO | PENDING | | PENDING |
| VP Sales | PENDING | | PENDING |
| VP Marketing | PENDING | | PENDING |
| Head of Customer Service | PENDING | | PENDING |
| IT Director | PENDING | | PENDING |
| Finance Director | PENDING | | PENDING |
| DPO | PENDING | | PENDING |

### Document Approval

| Role | Name | Signature | Date |
|------|------|-----------|------|
| Programme Sponsor (CEO) | | | |
| Business Owner (VP Sales) | | | |
| Enterprise Architect | | | |

---

## Appendices

### Appendix A: Stakeholder Interview Summaries

No formal interviews conducted at this stage. Analysis derived from documented business context and stated programme objectives. Recommend scheduling 30-minute interviews with each Manage Closely stakeholder within 2 weeks of this document being shared for validation and to capture nuances not visible at this stage.

---

### Appendix B: Survey Results

No surveys conducted at this stage. Recommend a baseline stakeholder alignment survey (5 questions, anonymous) before programme launch to establish a readiness baseline that can be tracked over time.

---

### Appendix C: References

- CRM System Programme initiation briefing (internal)
- Customer satisfaction survey results — Q4 2025
- IT systems landscape and integration inventory — IT Operations
- GDPR advisory notice — ICO correspondence (DPO office)
- FY2026/27 Revenue Growth Target — CEO Board Presentation

---

## Revision History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | 2026-03-01 | ArcKit AI | Initial creation from `/arckit:stakeholders` command |

## External References

| Document | Type | Source | Key Extractions | Path |
|----------|------|--------|-----------------|------|
| *None provided* | — | — | — | — |

---

**Generated by**: ArcKit `/arckit:stakeholders` command
**Generated on**: 2026-03-01
**ArcKit Version**: 2.22.3
**Project**: CRM System (Project 001)
**AI Model**: claude-sonnet-4-6
