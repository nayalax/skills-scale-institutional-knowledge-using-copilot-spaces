# OctoAcme — Dependency & Risk Management

## Purpose
Provide systematic processes for identifying, tracking, and resolving cross-team dependencies and risks to prevent delays and escalations.

## Dependency Identification & Tracking

### Types of Dependencies
1. **Internal** – Between teams within OctoAcme
2. **External** – Third-party APIs, infrastructure, vendor deliverables
3. **Sequential** – Task B cannot start until Task A completes
4. **Parallel** – Tasks run concurrently but require coordination
5. **Technical** – One component depends on another component's completion

### Dependency Checklist (Planning Phase)

- [ ] All external dependencies identified and documented
- [ ] Dependent team owners notified and aligned
- [ ] Integration points and APIs defined
- [ ] Data contracts or interface specs documented
- [ ] Timeline impact assessed (critical path analysis)
- [ ] Backup plan / mitigation defined for each critical dependency
- [ ] Escalation path defined if dependency slips

### Dependency Tracking Template

| ID | Dependency | Owner | Dependent Team | Target Completion | Status | Risk Level | Notes |
|---|---|---|---|---|---|---|---|
| D-1 | Auth service API finalized | Platform Team | Feature Team A | 2026-06-15 | In Progress | Medium | Design finalized; implementation in progress |
| D-2 | Data warehouse schema ready | Data Team | Analytics Feature | 2026-06-20 | On Track | Low | Schema doc approved |
| D-3 | Third-party SDK license | Legal/Procurement | Mobile Team | 2026-06-10 | At Risk | High | Awaiting legal review—escalated |

### Weekly Dependency Sync

- **Who**: Project Managers + dependent team leads
- **When**: Weekly (e.g., Tuesday 2pm)
- **Duration**: 30 minutes
- **Agenda**:
  1. Review high-risk dependencies (Red status)
  2. Confirm on-track dependencies still on schedule
  3. Identify new dependencies or blockers
  4. Escalate if slip expected > 3 days
  5. Document decisions and next steps in project board

---

## Risk Management

### Risk Categories

1. **Technical Risk** – Feasibility, performance, architecture concerns
2. **Resource Risk** – Staffing, availability, skill gaps
3. **Schedule Risk** – Timeline pressure, dependent delays
4. **Market/Business Risk** – Customer feedback, competitive threats
5. **Quality Risk** – Testing gaps, insufficient QA time
6. **External Risk** – Vendor delays, third-party issues, compliance changes

### Risk Register Template

| ID | Title | Description | Category | Impact | Likelihood | Owner | Mitigation | Status | Last Updated |
|---|---|---|---|---|---|---|---|---|---|
| R-1 | API rate limits impact performance | Third-party API enforces strict rate limits under load testing | Technical | High | Medium | Tech Lead | Implement caching layer; stress test with limits | Active | 2026-06-08 |
| R-2 | Key developer on leave during critical phase | Senior dev unavailable for 2 weeks mid-project | Resource | High | Medium | Project Manager | Cross-train backup dev; front-load critical work | Active | 2026-06-08 |
| R-3 | Unclear acceptance criteria for complex feature | Feature scope ambiguous; risk of rework | Quality | Medium | High | Product Manager | Design workshop + detailed AC doc; dev review | Active | 2026-06-08 |

### Risk Assessment Scoring

- **Impact**: Low (1) – Manageable within scope; Medium (2) – Requires workaround; High (3) – Blocks milestone
- **Likelihood**: Low (1) – < 25%; Medium (2) – 25-75%; High (3) – > 75%
- **Risk Score** = Impact × Likelihood (scores 1-9)
  - **1-2**: Monitor, no action needed
  - **3-4**: Mitigation plan recommended
  - **6-9**: Immediate mitigation required; escalate if not addressed

### Risk Identification Triggers

- **Planning**: Technical spikes, new technology, tight timeline, unclear requirements
- **Execution**: Velocity slowdown, bug discovery, scope creep, team changes
- **Testing**: High defect density, late bug discovery, test environment issues
- **Release**: Production concerns, rollback complexity, communication gaps

