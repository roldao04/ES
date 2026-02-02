# Software Engineering - Study Guide (Slide 07)
## Infrastructure as Code (IaC) - Complete Exam Preparation Guide

---

# Table of Contents

1. [Deployment History](#deployment-history)
   - [CAPEX vs OPEX](#capex-vs-opex)
   - [Pets vs Cattle Servers](#pets-vs-cattle-servers)
   - [Pre-Cloud Era](#pre-cloud-era)
   - [Cloud Era](#cloud-era)
   - [Configuration Problems](#configuration-problems)
2. [DevOps Recap](#devops-recap)
3. [Infrastructure as Code (IaC)](#infrastructure-as-code-iac)
   - [What is IaC?](#what-is-iac)
   - [IaC Tools Overview](#iac-tools-overview)
   - [Benefits of IaC](#benefits-of-iac)
4. [IaC Tool Categories](#iac-tool-categories)
   - [Docker (Containerization)](#docker-containerization)
   - [Ad-hoc Scripts](#ad-hoc-scripts)
   - [Configuration Management Tools](#configuration-management-tools)
   - [Server Templating Tools](#server-templating-tools)
   - [Orchestration Tools](#orchestration-tools)
   - [Provisioning Tools](#provisioning-tools)
5. [Terraform 101](#terraform-101)
   - [Overview and Features](#overview-and-features)
   - [Declarative Infrastructure](#declarative-infrastructure)
   - [State Management](#state-management)
   - [Variables and Outputs](#variables-and-outputs)
   - [Resource Dependencies](#resource-dependencies)
   - [Terraform Workflow](#terraform-workflow)
6. [Scalability & Availability](#scalability--availability)
   - [Scalability Concepts](#scalability-concepts)
   - [Load Balancing](#load-balancing)
   - [Availability](#availability)
7. [Practical Implementation](#practical-implementation)
8. [Study Tips and Exam Preparation](#study-tips-and-exam-preparation)

---

# Deployment History

## CAPEX vs OPEX

### Two Financial Models for Infrastructure

Understanding the financial models helps explain why cloud computing became dominant.

---

### CAPEX (Capital Expenditure)

**Definition:**
> "**Upfront investment** in physical infrastructure"

---

#### Characteristics

**1. Large Initial Cost:**
- Buy servers upfront
- Pay before using
- Major financial commitment
- Budget approval needed

**2. Fixed Assets:**
- Physical ownership
- Balance sheet asset
- Depreciation over time
- Tax implications

**3. Long-term Expenses:**
- Maintenance costs
- Power and cooling
- Staff to manage
- Facility costs

**4. Ownership of Infrastructure:**
- You own the hardware
- Full control
- Full responsibility
- Full risk

---

### OPEX (Operational Expenditure)

**Definition:**
> "**Pay-as-you-go model**"

---

#### Characteristics

**1. Operational Expenses:**
- Monthly/hourly billing
- Part of operating budget
- No large upfront cost
- Easy to justify

**2. Flexible Scaling Costs:**
- Pay for what you use
- Scale up → costs increase
- Scale down → costs decrease
- Aligned with revenue

**3. No Ownership Required:**
- Rent infrastructure
- No assets on balance sheet
- Provider maintains hardware
- Provider handles upgrades

**4. No Depreciation:**
- Not an asset
- Simple accounting
- Predictable costs
- Operational simplicity

---

### Comparison Table

| Aspect | CAPEX | OPEX |
|--------|-------|------|
| **Payment** | Large upfront | Monthly/hourly |
| **Ownership** | You own it | Provider owns |
| **Scaling** | Buy more hardware | Add/remove resources |
| **Risk** | Hardware obsolescence | Provider responsibility |
| **Flexibility** | Low (stuck with capacity) | High (scale dynamically) |
| **Cash Flow** | Large initial outlay | Spread over time |
| **Accounting** | Capital asset | Operating expense |

---

### Business Impact

**CAPEX Model (Traditional):**
- High barrier to entry
- Risk of over/under provisioning
- Long procurement cycles
- Difficult for startups

**OPEX Model (Cloud):**
- Low barrier to entry
- Right-size resources
- Instant provisioning
- **Easier for startups** ← Key advantage

---

## Pets vs Cattle Servers

### The Metaphor

This metaphor revolutionized how we think about servers.

---

## Pets Servers

### Characteristics

**1. Individually Named and Cared For:**
> "Each server has a **unique name** (like 'db-server-prod-01' or 'WebServerJohn')"

**Examples:**
- `db-server-prod-01`
- `WebServerJohn`
- `email-server-main`
- Personal, meaningful names

---

**2. Lovingly Maintained:**
> "You **diagnose and manually fix** each problem"

**What This Means:**
- SSH into server
- Debug issues manually
- Apply patches individually
- Custom troubleshooting per server

---

**3. Irreplaceable:**
> "Server failure causes **crisis** and **significant downtime**"

**Why Crisis:**
- Only one like it
- Configuration not documented
- Years of manual changes
- Cannot easily recreate
- Loss is devastating

---

**4. Manually Configured:**
> "**Hand-crafted** with custom settings and accumulated tweaks"

**Reality:**
- Configured over months/years
- Snowflake configuration
- Undocumented changes
- Tribal knowledge required

---

**5. Long-Lived:**
> "Run for **years**, becoming **difficult to replicate**"

**The Problem:**
- Configuration drift
- Unknown state
- Fear of touching it
- "If it ain't broke, don't touch it"

---

**6. You Know When They're Sick:**
> "Problems trigger **immediate all-hands response**"

**Team Response:**
- Page the on-call engineer
- Emergency meeting
- All hands on deck
- Work through the night

---

## Cattle Servers

### Characteristics

**1. Numbered, Not Named:**
> "Servers are **'web-server-001'**, **'web-server-002'**"

**Examples:**
- `web-server-001`
- `web-server-002`
- `web-server-003`
- Generic, sequential identifiers

**Philosophy:**
- No emotional attachment
- Interchangeable
- Anonymous

---

**2. Disposable:**
> "**Terminate and replace** rather than fix problems"

**Approach:**
- Server has issue?
- Kill it
- Spin up new one
- Move on

**Benefits:**
- No troubleshooting time
- Always fresh state
- Prevents configuration drift

---

**3. Automatically Provisioned:**
> "Created from **templates/code** in minutes"

**Process:**
- Template defines server
- Code provisions server
- Automated, repeatable
- Consistent every time

**Speed:**
- Minutes, not days/weeks
- On-demand
- No manual setup

---

**4. Ephemeral:**
> "Expected to be **short-lived** for easy updates"

**Lifecycle:**
- Spin up
- Run for days/weeks
- Terminate
- Replace with new version

**Benefits:**
- Always up-to-date
- No legacy baggage
- Clean slate regularly

---

**5. Scalable:**
> "**Add or remove servers automatically** as needed"

**Dynamic Scaling:**
- Traffic increases → add servers
- Traffic decreases → remove servers
- Automatic response
- No human intervention

---

**6. Self-Healing:**
> "System **auto-replaces failures** without human intervention"

**Automation:**
- Health checks monitor servers
- Failure detected
- Unhealthy server terminated
- New server provisioned automatically
- No human involved

---

### The Paradigm Shift

**Pets Philosophy:**
- "These servers are precious"
- "We must keep them alive"
- "Expert knowledge required"

**Cattle Philosophy:**
- "Servers are disposable"
- "Replace, don't repair"
- "Automation handles everything"

**Modern Cloud:**
Cattle approach is the standard.

---

## Pre-Cloud Era

### On-Premise Model

**Visual Description:** The slides show characteristics of pre-cloud infrastructure.

---

### Characteristics

**1. CAPEX:**
- Large upfront investment
- Buy before you use
- Financial commitment

**2. Pet Servers:**
- Individually managed
- Long-lived
- Irreplaceable

**3. Buy Physical Servers:**
- Dell, HP, IBM servers
- Racks and data centers
- Physical procurement

**4. High Initial Cost:**
- Servers expensive
- Network equipment
- Cooling and power
- Facility costs

**5. Difficult to Scale:**
- Buy new hardware
- Install and configure
- Weeks/months to add capacity
- Risk of over/under provisioning

**6. Manual Configuration:**
- Hand-configured each server
- No automation
- Snowflake servers
- Configuration drift

---

### The Problems

**Capacity Planning Nightmare:**
- Estimate peak load
- Buy for peak
- Waste money on idle resources
- Or under-provision and crash

**Slow Response to Change:**
- Need more servers? Wait weeks
- Market opportunity? Too slow
- Competitor faster? Lose market

**Operational Burden:**
- Large ops teams
- Manual processes
- Heroic efforts during outages
- Burnout common

---

## Cloud Era

### Cloud Model

**Visual Description:** The slides show the transformation to cloud infrastructure.

---

### Characteristics

**1. OPEX:**
- Pay-as-you-go
- Monthly billing
- Operational expenses
- No large upfront cost

**2. Cattle Servers:**
- Disposable instances
- Auto-provisioned
- Self-healing
- Scalable

**3. Pay-per-Usage:**
- Only pay for what you use
- Scale up = costs increase
- Scale down = costs decrease
- Granular billing (per hour/second)

**4. Provisioning On-the-Fly:**
- API calls provision servers
- Minutes, not weeks
- Instant capacity
- No procurement delay

**5. Scalability On-Demand:**
- Need more servers? Launch them
- Need fewer? Terminate them
- Automatic scaling
- Respond to traffic in real-time

**6. Easier for Startups:**
- No upfront investment
- Start small, grow as needed
- Experiment cheaply
- Fail fast without huge losses

---

### The Cloud Promise

**Speed:**
- Instant provisioning
- Rapid iteration
- Fast time to market

**Flexibility:**
- Scale up and down
- Try different configurations
- Global deployment

**Cost Efficiency:**
- Pay for actual usage
- No wasted capacity
- Predictable costs

---

### Not All Days Are Sunny Days

**Visual Description:** The slides reference challenges even in the cloud era.

**Reality Check:**
- Cloud solves many problems
- But introduces new challenges
- Manual configuration still needed
- New complexity emerges

**Foreshadowing:**
This leads us to the configuration problem...

---

## Configuration Problems

### Manual Configuration Persists

> "Even when using **cloud solutions**, it is needed **manual configuration**."

**The Reality:**
- Cloud provides infrastructure
- But you still configure it
- Often manually through web console
- Click, click, click...

---

### Problem 1: Snowflake Servers

> "**Snowflake servers**, that diverge over time and become **hard to replicate**"

---

#### What Are Snowflake Servers?

**Definition:**
Like snowflakes, no two are exactly alike.

**How They Form:**
1. Start with standard configuration
2. Manual change #1
3. Manual change #2
4. ...
5. Manual change #100
6. Now unique, undocumented server

**Why Called Snowflakes:**
- Each server slightly different
- Configuration drift over time
- Unique, irreproducible state
- Beautiful but problematic

---

#### The Problems

**Cannot Replicate:**
- Try to create identical server
- Missing some manual step
- Different behavior
- Subtle bugs

**Cannot Scale:**
- Need 10 more servers
- Can't copy snowflake reliably
- Each new server potentially different
- Inconsistent fleet

**Cannot Debug:**
- Works on server A
- Fails on server B
- Why? Who knows!
- Different configurations

**Cannot Recover:**
- Server crashes
- Rebuild from what?
- Lost all manual changes
- Different server now

---

### Problem 2: No Version Control

> "**No versioning control** making **impossible to rollback**"

---

#### The Problem

**Configuration Not in Git:**
- Changes made via web console
- Or manual commands
- No record of what changed
- No commit history

**Cannot Rollback:**
- Something breaks
- Want to undo last change
- What WAS the last change?
- No way to know!

**Cannot Audit:**
- Who changed what?
- When?
- Why?
- No trail

**Cannot Review:**
- No code review for infrastructure changes
- No approval process
- No testing
- Hope for the best

---

### The Solution

**Visual Description:** The slides reveal the solution:

> "Solution: **Infrastructure as Code**"

**The Answer:**
- Treat infrastructure like code
- Version controlled
- Automated
- Reproducible
- Reviewable

---

# DevOps Recap

## DevOps Movement

### What is DevOps?

> "**Movement**: Culture, automation, measurement and sharing (**CAMS**)"

---

### CAMS Framework

**C - Culture:**
- Collaboration over silos
- Shared responsibility
- Blameless postmortems

**A - Automation:**
- Automate everything
- Reduce toil
- Increase consistency

**M - Measurement:**
- Metrics and monitoring
- Data-driven decisions
- Continuous improvement

**S - Sharing:**
- Knowledge sharing
- Open communication
- Cross-functional teams

---

### DevOps Goals

**1. Join Developer Team with Operator Team:**
> "Join the **Developer Team** with the **Operator Team**"

**Breaking Down Walls:**
- No more "throw over the wall"
- Shared ownership
- Collaboration

---

**2. Combat "It Works on My Machine":**
> "Combat the **'It works on my machine syndrome!'**"

**The Problem:**
- Dev: "Works on my laptop"
- Ops: "Doesn't work in production"
- Hours of debugging

**The Solution:**
- Same environment everywhere
- Containers and IaC
- Reproducible deployments

---

**3. Enhance Software Delivery:**
> "Enhance **Software delivery**"

**How:**
- Faster deployments
- More reliable releases
- Better quality
- Happier teams

---

## DevOps Operate Tools

### Focus: Running Production Systems

> "**Running and maintaining applications** in production environments"

**Responsibilities:**
- Keep systems up
- Monitor performance
- Respond to incidents
- Maintain infrastructure

---

### Goals

**1. Ensuring System Reliability:**
- High availability
- Fault tolerance
- Disaster recovery

**2. Performance:**
- Fast response times
- Efficient resource usage
- Scalability

**3. Availability:**
- Uptime targets (99.9%, 99.99%)
- Redundancy
- No single point of failure

---

### Managing Infrastructure

> "**Managing infrastructure** and responding to incidents"

**Infrastructure Management:**
- Provisioning servers
- Configuring networks
- Managing databases
- Scaling resources

**Incident Response:**
- Alerts and monitoring
- On-call rotations
- Debugging and fixes
- Postmortem analysis

---

### Visual Reference

**Visual Description:** Slide 15 shows a DevOps diagram illustrating the continuous cycle of Plan → Code → Build → Test → Release → Deploy → Operate → Monitor → back to Plan.

**The DevOps Loop:**
- Continuous cycle
- No handoffs
- Shared responsibility
- Infrastructure as Code fits in this loop

---

# Infrastructure as Code (IaC)

## What is IaC?

### Definition

> "Infrastructure as Code (IaC) is the idea of **writing and executing code** to **define, deploy, update and destroy** your infrastructure"

---

### Core Concept

**Infrastructure as Text Files:**
> "Infrastructure defined as **text files**"

**What This Means:**
- Your infrastructure is code
- Servers, networks, databases
- All defined in files
- Human-readable, machine-executable

**Example:**
```hcl
# Terraform code defining a server
resource "aws_instance" "web" {
  ami           = "ami-12345"
  instance_type = "t2.micro"
}
```

Instead of:
- Click "Create Instance" in AWS console
- Select AMI from dropdown
- Choose instance type
- Click "Launch"

---

### Key Characteristics

**1. Version Control (Git):**
> "**Version Control (Git)**"

**Benefits:**
- Every change tracked
- Can rollback to any version
- Commit messages explain why
- Branching and merging
- Code review process
- Audit trail

**Example:**
```
commit 3a7b2c1
Author: Alice
Date: Mon Jan 20 10:30:00 2026

Add production database server
- RDS instance with 100GB storage
- Multi-AZ for high availability
```

---

**2. Declarative:**
> "**Declarative**"

**What You Want, Not How:**
- Describe desired end state
- Not step-by-step instructions
- Terraform figures out how

**Example:**

**Declarative (IaC):**
```hcl
resource "aws_instance" "web" {
  count = 5  # I want 5 servers
}
```

**Imperative (Script):**
```bash
for i in 1 2 3 4 5; do
  aws ec2 run-instances ...
  wait for server to start
  configure server
done
```

**Advantage:**
- Simpler to understand
- Less error-prone
- Idempotent by design

---

**3. Idempotent:**
> "**Idempotent**"

**Definition:**
Can run multiple times, same result.

**Example:**

**Idempotent:**
```hcl
resource "aws_instance" "web" {
  count = 5
}
```

Run once: 5 servers created
Run again: Already 5 servers, nothing changes
Run 100 times: Still 5 servers

**Not Idempotent:**
```bash
aws ec2 run-instances --count 5
```

Run once: 5 servers
Run again: 5 MORE servers (now 10 total!)
Run 100 times: 500 servers!!

**Why Important:**
- Safe to re-run
- No accidental duplication
- Convergence to desired state

---

**4. Automatic and Reproducible:**
> "**Automatic and Reproducible**"

**Automatic:**
- No manual steps
- Execute and done
- Consistent every time

**Reproducible:**
- Same code → same infrastructure
- Dev environment = Prod environment
- Can recreate from scratch
- Disaster recovery simplified

---

### The Question

**Visual Description:** The slides pose a question:

> "**What's the purpose of this when we already have Docker?**"

**Good Question!**
This leads us to understand the different roles...

---

## IaC Tools Overview

### The Ecosystem

Infrastructure as Code encompasses multiple tool categories:

1. Containerization (Docker)
2. Ad-hoc Scripts
3. Configuration Management
4. Server Templating
5. Orchestration
6. Provisioning

Each solves different problems.

---

# IaC Tool Categories

## Docker (Containerization)

### What Docker Does

> "Docker is about **running your app**:"

---

### Capabilities

**1. Creates Containers:**
> "It creates **containers**: **self-contained environments** that hold your app and its dependencies."

**Container Contents:**
- Your application code
- Runtime (Python, Node.js, Java)
- Libraries and dependencies
- Configuration files
- Everything needed to run

**Self-Contained:**
- No external dependencies
- Isolated from host
- Portable

---

**2. Ensures Same Environment:**
> "It **ensures the same environment on any host**."

**The Promise:**
- Runs on your laptop? ✓
- Runs on colleague's laptop? ✓
- Runs in staging? ✓
- Runs in production? ✓

**No More:**
- "Works on my machine"
- Environment differences
- Missing dependencies

---

**3. Build → Ship → Run Consistency:**
> "It's great for **build → ship → run consistency**."

**The Workflow:**
1. **Build**: Create container image
2. **Ship**: Push to registry (Docker Hub, etc.)
3. **Run**: Deploy anywhere

**Consistency:**
Same image everywhere, guaranteed identical execution.

---

### Example

> "You can run a web app in a Docker container with its specific version of **Python, Nginx, and libraries**, without caring about the host OS."

**Scenario:**
- Your app needs Python 3.9
- Colleague's laptop has Python 3.11
- Production server has Python 3.8
- No problem! Container has its own Python 3.9

**Benefits:**
- Version conflicts eliminated
- Dependency hell solved
- Portable across environments

---

### Docker's Scope

**What Docker IS:**
- Application packaging
- Runtime environment
- Build → Ship → Run

**What Docker IS NOT:**
- Creating the infrastructure (servers, networks)
- Provisioning cloud resources
- Managing multiple hosts (at scale)

**You Still Need:**
- Servers to run containers on
- Networks for containers to communicate
- Load balancers to distribute traffic
- Storage for data

**That's Where Other IaC Tools Come In!**

---

## Ad-hoc Scripts

### The Straightforward Approach

> "The most **straightforward way**: Writing a simple script in your favorite scripting language (Bash, Python) to define each step to execute"

---

### How It Works

**Example Bash Script:**
```bash
#!/bin/bash
# deploy.sh

# Create server
aws ec2 run-instances --image-id ami-12345 --count 1

# Wait for server
sleep 60

# Install software
ssh ubuntu@server 'sudo apt-get update && sudo apt-get install nginx'

# Deploy app
scp app.tar.gz ubuntu@server:/var/www/
```

**Simple and Direct:**
- Step-by-step commands
- Familiar syntax
- Easy to understand

---

### Main Advantage

> "The main advantage is you can **use your preferred language**"

**Flexibility:**
- Know Bash? Use Bash
- Know Python? Use Python
- Know Ruby? Use Ruby
- Use language you're comfortable with

**No New Tools:**
- No new syntax to learn
- Standard programming constructs
- Familiar debugging

---

### Main Disadvantage

> "The main disadvantage is you can **use your preferred language**, provoking **inconsistency**"

**The Problem:**
- Team member A uses Bash
- Team member B uses Python
- Team member C uses Ruby
- No consistency

**Collaboration Issues:**
- Can't read each other's scripts
- Different patterns and styles
- Harder to maintain
- Knowledge silos

---

### The Spaghetti Problem

> "More ad-hoc scripts generally means **more spaghetti code to maintain**."

**What Happens:**
1. Start with simple script
2. Add feature
3. Add another feature
4. Add error handling
5. Add retry logic
6. Add logging
7. Now: 500-line bash script nobody understands

**Characteristics:**
- Poor error handling
- No idempotence
- Hard to test
- Brittle and fragile
- Maintenance nightmare

---

### When to Use

**Good For:**
- One-off tasks
- Simple automation
- Quick prototypes
- Learning

**Bad For:**
- Production infrastructure
- Team collaboration
- Long-term maintenance
- Critical systems

---

## Configuration Management Tools

### The Common Tools

> "The most common tools: **Chef, Puppet, Ansible**"

---

### Purpose

> "Designed to **install and manage software** on **existing servers**"

**Focus:**
- Server already exists
- Install software on it
- Configure the software
- Maintain desired state

**Examples:**
- Install and configure Nginx
- Set up database server
- Configure monitoring agents
- Manage user accounts

---

### Key Features

**1. Enforces Consistent Coding Conventions:**
> "Enforces **consistent coding conventions** including documentation, file layout, and secrets management"

**Standards:**
- Structure code consistently
- Document configurations
- Secure secret handling
- Best practices enforced

**Benefits:**
- Team consistency
- Easier onboarding
- Maintainable code
- Secure by default

---

**2. Idempotence:**
> "The main advantage is **idempotence** - code that works correctly **no matter how many times you run it**"

**Example (Ansible):**
```yaml
- name: Install Nginx
  apt:
    name: nginx
    state: present
```

**Run 1:** Nginx not installed → Install it
**Run 2:** Nginx installed → Do nothing
**Run 100:** Nginx installed → Still do nothing

**Benefits:**
- Safe to re-run
- Convergence to desired state
- Self-healing

---

**3. Built for Distribution:**
> "Built for distribution - designed to **manage large numbers of remote servers in parallel**"

**Capabilities:**
- SSH to 100 servers simultaneously
- Apply configuration in parallel
- Inventory management
- Grouping and targeting

**Example:**
```yaml
# Apply to all web servers
hosts: webservers
tasks:
  - install nginx
  - deploy app
```

**Benefits:**
- Scale to thousands of servers
- Consistent configuration
- Parallel execution = fast

---

### Main Disadvantage

> "The main disadvantage is **still requires managing the servers themselves**"

**The Gap:**
- Configuration management configures servers
- But doesn't create servers
- Doesn't create networks
- Doesn't create load balancers

**You Still Need:**
- To provision infrastructure first
- Another tool for that (Terraform, CloudFormation)
- Two-tool approach

**Typical Pattern:**
1. Terraform creates servers
2. Ansible configures servers

---

### Tool Comparison

**Chef:**
- Ruby-based DSL
- Pull model (agent pulls config)
- Complex but powerful

**Puppet:**
- Declarative language
- Pull model
- Large enterprise adoption

**Ansible:**
- YAML-based
- Push model (agentless, SSH)
- Simpler, more popular now

---

## Server Templating Tools

### The Common Tools

> "The most common tools: **Docker, Packer, Vagrant**"

---

### Purpose

> "Create an **image** that captures a **fully self-contained snapshot** of the OS, software, and files"

**What's an Image:**
- Complete system snapshot
- OS + applications + configuration
- Ready to boot and run
- Like a photo of your server

---

### Two Main Types

> "Two main types: **Virtual Machines** (VMware, VirtualBox) and **Containers** (Docker, rkt)"

---

#### Virtual Machines (VMs)

**Technology:**
- VMware
- VirtualBox
- KVM
- Hyper-V

**Characteristics:**
- Full OS included
- Hardware virtualization
- Heavier (GBs in size)
- Slower to start (minutes)

**Image Example:**
- Ubuntu 20.04
- Nginx installed
- App deployed
- 2GB image

---

#### Containers

**Technology:**
- Docker
- rkt (pronounced "rocket")
- containerd

**Characteristics:**
- Shares host OS kernel
- Application isolation
- Lighter (MBs in size)
- Faster to start (seconds)

**Image Example:**
- Alpine Linux base
- Node.js app
- 50MB image

---

### Main Advantage: Immutable Infrastructure

> "The main advantage enables **immutable infrastructure** - servers **never change after deployment**"

---

#### What is Immutable Infrastructure?

**Traditional (Mutable):**
1. Deploy server
2. Install software
3. Configure
4. Run for years
5. Update in place
6. Patch and modify
7. Configuration drift

**Immutable:**
1. Create image
2. Deploy image
3. Run unchanged
4. Need update? Create new image
5. Deploy new image
6. Terminate old servers
7. No drift, always fresh

---

#### Benefits

**No Configuration Drift:**
- Server never changes
- Always known state
- Reproducible

**Easy Rollback:**
- Keep old image
- Problem with new image?
- Deploy old image again
- Instant rollback

**Consistency:**
- All servers identical
- Built from same image
- Predictable behavior

**Simplified Operations:**
- Don't debug, replace
- Don't patch, redeploy
- Cattle, not pets

---

### Main Disadvantage

> "The main disadvantage **requires orchestration tools** to manage the images at scale"

**The Problem:**
- Have 100 container images
- Need to deploy across 10 servers
- Need load balancing
- Need health checks
- Need auto-scaling
- Need rolling updates

**Too Complex Manually:**
Cannot manage by hand at scale.

**Need Orchestration:**
- Kubernetes
- Docker Swarm
- ECS

---

## Orchestration Tools

### The Common Tools

> "The most common tools: **Kubernetes, Docker Swarm**"

---

### Purpose

> "**Manage deployment** of VMs and containers making **efficient use of hardware**"

**What Orchestration Does:**
- Decides which container goes on which server
- Packs containers efficiently
- Balances resource usage
- Maximizes hardware utilization

---

### Key Capabilities

**1. Handle Deployments:**
> "Handle **rolling updates, blue-green deployments, and canary deployments**"

**Rolling Updates:**
- Update servers one by one
- Always some servers running
- No downtime

**Blue-Green:**
- Deploy to inactive environment
- Switch traffic over
- Instant rollback

**Canary:**
- Deploy to small % of servers
- Monitor for issues
- Gradually increase %

---

**2. Auto-Healing:**
> "Provide **auto-healing** by monitoring health and replacing unhealthy instances"

**How It Works:**
1. Health check runs every 10 seconds
2. Container fails health check
3. Orchestrator detects failure
4. Kills unhealthy container
5. Starts new container
6. All automatic, no human

**Benefits:**
- Self-healing system
- High availability
- No 3am pages

---

**3. Auto-Scaling:**
> "Enable **auto-scaling** in response to load"

**Dynamic Scaling:**
- Monitor CPU/memory/requests
- Load increases → add containers
- Load decreases → remove containers
- Automatic, real-time

**Example:**
- Normal load: 5 containers
- Black Friday traffic: 50 containers
- After Black Friday: Back to 5
- No manual intervention

---

**4. Load Balancing:**
> "Distribute traffic through **load balancing**"

**Traffic Distribution:**
- Requests distributed across containers
- Unhealthy containers removed from pool
- Even load distribution
- Automatic failover

---

**5. Service Discovery:**
> "Facilitate **service discovery** so containers can communicate"

**The Problem:**
- Containers get dynamic IPs
- Containers come and go
- How do they find each other?

**The Solution:**
- Service registry
- DNS-based discovery
- Environment variables
- Automatic, dynamic

**Example:**
```
Frontend needs database?
Ask for "database" service
Orchestrator provides current IP
Connection established
```

---

### Tool Comparison

**Kubernetes:**
- Industry standard
- Complex but powerful
- Huge ecosystem
- Steep learning curve

**Docker Swarm:**
- Simpler than Kubernetes
- Built into Docker
- Easier to learn
- Smaller ecosystem

---

## Provisioning Tools

### The Common Tools

> "The most common tools: **Terraform, OpenTofu, Pulumi**"

---

### Purpose

> "Responsible for **creating the servers and infrastructure themselves**"

**What They Create:**
Not just servers!

> "Create not only servers but **databases, load balancers, networks, firewall rules, SSL certificates**"

**Complete Infrastructure:**
- Compute (EC2, VMs)
- Storage (S3, EBS)
- Databases (RDS, DynamoDB)
- Networking (VPC, subnets)
- Security (security groups, IAM)
- Load balancers (ALB, NLB)
- DNS (Route53)
- CDN (CloudFront)
- Monitoring (CloudWatch)
- Everything!

---

### Key Features

**1. Declarative Infrastructure:**
> "Define infrastructure resources **declaratively as code**"

**Example (Terraform):**
```hcl
resource "aws_instance" "web" {
  ami           = "ami-12345"
  instance_type = "t2.micro"
  count         = 3
}

resource "aws_lb" "main" {
  name = "web-lb"
  # ...
}
```

**Benefits:**
- Describe what you want
- Terraform figures out how
- Version controlled
- Reviewable

---

**2. Cloud-Agnostic:**
> "Work across **multiple cloud providers**"

**Supported Providers:**
- AWS
- Azure
- Google Cloud
- DigitalOcean
- Alibaba Cloud
- VMware
- OpenStack
- 100+ more

**Benefits:**
- Not locked to one cloud
- Multi-cloud deployments
- Same syntax, different providers

**Example:**
```hcl
# AWS
resource "aws_instance" "web" { }

# Azure
resource "azurerm_virtual_machine" "web" { }

# Same Terraform, different cloud!
```

---

**3. Combination with Other Tools:**
> "Often **used in combination** with other IaC tools (config management, templating, orchestration)"

**Typical Stack:**
1. **Terraform**: Create infrastructure (servers, networks)
2. **Packer**: Build VM/container images
3. **Ansible**: Configure servers
4. **Kubernetes**: Orchestrate containers

**Each Tool's Role:**
- Terraform: Infrastructure foundation
- Packer: Image creation
- Ansible: Configuration
- Kubernetes: Runtime orchestration

**Why Combination:**
- Each tool specializes
- Best tool for each job
- Integrated workflow

---

### Tool Comparison

**Terraform:**
- Most popular
- HCL language
- Large ecosystem
- HashiCorp (commercial company)

**OpenTofu:**
- Open source fork of Terraform
- Same syntax
- Community-driven
- Free forever

**Pulumi:**
- Use real programming languages (Python, TypeScript, Go)
- Not DSL (Domain Specific Language)
- More flexible
- Steeper learning curve

---

## Benefits of IaC

### From State of DevOps Report 2016

The benefits are well-documented and research-backed.

---

### Benefit 1: Self-Service

> "**Entire deployment process automated**, developers can deploy **without bottlenecks**"

**Traditional:**
- Developer needs server
- File ticket with ops
- Wait days/weeks
- Ops provisions manually
- Finally get server

**With IaC:**
- Developer runs: `terraform apply`
- Infrastructure created in minutes
- No waiting
- No ticket
- No ops bottleneck

**Benefits:**
- Developer autonomy
- Faster development
- Reduced ops burden
- Higher productivity

---

### Benefit 2: Speed and Consistency

> "**Automated deployments** are **faster** and **more consistent** than manual processes"

**Speed:**
- Manual: Hours/days
- Automated: Minutes
- 10x-100x faster

**Consistency:**
- Manual: Humans make mistakes
- Automated: Same every time
- Zero errors

**Result:**
- Deploy more frequently
- Reliable deployments
- Less risk

---

### Benefit 3: Documentation

> "**Infrastructure state** is in **source files** everyone can read, not locked in one person's head"

**The Problem (Before IaC):**
- Bob knows how servers configured
- Knowledge in Bob's head
- Bob goes on vacation? Uh oh.
- Bob quits? Disaster.

**With IaC:**
- Infrastructure defined in code
- Code in Git
- Everyone can read it
- Self-documenting
- No bus factor

**Benefits:**
- Knowledge sharing
- Onboarding easier
- No single point of failure
- Team resilience

---

### Benefit 4: Version History

> "**Complete infrastructure history** captured in **commit logs** for debugging and rollbacks"

**Git Commit Log:**
```
commit a7b3c21
Added production database
- RDS instance, multi-AZ
- 100GB storage

commit 5d8e9f2
Increased web server count from 3 to 5
- Handle increased traffic

commit 1a2b3c4
Fixed security group rules
- Closed port 22 to internet
```

**Benefits:**
- Audit trail
- Understand why changes made
- Rollback to any point
- Debug historical issues

---

### Benefit 5: Validation

> "**Every change can go through** code review, automated tests, and static analysis"

**Traditional:**
- Ops makes change in console
- No review
- Hope it works

**With IaC:**
```
1. Write Terraform code
2. Create pull request
3. Team reviews code
4. Automated tests run
5. Static analysis (terraform validate)
6. Merge when approved
7. Apply to infrastructure
```

**Benefits:**
- Catch errors before production
- Team knowledge sharing
- Quality improvements
- Fewer incidents

---

### Benefit 6: Reusability

> "Package infrastructure into **reusable modules** instead of building from scratch each time"

**Modules:**
```hcl
# Define reusable module
module "web_cluster" {
  source = "./modules/web-cluster"

  cluster_size = 5
  instance_type = "t2.micro"
}

# Use same module multiple times
module "staging_cluster" {
  source = "./modules/web-cluster"
  cluster_size = 2
}

module "prod_cluster" {
  source = "./modules/web-cluster"
  cluster_size = 10
}
```

**Benefits:**
- Don't repeat yourself (DRY)
- Faster development
- Consistent patterns
- Tested, reliable components

---

### Benefit 7: Happiness

> "**Eliminates repetitive manual work**, letting computers handle automation and developers **focus on coding**"

**Traditional:**
- Click, click, click in console
- Repeat for every environment
- Boring, error-prone
- Soul-crushing

**With IaC:**
- Write code once
- Automate everything
- Focus on interesting problems
- Enjoyable work

**Team Benefits:**
- Higher morale
- Less burnout
- More productivity
- Better retention

---

# Terraform 101

## Overview and Features

### What is Terraform?

**Official Definition:**
> "Terraform is a tool for **building, changing, and versioning infrastructure safely and efficiently**."

**In Simple Terms:**
- Write code describing infrastructure
- Terraform creates it
- Modify code, Terraform updates it
- Delete code, Terraform destroys it

---

### Main Features

**1. Open Source:**
- Free to use
- Community-driven
- Transparent development

**2. Declarative:**
- Describe desired state
- Terraform determines how to achieve it
- No imperative steps

**3. Cloud-Agnostic:**
- Works with any cloud
- Also works on-premise
- Multi-cloud support

**4. Multiple Provider Support:**
- 100+ providers
- AWS, Azure, GCP
- GitHub, Kubernetes
- Everything

**5. State Management:**
- Tracks current infrastructure
- Knows what exists
- Determines changes needed

**6. Planned Execution:**
- Shows changes before applying
- "Plan" before "Apply"
- Safe, predictable

---

## Declarative Infrastructure

### HCL (HashiCorp Configuration Language)

**What is HCL:**
> "HCL (HashiCorp Configuration Language)"

**Characteristics:**
- Human-readable
- Machine-parseable
- Declarative syntax
- JSON-compatible

---

### Describe Desired State

> "**Describe the desired state**, Terraform handles the 'how'"

**Example:**
```hcl
resource "aws_instance" "web" {
  ami           = "ami-12345"
  instance_type = "t2.micro"
  count         = 5
}
```

**What You Say:**
"I want 5 t2.micro instances"

**What Terraform Does:**
1. Check current state (0 instances)
2. Determine needed: 5 instances
3. Call AWS API 5 times
4. Wait for instances to start
5. Update state file
6. Report success

**You don't tell it HOW, just WHAT.**

---

### Resources: Building Blocks

> "**Resources** are the **building blocks** of infrastructure"

**What is a Resource:**
- Fundamental unit in Terraform
- Represents infrastructure component
- Can be anything: server, database, network

**Syntax:**
```hcl
resource "TYPE" "NAME" {
  # Configuration
}
```

**Examples:**
```hcl
resource "aws_instance" "web" {
  # EC2 instance
}

resource "aws_db_instance" "database" {
  # RDS database
}

resource "aws_vpc" "main" {
  # Virtual network
}
```

---

### Automatic Ordering

> "Terraform determines the **order of operations automatically**"

**Dependency Detection:**

```hcl
resource "aws_vpc" "main" {
  cidr_block = "10.0.0.0/16"
}

resource "aws_subnet" "public" {
  vpc_id = aws_vpc.main.id  # Depends on VPC!
  cidr_block = "10.0.1.0/24"
}

resource "aws_instance" "web" {
  subnet_id = aws_subnet.public.id  # Depends on subnet!
  # ...
}
```

**Terraform Knows:**
1. Create VPC first (no dependencies)
2. Create subnet second (needs VPC)
3. Create instance third (needs subnet)

**You Don't Specify Order:**
Terraform figures it out from references.

---

## State Management

### Terraform Tracks Infrastructure State

> "Terraform **tracks infrastructure state**"

---

### State File

> "**State file** stores current infrastructure configuration"

**What's in State File:**
```json
{
  "version": 4,
  "terraform_version": "1.0.0",
  "resources": [
    {
      "type": "aws_instance",
      "name": "web",
      "instances": [
        {
          "attributes": {
            "id": "i-1234567890abcdef",
            "instance_type": "t2.micro",
            "public_ip": "203.0.113.1"
          }
        }
      ]
    }
  ]
}
```

**Purpose:**
- Records what exists
- Maps code to real infrastructure
- Tracks metadata

---

### Enables Change Detection

> "Enables Terraform to **detect what needs to be changed**"

**How It Works:**
1. Read configuration file (desired state)
2. Read state file (current state)
3. Compare them
4. Determine differences
5. Generate plan to reconcile

**Example:**

**Current State:** 3 servers
**Desired State:** 5 servers
**Plan:** Create 2 more servers

---

### Storage Options

> "Can be stored **locally** or **remotely** (S3, Terraform Cloud)"

**Local State:**
```
terraform.tfstate (file in directory)
```

**Pros:**
- Simple for solo work
- No setup needed

**Cons:**
- Not shareable
- No locking
- Risk of loss

**Remote State:**
```hcl
terraform {
  backend "s3" {
    bucket = "my-terraform-state"
    key    = "prod/terraform.tfstate"
    region = "us-east-1"
  }
}
```

**Pros:**
- Team collaboration
- State locking
- Versioning
- Secure

**Cons:**
- Requires setup
- More complex

---

### Team Collaboration

> "Allows **collaboration across teams**"

**Scenario:**

**Without Remote State:**
- Alice makes changes
- Updates local state
- Bob makes changes
- Updates his local state
- Conflict! Diverged states!

**With Remote State:**
- Alice locks state
- Makes changes
- Unlocks state
- Bob locks state
- Makes changes
- No conflicts!

---

## Variables and Outputs

### Variables: Make Configurations Reusable

> "Make configurations **reusable and flexible**"

---

### Variable Definition

> "**Variables allow parameterization** of configurations"

**Define Variable:**
```hcl
variable "instance_count" {
  description = "Number of instances to create"
  type        = number
  default     = 3
}

variable "instance_type" {
  description = "EC2 instance type"
  type        = string
  default     = "t2.micro"
}
```

**Use Variable:**
```hcl
resource "aws_instance" "web" {
  count         = var.instance_count
  instance_type = var.instance_type
  # ...
}
```

---

### Variable Types

> "Support different **types**: string, number, list, map, object"

**Examples:**

```hcl
variable "name" {
  type = string
}

variable "port" {
  type = number
}

variable "availability_zones" {
  type = list(string)
}

variable "tags" {
  type = map(string)
}

variable "instance_config" {
  type = object({
    size = string
    disk = number
  })
}
```

---

### Default Values and Validation

> "Can have **default values** and **validation rules**"

**Default Values:**
```hcl
variable "environment" {
  type    = string
  default = "development"
}
```

**Validation:**
```hcl
variable "instance_type" {
  type = string

  validation {
    condition     = contains(["t2.micro", "t2.small"], var.instance_type)
    error_message = "Must be t2.micro or t2.small"
  }
}
```

---

### Providing Values

> "Values can be provided via **CLI, files, or environment variables**"

**CLI:**
```bash
terraform apply -var="instance_count=5"
```

**File (terraform.tfvars):**
```hcl
instance_count = 5
instance_type = "t2.small"
```

**Environment Variable:**
```bash
export TF_VAR_instance_count=5
terraform apply
```

---

### Outputs: Expose Information

> "**Expose information** from your infrastructure"

---

### Output Definition

> "**Outputs display values** after terraform apply"

**Define Output:**
```hcl
output "instance_ip" {
  description = "Public IP of web server"
  value       = aws_instance.web.public_ip
}

output "load_balancer_dns" {
  value = aws_lb.main.dns_name
}
```

**After Apply:**
```
Outputs:

instance_ip = "203.0.113.45"
load_balancer_dns = "my-lb-123456.us-east-1.elb.amazonaws.com"
```

---

### Output Uses

**1. Display Important Info:**
> "Outputs display values after terraform apply"

- See critical information
- Copy-paste into documentation
- Share with team

**2. Pass Between Modules:**
> "Can be **used by other Terraform configurations**"

```hcl
# Module A outputs
output "vpc_id" {
  value = aws_vpc.main.id
}

# Module B inputs
module "network" {
  source = "./network"
}

resource "aws_instance" "web" {
  vpc_id = module.network.vpc_id
}
```

**3. Documentation:**
> "Help **document important infrastructure details**"

- What's the database endpoint?
- What's the load balancer URL?
- Outputs answer these questions

---

## Resource Dependencies

### Automatic and Explicit Dependency Management

> "**Automatic** and **explicit** dependency management"

---

### Automatic Dependencies

> "Terraform **automatically detects dependencies**"

**How:**
Terraform analyzes resource references.

**Example:**
```hcl
resource "aws_vpc" "main" {
  cidr_block = "10.0.0.0/16"
}

resource "aws_subnet" "public" {
  vpc_id = aws_vpc.main.id  # Reference creates dependency!
}
```

**Terraform Knows:**
Subnet depends on VPC (because it references `aws_vpc.main.id`)

**Result:**
VPC created before subnet automatically.

---

### Explicit Dependencies

> "Can **explicitly define dependencies** when needed"

**When Needed:**
Sometimes dependency not obvious from references.

**Example:**
```hcl
resource "aws_instance" "web" {
  # ...

  depends_on = [aws_iam_role.instance_role]
}
```

**Why:**
- Instance doesn't reference role directly
- But needs role to exist first
- Explicit dependency required

---

### Correct Ordering

> "Creates resources in **correct order**"

**Example:**

```hcl
# 1. VPC (no dependencies)
resource "aws_vpc" "main" { }

# 2. Subnet (depends on VPC)
resource "aws_subnet" "public" {
  vpc_id = aws_vpc.main.id
}

# 3. Security Group (depends on VPC)
resource "aws_security_group" "web" {
  vpc_id = aws_vpc.main.id
}

# 4. Instance (depends on subnet and security group)
resource "aws_instance" "web" {
  subnet_id = aws_subnet.public.id
  vpc_security_group_ids = [aws_security_group.web.id]
}
```

**Terraform Creates:**
1. VPC first
2. Subnet and security group in parallel (both only depend on VPC)
3. Instance last (depends on both)

---

### Parallel Creation

> "Handles **parallel resource creation** when possible"

**Efficiency:**
- Independent resources created in parallel
- Faster execution
- Optimal use of time

**Example:**
Creating 10 independent servers? All created simultaneously!

---

## Terraform Workflow

### Three Steps When Using Terraform

> "**Three Steps** when using Terraform"

---

### Step 1: Write

> "**Write** - Author infrastructure as code."

**What You Do:**
1. Create `.tf` files
2. Define resources
3. Set variables
4. Write configuration

**Example:**
```hcl
# main.tf
resource "aws_instance" "web" {
  ami           = "ami-12345"
  instance_type = "t2.micro"
}
```

**Tools:**
- Text editor
- IDE with Terraform plugin
- Version control (Git)

---

### Step 2: Plan

> "**Plan** - Preview changes before applying."

**Command:**
```bash
terraform plan
```

**What It Does:**
1. Read configuration
2. Read state file
3. Compare desired vs current
4. Generate execution plan
5. Show what will change

**Example Output:**
```
Terraform will perform the following actions:

  # aws_instance.web will be created
  + resource "aws_instance" "web" {
      + ami           = "ami-12345"
      + instance_type = "t2.micro"
      + id            = (known after apply)
      # ...
    }

Plan: 1 to add, 0 to change, 0 to destroy.
```

**Symbols:**
- `+` = will create
- `-` = will destroy
- `~` = will modify
- `-/+` = will replace (destroy then create)

**Benefits:**
- See changes before making them
- Catch mistakes
- Review with team
- Safe, predictable

---

### Step 3: Apply

> "**Apply** - Provision reproducible infrastructure."

**Command:**
```bash
terraform apply
```

**What It Does:**
1. Show plan
2. Ask for confirmation
3. Execute plan
4. Create/update/delete resources
5. Update state file
6. Show outputs

**Example:**
```bash
$ terraform apply

# Shows plan...

Do you want to perform these actions?
  Enter a value: yes

aws_instance.web: Creating...
aws_instance.web: Creation complete after 45s [id=i-1234567890]

Apply complete! Resources: 1 added, 0 changed, 0 destroyed.

Outputs:
instance_ip = "203.0.113.45"
```

**Auto-Approve (Use Carefully):**
```bash
terraform apply -auto-approve
```

---

### The Complete Cycle

```
1. Write code
   ↓
2. Plan changes
   ↓
3. Review plan
   ↓
4. Apply changes
   ↓
5. Infrastructure updated
   ↓
(Repeat as needed)
```

**Best Practice:**
- Always run `plan` before `apply`
- Review plan carefully
- Use version control
- Collaborate via pull requests

---

# Scalability & Availability

## Overview

### Modern Application Requirements

> "Modern applications need to **handle growth** and **stay online**"

**Two Critical Needs:**
1. **Scalability** - Handle increasing load
2. **Availability** - Stay online

---

### The Reality

**1. Cloud Infrastructure:**
> "Cloud infrastructure provides **flexible and scalable options**"

- Elastic resources
- On-demand scaling
- Pay for what you use

**2. User Expectations:**
> "Users expect systems to be **always available and responsive**"

- 24/7 uptime
- Fast response times
- No downtime tolerance

**3. Unpredictable Traffic:**
> "Traffic patterns can be **unpredictable** and **change significantly**"

- Black Friday spikes
- Viral content
- Seasonal variation
- Marketing campaigns

**4. Failure is Normal:**
> "Systems must **handle both normal operations and unexpected failures**"

- Servers crash
- Networks fail
- Databases go down
- Must keep running anyway

---

## Scalability Concepts

### Definition

> "Scalability is the ability of a system to **handle increasing workload**"

---

### Two Types of Scaling

**1. Vertical Scaling:**
> "**Vertical scaling**: adding more **CPU, RAM, or storage** to existing servers"

**Also Called:**
- "Scaling up"
- "Bigger box"

**Example:**
- Current: 4 CPU, 8GB RAM
- Scaled: 16 CPU, 64GB RAM

**Advantages:**
- Simple (no code changes)
- No distributed system complexity

**Disadvantages:**
- Physical limits (can't infinitely scale)
- Expensive (high-end hardware costly)
- Single point of failure
- Downtime to upgrade

---

**2. Horizontal Scaling:**
> "**Horizontal scaling**: adding **more servers** to distribute the load"

**Also Called:**
- "Scaling out"
- "More boxes"

**Example:**
- Current: 1 server
- Scaled: 10 servers

**Advantages:**
- No physical limits (add more servers)
- Cheaper (commodity hardware)
- Redundancy (no single point of failure)
- No downtime (add servers online)

**Disadvantages:**
- More complex (distributed system)
- Code must support it
- Network overhead

**Modern Preference:**
Horizontal scaling is the cloud-native approach.

---

### Auto-Scaling

> "**Auto-scaling** adjusts resources based on demand"

**How It Works:**
1. Monitor metrics (CPU, requests, etc.)
2. Detect high load → add servers
3. Detect low load → remove servers
4. Automatic, no human intervention

**Example:**
```
Monday 9am:  Traffic low  → 2 servers
Monday 2pm:  Traffic high → 10 servers
Monday 10pm: Traffic low  → 3 servers
```

**Benefits:**
- Respond to demand automatically
- Cost efficient (only pay for what's needed)
- Better performance (enough capacity)
- No manual intervention

---

### Scalability Formula

> "Scalability = (Maximum Load / Initial Load) or (Performance at Scale / Baseline Performance)"

**Example 1 (Load):**
- Initial: Handle 100 requests/sec
- Maximum: Handle 10,000 requests/sec
- Scalability: 10,000 / 100 = **100x**

**Example 2 (Performance):**
- Baseline: 200ms response time @ 100 users
- At Scale: 200ms response time @ 10,000 users
- Scalability: Maintained performance = **Good**

---

## Load Balancing

### Definition

> "Load balancers **distribute incoming traffic** across **multiple servers**. This prevents any single server from being overwhelmed and improves overall performance."

---

### How It Works

**1. Distributes Requests:**
> "Distributes requests **evenly** across available servers"

**Without Load Balancer:**
```
User → Server1 (overloaded!)
User → Server1 (overloaded!)
        Server2 (idle)
        Server3 (idle)
```

**With Load Balancer:**
```
User → Load Balancer → Server1
User → Load Balancer → Server2
User → Load Balancer → Server3
(Evenly distributed)
```

---

**2. Health Checks:**
> "Health checks **detect and remove failing servers** from rotation"

**Process:**
1. Load balancer pings each server every 10 seconds
2. Server responds → healthy, keep in pool
3. Server doesn't respond → unhealthy, remove from pool
4. Unhealthy server recovers → add back to pool

**Result:**
- Users never sent to dead servers
- Automatic failover
- High availability

---

**3. Load Distribution:**
> "**Load per server** = Total Load / Number of Active Servers"

**Example:**
- Total load: 1000 requests/sec
- Active servers: 5
- Load per server: 1000 / 5 = 200 req/sec

**If Server Fails:**
- Total load: 1000 requests/sec
- Active servers: 4 (one failed, removed)
- Load per server: 1000 / 4 = 250 req/sec
- System still works!

---

### Load Balancing Methods

> "Supports different methods: **round-robin, least connections, IP hash**"

---

**1. Round-Robin:**
- Send to Server1
- Send to Server2
- Send to Server3
- Back to Server1
- Simple, fair

**2. Least Connections:**
- Send to server with fewest active connections
- Better for varying request durations
- More even load

**3. IP Hash:**
- Hash client IP → always same server
- Session affinity
- Useful for stateful apps

**4. Others:**
- Weighted round-robin
- Random
- Geographic

---

## Availability

### Definition

> "Availability measures **how often your system is up and running**."

---

### Availability Levels

**99.9% Availability:**
> "99.9% availability = **8.76 hours downtime per year**"

**Calculation:**
- 365 days × 24 hours = 8760 hours/year
- 0.1% downtime = 0.001 × 8760 = 8.76 hours
- About 43 minutes per month

**Use Cases:**
- Internal tools
- Low-criticality apps

---

**99.99% Availability:**
> "99.99% availability = **52 minutes downtime per year**"

**Calculation:**
- 0.01% × 8760 hours = 0.876 hours = 52.6 minutes
- About 4.3 minutes per month

**Use Cases:**
- Production applications
- Customer-facing services

**The Nines:**
- 99% = "two nines"
- 99.9% = "three nines"
- 99.99% = "four nines"
- 99.999% = "five nines" (5.26 min/year!)

---

### Availability Formula

> "**Availability (%)** = (Uptime / (Uptime + Downtime)) × 100"

**Example:**
- Uptime: 8700 hours
- Downtime: 60 hours
- Total: 8760 hours (1 year)
- Availability: (8700 / 8760) × 100 = 99.32%

---

### Achieving High Availability

> "**Redundancy** removes single points of failure"

**Single Point of Failure (SPOF):**
- One component fails → entire system fails
- Example: One database server

**Removing SPOF:**
- Add redundancy
- Multiple components
- If one fails, others take over

**Examples:**

**Redundant Servers:**
```
Load Balancer
├─> Server1
├─> Server2 (if Server1 fails)
└─> Server3 (if Server2 fails)
```

**Redundant Databases:**
```
Primary DB → Replica DB
(Auto-failover if primary fails)
```

**Redundant Data Centers:**
```
US-East Region → US-West Region
(Disaster recovery)
```

---

### Availability Best Practices

**1. Eliminate SPOFs:**
- Multiple servers
- Multiple availability zones
- Multiple regions

**2. Health Checks:**
- Detect failures quickly
- Auto-remove unhealthy components
- Auto-recovery

**3. Load Balancing:**
- Distribute traffic
- Failover capability
- Even resource usage

**4. Auto-Scaling:**
- Handle traffic spikes
- Maintain performance
- Cost optimization

**5. Monitoring:**
- Track uptime
- Alert on issues
- Data-driven improvements

---

# Practical Implementation

## Practical Guide

### Lab Tutorial

> "Learn from this tutorial (Use Terraform with Docker provider): https://developer.hashicorp.com/terraform/tutorials/docker-get-started"

**Learning Path:**
1. Install Terraform
2. Write first configuration
3. Use Docker provider
4. Practice workflow (write, plan, apply)
5. Understand state management
6. Learn to destroy resources

**Why Docker Provider:**
- Local, no cloud account needed
- Fast feedback
- See results immediately
- Great for learning

---

## Project Requirements

### Your Project Implementation

> "You should **change your deployment from docker compose into terraform scripts**, only your frontend, backend and database."

---

### Requirements Breakdown

**1. Convert to Terraform:**

**Current (docker-compose.yml):**
```yaml
version: '3'
services:
  frontend:
    image: my-frontend
  backend:
    image: my-backend
  database:
    image: postgres
```

**New (Terraform):**
```hcl
resource "docker_container" "frontend" {
  image = "my-frontend"
  # ...
}

resource "docker_container" "backend" {
  image = "my-backend"
  # ...
}

resource "docker_container" "database" {
  image = "postgres"
  # ...
}
```

---

**2. CI/CD Integration:**
> "They should be **integrated in your CI-CD pipeline**"

**GitHub Actions Example:**
```yaml
steps:
  - name: Terraform Init
    run: terraform init

  - name: Terraform Plan
    run: terraform plan

  - name: Terraform Apply
    run: terraform apply -auto-approve
```

---

**3. High Availability:**
> "You need to make sure that there are **two replicas** of your frontend and backend"

**Terraform Implementation:**
```hcl
resource "docker_container" "frontend" {
  count = 2  # Two replicas!
  name  = "frontend-${count.index}"
  image = "my-frontend"
}

resource "docker_container" "backend" {
  count = 2  # Two replicas!
  name  = "backend-${count.index}"
  image = "my-backend"
}
```

---

**4. Fault Tolerance:**
> "If one of the services fail the application must be **fault tolerant**"

**Requirement:**
- Service crashes → app still works
- Other replica handles traffic

---

**5. Load Balancer:**
> "**TIP:** You can use **nginx as load balancer** to achieve High Availability"

**Nginx Configuration Example:**
```nginx
upstream frontend_backend {
  server frontend-0:3000;
  server frontend-1:3000;
}

server {
  listen 80;
  location / {
    proxy_pass http://frontend_backend;
  }
}
```

**In Terraform:**
```hcl
resource "docker_container" "nginx" {
  name  = "load-balancer"
  image = "nginx"
  # Mount nginx.conf
  # ...
}
```

---

### Complete Architecture

```
User Request
    ↓
Nginx Load Balancer
    ↓
├─> Frontend-0    Frontend-1
    ↓
├─> Backend-0     Backend-1
    ↓
Database (Single instance is OK for project)
```

**Fault Tolerance:**
- Frontend-0 crashes → Nginx routes to Frontend-1
- Backend-0 crashes → Nginx routes to Backend-1
- Application stays online!

---

# Study Tips and Exam Preparation

## Critical Concepts to Master

### Deployment History

**1. CAPEX vs OPEX:**
- Know all characteristics of each
- Understand business implications
- Why OPEX better for startups

**2. Pets vs Cattle:**
- All characteristics of pets
- All characteristics of cattle
- Modern cloud = cattle
- Why paradigm shift important

**3. Pre-Cloud vs Cloud Era:**
- Pre-cloud: CAPEX, pets, manual
- Cloud: OPEX, cattle, automated
- Configuration problems persist

---

### Infrastructure as Code

**1. IaC Definition:**
- Write code to define infrastructure
- Version controlled
- Declarative
- Idempotent
- Automatic and reproducible

**2. IaC vs Docker:**
- Docker runs apps
- IaC creates infrastructure
- Different purposes
- Complementary tools

**3. Benefits of IaC:**
- All 7 benefits from State of DevOps Report
- Know examples for each
- Understand business value

---

### IaC Tool Categories (Critical!)

**Know All Six Categories:**

**1. Containerization (Docker):**
- Runs apps
- Self-contained environments
- Build → Ship → Run

**2. Ad-hoc Scripts:**
- Bash, Python scripts
- Advantage: Preferred language
- Disadvantage: Inconsistency, spaghetti code

**3. Configuration Management (Chef, Puppet, Ansible):**
- Install and manage software
- Idempotent
- Distributed
- Disadvantage: Still manage servers

**4. Server Templating (Docker, Packer, Vagrant):**
- Create images
- VMs vs Containers
- Immutable infrastructure
- Disadvantage: Needs orchestration

**5. Orchestration (Kubernetes, Docker Swarm):**
- Manage containers at scale
- Auto-healing, auto-scaling
- Load balancing, service discovery
- Rolling updates

**6. Provisioning (Terraform, OpenTofu, Pulumi):**
- Create infrastructure itself
- Servers, networks, databases, everything
- Cloud-agnostic
- Declarative

---

### Terraform Deep Dive

**1. Main Features (6):**
- Open Source
- Declarative
- Cloud-agnostic
- Multiple Provider Support
- State Management
- Planned Execution

**2. HCL:**
- Declarative language
- Describe desired state
- Resources are building blocks
- Automatic dependency ordering

**3. State Management:**
- Tracks current infrastructure
- Enables change detection
- Local vs remote storage
- Team collaboration

**4. Variables:**
- Make configs reusable
- Types: string, number, list, map, object
- Default values, validation
- Provide via CLI, files, env vars

**5. Outputs:**
- Expose information
- Display after apply
- Pass between modules
- Documentation

**6. Dependencies:**
- Automatic (from references)
- Explicit (depends_on)
- Correct ordering
- Parallel when possible

**7. Workflow (3 steps):**
- Write (author code)
- Plan (preview changes)
- Apply (provision infrastructure)

---

### Scalability & Availability

**1. Scalability:**
- Vertical (scale up)
- Horizontal (scale out)
- Auto-scaling
- Formula: Max Load / Initial Load

**2. Load Balancing:**
- Distributes traffic
- Health checks
- Load per server formula
- Methods: round-robin, least connections, IP hash

**3. Availability:**
- 99.9% = 8.76 hours downtime/year
- 99.99% = 52 minutes downtime/year
- Formula: (Uptime / (Uptime + Downtime)) × 100
- Redundancy removes SPOFs

---

## Key Numbers to Remember

### CAPEX vs OPEX
- CAPEX: Upfront, ownership
- OPEX: Pay-as-you-go, no ownership

### IaC Tool Categories (6)
1. Containerization
2. Ad-hoc Scripts
3. Configuration Management
4. Server Templating
5. Orchestration
6. Provisioning

### Terraform Features (6)
1. Open Source
2. Declarative
3. Cloud-agnostic
4. Multiple Provider Support
5. State Management
6. Planned Execution

### Terraform Workflow (3)
1. Write
2. Plan
3. Apply

### Scalability Types (2)
1. Vertical (up)
2. Horizontal (out)

### Availability Levels
- 99.9% = 8.76 hours/year downtime
- 99.99% = 52 minutes/year downtime

---

## Common Exam Question Types

### Comparison Questions
- "Compare CAPEX vs OPEX"
- "Pets vs Cattle servers - characteristics and advantages"
- "Vertical vs Horizontal scaling"
- "Configuration Management vs Provisioning tools"
- "Local vs Remote state in Terraform"

### Scenario Questions
- "You need to create 100 servers with identical config. Which IaC tool category?"
- "App needs to handle 10x more traffic during Black Friday. What approach?"
- "One server crashes. How does system stay available?"
- "Terraform plan shows 5 resources will be destroyed. What should you do?"

### Conceptual Questions
- "What is immutable infrastructure?"
- "Why is idempotence important in IaC?"
- "Explain Terraform state management"
- "What problems does IaC solve?"

### Practical Questions
- "Write Terraform code to create 3 web servers"
- "How would you achieve 99.99% availability?"
- "Design HA architecture with load balancer"
- "Convert docker-compose to Terraform"

---

## Important Distinctions

### Infrastructure Types
- **Pets**: Named, maintained, irreplaceable, manual
- **Cattle**: Numbered, disposable, auto-provisioned, ephemeral

### Financial Models
- **CAPEX**: Buy upfront, own, fixed asset
- **OPEX**: Pay-as-you-go, rent, operational expense

### IaC Approaches
- **Imperative**: How to do it (step-by-step)
- **Declarative**: What you want (desired state)

### Scaling Types
- **Vertical**: Bigger server (scale up)
- **Horizontal**: More servers (scale out)

### Tool Purposes
- **Docker**: Runs apps
- **Ansible**: Configures servers
- **Kubernetes**: Orchestrates containers
- **Terraform**: Creates infrastructure

---

## Real-World Application

### Terraform in Practice

**Learning Project:**
1. Start with Docker provider (local)
2. Write simple configs
3. Practice workflow (write/plan/apply)
4. Understand state
5. Use variables and outputs

**Your Project:**
1. Convert docker-compose to Terraform
2. Add replicas (count = 2)
3. Add nginx load balancer
4. Integrate with CI/CD
5. Test fault tolerance

---

### High Availability Design

**Requirements:**
- 2 frontend replicas
- 2 backend replicas
- Nginx load balancer
- Health checks
- Auto-recovery

**Architecture:**
```
Nginx
├─> Frontend-0, Frontend-1
    ├─> Backend-0, Backend-1
        └─> Database
```

**Testing:**
- Kill frontend-0 → Still works
- Kill backend-1 → Still works
- Nginx health checks → Auto-remove failed

---

## Connections to Other Slides

### Integration with Slide 04 (CI/CD)

**GitHub Actions + Terraform:**
```yaml
- name: Terraform Plan
  run: terraform plan

- name: Terraform Apply
  run: terraform apply -auto-approve
```

**Pipeline:**
Code → Tests → Terraform Apply → Deployed

---

### Integration with Slide 05 (Delivery Strategies)

**Blue/Green with IaC:**
```hcl
# Blue environment
module "blue" {
  source = "./app"
  version = "v1.0"
}

# Green environment
module "green" {
  source = "./app"
  version = "v2.0"
}

# Switch load balancer
resource "aws_lb_target_group_attachment" {
  target_group = var.active_env == "blue" ? module.blue : module.green
}
```

**IaC Enables:**
- Canary releases
- Blue/green deployments
- Infrastructure versioning

---

### Integration with Slide 06 (Testing)

**Test Infrastructure Code:**
- Terraform validate
- Terraform plan (preview)
- Automated tests for Terraform (Terratest)
- CI integration

---

## Final Exam Preparation Checklist

### Core Knowledge
- ✓ CAPEX vs OPEX (all characteristics)
- ✓ Pets vs Cattle (all characteristics)
- ✓ IaC definition and benefits
- ✓ All 6 IaC tool categories
- ✓ Terraform 6 main features
- ✓ Terraform workflow (3 steps)
- ✓ State management
- ✓ Variables and outputs
- ✓ Scalability (vertical vs horizontal)
- ✓ Load balancing
- ✓ Availability (99.9% vs 99.99%)

### Tool Knowledge
- ✓ Docker purpose and scope
- ✓ Configuration management tools
- ✓ Server templating tools
- ✓ Orchestration tools
- ✓ Provisioning tools
- ✓ When to use which tool

### Terraform Deep Knowledge
- ✓ HCL syntax
- ✓ Resources and dependencies
- ✓ State file purpose
- ✓ Local vs remote state
- ✓ Variable types and usage
- ✓ Output uses
- ✓ Write/Plan/Apply workflow

### Practical Skills
- ✓ Write basic Terraform config
- ✓ Understand Terraform plan output
- ✓ Design HA architecture
- ✓ Calculate availability percentages
- ✓ Configure load balancing

### Conceptual Understanding
- ✓ Immutable infrastructure
- ✓ Idempotence importance
- ✓ Declarative vs imperative
- ✓ Infrastructure as code benefits
- ✓ Redundancy and SPOF

---

# Summary

## Key Takeaways

### Evolution of Infrastructure
- Pre-cloud: CAPEX, pets, manual → Expensive, slow, risky
- Cloud: OPEX, cattle, automated → Flexible, fast, scalable
- Problem: Manual configuration still needed
- Solution: Infrastructure as Code

### IaC Fundamentals
- Define infrastructure as code
- Version controlled (Git)
- Declarative (what, not how)
- Idempotent (safe to re-run)
- Reproducible (same every time)

### IaC Tool Ecosystem
- 6 categories, each with purpose
- Docker: Runs apps
- Configuration management: Configures servers
- Server templating: Creates images
- Orchestration: Manages at scale
- Provisioning: Creates infrastructure
- All work together

### Terraform
- Leading provisioning tool
- Declarative HCL language
- State management critical
- Write → Plan → Apply workflow
- Cloud-agnostic
- Production-ready

### Scalability & Availability
- Scalability: Handle growth (vertical or horizontal)
- Load balancing: Distribute traffic, health checks
- Availability: Stay online (redundancy, no SPOF)
- High availability requires multiple replicas
- Auto-scaling responds to demand

### Practical Application
- Convert docker-compose to Terraform
- Add replicas for HA
- Implement load balancing
- Integrate with CI/CD
- Test fault tolerance

---

# End of Study Guide

This comprehensive guide covers all material from ES Slide 07: Infrastructure as Code. Use it to:
- Understand infrastructure evolution
- Master IaC concepts deeply
- Learn Terraform fundamentals
- Prepare for exams
- Implement in your project
- Reference during development

**Remember:** Infrastructure as Code is not just about automation. It's about **treating infrastructure with the same rigor as application code** - version control, testing, code review, and continuous improvement.

Good luck with your studies and happy infrastructure coding!
