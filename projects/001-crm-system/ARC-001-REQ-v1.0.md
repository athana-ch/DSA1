# Project Requirements: CRM System

> **Template Status**: Live | **Version**: 1.0 | **Command**: `/arckit:requirements`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-001-REQ-v1.0 |
| **Document Type** | Business and Technical Requirements |
| **Project** | CRM System (Project 001) |
| **Classification** | OFFICIAL |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-03-01 |
| **Last Modified** | 2026-03-01 |
| **Review Cycle** | Monthly |
| **Next Review Date** | 2026-04-01 |
| **Owner** | Enterprise Architect |
| **Reviewed By** | PENDING |
| **Approved By** | PENDING |
| **Distribution** | Project Board, IT Leadership, VP Sales, VP Marketing, Head of Customer Service, DPO |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-03-01 | ArcKit AI | Initial creation from `/arckit:requirements` command — NFR-focused | PENDING | PENDING |

## Document Purpose

This document defines the requirements for the enterprise CRM system implementation, with emphasis on non-functional requirements (NFRs). It is the primary input for vendor RFP/evaluation, architecture design reviews, and acceptance testing. All requirements trace to stakeholder drivers and goals documented in ARC-001-STKE-v1.0 and are governed by the architecture principles in ARC-000-PRIN-v1.0.

---

## Executive Summary

### Business Context

The organisation currently manages customer relationships across 11 fragmented systems with no unified customer view. Sales pipeline data is maintained in individual spreadsheets, customer service agents switch between 3–4 systems per interaction, and marketing has no closed-loop attribution from lead to revenue. This fragmentation costs an estimated £180,000 per year in IT integration maintenance, produces a 35% forecast variance in sales, and contributes to an NPS of 51 (down from 58 two years ago).

The CRM programme will replace this fragmented landscape with a single platform serving sales (100+ users), customer service (60+ agents), and marketing (25 users). It must be deployed in phases, with Phase 1 delivering core sales pipeline and customer service capabilities within 6 months of contract award.

### Objectives

- Deliver a unified 360° view of every customer across sales, service, and marketing
- Increase Annual Recurring Revenue (ARR) by 15% within 12 months of go-live through improved pipeline management
- Reduce customer service average handle time from 8.5 to 5.5 minutes per interaction
- Achieve full UK GDPR compliance with automated data subject rights fulfilment
- Consolidate the customer-facing technology landscape from 11 systems to 3 within 18 months of go-live
- Achieve positive ROI breakeven within 24 months of go-live

### Expected Outcomes

- ARR growth from £8.4M to £9.66M (+15%) within 12 months of go-live
- NPS improvement from 51 to 68 within 12 months of go-live
- Sales rep CRM admin time reduced from 2.5 hours/day to under 1 hour/day
- SAR response time reduced from 12–18 hours to under 2 hours
- IT integration maintenance cost reduced from £180,000/year to under £60,000/year

### Project Scope

**In Scope**:
- Sales pipeline management and opportunity tracking for 100+ sales users
- Customer service case management and customer 360 view for 60+ agents
- Marketing integration (lead capture, attribution, campaign management) for 25 marketing users
- Integration with existing ERP/billing system, marketing automation platform, and telephony (CTI)
- Data migration from all existing CRM-adjacent systems
- UK GDPR compliance controls (consent management, retention automation, SAR workflow)
- Mobile application for field sales representatives

**Out of Scope**:
- ERP/billing system replacement
- Marketing automation platform replacement
- Customer self-service portal (future phase)
- AI-driven sales forecasting (future phase)
- Field service management

---

## Stakeholders

| Stakeholder | Role | Organization | Involvement Level |
|-------------|------|--------------|-------------------|
| CEO | Executive Sponsor | Executive | Decision maker — steering board |
| VP Sales | Business Owner | Sales | Requirements definition, pilot lead |
| VP Marketing | Business Owner | Marketing | Integration requirements |
| Head of Customer Service | Business Owner | Customer Service | Process design, agent requirements |
| IT Director / CTO | Technical Authority | IT | Architecture approval |
| Finance Director | Budget Holder | Finance | ROI validation, budget approval |
| Data Protection Officer | Compliance Authority | Legal | GDPR sign-off, data requirements |
| Enterprise Architect | Document Owner | Architecture | Technical governance |
| Sales Representatives | End Users | Sales | User acceptance |
| Customer Service Agents | End Users | Customer Service | User acceptance |

---

## Business Requirements

### BR-001: Unified Customer Record

**Description**: The CRM must maintain a single, authoritative record for every customer, aggregating data from all integrated systems into a 360° view visible to sales, service, and marketing users.

**Rationale**: Fragmented customer data is the root cause of the NPS decline and agent handle time problem. A unified record is the foundational capability on which all other CRM value depends. Aligns with stakeholder driver SD-4 (Head of Customer Service) and SD-9 (CS Agents).

**Success Criteria**:
- Every customer record displays complete interaction history across sales, service, and marketing channels
- Customer data is consistent across all integrated systems within the defined sync SLA
- Agents can see a customer's full history in under 3 seconds from login

**Priority**: MUST_HAVE

**Stakeholder**: CEO (SD-1), Head of Customer Service (SD-4), VP Sales (SD-2)

---

### BR-002: Sales Pipeline Management and Forecasting

**Description**: The CRM must enable sales managers to view the full pipeline in real time, with automated data capture reducing manual entry, and forecast accuracy within 10% of actual results.

**Rationale**: Current forecast variance is 30–40%, requiring 2 days of manual consolidation per month. Pipeline data quality depends on rep adoption (see conflict C-1). Aligns with driver SD-2 (VP Sales) and goal G-1 (15% ARR growth).

**Success Criteria**:
- Pipeline forecast variance at or below 10% (vs current 30–40%) within 6 months of go-live
- Monthly forecast consolidation time reduced from 2 days to under 2 hours
- 80%+ of active opportunities updated within the last 7 days at any time

**Priority**: MUST_HAVE

**Stakeholder**: VP Sales (SD-2), CEO (SD-1)

---

### BR-003: UK GDPR Compliance and Data Subject Rights

**Description**: The CRM must implement full UK GDPR compliance controls before processing any personal data, including consent management, automated retention, and Subject Access Request (SAR) fulfilment in under 2 hours of manual effort.

**Rationale**: The organisation has an active ICO advisory notice. Non-compliance risk is up to 4% of global annual turnover (approximately £420,000). GDPR compliance is a go/no-go condition for data migration sign-off by the DPO. Aligns with driver SD-7 (DPO) and goal G-3.

**Success Criteria**:
- 100% of migrated contact records have documented lawful basis for processing before migration begins
- SAR response completed within 2 hours of manual effort (current: 12–18 hours)
- Automated data deletion executes against retention schedule with zero manual intervention required
- Zero ICO complaints within 12 months of go-live

**Priority**: MUST_HAVE

**Stakeholder**: DPO (SD-7), CEO (SD-1)

---

### BR-004: Return on Investment Within 24 Months

**Description**: The total programme must deliver a cumulative net benefit of at least £1.8M within 24 months of go-live, demonstrated through a monthly benefits realisation report validated by the Finance Director.

**Rationale**: Finance Director will release final budget tranche only on confidence in the 24-month ROI commitment. Total programme investment is £850,000 implementation plus £360,000 two-year ongoing cost. Aligns with driver SD-6 (Finance Director) and goal G-5.

**Success Criteria**:
- Month 24 benefits realisation report shows cumulative net benefit exceeding £590,000 (net of all costs)
- Monthly benefits tracking report produced from month 1 of go-live
- Revenue contribution to ARR growth attributable to CRM pipeline improvements measurable and separately reported

**Priority**: MUST_HAVE

**Stakeholder**: Finance Director (SD-6), CEO (SD-1)

---

### BR-005: System Consolidation — 11 Systems to 3

**Description**: Within 18 months of CRM go-live, the organisation's customer-facing technology estate must be reduced from 11 systems to 3 (CRM, ERP/billing, marketing automation), eliminating all point-to-point integrations in favour of a centralised integration layer.

**Rationale**: The current estate costs £180,000/year in integration maintenance and generated 3 data incidents in the past 18 months. Consolidation is a major benefit stream in the ROI case. Aligns with driver SD-5 (IT Director) and goal G-6.

**Success Criteria**:
- IT asset register confirms 3 active customer-facing systems by month 18 post-go-live
- Zero active point-to-point integrations by month 18 (all integrations via central iPaaS layer)
- Annual integration maintenance cost below £60,000 by month 24

**Priority**: MUST_HAVE

**Stakeholder**: IT Director (SD-5), Finance Director (SD-6)

---

## Functional Requirements

### User Personas

#### Persona 1: Sales Representative (Field and Office)

