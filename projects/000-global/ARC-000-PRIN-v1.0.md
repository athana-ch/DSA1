# Enterprise Architecture Principles

> **Template Status**: Live | **Version**: 1.0 | **Command**: `/arckit:principles`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-000-PRIN-v1.0 |
| **Document Type** | Enterprise Architecture Principles |
| **Project** | Global / Cross-Project (Project 000) |
| **Classification** | OFFICIAL |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-03-01 |
| **Last Modified** | 2026-03-01 |
| **Review Cycle** | Annual |
| **Next Review Date** | 2027-03-01 |
| **Owner** | Enterprise Architect |
| **Reviewed By** | PENDING |
| **Approved By** | PENDING |
| **Distribution** | All Technology Projects, Architecture Review Board, IT Leadership |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-03-01 | ArcKit AI | Initial creation from `/arckit:principles` command | PENDING | PENDING |

---

## Executive Summary

This document establishes the enterprise architecture principles governing all technology decisions across the organisation. These principles are the architectural "constitution" — they take precedence over project-level preferences and are referenced in requirements specifications, design reviews, vendor evaluations, and architecture conformance assessments.

**Scope**: All technology projects, systems, and initiatives — including the CRM System (Project 001) and all future projects.

**Authority**: Enterprise Architecture Review Board, ratified by IT Director / CTO.

**Compliance**: Mandatory for all new systems and major enhancements. Legacy systems are expected to achieve compliance through a managed migration path. Exceptions require formal approval (see Section VI).

**Philosophy**: These principles are **technology-agnostic**. They describe *what qualities* the architecture must have, not *how* to achieve them with specific products. Technology selection happens during research and design phases, guided by these principles. A principle that says "encrypt data at rest" is timeless; a principle that says "use AES-256" is a technical standard and belongs in a standards register, not here.

---

## I. Strategic Principles

### P-01: Design for Horizontal Scale

**Category**: Strategic

**Principle Statement**:
All systems MUST be designed to scale horizontally — by adding capacity rather than increasing the size of individual components — to meet both planned growth and unplanned demand spikes.

**Rationale**:
Business demand is inherently variable. A growing customer base, seasonal peaks, and marketing-driven traffic spikes require architecture that can expand and contract without manual intervention or fundamental redesign. Vertical scaling (bigger hardware) has hard limits and creates single points of failure. Horizontal scaling is more cost-effective and resilient at enterprise scale.

**Implications**:
- Components must be stateless or must externalise state to a shared store that all instances can access
- Session affinity (sticky sessions) should be avoided; if required, a documented justification is needed
- Load distribution mechanisms must be in place to spread traffic across instances
- Capacity must be measurable and scaling triggers must be defined and automated
- Cost models must account for variable (elastic) capacity rather than fixed provisioning

**Validation Gates**:
- [ ] System can add instances without architectural change
- [ ] No session or state stored exclusively in application memory
- [ ] Load distribution is automated, not manual
- [ ] Scaling triggers and thresholds are defined and tested
- [ ] Load testing confirms throughput increases proportionally with added instances

**Common Violations to Avoid**:
- Storing user session state in application memory without a shared session store
- Hard-coding instance counts or IP addresses in configuration
- Licensing models that charge per-CPU or per-server, creating a financial disincentive to scale

---

### P-02: Resilience and Graceful Degradation

**Category**: Strategic

**Principle Statement**:
All systems MUST gracefully degrade when dependencies become unavailable, recover automatically without data loss, and avoid cascading failures to other systems.

**Rationale**:
In distributed architectures, partial failure is not exceptional — it is routine. Assuming all dependencies will always be available leads to brittle systems that fail catastrophically rather than gracefully. Architecture must anticipate failure and ensure that the failure of one component is contained and does not propagate.

**Implications**:
- All outbound calls to external systems must have defined timeouts
- Retry logic must use exponential backoff with jitter to prevent thundering-herd problems
- Circuit breakers must protect the system from repeatedly calling an unavailable dependency
- Non-critical features must degrade gracefully when their backing services are unavailable (e.g., a CRM search feature failing should not prevent an agent from viewing a customer record)
- Bulkhead patterns must isolate critical workloads from non-critical ones
- Recovery Time Objective (RTO) and Recovery Point Objective (RPO) must be defined for every system

**Validation Gates**:
- [ ] Timeout values defined for all external calls
- [ ] Circuit breaker pattern implemented for all downstream dependencies
- [ ] Graceful degradation behaviour documented and tested for each dependency failure scenario
- [ ] RTO and RPO defined, agreed with the business, and tested via disaster recovery exercises
- [ ] Automated failover tested at least annually

