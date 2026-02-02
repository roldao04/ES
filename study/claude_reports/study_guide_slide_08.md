# Software Engineering - Study Guide (Slide 08)
## Monitoring and Observability - Complete Exam Preparation Guide

---

# Table of Contents

1. [Introduction](#introduction)
   - [Why Monitoring and Observability Matter](#why-monitoring-and-observability-matter)
   - [Service Level Agreements (SLA)](#service-level-agreements-sla)
2. [Core Definitions](#core-definitions)
   - [Service Level Indicator (SLI)](#service-level-indicator-sli)
   - [Service Level Objective (SLO)](#service-level-objective-slo)
   - [Service Level Agreement (SLA)](#service-level-agreement-sla)
   - [Other Key Terms](#other-key-terms)
3. [Hierarchy of Reliability Engineering](#hierarchy-of-reliability-engineering)
4. [Monitoring vs Observability](#monitoring-vs-observability)
   - [Key Differences](#key-differences)
   - [Complementary Roles](#complementary-roles)
   - [End-Users' Expectations](#end-users-expectations)
5. [Monitoring](#monitoring)
   - [Monitoring Anti-Patterns](#monitoring-anti-patterns)
   - [Monitoring Best Practice Patterns](#monitoring-best-practice-patterns)
6. [Statistics for Monitoring](#statistics-for-monitoring)
   - [Why Statistics Matter](#why-statistics-matter)
   - [Core Statistical Tools](#core-statistical-tools)
7. [Observability](#observability)
   - [Three Pillars of Observability](#three-pillars-of-observability)
   - [Observability Requirements](#observability-requirements)
   - [Software Telemetry](#software-telemetry)
8. [Distributed Tracing](#distributed-tracing)
   - [Understanding Spans](#understanding-spans)
   - [Trace Visualizations](#trace-visualizations)
   - [Latency Analysis Examples](#latency-analysis-examples)
9. [Observability Tools Ecosystem](#observability-tools-ecosystem)
   - [Metrics Tools](#metrics-tools)
   - [Logging Tools](#logging-tools)
   - [Tracing Tools](#tracing-tools)
   - [Unified Platforms](#unified-platforms)
10. [Practical Implementation](#practical-implementation)
    - [OpenTelemetry Spring Boot Integration](#opentelemetry-spring-boot-integration)
    - [Elastic Observability Solution](#elastic-observability-solution)
11. [Project Requirements](#project-requirements)
12. [Study Tips and Exam Preparation](#study-tips-and-exam-preparation)

---

# Introduction

## Why Monitoring and Observability Matter

### The Business Context

> "What are the main reason to perform that?"

**Modern Software Challenges:**
- Systems are distributed and complex
- Failures are inevitable, not exceptional
- User expectations are higher than ever
- Downtime has direct business impact
- Need to understand system behavior

**The Reality:**
- Can't prevent all failures
- Must detect problems quickly
- Need to diagnose root causes
- Must measure and improve reliability
- Business commitments require proof

---

## Service Level Agreements (SLA)

### Definition

> "**Service Level Agreement** - a contract!"

**Formal Definition:**
> "A formal contract between a service provider and a customer. It usually includes SLOs, and adds consequences (like penalties or compensation) if the objectives are not met."

---

### Key Characteristics

**1. Legal Contract:**
- Binding agreement
- Between provider and customer
- Specifies service expectations
- Includes consequences

**2. Based on SLOs:**
- Contains measurable objectives
- Defines acceptable service levels
- Sets clear thresholds
- Quantifiable targets

**3. Financial Consequences:**
- Penalties for non-compliance
- Service credits
- Compensation mechanisms
- Business risk

---

### Example

> "If availability drops below 99.9% in a given month, the customer receives a service credit."

**Scenario:**
- **SLA Commitment**: 99.9% uptime per month
- **Month Duration**: 30 days = 720 hours
- **Allowed Downtime**: 0.1% × 720 = 43.2 minutes
- **Actual Downtime**: 2 hours (120 minutes)
- **Result**: SLA violated → Customer gets service credit

**Business Impact:**
- Lost revenue from credits
- Reputation damage
- Customer trust erosion
- Potential contract loss

---

### The Importance

> "This highlights the importance of maintaining continuous monitoring and ensuring that the system remains observable."

**Why Critical:**
- **Prove Compliance**: Need data to show SLA met
- **Early Detection**: Catch issues before SLA violation
- **Root Cause Analysis**: Understand why failures happen
- **Prevention**: Improve to avoid future violations
- **Trust**: Transparency with customers

**Connection:**
- SLA requires measurement
- Measurement requires monitoring
- Understanding requires observability
- All three interconnected

---

# Core Definitions

## Service Level Indicator (SLI)

### Definition

> "**Service Level Indicator (SLI)**: A quantitative measure of some aspect of a service's performance or reliability. It should provide the raw data that tells us how the system is behaving."

---

### Key Characteristics

**1. Quantitative Measurement:**
- Numerical values
- Measurable data
- Objective metrics
- Not subjective

**2. Raw Data:**
- Direct measurements
- Not goals or targets
- Factual information
- Baseline for decisions

**3. Not Goals or Contracts:**
> "The SLIs are measurements, not goals or contracts."

**Important Distinction:**
- SLI = What you measure
- SLO = What you target
- SLA = What you promise

---

### Common SLI Examples

**1. Availability:**
> "Availability: % of successful HTTP requests."

**Measurement:**
```
Availability SLI = (Successful Requests / Total Requests) × 100%
```

**Example:**
- Total requests: 10,000
- Successful (200, 201, etc.): 9,950
- Failed (500, 503, etc.): 50
- Availability SLI: 99.5%

---

**2. Latency:**
> "Latency: % of requests served within 300 ms."

**Measurement:**
```
Latency SLI = (Requests < 300ms / Total Requests) × 100%
```

**Example:**
- Total requests: 10,000
- Fast (< 300ms): 9,700
- Slow (≥ 300ms): 300
- Latency SLI: 97%

**Alternative Measurement:**
- p95 latency (95th percentile)
- p99 latency (99th percentile)
- Mean/median latency

---

**3. Error Rate:**
> "Error Rate: % of failed transactions."

**Measurement:**
```
Error Rate SLI = (Failed Transactions / Total Transactions) × 100%
```

**Example:**
- Total login attempts: 10,000
- Successful logins: 9,990
- Failed logins: 10
- Error Rate SLI: 0.1%

---

### Types of SLIs

**Request/Response SLIs:**
- Availability (success rate)
- Latency (response time)
- Throughput (requests per second)

**Data Processing SLIs:**
- Freshness (data age)
- Correctness (error rate)
- Coverage (% of data processed)

**Storage SLIs:**
- Durability (data loss rate)
- Throughput (read/write ops)
- Latency (access time)

---

## Service Level Objective (SLO)

### Definition

> "**Service Level Objective (SLO)**: A target or threshold for a Service Level Indicator (SLI). The purpose is to translate raw metrics into reliability goals that guide engineering decisions."

---

### Key Characteristics

**1. Target or Threshold:**
- Specific goal
- Based on SLI
- Sets expectations
- Measurable target

**2. Reliability Goals:**
> "The purpose is to translate raw metrics into reliability goals that guide engineering decisions."

**Translation:**
- Raw metric (SLI) → Goal (SLO)
- Example: "99.5% availability" (SLI) → "Must be ≥ 99.9%" (SLO)

**3. Internal Commitments:**
> "SLOs are commitments teams set internally to balance reliability with innovation speed."

**Key Insight:**
- Set by engineering teams
- Internal, not external contracts
- Balance reliability vs velocity
- Guide decisions

---

### SLO Examples

**1. Availability:**
> "Availability: 99.9% of requests succeed over 30 days."

**Breakdown:**
- **SLI**: % of successful requests
- **SLO**: ≥ 99.9%
- **Time Window**: 30 days
- **Measurement**: Rolling or calendar month

---

**2. Latency:**
> "Latency: 95% of requests served within 300 ms."

**Breakdown:**
- **SLI**: Request response time
- **SLO**: p95 < 300ms
- **Meaning**: 95% of requests fast
- **Alternative**: p99 < 500ms (99% of requests)

---

**3. Error Rate:**
> "Error Rate: <0.1% failed logins per week."

**Breakdown:**
- **SLI**: % of failed logins
- **SLO**: < 0.1%
- **Time Window**: Weekly
- **Calculation**: (Failed / Total) < 0.001

---

### The Relationship

> "**Relation:**
> - SLI = Metric
> - SLO = Target for the metric
> - SLA = Contract based on the target"

**Visual Relationship:**
```
SLI (Measurement)
    ↓
SLO (Internal Goal)
    ↓
SLA (External Contract)
```

**Example Flow:**
1. **SLI**: Measure availability = 99.95%
2. **SLO**: Target availability ≥ 99.9%
3. **SLA**: Promise to customer ≥ 99.5% (with buffer)

**Why Buffer:**
- SLA < SLO gives safety margin
- Allows catching issues before violation
- Prevents constant emergency mode
- Engineering has breathing room

---

## Service Level Agreement (SLA)

### Definition (Recap)

> "A formal contract between a service provider and a customer."

**Already covered in Introduction**, but key points:

---

### Relationship to SLO

**SLA is based on SLO:**
- SLO is internal target
- SLA is external promise
- SLA typically less strict than SLO
- Buffer prevents violations

**Example:**
- **SLO**: 99.95% (internal)
- **SLA**: 99.9% (customer contract)
- **Buffer**: 0.05% safety margin

**Why:**
- Catch issues before SLA breach
- Time to react and fix
- Avoid penalties
- Maintain trust

---

## Other Key Terms

### Error Budgets

> "**Error budgets**: A measurement of the allowable amount of downtime or outage of some component within the system."

**Definition:**
The amount of unreliability you can tolerate.

**Calculation:**
```
Error Budget = 100% - SLO
```

**Example:**
- SLO: 99.9% uptime
- Error Budget: 0.1% downtime
- Per month (30 days): 0.1% × 720 hours = 43.2 minutes

**Purpose:**
- Balance reliability and velocity
- Allows taking risks
- Innovation budget
- Quantifies trade-offs

**Usage:**
- Budget remaining → Deploy new features
- Budget exhausted → Focus on reliability
- Data-driven decisions
- No more gut feelings

---

### Fault Tolerance

> "**Fault tolerance**: The ability of a system to operate without failure when a single or multiple components fail."

**Key Concepts:**
- System continues working despite failures
- Graceful degradation
- No single point of failure
- Redundancy required

**Examples:**
- One server crashes → Others take over
- Database replica fails → Primary still works
- Network partition → System degrades but runs

**Techniques:**
- Redundancy
- Failover mechanisms
- Load balancing
- Circuit breakers
- Retry logic

---

### Redundancy

> "**Redundancy**: The duplication of systems or components as a backup mechanism."

**Purpose:**
- Eliminate single points of failure
- Enable fault tolerance
- Improve availability
- Allow maintenance without downtime

**Types:**
- **Active-Active**: All replicas serve traffic
- **Active-Passive**: Backup ready but idle
- **N+1**: One extra beyond minimum
- **N+2**: Two extra for higher availability

**Trade-offs:**
- **Pro**: Higher reliability
- **Con**: Higher cost (2x, 3x resources)
- **Pro**: Better performance (load distribution)
- **Con**: More complexity

---

### Failure Analysis

> "**Failure analysis**: The process of collecting and analyzing data to determine the cause of a failure."

**Process:**
1. Detect failure
2. Collect data (logs, metrics, traces)
3. Analyze root cause
4. Document findings
5. Implement fixes
6. Prevent recurrence

**Techniques:**
- Root Cause Analysis (RCA)
- 5 Whys
- Fishbone diagrams
- Postmortems (blameless)

---

### Incident Response

> "**Incident response**: The set of processes in place for responding to and managing incidents."

**Phases:**
1. **Detection**: Alert triggered
2. **Triage**: Assess severity
3. **Response**: Fix the issue
4. **Recovery**: Restore service
5. **Postmortem**: Learn and improve

**Best Practices:**
- Clear escalation paths
- Runbooks and playbooks
- On-call rotations
- Blameless culture
- Document everything

---

### Capacity Planning

> "**Capacity planning**: The set practices in place to help determine the current and future demand(s)."

**Purpose:**
- Ensure sufficient resources
- Plan for growth
- Avoid over-provisioning (waste)
- Avoid under-provisioning (outages)

**Process:**
1. Measure current usage
2. Analyze trends
3. Forecast future demand
4. Plan resource additions
5. Monitor and adjust

**Considerations:**
- Seasonal variations
- Business growth
- New features impact
- Marketing campaigns

---

### Monitoring

> "**Monitoring**: The set of processes and tooling used to monitor, and later alert, events within the system."

**We'll cover this extensively in the Monitoring section.**

---

# Hierarchy of Reliability Engineering

## The Stack

**Visual Description:** The slides show a hierarchy/stack diagram illustrating how concepts build on each other.

**From Bottom to Top:**

### 1. Foundation: Monitoring
- Bottom layer
- Collects data
- Provides visibility
- Enables everything above

### 2. SLIs (Service Level Indicators)
- Built on monitoring data
- Quantitative measurements
- Raw metrics
- Foundation for goals

### 3. SLOs (Service Level Objectives)
- Built on SLIs
- Set targets
- Guide decisions
- Internal commitments

### 4. SLAs (Service Level Agreements)
- Top of stack
- Based on SLOs
- External promises
- Business contracts

### 5. Supporting Elements

**Error Budgets:**
- Derived from SLOs
- Quantify allowable failures
- Balance velocity and reliability

**Observability:**
- Complements monitoring
- Enables understanding
- Supports debugging
- Root cause analysis

---

## The Flow

```
Monitoring (collect data)
    ↓
SLIs (measure metrics)
    ↓
SLOs (set targets)
    ↓
Error Budgets (calculate allowance)
    ↓
SLAs (promise customers)
    ↓
Incident Response (when violated)
    ↓
Failure Analysis (learn and improve)
    ↓
Capacity Planning (prevent future issues)
```

**Key Insight:**
Everything starts with monitoring and observability. Without visibility, you cannot measure, target, or promise anything.

---

# Monitoring vs Observability

## Key Differences

### Observability Definition

> "**Observability**: Ability to understand and diagnose system behaviors through telemetry (logs, metrics, traces). Provides visibility, traceability, and insights into latency, errors, and performance."

**What It Provides:**
- **Visibility**: See what's happening
- **Traceability**: Follow request paths
- **Insights**: Understand behavior
- **Context**: Latency, errors, performance

**Key Characteristic:**
Answers the question "**WHY?**"

---

### Monitoring Definition

> "**Monitoring**: Systematic collection and analysis of observability data to track SLIs, detect anomalies, identify trends, and trigger proactive responses."

**What It Provides:**
- **Collection**: Gather telemetry
- **Analysis**: Process data
- **Tracking**: Measure SLIs
- **Alerting**: Notify on issues
- **Trending**: Identify patterns

**Key Characteristic:**
Answers the question "**WHAT?**" and "**WHEN?**"

---

## Complementary Roles

> "**Complementary roles**: Observability explains why something happens, while monitoring alerts when it happens."

**The Relationship:**

**Monitoring:**
- Tells you WHAT is broken
- Tells you WHEN it broke
- Triggers alerts
- Tracks known issues

**Observability:**
- Tells you WHY it broke
- Enables debugging
- Supports exploration
- Handles unknown unknowns

---

### Example Scenario

**Incident: API Latency Spike**

**Monitoring Says:**
- Alert triggered: "API p99 latency > 1000ms"
- When: 14:23 UTC
- What: Latency SLO violated
- Which service: Payment API

**Observability Provides:**
- Distributed trace shows database query slow
- Log shows specific query taking 5 seconds
- Metric shows database connection pool exhausted
- Why: Database migration running, consuming connections

**Together:**
- Monitoring: Detected the problem
- Observability: Diagnosed the cause
- Result: Fix identified (pause migration or scale pool)

---

## Impact

> "**Impact**: Together, they provide visibility across system components, strengthen incident management, improve development quality, and enhance reliability."

**Combined Benefits:**

**1. Visibility Across Components:**
- End-to-end view
- Understand dependencies
- See the big picture

**2. Strengthen Incident Management:**
- Faster detection (monitoring)
- Faster diagnosis (observability)
- Faster resolution
- Better postmortems

**3. Improve Development Quality:**
- Understand performance impact
- Catch issues in development
- Data-driven optimization

**4. Enhance Reliability:**
- Measure SLIs
- Meet SLOs
- Prevent SLA violations
- Continuous improvement

---

## Connection to SLIs/SLOs

> "**Connection to SLIs/SLOs**: Essential for setting measurable objectives, aligning technical metrics with business goals, and ensuring customer-centric reliability."

**How They Connect:**

**1. Setting Objectives:**
- Observability shows what matters to users
- Monitoring measures those things
- SLIs quantify measurements
- SLOs set targets

**2. Aligning Metrics with Business:**
- User-centric metrics (not just CPU%)
- Business impact focus
- Customer experience driven
- Revenue protection

**3. Customer-Centric Reliability:**
- Measure what users experience
- Not just internal health
- End-to-end perspective
- User journey focused

---

## End-Users' Expectations

### The Three Pillars of User Experience

> "**Availability**: Is the system online?"

**User Perspective:**
- Can I access the application?
- Is the website loading?
- Are features working?
- Can I complete my task?

**Measurement:**
- HTTP 200 vs 500 codes
- Uptime percentage
- Request success rate

**SLI Example:**
```
Availability = (Successful Requests / Total Requests) × 100%
```

---

> "**Latency**: Does it take too long to access and use the application?"

**User Perspective:**
- Is it fast enough?
- Am I waiting too long?
- Is the experience smooth?
- Am I getting frustrated?

**Measurement:**
- Response time
- Time to first byte
- Page load time
- API latency

**SLI Example:**
```
Latency SLI = % of requests under 300ms
```

**Key Insight:**
Users won't wait. Studies show:
- 100ms delay → 1% conversion drop
- 1 second delay → 7% conversion drop
- 3+ seconds → 40% abandon

---

> "**Reliability**: Can the user rely on this application?"

**User Perspective:**
- Does it work consistently?
- Will my data be safe?
- Can I trust this service?
- Will it work when I need it?

**Measurement:**
- Error rate
- Data durability
- Consistency
- Predictability

**SLI Example:**
```
Reliability = 1 - Error Rate
```

**User Trust Factors:**
- Consistent behavior
- Rare errors
- Data never lost
- Predictable performance

---

### Why These Three?

**User-Centric Focus:**
- What users actually care about
- Not internal metrics (CPU, memory)
- Business impact direct
- Experience-driven

**The Reality:**
Users don't care about:
- Your database CPU usage
- Your network throughput
- Your container count

Users care about:
- ✓ Is it available?
- ✓ Is it fast?
- ✓ Is it reliable?

**Design Implication:**
Monitor and observe from the user's perspective, not just infrastructure health.

---

# Monitoring

## Monitoring Anti-Patterns

### Anti-Pattern #1: Tool Obsession

> "**#1 Tool Obsession**: Chasing 'single pane of glass' or new tools without defined outcomes."

---

#### The Problem

**What It Looks Like:**
- "We need a new monitoring tool!"
- "Let's get the latest observability platform!"
- "This tool has a unified dashboard!"
- Buying tools before defining needs

**Why It Happens:**
- Shiny object syndrome
- Vendor marketing
- Thinking tool solves problems
- No clear requirements

**The Trap:**
- Tool sprawl (5+ monitoring tools)
- High costs
- Complexity increases
- Still can't answer basic questions
- Integration nightmare

---

#### The Solution

> "**Do instead**: Start from user/business outcomes → capabilities → minimal toolset; prototype, integrate, and consolidate."

**The Right Approach:**

**1. Start with Outcomes:**
- What questions need answering?
- What decisions will data drive?
- What user impact to prevent?

**2. Define Capabilities:**
- Need to track SLIs?
- Need distributed tracing?
- Need log aggregation?

**3. Minimal Toolset:**
- Fewest tools possible
- Each tool has clear purpose
- Avoid overlap
- Integration considered

**4. Prototype:**
- Test before buying
- Prove value
- Validate assumptions

**5. Consolidate:**
- Retire old tools
- Unify where possible
- Reduce complexity

**Example:**
```
Wrong: "Buy Datadog because everyone uses it"
Right: "We need to track API latency (outcome) →
       Need metrics collection (capability) →
       Prometheus (minimal tool) →
       Test with one service (prototype)"
```

---

### Anti-Pattern #2: Monitoring-as-a-Job

> "**#2 Monitoring-as-a-Job**: One team 'owns' all monitoring; product teams uninvolved."

---

#### The Problem

**What It Looks Like:**
- Central "Monitoring Team"
- Product teams file tickets for alerts
- Ops team maintains all dashboards
- Product teams don't understand metrics
- "Not my job" mentality

**Why It's Bad:**
- Bottleneck (monitoring team overloaded)
- Product teams lack ownership
- Alerts are generic, not specific
- Slow to respond to changes
- Monitoring lags behind development

**The Consequences:**
- Alerts that don't help
- Dashboards nobody uses
- Product teams ignore monitoring
- Incidents take longer to resolve

---

#### The Solution

> "**Do instead**: Make monitoring a shared engineering skill; platform/observability team provides self-service tooling, not all alerts."

**The Right Model:**

**Product Teams:**
- Own their service's monitoring
- Define their own SLIs/SLOs
- Create their dashboards
- Manage their alerts
- On-call for their services

**Platform/Observability Team:**
- Provide self-service tools
- Create templates and standards
- Build monitoring infrastructure
- Offer training and guidance
- Enable, not own

**Example:**
```
Wrong: Product team: "We need an alert on API errors"
       → File ticket with monitoring team
       → Wait 2 weeks
       → Generic alert created

Right: Product team: Uses self-service platform
       → Creates alert themselves
       → Iterates based on feedback
       → Owns and maintains it
```

**Benefits:**
- Faster iteration
- Better alerts (context)
- Ownership culture
- Scales better

---

### Anti-Pattern #3: Checkbox Monitoring

> "**#3 Checkbox Monitoring**: Superficial metrics/alerts to tick compliance boxes; noisy, low trust."

---

#### The Problem

**What It Looks Like:**
- Monitoring for compliance, not usefulness
- "Check: We monitor CPU ✓"
- "Check: We have alerts ✓"
- But alerts are noise
- Nobody trusts them

**Examples of Checkbox Monitoring:**
- Monitor disk space but never alert
- Track 100 metrics, use 3
- Alerts that always fire
- Dashboards nobody looks at
- Required by policy, not useful

**The Consequences:**
- Alert fatigue
- Ignored notifications
- False sense of security
- Real issues missed
- Low trust in monitoring

---

#### The Solution

> "**Do instead**: Define 'what does working mean?'; create high-signal checks tied to user journeys and SLIs; tune/retire noisy alerts."

**The Right Approach:**

**1. Define "Working":**
- What does success look like?
- User can log in
- Payment processes
- Data updates correctly

**2. High-Signal Checks:**
- Tied to user journeys
- Based on SLIs
- Actionable alerts
- Clear remediation

**3. Tune Alerts:**
- Reduce false positives
- Adjust thresholds
- Add context
- Test alert runbooks

**4. Retire Noisy Alerts:**
- Alert fires constantly? Delete it
- Alert ignored? Delete it
- Alert unclear? Fix or delete it

**Example:**
```
Wrong: Alert "CPU > 80%"
       → Fires often
       → System still works fine
       → Ignored

Right: Alert "p99 Latency > 500ms for 5 minutes"
       → Tied to user experience
       → SLO-based
       → Actionable
       → Trusted
```

**Key Principle:**
Every alert should be actionable. If you can't do anything about it, don't alert.

---

### Anti-Pattern #4: Monitoring as a Crutch

> "**#4 Monitoring as a Crutch**: Adding more alerts to compensate for brittle systems."

---

#### The Problem

**What It Looks Like:**
- System crashes often
- Response: Add more alerts
- System still crashes
- Response: Add even more alerts
- Treating symptom, not cause

**The Cycle:**
1. Service is unreliable
2. Add monitoring and alerts
3. Get alerted frequently
4. Firefight constantly
5. System still unreliable
6. Add more alerts (repeat)

**Why It's Wrong:**
- Monitoring doesn't fix bugs
- Alerts don't improve reliability
- Hides systemic problems
- Alert fatigue increases
- On-call burnout

**The Reality:**
More monitoring ≠ More reliability

---

#### The Solution

> "**Do instead**: Fix root causes; invest in reliability engineering (SLOs, error budgets, chaos tests, resilience patterns)."

**The Right Approach:**

**1. Fix Root Causes:**
- Why does service crash?
- Fix the bugs
- Improve architecture
- Add proper error handling

**2. Reliability Engineering:**
- Define SLOs
- Use error budgets
- Prioritize reliability work
- When budget low → fix stability

**3. Chaos Testing:**
- Deliberately break things
- Find weaknesses
- Fix before production
- Build resilience

**4. Resilience Patterns:**
- Circuit breakers
- Retry logic
- Graceful degradation
- Fault tolerance

**Example:**
```
Wrong: Database crashes nightly
       → Add alert for database down
       → Get paged every night
       → Restart database
       → Repeat forever

Right: Database crashes nightly
       → Investigate root cause
       → Find memory leak
       → Fix the leak
       → Database stable
       → Remove alert (no longer needed)
```

**Key Insight:**
Use monitoring to identify problems, then fix the problems. Don't just monitor forever.

---

### Anti-Pattern #5: Manual Configuration

> "**#5 Manual Configuration**: Hand-crafted checks/dashboards; slow, inconsistent, stale."

---

#### The Problem

**What It Looks Like:**
- Click through UI to create alerts
- Manually configure each service
- Dashboards created ad-hoc
- No version control
- Configuration drift

**Why It's Bad:**
- Slow to create
- Inconsistent across services
- Hard to replicate
- No audit trail
- Goes stale (not updated)
- Knowledge in one person's head

**The Consequences:**
- New services not monitored
- Dashboards outdated
- Can't reproduce setup
- Bus factor = 1

---

#### The Solution

> "**Do instead**: Automate discovery/registration; config-as-code; templates; golden dashboards; enforce review and versioning."

**The Right Approach:**

**1. Automate Discovery:**
- Services auto-register
- Monitoring configured automatically
- No manual setup
- Use service discovery

**2. Configuration as Code:**
- Monitoring config in Git
- Version controlled
- Reviewed like code
- Auditable

**3. Templates:**
- Standard dashboard templates
- Standard alert templates
- Customize when needed
- Consistent baseline

**4. Golden Dashboards:**
- Standard dashboards for common services
- Pre-configured best practices
- Reusable across teams

**5. Review and Versioning:**
- Pull requests for changes
- Team reviews
- Git history
- Rollback possible

**Example:**
```
Wrong: Manually create Grafana dashboard
       → Click, click, click
       → Takes 2 hours
       → Colleague can't reproduce it
       → Service updates, dashboard not updated

Right: Dashboard as code (Terraform/Grafonnet)
       → Define in code
       → Version in Git
       → Automated deployment
       → Self-updating from service discovery
       → Consistent across services
```

**Technologies:**
- Terraform for infrastructure
- Grafana provisioning
- Prometheus service discovery
- Alert manager config files

---

## Monitoring Best Practice Patterns

### Pattern #1: Composable Monitoring

> "**Concept**: Instead of monolithic tools, build a platform by combining specialized tools, loosely coupled."

**Philosophy:**
> "'Write programs that do one thing and do it well. Write programs to work together.' - Doug McIlroy"

---

#### The Unix Philosophy Applied

**Principles:**
1. Do one thing well
2. Work together
3. Loosely coupled
4. Composable pieces

**Applied to Monitoring:**
- Not one tool for everything
- Specialized tools for each function
- Tools integrate via standard interfaces
- Mix and match as needed

---

#### Components of Monitoring System

> "Every monitoring system includes collection, storage, visualization, analytics, and alerting."

**The Five Components:**

**1. Collection:**
- Gather metrics, logs, traces
- Tools: Telegraf, Fluentd, OTEL Collector
- Push vs Pull models

**2. Storage:**
- Time-series databases (TSDB)
- Tools: Prometheus, InfluxDB, Victoria Metrics
- Log storage: Elasticsearch, Loki

**3. Visualization:**
- Dashboards and graphs
- Tools: Grafana, Kibana
- User interface

**4. Analytics:**
- Query and analyze data
- Tools: PromQL, LogQL, SQL
- Data processing

**5. Alerting:**
- Notify on issues
- Tools: Alertmanager, PagerDuty
- Notification routing

---

#### Composable Architecture Example

```
Collection:       Telegraf → Prometheus
                  Fluentd → Elasticsearch
                  OTEL → Jaeger

Storage:          Prometheus (metrics)
                  Elasticsearch (logs)
                  Jaeger (traces)

Visualization:    Grafana (connects to all)

Analytics:        PromQL, Lucene, Jaeger UI

Alerting:         Alertmanager → PagerDuty
```

**Benefits:**
- Best tool for each job
- Replace components independently
- Avoid vendor lock-in
- Evolve over time

---

#### Design Choices

> "Push vs pull, structured vs unstructured logs, TSDBs (Time Series Databases), and visualization principles define design choices."

**Push vs Pull:**
- **Push**: Agent sends data to server
- **Pull**: Server scrapes agent
- Prometheus uses pull
- StatsD uses push

**Structured vs Unstructured Logs:**
- **Structured**: JSON, key-value
- **Unstructured**: Plain text
- Structured better for analysis

**TSDBs:**
- Optimized for time-series data
- Efficient storage (compression)
- Fast queries
- Retention policies

---

#### The Main Goal

> "SLAs and alerts are secondary outcomes; the main goal is to understand and reason about systems."

**Key Insight:**
- Monitoring isn't just about alerts
- Primary goal: Understanding
- Enable reasoning about behavior
- Support debugging and optimization
- Alerts are byproduct

**Philosophy:**
Observability first, monitoring second.

---

### Pattern #2: Monitor from the User Perspective

> "**Starting point**: Begin monitoring at the point where users interact with the app."

**User-Centric Approach:**
- Monitor what users experience
- Not just internal metrics
- Outside-in perspective
- Business impact focus

---

#### Key Metrics

> "**Key metrics:**
> - HTTP response codes (especially 5xx errors)
> - Request times/latency"

**Why These Metrics:**

**HTTP Response Codes:**
- **2xx (Success)**: Request worked
- **4xx (Client Error)**: User mistake (bad request)
- **5xx (Server Error)**: Our fault! (system broken)

**Focus on 5xx:**
- Indicates system problems
- Direct user impact
- Affects availability SLI
- Requires action

**Example Monitoring:**
```
5xx Error Rate = (5xx Responses / Total Requests) × 100%

Alert if: 5xx rate > 1% for 5 minutes
```

---

**Request Times/Latency:**
- How long requests take
- User-perceived performance
- Affects user experience
- Correlates with conversions

**What to Measure:**
- p50 (median): Typical user
- p95: Most users (95%)
- p99: Almost all users (99%)
- p99.9: Even slower cases

**Why Percentiles:**
Mean hides outliers. p99 shows worst-case users experience.

**Example:**
- Mean: 100ms (looks good!)
- p99: 5000ms (1% of users wait 5 seconds!)

---

#### The Benefit

> "**Benefit**: Focuses attention on actual user impact, not just internal system health."

**Traditional Approach (Wrong):**
- Monitor CPU usage
- Monitor memory
- Monitor disk I/O
- High CPU alert!

**Problem:**
- CPU at 90%
- But users happy
- System working fine
- Alert is noise

**User-Centric Approach (Right):**
- Monitor availability (5xx rate)
- Monitor latency (p99)
- Monitor error rate
- Slow requests alert!

**Problem:**
- CPU at 50% (fine)
- But requests slow
- Users frustrated
- Alert is signal

**The Principle:**
Monitor symptoms (user impact), not causes (internal metrics). Internal metrics help diagnose, but alerts should be user-focused.

---

### Pattern #3: Buy, Not Build

> "**Progression of Monitoring Maturity**"

**The Typical Journey:**
Organizations follow a progression path as they mature.

---

#### Stage 1: SaaS (Start Here)

> "Start with SaaS (quick setup), focus on product."

**SaaS Solutions:**
- Datadog
- New Relic
- Splunk Cloud
- Elastic Cloud

**Advantages:**
- Setup in minutes
- No infrastructure to manage
- Instant updates
- Support included
- Focus on product, not monitoring

**When to Use:**
- Startups
- Small teams
- MVP/prototype phase
- Want to focus on core product

**Cost:**
- Pay per usage
- Scales with you
- Predictable pricing

---

#### Stage 2: Open Source Tools (FOSS)

> "Move to FOSS tools (Graphite, Prometheus, InfluxDB, etc.) when SaaS no longer fits needs."

**FOSS Solutions:**
- Prometheus + Grafana
- ELK Stack (Elasticsearch, Logstash, Kibana)
- Jaeger
- InfluxDB

**When to Transition:**
- SaaS too expensive at scale
- Need more customization
- Compliance/data sovereignty
- Have ops capacity

**Advantages:**
- Free software
- Full control
- Customize everything
- No vendor lock-in

**Disadvantages:**
- Must manage infrastructure
- Need expertise
- Operational burden
- No built-in support

---

#### Stage 3: Custom Platforms (Rare)

> "Custom platforms (Netflix, Dropbox, ..) only when scale/requirements exceed existing tools."

**Custom Solutions:**
- Netflix: Atlas, Mantis
- Uber: M3
- Dropbox: Custom monitoring

**When to Build:**
- Massive scale (millions of metrics/sec)
- Unique requirements
- Existing tools can't handle load
- Have resources (100+ engineer team)

**Examples:**
- Netflix: Billions of metrics
- Uber: Global scale
- Google: Custom everything

**Warning:**
> "Stages can overlap (e.g., SaaS logging + in-house metrics)."

**Hybrid Approach:**
- SaaS for some components
- Self-hosted for others
- Best of both worlds

---

#### The Advice

> "**Advice**: Do not jump to custom too early, master fundamentals first."

**Common Mistake:**
- Startup with 5 engineers
- "Let's build our own monitoring!"
- Spends 6 months building
- Result: Worse than SaaS
- Wasted time

**The Reality:**
> "SaaS monitoring is typically cheaper, faster, and better for most companies. Only very large or specialized organizations truly need custom, in-house solutions."

**Rule of Thumb:**
- < 50 engineers: Use SaaS
- 50-200 engineers: Consider FOSS
- 200+ engineers: Maybe custom for specific needs

**Focus:**
Don't build what you can buy. Build your product.

---

### Pattern #4: Continual Improvement

> "Leading companies (Google, Netflix, etc.) reached advanced monitoring through years of iteration, not overnight success."

---

#### The Long Journey

**The Reality:**
- Google's monitoring: 15+ years of evolution
- Netflix's observability: 10+ years
- Amazon's CloudWatch: Decades of learning

**Key Insight:**
Advanced monitoring is a journey, not a destination.

---

#### Tools Evolve

> "Tools evolve: old ones get retired, new ones are built as needs change."

**Natural Evolution:**
- Year 1: Nagios → basic checks
- Year 2: Add Graphite → metrics
- Year 3: Switch to Prometheus → better metrics
- Year 4: Add ELK → logs
- Year 5: Add Jaeger → tracing
- Year 6: Consolidate to unified platform

**Pattern:**
- Start simple
- Add capabilities
- Replace as needed
- Consolidate periodically

---

#### Consistent Effort

> "Monitoring maturity requires consistent effort over time, not a single big leap."

**Not a Project:**
- Monitoring is ongoing
- Not "done" and finished
- Continuous refinement
- Always improving

**Consistent Effort:**
- Regular reviews
- Tune alerts quarterly
- Update dashboards
- Retire unused metrics
- Add new capabilities

---

#### Re-architecture Cycles

> "Expect to re-architect every 2-3 years as systems grow and industry practices shift."

**Why Re-architecture:**
- Company grows (10x)
- Technology evolves
- New best practices
- Tool improvements
- Requirements change

**Typical Cycles:**
- **Years 0-2**: SaaS, simple
- **Years 3-4**: FOSS, learning
- **Years 5-6**: Re-arch for scale
- **Years 7-8**: Optimize and consolidate
- **Years 9+**: Maybe custom

**Expectation:**
Plan to rebuild every 2-3 years. Not failure, it's evolution.

---

#### Key Insight

> "**Key insight**: Monitoring excellence is a long-term journey, built on steady, continual improvement."

**The Mindset:**
- Marathon, not sprint
- Incremental progress
- Learn from mistakes
- Celebrate improvements
- Never "done"

**Success Formula:**
1. Start simple
2. Improve regularly
3. Learn from incidents
4. Iterate based on feedback
5. Evolve tools as needed
6. Repeat

---

# Statistics for Monitoring

## Why Statistics Matter

### The Context

> "**Undervalued & misunderstood**: Stats won't create 'magic,' but basic methods are highly useful for monitoring."

**The Reality:**
- Statistics isn't magic
- But incredibly useful
- Don't need advanced math
- Basic methods go far
- Often misunderstood

**Practical Application:**
- Reduce false positives
- Detect anomalies
- Understand trends
- Design better alerts

---

## Threshold Pitfalls (Old Approach)

### The Nagios Era

> "**Threshold pitfalls (Nagios era)**: Single-point checks vs fixed warn/crit thresholds will create noise & flapping; flap detection only masks bad alert design."

---

#### The Old Way (Problematic)

**Single-Point Checks:**
```
if (cpu_usage > 80) {
  ALERT: "CPU High!"
}
```

**Problems:**
1. **Flapping**: Value oscillates around threshold
   - 79% → OK
   - 81% → ALERT
   - 79% → OK (Alert resolves)
   - 81% → ALERT (Alert fires again)
   - Result: Alert spam

2. **No Context**: Single sample insufficient
   - Spike for 1 second? Alert
   - Sustained high? Alert
   - Can't distinguish

3. **Fixed Thresholds**: Don't adapt
   - 80% might be fine for one service
   - 80% might be critical for another
   - No seasonality consideration

---

#### Flap Detection (Band-Aid)

**Nagios Solution:**
- Detect when alert flapping
- Suppress notifications
- "Flap detection enabled"

**Problem:**
Masks the symptom, doesn't fix the cause.

**The Issue:**
Bad alert design, not notification problem.

---

## Modern Approach

> "**Modern approach**: Decouple collection and evaluation, collect to a TSDB (e.g., via agents) at intervals, then evaluate over windows of data."

---

### The Better Way

**1. Decouple Collection from Evaluation:**
- **Collection**: Agent gathers metrics every 10s
- **Storage**: Metrics stored in TSDB
- **Evaluation**: Alerting system queries TSDB
- **Benefit**: Can evaluate over time, not just instant

**2. Collect to TSDB:**
- Time-Series Database (Prometheus, InfluxDB)
- Stores metrics over time
- Enables historical analysis

**3. Evaluate Over Windows:**
- Not single data point
- Look at 5 minutes, 10 minutes
- Consider trends
- Reduces noise

---

### Example: Modern Alert

**Old (Bad):**
```
Alert if: cpu_usage > 80%
```
- Flaps constantly

**New (Good):**
```
Alert if: avg(cpu_usage[5m]) > 80% for 10 minutes
```
- Sustained high CPU
- Filters transient spikes
- No flapping

**Better (Best):**
```
Alert if: p95_latency > 500ms for 5 minutes
```
- User-centric (latency, not CPU)
- Statistical measure (p95)
- Time window (5 minutes)
- Clear threshold

---

## Key Shift

> "**Key shift**: keep historical metrics to enables trends, smarter detection, and fewer false positives."

**Historical Data Benefits:**

**1. Trend Analysis:**
- See if problem growing
- Predict future issues
- Understand patterns

**2. Smarter Detection:**
- Compare to past
- Detect anomalies
- Seasonality awareness

**3. Fewer False Positives:**
- Filter noise
- High confidence alerts
- Reduced alert fatigue

---

## Core Statistical Tools

### Mean and Moving Average

> "**Mean (average) & moving average**: Smooths spikes; improves readability but hides extremes, choose smoothing windows carefully."

---

#### Mean (Average)

**Formula:**
```
Mean = Sum of all values / Count of values
```

**Example:**
Response times: 100ms, 200ms, 150ms, 180ms, 170ms
Mean = (100 + 200 + 150 + 180 + 170) / 5 = 160ms

**Use Cases:**
- Overall average
- General trend
- Simple summary

**Problems:**
- Hides outliers
- Skewed by extremes
- Not representative for long-tail distributions

**Example Problem:**
Response times: 100ms, 100ms, 100ms, 100ms, 5000ms
Mean = 1080ms (misleading! Most requests are 100ms)

---

#### Moving Average

**Concept:**
Average over a sliding window.

**Example:**
5-minute moving average of request rate:
- 14:00: avg(13:55-14:00)
- 14:01: avg(13:56-14:01)
- 14:02: avg(13:57-14:02)

**Benefits:**
- Smooths spikes
- Shows trend
- Reduces noise
- Easier to read graphs

**Trade-offs:**
- Hides short-term changes
- Lags behind reality
- Window size critical

**Window Size Choice:**
- Too small: Still noisy
- Too large: Misses issues
- Typical: 1-15 minutes

---

### Median

> "**Median**: Better than mean for skewed datasets (robust to outliers)."

**Definition:**
The middle value when sorted.

**Example:**
Response times: 100ms, 100ms, 100ms, 100ms, 5000ms
Sorted: 100, 100, 100, 100, 5000
Median: 100ms (the middle value)

Compare to mean: 1080ms (misleading)

**Why Better:**
- Not affected by outliers
- Represents typical experience
- Robust

**When to Use:**
- Latency measurements
- Any long-tail distribution
- Skewed data

**Limitation:**
Doesn't show outliers. Combine with percentiles.

---

### Seasonality

> "**Seasonality**: Repeating patterns (hourly/daily/weekly)."

**Definition:**
Predictable patterns that repeat over time.

---

#### Types of Seasonality

**Hourly:**
- 9 AM: Traffic spike (people start work)
- 12 PM: Lunch dip
- 5 PM: Evening spike

**Daily:**
- Weekdays: High traffic
- Weekends: Low traffic

**Weekly:**
- Monday: Peak
- Friday: Medium
- Sunday: Low

**Seasonal (yearly):**
- Black Friday: Peak
- January: Low
- Holiday season: High

---

#### Using Seasonality

> "Compare now vs same time last week/day to detect anomalies."

**Smart Alerting:**
```
Bad:  if (requests < 1000) alert
      → Fires every night (low traffic normal)

Good: if (requests < 80% of same time last week) alert
      → Monday 9 AM: Expect high traffic
      → Alert if significantly lower than last Monday 9 AM
```

**Benefits:**
- Context-aware
- Adapts to patterns
- Reduces false positives

**Implementation:**
- Store historical data
- Compare time windows
- Use week-over-week
- Consider day-of-week

---

### Quantiles and Percentiles

> "**Quantiles/percentiles (e.g., p95, p99)**: Summarize 'most users' experience' (latency, bandwidth)."

---

#### Understanding Percentiles

**Definition:**
The value below which a percentage of observations fall.

**p95 (95th percentile):**
95% of requests faster than this value.

**Example:**
100 requests with response times:
- 95 requests: < 200ms
- 5 requests: 1000-5000ms
- p95: 200ms

**Meaning:**
95% of users experience ≤ 200ms response time.

---

#### Common Percentiles

**p50 (Median):**
- 50% of requests faster
- Typical user experience
- Not affected by outliers

**p95:**
- 95% of requests faster
- Most users' experience
- Shows some slower cases

**p99:**
- 99% of requests faster
- Almost all users
- Reveals tail latency

**p99.9:**
- 99.9% of requests faster
- Extreme cases
- Very rare but important

---

#### Why Percentiles Matter

**Example:**

| Metric | Value | Interpretation |
|--------|-------|----------------|
| Mean | 150ms | Average (misleading) |
| p50 | 100ms | Typical user |
| p95 | 200ms | Most users |
| p99 | 500ms | 1% wait this long |
| p99.9 | 5000ms | Some users suffer |

**Insight:**
Mean looks good (150ms), but 1% of users wait 500ms+. That's poor experience for thousands of users!

**For SLIs/SLOs:**
```
Good:  "p95 latency < 300ms"
       → 95% of users have fast experience

Bad:   "Average latency < 300ms"
       → Could mean 50% fast, 50% very slow
       → Average says nothing
```

---

## Designing Better Alerts

> "**Design better alerts:**
> - Alert on 'is it working?' user-journey checks, not raw OS metrics
> - Evaluate over time windows (rates/percentiles), not single samples"

---

### Principle 1: User Journey Checks

**Bad Alerts (Internal Metrics):**
```
✗ CPU > 80%
✗ Memory > 90%
✗ Disk I/O > 1000 ops/s
```

**Why Bad:**
- Internal metrics
- Not user-visible
- May not indicate actual problem

**Good Alerts (User Impact):**
```
✓ Login success rate < 99%
✓ Checkout completion rate < 95%
✓ API p99 latency > 500ms
```

**Why Good:**
- Measures user experience
- Direct business impact
- Actionable

---

### Principle 2: Time Windows

**Bad Alerts (Single Sample):**
```
✗ if (latency > 500ms) alert
   → Fires on single slow request
   → Noise

✗ if (cpu > 80%) alert
   → Fires on brief spike
   → Flapping
```

**Good Alerts (Time Windows):**
```
✓ if (p95_latency > 500ms for 5 minutes) alert
   → Sustained issue
   → Filters transient spikes
   → Actionable

✓ if (error_rate > 1% for 10 minutes) alert
   → Real problem
   → Not brief blip
   → High confidence
```

---

### Alert Design Checklist

**Good Alert Characteristics:**
1. **User-focused**: Measures user impact
2. **Actionable**: Clear what to do
3. **Time-windowed**: Evaluates over time
4. **Statistical**: Uses rates/percentiles
5. **SLO-based**: Tied to objectives
6. **Documented**: Runbook exists

**Example of Great Alert:**
```
Name: "Payment API SLO Violation"
Condition: p95_latency > 500ms for 10 minutes
Why: Users experiencing slow checkout
Action: Check database connection pool
Runbook: docs/runbooks/payment-slow.md
SLO: Latency p95 < 300ms (violated)
```

---

# Observability

## Three Pillars of Observability

### Event-Based Foundation

> "**Unifying the three features – event based**
> All of these is based on the events."

**Core Insight:**
Logs, metrics, and traces all record events, just in different formats.

**The Three Forms:**
> "**Logging**: recording events
> **Metrics**: data combined from measuring events
> **Tracing**: recording events with causality order"

---

### Comparison Using Latency

> "Use latency to compare a few tools:
> - **Log** - event (response time)
> - **Metric** - value (response time)
> - **Trace** - tree (response time)"

**Example: API Request with 200ms latency**

**1. Log (Event):**
```
2025-01-22T14:23:45Z GET /api/users/123 200 200ms
```
- Single event
- Point in time
- Context around request

**2. Metric (Value):**
```
api_request_duration_seconds{endpoint="/api/users",method="GET"} 0.200
```
- Numerical value
- Aggregatable
- Time-series

**3. Trace (Tree):**
```
Request [200ms]
  ├─ API Gateway [10ms]
  ├─ Auth Service [30ms]
  ├─ Database Query [150ms]  ← Bottleneck!
  └─ Response Format [10ms]
```
- Causal relationships
- End-to-end flow
- Performance breakdown

---

## Pillar 1: Logging

### What Are Logs?

**Definition:**
Recording of discrete events that happened in the system.

**Characteristics:**
- Timestamped
- Human-readable
- Contextual
- Narrative

---

### Log Example

**Unstructured Log:**
```
2025-01-22 14:23:45 INFO User 123 logged in from 203.0.113.45
```

**Structured Log (JSON):**
```json
{
  "timestamp": "2025-01-22T14:23:45Z",
  "level": "INFO",
  "message": "User logged in",
  "user_id": 123,
  "ip": "203.0.113.45",
  "session_id": "abc-def-123"
}
```

---

### Log Levels

**Standard Levels:**
- **DEBUG**: Detailed diagnostic info (development)
- **INFO**: General informational (normal operations)
- **WARN**: Warning, but system continues
- **ERROR**: Error occurred, feature failed
- **FATAL/CRITICAL**: System crash, immediate attention

**Usage Guidelines:**
- **DEBUG**: "User query: SELECT * FROM..."
- **INFO**: "User 123 logged in successfully"
- **WARN**: "Retry attempt 3/5 for API call"
- **ERROR**: "Failed to save user profile, database timeout"
- **FATAL**: "Cannot connect to database, shutting down"

---

### When to Use Logs

**Good For:**
- Debugging specific issues
- Audit trails
- Understanding sequence of events
- Contextual information
- Error details

**Examples:**
- "Why did this user's checkout fail?"
- "Who accessed this resource?"
- "What was the error message?"

**Not Good For:**
- High-frequency events (every request)
- Metrics/aggregation
- Real-time dashboards
- Performance monitoring (use metrics)

---

### Structured Logging

**Why Structured:**
- Easy to parse
- Queryable
- Consistent
- Machine-readable

**Best Practices:**
- JSON format
- Consistent fields
- Add context (request_id, user_id)
- Avoid PII (personal info)

---

## Pillar 2: Metrics

### What Are Metrics?

**Definition:**
Numerical measurements aggregated over time.

**Characteristics:**
- Numeric values
- Time-series data
- Aggregatable
- Efficient storage

---

### Types of Metrics

**1. Counters:**
- Only increase
- Never decrease
- Examples: Total requests, errors, bytes sent

**2. Gauges:**
- Can go up or down
- Point-in-time value
- Examples: CPU usage, memory, active connections

**3. Histograms:**
- Distribution of values
- Buckets of observations
- Examples: Request duration, response size

**4. Summaries:**
- Quantiles/percentiles
- Pre-calculated percentiles
- Examples: p95, p99 latency

---

### Metric Example

**Prometheus Format:**
```
# Counter
http_requests_total{method="GET",endpoint="/api/users",status="200"} 15234

# Gauge
memory_usage_bytes 4294967296

# Histogram
http_request_duration_seconds_bucket{le="0.1"} 9500
http_request_duration_seconds_bucket{le="0.5"} 9950
http_request_duration_seconds_bucket{le="1.0"} 10000
```

---

### When to Use Metrics

**Good For:**
- Real-time dashboards
- Alerting on thresholds
- Trending over time
- Aggregation and statistics
- SLIs/SLOs

**Examples:**
- "What's the current request rate?"
- "Is latency increasing?"
- "Alert when error rate > 1%"

**Not Good For:**
- Individual event details
- Why something happened
- Debugging specific issues

---

### Cardinality Considerations

**Cardinality:**
Number of unique time series.

**Example:**
```
metric{label1="value1",label2="value2"}
```

**Low Cardinality (Good):**
```
http_requests{method="GET",status="200"}
```
- Few methods (GET, POST, PUT, DELETE)
- Few statuses (200, 400, 500, ...)
- = 4 methods × 10 statuses = 40 time series

**High Cardinality (Bad):**
```
http_requests{method="GET",user_id="12345"}
```
- Millions of user IDs
- = Millions of time series
- Kills performance!

**Rule:**
Keep labels to low-cardinality dimensions.

---

## Pillar 3: Distributed Tracing

### What Is Tracing?

**Definition:**
Recording the path of a request through a distributed system, with timing information.

**Purpose:**
- Understand request flow
- Find bottlenecks
- Diagnose latency issues
- Visualize dependencies

---

### Why Distributed Tracing?

**The Problem:**

**Monolith (Simple):**
```
Request → Application → Database → Response
```
- Easy to debug
- Single log file
- Clear flow

**Microservices (Complex):**
```
Request → API Gateway → Auth Service → User Service → Profile Service
                                    → Database
                      → Cache
                      → Payment Service → Payment Gateway
                                       → Fraud Check Service
```
- Where's the delay?
- Which service slow?
- Can't tell from logs alone

**Tracing Solution:**
Track request through entire flow with timing.

---

### Trace Concepts

**Trace:**
- Represents a single transaction/request
- End-to-end journey
- Unique trace ID

**Span:**
- Unit of work within a trace
- Has start and end time
- Represents one operation

**Parent-Child Relationship:**
- Spans form a tree
- Parent span calls child spans
- Causality preserved

---

# Distributed Tracing

## Understanding Spans

### Span Definition

> "**Span** = operation within a transaction."

**What Is a Span:**
- A single unit of work
- Has a start time
- Has an end time
- Duration = end - start
- Part of a larger trace

---

### Span Contents

> "**Span contains:**
> - Parent's Span identifier
> - An operation name
> - A start and finish timestamp
> - Attributes will be key-value pairs
> - A set of zero or more Events, each of which itself a tuple (timestamp, name, attributes)"

---

#### Span Fields

**1. Parent Span ID:**
```
parent_span_id: "abc123"
```
- Links to parent operation
- Forms tree structure
- Null if root span

**2. Operation Name:**
```
operation: "GET /api/users/{id}"
```
- What this span represents
- Human-readable
- Standardized naming

**3. Start and Finish Timestamps:**
```
start_time: 2025-01-22T14:23:45.000Z
end_time: 2025-01-22T14:23:45.200Z
duration: 200ms
```

**4. Attributes (Key-Value Pairs):**
```
attributes: {
  "http.method": "GET",
  "http.url": "/api/users/123",
  "http.status_code": 200,
  "user.id": 123,
  "db.statement": "SELECT * FROM users WHERE id=?"
}
```

**5. Events:**
```
events: [
  {
    timestamp: 2025-01-22T14:23:45.050Z,
    name: "cache_miss",
    attributes: {"cache.key": "user:123"}
  },
  {
    timestamp: 2025-01-22T14:23:45.180Z,
    name: "db_query_complete",
    attributes: {"rows_returned": 1}
  }
]
```

---

### Example Span

```json
{
  "trace_id": "xyz789",
  "span_id": "span456",
  "parent_span_id": "span123",
  "name": "database.query",
  "start_time": "2025-01-22T14:23:45.100Z",
  "end_time": "2025-01-22T14:23:45.250Z",
  "duration_ms": 150,
  "attributes": {
    "db.system": "postgresql",
    "db.statement": "SELECT * FROM users WHERE id = $1",
    "db.user": "app_user"
  },
  "events": [
    {
      "timestamp": "2025-01-22T14:23:45.105Z",
      "name": "query_start",
      "attributes": {}
    }
  ]
}
```

---

## Trace Visualizations

### Graph View

> "**Tracing | Graph view**
> Traces can be seen as directed acyclic graph of Spans"

**What Is a DAG:**
- **Directed**: Arrows show flow (parent → child)
- **Acyclic**: No loops (no cycles)
- **Graph**: Nodes (spans) and edges (relationships)

---

#### Example Graph Structure

```
      [API Request]          ← Root Span
           |
     +-----------+
     |           |
  [Auth]    [Get User]        ← Child Spans
             |
        +----------+
        |          |
   [Database]  [Cache]        ← Grandchild Spans
```

**Characteristics:**
- Shows dependencies
- Parallel operations visible
- Can identify sequential vs parallel

---

### Temporal View

> "**Tracing | Temporal View**
> Traces can be seen as directed acyclic graph of Spans"

**Timeline Visualization:**
Shows spans over time, like a Gantt chart.

```
Time →
0ms        50ms       100ms      150ms      200ms
|----------|----------|----------|----------|
[========== API Request =======================]
  [=Auth=]
           [====== Get User ================]
              [=Cache=]
                      [===== Database =====]
                                    [=Format=]
```

**What You See:**
- Duration of each operation
- Which operations overlap (parallel)
- Which are sequential
- Where time is spent

---

### Example Temporal View

**Request: GET /api/client/123 (92ms total)**

```
0ms        20ms       40ms       60ms       80ms      92ms
|----------|----------|----------|----------|----------|
[=============== POST /api/v1/client/123 ================] 92ms
  [Wire Time]
  [===== Sync Client Manager ====] 42ms
                                   [=Async Client Manager=]
```

**Insights:**
- Total time: 92ms
- Sync operation: 42ms (46%)
- Wire time and async: Remaining time
- **Bottleneck**: Sync Client Manager

---

## Latency Analysis Examples

### Logging Example

> "**Logging:**
> `127.0.0.1 - - [12/Sep/2025:12:44:32 +0100] "GET /api/v1/client/123 HTTP/1.1" 200 512 "https://example.com/dashboard" "curl/7.88.1" 0.092`
>
> The response time is 92 ms."

**What Log Tells Us:**
- Request happened
- Took 92ms
- Succeeded (200)

**What Log DOESN'T Tell Us:**
- Why 92ms?
- What was slow?
- Where's the bottleneck?
- Was it database? Cache? Network?

**Limitation:**
Single number, no breakdown.

---

### Metrics Example

> "**Metrics:**
> Is the system slow? How fast were the requests at 14:19?"

**Metrics Dashboard:**
```
api_request_duration_seconds{endpoint="/api/v1/client"}

14:15 - p50: 45ms, p95: 120ms, p99: 250ms
14:16 - p50: 50ms, p95: 130ms, p99: 280ms
14:17 - p50: 48ms, p95: 125ms, p99: 260ms
14:18 - p50: 52ms, p95: 135ms, p99: 290ms
14:19 - p50: 90ms, p95: 250ms, p99: 1200ms  ← SPIKE!
```

**What Metrics Tell Us:**
- System got slower at 14:19
- Significant spike in p99 (1200ms)
- But still don't know WHY

**Limitation:**
Shows the problem, not the cause.

---

### Trace Example

> "**Tracing:**
> What cause the delay of 92 ms?"

**Trace Breakdown:**
```
Root Span: POST /api/v1/client/123 [92ms total]
  ├─ Wire Time [5ms]
  ├─ Sync Client Manager [42ms]  ← Nearly 50% of time!
  │   ├─ Validate Request [2ms]
  │   ├─ Load Client Config [8ms]
  │   └─ Process Business Logic [32ms]  ← Bottleneck!
  └─ Async Client Manager [45ms]
      ├─ Update Cache [10ms]
      └─ Send Notification [35ms]
```

**What Trace Tells Us:**
- Total time: 92ms
- Wire time: Negligible (5ms)
- **Bottleneck #1**: Sync Client Manager (42ms)
  - Specifically: Business logic (32ms)
- **Bottleneck #2**: Async notification (35ms)

**Actionable Insights:**
1. Investigate business logic - why 32ms?
2. Consider async notifications - block user?
3. Optimize client config loading

---

### Another Trace Example

**Visual Description:** Slides show a flame graph from Datadog.

> "**Trace – another example**
> Source: https://docs.datadoghq.com/fr/dashboards/widgets/profiling_flame_graph/"

**Flame Graph:**
- Width = time spent
- Depth = call stack
- Color = service/function
- Interactive drill-down

**Example Interpretation:**
```
[============================ HTTP Handler ============================] 100%
  [========= Auth =======] 30%
  [==================== Database ====================] 50%
    [======== Query =========] 35%
    [= Connection =] 5%
    [= Parse =] 10%
  [==== Response ====] 20%
```

**Insights:**
- 50% time in database
- 35% on query itself
- Optimize database query first (biggest impact)

---

# Observability Tools Ecosystem

## Overview

> "**Observability tools**"

**The Landscape:**
Modern observability requires multiple tools working together.

---

## Metrics Tools

### Prometheus

> "**Prometheus**: Metrics collection & time-series storage; strong in cloud-native/Kubernetes."

**What It Is:**
- Open-source monitoring system
- Time-series database (TSDB)
- Pull-based metric collection
- Powerful query language (PromQL)

**Key Features:**
- Service discovery (automatically find targets)
- Multi-dimensional data model
- Flexible queries
- Built-in alerting (Alertmanager)

**Strong In:**
- Kubernetes environments
- Cloud-native applications
- Container monitoring
- Dynamic infrastructure

**Example Usage:**
```
# Prometheus config
scrape_configs:
  - job_name: 'api'
    static_configs:
      - targets: ['localhost:8080']

# PromQL query
rate(http_requests_total[5m])
```

---

### VictoriaMetrics / Thanos / Cortex

> "**VictoriaMetrics / Thanos / Cortex**: Scalable TSDB solutions, often Prometheus-compatible."

**Purpose:**
Scale Prometheus beyond single server.

**VictoriaMetrics:**
- Drop-in Prometheus replacement
- Better performance
- Lower resource usage
- Simpler than alternatives

**Thanos:**
- Prometheus add-on
- Long-term storage (S3, GCS)
- Global query view
- High availability

**Cortex:**
- Multi-tenant Prometheus
- Horizontally scalable
- Long-term storage
- Complex setup

**When to Use:**
- Prometheus not scaling
- Need long-term storage (years)
- Multi-cluster setup
- High cardinality metrics

---

## Visualization Tools

### Grafana

> "**Grafana**: Visualization and dashboards; integrates with multiple data sources."

**What It Is:**
- Open-source visualization platform
- Create dashboards
- Supports many data sources
- Alert capabilities

**Data Sources:**
- Prometheus
- InfluxDB
- Elasticsearch
- MySQL/PostgreSQL
- CloudWatch
- 50+ more

**Key Features:**
- Drag-and-drop dashboard builder
- Template variables
- Alert rules
- Annotations
- Sharing and embedding

**Example Use:**
```
Dashboard: "API Performance"
├─ Panel 1: Request Rate (Prometheus)
├─ Panel 2: Error Rate (Prometheus)
├─ Panel 3: Latency p95/p99 (Prometheus)
└─ Panel 4: Log Errors (Elasticsearch)
```

---

## Logging Tools

### Elastic Stack (ELK / OpenSearch)

> "**Elastic Stack (ELK/Opensearch)**: Elasticsearch (storage/search), Logstash (processing), Kibana (visualization) / EDOT (Elastic Observability)."

**Components:**

**Elasticsearch:**
- Distributed search engine
- Log storage
- Full-text search
- JSON document store

**Logstash:**
- Log processing pipeline
- Parse and transform logs
- Enrich data
- Output to Elasticsearch

**Kibana:**
- Visualization UI
- Search logs
- Create dashboards
- Discover patterns

**Alternative: OpenSearch:**
- Open-source fork of Elasticsearch
- AWS-maintained
- Fully compatible

**EDOT (Elastic Observability):**
- Unified observability solution
- Logs + Metrics + Traces + APM
- All-in-one platform

**Typical Flow:**
```
Application Logs
    ↓
Filebeat (shipper)
    ↓
Logstash (processing)
    ↓
Elasticsearch (storage)
    ↓
Kibana (visualization)
```

---

### Fluentd / Fluent Bit

> "**Fluentd / Fluent Bit**: Log forwarding and aggregation; lightweight and extensible."

**Fluentd:**
- Log aggregation daemon
- Ruby-based
- 500+ plugins
- Flexible routing
- Buffer and retry logic

**Fluent Bit:**
- Lightweight version
- C-based (fast, low memory)
- For edge and embedded
- Fewer plugins
- Ideal for containers

**Use Cases:**
- Collect logs from multiple sources
- Parse and filter
- Route to multiple destinations
- Format conversion

**Example:**
```
[Input]       [Processing]     [Output]
Container  →  Fluent Bit   →  Elasticsearch
                ↓
                ├→ S3 (archive)
                └→ Kafka (stream)
```

---

## Unified Observability Frameworks

### OpenTelemetry (OTel)

> "**OpenTelemetry (OTel)**: Vendor-neutral framework for generating and exporting traces, metrics, logs."

**What It Is:**
- CNCF project
- Unified API/SDK
- Standardize observability
- Vendor-agnostic

**Key Components:**
- **API**: Instrument your code
- **SDK**: Collect telemetry
- **Collector**: Receive, process, export
- **Exporters**: Send to backends

**Supported Languages:**
- Java, Python, Go, JavaScript, .NET
- Ruby, PHP, Rust, C++, Swift
- And more

**Benefits:**
- No vendor lock-in
- Single instrumentation
- Export to any backend
- Industry standard

**Architecture:**
```
Application (instrumented with OTel SDK)
    ↓
OTel Collector (receives telemetry)
    ↓
  ├→ Prometheus (metrics)
  ├→ Jaeger (traces)
  └→ Elasticsearch (logs)
```

---

### Jaeger

> "**Jaeger**: Distributed tracing, often paired with OpenTelemetry."

**What It Is:**
- Open-source tracing platform
- CNCF project
- Originally from Uber

**Key Features:**
- Distributed context propagation
- Service dependency analysis
- Performance optimization
- Root cause analysis

**Components:**
- **Client Libraries**: Instrument apps
- **Agent**: Receive traces locally
- **Collector**: Aggregate traces
- **Storage**: Elasticsearch, Cassandra, etc.
- **UI**: Visualize traces

**Use Cases:**
- Microservices tracing
- Performance troubleshooting
- Dependency mapping
- Latency analysis

**Integration:**
```
Application (OTel instrumented)
    ↓
OTel Collector (receives traces)
    ↓
Jaeger (stores and visualizes)
```

---

## Unified Platforms

### Elastic Observability Solution

> "**Elastic Observability Solution**"

**What It Is:**
All-in-one observability platform from Elastic.

**Components:**
- **APM (Application Performance Monitoring)**
  - Distributed tracing
  - Performance metrics
  - Error tracking

- **Logs**
  - Centralized log management
  - Full-text search
  - Log correlation

- **Metrics**
  - Infrastructure monitoring
  - Custom metrics
  - Kubernetes monitoring

- **Uptime Monitoring**
  - Synthetic monitoring
  - Availability checks
  - Alerting

**Integration:**
- Single platform
- Unified UI (Kibana)
- Correlated data
- Logs + Metrics + Traces together

**When to Use:**
- Want all-in-one solution
- Already using Elastic Stack
- Need tight integration
- Prefer commercial support

---

### Feature Usage Tracking

> "**Feature Usage Tracking**
> …is related, but it's not exactly the same as monitoring and observability in the strict reliability engineering sense."

---

#### Definition

> "**Definition**: Collecting data on how users interact with the system, which features are used, how often, in what sequence, and by whom. The end goal is to understand user behavior and product adoption, not just system reliability."

**Focus:**
- User behavior
- Product analytics
- Feature adoption
- User journey

**Different From Observability:**
- Not about system health
- Not about performance
- About product decisions
- Business metrics

---

#### Techniques and Tools

> "**Techniques/Tools**: Event logging, product analytics (Mixpanel, Amplitude, Google Analytics, Matomo, Elastic, Sentry, custom telemetry pipelines)."

**Product Analytics Tools:**
- **Mixpanel**: Event tracking, funnels, retention
- **Amplitude**: User behavior, cohorts
- **Google Analytics**: Web analytics
- **Matomo**: Open-source analytics
- **Heap**: Auto-capture events
- **Segment**: Data pipeline

**Use Cases:**
- Which features are used most?
- Where do users drop off?
- What's the user journey?
- A/B test analysis
- Conversion tracking

**Example Events:**
```json
{
  "event": "button_clicked",
  "properties": {
    "button_name": "checkout",
    "user_id": 12345,
    "timestamp": "2025-01-22T14:23:45Z",
    "page": "/cart"
  }
}
```

**Difference:**
- Observability: "Is system healthy?"
- Feature Tracking: "Are users engaged?"

---

# Practical Implementation

## Observability Requirements

### Maintaining Logs and Metrics

> "**Maintaining Logs and Metrics**"

**Requirements:**
> "- Check if new functionality needs new or updated logs/metrics
> - Clarify edge cases (e.g., WARN vs ERROR) → better discussions
> - Encourage observability as a first-class concern
> - Avoid last-minute, poorly tested logging"

---

#### Check New Functionality

**Process:**
When adding a feature, ask:
- What could go wrong?
- How will we know if it fails?
- What metrics matter?
- What logs needed for debugging?

**Example:**
Adding payment processing:
- **Metrics**: payment_success_rate, payment_duration
- **Logs**: Payment started, validation failed, payment completed
- **Traces**: Span for entire payment flow

---

#### Clarify Edge Cases

> "Clarify edge cases (e.g., WARN vs ERROR) → better discussions"

**The Debate:**
- Is failed login an ERROR or WARN?
- Is retry attempt a WARN or INFO?
- Is slow query an ERROR or WARN?

**Why Clarify:**
- Consistent logging
- Better filtering
- Clear severity
- Team alignment

**Guidelines:**
- **ERROR**: Feature failed, user impacted
- **WARN**: Potential issue, system continues
- **INFO**: Normal operation
- **DEBUG**: Detailed diagnostic

**Example Decisions:**
- Failed login (wrong password): **WARN** (expected)
- Failed login (system error): **ERROR** (unexpected)
- Retry attempt: **INFO** (normal resilience)
- Retry exhausted: **ERROR** (failure)

---

#### First-Class Concern

> "Encourage observability as a first-class concern"

**What This Means:**
- Not an afterthought
- Part of design
- Part of code review
- Part of testing

**Code Review Checklist:**
- ✓ Are key operations logged?
- ✓ Are metrics instrumented?
- ✓ Are traces complete?
- ✓ Are error cases handled?

---

#### Avoid Last-Minute Logging

> "Avoid last-minute, poorly tested logging"

**The Problem:**
- Feature "done"
- Oh, need logs!
- Add logs everywhere
- Not tested
- Logs break production

**The Right Way:**
- Design observability upfront
- Add during development
- Test logging code
- Validate in staging

---

#### Benefits

> "Enable richer monitoring & testing in production (incl. canary releases)"

**Rich Monitoring:**
- Comprehensive metrics
- Detailed logs
- Complete traces
- Understand behavior

**Testing in Production:**
- Canary releases
- Feature flags
- A/B testing
- Safe experimentation

---

### Maintaining Dashboards and Alerts

> "**Maintaining Dashboards and Alerts**"

**Requirements:**
> "- Dashboards/alerts often overlooked → include in 'definition of done'
> - Updates vary: none, minor tweaks, or full restructuring
> - Ensure observability keeps pace with deployments
> - Testing in production should check dashboards, not just user behavior"

---

#### Include in Definition of Done

> "Dashboards/alerts often overlooked → include in 'definition of done'"

**Traditional DoD:**
- ✓ Code written
- ✓ Tests pass
- ✓ Code reviewed
- ✓ Deployed
- ✗ Observability forgotten

**Improved DoD:**
- ✓ Code written
- ✓ Tests pass
- ✓ Code reviewed
- ✓ **Metrics added**
- ✓ **Logs implemented**
- ✓ **Dashboard updated**
- ✓ **Alerts configured**
- ✓ Deployed

**Why:**
Feature isn't "done" if you can't observe it.

---

#### Update Scope Varies

> "Updates vary: none, minor tweaks, or full restructuring"

**Examples:**

**No Update:**
- Internal refactoring
- No user-visible change
- Same metrics apply

**Minor Tweaks:**
- Add one metric to dashboard
- Adjust alert threshold
- Add log line

**Full Restructuring:**
- New service → new dashboard
- Changed architecture → new metrics
- Microservice split → new traces

**Key:**
Assess impact on observability for every change.

---

#### Keep Pace with Deployments

> "Ensure observability keeps pace with deployments"

**The Problem:**
- Deploy 10x per day
- Dashboards updated monthly
- Observability lags behind
- Can't understand new system

**The Solution:**
- Automate dashboard updates
- Config as code
- Deploy with application
- Version together

**Example:**
```
Application Code (v2.5)
    +
Terraform (metrics config)
    +
Dashboard JSON (Grafana)
    ↓
Deploy as unit
```

---

#### Test Dashboards in Production

> "Testing in production should check dashboards, not just user behavior"

**What to Test:**
- Metrics flowing?
- Dashboards displaying?
- Alerts working?
- No errors in telemetry?

**Canary Release Test:**
1. Deploy to 5% of traffic
2. **Check metrics**: Receiving data?
3. **Check dashboards**: Visualizing correctly?
4. **Check alerts**: Firing appropriately?
5. If all good → proceed to 100%

---

#### Guarantees

> "Guarantees correct logs/metrics and timely notifications when failures occur"

**The Goal:**
- When system breaks
- Logs are there
- Metrics show it
- Alerts fire
- Dashboards display it
- Team can debug

**Without This:**
- System breaks
- No visibility
- Blind debugging
- Long outage

---

## OpenTelemetry Spring Boot Integration

### Setup Dependencies

> "**OpenTelemetry SpringBoot starter**"

**Maven Dependencies:**
```xml
<dependencyManagement>
  <dependencies>
    <!-- OpenTelemetry BOM -->
    <dependency>
      <groupId>io.opentelemetry.instrumentation</groupId>
      <artifactId>opentelemetry-instrumentation-bom</artifactId>
      <version>2.10.0</version>
      <type>pom</type>
      <scope>import</scope>
    </dependency>
  </dependencies>
</dependencyManagement>

<dependencies>
  <!-- Spring Boot Actuator -->
  <dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-actuator</artifactId>
  </dependency>

  <!-- OpenTelemetry Spring Boot Starter -->
  <dependency>
    <groupId>io.opentelemetry.instrumentation</groupId>
    <artifactId>opentelemetry-spring-boot-starter</artifactId>
  </dependency>
</dependencies>
```

**What This Provides:**
- Auto-instrumentation
- Actuator integration
- OTLP export
- Managed dependencies

---

### Configuration

> "**OpenTelemetry SpringBoot starter**"

**application.properties:**
```properties
# Tracing Configuration
management.otlp.tracing.endpoint=http://localhost:4318/v1/traces
management.otlp.tracing.timeout=10s
management.tracing.sampling.probability=1

# Metrics Configuration
management.otlp.metrics.export.url=http://localhost:4318/v1/metrics
management.otlp.metrics.export.step=5s

# Service Name
management.opentelemetry.resource-attributes."service-name"=${spring.application.name}
```

---

#### Configuration Breakdown

**Tracing Endpoint:**
```
management.otlp.tracing.endpoint=http://localhost:4318/v1/traces
```
- Where to send traces
- OTLP protocol (OpenTelemetry Protocol)
- Port 4318 = HTTP (4317 = gRPC)

**Tracing Timeout:**
```
management.otlp.tracing.timeout=10s
```
- Export timeout
- Prevents hanging

**Sampling Probability:**
```
management.tracing.sampling.probability=1
```
- Sample 100% of traces (development)
- Production: 0.1 = 10% (reduce volume)

**Metrics Export:**
```
management.otlp.metrics.export.url=http://localhost:4318/v1/metrics
management.otlp.metrics.export.step=5s
```
- Export metrics every 5 seconds

**Service Name:**
```
management.opentelemetry.resource-attributes."service-name"=${spring.application.name}
```
- Identifies service in traces
- Uses Spring app name

---

### Code Integration

> "**OpenTelemetry SpringBoot starter**"

**Controller Example:**
```java
import io.opentelemetry.api.OpenTelemetry;
import io.opentelemetry.api.trace.Tracer;

@Controller
public class MyController {
    private final Tracer tracer;

    public MyController(OpenTelemetry openTelemetry) {
        this.tracer = openTelemetry.getTracer("application");
    }
}
```

**What This Does:**
- Injects OpenTelemetry
- Gets Tracer instance
- Ready to create custom spans

---

#### Auto-Instrumentation

**Out-of-the-Box:**
Spring Boot Starter auto-instruments:
- HTTP requests (incoming)
- HTTP clients (outgoing)
- Database calls (JDBC)
- Redis calls
- Kafka producers/consumers

**No Code Changes Required!**

---

#### Custom Spans

**Example:**
```java
@Service
public class UserService {
    private final Tracer tracer;

    public User getUser(Long id) {
        Span span = tracer.spanBuilder("getUser")
            .startSpan();
        try (Scope scope = span.makeCurrent()) {
            // Your business logic
            span.setAttribute("user.id", id);
            User user = userRepository.findById(id);
            return user;
        } finally {
            span.end();
        }
    }
}
```

**What This Adds:**
- Custom span for business logic
- Attributes (metadata)
- Proper scope management

---

### Full Stack Example

**Architecture:**
```
Spring Boot Application
    ↓ (OTLP)
OTel Collector (localhost:4318)
    ↓
  ├→ Jaeger (traces)
  ├→ Prometheus (metrics)
  └→ Elasticsearch (logs)
```

**Docker Compose:**
```yaml
services:
  otel-collector:
    image: otel/opentelemetry-collector:latest
    ports:
      - "4318:4318"  # OTLP HTTP

  jaeger:
    image: jaegertracing/all-in-one:latest
    ports:
      - "16686:16686"  # UI

  prometheus:
    image: prom/prometheus:latest
    ports:
      - "9090:9090"
```

---

# Project Requirements

## Practice Guide

> "**Practice Guide**
> In the project:"

---

### Requirement 1: Health Checks

> "Implementation of health checks in the project's containers."

**What Are Health Checks:**
- Endpoint that reports service health
- Used by orchestrators (Docker, K8s)
- Used by load balancers
- Enables auto-recovery

**Implementation:**

**Spring Boot:**
```java
// Already provided by Actuator
// Endpoint: /actuator/health

@Component
public class CustomHealthIndicator implements HealthIndicator {
    @Override
    public Health health() {
        // Check database connection
        if (databaseConnected()) {
            return Health.up()
                .withDetail("database", "reachable")
                .build();
        }
        return Health.down()
            .withDetail("database", "unreachable")
            .build();
    }
}
```

**Docker:**
```dockerfile
HEALTHCHECK --interval=30s --timeout=3s --start-period=5s \
  CMD curl -f http://localhost:8080/actuator/health || exit 1
```

**What It Does:**
- Check every 30 seconds
- Mark unhealthy if fails
- Load balancer stops sending traffic
- Container restarted if unhealthy

---

### Requirement 2: Structured Logging

> "Implementation of persistent structured logs, following a structured logging methodology that allows easy understanding of system behavior."

**What Is Structured Logging:**
- JSON format
- Key-value pairs
- Machine-readable
- Queryable

---

#### Implementation

**Logback Configuration (Spring Boot):**
```xml
<configuration>
  <appender name="JSON" class="ch.qos.logback.core.ConsoleAppender">
    <encoder class="net.logstash.logback.encoder.LogstashEncoder">
      <includeContext>true</includeContext>
      <includeCallerData>false</includeCallerData>
      <fieldNames>
        <timestamp>@timestamp</timestamp>
        <message>message</message>
        <logger>logger</logger>
        <level>level</level>
      </fieldNames>
    </encoder>
  </appender>

  <root level="INFO">
    <appender-ref ref="JSON" />
  </root>
</configuration>
```

**Application Code:**
```java
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import net.logstash.logback.argument.StructuredArguments;

@Service
public class UserService {
    private static final Logger log = LoggerFactory.getLogger(UserService.class);

    public void createUser(User user) {
        log.info("Creating user",
            StructuredArguments.kv("user_id", user.getId()),
            StructuredArguments.kv("username", user.getUsername()),
            StructuredArguments.kv("action", "user_creation")
        );
    }
}
```

**Output (JSON):**
```json
{
  "@timestamp": "2025-01-22T14:23:45.123Z",
  "level": "INFO",
  "logger": "com.example.UserService",
  "message": "Creating user",
  "user_id": 12345,
  "username": "john.doe",
  "action": "user_creation",
  "thread": "http-nio-8080-exec-1"
}
```

**Benefits:**
- Easy to parse
- Searchable in Elasticsearch
- Filter by fields
- Correlate logs

---

#### Persistent Storage

**Store Logs:**
- Not just console
- Send to log aggregator
- Fluentd/Fluent Bit → Elasticsearch
- Retain for analysis

**Docker Logging Driver:**
```yaml
services:
  backend:
    logging:
      driver: "fluentd"
      options:
        fluentd-address: localhost:24224
        tag: backend
```

---

### Requirement 3: SLO/SLI Definition

> "Definition of the SLOs/SLIs that your system aims to meet (must be documented in docs/observability.md)."

**What to Define:**
- Key SLIs for your system
- Target SLOs
- Measurement method
- Time window

---

#### Example Document

**docs/observability.md:**
```markdown
# Observability - SLIs and SLOs

## Service Level Indicators (SLIs)

### Availability
- **Definition**: Percentage of successful HTTP requests
- **Measurement**: (2xx + 3xx responses) / (total requests)
- **Data Source**: Prometheus metric `http_requests_total`

### Latency
- **Definition**: 95th percentile response time
- **Measurement**: p95 of request duration
- **Data Source**: Prometheus histogram `http_request_duration_seconds`

### Error Rate
- **Definition**: Percentage of 5xx errors
- **Measurement**: (5xx responses) / (total requests)
- **Data Source**: Prometheus metric `http_requests_total{status=~"5.."}`

## Service Level Objectives (SLOs)

### Availability SLO
- **Target**: ≥ 99.5% over 30 days
- **Error Budget**: 0.5% = 3.6 hours/month
- **Alert Threshold**: < 99.5% over 1 hour

### Latency SLO
- **Target**: p95 < 500ms
- **Measurement Window**: 5 minutes
- **Alert Threshold**: p95 > 500ms for 10 minutes

### Error Rate SLO
- **Target**: < 1% errors
- **Measurement Window**: 5 minutes
- **Alert Threshold**: > 1% errors for 5 minutes

## Monitoring Implementation

### Metrics
- Prometheus scrapes `/metrics` endpoint every 15s
- Grafana dashboard: "System Overview"
- Alert rules configured in Prometheus

### Logging
- Structured JSON logs
- Shipped to Elasticsearch via Fluentd
- Kibana for log analysis

### Tracing
- OpenTelemetry instrumentation
- Traces exported to Jaeger
- 10% sampling in production
```

---

### Requirement 4: Backend Observability

> "Implementation of observability in the backend component (e.g., via OTLP / OpenTelemetry)."

**What to Implement:**
- OpenTelemetry integration
- Export traces, metrics, logs
- OTLP protocol
- Configure collectors

**Already Covered:**
See [OpenTelemetry Spring Boot Integration](#opentelemetry-spring-boot-integration) section.

**Checklist:**
- ✓ Add OpenTelemetry dependencies
- ✓ Configure OTLP endpoints
- ✓ Set service name
- ✓ Instrument custom spans (if needed)
- ✓ Test trace export
- ✓ Verify in Jaeger/backend

---

### Project Labeling

> "Use the following label: **category:observability**"

**GitHub Issues/PRs:**
Tag all observability work with `category:observability`.

**Why:**
- Track observability work
- Measure effort
- Sprint planning
- Documentation

---

### Elastic Cloud Trial

> "**Tools**: http://cloud.elastic.co/ | You can setup a trial of 14 days for this Sprint (only a member of the team should enable the trial)."

**Setup:**
1. One team member signs up
2. Create Elastic Cloud deployment
3. Get credentials
4. Configure application to send data
5. Use for 14 days (one sprint)

**What You Get:**
- Elasticsearch (logs, metrics)
- Kibana (visualization)
- APM (traces)
- Uptime monitoring

**Alternative (Free):**
- Self-hosted ELK stack
- Docker compose setup
- No trial limitations

---

# Study Tips and Exam Preparation

## Critical Concepts to Master

### Core Definitions (Essential!)

**Master These:**
1. **SLI, SLO, SLA**:
   - Definitions
   - Differences
   - Relationships
   - Examples
   - Calculations

2. **Error Budgets**:
   - Definition
   - Calculation
   - Purpose
   - Usage

3. **Fault Tolerance and Redundancy**:
   - Definitions
   - Relationship
   - Techniques

---

### Monitoring vs Observability

**Understand:**
- Definitions (precise)
- Key differences
- Complementary nature
- When to use each
- Impact together

**Can You Explain:**
- "Monitoring alerts WHEN, Observability explains WHY"
- Three pillars: Logs, Metrics, Traces
- Event-based foundation

---

### Anti-Patterns and Patterns

**5 Anti-Patterns (Know All):**
1. Tool Obsession
2. Monitoring-as-a-Job
3. Checkbox Monitoring
4. Monitoring as a Crutch
5. Manual Configuration

**For Each:**
- Problem description
- Why it's bad
- The solution
- Example

**4 Best Practice Patterns (Know All):**
1. Composable Monitoring
2. Monitor from User Perspective
3. Buy, Not Build
4. Continual Improvement

**For Each:**
- Concept
- Benefits
- Implementation
- When to use

---

### Statistics for Monitoring

**Core Concepts:**
- Mean vs Median (when to use each)
- Moving average
- Seasonality
- Percentiles (p50, p95, p99, p99.9)
- Why percentiles > mean for latency

**Can You:**
- Calculate percentiles?
- Explain flapping?
- Design time-windowed alerts?
- Justify p95 vs mean?

---

### Three Pillars Deep Dive

**Logs:**
- What they are
- When to use
- Structured vs unstructured
- Log levels (DEBUG, INFO, WARN, ERROR)

**Metrics:**
- Types (counter, gauge, histogram, summary)
- When to use
- Cardinality considerations
- TSDB concept

**Traces:**
- Distributed tracing purpose
- Span concept (all fields)
- Temporal vs graph view
- Latency analysis

**Understand:**
- All based on events
- Different representations
- Complementary
- Use together

---

### Tools Ecosystem

**Know Purpose of Each:**
- **Prometheus**: Metrics collection, TSDB
- **Grafana**: Visualization
- **ELK Stack**: Log aggregation (E, L, K roles)
- **OpenTelemetry**: Vendor-neutral instrumentation
- **Jaeger**: Distributed tracing
- **Fluentd/Fluent Bit**: Log forwarding

**Can You:**
- Match tool to use case?
- Explain composable architecture?
- Design observability stack?

---

## Key Numbers and Formulas

### Availability Calculations

**Availability Formula:**
```
Availability (%) = (Uptime / (Uptime + Downtime)) × 100
```

**Downtime Per Year:**
- 99.9% ("three nines") = 8.76 hours/year
- 99.99% ("four nines") = 52.6 minutes/year

**Example:**
- 30-day month = 720 hours
- 99.9% SLO → 0.1% downtime = 43.2 minutes allowed

---

### SLI Formulas

**Availability SLI:**
```
Availability = (Successful Requests / Total Requests) × 100%
```

**Error Rate SLI:**
```
Error Rate = (Failed Requests / Total Requests) × 100%
```

**Latency SLI:**
```
Latency = % of requests < threshold
```
or
```
Latency = p95/p99 response time
```

---

### Error Budget

**Error Budget Formula:**
```
Error Budget = 100% - SLO
```

**Example:**
- SLO: 99.9% uptime
- Error Budget: 0.1% downtime
- Per month: 0.1% × 720 hours = 43.2 minutes

**Burn Rate:**
```
Burn Rate = Actual Error Rate / Error Budget
```
- Burn Rate > 1 → Consuming budget faster than sustainable
- Burn Rate < 1 → Within budget

---

## Common Exam Question Types

### Comparison Questions

**Expect:**
- "Compare Monitoring vs Observability"
- "Difference between SLI, SLO, and SLA"
- "When to use logs vs metrics vs traces?"
- "Mean vs Median for latency monitoring"
- "Structured vs unstructured logs"

**How to Answer:**
- Create comparison table
- Highlight key differences
- Give examples
- Explain when to use each

---

### Scenario Questions

**Expect:**
- "System has high latency. How to investigate?"
  - Answer: Use traces to find bottleneck
- "Need to alert on API errors. Design the alert."
  - Answer: Time-windowed, SLO-based, user-centric
- "Startup with limited resources. Which monitoring approach?"
  - Answer: SaaS (Pattern #3: Buy Not Build)
- "Alerts firing constantly. What anti-pattern?"
  - Answer: Checkbox Monitoring or Manual Configuration

---

### Conceptual Questions

**Expect:**
- "What is an error budget and why is it useful?"
- "Explain the three pillars of observability"
- "What is distributed tracing and why needed?"
- "Why are percentiles better than mean for latency?"
- "What is seasonality in monitoring?"

**How to Answer:**
- Clear definition
- Practical explanation
- Real example
- Benefits/trade-offs

---

### Design Questions

**Expect:**
- "Design SLIs/SLOs for an e-commerce API"
- "Design monitoring stack for microservices"
- "Design alert for payment system reliability"
- "How to implement observability in Spring Boot?"

**How to Answer:**
- User-centric approach
- Justify choices
- Consider trade-offs
- Practical implementation

---

### Calculation Questions

**Expect:**
- "99.9% SLO for 30 days. How much downtime allowed?"
  - Answer: 0.1% × 720h = 43.2 minutes
- "1000 requests, 990 successful. What's availability SLI?"
  - Answer: 990/1000 = 99%
- "SLO 99.95%, actual 99.8%. Error budget remaining?"
  - Answer: Budget = 0.05%, consumed = 0.2%, over budget!

---

## Important Distinctions

### SLI vs SLO vs SLA

| Aspect | SLI | SLO | SLA |
|--------|-----|-----|-----|
| **What** | Measurement | Target | Contract |
| **Type** | Metric | Goal | Promise |
| **Audience** | Engineers | Internal team | Customers |
| **Example** | 99.5% uptime | ≥ 99.9% uptime | ≥ 99.5% or credit |
| **Consequence** | None | Engineering focus | Financial penalty |

---

### Monitoring vs Observability

| Aspect | Monitoring | Observability |
|--------|-----------|---------------|
| **Question** | What? When? | Why? |
| **Purpose** | Alert on issues | Diagnose issues |
| **Data** | Aggregated metrics | Detailed telemetry |
| **Approach** | Known issues | Unknown unknowns |
| **Example** | "Latency high alert" | "Why is latency high?" |

---

### Logs vs Metrics vs Traces

| Aspect | Logs | Metrics | Traces |
|--------|------|---------|--------|
| **Format** | Text/JSON | Numbers | Spans |
| **Cardinality** | High | Low-Medium | High |
| **Storage** | Large | Small | Large |
| **Use Case** | Debugging | Dashboards/Alerts | Latency analysis |
| **Example** | Error message | Request rate | Request path |
| **Query** | Full-text search | Aggregation | Trace ID lookup |

---

### Mean vs Median vs Percentiles

| Metric | Pros | Cons | Use When |
|--------|------|------|----------|
| **Mean** | Simple | Skewed by outliers | Uniform distribution |
| **Median** | Robust | Hides outliers | Typical user |
| **p95** | Shows most users | Misses 5% | SLOs |
| **p99** | Shows edge cases | Expensive to compute | Critical paths |

---

## Practical Skills Checklist

### Implementation Skills

**Can You:**
- ✓ Add OpenTelemetry to Spring Boot app?
- ✓ Configure structured logging (JSON)?
- ✓ Write Prometheus metrics?
- ✓ Create Grafana dashboard?
- ✓ Define SLIs and SLOs?
- ✓ Design health check endpoint?
- ✓ Export traces to Jaeger?
- ✓ Query logs in Elasticsearch?
- ✓ Design effective alerts?

---

### Tool Skills

**Can You:**
- ✓ Write PromQL queries?
- ✓ Create Grafana panels?
- ✓ Search logs in Kibana?
- ✓ Navigate Jaeger traces?
- ✓ Configure Prometheus scrape targets?
- ✓ Set up Alertmanager?
- ✓ Use Fluentd for log forwarding?
- ✓ Configure OpenTelemetry Collector?

---

### Design Skills

**Can You:**
- ✓ Choose appropriate SLIs for a service?
- ✓ Set realistic SLOs?
- ✓ Calculate error budgets?
- ✓ Design monitoring architecture?
- ✓ Choose between SaaS vs self-hosted?
- ✓ Identify monitoring anti-patterns?
- ✓ Apply best practice patterns?
- ✓ Design user-centric alerts?

---

## Real-World Application

### Designing SLIs/SLOs for E-commerce API

**Scenario:**
E-commerce REST API for product catalog and checkout.

**SLI Choices:**

**1. Availability:**
```
SLI: (HTTP 2xx + 3xx) / Total Requests
SLO: ≥ 99.5% over 30 days
Why: Users need to access products
```

**2. Latency:**
```
SLI: p95 response time
SLO: p95 < 500ms
Why: Fast browsing experience
```

**3. Checkout Success Rate:**
```
SLI: Successful checkouts / Checkout attempts
SLO: ≥ 99.9%
Why: Revenue-critical, higher bar
```

**4. Search Quality:**
```
SLI: Searches with results / Total searches
SLO: ≥ 95%
Why: User experience, but some searches legitimately empty
```

---

### Investigating a Latency Issue

**Problem:**
API p99 latency spiked from 200ms to 2000ms.

**Investigation Steps:**

**1. Check Metrics (Prometheus/Grafana):**
- When did spike start?
- Which endpoints affected?
- Error rate increased?

**2. Correlate with Logs (Elasticsearch/Kibana):**
- Any error logs at that time?
- Warnings about slow queries?
- Connection pool exhausted?

**3. Analyze Traces (Jaeger):**
- Get example slow trace
- Identify bottleneck span
- Database query taking 1.8s → Found it!

**4. Root Cause:**
- Database migration running
- Locking table
- Queries waiting

**5. Resolution:**
- Pause migration
- Run during maintenance window
- Add index to prevent future locks

**Takeaway:**
All three pillars needed:
- Metrics: Detected problem
- Logs: Provided context
- Traces: Identified bottleneck

---

### Designing Alerts

**Bad Alert:**
```
Alert: CPU > 80%
Problem:
- Not user-centric
- May not impact users
- Flaps
```

**Good Alert:**
```
Alert: API Checkout p95 Latency > 1s for 5 minutes
Why Good:
- User-centric (checkout)
- Time-windowed (5 min)
- Tied to SLO
- Actionable
- Clear impact

Runbook:
1. Check Jaeger for slow traces
2. Look at database query times
3. Check connection pool
4. Scale if needed
```

---

## Connections to Other Slides

### Integration with Slide 04 (CI/CD)

**Observability in CI/CD:**
- Run tests with observability enabled
- Validate metrics exported
- Check dashboard rendering
- Test alerts fire correctly

**Pipeline:**
```yaml
- name: Run Tests with Observability
  run: |
    export OTEL_EXPORTER_OTLP_ENDPOINT=http://collector:4318
    ./run-tests.sh

- name: Validate Metrics
  run: |
    curl prometheus:9090/api/v1/query?query=http_requests_total
    # Expect: metrics present
```

---

### Integration with Slide 05 (Delivery Strategies)

**Observability Enables:**
- **Canary Releases**: Monitor canary metrics separately
- **Blue/Green**: Compare blue vs green observability
- **Feature Flags**: Track feature usage
- **A/B Testing**: Measure experiment metrics

**Example:**
```
Canary Deployment:
├─ 5% traffic to new version
├─ Monitor SLIs separately
│   ├─ Canary error rate
│   └─ Production error rate
├─ Compare metrics
└─ Rollout or rollback based on data
```

---

### Integration with Slide 06 (Testing)

**Testing and Observability:**
- Observability IS testing in production
- Feature toggles + observability = safe experimentation
- Performance tests tracked via metrics
- Chaos tests monitored via observability

**Example:**
```
Chaos Test:
1. Kill random pod
2. Observe:
   ├─ Metrics: Request success rate
   ├─ Logs: Error messages
   └─ Traces: Failover path
3. Validate: System self-heals
```

---

### Integration with Slide 07 (Infrastructure as Code)

**IaC + Observability:**
- Monitoring configured as code
- Dashboards in Terraform
- Alert rules version controlled
- Consistent across environments

**Example:**
```hcl
# Terraform: Prometheus alert rule
resource "prometheus_alert_rule" "api_latency" {
  name = "HighAPILatency"
  expr = "histogram_quantile(0.95, http_request_duration_seconds) > 0.5"
  for  = "5m"
  annotations = {
    summary = "API latency p95 > 500ms"
  }
}
```

---

## Final Exam Preparation Checklist

### Core Knowledge
- ✓ SLI, SLO, SLA definitions and differences
- ✓ Error budget concept and calculation
- ✓ Monitoring vs Observability (clear distinction)
- ✓ Three pillars: Logs, Metrics, Traces
- ✓ Five monitoring anti-patterns (all details)
- ✓ Four best practice patterns (all details)
- ✓ Statistics: mean, median, percentiles, seasonality
- ✓ End-users' expectations (availability, latency, reliability)

### Technical Knowledge
- ✓ Distributed tracing (spans, traces)
- ✓ Span structure (all fields)
- ✓ Graph vs temporal view
- ✓ Tools ecosystem (Prometheus, Grafana, ELK, OTel, Jaeger)
- ✓ Structured logging (why and how)
- ✓ Health checks
- ✓ OpenTelemetry integration

### Practical Skills
- ✓ Design SLIs for a service
- ✓ Set appropriate SLOs
- ✓ Calculate error budgets
- ✓ Design effective alerts
- ✓ Choose right tool for job
- ✓ Implement observability in Spring Boot
- ✓ Analyze traces for bottlenecks

### Formulas and Calculations
- ✓ Availability formula
- ✓ Error budget formula
- ✓ SLI calculations
- ✓ Downtime from SLO (99.9%, 99.99%)
- ✓ Percentile concepts

### Conceptual Understanding
- ✓ Why observability matters (business value)
- ✓ User-centric vs infrastructure-centric monitoring
- ✓ Buy vs build progression
- ✓ Continual improvement mindset
- ✓ Event-based foundation
- ✓ Composable architecture

---

# Summary

## Key Takeaways

### Reliability Engineering Foundation
- **SLIs**: Measure what matters (availability, latency, errors)
- **SLOs**: Set targets (balance reliability and velocity)
- **SLAs**: Promise customers (with consequences)
- **Error Budgets**: Quantify acceptable failures (innovation budget)
- **Hierarchy**: All built on monitoring and observability

### Monitoring and Observability
- **Monitoring**: Alerts WHEN (metrics, dashboards, alerts)
- **Observability**: Explains WHY (logs, metrics, traces)
- **Complementary**: Need both (detect and diagnose)
- **User-Centric**: Monitor from user perspective
- **Three Pillars**: Logs, Metrics, Traces (event-based)

### Anti-Patterns to Avoid
1. **Tool Obsession**: Define needs first, then tools
2. **Monitoring-as-a-Job**: Shared responsibility, not centralized
3. **Checkbox Monitoring**: High-signal alerts, not noise
4. **Monitoring as Crutch**: Fix root causes, not just alert more
5. **Manual Configuration**: Automate and version control

### Best Practices to Follow
1. **Composable**: Specialized tools working together
2. **User Perspective**: Monitor what users experience
3. **Buy Not Build**: SaaS → FOSS → Custom (progress gradually)
4. **Continual Improvement**: Journey, not destination (re-architect every 2-3 years)

### Statistics for Better Monitoring
- **Percentiles > Mean**: For latency and skewed distributions
- **Time Windows**: Evaluate over time, not single samples
- **Seasonality**: Context-aware alerting
- **Smart Alerts**: User impact, not raw metrics

### Three Pillars Deep Dive
- **Logs**: Events for debugging (structured, JSON)
- **Metrics**: Numbers for dashboards (low cardinality)
- **Traces**: Request flows for latency analysis (distributed systems)
- **Together**: Complete observability

### Distributed Tracing
- **Spans**: Operations with timing (parent-child relationships)
- **Traces**: End-to-end request journey (visualized as graphs/timelines)
- **Purpose**: Find bottlenecks in microservices
- **Essential**: For distributed systems

### Tools Ecosystem
- **Metrics**: Prometheus (collection), Grafana (visualization)
- **Logs**: ELK Stack (Elasticsearch, Logstash, Kibana)
- **Traces**: Jaeger (distributed tracing)
- **Unified**: OpenTelemetry (vendor-neutral framework)
- **Forwarding**: Fluentd/Fluent Bit (log aggregation)

### Practical Implementation
- **OpenTelemetry**: Industry standard for instrumentation
- **Spring Boot**: Easy integration with actuator + OTel starter
- **Structured Logging**: JSON format, machine-readable
- **Health Checks**: Enable auto-recovery
- **SLO Documentation**: Define and track objectives
- **Configuration as Code**: Version and automate

### Project Success
- Implement all three pillars (logs, metrics, traces)
- Define meaningful SLIs/SLOs
- Use structured logging
- Add health checks
- Integrate OpenTelemetry
- Document in `docs/observability.md`
- Enable testing in production

---

# End of Study Guide

This comprehensive guide covers all material from ES Slide 08: Monitoring and Observability. Use it to:
- Understand reliability engineering fundamentals
- Master monitoring and observability concepts
- Learn anti-patterns and best practices
- Understand statistical approaches
- Explore the three pillars deeply
- Prepare for exams thoroughly
- Implement in your project successfully
- Reference during development

**Remember:**

> "You can't improve what you can't measure. You can't measure what you can't observe."

**Three Pillars:**
- **Logs**: Tell stories (what happened)
- **Metrics**: Show trends (how much, how fast)
- **Traces**: Reveal paths (where time spent)

**The Goal:**
Reliable systems that meet SLOs, delight users, and enable confident innovation through data-driven decisions.

**Final Wisdom:**
> "Monitoring tells you that something is wrong. Observability tells you why."

Good luck with your studies, implementation, and exam!

---

**Generated for ES 2025/2026 - Monitoring and Observability (Slide 08)**
