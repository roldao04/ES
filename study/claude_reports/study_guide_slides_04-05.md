# Software Engineering - Study Guide (Slides 04-05)
## Continuous Deployment & Continuous Delivery - Complete Exam Preparation Guide

---

# Table of Contents

1. [Slide 04: Continuous Deployment](#slide-04-continuous-deployment)
   - [The Dev vs Ops Problem](#the-dev-vs-ops-problem)
   - [CI/CD Pipelines](#cicd-pipelines)
   - [Continuous Integration (CI)](#continuous-integration-ci)
   - [Continuous Deployment (CD)](#continuous-deployment-cd)
   - [Benefits of Continuous Deployment](#benefits-of-continuous-deployment)
   - [GitHub Actions](#github-actions)
   - [Practical Implementation](#practical-implementation)

2. [Slide 05: Continuous Delivery Strategies](#slide-05-continuous-delivery-strategies)
   - [Core Principles of Software Delivery](#core-principles-of-software-delivery)
   - [Feature Toggling](#feature-toggling)
   - [Progressive Delivery Strategies](#progressive-delivery-strategies)
   - [User-Installed Software](#continuously-releasing-user-installed-software)

3. [Study Tips and Exam Preparation](#study-tips-and-exam-preparation)

---

# Slide 04: Continuous Deployment

## The Dev vs Ops Problem

### What Are the Limitations of Agile?

#### The Core Problem
Agile solves many development problems, but has a critical limitation:

- **The Development part is continuous** ✓
- **The Operation is NOT continuous** ✗

This creates what's known as the **"Wall of Confusion"**

---

### Dev vs Ops: The Traditional Divide

**Visual Description:** The slides reference a "wall of confusion" - a metaphorical barrier between Development and Operations teams.

#### How the Traditional Process Works

**Step 1: Development Team**
- Development team kicks things off
- "Throws" a software release **"over the wall"** to Operations
- Hands off responsibility

**Step 2: Operations Team**
- Operations picks up the release artifacts
- Begins preparing for deployment
- **Hand-edits configuration files** to reflect production environment
  - Production is **significantly different** than Development environments
  - Manual, error-prone process
  - No version control

---

### The Problems with This Approach

1. **Manual, error-prone processes**
   - Human errors in configuration
   - Inconsistencies between environments
   - No repeatability

2. **Lack of collaboration**
   - Dev and Ops work in silos
   - Different goals and incentives
   - Communication breakdown

3. **Environment differences**
   - "It works on my machine"
   - Production surprises
   - Configuration drift

4. **Slow feedback**
   - Problems discovered late
   - Long deployment cycles
   - Difficult debugging

---

## CI/CD Pipelines

### What is a Pipeline?

#### Definition
> "A pipeline in CI/CD is a **structured sequence of automated steps** that transform source code into a deployable software product."

---

### Purpose
Ensures **consistent, repeatable, and reliable** software delivery by automating:
- Integration
- Testing
- Deployment tasks

---

### Key Characteristics

**1. Sequential and/or parallel stages**
   - Build stage
   - Test stage
   - Deploy stage
   - Can run in sequence or parallel

**2. Automated execution**
   - Triggered by events (e.g., code commit, merge)
   - No manual intervention
   - Consistent process

**3. Feedback loops**
   - Logs for developers
   - Reports on status
   - Alerts when issues occur
   - Rapid notification

**4. Environment consistency**
   - Development → Staging → Production
   - Same process across environments
   - Reproducible deployments

---

### In Other Words

A pipeline is:
- A **route from development to production**
- **Triggered by different events** (push, merge, schedule, etc.)
- **Different branches may take different paths**
  - Main branch → full pipeline to production
  - Feature branch → build and test only
  - Release branch → staging deployment

---

## Continuous Integration (CI)

### Definition

> "CI is the practice of **integrating developer changes as frequently as possible** in the same version-controlled branch."

---

### Core Principle

> "CI is about ensuring that the **amount of code to be merged and verified is reduced to a minimum**."

#### Why This Matters
- **Smaller changes** = easier to review
- **Frequent integration** = fewer conflicts
- **Quick feedback** = faster fixes
- **Reduced risk** = less can go wrong

---

### CI: Foundational Practice

#### Key Characteristics

**1. Frequent integration**
   - Ensures frequent integration of changes into main branch
   - **Minimizes divergence** between branches
   - Prevents integration hell

**2. Centralized, automated pipelines**
   - Build automatically
   - Test automatically
   - Validate each code increment
   - Consistent process

**3. Produces artifacts**
   - Artifacts serve as **authoritative, deployable units** of software
   - Version controlled
   - Traceable
   - Reusable

**4. Rapid feedback cycle**
   - Shifts "completion" to **integrated and verified code**
   - Not done until integrated
   - Not done until tested
   - Quick notification of problems

**5. Reduces integration conflicts**
   - Facilitates **early detection of defects**
   - Merge conflicts caught immediately
   - Bugs found quickly
   - Less rework

---

## Traditional vs Modern Deployment

### Deploying Every Few Months or Years (Traditional)

**Characteristics:**
- ❌ Manual, error-prone processes
- ❌ Slow integration of changes
- ❌ Builds created by hand
- ❌ Configs & dependencies outside version control
- ❌ Poorly documented, sequential deployment steps
- ❌ Manual testing for every release
- ❌ Release cycles: **months or years**

**Result:** High risk, slow feedback, poor quality

---

### Deploying Every Few Days (Modern)

#### The Transformation

**Automation at the core:**
- Build handled by tools ✓
- Test handled by tools ✓
- Deploy handled by tools ✓

---

#### Rationale

> "Human intervention often represents a **bottleneck**, whereas automation enables **greater speed** and **reduces errors**."

---

#### Paradigm Shift

> "The focus has evolved from simply **writing code** to the broader goal of **delivering software**."

**Key Insight:**
- Old mindset: "I wrote the code, my job is done"
- New mindset: "I'm responsible until it's delivering value in production"

---

## Continuous Deployment (CD)

### Scope and Premise

#### Definition
> "From **'code committed'** to **'code in production'** as a **unified process**"

---

#### Context and Evolution

**Culmination of decades of automation:**
- Builds upon **XP** (Extreme Programming)
- Builds upon **DevOps** culture
- Builds upon **Continuous Integration**
- Builds upon **Continuous Delivery**

**Emphasis on:**
- **Repeatability** - Same process every time
- **Reliability** - Trustworthy deployments
- **Speed** - Fast time to production

**Key Principle:**
> "Positions **production** as the primary locus of **value realization**"

Value only realized when users can use the software!

---

### Continuous Deployment: Formal Definition

> "The practice of structuring your software pipeline so that it is **completely free of manual intervention**. With this methodology, **every code commit that passes its quality gates is automatically deployed to production**."

---

### Continuous Delivery vs Continuous Deployment

**Important Distinction:**

**Continuous Delivery:**
- Continuous delivery in such a way that deployments happen **without human intervention** in at least some **pre-production environments** for every build
- However, the same automation does **not carry changes all the way to production**
- To cover that last step, a **human still has to press a button** in the pipeline tool to deploy the release candidate

**Continuous Deployment:**
- **Every commit** that passes quality gates goes to **production automatically**
- **No manual button** to press
- Fully automated

---

### The Key Differentiator

> "The presence of that **manual 'button'** is the main differentiator between continuous delivery and continuous deployment."

**Visual Comparison:**

```
Continuous Delivery:
Code → Build → Test → Staging → [MANUAL APPROVAL] → Production

Continuous Deployment:
Code → Build → Test → Staging → Production (all automatic)
```

---

### CD: Maintaining Deployability

#### How CD Works

**1. Extends CI pipelines**
   - Supports automated deployments across environments
   - Builds on CI foundation
   - Adds deployment stages

**2. Treats each commit as potential release**
   - Every commit is a **potential release candidate**
   - Ready for production
   - Fully tested and validated

**3. Automated promotion**
   - To staging environments
   - To UAT (User Acceptance Testing) environments
   - Validates **higher-order behaviors**
   - Not just unit tests, but integration and system tests

**4. Increases deployment frequency**
   - More frequent deployments
   - **Lowers per-release risk exposure**
   - Smaller changes = less risk

**5. Manual approval for Continuous Delivery**
   - Retains a **manual approval step** as final control
   - Before production deployment
   - Human oversight preserved

---

## Implications and Organizational Outcomes

### Benefits of Continuous Deployment

#### 1. Granular, low-risk deployments
- **Facilitates** small, incremental changes
- **Immediate production feedback**
- Quick validation
- Fast learning

#### 2. Rapid fault detection and recovery
- **Enables** rapid detection of faults in live environments
- Quick diagnosis
- Fast recovery
- Minimal downtime

#### 3. Accelerated experimentation
- **Supports** timely, data-driven product decisions
- A/B testing easier
- Fast iteration
- Learn from real users

#### 4. Improved delivery metrics
- **Lead time** - Time from commit to production
- **Throughput** - Number of deployments
- **Defect rate** - Bugs in production
- **Recovery speed** - MTTR (Mean Time To Recovery)

#### 5. Culture of accountability
- **Embeds** a culture prioritizing operational resilience
- And agility
- Ownership of production
- Responsibility for quality

---

## Benefits of Continuous Deployment (Detailed)

### 1. Operational Efficiency and Waste Reduction

> "Continuous deployment streamlines the software value stream by **minimizing rework, batch sizes, and queueing**, thereby improving **end-to-end flow** in alignment with **Lean one-piece flow principles**."

**Key Concepts:**
- **Minimize rework** - Get it right the first time
- **Small batch sizes** - Deploy small changes
- **Reduce queueing** - No waiting for release windows
- **Lean one-piece flow** - Continuous flow of value

**Result:** More efficient delivery pipeline

---

### 2. Accelerated Delivery Cadence

> "**Lead time** from code commit to production is **substantially reduced**, and **deployment frequency increases**, enabling timely delivery of increments and faster responsiveness to stakeholder needs."

**Metrics:**
- **Lead time**: Days/weeks → Hours/minutes
- **Deployment frequency**: Quarterly → Daily/hourly
- **Responsiveness**: Slow → Fast

**Result:** Faster time to market

---

### 3. Enhanced System Stability

> "Deploying **smaller, isolated changes** lowers deployment risk, reduces the **change-failure rate**, and facilitates **rapid remediation**, thereby improving **mean time to recovery (MTTR)**."

**Why Smaller = Safer:**
- Easier to understand impact
- Easier to test thoroughly
- Easier to identify root cause if problems occur
- Easier to rollback

**Key Metrics:**
- **Change-failure rate** ↓ (fewer failed deployments)
- **MTTR** ↓ (faster recovery when issues occur)

**Result:** More stable production environment

---

### 4. Shift-Left Quality Assurance

> "Quality controls (testing, security checks, and other cross-functional verifications) are **executed earlier and automatically** within the pipeline, promoting **disciplined engineering practices** and **consistent release readiness**."

**Shift-Left Concept:**
- Traditional: Test at the end
- Shift-Left: Test throughout development
- Earlier = cheaper to fix

**Automated Checks:**
- Unit tests
- Integration tests
- Security scans
- Code quality checks
- Performance tests

**Result:** Higher quality, fewer production bugs

---

### 5. Strengthened Engineering Ownership

> "**End-to-end responsibility** for changes in production reduces handovers and loss of context, fostering **accountability** and sustained attention to **operational excellence**."

**Traditional Model:**
- Dev writes code, throws over wall
- Ops deploys code
- Blame game when things fail

**CD Model:**
- Dev owns code in production
- "You build it, you run it"
- Full accountability

**Result:** Better software, more responsible teams

---

### 6. Alignment with DORA Performance Indicators

> "The practice positively influences **all four key metrics**: deployment frequency, lead time for changes, MTTR, and change-failure rate, supporting **superior software delivery performance**."

**The Four DORA Metrics:**

1. **Deployment Frequency**
   - How often you deploy to production
   - Elite: Multiple times per day
   - CD enables high frequency

2. **Lead Time for Changes**
   - Time from commit to production
   - Elite: Less than one hour
   - CD reduces lead time dramatically

3. **Mean Time to Recovery (MTTR)**
   - How quickly you recover from failures
   - Elite: Less than one hour
   - CD enables fast rollback/fix

4. **Change Failure Rate**
   - Percentage of deployments causing failures
   - Elite: 0-15%
   - CD with good practices reduces failures

**Result:** World-class software delivery performance

---

## Lowering Transaction Cost in Software

**Visual Description:** The slides show a series of diagrams illustrating the concept of transaction costs in software delivery.

### The Economic Principle

**Traditional Software Delivery:**
- High transaction cost per release
- Batching changes to amortize cost
- Long release cycles
- High risk per release

**Continuous Deployment:**
- Low transaction cost per release
- Can deploy individual changes economically
- Short release cycles
- Low risk per release

---

### The Transformation

**Slide Progression Shows:**

1. **High Fixed Cost** (Traditional)
   - Large overhead to release
   - Makes sense to batch changes
   - Infrequent releases

2. **Reducing Fixed Cost** (Automation)
   - Automate deployment process
   - Lower cost per release
   - More frequent releases possible

3. **Variable Cost Dominates** (CD)
   - Fixed cost nearly eliminated
   - Can release single changes
   - Optimal batch size = 1

4. **Continuous Flow** (Modern)
   - Smooth flow of changes
   - Each commit potentially releasable
   - Maximum value delivery

---

## GitHub Actions

### Fundamentals

#### What is GitHub Actions?

> "GitHub Actions provides a **unified automation framework** inside the development lifecycle"

---

#### Capabilities

**Enables:**
- Traditional **CI/CD pipelines**
- **Ancillary automation**:
  - Project management
  - Quality assurance
  - Collaboration workflows

**Significance:**
> "Illustrates modern trends in **developer-centric automation ecosystems**"

Everything in one place, integrated with your code repository.

---

#### Benefits

1. **Automated deployments**
   - Triggered by code changes
   - Consistent process
   - Reliable execution

2. **Version control for deployment scripts**
   - Scripts live with code
   - Versioned together
   - Auditable history

3. **Collaboration and access control**
   - Team-based permissions
   - Review workflows
   - Secure secrets management

4. **Continuous integration and delivery**
   - Build on every commit
   - Test automatically
   - Deploy seamlessly

---

### GitHub Actions: Workflows

#### What is a Workflow?

A workflow is a configurable automated process defined in YAML.

---

#### Workflow Files

**Location:** `.github/workflows/`

**Format:** YAML (Yet Another Markup Language / YAML Ain't Markup Language)

**File Extensions:** `.yml` or `.yaml`

---

#### YAML Characteristics

**Human-readable data serialization:**
- Strict superset of JSON
- Newlines and indentation **carry meaning**
- No braces required
- Comments start with `#`
- Inline comments allowed

**Why YAML for Version Control:**
- Line-oriented diffs
- Easy to review changes
- Merge-friendly
- UTF-8 encoding in GitHub

---

#### YAML Data Types

**Scalar Types:**
- Integers
- Floats
- Strings
- Booleans
- Nulls
- Timestamps

**Collection Types:**
- **Maps** (dictionaries/objects)
- **Sequences** (lists/arrays)

---

#### Workflow Structure

**Key Components:**

1. **Triggered by specific events**
   - Push to branch
   - Pull request opened
   - Label added
   - Schedule
   - Manual trigger

2. **Composed of jobs**
   - Logical grouping of work
   - Can run in parallel or sequence

3. **Jobs consist of steps**
   - Sequential execution
   - Individual commands or actions

4. **Jobs run on runners**
   - GitHub-hosted (Linux, macOS, Windows)
   - Or self-hosted
   - Isolated execution environment

5. **Jobs run in parallel by default**
   - Dependencies defined with `needs`
   - Creates execution graph

---

### GitHub Actions: Workflow Triggers

#### Overview

> "Workflows can be triggered by a **variety of repository events**"

**Purpose:**
- Provides **fine-grained control** over workflow execution
- Based on project activities
- Reduces need for conditional logic inside workflows
- Ensures automation runs **only when meaningful**

---

### Trigger Types

There are three main categories of triggers:

1. **Webhook Triggers** - Repository events
2. **Scheduled Triggers** - Time-based (cron)
3. **Manual Triggers** - On-demand execution

---

## Webhook Triggers

### Definition

> "Webhook triggers respond directly to **repository activity**."

---

### Common Examples

**1. Push events**
- Triggered when code is **pushed to a branch**
- Most common trigger
- Enables CI on every commit

**2. Pull request events**
- Triggered when a pull request is:
  - Opened
  - Updated
  - Merged
  - Closed
- Enables PR validation

**3. Issue events**
- Triggered when an issue is:
  - Opened
  - Labeled
  - Closed
  - Assigned
- Enables issue automation

---

### Filtering

**Branch Filtering:**
- Run only on specific branches
- Example: only on `main` or `develop`

**Path Filtering:**
- Run only when specific files change
- Example: only when `src/**` changes

**Benefits:**
> "This fine-grained control **conserves computational resources** and **avoids redundant runs**."

---

## Scheduled Triggers

### Cron Syntax

> "Scheduled triggers are expressed using **cron syntax**, which consists of **five fields**: minute, hour, day of month, month, and day of week."

---

### Cron Format

```
┌───────────── minute (0 - 59)
│ ┌───────────── hour (0 - 23)
│ │ ┌───────────── day of month (1 - 31)
│ │ │ ┌───────────── month (1 - 12)
│ │ │ │ ┌───────────── day of week (0 - 6) (Sunday to Saturday)
│ │ │ │ │
│ │ │ │ │
* * * * *
```

---

### Cron Capabilities

**Supports:**
- **Ranges**: `1-5` (Monday through Friday)
- **Steps**: `*/15` (every 15 minutes)
- **Lists**: `0,6` (Sunday and Saturday)

---

### Examples

**Every 15 minutes:**
```yaml
schedule:
  - cron: '*/15 * * * *'
```

**Fridays at midnight:**
```yaml
schedule:
  - cron: '0 0 * * 5'
```

**Quarterly on first day of month:**
```yaml
schedule:
  - cron: '0 0 1 */3 *'
```

**Multiple schedules:**
```yaml
schedule:
  - cron: '0 8 * * 1-5'  # Weekdays at 8am
  - cron: '0 0 * * 0'    # Sundays at midnight
```

---

### Use Cases

- Nightly builds
- Periodic cleanup
- Scheduled reports
- Dependency updates
- Security scans

---

## Manual Triggers

### Definition

> "Manual triggers give **users or systems explicit control** over workflow execution."

---

### Two Types

**1. `workflow_dispatch`**
- Enables workflows to be started from:
  - GitHub user interface
  - GitHub CLI
- Can accept **typed input parameters**
- User-initiated

**2. `repository_dispatch`**
- Allows **external systems** to trigger workflows
- Via GitHub API
- Can send custom payloads
- System-initiated

---

### Use Cases

**Workflow Dispatch:**
- Controlled releases
- On-demand tests
- Manual deployments
- Ad-hoc operations

**Repository Dispatch:**
- Integrations with external platforms
- Webhook receivers
- Multi-repo orchestration
- External event responses

---

### Example: Input Parameters

```yaml
on:
  workflow_dispatch:
    inputs:
      environment:
        description: 'Environment to deploy to'
        required: true
        type: choice
        options:
          - development
          - staging
          - production
      version:
        description: 'Version to deploy'
        required: true
        type: string
```

---

## GitHub Actions: Workflow Hands-On

### Example Workflow Structure (Part 1)

**Visual Description:** The slides show annotated workflow YAML

**Key Elements:**

**Trigger Configuration:**
```yaml
on:
  push:
    branches:
      - main
  repository_dispatch:
  workflow_dispatch:
    inputs:
      parameter_name:
        description: 'Description here'
        required: true
```

**Annotations:**
- **Activate on push to main branches** - Automatic trigger
- **Triggered by API** - repository_dispatch for external systems
- **Manual inputs for workflow/action** - workflow_dispatch with parameters

---

### Example Workflow Structure (Part 2)

**Visual Description:** Continuation showing job and step definitions

**Job Configuration:**
```yaml
jobs:
  job-name:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Step name
        run: echo "Hello ${{ inputs.parameter }}"
      - name: Conditional step
        if: github.event_name == 'repository_dispatch'
        run: echo "Triggered by API"
```

**Annotations:**
- **Will execute job on latest Ubuntu machine hosted by GitHub** - Runner specification
- **Steps execute different types of actions** - Mix of marketplace actions and custom scripts
- **Using mustache-style syntax** - `${{ }}` for expressions
- **Condition step** - `if:` for conditional execution
- **Actions from marketplace** - Reusable actions like `actions/checkout`

---

## GitHub Actions: Workflow Deep Dive

### Jobs and Runners

#### Jobs: Core Building Blocks

**Characteristics:**
- Jobs are the **core building blocks** of a workflow
- Each job runs on a **runner**
- Runners may be **GitHub-hosted** or **self-hosted**

---

#### Execution Model

**Parallel by Default:**
- Jobs execute in **parallel** by default
- Fast execution when independent

**Dependencies with `needs`:**
- Use `needs` keyword to express dependencies
- Creates **complex execution graphs**
- Example: `build → test → deploy`

---

#### Runner Images

**GitHub-Hosted:**
- `ubuntu-latest`
- `windows-latest`
- `macos-latest`
- Preconfigured environments
- Regularly updated

**Self-Hosted:**
- Custom setups
- Specific hardware
- Corporate networks
- Cost optimization

---

### Steps and Shells

#### Step Execution

**Characteristics:**
- Steps are **executed sequentially** within a job
- Order matters
- Each step can either:
  - Run a **shell command**
  - Invoke a **reusable action**

---

#### Shell Defaults

**By Default:**
- **Linux and macOS jobs**: Use **Bash**
- **Windows jobs**: Use **PowerShell**

**Other Shells Available:**
- `cmd`
- `python`
- `perl`
- Custom shells

---

#### Multi-line Scripts

**Best Practice:**
```yaml
- name: Multi-line script
  run: |
    echo "Line 1"
    echo "Line 2"
    echo "Line 3"
```

**Why:**
- Written as **literal YAML blocks** for clarity
- Easier to read
- Better version control diffs

---

#### Step Naming

**Importance:**
> "Clear **naming of steps** improves the readability of **workflow logs**, making **debugging easier**."

**Good Practice:**
```yaml
- name: Install dependencies
  run: npm install

- name: Run unit tests
  run: npm test

- name: Build production bundle
  run: npm run build
```

---

### Reusable Actions

#### What Are Reusable Actions?

> "Reusable actions allow **encapsulation of common functionality**."

---

#### How to Use Actions

**Referenced with `uses` keyword:**
```yaml
- uses: actions/checkout@v3
- uses: actions/setup-node@v3
  with:
    node-version: '18'
```

**Identified by:**
- Repository reference: `owner/repo@ref`
- Version reference: tag, branch, or commit SHA

---

#### Best Practices

**1. Pin to Specific Versions:**
```yaml
- uses: actions/checkout@v3  # Tag
- uses: actions/checkout@8e5e7e5a...  # Commit SHA
```

**Why:**
- **Stability** - Consistent behavior
- **Security** - Known code
- Avoid breaking changes

**2. Local Actions:**
```yaml
- uses: ./.github/actions/my-action
```

**Why:**
- Custom, project-specific logic
- Version controlled with code

**3. Container Actions:**
```yaml
- uses: docker://alpine:3.14
```

**Why:**
- Specific environments
- Reproducible builds

---

#### Customization

**Inputs:**
```yaml
- uses: actions/setup-node@v3
  with:
    node-version: '18'
    cache: 'npm'
```

**Environment Variables:**
```yaml
- uses: some-action@v1
  env:
    API_KEY: ${{ secrets.API_KEY }}
```

**Result:**
> "Inputs and environment variables allow actions to be **customized**, increasing **flexibility and reusability**."

---

## GitHub Actions: Matrix Strategy

### What is Matrix Strategy?

> "The matrix strategy allows the **same job to run across multiple parameter combinations** (for example, operating systems, language versions, or toolchains)."

---

### How It Works

**GitHub Actions generates one job per combination:**
- Test across multiple OS
- Test across multiple language versions
- Test across multiple configurations

**Provides broader test coverage** automatically.

---

### Example

```yaml
strategy:
  matrix:
    os: [ubuntu-latest, windows-latest, macos-latest]
    node-version: [14, 16, 18]
```

**Result:** 9 jobs (3 OS × 3 Node versions)

---

### Control Options

**`fail-fast`:**
- Whether failures stop other jobs
- Default: `true`
- Can set to `false` to run all combinations

```yaml
strategy:
  fail-fast: false
  matrix:
    # ...
```

**`max-parallel`:**
- How many jobs run simultaneously
- Controls resource usage
- Prevents overwhelming runners

```yaml
strategy:
  max-parallel: 2
  matrix:
    # ...
```

---

### Use Cases

> "This approach is **essential** for projects that **support multiple environments**."

Examples:
- Cross-platform applications
- Multi-version libraries
- Browser compatibility testing
- Database compatibility testing

---

## GitHub Actions: Expressions

### What Are Expressions?

> "Expressions, written as **`${{ … }}`**, allow **conditional logic** and access to **runtime information**."

---

### Available Contexts

Expressions can reference various contexts:

**1. `github`**
- Event data and metadata
- Repository information
- Workflow details

**2. `env`**
- Environment variables
- Custom or predefined

**3. `matrix`**
- Parameters from matrix build
- Current combination values

**4. `inputs`**
- User-supplied values
- From workflow_dispatch

**5. `needs`**
- Outputs from dependent jobs
- Cross-job communication

---

### Common Uses

**1. Conditions (`if`):**
```yaml
- name: Deploy to production
  if: github.ref == 'refs/heads/main'
  run: ./deploy.sh
```

**2. Dynamic Naming:**
```yaml
- name: Test on ${{ matrix.os }}
  run: npm test
```

**3. Parameter Passing:**
```yaml
- name: Build
  run: npm run build
  env:
    NODE_ENV: ${{ inputs.environment }}
```

---

### Best Practice

> "Their use should remain **clear** and avoid **unnecessary complexity**."

**Good:**
```yaml
if: github.event_name == 'push'
```

**Avoid:**
```yaml
if: |
  github.event_name == 'push' &&
  (github.ref == 'refs/heads/main' ||
   github.ref == 'refs/heads/develop') &&
  !contains(github.event.head_commit.message, '[skip ci]')
```

---

## GitHub Actions: Functions

### Built-in Functions (1/2)

> "GitHub provides **built-in functions** such as `contains`, `startsWith`, `endsWith`, `join`, `toJSON`, and `hashFiles`."

---

### String Functions

**`contains(search, item)`**
- Checks if item exists in search
- Case insensitive
- Returns boolean

**`startsWith(search, item)`**
- Checks if search starts with item
- Case insensitive

**`endsWith(search, item)`**
- Checks if search ends with item
- Case insensitive

---

### Array/Data Functions

**`join(array, separator)`**
- Joins array elements with separator
- Returns string

**`toJSON(value)`**
- Converts value to JSON string
- Useful for debugging

**`hashFiles(pattern)`**
- Creates hash of files matching pattern
- Useful for caching

---

### Status Functions (2/2)

> "Additionally, **status functions** such as `success()`, `failure()`, `cancelled()`, and `always()` allow workflows to **branch based on job outcomes**."

---

### Status Function Details

**`success()`**
- Returns true if all previous steps succeeded
- Default condition for steps

**`failure()`**
- Returns true if any previous step failed
- Useful for cleanup or notifications

**`cancelled()`**
- Returns true if workflow was cancelled
- Handle graceful shutdown

**`always()`**
- Always returns true
- Runs regardless of status

---

### Example Usage

```yaml
- name: Cleanup
  if: always()
  run: ./cleanup.sh

- name: Notify on failure
  if: failure()
  run: ./notify-team.sh

- name: Upload artifacts
  if: success()
  uses: actions/upload-artifact@v3
```

---

### Purpose

> "These functions help implement **robust workflows** that **adapt to real-world conditions**."

Benefits:
- Error handling
- Conditional execution
- Flexible workflows
- Production-ready automation

---

## GitHub Actions: Workflow Commands

### What Are Workflow Commands?

> "Workflow commands enable **steps to interact with the runner**."

---

### Capabilities

**1. Logging Messages:**
```bash
echo "::notice::This is a notice"
echo "::warning::This is a warning"
echo "::error::This is an error"
```

**2. Creating Warnings/Errors with File References:**
```bash
echo "::error file=app.js,line=10::Syntax error"
```

**3. Passing Outputs to Later Steps:**
```bash
echo "version=1.2.3" >> $GITHUB_OUTPUT
```

**4. Setting Environment Variables:**
```bash
echo "API_URL=https://api.example.com" >> $GITHUB_ENV
```

---

### Output Mechanism

**Writing Outputs:**
- Outputs written to `$GITHUB_OUTPUT`
- Persisted for later steps
- Accessed via `steps.<step-id>.outputs.<name>`

**Example:**
```yaml
- name: Get version
  id: version
  run: echo "number=1.2.3" >> $GITHUB_OUTPUT

- name: Use version
  run: echo "Version is ${{ steps.version.outputs.number }}"
```

---

### Environment Variables

**Persisting Across Steps:**
- Written to `$GITHUB_ENV`
- Available in subsequent steps
- Scoped to job

**Example:**
```yaml
- name: Set environment
  run: echo "DEPLOY_ENV=production" >> $GITHUB_ENV

- name: Deploy
  run: ./deploy.sh $DEPLOY_ENV
```

---

### Importance

> "These mechanisms are **fundamental** for **sharing data** and maintaining **traceability** in workflow execution."

Benefits:
- Inter-step communication
- Dynamic workflows
- Data passing
- Auditability

---

## GitHub Actions: Secrets and Variables

### Secrets

#### What Are Secrets?

> "Secrets store **sensitive data** such as API keys and are **encrypted at rest**."

---

#### Security Features

**1. Encrypted Storage:**
- Encrypted at rest in GitHub
- Only decrypted at runtime
- Never exposed in logs

**2. Log Masking:**
- Automatically masked in logs
- Prevents accidental exposure
- Shows as `***`

**3. Runtime Access Only:**
- Can only be decrypted during workflow execution
- Not accessible via API
- Secure by design

---

### Variables

#### What Are Variables?

> "Variables store **non-sensitive configuration values**."

**Differences from Secrets:**
- Not encrypted
- Visible in repository settings
- Can be logged
- For configuration, not credentials

---

### Scope Levels

**Both secrets and variables can be defined at:**

**1. Organization Level:**
- Shared across all repos
- Highest level
- Managed centrally

**2. Repository Level:**
- Specific to one repo
- Override organization values
- Most common

**3. Environment Level:**
- Specific to deployment environment
- Override repository values
- Most specific

**Precedence:**
> "Values at **lower levels override higher ones**."

Environment > Repository > Organization

---

### Best Practices

> "Following **strict naming conventions** and **limiting scope** is essential for **security** and **maintainability**."

**Naming:**
- Use UPPER_SNAKE_CASE
- Descriptive names
- Consistent prefixes

**Scope:**
- Minimum necessary scope
- Environment-specific when possible
- Audit access regularly

---

## GitHub Actions: Debugging

### Development Workflow

> "Workflow development requires **careful iteration**."

---

### Where to Develop

**Greenfield Repositories:**
- Workflows can be authored **directly in main branch**
- No risk of disrupting others
- Quick iteration

**Active Projects:**
- **Safer to work in branches or forks**
- Avoid disrupting the team
- Test before merging

---

### Testing Strategies

**Manual Triggers:**
- Allow **iterative testing**
- Test without pushing
- On-demand execution

**Example:**
```yaml
on:
  workflow_dispatch:
  push:
    branches:
      - feature/new-workflow
```

---

### Enhanced Debugging

**Verbose Logging:**

Set environment variables for debug output:

**`ACTIONS_STEP_DEBUG`:**
- Enables step debug logging
- More detailed output
- Diagnose step failures

**`ACTIONS_RUNNER_DEBUG`:**
- Enables runner debug logging
- Diagnose runner issues
- Infrastructure problems

**Setting:**
- Repository secrets or variables
- Set to `true`

---

### Tooling Support

**Linting Tools:**

**`actionlint`:**
- Command-line linter
- Catches common errors
- Validates syntax

**Editor Extensions:**
- Visual Studio Code plugins
- Syntax highlighting
- IntelliSense
- Real-time validation

---

### Best Practices

> "Linting tools and editor extensions, such as **actionlint** or **Visual Studio Code plugins**, further improve **workflow correctness**."

**Benefits:**
- Catch errors early
- Faster development
- Better quality
- Less debugging time

---

## What is an Action?

### Definition

> "An action is a **self-contained, reusable step** that can be invoked from a workflow. It encapsulates **logic, dependencies, configuration**, and an **interface for inputs and outputs**."

---

### Purpose

> "Actions promote **consistency** and reduce **duplication** by allowing teams to **standardize common tasks**."

**Common Tasks:**
- Checking out source code
- Setting up toolchains
- Running linters
- Performing deployments
- Sending notifications
- Publishing packages

---

### Action Manifest

**Manifest File:**
> "Every action is described by a manifest file named **`action.yml`** (or `action.yaml`)."

---

#### Manifest Contents

The manifest declares:
- **Name** - Action name
- **Description** - What it does
- **Author** - Who created it
- **Branding** - Icon and color
- **Inputs** - Parameters it accepts
- **Outputs** - Values it produces
- **Runs** - Execution model

---

#### File Location

**Fixed Filename:**
> "Because the filename is fixed, each action resides either at the **repository root** or in its **own subfolder**."

**Examples:**
- `action.yml` (root)
- `.github/actions/my-action/action.yml` (subfolder)

---

#### Importance

> "The manifest is the **contract** between the action and its **consumers** and should be treated as a **stable interface**."

Like an API contract - changing it breaks consumers.

---

## Types of Actions

### Three Action Types

> "There are **three different types** of actions:"

1. **Docker container actions**
2. **JavaScript actions**
3. **Composite actions**

---

### 1. Docker Container Actions

**Characteristics:**
- Only run on **Linux** (not Windows or macOS)
- Can retrieve image from Docker library (e.g., Docker Hub)
- Or build from Dockerfile

**Advantages:**
- Consistent environment
- Custom dependencies
- Isolated execution

**Disadvantages:**
- Linux only
- Slower (container startup)
- More complex

---

### 2. JavaScript Actions

**Characteristics:**
- Run directly on the runner using **Node.js**
- **Faster** than container actions
- Cross-platform (Linux, Windows, macOS)

**Advantages:**
- Fast execution
- Platform independent
- Native runner integration

**Disadvantages:**
- Node.js dependency
- Less isolation

---

### 3. Composite Actions

**Characteristics:**
- A **wrapper for other steps or actions**
- Written in YAML
- Reusable workflow fragments

**Advantages:**
- Simple to create
- No coding required
- Combine existing actions

**Disadvantages:**
- Less powerful
- No custom logic

---

### Comparison Summary

| Type | Platforms | Speed | Complexity | Use Case |
|------|-----------|-------|------------|----------|
| **Docker** | Linux only | Slower | High | Custom environment needed |
| **JavaScript** | All | Fast | Medium | General automation |
| **Composite** | All | Fast | Low | Combine existing actions |

---

### Visual Example

**Visual Description:** The slides show a diagram illustrating the three action types and their relationships to workflows.

---

## Practical Guide

### Project Implementation

#### In Your Project:

**1. Implement a pipeline to build software components**
- Build backend
- Build frontend
- Build other components

**Best Practices:**
- Use **Docker multi-stage builds**, if applicable
  - Smaller images
  - Faster builds
  - Layer caching
- Run tests (even if just boilerplate)
  - Validates pipeline works
  - Foundation for real tests

---

**2. Implement a pipeline to deploy software components**

**Deployment Options:**
- Can use **local runners** (self-hosted)
- Follow guide: https://docs.github.com/en/actions/concepts/runners/self-hosted-runners

**Trigger Configuration:**
- Triggered on **push to main or dev**, at minimum
- Can add more sophisticated triggers

**Pipeline Should:**
- Build your projects
- Update containers
- Deploy to target environment

---

### Resources

**Hands-On Materials:**
- Main repository: https://github.com/GitHubActionsInAction/ActionInAction
- Hands-On exercises: https://github.com/GitHubActionsInAction

**Documentation:**
- Self-hosted runners guide
- GitHub Actions documentation
- Community examples

---

# Slide 05: Continuous Delivery Strategies

## Core Principles of Software Delivery

### Create a Repeatable, Reliable Process for Releasing Software

#### The Foundation

**Repeatability and reliability derive from two principles:**

1. **Automate almost everything**
   - Reduce manual effort
   - Ensure consistency
   - Enable speed

2. **Keep everything in version control**
   - Single source of truth
   - Auditability
   - Reproducibility

---

### What Software Deployment Involves

> "Deploying software ultimately involves **three things**:"

---

#### 1. Provisioning and Managing the Environment

**The environment** in which your application will run:
- **Hardware configuration**
  - Compute resources
  - Memory
  - Storage
  - Network

- **Software**
  - Operating system
  - Runtime dependencies
  - Libraries

- **Infrastructure**
  - Load balancers
  - Databases
  - Caching layers

- **External services**
  - APIs
  - Third-party integrations
  - Cloud services

---

#### 2. Installing the Correct Version

- Deploying **the correct version** of your application
- Ensuring version consistency
- Managing multiple versions (blue/green, canary)
- Version rollback capability

---

#### 3. Configuring the Application

- **Application configuration**
  - Environment-specific settings
  - Feature flags
  - API keys and credentials

- **Data or state** it requires
  - Database initialization
  - Seed data
  - Migration scripts

---

### The Automation Goal

**Application Deployment:**
> "Can be implemented using a **fully automated process** from version control"

**Application Configuration:**
> "Can also be a **fully automated process**, with the necessary **scripts and state kept in version control or databases**"

**Key Insight:**
Everything can and should be automated and version controlled.

---

## Core Principle 1: Automate Almost Everything

### "Almost" - What Can't Be Automated?

> "Some tasks **cannot be automated**:"

- **Exploratory testing**
  - Human creativity required
  - Discovering unknowns
  - User experience evaluation

- **User demos**
  - Human presentation
  - Stakeholder engagement
  - Feedback gathering

- **Compliance approvals**
  - Human judgment
  - Legal requirements
  - Regulatory oversight

---

### What CAN Be Automated

> "**Most** of the release process can be automated:"

- **Builds**
  - Compilation
  - Packaging
  - Asset generation

- **Deployments**
  - Environment provisioning
  - Application installation
  - Configuration application

- **Acceptance tests**
  - Functional validation
  - Integration testing
  - End-to-end scenarios

- **Database migrations**
  - Schema updates
  - Data transformations
  - Rollback scripts

- **Network/firewall configs**
  - Security rules
  - Routing configuration
  - DNS updates

---

### Benefits of Automation

> "Automation **reduces repeated manual effort** and **ensures consistency**"

---

### Implementation Strategy

> "**Start gradually**: Automate bottlenecks first, expand over time"

**Approach:**
1. Identify biggest pain points
2. Automate highest-value tasks first
3. Iterate and expand
4. Continuous improvement

---

### The Vision

> "Automation is **essential for an efficient deployment pipeline**. People get what they need **at the push of a button**."

**Result:**
- Self-service deployments
- Fast feedback
- Consistent process
- Reduced toil

---

## Core Principle 2: Keep Everything in Version Control

### What to Keep in Version Control

> "Keep **everything needed** to build, deploy, test, and release under version control:"

---

#### Documentation and Requirements
- **Requirement documents**
  - User stories
  - Specifications
  - Design docs

- **Test scripts**
  - Test cases
  - Test data
  - Test procedures

- **Automated tests**
  - Unit tests
  - Integration tests
  - E2E tests

---

#### Configuration and Scripts
- **Deployment scripts**
  - Deployment automation
  - Rollback procedures
  - Health checks

- **Database scripts**
  - Schema definitions
  - Migration scripts
  - Seed data

- **Network configuration**
  - Infrastructure as code
  - Firewall rules
  - Load balancer config

- **Stack configuration**
  - Container definitions
  - Orchestration configs
  - Service manifests

---

#### Dependencies and Tools
- **Libraries**
  - Third-party dependencies
  - Version locks
  - Dependency manifests

- **Toolchains**
  - Build tools
  - Compilers
  - Utilities

- **Technical documentation**
  - Architecture docs
  - Runbooks
  - Troubleshooting guides

---

### Build Identification

> "Each build should have a **single identifier** linking all relevant files (e.g., **build number** or **change set**)"

**Why Important:**
- Traceability
- Reproducibility
- Debugging
- Audit trail

**Examples:**
- Git commit SHA
- Build number
- Version tag
- Release identifier

---

### The New Team Member Test

> "A new team member should be able to:"

1. **Check out the repository**
   - Single source of truth
   - Complete codebase

2. **Run a single command** to build and deploy the application
   - No tribal knowledge required
   - Documented process
   - Fully automated

**If this works:**
- Good documentation ✓
- Good automation ✓
- Good version control ✓

**If this doesn't work:**
- Missing pieces
- Tribal knowledge
- Manual steps

---

## Core Principle 3: Done Means Released

### The Definition of Done

> "There is no **'80% done.'** Things are either **done**, or they are **not**."

---

### Estimating Remaining Work

> "It is **possible** to estimate the work remaining before something is done. But those will **only ever be estimates**."

**Reality:**
- Can estimate
- Will be wrong
- Always uncertainty
- Plan accordingly

---

### Team Responsibility

> "This principle has an interesting **corollary**:"

**Three Key Insights:**

1. **Individual Limitation:**
   > "It is **not in the power of one person** to get something done."

2. **Team Collaboration:**
   > "It requires a **number of people on a delivery team to work together** to get anything done."

3. **Early Collaboration:**
   > "That's why it's so **important for everybody to work together from the beginning**."

---

### Whole Team Accountability

> "It's also why the **whole delivery team is responsible** for delivering"

**Not:**
- Dev done, waiting for Ops
- Code done, waiting for testing
- Testing done, waiting for release

**Instead:**
- Everyone responsible until in production
- Cross-functional ownership
- Collective accountability

---

## Software Delivery Scenario

### The Business Context

**Scenario:**
> "Client liked the product, now he wants more features."

---

### Critical Questions to Answer

**1. Delivery Method:**
> "How should we deliver new features to him?"

**2. Release Strategy:**
> "Should we release everything at once or gradually?"

**3. Update Policy:**
> "Do we force updates, or give users a choice?"

**4. Risk Management:**
> "How do we minimize risk while keeping users happy?"

**5. Decision Metrics:**
> "What metrics or feedback should guide our release decisions?"

---

### The Central Dilemma

> "Would you rather **risk upsetting a few users** with automatic updates or **risk losing everyone** by delaying new features?"

**Tension:**
- Speed vs Safety
- Innovation vs Stability
- Push vs Pull
- Automation vs Control

**No Perfect Answer:**
- Context dependent
- User expectations matter
- Risk tolerance varies
- Industry norms differ

---

## Feature Toggling

### Overview

#### Definition

> "Feature toggling (also called **feature flags**) is a software development technique that allows features to be **turned on or off without deploying new code**."

---

### Core Capability

> "Instead of releasing a new feature to **all users immediately**, it enables **control** over **who can access it** and **when**."

**Key Insight:**
Decouples **deployment** from **release**

**Deployment:**
- Code goes to production
- Infrastructure change
- Technical event

**Release:**
- Feature becomes available to users
- Business decision
- User-facing event

---

## Feature Toggling: Motivation

### Why Use Feature Toggles?

---

### 1. Continuous Delivery

> "Ship code to production **even if features aren't ready**."

**Benefits:**
- Keep deploying regularly
- No long-lived branches
- Integration is continuous
- Features hidden until complete

---

### 2. A/B Testing & Experimentation

> "Test features on a **subset of users**."

**Benefits:**
- Gather real usage data
- Compare variants
- Data-driven decisions
- Measure impact

---

### 3. Safe Rollbacks

> "Disable a feature **instantly** if issues appear."

**Benefits:**
- No redeployment needed
- Instant mitigation
- Reduce MTTR
- Low-risk releases

---

### 4. Targeted Releases

> "Roll out features to **specific users, regions, or accounts**."

**Benefits:**
- Gradual rollouts
- Geographic rollouts
- Customer-specific features
- Premium features

---

### 5. Decouple Deployment from Release

> "Code can be **deployed independently** of feature activation."

**Benefits:**
- Deploy anytime
- Release when ready
- Technical and business cadences separated
- Flexibility

---

## Feature Toggling: Four Main Types

### 1. Release Toggles

**Purpose:**
> "Control when a feature is **visible**."

**Lifecycle:**
- **Temporary** - removed after full release
- Short to medium lived
- Deleted when feature complete

**Example:**
> "Releasing a new payment system to **10% of users**."

**Use Cases:**
- Gradual rollouts
- Feature completion
- Risk mitigation
- Dark launches

---

### 2. Experiment Toggles

**Purpose:**
> "For **A/B testing**. Determine which variant of a feature **performs better**."

**Lifecycle:**
- Short lived
- Removed after experiment concludes
- Data-driven decisions

**Example:**
> "Two versions of a signup form."

**Use Cases:**
- A/B testing
- Multivariate testing
- User research
- Optimization

**Typical Flow:**
1. Deploy both variants
2. Split traffic
3. Collect metrics
4. Analyze results
5. Keep winner, remove loser
6. Remove toggle

---

### 3. Ops Toggles (Operational Toggles)

**Purpose:**
> "Control **operational aspects** rather than functionality. Useful for **performance tuning**, enabling/disabling features under load."

**Lifecycle:**
- Can be long-lived
- Adjusted as needed
- System health focused

**Example:**
> "Toggle caching or logging level."

**Use Cases:**
- Performance optimization
- Circuit breakers
- Rate limiting
- Graceful degradation
- Emergency switches

**Common Scenarios:**
- Disable expensive feature under high load
- Enable verbose logging for debugging
- Switch to cached data when DB slow
- Shed load during incidents

---

### 4. Permission Toggles (or Permanent Toggles)

**Purpose:**
> "Enable features for **specific users or groups**."

**Lifecycle:**
- Can be **long-lived** or permanent
- Part of business logic
- Entitlement management

**Example:**
> "Premium features enabled for **paying customers**."

**Use Cases:**
- Premium/freemium features
- Beta programs
- User roles/permissions
- Enterprise features
- Geographic restrictions

**Characteristics:**
- Business-driven
- User-specific
- May become permanent
- Part of authorization system

---

### Feature Toggle Types Summary

| Type | Purpose | Lifecycle | Example |
|------|---------|-----------|---------|
| **Release** | Control visibility | Temporary | Gradual rollout to 10% |
| **Experiment** | A/B testing | Short-lived | Two signup forms |
| **Ops** | Performance tuning | Long-lived | Toggle caching |
| **Permission** | User entitlements | Permanent | Premium features |

---

## Progressive Delivery Strategies

### Overview

Progressive delivery is about delivering software changes gradually, with increasing exposure and confidence.

**Key Strategies:**
1. Eat Your Own Dog Food
2. Canary Releases
3. Dark Launches
4. Gradual Rollouts
5. A/B Testing
6. Blue/Green Deployments

---

## Strategy 1: Eat Your Own Dog Food

### Concept

> "**Idea:** Dev team (and internal staff) use the newest version internally"

---

### Process

**Step 1:** Deploy new version to internal users
- Development team
- QA team
- Internal staff
- Company employees

**Step 2:** Monitor and validate
- Collect feedback
- Observe behavior
- Fix issues

**Step 3:** If everything is as expected
> "Roll it out to further users"

---

### Benefits

- **Real-world testing** by people who understand the product
- **Early issue detection** before customer impact
- **Team confidence** from using own product
- **Dogfooding culture** - team invested in quality

---

### Also Known As

- "Dogfooding"
- "Internal beta"
- "Staff rollout"

---

## Strategy 2: Canary Releases

### Concept

> "**Idea:** Release a new version to a **subset of users first**, while all other users interact with the **old, stable version**"

---

### The Name Origin

> "The name comes from the **'canary in a coal mine'**"

**Historical Context:**
> "Miners used canaries to detect toxic gases before it was too late. If the canary showed signs of distress, the miners knew there was danger — the same principle applies here."

**Software Analogy:**
- Small group = canary
- Shows problems first
- Others protected
- Early warning system

---

### User Selection Criteria

User selection based on:

**1. Geographic location:**
- Region
- Country
- Data center proximity

**2. Role:**
- Admin users
- Early adopters
- Stable/conservative users
- Beta testers

**3. Random basis:**
- e.g., 1% of traffic
- 5% of users
- Statistical sampling

---

### Implementation Levels

> "Canary releases can be implemented at **different levels**:"

---

#### a) Infrastructure / Load Balancer Level

- **Traffic routed selectively** using reverse proxies or load balancers
- Network-level routing
- Fast switching
- No application code changes

**Example:**
```
Load Balancer
├─> 95% → Version 1.0 (stable)
└─> 5%  → Version 2.0 (canary)
```

---

#### b) Application Level

- **The application decides** which users get canary version
- Based on: user ID, region, feature flag, etc.
- **Often combined with feature toggles**
- More granular control

**Example:**
```javascript
if (userInCanaryGroup(user)) {
  return newFeature();
} else {
  return oldFeature();
}
```

---

#### c) CI/CD Pipeline Level

- **Orchestrated directly in the pipeline**
- Automated promotion
- Metric-driven decisions
- Integrated with monitoring

---

### Monitoring is Crucial

> "**Monitoring is crucial** for canary releases. **Key indicators include:**"

**1. Error rates**
- 5xx errors
- Exception counts
- Failed requests

**2. Response times**
- Latency percentiles (p50, p95, p99)
- Timeout rates
- Slow queries

**3. CPU/memory usage**
- Resource consumption
- Memory leaks
- CPU spikes

**4. User satisfaction metrics**
- User feedback
- Support tickets
- Crash reports

**5. Business KPIs**
- Conversion rate
- Retention
- Revenue impact
- User engagement

---

### Automated Canary Analysis (ACA)

> "Automation can **compare canary metrics to the baseline** and **automatically decide** whether to continue or rollback"

**Known as:** Automated Canary Analysis (ACA)

**How it works:**
1. Define success criteria
2. Collect metrics from both versions
3. Statistical comparison
4. Automated decision
5. Promote or rollback

**Benefits:**
- No manual monitoring
- Objective decisions
- Fast response
- 24/7 operation

---

### Canary Release Example

> "Let's say **version 2.0** of an API is ready."

**Step 1:** Deploy it to **5% of users**
- Small initial exposure
- Limited blast radius
- Real-world validation

**Step 2:** Monitor latency, error rate, CPU load, etc.
- Continuous observation
- Compare to baseline
- Alert on anomalies

**Step 3:** If metrics are healthy
- → Increase rollout to **20%, 50%, 100%**
- Gradual expansion
- Confidence building

**Step 4:** If metrics degrade
- → Rollback to **version 1.9** for everyone
- Fast mitigation
- No user impact (most users)

---

### Key Objectives

- **Reduce risk** of production failures
- **Validate functionality** under real-world conditions
- **Gather early feedback** from a small audience
- **Enable fast rollback** if the release introduces issues

---

## Strategy 3: Dark Launches

### Concept

> "A deployment strategy where a feature is **released to production** but **not yet exposed to end-users**"

---

### Key Characteristics

**Feature is:**
- Deployed to production ✓
- Not visible to users ✗
- Running in background
- Gathering data
- Testing infrastructure

**Often combined with:**
- Feature toggles (disabled by default)
- Hidden endpoints
- Internal-only access

---

### Purpose

> "Used to test **scalability, performance, and stability**"

---

### Goals

- **Identify performance bottlenecks** before release
- **Detect infrastructure or integration issues**
- **Validate resource usage** under real conditions
- **Ensure smooth user experience** once the feature is public

---

### Core Idea

> "Deploy new features into production, keep them invisible to users, observe how they behave under real production load"

**Benefits:**
- Production environment testing
- Real load conditions
- No user impact
- Safe experimentation

---

### Common Use Cases

**1. Load Testing New Features:**
- Send production traffic to new code
- Observe resource consumption
- Validate scalability

**2. Database Migration:**
- Dual-write to old and new DB
- Validate new schema
- Compare results

**3. Algorithm Testing:**
- Run new algorithm alongside old
- Compare outputs
- Validate correctness

**4. Infrastructure Changes:**
- New caching layer
- New service
- Validate integration

---

## Strategy 4: Gradual Rollouts

### Concept

> "**Gradually increase** the number of users assigned to the newest version. **Continue the rollout step by step** until it fully replaces the previous version."

---

### Benefits

> "Allows **early detection of issues** before full release"

---

### Workflow

**1. Start with a small subset of users**
- 1% or 5% initially
- Limited exposure
- Early validation

**2. Monitor performance and errors**
- Track metrics
- Compare to baseline
- Watch for anomalies

**3. Gradually expand user percentage**
- 1% → 5% → 10% → 25% → 50% → 100%
- Stepwise increase
- Build confidence

**4. Once stable, complete the rollout**
- Full deployment
- New version becomes default
- Old version retired

---

### Purpose

- **Test scalability and stability** under real-world conditions
- **Observe system behavior** with increasing load
- **Minimize risk** of widespread failure

---

### Gradual Rollout vs Canary Release

**Similarities:**
- Both use subset of users
- Both monitor metrics
- Both can rollback

**Differences:**

**Canary:**
- Fixed small percentage initially
- Focus on validation
- Then promote fully or rollback

**Gradual Rollout:**
- Continuous percentage increase
- Focus on scale
- Multiple expansion steps

---

## Strategy 5: A/B Testing

### Concept

> "**A/B Testing compares two or more versions** of a feature or interface"

---

### How It Works

**1. Users are randomly divided into groups** (A, B, etc.)
- Random assignment
- Statistically significant samples
- Control group vs treatment group(s)

**2. Each group experiences a different version**
- Group A: Version A (often current/control)
- Group B: Version B (new variant)
- Group C, D, etc.: Additional variants

**3. Results determine which version performs better**
- Data-driven decision
- Statistical analysis
- Objective comparison

---

### Purpose

- **Evaluate user behavior** and measure impact of design or functional changes
- **Validate hypotheses** before full rollout
- **Support evidence-based decision-making**

---

### Process Overview

**Step 1:** Define a goal or success metric
- Click rate
- Engagement time
- Conversion rate
- Revenue per user
- Retention rate

**Step 2:** Split users into test groups
- Random assignment
- Balanced distribution
- Representative samples

**Step 3:** Deploy each variant
- Simultaneous deployment
- Same time period
- Same external conditions

**Step 4:** Collect and analyze data statistically
- Statistical significance
- Confidence intervals
- Effect size

**Step 5:** Decide which version to adopt or discard
- Choose winner
- Remove variants
- Apply learnings

---

### Visual Comparison

**Traditional Release:**
```
All users → Same version
```

**A/B Testing:**
```
50% users → New version (B)
50% users → Old version (A)
```

Or:
```
33% users → Version A (control)
33% users → Version B (variant 1)
33% users → Version C (variant 2)
```

---

### A/B Testing vs Progressive Rollout

**Can be used together:**
> "Can be used within a progressive rollout to test user reactions"

**Focus Difference:**
- **A/B Testing** focuses on **comparison**
  - Which is better?
  - User preference
  - Behavioral impact

- **Progressive rollout** focuses on **scale and stability**
  - Can it handle load?
  - Infrastructure ready?
  - Performance acceptable?

---

### Combined Approach

> "Combining both ensures **functional and performance validation**"

**Example:**
1. A/B test two variants (compare)
2. Winner progresses to gradual rollout (scale)
3. Both validation types achieved

---

### Organizational Benefits

> "A/B Testing helps organizations:"

- Make **data-backed decisions**
- Understand **user preferences**
- Deliver **better-performing features**

---

## Strategy 6: Blue/Green Deployments

### Concept

> "Maintain **two identical production environments:**"

- **Green:** current, stable version
- **Blue:** new version under preparation

(Note: Color names are arbitrary and sometimes reversed)

---

### The Router

> "The **router** directs traffic to either environment"

**Traffic Routing:**
- Can be load balancer
- Can be DNS
- Can be reverse proxy
- Instant switching capability

---

### Release Mechanism

> "**Switching traffic** effectively releases the new version"

**No Code Deployment During Release:**
- Code already deployed to Blue
- Release = traffic switch
- Nearly instantaneous
- No downtime

---

### Release Process

**Step 1:** Deploy the new version to the inactive environment (e.g., Blue)
- Blue is idle
- No user traffic
- Safe deployment

**Step 2:** Test the new version in isolation
- Full production environment
- No user impact
- Comprehensive validation
- Smoke tests
- Integration tests

**Step 3:** Once validated, switch traffic from Green → Blue
- Instant cutover
- All users moved simultaneously
- Blue becomes active
- Green becomes idle

**Step 4:** Keep the previous environment ready for instant rollback
- Green still running
- Can switch back instantly
- Safety net
- Monitor Blue for issues

---

### Advantages

**1. Enables zero-downtime releases**
- Instant traffic switch
- No user interruption
- Seamless transition

**2. Supports quick rollback in case of errors**
- Just switch traffic back
- No redeployment needed
- Seconds to rollback

**3. Simplifies testing under production-like conditions**
- Exact production environment
- Real infrastructure
- Realistic validation

---

### Considerations

**1. Databases are shared or duplicated across environments**
- Challenge: Database state
- Cannot easily switch DB
- Schema changes tricky

**2. Switching requires data migration or synchronization**
- Database migrations must be backward compatible
- Or run before traffic switch
- Careful planning needed

**3. Consistency and latency must be carefully managed**
- Session state
- In-flight transactions
- Cache coherence
- Geographic distribution

---

### Database Strategies

**Shared Database:**
- Both Blue and Green use same DB
- Simpler architecture
- Schema changes must be compatible with both versions
- Migration runs before deploy

**Duplicated Database:**
- Each environment has own DB
- Data synchronization required
- More complex
- True isolation

---

## Progressive Delivery Strategies: Relationship

### Comparison Table

| Strategy | Key Focus | Rollback Type | User Exposure |
|----------|-----------|---------------|---------------|
| **Progressive Rollout** | Gradual exposure | Partial | Controlled increase |
| **Canary Release** | Early validation | Partial | Selected users |
| **Blue-Green Deployment** | Full environment swap | Instant | Complete switch |
| **A/B Testing** | Behavioral comparison | N/A | Parallel testing groups |

---

### Key Insights

**Progressive Rollout:**
- Focus: Risk mitigation through gradual scale
- Users: Percentage gradually increases
- Rollback: Reduce percentage or stop

**Canary Release:**
- Focus: Validation with small group first
- Users: Small fixed percentage initially
- Rollback: Remove canary deployment

**Blue-Green:**
- Focus: Zero-downtime with instant switch
- Users: Everyone at once
- Rollback: Switch traffic back

**A/B Testing:**
- Focus: Comparing variants for best outcome
- Users: Split into parallel groups
- Rollback: Not applicable (choose winner)

---

### Complementary Strategies

These strategies can be **combined**:

**Example 1:** Canary + Blue/Green
- Blue/Green for instant rollback capability
- Canary to validate new version first

**Example 2:** A/B Test + Progressive Rollout
- A/B test to choose best variant
- Progressive rollout winner to scale

**Example 3:** Dark Launch + Canary
- Dark launch to test infrastructure
- Canary to validate user experience

---

## Continuously Releasing User-Installed Software

### The Challenge

> "Releasing a new version of your application to a **production environment you control** is one thing."

> "Releasing a new version of software **installed by users on their own machines** (client-installed software) is another."

**Key Difference:**
- Server software: You control deployment
- Client software: Users control deployment

---

### Issues to Consider

There are **several issues** to consider:

1. **Managing the upgrade experience**
   - User interface
   - Interruption timing
   - Communication

2. **Migrating binaries, data, and configuration**
   - Files replacement
   - Data format changes
   - Settings migration
   - Backward compatibility

3. **Testing the upgrade process**
   - Multiple version combinations
   - Partial upgrades
   - Failed upgrades

4. **Getting crash reports from users**
   - Telemetry
   - Error reporting
   - Privacy considerations

---

## The Problem with Multiple Versions

> "**Multiple versions** of software 'in the wild' cause **support headaches**."

---

### Challenges

**Debugging Issues:**
- "Which version are you running?"
- Cannot reproduce in current version
- Need to build old versions
- > "Debugging requires **reverting to specific historical versions**"

**Testing Burden:**
- Test all version combinations
- Compatibility matrix explosion
- Expensive and time-consuming

**Support Complexity:**
- Different bugs per version
- Different features per version
- Fragmented user base

---

### The Ideal State

> "**Ideally:** all users run the **latest stable version**."

**Benefits:**
- Single version to support
- All users have latest features
- All users have latest bug fixes
- Simplified testing

---

### The Goal

> "**Goal:** make upgrades **painless and seamless**."

If upgrades are painless, users will upgrade.
If users upgrade, everyone runs latest version.
If everyone runs latest, support is easier.

---

## Upgrade Strategies for Client Software

### Strategy 1: Check and Prompt for Download

> "Check for new version, **prompt user to download & upgrade**."

**How it works:**
1. App checks for updates
2. Notifies user update available
3. User downloads update
4. User installs update manually

**Advantages:**
- Easy to implement
- Simple architecture
- User has control

**Disadvantages:**
- Frustrating for users
- Manual steps
- Many users ignore
- Leads to version fragmentation

---

### Strategy 2: Download in Background, Prompt for Installation

> "Download in background, **prompt for installation**."

**How it works:**
1. App checks for updates silently
2. Downloads update in background
3. Prompts user when ready to install
4. User approves installation

**Advantages:**
- Less intrusive than Strategy 1
- Download time doesn't delay user
- User still has control

**Disadvantages:**
- Repeated prompts can annoy
- Users still can ignore
- Still manual approval step
- Still leads to some fragmentation

---

### Strategy 3: Silent Download and Upgrade on Restart

> "Download silently, **upgrade on restart** (Firefox model)."

**How it works:**
1. App downloads update silently in background
2. Prepares update for installation
3. On next app restart, update applies automatically
4. No user interaction required

**Advantages:**
- Most user-friendly **if done correctly**
- No interruption during work
- Automatic upgrades
- Minimal version fragmentation

**Disadvantages:**
- User not aware of updates
- Surprise changes
- If upgrade fails, user stuck

---

## The Pitfalls of User Choice

> "Users often **delay upgrades** due to **fear of breaking software**."

---

### User Psychology

**User Thinking:**
- "Current version works"
- "What if update breaks it?"
- "I'm busy now"
- "Maybe later"

**Result:**
> "Providing choice can signal **lack of developer confidence**."

**User Interpretation:**
- "If devs aren't confident, why should I upgrade?"
- "If it's optional, maybe it's risky"

---

### The Rational Decision

> "**Rational user decision:** avoid upgrading if process seems risky."

**If upgrade:**
- Requires manual steps → seems complex → seems risky
- Asks for permission → implies uncertainty → seems risky
- Can be postponed → implies not critical → skip it

**Result:** Users don't upgrade

---

## The Correct Approach

> "Make upgrades **bulletproof and silent**."

---

### Four Key Principles

**1. Automatic and Silent:**
> "Make upgrades bulletproof and silent."

- No user intervention
- Happens automatically
- No interruption

---

**2. Automatic Rollback:**
> "Automatically revert to previous version if upgrade fails."

- Detect upgrade failure
- Rollback automatically
- User unaware of problem
- No broken software

---

**3. Silent Error Reporting:**
> "Report failures to development team **without bothering the user**."

- Telemetry/crash reports
- Automatic error submission
- Team gets notification
- User experience unaffected

---

**4. User Prompt Only When Necessary:**
> "Only prompt users if **corrective action is needed**."

- 99% of time: silent
- Only ask user if truly needed
- "We need to restart app to complete update"
- "Update requires permission change"

---

### The Philosophy

**Build Confidence:**
- Make upgrades so reliable users don't worry
- Prove it works consistently
- Build trust over time

**Reduce Friction:**
- Remove every obstacle
- Make it automatic
- Make it invisible

**Result:**
- Users always on latest version
- No fragmentation
- Better product
- Easier support

---

## Don't Delete the Old Files, Move Them

### The Principle

> "Make sure you **keep a copy of the previous version around**"

---

### Critical Steps

**Step 1: Clear Out Old Files**
> "Then, ensure that you **clear out the old files** before deploying the new version."

**Why:**
> "If a **stray file from the old deployment** is still lying around in the newly deployed version, it can cause **hard-to-track-down bugs**."

**Examples of Problems:**
- Old configuration file
- Deprecated library
- Conflicting class file
- Orphaned data file

---

### UNIX Best Practice

> "A good practice in the UNIX world is to **deploy each version of the application into a new directory** and have a **symbolic link** that points to the current version"

---

#### How It Works

**Directory Structure:**
```
/app/
├── v1.0.0/          # Old version
├── v1.1.0/          # Previous version
├── v1.2.0/          # Current version
└── current -> v1.2.0/  # Symlink to current
```

**Deployment Process:**
1. Deploy new version to new directory (`v1.2.0`)
2. Test new version
3. Update symlink: `current -> v1.2.0`
4. Done

---

#### Benefits

**Deploying:**
> "Deploying... is simply a matter of changing the symbolic link to point to the [new] version."

- Atomic operation
- Instant switch
- No file copying
- Very fast

**Rolling Back:**
> "...rolling back versions is simply a matter of changing the symbolic link to point to the **previous version**."

- Instant rollback
- Just change symlink
- Previous version intact
- No redeployment

---

### Network Version: Blue/Green Deployments

> "The **network version** of this is to have **different versions sitting on different servers** or **different port ranges on the same server**."

**Examples:**

**Different Servers:**
```
server1.example.com:80  → Version 1.2.0
server2.example.com:80  → Version 1.1.0
```

**Different Ports:**
```
localhost:8080  → Version 1.2.0
localhost:8081  → Version 1.1.0
```

**Switching:**
> "Switch between them using a **reverse proxy**"

**Example with Reverse Proxy:**
```
Load Balancer
├─> server1:80 (v1.2.0) ✓ Active
└─> server2:80 (v1.1.0) ✗ Standby
```

**This is Blue/Green Deployments!**

---

## Practical Guide

### Hands-On Learning

**Install a local version to learn:**
> "Install a local version to learn and later deploy it on your server."

**Tool:** Flagsmith (Feature Flag Management)
- Repository: https://github.com/flagsmith/flagsmith
- Documentation: https://docs.flagsmith.com/quickstart

---

### What is Flagsmith?

**Feature Flag Management Platform:**
- Open source
- Self-hosted or cloud
- Manage feature toggles
- A/B testing support
- Remote configuration

---

### Getting Started

**Quick Start:**
- Follow guide: https://docs.flagsmith.com/quickstart
- Docker-based deployment
- Simple setup
- Full-featured

---

### Learning Path

**1. Local Installation:**
- Install locally
- Experiment safely
- Learn features
- Understand concepts

**2. Practice:**
- Create feature flags
- Test toggling
- Try user segments
- Experiment with A/B tests

**3. Deploy to Server:**
- Once comfortable
- Deploy to project
- Production use
- Team collaboration

---

# Study Tips and Exam Preparation

## For Slide 04: Continuous Deployment

### Critical Concepts to Master

#### 1. Understand the Dev vs Ops Problem
- "Wall of confusion"
- Manual processes
- Environment differences
- Why this is problematic

#### 2. CI/CD Pipeline Fundamentals
- Definition of pipeline
- Key characteristics
- Event triggers
- Environment consistency

#### 3. Continuous Integration (CI)
- Definition and purpose
- Frequent integration benefits
- Automated pipelines
- Artifact creation
- Feedback loops

#### 4. Continuous Deployment vs Continuous Delivery
- **Critical distinction:**
  - CD (Delivery): Manual approval before production
  - CD (Deployment): Fully automated to production
- The "button" differentiator

#### 5. Benefits of CD
- All six benefits in detail
- DORA metrics (know all four)
- Transaction cost reduction
- Shift-left quality

#### 6. GitHub Actions Comprehensive Knowledge
- Workflow structure (YAML)
- Trigger types (webhook, scheduled, manual)
- Jobs and runners
- Steps and shells
- Matrix strategy
- Expressions and functions
- Secrets vs variables
- Action types (Docker, JavaScript, Composite)

---

## For Slide 05: Continuous Delivery Strategies

### Critical Concepts to Master

#### 1. Core Principles of Software Delivery
- The three things deployment involves
- Automate almost everything
- Keep everything in version control
- "Done means released"

#### 2. Feature Toggling
- Definition and purpose
- **Four types** (Release, Experiment, Ops, Permission)
- Know characteristics and examples for each
- Lifecycle of each type

#### 3. Progressive Delivery Strategies
- **All six strategies:**
  1. Eat your own dog food
  2. Canary releases (know in depth!)
  3. Dark launches
  4. Gradual rollouts
  5. A/B testing
  6. Blue/Green deployments

#### 4. Canary Releases (Deep Dive)
- Origin of name
- Implementation levels (infrastructure, application, pipeline)
- Monitoring metrics
- Automated Canary Analysis
- Example process (5% → 20% → 50% → 100%)

#### 5. Strategy Comparison
- Know comparison table
- Key focus of each
- Rollback types
- User exposure
- When to use which

#### 6. User-Installed Software
- Challenges vs server software
- Three upgrade strategies
- Why user choice is problematic
- Correct approach (bulletproof, silent)
- Don't delete old files (symlink approach)

---

## Key Numbers and Terms to Remember

### DORA Metrics (Four Keys)
1. **Deployment Frequency** - How often deploy
2. **Lead Time for Changes** - Commit to production
3. **Mean Time to Recovery (MTTR)** - Time to recover from failure
4. **Change Failure Rate** - % of deployments causing failure

### Feature Toggle Types (Four)
1. **Release** - Control visibility (temporary)
2. **Experiment** - A/B testing (short-lived)
3. **Ops** - Performance tuning (long-lived)
4. **Permission** - User entitlements (permanent)

### Progressive Delivery Strategies (Six)
1. Eat your own dog food
2. Canary releases
3. Dark launches
4. Gradual rollouts
5. A/B testing
6. Blue/Green deployments

### GitHub Actions Components
- **Workflows** - YAML files in .github/workflows/
- **Jobs** - Parallel by default, use `needs` for dependencies
- **Steps** - Sequential within jobs
- **Runners** - GitHub-hosted or self-hosted
- **Actions** - Reusable steps (Docker, JavaScript, Composite)

---

## Common Exam Question Types

### Comparison Questions
- "Compare CI vs CD (Delivery) vs CD (Deployment)"
- "Canary vs Blue/Green vs Gradual Rollout"
- "Feature toggle types - when to use each"
- "GitHub-hosted vs self-hosted runners"

### Scenario Questions
- "Your deployment failed in production. How do you handle it with Blue/Green vs Canary?"
- "Client wants to test two different UIs. Which strategy?"
- "You need to validate infrastructure under production load without user impact. Which strategy?"

### Implementation Questions
- "Design a GitHub Actions workflow that..."
- "Implement a canary release strategy for..."
- "Create feature toggles for..."

### Conceptual Questions
- "Why is 'done means released' important?"
- "What problems does feature toggling solve?"
- "Explain the 'wall of confusion' between Dev and Ops"

---

## Important Distinctions to Understand

### CI vs CD vs CD
- **CI** - Continuous Integration (to main branch)
- **CD** - Continuous Delivery (manual button to production)
- **CD** - Continuous Deployment (automatic to production)

### Deployment vs Release
- **Deployment** - Code to production environment
- **Release** - Feature available to users
- Feature toggles decouple these!

### Canary vs Gradual Rollout
- **Canary** - Small fixed % first, then all-or-nothing
- **Gradual** - Continuous % increase over time

### A/B Testing vs Other Strategies
- **A/B Testing** - Comparison (which is better?)
- **Others** - Validation (does it work at scale?)

---

## Connections Between Slides 04 and 05

### Flow of Concepts

**Slide 04 → Slide 05:**
- **CD foundation** → Progressive delivery strategies
- **GitHub Actions** → Implement feature toggles and deployments
- **Automation principles** → Core principles of delivery
- **DORA metrics** → Measured by delivery strategies

### Practical Implementation

**How They Connect:**
1. Use **GitHub Actions** (Slide 04) to implement **Blue/Green** (Slide 05)
2. Use **CI/CD pipelines** (Slide 04) to deploy **Canary releases** (Slide 05)
3. **Feature toggles** (Slide 05) enable **continuous deployment** (Slide 04)
4. **Core principles** (Slide 05) guide **pipeline design** (Slide 04)

---

## Real-World Application

### In Your Project

**From Slide 04:**
- Implement GitHub Actions workflows
- Build and deploy pipelines
- Automated testing
- Self-hosted runners

**From Slide 05:**
- Implement feature toggles (Flagsmith)
- Choose deployment strategy
- Plan rollout approach
- Define "done"

**Integration:**
- Pipeline deploys code
- Feature toggle controls release
- Monitor metrics
- Gradual rollout if appropriate

---

## Exam Preparation Checklist

### Slide 04 Knowledge
- ✓ Can explain Dev vs Ops problem
- ✓ Know CI/CD pipeline components
- ✓ Understand CI fundamentals
- ✓ Distinguish CD Delivery vs Deployment
- ✓ List all six CD benefits
- ✓ Know all four DORA metrics
- ✓ Understand GitHub Actions structure
- ✓ Know three trigger types
- ✓ Understand matrix strategy
- ✓ Know three action types
- ✓ Understand secrets vs variables

### Slide 05 Knowledge
- ✓ Know three core principles
- ✓ Understand all four feature toggle types
- ✓ Can explain all six progressive delivery strategies
- ✓ Deep understanding of canary releases
- ✓ Know canary implementation levels
- ✓ Understand monitoring metrics
- ✓ Know A/B testing process
- ✓ Understand Blue/Green advantages
- ✓ Know user-installed software challenges
- ✓ Understand upgrade strategies
- ✓ Know symlink/Blue-Green pattern

### Integration Understanding
- ✓ How GitHub Actions enables strategies
- ✓ How feature toggles enable CD
- ✓ When to use which strategy
- ✓ How strategies complement each other

---

# Final Summary

## Slide 04: Continuous Deployment
Focus on **automation, pipelines, and GitHub Actions** as the foundation for modern software delivery.

**Key Message:** Automate everything from commit to production with proper tooling.

## Slide 05: Continuous Delivery Strategies
Focus on **safe, gradual releases** using various strategies and feature toggles.

**Key Message:** Deploy frequently, release carefully, using progressive strategies to minimize risk.

## Together
They provide a **complete picture** of modern software delivery:
- **How** to automate (Slide 04)
- **How** to release safely (Slide 05)

---

# End of Study Guide

This comprehensive guide covers all material from ES Slides 04 and 05. Use it to:
- Understand CI/CD deeply
- Master progressive delivery strategies
- Prepare for exams
- Implement in your project
- Reference during development

Good luck with your studies and implementations!