**Common Violations to Avoid**:
- No timeout on database or API calls — a slow dependency becomes an indefinite hang
- Propagating a downstream 500 error directly to the user without a fallback behaviour
- Treating all failures as equal — a payment service outage and a recommendation service outage are not equivalent

---

### P-03: Security by Design (Non-Negotiable)

**Category**: Strategic

**Principle Statement**:
Security controls MUST be designed into every system from the outset. Security is not a feature to be added after delivery. All architectures MUST implement defence-in-depth with zero-trust principles: no implicit trust based on network location, continuous verification of all access, and least-privilege access to all resources.

**Rationale**:
The threat landscape assumes that perimeter defences will be breached. Internal network traffic is not inherently trustworthy. The cost of remediating a security issue after deployment is orders of magnitude higher than designing it correctly from the start. Regulatory obligations (UK GDPR, ICO guidance) impose legal duties on data processors and controllers.

**Zero Trust Pillars**:
1. **Identity-Based Access**: Every request — human or machine — must be authenticated and authorised before access is granted. Network location grants no privilege.
2. **Least Privilege**: Accounts and service identities must be granted the minimum permissions required for their function, for the minimum time required.
3. **Encryption Everywhere**: All data must be encrypted in transit and at rest. There are no exceptions for internal network traffic.
4. **Continuous Verification**: All access must be logged. Anomalous patterns must trigger alerts.

**Mandatory Controls**:
- [ ] Multi-factor authentication required for all human access to systems holding personal or sensitive data
- [ ] Service-to-service authentication using signed credentials (never shared static passwords)
- [ ] Secrets (API keys, database credentials, certificates) stored in a dedicated secrets management system — never in source code, configuration files, or environment variables committed to version control
- [ ] Network segmentation with explicit allow-list rules between segments
- [ ] All data stores encrypted at rest
- [ ] All data in transit encrypted using industry-standard transport protocols
- [ ] Authentication and authorisation events written to a tamper-evident audit log
- [ ] Dependency vulnerability scanning integrated into the deployment pipeline
- [ ] Penetration testing conducted before go-live for systems handling personal data

**Applicable Compliance Frameworks**:
- UK GDPR / Data Protection Act 2018 (mandatory for systems processing personal data)
- NCSC Cyber Essentials (minimum baseline for all systems)
- NCSC Secure by Design principles
- ISO 27001 (target certification for systems handling Confidential or above data)

**Exceptions**:
None. Security principles are non-negotiable. Specific control implementations may vary where documented compensating controls are in place and approved by the Information Security team.

**Validation Gates**:
- [ ] Threat model completed and peer-reviewed before design is finalised
- [ ] Security controls mapped to identified threats
- [ ] Secrets management solution in use — no secrets in code or config
- [ ] Dependency scanning integrated into CI/CD pipeline
- [ ] Penetration test completed (or scheduled) before handling production personal data

**Common Violations to Avoid**:
- Storing API keys or database passwords in `.env` files committed to source control
- Using service accounts with administrator-level permissions for routine operations
- Deferring penetration testing to "post-launch Phase 2"
- Treating internal APIs as trusted without authentication

---

### P-04: Interoperability Through Standard Interfaces

**Category**: Strategic

**Principle Statement**:
All systems MUST expose their functionality through well-defined, versioned interfaces using industry-standard protocols. Direct database access across system boundaries is prohibited.

**Rationale**:
Loose coupling through standard interfaces enables independent evolution, technology diversity, and system composability. When System A reads System B's database directly, any schema change in B breaks A — creating invisible, undocumented dependencies that make change expensive and risky.

**Implications**:
- All cross-system integration must use published interface contracts (API specifications, event schemas)
- Interfaces must be versioned, with a defined backward-compatibility and deprecation policy
- Consumers must be notified in advance of breaking changes with adequate transition time
- Direct database queries across system boundaries are prohibited without a formal exception
- Interface contracts must be machine-readable and publicly discoverable within the organisation

**Validation Gates**:
- [ ] Interface specifications published in a discoverable location (API catalogue, event registry)
- [ ] Versioning strategy defined and communicated to all consumers
- [ ] Deprecation and sunset policy documented
- [ ] No direct database access across system ownership boundaries
- [ ] Consumer-driven contract tests in place for critical integrations