- **Role**: Account executive / business development representative
- **Goals**: Log activities quickly (mobile), see full account history, get next-best-action prompts, manage pipeline with minimal admin
- **Pain Points**: 2.5 hours daily admin across 4 tools; no mobile access; duplicate data entry from email/calendar
- **Technical Proficiency**: Medium — comfortable with smartphones and standard business apps, resistant to complex enterprise software

#### Persona 2: Customer Service Agent

- **Role**: Front-line customer service representative (inbound calls and email)
- **Goals**: See full customer context before picking up the phone; log cases quickly; find knowledge base answers fast; resolve cases on first contact
- **Pain Points**: 3.8 system logins per interaction; 8.5 min average handle time; customers repeating themselves; no context on sales activity
- **Technical Proficiency**: Medium — experienced with ticketing tools; needs a simple, fast interface

#### Persona 3: Sales / CS Manager

- **Role**: Regional sales manager or CS team leader
- **Goals**: Real-time pipeline visibility; team performance dashboards; identify at-risk deals or escalated cases
- **Pain Points**: 2-day manual forecast consolidation; no visibility into individual rep activity without chasing
- **Technical Proficiency**: Medium-High — comfortable with reports and dashboards

#### Persona 4: Marketing Analyst

- **Role**: Campaign manager / marketing operations
- **Goals**: Attribute revenue to campaigns; segment contacts for targeted campaigns; track lead quality from source to close
- **Pain Points**: No closed-loop reporting; no visibility into deal outcomes from leads generated
- **Technical Proficiency**: High — experienced with marketing automation and analytics tools

---

### Functional Requirements Detail

#### FR-001: 360° Customer Profile

**Description**: The system must display a unified customer profile aggregating all interactions (calls, emails, cases, opportunities, purchases) in a chronological timeline view.

**Relates To**: BR-001, UC-1 (Agent handles inbound call)

**Acceptance Criteria**:
- [ ] Given an agent opens a customer record, when the screen loads, then all interaction history across sales, service, and marketing channels is visible in a single timeline within 3 seconds
- [ ] Given a sales rep views an account, when the account record opens, then open service cases are visible with status and priority
- [ ] Given a customer contacts support, when the agent opens the record, then the last 5 interactions across all channels are visible without any system switching

**Priority**: MUST_HAVE | **Complexity**: HIGH

---

#### FR-002: Sales Pipeline and Opportunity Management

**Description**: The system must support structured sales pipeline management with configurable stages, automated next-best-action prompts, and activity logging via email/calendar integration.

**Relates To**: BR-002

**Acceptance Criteria**:
- [ ] Given a rep completes a call or sends an email, when the email/calendar integration is active, then the activity is logged automatically with no manual input required
- [ ] Given an opportunity has had no activity for more than a configurable number of days, when the threshold is reached, then the rep and their manager receive an automated alert
- [ ] Given a manager opens the pipeline view, when the dashboard loads, then all opportunities are visible with stage, value, expected close date, and days since last activity in real time

**Priority**: MUST_HAVE | **Complexity**: HIGH

---

#### FR-003: Case Management and Routing

**Description**: The system must provide case creation, categorisation, automated routing to the correct team/agent, escalation workflows, and knowledge base integration for customer service.

**Relates To**: BR-001, BR-004

**Acceptance Criteria**:
- [ ] Given a new case is created (phone, email, or web form), when it arrives, then it is automatically categorised and routed to the appropriate queue within 30 seconds
- [ ] Given a case meets a defined escalation threshold (e.g., waiting more than 2 hours without agent response), when the threshold is crossed, then the team leader is automatically notified
- [ ] Given an agent is handling a case, when they search the knowledge base, then relevant articles are surfaced based on the case category within 2 seconds

**Priority**: MUST_HAVE | **Complexity**: HIGH

---

#### FR-004: Mobile Application for Field Sales

**Description**: The system must provide a mobile application for iOS and Android supporting offline access to opportunity and account data, activity logging, and push notifications for pipeline alerts.

**Relates To**: BR-002, SD-8 (Sales Rep adoption)

**Acceptance Criteria**:
- [ ] Given a sales rep has no network connectivity, when they open the mobile app, then their assigned accounts and opportunities are accessible from local cache
- [ ] Given a rep logs an activity on mobile, when connectivity is restored, then the activity synchronises to the CRM within 60 seconds
- [ ] Given a pipeline alert is triggered, when the rep's mobile app is in the background, then a push notification is delivered within 5 minutes

**Priority**: MUST_HAVE | **Complexity**: MEDIUM

---

#### FR-005: GDPR Consent Management

**Description**: The system must capture, store, and enforce marketing communication consent at the individual contact level, with a full consent audit trail and revocation capability.

**Relates To**: BR-003

**Acceptance Criteria**:
- [ ] Given a new contact is created, when the record is saved, then the lawful basis for processing must be selected from a controlled list before the record can be saved
- [ ] Given a contact withdraws consent, when the preference is updated, then all downstream marketing systems are notified and the contact is suppressed within 24 hours
- [ ] Given a user views a contact record, when they access the consent history, then a complete timestamped audit trail of all consent changes is displayed

**Priority**: MUST_HAVE | **Complexity**: MEDIUM

---

#### FR-006: Subject Access Request (SAR) Automation

**Description**: The system must provide an automated SAR workflow that extracts all personal data held on a data subject across all CRM modules and produces a formatted export report.

**Relates To**: BR-003

**Acceptance Criteria**:
- [ ] Given a SAR is raised for a data subject, when the DPO initiates the export workflow, then a complete export of all personal data fields for that subject is produced within 30 minutes of automated processing
- [ ] Given the SAR export is produced, when it is downloaded, then it includes all interactions, consent records, and data fields in a human-readable format
- [ ] Total manual effort to respond to a SAR must not exceed 2 hours (target: under 1 hour)

**Priority**: MUST_HAVE | **Complexity**: MEDIUM

---

#### FR-007: Marketing Attribution and Closed-Loop Reporting

**Description**: The system must track the source of every lead from creation through to closed-won deal, enabling campaign ROI reporting by source and campaign.

**Relates To**: BR-001, SD-3 (VP Marketing)

**Acceptance Criteria**:
- [ ] Given a lead is created from a marketing campaign, when the lead is converted to an opportunity and the deal closes, then the closed revenue is attributed to the originating campaign in the marketing attribution report
- [ ] Given a marketing manager views the attribution dashboard, when they filter by campaign, then revenue attributed, pipeline generated, and cost per closed deal are displayed

**Priority**: MUST_HAVE | **Complexity**: MEDIUM

---

#### FR-008: CTI Screen-Pop Integration

**Description**: When an inbound call is received, the CRM must automatically display the matching customer record before the agent answers, using caller ID matched against contact records.

**Relates To**: BR-001, G-4 (Handle time reduction)

**Acceptance Criteria**:
- [ ] Given an inbound call arrives at an agent's station, when the caller ID matches a CRM contact, then the customer's 360° profile opens automatically within 3 seconds of the call connecting
- [ ] Given the caller ID does not match any contact, when the call connects, then the agent is presented with a new contact creation form pre-populated with the caller ID

**Priority**: MUST_HAVE | **Complexity**: HIGH

**Note**: See Conflict C-3 — CTI integration is subject to IT resource prioritisation. If descoped from Phase 1, handle time target is rebased to 7.0 minutes for Phase 1.

---

## Non-Functional Requirements

### Performance Requirements

#### NFR-P-001: User Interface Response Time

**Requirement**: All interactive CRM screens must load and be usable within defined response time targets under normal and peak load conditions.

**Targets**:
- Standard page load (account/contact/opportunity record): p50 under 1.5 seconds, p95 under 3 seconds
- Customer 360 view (aggregated timeline): p50 under 2 seconds, p95 under 4 seconds
- List views (pipeline, case queue, contact list): p50 under 1 second, p95 under 2 seconds
- Dashboard views (management, forecasting): p50 under 3 seconds, p95 under 5 seconds

**Load Conditions**:
- Normal load: 185 concurrent users (100 sales + 60 CS agents + 25 marketing)
- Peak load: 250 concurrent users (growth projection year 2)
- Data volume at go-live: approximately 50,000 customer records, 200,000 historical interactions, 5,000 open opportunities

**Measurement Method**: Synthetic monitoring from application performance management (APM) tooling measuring time-to-interactive (TTI), measured at p50 and p95 across a 5-minute rolling window.

**Aligns With**: Architecture Principle P-12 (Performance Requirements Defined Before Implementation)

**Acceptance Criteria**:
- [ ] Load testing at 250 concurrent users confirms all response time targets met before go-live
- [ ] APM dashboards show p95 response times in production within 72 hours of go-live
- [ ] Response time targets maintained after data migration with full production data set

