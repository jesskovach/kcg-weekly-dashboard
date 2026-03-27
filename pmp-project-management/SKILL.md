---
name: pmp-project-management
description: |
  Run a project through PMI's PMBOK framework to understand real-world application of all 10 knowledge areas. Use this whenever you're planning or managing a project (client work, internal tools, business initiatives, consulting engagements), creating a project charter, defining scope, building schedules, managing resources, handling risks, or documenting stakeholder communications. This skill integrates PMP learning directly into your work by mapping every project decision to PMBOK knowledge areas (Integration, Scope, Schedule, Cost, Quality, Resource, Communications, Risk, Procurement, Stakeholder Management). Perfect for building consulting credibility while studying for your exam—every project becomes a case study in PMI best practices.
argument-hint: "[plan | status | risk-register | charter | closure]"
---

# /pmp-project-management

Use this skill to apply the PMBOK framework to your real projects. Every decision you make becomes a learning checkpoint for your PMP exam prep.

## The 10 PMBOK Knowledge Areas

Understanding where your project decisions live in the framework:

1. **Integration** — Project charter, overall planning, monitoring & controlling, project closure
2. **Scope** — What's in/out, requirements gathering, scope validation, change control
3. **Schedule** — Timeline, dependencies, critical path, resource leveling
4. **Cost** — Budget, estimates, tracking, earned value
5. **Quality** — Standards, defect prevention, testing strategy
6. **Resource** — Team structure, skills, acquisition, development
7. **Communications** — Stakeholder engagement, reporting, status updates, decision logs
8. **Risk** — Identification, analysis, response planning, monitoring
9. **Procurement** — Vendor selection, contracts, supplier management
10. **Stakeholder** — Identification, engagement, expectations, conflict resolution

## How to Use This Skill

### Option 1: Project Charter (Planning Phase)
Ask me to create a project charter that documents:
- Business case and justification
- High-level scope and objectives
- Key stakeholders and their roles
- Constraints (timeline, budget, resources)
- Initial risks
- Success criteria
- Authority and governance structure

**Trigger phrase**: "Create a project charter for [project]"

**What you'll get**:
- Executive summary aligned with business goals
- Clear scope boundaries (in/out)
- Stakeholder analysis and communication plan
- Risk register (initial)
- Assumptions and constraints
- Sign-off documentation

**PMP Learning**: Integrates scope, stakeholder, communications, and risk knowledge areas

---

### Option 2: Project Plan (Planning Phase)
Ask me to build a comprehensive project plan covering:
- Scope statement (detailed requirements)
- Work breakdown structure (WBS)
- Schedule (timeline, milestones, critical path)
- Resource plan (team, skills, acquisition)
- Cost estimate and budget
- Quality criteria
- Risk register and response plan
- Communications schedule
- Procurement needs (if applicable)
- Stakeholder engagement plan

**Trigger phrase**: "Build a project plan for [project]"

**What you'll get**:
- Complete project planning artifact
- Risk-aware timeline with buffers
- Resource capacity analysis
- Quality gates and acceptance criteria
- Communication cadence aligned to stakeholder needs
- Change control process defined
- PMBOK knowledge area callouts showing how each decision maps to the framework

**PMP Learning**: Applies all 10 knowledge areas in an integrated way

---

### Option 3: Project Status (Execution & Monitoring Phase)
Ask me to assess project health using PMI practices:
- Performance against schedule (EV, SV, SPI)
- Performance against budget (EV, CV, CPI)
- Quality metrics (defect rate, rework, acceptance)
- Risk status (realized risks, emerging risks, mitigation progress)
- Stakeholder sentiment and engagement
- Resource utilization and team health
- Scope creep analysis
- Upcoming milestones and blockers

**Trigger phrase**: "Give me a project status for [project]" or "Assess [project] health"

**What you'll get**:
- Executive summary of health (RAG status)
- Earned value analysis with trend
- Risk update with new mitigations
- Stakeholder engagement assessment
- Corrective action recommendations
- Change requests in flight
- Callouts on decisions made and lessons learned

**PMP Learning**: Demonstrates monitoring & controlling phase and earned value management

---

### Option 4: Risk Register & Response Plan
Ask me to identify and structure risks:
- Risk identification (brainstorm threats and opportunities)
- Qualitative risk analysis (probability, impact, score)
- Quantitative analysis (if data available)
- Risk response strategies (avoid, mitigate, transfer, accept)
- Risk owner assignment
- Contingency and fallback plans
- Risk monitoring triggers

**Trigger phrase**: "Create a risk register for [project]" or "Analyze risks in [project]"