**Common Violations to Avoid**:
- Writing SQL queries against another team's database as an "easy" integration
- Removing a field from an API response without a versioning strategy and consumer notification
- Undocumented point-to-point integrations not captured in the integration inventory

---

### P-05: Observability as a First-Class Requirement

**Category**: Strategic

**Principle Statement**:
All production systems MUST emit structured telemetry — logs, metrics, and distributed traces — sufficient to diagnose failures, measure service level performance, and plan capacity. Observability is designed in, not bolted on.

**Rationale**:
A system that cannot be observed cannot be operated. Debugging a production incident without logs, metrics, or traces is guesswork. The cost of adding observability post-deployment is high; the cost of a prolonged outage due to lack of visibility is higher.

**Required Telemetry**:
- **Structured Logs**: JSON-formatted, with correlation ID, timestamp, severity, service name, and request context. Human-readable log messages are an anti-pattern at scale.
- **Metrics**: Request volume, latency percentiles (p50, p95, p99), error rate, and resource utilisation (CPU, memory, I/O). Business metrics (transactions processed, active sessions) are also required.
- **Distributed Traces**: Trace context propagated across service calls to enable end-to-end request flow analysis.
- **Alerting**: Service Level Objective (SLO)-based alerts with actionable runbooks. Alerts must be actionable — alert fatigue from low-signal noise is as dangerous as no alerting.

**Log Retention Policy**:
- Security and audit logs: minimum 12 months online, 7 years archived (UK GDPR and ICO guidance)
- Application logs: minimum 30 days online for operational troubleshooting
- Metrics: minimum 13 months for trend analysis and capacity planning

**Validation Gates**:
- [ ] Structured logging implemented with correlation ID propagation
- [ ] Key metrics (latency, error rate, throughput) instrumented and visible in dashboard
- [ ] Distributed tracing enabled for inter-service calls
- [ ] SLOs defined and SLI measurements automated
- [ ] Runbooks exist for all production alerts
- [ ] Log retention configuration meets compliance requirements

**Common Violations to Avoid**:
- Unstructured log messages (plain text strings not parseable by log aggregation tools)
- No correlation ID — impossible to trace a single request across multiple services
- Alerts with no runbook — "CPU high" with no guidance on what to do

---

## II. Data Principles

### P-06: Customer Data as a Strategic Asset

**Category**: Data

**Principle Statement**:
Customer data MUST be treated as a strategic organisational asset. It must be governed, quality-controlled, and protected with the same rigour applied to financial assets. A single authoritative source of customer record MUST be maintained across all systems.

**Rationale**:
The organisation's ability to personalise service, manage accounts, and analyse customer behaviour depends entirely on the quality and completeness of customer data. Fragmented, inconsistent customer data — spread across CRM, billing, support, and marketing systems — produces the exact failures that undermine customer experience: agents asking customers to repeat themselves, duplicate marketing communications, inaccurate account status. Customer data is also subject to UK GDPR, making poor data governance a regulatory as well as a commercial risk.

**Implications**:
- One system must be designated as the system of record for each customer data entity (identity, contact details, account status, preferences, interaction history)
- All other systems holding copies of customer data are read-replicas or derived views — clearly labelled, with defined synchronisation frequency and a staleness SLA
- Customer data quality rules (completeness, accuracy, consistency) must be defined, automated, and monitored continuously
- A data model and data dictionary for customer entities must be maintained and version-controlled
- Customer data must never be siloed in a system that does not expose it via a standard interface

**Validation Gates**:
- [ ] System of record identified for each customer data entity
- [ ] Data dictionary for customer entities published and current
- [ ] Data quality rules defined and automated checks in place
- [ ] Derived copies documented with sync frequency and staleness SLA
- [ ] No customer data held exclusively in a system that cannot be queried via a standard interface

**Common Violations to Avoid**:
- Each team maintaining their own "master" customer record with no reconciliation
- Customer contact details updated in one system but not propagated to others
- Customer interaction history locked inside a tool with no API export

---

### P-07: Privacy by Design and UK GDPR Compliance

**Category**: Data

**Principle Statement**:
All systems that process personal data MUST embed privacy controls into the architecture from the outset. Lawful basis for processing must be established before data is collected. Consent, when used as the lawful basis, must be explicit, granular, and revocable. Automated data subject rights fulfilment (access, erasure, portability) must be designed in — not handled manually.