**Priority**: CRITICAL

---

#### NFR-P-002: API Response Time

**Requirement**: All CRM API endpoints used by integrations must meet latency targets to support real-time integration patterns.

**Targets**:
- Read endpoints (GET): p95 under 300ms, p99 under 800ms
- Write endpoints (POST/PUT/PATCH): p95 under 500ms, p99 under 1,200ms
- Search/query endpoints: p95 under 1,000ms, p99 under 3,000ms
- Bulk operations: throughput of at least 500 records per second

**Measurement Method**: API gateway metrics, measured per-endpoint under load test and in production.

**Aligns With**: Architecture Principle P-12

**Acceptance Criteria**:
- [ ] API load test at 3x expected integration call volume confirms targets met
- [ ] API latency monitored continuously in production with alerting if p95 exceeds target for 5 consecutive minutes

**Priority**: HIGH

---

#### NFR-P-003: CTI Screen-Pop Latency

**Requirement**: The screen-pop response (from inbound call signal to customer record displayed) must complete within 3 seconds to enable the agent to greet the customer by name before the call connects.

**Targets**:
- Screen-pop latency (call signal to record displayed): under 3 seconds at p95
- Customer record lookup (caller ID to contact match): under 1 second at p95

**Load Conditions**: 60 concurrent agents with peak call arrival rate of 120 calls per hour (2 calls per agent per hour average during busy periods).

**Measurement Method**: CTI middleware logging, caller ID to screen-pop timestamp delta.

**Acceptance Criteria**:
- [ ] CTI load test simulating 60 concurrent agents confirms under 3-second screen-pop at p95
- [ ] Screen-pop latency monitored in production; alert if p95 exceeds 5 seconds

**Priority**: HIGH (see Conflict C-3 — subject to Phase 1 scope)

---

#### NFR-P-004: Mobile Application Performance

**Requirement**: The mobile CRM application must provide a responsive experience on standard mobile hardware with graceful offline operation.

**Targets**:
- App launch to usable state (cached data): under 2 seconds on a mid-range smartphone
- Activity sync on reconnect: within 60 seconds for a queue of up to 50 offline activities
- Push notification delivery (pipeline alert to notification received): within 5 minutes

**Acceptance Criteria**:
- [ ] Mobile performance tested on devices with minimum 4GB RAM and 3-year-old hardware
- [ ] Offline mode tested by toggling airplane mode and confirming data persistence
- [ ] Sync tested on 3G equivalent connectivity (simulated 5Mbps bandwidth)

**Priority**: HIGH

---

### Availability and Resilience Requirements

#### NFR-A-001: System Availability SLA

**Requirement**: The CRM must meet an availability SLA of 99.5% (Enhanced tier), calculated on a rolling monthly basis, excluding approved maintenance windows.

**Targets**:
- Monthly availability: 99.5% (maximum 3.7 hours unplanned downtime per month)
- Annual availability: 99.5% (maximum 43.8 hours unplanned downtime per year)
- Maintenance window: Maximum 4 hours per month, scheduled outside business hours (Monday–Friday 08:00–18:00 UK time)
- Planned maintenance must be notified to users with at least 5 business days' notice

**Rationale**: The CRM will be an operational system used by 185+ users during business hours. 99.5% is the Enhanced tier from Architecture Principle P-13, appropriate for a core business operations system. The CS team operates cases and requires reliable access during contact centre hours.

**Measurement Method**: Vendor-provided uptime monitoring plus independent synthetic monitoring from at least two geographic points.

**Acceptance Criteria**:
- [ ] Vendor SLA contract specifies 99.5% monthly availability with financial remedy (service credits) for breach
- [ ] Independent monitoring confirms availability measurement methodology agreed before go-live
- [ ] Maintenance notification process documented and tested before go-live

**Priority**: CRITICAL

---

#### NFR-A-002: Recovery Time Objective (RTO)

**Requirement**: In the event of a major failure requiring system recovery, the CRM must be restored to full operation within 4 hours (RTO = 4 hours).

**Rationale**: A 4-hour RTO is consistent with the Enhanced tier availability target. The CS contact centre can operate in degraded mode (using telephone scripts) for up to 4 hours before customer experience impact becomes severe. Sales team can operate without CRM access for up to one business day without material pipeline risk.

**Measurement Method**: Annual disaster recovery exercise, timed from failure declaration to confirmed system restoration.

**Acceptance Criteria**:
- [ ] DR exercise conducted within 60 days of go-live confirms RTO target achievable
- [ ] DR runbook documented, tested, and available to on-call team
- [ ] Annual DR exercise scheduled and conducted with results reported to IT Director

**Priority**: HIGH

---

#### NFR-A-003: Recovery Point Objective (RPO)

**Requirement**: In the event of data loss, no more than 1 hour of transactional data may be lost (RPO = 1 hour).

**Rationale**: Sales activity logged throughout the day represents real business value. Losing more than 1 hour of pipeline updates, case notes, or customer interactions would require significant manual re-entry and could result in missed follow-up commitments.

**Backup Requirements**:
- Continuous transaction log backup (or equivalent) with point-in-time recovery capability
- Full backup: daily, retained for 30 days
- Weekly backup: retained for 3 months
- Monthly backup: retained for 12 months
- Annual backup: retained for 7 years (for GDPR audit records)

**Measurement Method**: Backup restoration test conducted within 60 days of go-live and annually thereafter.

**Acceptance Criteria**:
- [ ] Backup strategy documented and agreed with vendor before contract signature
- [ ] Point-in-time recovery demonstrated to within 15-minute granularity in DR exercise
- [ ] Backup restoration test confirms RPO target achievable from most recent backup

**Priority**: HIGH

---

#### NFR-A-004: Fault Tolerance and Graceful Degradation

**Requirement**: The CRM must remain partially operational during dependency failures, with defined degraded-mode behaviour for each failure scenario.

**Degraded Mode Scenarios**:

| Dependency Failure | Expected CRM Behaviour | Degraded Functions |
|-------------------|----------------------|-------------------|
| Marketing automation platform unavailable | CRM continues; lead sync pauses; alert raised | Campaign attribution delayed; new lead sync paused |
| ERP/billing integration unavailable | CRM continues; billing data shows cached values | Account balance/status may be stale (labelled as such) |
| CTI/telephony integration unavailable | CRM continues; agents search manually | No screen-pop; manual caller ID lookup |
| Email/calendar integration unavailable | CRM continues; auto-logging paused | Activities must be logged manually until restored |

**Resilience Patterns Required**:
- [ ] Circuit breaker for all external integration dependencies with configurable failure threshold
- [ ] Timeout on all outbound API calls (maximum 10 seconds for synchronous calls)
- [ ] Retry with exponential backoff for transient failures (maximum 3 retries, starting at 1 second)
- [ ] Stale data clearly labelled in the UI when integration data cannot be refreshed
- [ ] Health status dashboard showing integration status visible to administrators

**Aligns With**: Architecture Principle P-02 (Resilience and Graceful Degradation)

**Acceptance Criteria**:
- [ ] Failure injection testing (simulating each dependency outage) confirms CRM remains operational in degraded mode
- [ ] Integration health dashboard tested and operational before go-live
- [ ] All degraded-mode behaviours documented in user-facing communications and runbooks

**Priority**: HIGH

---

### Scalability Requirements

#### NFR-S-001: Concurrent User Capacity

**Requirement**: The CRM must support at least 250 concurrent authenticated users without performance degradation beyond defined targets.

**Growth Projections**:

| Year | Concurrent Users | Total Licensed Users | Data Volume (Customer Records) |
|------|-----------------|---------------------|-------------------------------|
| Go-live (Year 0) | 185 | 200 | 50,000 |
| Year 1 | 220 | 250 | 75,000 |
| Year 2 | 250 | 300 | 110,000 |
| Year 3 | 300 | 375 | 150,000 |

**Scaling Requirement**: Capacity must be expandable to 300 concurrent users without architectural change, software replacement, or vendor renegotiation beyond licence count adjustment.

**Aligns With**: Architecture Principle P-01 (Design for Horizontal Scale)

**Acceptance Criteria**:
- [ ] Load test at 300 concurrent users confirms all NFR-P-001 and NFR-P-002 targets met
- [ ] Vendor confirms capacity can be expanded to 300 concurrent users within 48 hours of request
- [ ] No single-tenancy hard limits below 500 concurrent users (to allow headroom)

**Priority**: HIGH

---

#### NFR-S-002: Data Volume Scalability

**Requirement**: The CRM must maintain NFR-P-001 performance targets as data volume grows to 500,000 customer records and 10 million interaction history records within 5 years.

**Data Volume Targets**:

| Data Entity | Year 0 (Go-live) | Year 3 | Year 5 |
|------------|-----------------|--------|--------|
| Customer/Contact records | 50,000 | 150,000 | 500,000 |
| Interaction history records | 200,000 | 2,000,000 | 10,000,000 |
| Open opportunities | 5,000 | 15,000 | 40,000 |
| Cases (open + closed 12 months) | 10,000 | 40,000 | 100,000 |

**Archival Strategy**: Records inactive for more than 3 years must be archivable to a warm storage tier without impacting search performance on active records.

**Acceptance Criteria**:
- [ ] Vendor provides documented evidence (benchmark results or reference customer data) of performance at target data volumes
- [ ] Load test uses production-equivalent data volume (not synthetic clean data)
- [ ] Archival strategy documented with tested restore procedure before go-live

**Priority**: HIGH

---

#### NFR-S-003: Storage Scalability

**Requirement**: Document, attachment, and email storage capacity must scale to at least 5TB within 3 years without architectural change.

**Acceptance Criteria**:
- [ ] Storage tier expandable to 10TB without data migration or restructuring
- [ ] Storage growth rate monitored with alert when 80% of licensed storage is consumed

**Priority**: MEDIUM

---

### Security Requirements

#### NFR-SEC-001: Authentication

**Requirement**: All CRM users must authenticate using the organisation's existing identity provider via industry-standard federation protocols. Multi-factor authentication (MFA) is mandatory for all users accessing the system from outside the corporate network.

**Authentication Requirements**:
- Integration with corporate identity provider via SAML 2.0 or OIDC/OAuth 2.0
- Single Sign-On (SSO): users authenticated via SSO must not be required to re-enter credentials to access the CRM
- MFA required for: all external access (off-network), all administrator accounts, all users with access to personal data export functions
- Session timeout: 8 hours of continuous session (absolute), 30 minutes of inactivity
- Re-authentication required for: bulk data export, user administration, data deletion operations

**Aligns With**: Architecture Principle P-03 (Security by Design)

**Acceptance Criteria**:
- [ ] SSO integration tested with corporate identity provider before go-live
- [ ] MFA enforced for all external access — verified by penetration test before go-live
- [ ] Session timeout behaviour confirmed in UAT
- [ ] No shared or generic user accounts permitted

**Priority**: CRITICAL

---

#### NFR-SEC-002: Role-Based Access Control (RBAC)

**Requirement**: The CRM must implement granular role-based access control aligned to the organisation's job roles, enforcing least-privilege access to all data and functions.

**Required Roles** (minimum — to be refined during configuration):

| Role | Description | Data Access Scope |
|------|-------------|------------------|
| Sales Representative | Own opportunities and accounts | Own assigned records only |
| Sales Manager | Team pipeline and forecasting | Team's records + read-only wider pipeline |
| CS Agent | Cases and customer 360 view | All customer records (read); own cases (write) |
| CS Team Leader | Team cases and reporting | Team cases + read-only customer data |
| Marketing Analyst | Leads, campaigns, attribution | Contact records (read); campaigns (write) |
| CRM Administrator | System configuration | All records + configuration |
| DPO / Privacy Officer | Consent records, SAR workflow | Full read access; consent/deletion write |
| Read-Only Analyst | Reporting and dashboards | Read-only all records |

**Additional Requirements**:
- Field-level security: sensitive fields (e.g., personal contact details, payment-related notes) must be concealable from roles that do not require them
- Record-level security: sales reps must not see competitors' account records or out-of-territory accounts unless explicitly shared
- Privilege elevation: temporary elevated access must require manager approval, be time-limited (maximum 24 hours), and be fully audit-logged

**Aligns With**: Architecture Principle P-03

**Acceptance Criteria**:
- [ ] RBAC configuration tested for all defined roles before go-live
- [ ] Penetration test verifies horizontal privilege escalation is not possible
- [ ] Audit log captures all privilege elevation events
- [ ] RBAC matrix documented and approved by IT Director and DPO before go-live

**Priority**: CRITICAL

---

#### NFR-SEC-003: Data Encryption

**Requirement**: All personal data and confidential business data stored in the CRM must be encrypted at rest. All data in transit between clients and the CRM platform must be encrypted using industry-standard transport security.

**Encryption Requirements**:
- Data at rest: industry-standard symmetric encryption (equivalent to AES-256) for all data stores, backups, and exported files
- Data in transit: TLS 1.2 minimum for all connections; TLS 1.3 preferred; TLS 1.0 and 1.1 must be disabled
- Field-level encryption: personal data fields (name, email, phone, address) must be encrypted at the application level in addition to database-level encryption
- Encryption key management: encryption keys must be managed separately from the encrypted data, with customer-managed key (CMK) capability available

**Data Residency**: All personal data relating to UK/EEA data subjects must be stored and processed in UK or EEA data centres. No personal data may be transferred to third countries without a documented and legally valid transfer mechanism (UK adequacy decision, SCCs, or equivalent).

**Aligns With**: Architecture Principle P-03, P-07

**Acceptance Criteria**:
- [ ] Vendor provides written confirmation of encryption standards used for data at rest and in transit
- [ ] Vendor confirms UK/EEA data residency for all personal data processing
- [ ] TLS configuration tested and confirmed — TLS 1.0 and 1.1 disabled before go-live
- [ ] Key management documentation reviewed by IT Security before contract signature

**Priority**: CRITICAL

---

#### NFR-SEC-004: Secrets and Credentials Management

**Requirement**: No credentials, API keys, passwords, or certificates used by the CRM or its integrations may be stored in application code, configuration files, or version control systems.

**Requirements**:
- All integration credentials stored in a dedicated secrets management system
- API keys and service account passwords must be rotatable without downtime
- Credential rotation: API keys must be rotatable at least annually; certificates must be rotatable before expiry with at least 30 days' notice
- Service accounts used by integrations must follow least-privilege principle — scoped to the minimum permissions required

**Aligns With**: Architecture Principle P-03

**Acceptance Criteria**:
- [ ] Integration architecture review confirms no credentials in code or config files
- [ ] Credential rotation procedure documented and tested before go-live
- [ ] All service account permissions reviewed and approved by IT Security

**Priority**: CRITICAL

---

#### NFR-SEC-005: Vulnerability Management

**Requirement**: The CRM platform must maintain a continuous vulnerability management programme, with remediation SLAs for identified vulnerabilities.

**Requirements**:
- Vendor must provide a documented vulnerability disclosure and patching policy
- Critical and high-severity vulnerabilities: remediated (patched) within 14 days of disclosure
- Medium-severity vulnerabilities: remediated within 60 days of disclosure
- Low-severity vulnerabilities: remediated within 180 days of disclosure
- Vendor must notify the organisation within 24 hours of any vulnerability directly affecting the organisation's CRM instance
- Annual penetration test of the CRM environment must be conducted by an accredited third party (CREST or equivalent) before go-live and annually thereafter

**Aligns With**: Architecture Principle P-03

**Acceptance Criteria**:
- [ ] Vendor provides vulnerability management policy and patching SLAs in contract
- [ ] Pre-go-live penetration test completed with no critical findings unresolved
- [ ] Penetration test scope includes CRM application, API, and integration layer
- [ ] Vendor provides evidence of most recent internal security assessment

**Priority**: CRITICAL

---

#### NFR-SEC-006: Security Audit Logging

**Requirement**: The CRM must maintain a comprehensive, tamper-evident audit log of all security-relevant events.

**Events to be Logged** (minimum):
- All authentication events (success, failure, MFA challenge, session timeout)
- All authorisation failures (access denied events)
- All data access to personal data fields
- All data exports and downloads (who exported what, when)
- All record creation, modification, and deletion
- All privilege elevation requests and approvals
- All consent changes (see FR-005)
- All SAR workflow actions (see FR-006)
- All administrator actions

**Log Requirements**:
- Tamper-evident: logs must be stored in a way that detects modification (cryptographic hashing or equivalent)
- Immutable retention: security and audit logs retained for minimum 12 months online, 7 years archived
- Exportable: logs must be exportable to the organisation's SIEM or log aggregation platform
- Searchable: logs must be searchable by user, time range, event type, and record ID within 30 seconds for queries spanning 12 months of data

**Aligns With**: Architecture Principle P-03, P-05, P-07

**Acceptance Criteria**:
- [ ] Audit log coverage confirmed in security architecture review — all required event types logged
- [ ] Log tamper-evidence mechanism documented and reviewed by IT Security
- [ ] Log export to SIEM tested before go-live
- [ ] Log retention configuration confirmed — 7-year archival path operational before data migration

**Priority**: CRITICAL

---

### Compliance Requirements

#### NFR-C-001: UK GDPR and Data Protection Act 2018

**Requirement**: The CRM must provide technical controls sufficient to demonstrate compliance with the UK General Data Protection Regulation (UK GDPR) and the Data Protection Act 2018 across all processing activities.