**What you'll get**:
- Comprehensive risk register (high priority first)
- Risk-scored impact matrix
- Response plans for top risks
- Contingency budget estimate (if cost relevant)
- Schedule contingency (buffers for schedule risks)
- Risk triggers and monitoring approach
- Escalation paths

**PMP Learning**: Deep dive into risk knowledge area; differentiates project managers from task managers

---

### Option 5: Project Closure (Closing Phase)
Ask me to document project close-out:
- Final deliverable acceptance
- Budget finalization (actual vs. planned)
- Schedule performance (actual vs. planned)
- Quality assessment (defects, rework, customer satisfaction)
- Lessons learned (what went well, what could improve)
- Team retrospective and feedback
- Document archival and handoff
- Post-implementation review plan

**Trigger phrase**: "Close out [project]" or "Prepare project closure for [project]"

**What you'll get**:
- Project closure checklist
- Lessons learned document
- Financial closeout summary
- Quality assessment
- Stakeholder sign-off template
- Archive structure and asset location
- Recommendations for future similar projects
- Team feedback collection approach

**PMP Learning**: Closing phase shows project lifecycle completion and organizational learning capture

---

## Mapping Your Decisions to PMBOK

Every time you use this skill, decisions are mapped to knowledge areas. This teaches you to think like a project manager:

**Example: You're deciding how to handle a scope change request**

```
Decision: Client asks for 3 new features mid-project

Knowledge Area: SCOPE MANAGEMENT
- Impact: 2 weeks timeline, $8K budget
- Process: Perform integrated change control
- Approval: Stakeholder approval required (Communications)
- Risk: Quality impact if schedule compressed (Quality)
- Resource: Need additional developer (Resource)
- Communication: Update all stakeholders (Communications)
- Documentation: Add to scope baseline change log (Integration)

Action: Submit change request for formal approval with impact analysis
PMP Learning: Shows how scope, risk, cost, schedule, resource, quality,
communications, and stakeholder management all interconnect
```

---

## How This Builds Your Consulting Practice

Every project you run through this framework:

1. **Deepens PMP knowledge** — You're not just reading about scope management, you're *doing* it
2. **Generates case studies** — You can tell potential clients: "I managed a $2M healthcare platform launch using full PMBOK framework"
3. **Builds confidence** — You'll pass the PMP exam from doing, not cramming
4. **Demonstrates value** — Clients see disciplined, predictable projects instead of chaos
5. **Creates repeatable processes** — You build templates and best practices for your consulting business

---

## Example Workflows

### Scenario 1: Consulting Engagement (You as PM)
```
Client Context: Mid-market nonprofit launching new donor management system
Your Role: Architect + Project Manager + Quality Lead

Week 1 (Planning):
  /pmp-project-management plan
  → Creates charter + full project plan
  → Maps all 10 knowledge areas
  → Identifies stakeholders (donor team, IT, finance, board)
  → Risk register: Change management risk high, data migration risk high
  → Budget and timeline documented
  → Governance structure defined

Week 2-8 (Execution):
  /pmp-project-management status
  → Weekly health checks using earned value
  → Risk monitoring (are the big risks appearing?)
  → Stakeholder updates (tailored by audience)
  → Change request tracking
  → Quality gate checkpoints

Week 9 (Closure):
  /pmp-project-management closure
  → Lessons learned: What would you do differently?
  → Financial closeout: Budget performance
  → Client satisfaction assessment
  → Team feedback
  → Post-launch plan (support, optimization)

PMP Exam Benefit:
  You just lived through a complete project lifecycle using the PMBOK.
  Interview question: "Tell me about a risk you identified and mitigated"
  → Real answer from real project > textbook answer
```

### Scenario 2: Internal Tool Build (Learning Focus)
```
You're building a feature for your own platform

Charter:
  /pmp-project-management charter
  → Justification (how does this serve your customers?)
  → Success criteria (what's the metric?)
  → Resource plan (you, maybe contractors)
  → Timeline estimate with buffer
  → Risk list (what could go wrong?)

Plan:
  /pmp-project-management plan
  → Detailed scope (acceptance criteria per feature)
  → Schedule with dependencies
  → Quality criteria (test coverage, accessibility)
  → Risk response (mitigation for top risks)

Status:
  /pmp-project-management status
  → Am I on schedule/budget?
  → Quality gates passing?
  → Are risks materializing?
  → What's blocking forward progress?

Closure:
  /pmp-project-management closure
  → Did I deliver what I planned?
  → What did I learn?
  → What would I do differently next time?

PMP Exam Benefit:
  You understand the tension between perfect planning and fast iteration.
  You can speak to risk-based scheduling and why buffers matter.
  You've lived through earned value (even if it's just your own hours).
```