**Rationale**:
The organisation has an active ICO advisory notice and a regulatory obligation under the UK GDPR and the Data Protection Act 2018. The maximum fine for a serious breach is 4% of global annual turnover. Beyond legal risk, customers have a reasonable expectation that their personal data is handled with care. Privacy practices directly influence customer trust and retention.

**Privacy by Design Obligations**:
1. Data minimisation — collect only what is necessary for the stated purpose
2. Purpose limitation — data collected for one purpose must not be used for another without additional lawful basis
3. Storage limitation — automated retention schedules must delete data after the defined period
4. Accuracy — processes must exist to keep personal data accurate and current
5. Integrity and confidentiality — security controls proportionate to the risk to data subjects
6. Accountability — processing activities documented, DPIAs completed for high-risk processing

**Validation Gates**:
- [ ] Data Protection Impact Assessment (DPIA) completed for any high-risk processing
- [ ] Lawful basis documented for every category of personal data processed
- [ ] Consent management implemented where consent is the lawful basis (explicit opt-in, granular, revocable)
- [ ] Automated data retention rules implemented and tested — no manual deletion processes for routine retention
- [ ] Subject Access Request (SAR) response automated — target under 2 hours manual effort per request
- [ ] Data Processing Agreement (DPA) signed with every third-party processor before data is shared
- [ ] Data residency confirmed as UK/EU-compliant before any personal data is migrated to a new system

**Common Violations to Avoid**:
- Migrating legacy contact records to a new system without first validating consent records
- Using personal data collected for service delivery for marketing purposes without separate consent
- Relying on manual processes for data deletion — they will be inconsistently applied
- Assuming a vendor's "GDPR compliance" claim is sufficient without reviewing their DPA terms

---

### P-08: Data Quality and Lineage

**Category**: Data

**Principle Statement**:
Data pipelines MUST maintain defined quality standards and provide end-to-end lineage. Data quality is owned by the producing system — consumers must not be required to cleanse data they receive.

**Rationale**:
Poor data quality at the source compounds downstream. If the CRM receives incomplete or incorrectly formatted lead data from a web form, every report, campaign, and agent interaction built on that data is compromised. The cost of cleaning data late in the pipeline far exceeds the cost of validating it at source.

**Quality Dimensions**:
- **Completeness**: Required fields are always populated; no unexpected nulls
- **Consistency**: The same entity represented consistently across systems (no "John Smith" vs "J Smith" vs "J. Smith")
- **Accuracy**: Data values reflect real-world truth (addresses are valid, phone numbers are callable)
- **Timeliness**: Data is available within a defined freshness SLA for each use case
- **Uniqueness**: No duplicate records for the same real-world entity

**Validation Gates**:
- [ ] Data quality rules defined for each data domain and automated in the pipeline
- [ ] Data quality dashboards monitoring key metrics (null rates, duplicate rates, validation failure rates)
- [ ] Source-to-target lineage documented for all data flows
- [ ] Schema changes follow a governed change process with impact analysis
- [ ] Data contracts between producing and consuming systems are machine-readable and enforced

**Common Violations to Avoid**:
- Accepting whatever data arrives from an external system and attempting to clean it downstream
- Schema changes deployed without notifying downstream consumers
- No duplicate detection — producing multiple customer records for the same individual

---

### P-09: Single Source of Truth

**Category**: Data

**Principle Statement**:
Every data domain MUST have a single authoritative source. Derived copies must be clearly labelled as such, synchronised on a defined schedule, and must not be updated directly.

**Rationale**:
Multiple systems claiming authority for the same data produce reconciliation overhead, inconsistency, and loss of trust in the data. When an agent sees a different account balance in the CRM than in the billing system, they lose confidence in both — and the customer suffers.

**Implications**:
- The system of record for each data entity must be formally designated in the data architecture
- Derived copies are read-only views — updates must be directed to the system of record
- Bidirectional synchronisation between two systems (where either can update and the other must follow) is an anti-pattern. If required, a conflict resolution strategy must be formally approved
- Reference data (product codes, country lists, currency codes) must be managed in a single canonical source and distributed, not maintained independently in each system

**Validation Gates**:
- [ ] System of record documented in the data architecture for every major data entity
- [ ] All derived copies documented with sync mechanism, frequency, and staleness SLA
- [ ] No bidirectional sync without a documented and approved conflict resolution strategy
- [ ] Reference data management strategy defined

**Common Violations to Avoid**:
- Sales and finance teams each maintaining their own "master" customer list with no reconciliation process
- Building a reporting database that is also used for operational writes

---

## III. Integration Principles

### P-10: Loose Coupling