**Specific Technical Requirements**:
- Consent management: capture, store, and enforce granular marketing consent at the individual contact level (see FR-005)
- Lawful basis documentation: every contact record must have a documented lawful basis for processing selected from a controlled list before the record is saved
- Right to erasure: automated deletion workflow must be available, deleting or anonymising all personal data fields on request, with confirmation report
- Right of access (SAR): automated export workflow producing all personal data fields for a data subject within 30 minutes of processing (see FR-006)
- Right to portability: personal data must be exportable in a machine-readable format (CSV or JSON) for the data subject
- Data retention: automated retention schedules must enforce deletion/anonymisation of records after the defined retention period without manual intervention
- Data residency: all personal data stored and processed in UK or EEA (see NFR-SEC-003)
- Privacy notice: system must record the version of the privacy notice in force at the time each consent was captured

**Data Processing Agreement (DPA)**:
- A compliant DPA between the organisation and the CRM vendor must be executed before any personal data is migrated to the platform
- DPA must cover: processing purpose and scope, security obligations, sub-processor list, data subject rights support, breach notification (within 72 hours), and UK/EEA data residency

**Aligns With**: Architecture Principle P-07

**Acceptance Criteria**:
- [ ] DPA reviewed by DPO and Legal, signed before data migration begins
- [ ] DPIA completed for the CRM data processing activities before migration
- [ ] All GDPR technical controls tested by DPO before go-live sign-off
- [ ] Consent capture tested end-to-end (web form → CRM record → marketing suppression)
- [ ] SAR workflow tested: complete export produced within 30 minutes
- [ ] Retention automation tested: records aged beyond retention period identified and deleted/anonymised in test environment

**Priority**: CRITICAL

---

#### NFR-C-002: Audit Log Retention for Regulatory Compliance

**Requirement**: Audit and security logs must be retained for a minimum of 7 years in tamper-evident storage to satisfy potential ICO investigation requirements and the organisation's own data governance obligations.

**Retention Schedule**:

| Log Type | Online Retention | Archived Retention | Total |
|----------|-----------------|--------------------|-------|
| Security audit logs (auth, access, exports) | 12 months | 6 years | 7 years |
| Consent change history | Duration of relationship + 3 years | — | Minimum 3 years post-deletion |
| SAR processing records | 3 years | 4 years | 7 years |
| Data deletion records | 3 years | 4 years | 7 years |
| General application logs | 30 days | 11 months | 12 months |

**Acceptance Criteria**:
- [ ] Vendor confirms retention configuration for each log type before contract signature
- [ ] Archival path tested — logs retrievable from archive within 4 hours of request
- [ ] Retention configuration reviewed and approved by DPO

**Priority**: CRITICAL

---

#### NFR-C-003: Accessibility — WCAG 2.1 Level AA

**Requirement**: The CRM web application must comply with WCAG 2.1 Level AA accessibility standards to ensure equitable access for all employees regardless of disability.

**Required Features**:
- [ ] Full keyboard navigation for all functions (no mouse-only interactions)
- [ ] Screen reader compatibility (NVDA, JAWS, VoiceOver)
- [ ] Colour contrast ratio at least 4.5:1 for normal text, 3:1 for large text
- [ ] Adjustable text size (up to 200% without loss of content or functionality)
- [ ] Alt text for all non-decorative images
- [ ] Focus indicators visible for all interactive elements

**Scope**: Web application only. Mobile app must meet WCAG 2.1 Level A as minimum.

**Testing**: Automated accessibility testing (e.g., axe or equivalent) in CI/CD pipeline, plus manual testing with assistive technology before go-live.

**Acceptance Criteria**:
- [ ] Automated accessibility scan shows zero critical WCAG 2.1 AA violations before go-live
- [ ] Manual accessibility test conducted with at least one user of assistive technology
- [ ] Vendor provides accessibility conformance report (VPAT or equivalent) before contract signature

**Priority**: HIGH

---

#### NFR-C-004: Data Migration Compliance

**Requirement**: Before any personal data is migrated from legacy systems into the CRM, 100% of contact records must have a documented and verified lawful basis for processing, and the organisation's Privacy Notice must be updated to reflect the new processing activities.

**Pre-Migration Compliance Checklist**:
- [ ] Privacy Notice updated and published before migration
- [ ] Consent validation exercise completed — all contacts without verified consent either re-permissioned or excluded from migration
- [ ] Data minimisation review completed — personal data fields not required for CRM purposes excluded from migration
- [ ] DPA with CRM vendor signed
- [ ] DPIA approved by DPO
- [ ] Migration data quality acceptance criteria agreed (less than 0.5% duplicate rate, 100% of key account records validated)

**Acceptance Criteria**:
- [ ] DPO provides written sign-off on compliance checklist before migration start date
- [ ] Migration audit report produced confirming 100% lawful basis coverage for migrated records
- [ ] Post-migration validation confirms no personal data migrated without lawful basis

**Priority**: CRITICAL

---

### Usability Requirements

#### NFR-U-001: Adoption-Optimised User Experience

**Requirement**: The CRM interface must be sufficiently intuitive that sales representatives can complete core daily tasks (log a call, update an opportunity, view an account) within 5 minutes of initial training, and achieve consistent usage without supervision.

**Rationale**: Two previous CRM implementations failed due to poor adoption (under 40% compliance at 6 months). The user experience must be a first-class design consideration, not an afterthought. Sales rep adoption is the existential risk to the programme (see Risk R-1, ARC-001-STKE-v1.0).

**UX Requirements**:
- Maximum 3 clicks to complete any core sales task (log activity, update stage, add note)
- Email and calendar integration must reduce, not add to, manual data entry burden
- Mobile interface must be optimised for one-handed use on a smartphone
- No mandatory fields that require data a sales rep cannot reasonably know in the field
- New user onboarding: guided tour or interactive tutorial for first-time users

**Acceptance Criteria**:
- [ ] UAT with 10 pilot sales reps: all reps can complete core tasks in under 5 minutes after 30-minute training
- [ ] Post-UAT adoption survey: at least 80% of pilot reps rate the system "easy" or "very easy" to use
- [ ] Core task click-count validated: log call, update opportunity stage, add account note all achievable in 3 clicks or fewer

**Priority**: CRITICAL (adoption risk)

---

#### NFR-U-002: Mobile Application Usability

**Requirement**: The mobile application must support full core sales rep functionality on iOS 16+ and Android 13+ with offline capability for up to 8 hours.

**Mobile-Specific Requirements**:
- Offline access to assigned accounts, contacts, and opportunities (cached data up to 8 hours old)
- Activity logging (call note, meeting note) available offline with sync on reconnect
- Touch-optimised interface — minimum 44px touch targets for all interactive elements
- Biometric authentication (Face ID, fingerprint) supported for app unlock

**Acceptance Criteria**:
- [ ] Mobile app tested on minimum iOS 16 (iPhone 12) and Android 13 (mid-range device)
- [ ] Offline mode tested: user can log activity with no network connection and confirm sync on reconnect
- [ ] Biometric authentication tested on both iOS and Android

**Priority**: HIGH

---

### Maintainability and Observability Requirements

#### NFR-M-001: System Observability

**Requirement**: The CRM platform must expose operational telemetry (availability, performance, error rates, integration status) via a monitoring interface accessible to the organisation's IT operations team.

**Required Telemetry**:
- System availability and response time metrics (aligned to NFR-P-001 and NFR-A-001)
- Integration health status for each connected system (ERP, marketing automation, telephony)
- Error rate per module (sales, service, marketing, API layer)
- Active session count and concurrent user count
- Storage utilisation and growth trend
- Failed authentication and security alert counts

**Access Requirements**:
- Operational dashboard accessible to IT operations without vendor support engagement
- Metrics exportable to the organisation's monitoring platform (standard protocols: REST API or SNMP)
- Email or webhook alerting for critical events (availability below target, integration failure, security threshold exceeded)

**Aligns With**: Architecture Principle P-05 (Observability as a First-Class Requirement)

**Acceptance Criteria**:
- [ ] Monitoring dashboard reviewed and accepted by IT Operations before go-live
- [ ] Metric export to organisation monitoring platform tested before go-live
- [ ] Alert thresholds configured and tested — test alert received within 5 minutes of threshold breach

**Priority**: HIGH

---

#### NFR-M-002: API and Integration Documentation

**Requirement**: The CRM platform must provide complete, up-to-date API documentation sufficient for the organisation's integration engineers to build and maintain integrations without vendor support involvement.

**Documentation Requirements**:
- REST API: complete OpenAPI 3.0 specification for all API endpoints used in integrations
- Event/webhook documentation: schema and payload specification for all outbound events
- Integration guides: step-by-step guides for ERP, marketing automation, and telephony integration patterns
- Sandbox environment: a non-production sandbox instance with full API access for integration development and testing