### Risk Mitigation Strategies

| Strategy | Example |
|---|---|
| **Reduce Likelihood** | Conduct technical spike; hire contractor; simplify scope |
| **Reduce Impact** | Build in buffer time; add backup resources; plan rollback |
| **Accept** | Acknowledge risk; document trade-off decision; monitor closely |
| **Avoid** | Remove requirement; defer to next release; use proven tech |
| **Contingency** | Plan B if primary approach fails; have backup vendor |

### Weekly Risk Review (Part of PM Sync)

- [ ] Review high-risk items (score 6+)
- [ ] Update mitigation status
- [ ] Identify new risks
- [ ] Escalate if mitigation plan is insufficient
- [ ] Close resolved risks with lessons learned

---

## Escalation Path

### Level 1: Team Triage (Daily Standups)
- **Trigger**: Blocker, dependency slip < 24 hours, question about requirements
- **Resolution**: Developer + PM sync, quick decision, document in Slack/issue
- **Escalate if**: Unresolved after 4 hours

### Level 2: Project Manager Escalation (Within 24 Hours)
- **Trigger**: Dependency slip likely, resource conflict, major scope question
- **Resolution**: PM coordinates cross-team sync, documents decision, notifies stakeholders
- **Escalate if**: Impacts milestone or requires leadership decision

### Level 3: Product Lead / Sponsor Escalation (Within 48 Hours)
- **Trigger**: Milestone at risk, significant scope change, resource unavailable
- **Resolution**: Leadership decides on trade-offs (timeline, scope, quality), communicates to sponsors
- **Escalate if**: Threatens project viability or customer commitment

### Escalation Template

| Field | Content |
|---|---|
| **Issue** | Clear, one-sentence summary |
| **Context** | Background, why it matters |
| **Options** | 2-3 paths forward with trade-offs |
| **Recommendation** | PM's suggested path |
| **Requested Decision** | What needs approval |
| **Timeline** | When decision is needed |

---

## Cross-Team Collaboration Checklist

### Before Kickoff
- [ ] All dependent teams identified
- [ ] Kickoff meeting scheduled with team leads
- [ ] Dependencies clearly mapped
- [ ] Success criteria and integration points documented

### During Planning
- [ ] Acceptance criteria include integration requirements
- [ ] Test scenarios cover cross-team interactions
- [ ] APIs / data contracts finalized and documented
- [ ] Each team's delivery timeline confirmed
- [ ] Backup plans defined for critical paths

### During Execution
- [ ] Weekly cross-team sync (even if brief)
- [ ] Integration testing scheduled early (not last minute)
- [ ] Any blockers escalated within 24 hours
- [ ] Documentation shared across teams

### Before Release
- [ ] All dependent features complete and tested
- [ ] End-to-end smoke tests pass
- [ ] Release communication includes all teams
- [ ] Rollback plan accounts for all components

### Post-Release
- [ ] Confirm all integrations working in production
- [ ] Collect feedback from dependent teams
- [ ] Document lessons learned (what went well, what to improve)
- [ ] Update process docs if patterns emerge

---

## Decision Log

Keep a simple decision log to provide transparency and reduce repeated questions:

| Date | Decision | Context | Owner | Rationale | Status |
|---|---|---|---|---|---|
| 2026-06-05 | Defer API enhancement to v2 | Scope pressure on v1 delivery | Product Manager | Focus v1 on core feature; simplify integration | Closed |
| 2026-06-08 | Hire contract developer for QA support | Resource constraint during critical testing phase | Project Manager | Accelerate test execution; reduce regression risk | In Progress |

---

## Resources & References
- Project board: `https://github.com/nayalax/skills-scale-institutional-knowledge-using-copilot-spaces/projects`
- Risk register: Maintained in project board or shared doc
- Escalation contacts: See RACI matrix in Role Interaction Matrix doc