**Category**: Integration

**Principle Statement**:
Systems MUST be loosely coupled — dependent only on published interfaces, not on internal implementations. Systems must be independently deployable without coordination with the systems they depend on.

**Rationale**:
Tight coupling means a change in one system forces a change in another. In a landscape of 10+ systems (as was the case before the CRM programme), tight coupling creates a web of dependencies where nothing can be changed safely and independently. Loose coupling enables team autonomy, independent delivery cadence, and technology evolution.

**Implications**:
- Integration is always through published interfaces (API, event, message) — never by direct database access, shared file system, or shared in-memory state
- Each system manages its own data store — no shared databases
- The public interface of a system is a contract; its internal implementation can change freely without consumer impact
- Avoid distributed transactions that span multiple systems — prefer eventual consistency with compensating transactions
- Shared libraries must be minimal and stability-focused. Favour duplication over coupling for business logic that might diverge

**Validation Gates**:
- [ ] All integrations use published interfaces — no direct database access across system boundaries
- [ ] Each system has its own data store
- [ ] Deploying System A does not require simultaneous deployment of System B
- [ ] Interface contracts are versioned and backward-compatible within a major version
- [ ] No distributed transactions spanning multiple system boundaries

**Common Violations to Avoid**:
- Two services sharing a database schema as an "integration shortcut"
- A microservice calling another service's internal endpoints not documented in its public API
- A shared domain model library that every service imports, creating a coupling point for all teams

---

### P-11: Asynchronous Communication for Non-Real-Time Flows

**Category**: Integration

**Principle Statement**:
Systems SHOULD use asynchronous, event-driven communication for non-real-time interactions. Synchronous request-response is appropriate for real-time user interactions and queries; it is not appropriate for business process flows that span multiple systems.

**Rationale**:
Synchronous chains — where System A calls B which calls C which calls D — create temporal coupling: all four systems must be available simultaneously for the chain to succeed. Asynchronous event-driven patterns break this temporal dependency, improve fault tolerance, and allow each system to process at its own pace.

**When to Use Asynchronous**:
- Cross-system business processes (e.g., lead created in CRM triggers enrichment in marketing, notification in sales)
- Long-running operations (e.g., data migration, bulk processing)
- Integration with external systems that may be slow or unreliable
- Event notification (e.g., customer status changed, deal closed)

**When Synchronous is Appropriate**:
- Real-time user interactions requiring an immediate response (e.g., form submission returning a confirmation)
- Read/query operations with low latency requirements
- Operations that require immediate transactional consistency

**Validation Gates**:
- [ ] Asynchronous patterns used for all cross-system business process flows
- [ ] Message durability guaranteed — messages are not lost if a consumer is temporarily unavailable
- [ ] Event schemas are versioned and published
- [ ] Dead letter queues configured for failed message handling
- [ ] Idempotency implemented for all message consumers (processing the same message twice must not cause duplicate effects)

**Common Violations to Avoid**:
- A synchronous REST call chain spanning 4 services for a business process that does not require a real-time response
- No dead letter queue — failed messages silently disappear
- Non-idempotent consumers — processing a message twice charges a customer twice

---

## IV. Quality Attribute Principles

### P-12: Performance Requirements Defined Before Implementation

**Category**: Quality

**Principle Statement**:
Performance requirements (response time targets, throughput targets, concurrency limits) MUST be defined and agreed with the business before implementation begins. Systems must be load-tested against these targets before production deployment.

**Rationale**:
"It needs to be fast" is not a requirement. Measurable performance targets enable design decisions (caching strategy, database indexing, async offloading) to be made correctly upfront. Discovering performance problems after go-live is expensive, disruptive, and damaging to user trust.

**Standard Performance Targets** (to be confirmed per system):
- Interactive user-facing responses: p95 latency under 2 seconds, p99 under 5 seconds
- API responses (non-search): p95 latency under 500ms
- Background processes: defined throughput SLA (e.g., process 10,000 records per hour)
- Search/reporting queries: p95 latency under 3 seconds for standard queries

**Implications**:
- Performance requirements captured in the requirements specification alongside functional requirements
- Load testing performed at realistic production data volumes, not just with synthetic test data
- Caching strategies designed based on profiled hot paths — not speculatively applied everywhere
- Database query performance reviewed as part of design review

**Validation Gates**:
- [ ] Performance requirements documented with measurable p50, p95, p99 targets
- [ ] Load tests run at expected production scale before go-live
- [ ] Production performance metrics monitored continuously against targets
- [ ] Query execution plans reviewed for any queries against large data sets