**Aligns With**: Architecture Principle P-04 (Interoperability Through Standard Interfaces)

**Acceptance Criteria**:
- [ ] OpenAPI specification provided and validated (all integration endpoints documented) before contract signature
- [ ] Sandbox environment available for integration development at least 8 weeks before go-live
- [ ] Integration guides for ERP and marketing automation reviewed by IT integration team

**Priority**: HIGH

---

#### NFR-M-003: Vendor Support and SLA

**Requirement**: The CRM vendor must provide enterprise-grade support with defined response and resolution SLAs for production incidents.

**Support SLAs**:

| Incident Severity | Definition | Response Time | Resolution Target |
|------------------|------------|---------------|------------------|
| P1 — Critical | System unavailable or data loss | 1 hour | 4 hours |
| P2 — High | Major feature unavailable; significant business impact | 4 hours | 1 business day |
| P3 — Medium | Feature impaired; workaround available | 1 business day | 5 business days |
| P4 — Low | Minor issue; cosmetic or minor inconvenience | 2 business days | 20 business days |

**Additional Requirements**:
- 24/7 support for P1 and P2 incidents
- Named customer success manager assigned to the organisation's account
- At least 12 months advance notice of end-of-life for any platform version
- At least 6 months advance notice of breaking API changes

**Acceptance Criteria**:
- [ ] Support SLAs documented in contract with financial remedy (service credits) for breach
- [ ] Support escalation path documented and tested before go-live (P1 test ticket raised and resolved)
- [ ] Named CSM introduced before contract signature

**Priority**: HIGH

---

### Portability and Interoperability Requirements

#### NFR-I-001: Data Portability and Exit Rights

**Requirement**: The organisation must retain the right to export all its data from the CRM platform in a standard, machine-readable format at any time and without additional charge.

**Export Requirements**:
- All CRM data (contacts, accounts, opportunities, cases, activities, custom fields, audit logs) exportable to CSV or JSON format
- Export must be completable by the organisation without vendor assistance
- Export of the complete data set must complete within 24 hours
- At contract termination, vendor must provide a complete data export and must not delete the organisation's data for at least 90 days after contract end

**Acceptance Criteria**:
- [ ] Data export capability demonstrated in vendor evaluation (complete export of test data)
- [ ] Export SLA and termination data retention terms included in contract
- [ ] Export procedure documented in IT runbooks before go-live

**Priority**: HIGH

---

#### NFR-I-002: Integration Standards Compliance

**Requirement**: All CRM APIs used for integration must follow published, versioned interface standards with a documented backward compatibility and deprecation policy.

**Requirements**:
- REST APIs must follow consistent URL structure, HTTP method conventions, and error response formats
- API versioning: breaking changes must be introduced in a new API version; the previous version must remain supported for at least 12 months
- Webhook payloads must use a consistent envelope structure with event type, timestamp, and correlation ID
- All APIs must support OAuth 2.0 or equivalent for authentication

**Aligns With**: Architecture Principle P-04 (Interoperability Through Standard Interfaces), P-10 (Loose Coupling)

**Acceptance Criteria**:
- [ ] API versioning and deprecation policy documented and reviewed by IT integration team
- [ ] At least 2 major API versions supported simultaneously (current and previous) confirmed by vendor
- [ ] OAuth 2.0 integration tested with the organisation's identity provider

**Priority**: HIGH

---

## Integration Requirements

### INT-001: ERP / Billing System Integration

**Purpose**: Synchronise account data, contract status, and billing information between the ERP and CRM to provide agents and sales reps with current account standing without switching systems.

**Integration Type**: Near-real-time API integration (event-driven preferred; polling as fallback)

**Data Exchanged**:
- ERP → CRM: Account status, contract value, renewal date, outstanding balance, order history (sync frequency: on-change, maximum 15-minute delay)
- CRM → ERP: New account creation, account name/address updates (sync on save)

**Integration Pattern**: Event-driven (ERP publishes account change events; CRM subscribes). Fallback to scheduled polling every 15 minutes if event streaming unavailable.

**Authentication**: OAuth 2.0 service-to-service (machine-to-machine)

**Error Handling**: Failed sync events written to dead letter queue; IT Operations alerted if queue depth exceeds 100 events; manual retry available via admin console

**SLA**: Data freshness: ERP account status visible in CRM within 15 minutes of change in ERP

**Priority**: MUST_HAVE

---

### INT-002: Marketing Automation Platform Integration

**Purpose**: Synchronise contact and lead data bidirectionally to enable closed-loop marketing attribution and ABM targeting.

**Integration Type**: Bidirectional near-real-time API

**Data Exchanged**:
- Marketing platform → CRM: New leads, lead scores, campaign engagement data, email opt-in/opt-out (sync on change)
- CRM → Marketing platform: Lead status updates, opportunity close data, contact preference changes, consent changes (sync on change, critical: consent changes within 24 hours)

**Integration Pattern**: Webhook-based (both platforms publish events on change); API polling fallback every 30 minutes

**Authentication**: OAuth 2.0 with scoped permissions (marketing platform may only read/write contact and campaign data)

**GDPR Note**: Consent changes must propagate from CRM to marketing platform within 24 hours. This is a hard compliance requirement, not a best-effort target.

**Priority**: MUST_HAVE

---

### INT-003: Telephony / CTI Integration

**Purpose**: Enable screen-pop functionality — automatically displaying the customer's CRM record when an inbound call connects to an agent.

**Integration Type**: Real-time CTI middleware integration

**Data Exchanged**:
- Telephony → CRM: Inbound call event with caller ID; call connected/ended events
- CRM → Telephony: Customer lookup result (name, case count, account status)

**Integration Pattern**: Real-time event (CTI middleware pushes call event; CRM responds with lookup within 3 seconds)

**Authentication**: Service account with read-only access to contact and account records

**SLA**: Screen-pop latency under 3 seconds at p95 (see NFR-P-003)

**Note**: See Conflict C-3 — CTI integration is the highest technical complexity integration. Phase 1 delivery is the target; if IT resource constraints require deferral, this integration moves to Phase 2 with a committed delivery date.

**Priority**: MUST_HAVE (Phase 1 target; Phase 2 if deferred per Conflict C-3 resolution)

---

### INT-004: Email and Calendar Integration

**Purpose**: Auto-log emails and calendar meetings to the relevant CRM contact/opportunity record to reduce sales rep manual data entry.

**Integration Type**: Email server and calendar API integration (read-only)

**Data Exchanged**:
- Email/calendar → CRM: Sent/received emails and meeting invitations auto-matched to CRM contacts and logged as activities

**Integration Pattern**: Background sync via email/calendar provider API (OAuth 2.0); activity logged within 5 minutes of send/receive

**Authentication**: Per-user OAuth 2.0 authorisation (each rep authorises their own mailbox)

**Privacy Note**: Email content logging must be opt-in per user. Subject line and participants logged by default; email body logged only if user explicitly enables it.

**Priority**: MUST_HAVE

---

## Data Requirements

### DR-001: Customer Data Migration

**Migration Scope**: All customer, contact, account, opportunity, and case data from the existing fragmented systems (estimated 11 source systems including Salesforce Starter, Zendesk, and spreadsheet-based tools).

**Migration Strategy**: Phased migration — priority accounts (top 500 by revenue) migrated and validated first; remaining records migrated in batches. No big-bang migration.

**Data Quality Acceptance Criteria** (go/no-go for migration):
- Duplicate rate: less than 0.5% of migrated records are duplicates of another migrated record
- Completeness: at least 95% of records have all mandatory fields (name, at least one contact method, lawful basis)
- Consent validation: 100% of contact records have a documented lawful basis before migration
- Key account validation: 100% of top 500 accounts validated by the owning sales rep before migration

**Rollback Plan**: 30-day parallel run — legacy systems remain accessible for 30 days post-migration; any record discrepancy resolved within the 30-day window.

**Priority**: CRITICAL

---

### DR-002: Data Retention and Deletion

**Retention Schedule** (minimum — subject to DPO review):

| Data Category | Active Retention | Archive Retention | Total | Deletion Method |
|--------------|-----------------|------------------|-------|-----------------|
| Active customer (B2B) | Duration of relationship | 3 years post-relationship end | Variable | Anonymisation |
| Active customer (B2C) | Duration of relationship | 1 year post-last-interaction | Variable | Erasure |
| Prospects (no purchase) | 24 months from last engagement | N/A | 24 months | Erasure |
| Closed-lost opportunities | 3 years | N/A | 3 years | Anonymisation |
| Service cases (resolved) | 3 years | 4 years | 7 years | Anonymisation |
| Audit logs | 12 months | 6 years | 7 years | N/A (immutable) |
| Consent records | Duration of consent + 3 years | 4 years | 7 years minimum | Erasure |

