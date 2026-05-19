# CSIT302 Cybersecurity — Day 5-3: Recovery Process

---

## Disaster Recovery Plan (DRP)

### Definition
A documented set of processes and procedures carried out to recover the IT infrastructure in the event of a disaster. Since disasters cannot be fully avoided, the goal is to plan ahead for recovery.

### Types of Disasters
- **Natural:** Blizzards, wildfires, hurricanes, volcanic eruptions, earthquakes, floods, lightning strikes
- **Man-made:** Fires, cyber warfare, hacking, power surges, accidents

### Objective
Protect the continuity of business operations when IT operations have been partially or fully stopped.

### Benefits
- **Sense of security** — assures continued ability to function during a disaster
- **Reduces recovery delays** — prevents uncoordinated, slow responses
- **Reliable standby systems** — ensures standby systems are always prepared
- **Standard test plan** — provides a benchmark for all business operations
- **Faster decision-making** — minimizes time spent deciding during a crisis
- **Mitigates legal liabilities** — reduces organizational exposure during disasters

---

### DRP Planning Process (8 Steps)

1. **Forming a DR team** — All-inclusive team from all departments + top management; determines scope and oversees development
2. **Performing risk assessment** — Identify natural/man-made risks; evaluate threats to sensitive files/servers; plan for worst-case scenario
3. **Prioritizing processes and operations** — Identify critical needs per department; rank operations as *essential*, *important*, or *nonessential*; determine max time each department can operate without critical systems
4. **Determining recovery strategies** — Cover all aspects: hardware, software, databases, communication channels, customer services, end-user systems; review third-party vendor agreements
5. **Collecting data** — Document inventory forms, policies, communication links, contact details, hardware/software details, backup schedules and storage info
6. **Creating the DRP** — Comprehensive, practical, standard format; step-by-step layout; easy to understand; includes its own review/update procedure
7. **Testing the plan** — Use simulations, checklist tests, full-interruption tests, parallel tests; must be proven practical and effective
8. **Obtaining approval** — Submit to top management; must be consistent with org policies and subject to annual reviews

### Maintaining the Plan
- Must be updated based on **need**, not just a rigid schedule (e.g., WannaCry spread to 150+ countries rapidly)
- Set up an updating schedule that allows for ad hoc updates when needed

### Challenges
- **Lack of management approval** — Top management may not prioritize planning
- **Incomplete RTO** — Difficult to create a cost-effective plan within the Recovery Time Objective
- **Outdated plans** — Hard to keep current; outdated plans may fail against new threat vectors

---

## Recovery Objectives

| Metric | Definition |
|--------|------------|
| **RTO** (Recovery Time Objective) | Maximum acceptable delay between service interruption and restoration |
| **RPO** (Recovery Point Objective) | Maximum acceptable amount of time since the last data recovery point |

### RTO vs. Cost Relationship
Lower RTO (faster recovery) = higher cost and complexity. AWS disaster recovery strategies in ascending cost:

| Strategy | RPO/RTO | Notes |
|----------|---------|-------|
| Backup & Restore | Hours | Lowest cost |
| Pilot Light | 10s of minutes | Data live, services idle |
| Warm Standby | Minutes | Partially running, business critical |
| Multi-Site Active/Active | Real-time | Zero downtime, highest cost |

---

## Live Recovery

### Why It's Needed
Traditional recovery requires taking the system offline — but some systems cannot tolerate downtime (e.g., always-on services, structurally interdependent systems).

### Two Methods

1. **Install a clean system on top of the faulty one**
   - Replaces the faulty system and its files entirely
   - A new, clean system takes over

2. **Use data recovery tools on a live system**
   - Used when valuable data must be preserved in the existing system
   - Tools update configurations and replace faulty files with recent backups
   - Allows recovery without a complete system restore

---

## Contingency Plan

### Definition
A course of action designed to help an organization respond effectively to a significant future event that may or may not happen. Informally called **"Plan B"**.

### Why It's Needed
- Organizations face many risks (natural disasters to human error)
- It is impossible to eliminate all risks

### Sound Contingency Plan Requirements
- Reliable execution plans and updating schedules
- Integration with other business continuity plans
- Defined recovery strategies and RTOs
- Exercise, training, and updating tasks

---

### Five Steps of IT Contingency Planning

#### Step 1: Develop the Contingency Planning Policy
- Define objectives and assign responsibilities
- Include all senior employees
- Policy must cover: scope, resources, training needs, testing/maintenance schedules, backup schedules/locations, roles and responsibilities

#### Step 2: Conduct Business Impact Analysis (BIA)
An analysis that predicts consequences of business function disruption and gathers information to develop recovery strategies.

**Three steps of BIA:**

1. **Identify critical IT resources** — Resources supporting core processes (payroll, transactions, e-commerce); typically servers, networks, and communication channels
2. **Identify disruption impacts** — Determine maximum allowable outage time per resource; balance cost of disruption vs. cost of recovery
3. **Develop recovery priorities** — Prioritize which resources to restore first (usually communication channels and networks, but depends on org type)

#### Step 3: Identify Preventive Controls
- Mitigate BIA-uncovered impacts through measures that detect, deter, or reduce disruption
- Implement only if feasible and cost-effective
- Range from power interruption prevention to fire prevention

#### Step 4: Develop Recovery Strategies

**Backups**
- Intervals should be short enough to capture reasonably recent data
- Policies should cover: storage sites, naming conventions, rotation frequency, transmission methods
- **Cloud backups:**
  - *Advantages:* Lower cost (no hardware), high reliability/availability, scalable storage
  - *Disadvantages:* Privacy and security concerns

**Alternative Sites** (by readiness, ascending order)

| Site Type | Description |
|-----------|-------------|
| Cold site | Supportive resources ready; requires IT equipment and telecom installation |
| Warm site | Partially equipped; requires staffing to become operational |
| Hot site | Adequately equipped and staffed; ready to continue IT operations |
| Mirrored site | Exact replica of the main site |

**Equipment Replacement Options**
- **Vendor agreement** — Vendors notified to supply replacements after a disaster
- **Equipment inventory** — Pre-purchased replacement equipment stored safely in advance
- **Existing compatible equipment** — Borrowing from alternative sites

#### Step 5: Plan Maintenance
- Review at least **annually**; update and document all changes promptly
- Must stay aligned with current risks, org structure, and policies

---

### Plan Testing, Training & Exercising

**Testing focuses on:**
- Speed of recovery from backups and alternative sites
- Collaboration between recovery personnel
- Performance of recovered systems at alternative sites
- Ease of restoring normal operations
- Conducted in worst-case scenario via classroom or functional exercises

**Training:**
- Theoretical training supplements practical exercises
- Conducted at least annually

**Exercising:**
- **Classroom exercises** — Low cost; staff walked through recovery operations in class
- **Functional exercises** — Higher cost; disaster is mimicked and staff respond practically

---

## Best Practices for Disaster Recovery

- **Offsite backup storage** — Use the cloud as a safe, always-available off-site backup location
- **Record IT infrastructure changes** — Keeps the contingency plan aligned with current systems
- **Proactive system monitoring** — Detect disasters early to begin recovery sooner
- **Fault-tolerant systems** — Implement RAID (Redundant Array of Independent Disks) for server redundancy; test backup integrity regularly
- **Regular restore testing** — All IT staff should be fully knowledgeable about the restoration process