---

### P-13: Availability and Recoverability

**Category**: Quality

**Principle Statement**:
All systems MUST define, agree, and meet availability targets. Redundancy, automated failover, and regular disaster recovery testing are mandatory for systems with an availability SLA at or above 99.5%.

**Rationale**:
A system without a defined availability target cannot be measured, and a system that cannot be measured cannot be improved. Agreeing availability targets with the business also provides a shared understanding of what level of investment in redundancy and resilience is justified.

**Availability Tiers**:

| Tier | Uptime SLA | Max Monthly Downtime | Typical Use Case |
|------|-----------|---------------------|-----------------|
| Standard | 99.0% | 7.3 hours | Internal tools, non-critical reporting |
| Enhanced | 99.5% | 3.7 hours | Operational systems (CRM, internal portals) |
| High | 99.9% | 43.8 minutes | Customer-facing services |
| Critical | 99.95%+ | 21.9 minutes | Payment, core transaction processing |

**Implications**:
- Systems at Enhanced tier and above require redundancy across at least two availability zones
- Automated health checks and recovery must be implemented — manual restart is not acceptable for Enhanced tier and above
- Disaster recovery exercises must be conducted at least annually, testing the full recovery procedure from a documented runbook
- RTO and RPO must be agreed with the business for each system and tested

**Validation Gates**:
- [ ] Availability tier assigned and approved by the business
- [ ] RTO and RPO defined and documented
- [ ] Redundancy strategy matches the availability tier
- [ ] Automated health checks and failover implemented and tested
- [ ] DR runbook documented and tested at least annually
- [ ] Backup and restore procedures validated with a timed restoration test

---

### P-14: Maintainability and Architectural Fitness

**Category**: Quality

**Principle Statement**:
All systems MUST be designed for change. Architectural decisions MUST be documented in Architecture Decision Records (ADRs). Automated test coverage must be sufficient to enable confident refactoring without manual regression testing.

**Rationale**:
A system's lifetime in production is orders of magnitude longer than its initial build time. The majority of total cost of ownership comes from maintenance, enhancement, and operation — not initial delivery. Design decisions that optimise for short-term delivery speed at the expense of maintainability compound over time into a technical debt burden that eventually makes the system unmaintainable.

**Implications**:
- Modular architecture with clearly defined component boundaries and responsibilities
- Architecture Decision Records document the context, options considered, decision made, and consequences for every significant architectural choice
- Automated test coverage at the unit and integration level must be sufficient that a developer can refactor a module and trust the test suite to catch regressions
- No "magic" — undocumented workarounds, unexplained configuration, or code only the original developer understands
- Technical debt must be tracked, sized, and scheduled for remediation — not ignored

**Validation Gates**:
- [ ] Architecture documented at system and component level and kept current
- [ ] ADRs written for all significant architectural decisions
- [ ] Automated test suite covers critical business logic and integration points
- [ ] No undocumented configuration or "tribal knowledge" dependencies
- [ ] Technical debt register maintained with remediation priorities

---

## V. Development and Delivery Principles

### P-15: Infrastructure as Code

**Category**: Delivery

**Principle Statement**:
All infrastructure MUST be defined as version-controlled code and deployed through automated pipelines. Manual changes to production infrastructure are prohibited.

**Rationale**:
Manual infrastructure changes create configuration drift between environments, produce undocumented state that is difficult to reproduce, and introduce human error. Infrastructure as Code enables environments to be reproduced reliably, audited through version history, and recovered rapidly in a disaster scenario.

**Implications**:
- All compute, networking, storage, and configuration defined in declarative code
- Infrastructure code reviewed through the same peer review process as application code
- Production infrastructure changes always flow through the automated pipeline — never via direct console access
- All environments (development, staging, production) are provisioned from the same code with environment-specific parameter overrides
- Infrastructure code is stored in the same version control system as the application code it supports

**Validation Gates**:
- [ ] 100% of production infrastructure defined as code
- [ ] Infrastructure code peer-reviewed before deployment
- [ ] No manual changes to production infrastructure (enforced via access controls)
- [ ] Environments reproducible from code in a documented time target
- [ ] Drift detection in place to identify undocumented changes

---

### P-16: Automated Testing

**Category**: Delivery

**Principle Statement**:
All code changes MUST be validated through automated testing before deployment to any environment above development. The test suite must be fast enough to run on every commit.