**Automation Requirement**: Retention enforcement must be fully automated. No manual process is acceptable for routine retention enforcement.

**Priority**: CRITICAL

---

### DR-003: Data Classification

All data held in the CRM must be classified according to the organisation's data classification policy (aligned to Architecture Principle P-06):

| Data Category | Classification | Access Control |
|--------------|---------------|----------------|
| Customer personal data (name, contact details) | CONFIDENTIAL | Role-based (see NFR-SEC-002) |
| Account commercial data (contract value, revenue) | CONFIDENTIAL | Sales and finance roles only |
| Customer service case notes | CONFIDENTIAL | CS and sales roles |
| Marketing campaign performance | INTERNAL | Marketing and management |
| Pipeline aggregate data (no PII) | INTERNAL | Management dashboards |
| System configuration and audit logs | RESTRICTED | IT Security and DPO only |

**Priority**: HIGH

---

## Constraints and Assumptions

### Technical Constraints

**TC-01**: The CRM must integrate with the existing ERP/billing system via its published REST API. No direct database access to the ERP is permissible.

**TC-02**: The CRM must integrate with the existing marketing automation platform (current: HubSpot). The integration must use HubSpot's published API and not require replacement of the marketing automation platform.

**TC-03**: The CRM must support the organisation's existing corporate identity provider for SSO. The identity provider uses SAML 2.0 or OIDC. Vendors must confirm compatibility before shortlisting.

**TC-04**: The CRM must be deployable as a SaaS solution. On-premise deployment is out of scope for this programme.

**TC-05**: All personal data must be stored in UK or EEA data centres. Vendors without UK/EEA data residency are disqualified.

---

### Business Constraints

**BC-01**: Programme budget is capped at £850,000 for implementation. Ongoing annual licence and support costs must not exceed £180,000 per year.

**BC-02**: Phase 1 go-live (core sales and service modules) must be achievable within 6 months of contract award. This is a business commitment made to the CEO.

**BC-03**: Data migration cannot commence until the DPO has signed off on the GDPR compliance checklist. No exceptions.

**BC-04**: The legacy Salesforce Starter and Zendesk licences must not be renewed — they expire within 12 months of the planned CRM go-live. The new CRM must be fully operational before these licences lapse.

---

### Assumptions

**A-01**: The existing corporate identity provider supports SAML 2.0 or OIDC, enabling SSO integration. If not, SSO setup will be an additional workstream.

**A-02**: The ERP/billing system's API is stable and documented. Any changes to the ERP API during the CRM implementation will be managed by the ERP team with at least 4 weeks' notice.

**A-03**: The existing telephony platform supports a standard CTI integration interface (e.g., SIP or a published CTI API). Vendor confirmation required during discovery.

**A-04**: The 50,000 estimated customer records are a reasonable baseline. Final record count will be confirmed during the data audit, which is the first workstream of the programme.

**A-05**: Sales representatives will be provided with corporate-managed mobile devices (iOS or Android) for the mobile CRM application. Personal device (BYOD) support is a future phase consideration.

---

## Success Criteria and KPIs

### Business Success Metrics

| Metric | Baseline | Target | Timeline | Measurement Method |
|--------|----------|--------|----------|-------------------|
| Annual Recurring Revenue (ARR) | £8.4M | £9.66M (+15%) | Month 12 post go-live | Finance system monthly close |
| Sales forecast variance | 30–40% | Under 10% | Month 6 post go-live | CRM pipeline vs actuals |
| Average deal cycle | 62 days | 45 days | Month 12 post go-live | CRM opportunity pipeline |
| CS average handle time | 8.5 minutes | 5.5 minutes | Month 6 post go-live | ACD system reports |
| First contact resolution rate | 61% | 75% | Month 6 post go-live | Case management reporting |
| Net Promoter Score (NPS) | 51 | 68 | Month 12 post go-live | Quarterly customer survey |
| SAR response time | 12–18 hours | Under 2 hours | Go-live | DPO process log |
| CRM adoption rate (sales) | 0% | 80% by day 60 | Day 60 post go-live | CRM active user reporting |

### Technical Success Metrics

| Metric | Target | Measurement Method |
|--------|--------|-------------------|
| System availability | 99.5% monthly | Vendor + independent monitoring |
| UI response time (p95) | Under 3 seconds | APM tooling |
| API response time (p95) | Under 300ms (reads) | API gateway metrics |
| Error rate | Under 0.1% | Log aggregation |
| Integration data freshness | Under 15 minutes (ERP) | Integration monitoring |
| Mean time to recovery (MTTR) | Under 4 hours | Incident tracking |

---

## Requirement Conflicts & Resolutions

### Conflict C-1: Speed of Deployment vs. Milestone-Based Funding

**Conflicting Requirements**:
- **Requirement A**: BC-02 — Phase 1 go-live within 6 months of contract award (VP Sales, CEO)
- **Requirement B**: BR-004 — Finance Director requires milestone-based evidence before releasing full budget, creating pressure for a longer, more cautious programme

**Stakeholders Involved**:
- **VP Sales**: Needs pipeline data quality improvements urgently — every month of delay is a month without the 15% ARR growth contribution from CRM. Personal commitment to board on FY2026/27 target.
- **Finance Director**: Cautious after two previous failed technology programmes. Will not release full budget without milestone evidence. Phased funding is the mechanism for managing risk.

**Nature of Conflict**: A strict milestone-gated funding model could delay Phase 1 go-live if early milestones are slow, while the VP Sales needs the fastest possible deployment of core pipeline functionality.

**Trade-off Analysis**:

| Option | Pros | Cons |
|--------|------|------|
| **Option 1**: Full upfront budget release | Fastest deployment, no funding delays | Finance Director will not approve — too much risk given programme history |
| **Option 2**: Strict milestone gating (every deliverable gated) | Maximum financial risk control | Too slow — Phase 1 could slip 2–3 months while awaiting gate approvals |
| **Option 3**: Phase-based release (2 tranches: Phase 1 design + Phase 1 delivery) | Balances speed and risk control | Requires expedited gate reviews |

**Resolution Strategy**: COMPROMISE — Phase-based budget release

**Decision**: Two-tranche funding release: (1) £350,000 released on contract award to fund Phase 1 design and procurement; (2) £500,000 released on Phase 1 design review gate approval (estimated week 8). Milestone evidence required at gate, but gate review is time-boxed to 5 business days to prevent delay.

**Decision Authority**: Finance Director (accountable), CEO (sponsor). Reference: ARC-001-STKE-v1.0 RACI matrix.

**Impact on Requirements**:
- BC-02 (6-month Phase 1 go-live) maintained — gate review is time-boxed
- BR-004 ROI tracking begins from month 1 post go-live, not from contract award

**Stakeholder Management**:
- VP Sales: Gate review is time-boxed to 5 business days — maximum 1-week delay to Phase 1 timeline
- Finance Director: Milestone evidence report for gate prepared by Programme Director with Finance sign-off before gate

---

### Conflict C-2: Sales Rep Simplicity vs. DPO Compliance Data Capture

**Conflicting Requirements**:
- **Requirement A**: NFR-U-001 — UI optimised for adoption; maximum 3 clicks for core tasks; no mandatory fields a rep cannot reasonably know
- **Requirement B**: NFR-C-001 / FR-005 — Every contact record must have a documented lawful basis before saving; consent management fields required

**Stakeholders Involved**:
- **Sales Representatives (SD-8)**: Complex, form-heavy interfaces killed both previous CRM attempts. Every additional mandatory field increases abandonment risk and undermines adoption.
- **DPO (SD-7)**: Lawful basis documentation is a legal obligation under UK GDPR Article 13. It cannot be optional. The organisation's ICO advisory notice means this is under active regulatory scrutiny.

**Nature of Conflict**: Both requirements are legitimate. Compliance fields must be present; adoption depends on minimising friction. The conflict is in the implementation approach, not the principle.

**Trade-off Analysis**:

| Option | Pros | Cons |
|--------|------|------|
| **Option 1**: Full compliance fields on every create screen | Legally complete | Adoption risk — reps will find workarounds |
| **Option 2**: Compliance fields optional (advisory only) | Maximum rep simplicity | Legally unacceptable — not an option |
| **Option 3**: Contextual compliance fields (shown based on record type and source) | Minimal friction where not needed; compliant where required | Requires careful UX design and configuration |
| **Option 4**: Compliance fields pre-populated via integration (consent captured at web form; lawful basis inferred from lead source) | Zero rep friction for leads from compliant sources | Requires integration investment; manual records still need fields |

**Resolution Strategy**: INNOVATE — Contextual fields + source-based pre-population