---

## Integration with Your Other Tools

This skill works alongside:

- **Standup Skill** — Status includes today's blockers, schedule risk, resource gaps
- **Design System** — Quality knowledge area includes design consistency and accessibility
- **Accessibility Review** — Quality knowledge area enforces WCAG compliance as project requirement
- **Code Review** — Quality gate in project plan reviews PRs against acceptance criteria
- **Exam Prep Tracker** — Each project decision creates spaced repetition study material

---

## What You'll Learn (Mapped to PMP Exam Domains)

Every project teaches you:

| Knowledge Area | What You'll Master | Real-World Skill |
|---|---|---|
| Integration | Unified planning & change control | Seeing how decisions ripple across projects |
| Scope | Boundary definition & requirements | Saying "no" with data; preventing scope creep |
| Schedule | Timeline, dependencies, critical path | Realistic estimates; identifying bottlenecks |
| Cost | Budgeting, earned value, ROI | Pricing your services accurately; cost/benefit analysis |
| Quality | Standards, testing, acceptance | Shipping with confidence; client satisfaction |
| Resource | Team structure, skills, capacity | Building teams; developing people; identifying skills gaps |
| Communications | Stakeholder engagement, reporting | Keeping clients/teams informed; avoiding surprises |
| Risk | Identification, analysis, response | Proactive problem-solving instead of reactive firefighting |
| Procurement | Vendor management, contracts | Getting best value from contractors/vendors |
| Stakeholder | Engagement, expectations, conflict | Aligning diverse interests; building trust |

---

## Quick Reference: Command Options

| Command | Use Case | PMP Phase |
|---------|----------|-----------|
| `/pmp-project-management charter` | Start a new project | Initiating |
| `/pmp-project-management plan` | Build comprehensive project plan | Planning |
| `/pmp-project-management status` | Check project health | Executing & Monitoring |
| `/pmp-project-management risk-register` | Deep dive on risks | Planning & Monitoring |
| `/pmp-project-management closure` | Wrap up project formally | Closing |

---

## Tips for Maximum Learning Value

1. **Do the planning upfront** — It feels slow but catches issues early
2. **Run status meetings with this framework** — Your stakeholders will notice the discipline
3. **Document risks explicitly** — Don't just feel anxious, write it down and plan response
4. **Capture lessons learned** — Every project teaches something; write it down
5. **Show your work** — When you close out, explain the PMI thinking behind decisions
6. **Use this for client proposals** — "Here's how I'll manage your project (PMBOK framework)" builds confidence

---

## Example Output: Project Charter

When you ask for a charter, you get something like:

```
PROJECT CHARTER: E-commerce Platform Rebuild
Client: [Company Name]
Project Manager: Jess Kovach
Approval Date: [Date]

BUSINESS CASE
Current platform: 15-year-old legacy code, 40% downtime, losing customers
Opportunity: Rebuild on modern stack, target 99.9% uptime, grow revenue 30%
Investment: $250K, 6 months
ROI: Break-even in 18 months, $500K annual savings thereafter

PROJECT OBJECTIVES
1. Zero-downtime migration of 50K SKUs
2. Mobile-first responsive design (WCAG AA)
3. Integrate with 3 payment processors
4. Support 10K concurrent users

HIGH-LEVEL SCOPE
In Scope:
- Product catalog rebuild
- Shopping cart and checkout
- Order fulfillment integration
- Customer account management

Out of Scope:
- Loyalty program (Phase 2)
- Marketplace features (Phase 2)
- Analytics/BI (Phase 2)

STAKEHOLDERS
[Table: name, role, interests, engagement level, communication frequency]

CONSTRAINTS
- Timeline: 6 months (Q2-Q3)
- Budget: $250K
- Team: You + 2 developers + 1 QA
- Platform: React frontend, Node.js backend, PostgreSQL

RISKS (High-Level)
1. Data migration complexity (High)
2. Third-party API integration (Medium)
3. Performance under load (High)
4. Team skill gaps on React (Medium)

SUCCESS CRITERIA
- Go-live on schedule and budget
- Zero data loss during migration
- All acceptance tests passing
- Customer satisfaction > 4.5/5
- Team retro shows learning captured

APPROVAL
[Sign-off by sponsor, client, you]
```

---

## Next Steps

Start with whichever phase your current projects are in:

- **Planning a new project?** → `charter` then `plan`
- **Running a project now?** → `status` (weekly check-in)
- **Project ending?** → `closure` (capture learning)
- **Worried about risks?** → `risk-register` (proactive)

Each time you use this skill, you're 1% closer to PMP mastery and 1% more valuable to your clients.