**Test Pyramid**:
- **Unit Tests** (70–80%): Fast, isolated, covering individual functions and classes
- **Integration Tests** (15–25%): Testing component interactions at service and database boundaries
- **End-to-End Tests** (5–10%): Critical user journeys only — kept small to remain fast and reliable

**Required Coverage Areas**:
- All business logic and calculation paths
- All API contract boundaries (consumer-driven contract tests for critical integrations)
- All data persistence operations
- Critical user journeys (smoke tests for go-live validation)
- Security controls (e.g., unauthenticated requests are rejected, authorisation rules are enforced)

**Validation Gates**:
- [ ] Automated tests run on every code commit via CI pipeline
- [ ] Test suite completes within 15 minutes for the pre-merge check
- [ ] Critical business logic has unit test coverage
- [ ] All API contracts covered by consumer-driven contract tests
- [ ] Security controls covered by automated tests (not just manual penetration testing)

---

### P-17: Continuous Integration and Deployment

**Category**: Delivery

**Principle Statement**:
All code changes MUST flow through an automated CI/CD pipeline with quality gates at each stage. No code is deployed to production without passing all automated quality gates.

**Pipeline Stages**:
1. **Commit**: Code committed to version control — triggers automated build and test
2. **Build**: Automated compilation, packaging, and artefact creation
3. **Test**: Full automated test suite execution
4. **Security Scan**: Dependency vulnerability scanning and static code analysis
5. **Deploy to Staging**: Automated deployment to a production-equivalent environment
6. **Smoke Test**: Automated validation of critical paths in staging
7. **Deploy to Production**: Automated or manual-gate deployment, with automated rollback capability

**Quality Gates** (must all pass before production deployment):
- All automated tests pass
- No critical or high severity security vulnerabilities introduced
- Code review approved by at least one peer
- Production readiness checklist completed for first deployments

**Validation Gates**:
- [ ] CI/CD pipeline exists and is the only route to production
- [ ] Pipeline includes dependency vulnerability scanning
- [ ] Rollback procedure automated and tested
- [ ] Deployment is repeatable — same pipeline run produces the same outcome
- [ ] No "cowboy" deployments — all production changes via pipeline only

---

## VI. Exception Process

### Requesting an Architecture Exception

These principles are mandatory for all new systems and major enhancements. Exceptions require formal approval.

**Valid Grounds for Exception**:
- A technical constraint that genuinely prevents compliance (must be demonstrated, not assumed)
- A regulatory or legal requirement that creates a conflict with a principle
- A transitional state during an approved migration or legacy system replacement, with a defined end date
- A time-limited proof of concept with a defined scope and sunset date

**Exception Request Requirements**:
- [ ] Named requester (project lead or architect)
- [ ] Principle(s) for which exception is requested
- [ ] Justification with specific technical or legal rationale
- [ ] Proposed compensating controls (how the intent of the principle is satisfied by other means)
- [ ] Risk assessment and mitigation plan
- [ ] Expiration date — all exceptions are time-bound (maximum 12 months, renewable)
- [ ] Remediation plan to achieve compliance before the expiration date

**Approval Process**:
1. Submit exception request to the Enterprise Architect
2. Review by Architecture Review Board (within 10 business days)
3. IT Director / CTO approval required for exceptions to P-03 (Security) or P-07 (Privacy)
4. Approved exception logged in the project's architecture documentation
5. Quarterly review of all active exceptions to confirm remediation is on track

**Exceptions Granted**:

| Exception ID | Project | Principle | Expiry | Status |
|-------------|---------|-----------|--------|--------|
| *None granted* | — | — | — | — |

---

## VII. Governance and Compliance

### Architecture Review Gates

All projects must pass the following architecture reviews at the gates below. Reviews are conducted by the Enterprise Architect with input from Information Security and Operations.

**Gate 1 — Concept / Discovery**:
- [ ] Architecture principles reviewed and understood by the delivery team
- [ ] High-level approach described and principles conflicts identified early
- [ ] Data classification of data to be processed confirmed
- [ ] No obviously disqualifying principle violations in the proposed approach

**Gate 2 — Design / Beta**:
- [ ] Detailed architecture documented and reviewed against each principle
- [ ] All principle compliance validated or exceptions formally requested
- [ ] Security threat model completed
- [ ] Data privacy impact assessment completed if personal data is processed
- [ ] Integration interfaces documented in the API/event catalogue