**Decision**: Options 3 and 4 combined. Consent and lawful basis fields pre-populated from lead source data where available (web form, marketing automation). For manually created records, lawful basis is a single-click dropdown defaulting to the most common value ("Legitimate interests — B2B sales") with a tooltip explanation. The full consent management UI is available but not the default view for sales reps.

**Decision Authority**: DPO (compliance sign-off), VP Sales (adoption sign-off), IT Director (configuration feasibility). Joint decision by steering committee.

**Impact on Requirements**:
- NFR-U-001 maintained: 3-click target met for standard sales tasks
- NFR-C-001 maintained: lawful basis field is always required before save, but defaults are pre-configured to reduce friction
- FR-005 updated: consent management UI is role-conditional (full UI for DPO/marketing; simplified view for sales reps)

**Stakeholder Management**:
- Sales Representatives: Configuration shown in pilot group UAT. Pilot reps sign off on usability before company-wide rollout.
- DPO: DPO reviews and approves the default lawful basis values and the contextual field logic before configuration sign-off.

---

### Conflict C-3: CTI Integration Priority vs. IT Resource Constraints

**Conflicting Requirements**:
- **Requirement A**: FR-008, NFR-P-003 — CTI screen-pop delivered in Phase 1 to achieve NFR-A-001 handle time reduction (8.5 → 5.5 minutes)
- **Requirement B**: IT Director has limited integration resource. ERP (INT-001) and marketing automation (INT-002) integrations are also required for Phase 1. CTI (INT-003) is the most technically complex integration.

**Stakeholders Involved**:
- **Head of Customer Service (SD-4)**: Screen-pop is the primary mechanism for handle time reduction. Without it, the 5.5-minute target is not achievable in Phase 1. Personal KPI depends on this.
- **IT Director (SD-5)**: Integration resource is finite. Attempting 4 integrations in Phase 1 risks all 4 being delivered late or with quality issues. ERP and marketing automation have direct revenue dependencies.

**Nature of Conflict**: All four integrations are "must-have" but cannot all be completed to full quality in 6 months with available IT resource.

**Trade-off Analysis**:

| Option | Pros | Cons |
|--------|------|------|
| **Option 1**: All 4 integrations in Phase 1 | Full functionality at go-live | IT resource overloaded; quality risk across all integrations |
| **Option 2**: ERP + marketing automation in Phase 1; CTI in Phase 2 | Reduced risk; revenue integrations first | Handle time target misses Phase 1; Head of CS KPI at risk |
| **Option 3**: Investigate native CTI connector from CRM vendor (lower complexity than bespoke) | May resolve resource constraint | Depends on vendor capability — needs confirmation in RFP |

**Resolution Strategy**: PHASE + INNOVATE

**Decision**: CTI integration delivery is conditional on vendor providing a native/certified integration with the organisation's telephony platform (Option 3). RFP must ask vendors to confirm native CTI connector availability. If native connector available: CTI delivered in Phase 1. If native connector not available: CTI deferred to Phase 2 (target: month 9 post go-live), and Phase 1 handle time target rebased to 7.0 minutes (CTI-independent improvements only).

**Decision Authority**: IT Director (integration scope), Head of Customer Service (target rebase acceptance), Programme Director. Escalation to CEO if Head of CS does not accept rebased target.

**Impact on Requirements**:
- FR-008 and NFR-P-003: Phase 1 delivery conditional on vendor native CTI connector
- G-4 (handle time 8.5 → 5.5 min): Phase 1 target rebased to 7.0 min if CTI deferred; 5.5 min achieved in Phase 2
- INT-003 priority: vendor capability confirmed during RFP evaluation (weighted evaluation criterion)

**Stakeholder Management**:
- Head of Customer Service: Commitment given that CTI integration is Phase 2 no later than month 9 if deferred. Phase 1 improvements (single system, customer 360 view) still reduce handle time to approximately 7.0 minutes.
- Finance Director: Benefits realisation plan updated to reflect phased CTI delivery; CS cost savings delayed by approximately 3 months in the model.

---

## Timeline and Milestones

| Milestone | Description | Target Date | Dependencies |
|-----------|-------------|-------------|--------------|
| Requirements Approved | Stakeholder sign-off on this document | 2026-03-31 | This document |
| Vendor Shortlist | RFP issued, responses evaluated, 3 vendors shortlisted | 2026-04-30 | Requirements |
| Vendor Selected | Contract award | 2026-05-31 | Evaluation |
| Phase 1 Design Gate | Architecture design reviewed and approved | 2026-07-15 | Contract award + 6 weeks |
| Data Migration Prep | Consent validation complete; DPIA approved | 2026-08-31 | DPO sign-off |
| Phase 1 UAT | Pilot group UAT complete | 2026-10-15 | Development complete |
| Phase 1 Go-Live | Sales pipeline + CS case management live | 2026-11-30 | UAT passed, DPO sign-off |
| Phase 2 Go-Live | Marketing integration + CTI (if deferred) | 2027-03-31 | Phase 1 stable |
| Legacy Decommission | 11 → 3 systems confirmed | 2028-05-31 | Phase 2 + 6 months |

---

## Budget

### Cost Estimate

| Category | Estimated Cost | Notes |
|----------|----------------|-------|
| CRM platform licence (Year 1) | £120,000 | 200 licensed users, enterprise tier |
| Implementation (vendor + internal) | £480,000 | Configuration, data migration, integration, training |
| Integration development (ERP, marketing, CTI) | £150,000 | Internal IT + systems integrator |
| Infrastructure and tooling | £50,000 | iPaaS, monitoring, testing tools |
| Change management and training | £50,000 | Training programme, change ambassadors |
| **Total Implementation** | **£850,000** | |

### Ongoing Operational Costs

| Category | Annual Cost | Notes |
|----------|-------------|-------|
| CRM platform licence | £120,000 | Per-user licence |
| Integration platform (iPaaS) | £30,000 | Integration middleware |
| Support and administration | £30,000 | Internal IT + vendor support contract |
| **Total Annual** | **£180,000** | |

---

## Approval

### Requirements Review

| Reviewer | Role | Status | Date | Comments |
|----------|------|--------|------|----------|
| CEO | Executive Sponsor | PENDING | | |
| VP Sales | Business Owner | PENDING | | |
| Head of Customer Service | Business Owner | PENDING | | |
| IT Director | Technical Authority | PENDING | | |
| Finance Director | Budget Holder | PENDING | | |
| DPO | Compliance Authority | PENDING | | |
| Enterprise Architect | Document Owner | PENDING | | |

---

## Appendices

### Appendix A: Glossary

| Term | Definition |
|------|-----------|
| ARR | Annual Recurring Revenue |
| CTI | Computer Telephony Integration — technology linking phone systems to computer applications |
| DPA | Data Processing Agreement — contract between data controller and data processor |
| DPIA | Data Protection Impact Assessment — required under UK GDPR for high-risk processing |
| FCR | First Contact Resolution — case resolved on first agent interaction without transfer or callback |
| iPaaS | Integration Platform as a Service — middleware for managing system integrations |
| NPS | Net Promoter Score — customer loyalty metric (-100 to +100) |
| RPO | Recovery Point Objective — maximum acceptable data loss in a disaster scenario |
| RTO | Recovery Time Objective — maximum acceptable downtime in a disaster scenario |
| SAR | Subject Access Request — data subject's right to obtain a copy of their personal data |
| WCAG | Web Content Accessibility Guidelines |

### Appendix B: Reference Documents

- ARC-001-STKE-v1.0 — CRM System Stakeholder Drivers and Goals Analysis
- ARC-000-PRIN-v1.0 — Enterprise Architecture Principles
- UK General Data Protection Regulation (UK GDPR)
- Data Protection Act 2018
- NCSC Cyber Essentials guidance
- ICO Accountability Framework

---

## External References

| Document | Type | Source | Key Extractions | Path |
|----------|------|--------|-----------------|------|
| ARC-001-STKE-v1.0 | Stakeholder Analysis | Internal | Drivers SD-1 to SD-10; Goals G-1 to G-6; Conflicts C-1 to C-3 | projects/001-crm-system/ARC-001-STKE-v1.0.md |
| ARC-000-PRIN-v1.0 | Architecture Principles | Internal | P-01 to P-17 — NFR alignment | projects/000-global/ARC-000-PRIN-v1.0.md |

---

**Generated by**: ArcKit `/arckit:requirements` command
**Generated on**: 2026-03-01
**ArcKit Version**: 2.22.3
**Project**: CRM System (Project 001)
**AI Model**: claude-sonnet-4-6
**Generation Context**: Generated from ARC-001-STKE-v1.0 (stakeholder drivers and goals) and ARC-000-PRIN-v1.0 (architecture principles). NFR-focused per user request.