**Gate 3 — Pre-Production**:
- [ ] Implementation verified to match approved architecture
- [ ] All validation gates from each applicable principle confirmed as passing
- [ ] Load testing results reviewed
- [ ] Disaster recovery procedure tested and timed
- [ ] Runbooks complete and reviewed by operations team
- [ ] All approved exceptions are active (not expired)

### Enforcement

- Architecture reviews are **mandatory** for all projects with a total budget above £50,000 or any system processing personal data
- Principle violations identified at Gate 2 must be remediated before Gate 3
- Principle violations identified at Gate 3 block production deployment until resolved or a formal exception is approved
- Retrospective conformance reviews conducted annually for all live systems
- Approved exceptions reviewed quarterly — expired exceptions with no remediation are escalated to the IT Director

---

## VIII. Appendix

### A: Principle Summary Checklist

| ID | Principle | Category | Criticality | Key Validation |
|----|-----------|----------|-------------|----------------|
| P-01 | Design for Horizontal Scale | Strategic | HIGH | Load test confirms linear scaling |
| P-02 | Resilience and Graceful Degradation | Strategic | CRITICAL | Circuit breakers, RTO/RPO tested |
| P-03 | Security by Design | Strategic | CRITICAL (Non-Negotiable) | Threat model, pen test, secrets management |
| P-04 | Interoperability Through Standard Interfaces | Strategic | HIGH | API catalogue, versioning strategy |
| P-05 | Observability as a First-Class Requirement | Strategic | HIGH | Logs, metrics, traces, runbooks |
| P-06 | Customer Data as a Strategic Asset | Data | HIGH | System of record, data dictionary |
| P-07 | Privacy by Design and UK GDPR Compliance | Data | CRITICAL | DPIA, consent management, SAR automation |
| P-08 | Data Quality and Lineage | Data | HIGH | Quality rules automated, lineage documented |
| P-09 | Single Source of Truth | Data | HIGH | System of record designated per entity |
| P-10 | Loose Coupling | Integration | HIGH | No shared databases, independent deployment |
| P-11 | Asynchronous Communication | Integration | MEDIUM | Async for business process flows |
| P-12 | Performance Requirements Defined | Quality | HIGH | Targets defined, load tested |
| P-13 | Availability and Recoverability | Quality | CRITICAL | SLA defined, DR tested annually |
| P-14 | Maintainability and Architectural Fitness | Quality | MEDIUM | ADRs, test coverage, debt register |
| P-15 | Infrastructure as Code | Delivery | HIGH | 100% IaC, no manual changes |
| P-16 | Automated Testing | Delivery | HIGH | Pipeline gates, test pyramid |
| P-17 | Continuous Integration and Deployment | Delivery | HIGH | CI/CD only route to production |

### B: Applicability Matrix

| Principle | CRM System (001) | Future Projects |
|-----------|-----------------|-----------------|
| P-01 Horizontal Scale | Required | Required |
| P-02 Resilience | Required | Required |
| P-03 Security | Required (Non-Negotiable) | Required (Non-Negotiable) |
| P-04 Standard Interfaces | Required | Required |
| P-05 Observability | Required | Required |
| P-06 Customer Data | Required (primary concern) | Where applicable |
| P-07 Privacy / GDPR | Required (personal data) | Where applicable |
| P-08 Data Quality | Required | Required |
| P-09 Single Source of Truth | Required | Required |
| P-10 Loose Coupling | Required | Required |
| P-11 Async Communication | Required | Required |
| P-12 Performance | Required | Required |
| P-13 Availability | Enhanced tier minimum | Tier based on criticality |
| P-14 Maintainability | Required | Required |
| P-15 IaC | Required | Required |
| P-16 Automated Testing | Required | Required |
| P-17 CI/CD | Required | Required |

### C: References

- UK General Data Protection Regulation (UK GDPR) and Data Protection Act 2018
- ICO Accountability Framework
- NCSC Cyber Essentials and Secure by Design guidance
- NCSC 10 Steps to Cyber Security
- ISO/IEC 27001:2022 Information Security Management
- TOGAF 10 Architecture Framework
- CRM System Stakeholder Drivers Analysis (ARC-001-STKE-v1.0)

---

## External References

| Document | Type | Source | Key Extractions | Path |
|----------|------|--------|-----------------|------|
| *None provided* | — | — | — | — |

---

**Generated by**: ArcKit `/arckit:principles` command
**Generated on**: 2026-03-01
**ArcKit Version**: 2.22.3
**Project**: Global / Cross-Project (Project 000)
**AI Model**: claude-sonnet-4-6
