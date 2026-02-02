# Software Engineering - Study Guide (Slides 01-03)
## Complete Exam Preparation Guide

---

# Table of Contents

1. [Slide 01: Software Engineering Principles](#slide-01-software-engineering-principles)
   - [Project Management Fundamentals](#project-management-fundamentals)
   - [Software Development Life Cycle](#software-development-life-cycle)
   - [Development Methodologies](#development-methodologies)
   - [Agile Methodology](#agile-methodology)
   - [Scrum Framework](#scrum-framework)
2. [Slide 02: Requirements Planning in DevOps](#slide-02-requirements-planning-in-devops)
   - [User Stories](#user-stories)
   - [Acceptance Criteria](#acceptance-criteria)
   - [Epics and Initiatives](#epics-and-initiatives)
   - [Estimation Techniques](#estimation-techniques)
   - [Requirements Types](#requirements-types)
3. [Slide 03: Software Components](#slide-03-software-components)
   - [Requirements to Components](#requirements-to-components)
   - [Horizontal vs Vertical Slicing](#horizontal-vs-vertical-slicing)
   - [Architecture Principles](#architecture-principles)
   - [SOLID Principles](#solid-principles)
   - [Component Principles](#component-principles)
   - [Refactoring](#refactoring)

---

# Slide 01: Software Engineering Principles

## Project Management Fundamentals

### Overview
Project management involves coordinating tasks, people, and resources to achieve project goals. It serves as the foundation for successful software engineering.

### The Three Key Pillars of Project Management

1. **Plan** - Define goals, scope, timeline, resources
   - Establishes what needs to be done
   - Sets boundaries and expectations
   - Allocates resources effectively

2. **Execute** - Coordinate tasks, guide teams, solve problems
   - Day-to-day management of work
   - Team coordination and communication
   - Problem-solving and impediment removal

3. **Deliver** - Meet objectives, measure success, close project
   - Ensures goals are achieved
   - Evaluates project success
   - Formally closes out the project

### Analogy: Building a House
The slides use building a house as an analogy for software engineering project management. Just as constructing a house requires planning, execution, and delivery phases, so does software development.

### Key Takeaways
- Project management is essential for organizing complex software projects
- The three pillars (Plan, Execute, Deliver) provide a framework for success
- Software engineering applies these same principles but with different tools and techniques

---

## Software Development Life Cycle (SDLC)

### Overview
The SDLC represents the phases through which software passes from conception to delivery and maintenance.

### The Five Core Phases

**Visual Description:** The slides show a circular/cyclical diagram with five phases:

1. **Analyse** - Understanding requirements and needs
2. **Design** - Creating the blueprint for the solution
3. **Build** - Actual implementation and coding
4. **Test** - Verification and validation
5. **Deliver** - Deployment and release

### Key Concepts
- SDLC provides structure to software development
- Different methodologies interpret and execute these phases differently
- The cycle is iterative - delivery leads back to analysis for improvements
- Modern approaches often overlap or repeat these phases

### Important Understanding
The SDLC is not a rigid sequence but a framework that can be adapted based on methodology (Waterfall, Agile, etc.).

---

## Development Methodologies

### 1. Waterfall Methodology

#### Characteristics
- **Plan-driven model** where phases are processed and completed one at a time
- Sequential approach: Analyse → Design → Build → Test → Deliver

#### Advantages
- **Easy to plan** - A schedule can be set with deadlines for each stage
- Product proceeds through development "like a car in a car-wash"
- Theoretically deliverable on time with proper planning

#### When to Use
- Requirements are **very well understood**
- Project scope is stable and unlikely to change
- Clear, fixed deliverables

#### Limitations
- Inflexible to changes
- Late discovery of issues
- Customer sees product only at the end

**Visual Description:** Linear flow diagram showing one-time progression through all SDLC phases.

---

### 2. Iterative Methodology

#### Characteristics
- Improves the product through **successive prototypes**
- Incorporates feedback at each cycle
- **Aims to learn in each cycle**

#### How It Works
1. Build a prototype
2. Gather stakeholder feedback
3. Gain team insights
4. Refine and repeat

#### When to Use
- **High complexity** projects
- **Frequent changes** expected
- **Different stakeholder views** on the final product
- Learning and discovery are important

**Visual Description:** Shows a refinement cycle with Analyse → Design → Build → Test phases repeating with a "Refine" feedback loop leading back to Analysis.

---

### 3. Incremental Methodology

#### Characteristics
- Work is optimized to **deliver value earlier and more often**
- Instead of waiting for a single final product, delivers in increments
- Customers get value sooner, even if the final vision evolves

#### Approach
- Multiple parallel tracks of Analyse → Design → Build → Test → Deliver
- Each track produces a functional increment
- Increments add up to the complete product

#### Benefits
- Early value delivery
- Faster return on investment
- Risk reduction through phased delivery

**Visual Description:** Three parallel vertical tracks, each showing complete SDLC phases, resulting in multiple sequential deliveries.

---

### 4. Characteristics Comparison Table

| Approach | Requirements | Activities | Delivery | Goal |
|----------|-------------|-----------|----------|------|
| **Predictive (Waterfall)** | Fixed | Performed once for entire project | Single delivery | Manage cost |
| **Iterative** | Dynamic | Repeated until correct | Single delivery | Correctness of solution |
| **Incremental** | Dynamic | Performed once per increment | Frequent smaller deliveries | Speed |
| **Agile** | Dynamic | Repeated until correct | Frequent smaller deliveries | Customer value via frequent deliveries and feedback |

### Key Insights
- **Predictive approaches** focus on cost management with fixed requirements
- **Iterative approaches** focus on getting the solution right through refinement
- **Incremental approaches** focus on speed through frequent deliveries
- **Agile approaches** combine iteration and increments for maximum customer value

---

## Agile Methodology

### Origin of the Agile Manifesto

#### Historical Context
- **Date:** February 11-13, 2001
- **Participants:** 17 software leaders from diverse methodologies
- **Problem:** Frustration with heavy, documentation-driven processes
- **Goal:** Find common ground and create an alternative

#### The Birth of "Agile"
- The concept was born on the **first day** of the meeting
- Represented a shared set of values focused on:
  - **People**
  - **Collaboration**
  - **Adaptability**
  - **Trust**

#### Fun Fact
The Agile Manifesto was written on the second day, shortly after 9 participants stepped out for a smoke break!

---

### The Agile Manifesto

> "We are uncovering better ways of developing software by doing it and helping others do it.
> Through this work we have come to value:"

#### The Four Core Values

1. **Individuals and interactions** over processes and tools
2. **Working software** over comprehensive documentation
3. **Customer collaboration** over contract negotiation
4. **Responding to change** over following a plan

#### Critical Understanding
> "That is, while there is value in the items on the right, we value the items on the left more"

This statement is crucial - Agile doesn't reject documentation, processes, contracts, or plans. It simply **prioritizes** the items on the left.

---

### The 12 Agile Principles

#### Principles 1-3: Customer Focus and Delivery
1. **Customer satisfaction** through early and continuous delivery of valuable software
   - Highest priority
   - Regular, frequent delivery

2. **Welcome changing requirements**, even late in development
   - Agile processes harness change for competitive advantage
   - Change is an opportunity, not a problem

3. **Deliver working software frequently**
   - From a couple of weeks to a couple of months
   - Preference to the shorter timescale

#### Principles 4-6: Collaboration and People
4. **Business people and developers must work together daily**
   - Throughout the project
   - Continuous collaboration, not just at milestones

5. **Build projects around motivated individuals**
   - Give them the environment and support they need
   - **Trust them** to get the job done

6. **Face-to-face conversation** is the most efficient method
   - For conveying information to and within teams
   - Direct communication reduces misunderstanding

#### Principles 7-9: Technical Excellence
7. **Working software** is the primary measure of progress
   - Not documentation or plans
   - Actual functioning code

8. **Sustainable development**
   - Sponsors, developers, and users maintain a constant pace
   - **Indefinitely** - no "crunch time"

9. **Continuous attention to technical excellence and good design**
   - Enhances agility
   - Quality enables speed

#### Principles 10-12: Simplicity and Improvement
10. **Simplicity** - the art of maximizing work not done
    - Essential principle
    - Do only what's needed

11. **Best architectures, requirements, and designs emerge from self-organizing teams**
    - Teams organize themselves
    - Bottom-up rather than top-down

12. **Regular reflection** on how to become more effective
    - At regular intervals
    - **Tune and adjust behavior accordingly**
    - Continuous improvement

---

### Agile Mindset

The Agile mindset goes beyond just following practices - it's a fundamental shift in how teams think about software development.

**Key Mindset Elements:**
- Embrace change rather than resist it
- Value working software over documentation
- Focus on people and collaboration
- Continuous improvement and learning
- Deliver value frequently
- Self-organization and empowerment

---

### Agile Management Methodologies

#### Overview
Agile is an **umbrella term** covering various frameworks and methods.

**Visual Description:** A Venn diagram-style illustration showing overlapping methodologies:
- **Lean** - Parent methodology
- **Agile** - Major subset
- Within Agile: Scrum, XP (Extreme Programming), Kanban, ScrumBan, Crystal, AUP, FDD, DSDM

#### Lean Thinking Connection
Agile shares lean thinking principles:
- **Focus on value**
- **Small batch sizes**
- **Elimination of waste**

#### Focus: Scrum
- **63% of Agile users use Scrum** (based on 17th annual State of Agile Report)
- Most popular Agile framework
- Well-defined structure and practices

---

## Scrum Framework

### Introduction: FBI Sentinel Project Case Study

#### Background
- FBI needed a **new case management system**
- Goal: Replace FBI's outdated infrastructure
- **After six years and $405 million spent**, project was nowhere near completion

#### The Scrum Solution
- **Jeff Sutherland**, co-founder of Scrum, used Scrum to solve the problem
- Project became a success story for Scrum methodology
- Demonstrates how Scrum can rescue failing projects

---

### Scrum Definition

#### Official Definition
> "Scrum is a lightweight framework that helps people, teams and organizations generate value through adaptive solutions for complex problems."

#### Key Points About Scrum

1. **Simple but purposefully incomplete**
   - Provides a framework, not a complete methodology
   - Teams fill in the details

2. **Builds on collective intelligence**
   - Leverages the knowledge of those using it
   - Team-driven adaptation

3. **Provides guiding rules, not step-by-step instructions**
   - Framework, not a recipe
   - Principles over prescriptions

4. **Can wrap around existing practices or make them unnecessary**
   - Adaptable to different contexts
   - May replace existing processes

5. **Makes effectiveness visible**
   - Reveals what works and what doesn't
   - Enables continuous improvement

---

### Scrum Theory

Scrum is built on empiricism - making decisions based on observation and experience.

**The Three Pillars of Scrum:**
1. **Transparency** - Everyone sees what's happening
2. **Inspection** - Regular checking of progress and artifacts
3. **Adaptation** - Adjusting based on what's learned

---

### Learn Scrum with Scrum: The Complete Framework

**Visual Description:** The slides present a comprehensive diagram showing all Scrum elements:

- **Backlog** (left side)
- **To Do, In Progress, Testing, Done** (workflow columns)
- **Events** circle containing: The Sprint, Sprint Planning, Daily Scrum, Sprint Review, Sprint Retrospective
- **Scrum Team** showing: Developers, Product Owner, Scrum Master

This visual provides the complete picture of how Scrum operates.

---

## Scrum Team Structure

### Overview
The Scrum Team consists of **exactly three roles** - no more, no less.

### Team Characteristics

#### No Hierarchy
- Unified, cross-functional, self-managing team
- No traditional hierarchy or rank
- Collaborative decision-making

#### Size
- **Up to 10 people** for agility and productivity
- Small enough to remain nimble
- Large enough to complete significant work

#### Shared Goal
- **One Product Goal per Sprint**
- Entire team works toward the same objective

#### Scope
- **Full ownership** of development, collaboration, maintenance, R&D
- End-to-end responsibility

#### Accountability
- **Entire team** delivers a valuable Increment every Sprint
- Team accountability, not individual blame

---

### Role 1: Product Owner

#### Primary Accountability
The Product Owner is accountable for **maximizing the value** of the product resulting from the work of the Scrum Team.

#### Responsibilities: Product Backlog Management

1. **Developing and explicitly communicating the Product Goal**
   - Clear vision for the product
   - Shared understanding of direction

2. **Creating and clearly communicating Product Backlog items**
   - Writing user stories
   - Ensuring clarity and understanding

3. **Ordering Product Backlog items**
   - Prioritization based on value
   - Determining what to work on next

4. **Ensuring transparency of the Product Backlog**
   - Visible to all stakeholders
   - Understood by the team

#### Key Characteristics
- **One person, not a committee**
- May delegate work but remains accountable
- Represents stakeholders and customers
- Final decision-maker on product priorities

#### Important Note
How the Product Owner achieves their goals may vary widely across organizations, teams, and individuals - there's no single "right way."

---

### Role 2: Scrum Master

#### Primary Accountability
The Scrum Master is accountable for **establishing Scrum** as defined in the Scrum Guide.

#### Serving the Scrum Team

1. **Coaching** team members in self-management and cross-functionality
   - Helping the team organize itself
   - Building cross-functional capabilities

2. **Helping focus** on creating high-value Increments
   - Ensuring work meets the Definition of Done
   - Quality and value focus

3. **Causing removal of impediments**
   - Removing blockers to team progress
   - Facilitating problem resolution

4. **Ensuring Scrum events take place**
   - All events happen as planned
   - Positive, productive, and within timebox

#### Serving the Product Owner

1. **Helping identify techniques** for clear Product Goal and Backlog management
   - Coaching on effective backlog practices
   - Supporting clarity and transparency

2. **Helping understand** the need for concise Product Backlog items
   - Ensuring items are well-formed
   - Promoting clarity

3. **Helping establish empirical product planning**
   - For complex environments
   - Data-driven decision making

4. **Facilitating stakeholder collaboration**
   - As requested or needed
   - Bridging communication gaps

#### Key Understanding
The Scrum Master is **not** a project manager or team lead. They are a **servant leader** who facilitates the Scrum process and removes impediments.

---

### Role 3: Developers

#### Definition
Developers are the people in the Scrum Team committed to **creating any aspect of a usable Increment**.

#### Skills
- Skills needed are often **broad** and vary with domain
- May include coding, testing, design, architecture, etc.
- Cross-functional skillset within the team

#### Accountabilities

1. **Creating a plan for the Sprint (Sprint Backlog)**
   - How work will be accomplished
   - Self-organized planning

2. **Instilling quality**
   - Adhering to Definition of Done
   - No compromise on quality

3. **Adapting their plan daily**
   - Toward the Sprint Goal
   - Responding to new information

4. **Holding each other accountable as professionals**
   - Peer accountability
   - Professional standards

#### Important Notes
- "Developers" doesn't mean only programmers
- Includes anyone creating the product increment
- Self-organizing and cross-functional

---

## Scrum Events

### Overview of Events

#### Purpose
- The Sprint **contains all other Scrum events**
- Each event is a **formal opportunity to inspect and adapt** artifacts
- Events ensure **transparency and regularity**

#### Key Principles
- **Skipping events** means losing chances to inspect and adapt
- Events **minimize the need for extra meetings**
- Ideally, all events occur at the **same time and place** to reduce complexity

---

### Event 1: The Sprint

#### Definition
Sprints are the **heartbeat of Scrum**, where ideas are turned into value.

#### Characteristics
- **Fixed-length events** of one month or less
- Creates consistency
- A **new Sprint starts immediately** after the previous Sprint concludes

#### During the Sprint

1. **No changes that endanger the Sprint Goal**
   - Goal remains stable
   - Team can focus

2. **Quality does not decrease**
   - Definition of Done maintained
   - No shortcuts

3. **Product Backlog refined as needed**
   - Continuous refinement
   - Preparation for future Sprints

4. **Scope may be clarified and renegotiated**
   - With Product Owner
   - As more is learned

#### Sprint Cancellation
- A Sprint could be **cancelled** if the Sprint Goal becomes obsolete
- **Only the Product Owner** has authority to cancel the Sprint
- Rare occurrence

#### Responsibilities During Sprint

**Product Owner:**
- Ensures Product Backlog is clear, transparent, and reflects priorities
- Works with stakeholders to maximize product value
- Available to clarify backlog items

**Scrum Master:**
- Ensures Scrum framework is understood and followed
- Coaches team and organization on Scrum practices
- Removes impediments to team's progress
- Helps team focus on high-value Increments

---

### Event 2: Sprint Planning

#### Purpose
Sprint Planning **initiates the Sprint** by laying out the work to be performed.

#### The Three Topics Addressed

**1. Why is this Sprint valuable?**
- Product Owner proposes how product could increase value
- Scrum Team collaborates to **set a Sprint Goal**

**2. What can be Done during this Sprint?**
- Developers select items from Product Backlog
- Team considers capacity and past performance (velocity)
- Items must be achievable within Sprint

**3. How will the chosen work get done?**
- For each selected item, Developers plan necessary work
- Work must meet Definition of Done
- Creates the Sprint Backlog

#### Responsibilities

**Product Owner:**
- Presents the Product Goal
- Proposes how product could increase value
- Ensures most valuable items are ready for discussion
- Works with Developers to define Sprint Goal and select items

**Scrum Master:**
- Ensures event takes place
- Ensures purpose is understood
- Teaches team to keep within timebox
- Facilitates discussion and collaboration

#### Key Outcome
Creates the **Sprint Backlog** - the plan for the Sprint.

---

### Event 3: Daily Scrum

#### Purpose
A **15-minute event** for Developers to synchronize work and plan the next 24 hours toward the Sprint Goal.

#### The Three Questions
Team members typically address:
1. **What did I do yesterday** to help achieve the Sprint Goal?
2. **What will I do today** to help achieve the Sprint Goal?
3. **Are there any impediments** blocking my progress?

#### Benefits
- **Improve communications**
- **Identify impediments**
- **Promote quick decision-making**
- **Eliminate need for other meetings**

#### Responsibilities

**Product Owner:**
- Usually **does not participate** unless actively working on Sprint Backlog items
- If present, listens and may adapt Product Backlog afterward
- Only participates as full member if acting as a Developer

**Scrum Master:**
- Ensures Developers hold the event
- Ensures understanding of purpose
- Ensures **15-minute timebox** is not exceeded
- Coaches to keep focused on Sprint Goal and next 24-hour plan

#### Important Notes
- **For Developers** - Product Owner and Scrum Master are usually observers
- Same time and place every day
- Focus on progress toward Sprint Goal

---

### Event 4: Sprint Review

#### Purpose
Held at the **end of the Sprint** to:
- **Inspect the Increment**
- Determine future adaptations

#### Characteristics
- Scrum Team presents results to **key stakeholders**
- Progress toward Product Goal is discussed
- A **working session**, not just a presentation
- Second to last event of the Sprint

#### Responsibilities

**Product Owner:**
- Explains what was "Done" and what wasn't completed
- Discusses Product Backlog status
- Proposes likely next steps to increase value
- Works with stakeholders and team on future adaptations

**Scrum Master:**
- Ensures event happens
- Ensures participants understand purpose
- Keeps within timebox
- Facilitates collaboration between team and stakeholders

#### Key Understanding
Sprint Review should **avoid limiting it to a presentation** - it's a collaborative working session where the team and stakeholders inspect and adapt together.

---

### Event 5: Sprint Retrospective

#### Purpose
Plan ways to **increase quality and effectiveness**.

#### Focus
The Scrum Team identifies the **most helpful changes** to improve effectiveness:
- Most impactful improvements addressed **as soon as possible**
- May even be **added to Sprint Backlog** for next Sprint

#### Typical Discussion Topics
- **What went well**
- **What could be improved**
- **Quick wins**

#### Happiness Metric
The slides emphasize measuring team happiness:
- **Happy teams are more productive and creative**
- Measuring happiness helps identify changes that boost **morale and efficiency**

**Visual Description:** A happiness scale from 1-11 shown in the slides.

#### The Four Retrospective Questions

At the end of each Sprint, each person answers:
1. On a scale from 1 to 5, **how do you feel about your role** in the company?
2. On the same scale, **how do you feel about the company** as a whole?
3. **Why do you feel that way?**
4. What **one thing would make you happier** in the next Sprint?

#### Responsibilities

**Product Owner:**
- Participates as a Scrum Team member
- Collaborates on identifying improvements for processes, tools, relationships, and work quality

**Scrum Master:**
- Ensures event occurs
- Ensures purpose is clear
- Encourages team to inspect itself and create improvement plan
- Promotes Scrum practices that improve effectiveness

#### Timing
Sprint Retrospective **concludes the Sprint** - it's the final event.

---

## Scrum Artifacts

### Overview
Scrum's artifacts represent **work or value**.

#### Purpose
- Designed to **maximize transparency** of key information
- Everyone inspecting has same basis for adaptation
- Each artifact provides **measurable information**

#### The Three Artifacts and Their Commitments
1. **Product Backlog** → Product Goal
2. **Sprint Backlog** → Sprint Goal
3. **Increment** → Definition of Done

---

### Artifact 1: Product Backlog

#### Definition
An **emergent, ordered list** of what is needed to improve the product.
- Single source of work undertaken by Scrum Team
- Dynamic and constantly evolving

#### Readiness
Product Backlog items that can be **Done within one Sprint** are deemed ready for selection:
- Usually acquire transparency after **refining activities**
- Team breaks down and clarifies items

#### Sizing
- **Developers who will do the work** are responsible for sizing
- Product Owner may influence by helping understand and select trade-offs

#### Refinement
**Product Backlog refinement** is the act of:
- Breaking down items into **smaller, more precise items**
- An **ongoing activity**
- Adding details: description, order, size
- Attributes vary with domain

#### Commitment: Product Goal

**Product Goal describes:**
- A **future state of the product**
- A **target** for the Scrum Team to plan against
- Lives in the Product Backlog
- Rest of backlog emerges to define "what" will fulfill Product Goal

**Product Definition:**
A product is a vehicle to deliver value with:
- Clear boundary
- Known stakeholders
- Well-defined users or customers
- Could be service, physical product, or something abstract

---

### Artifact 2: Sprint Backlog

#### Composition
The Sprint Backlog contains:
1. **Sprint Goal** (why)
2. **Product Backlog items selected** for Sprint (what)
3. **Actionable plan** for delivering Increment (how)

#### Characteristics
- **Plan by and for Developers**
- **Highly visible**, real-time picture of work
- Work Developers plan to accomplish during Sprint to achieve Sprint Goal
- **Updated throughout Sprint** as more is learned
- Should have **enough detail** for inspection in Daily Scrum

#### Commitment: Sprint Goal
- The objective for the Sprint
- Created during Sprint Planning
- Provides focus and coherence
- Guides daily work

---

### Artifact 3: Increment

#### Definition
A concrete **stepping stone toward the Product Goal**.

#### Characteristics
- Each Increment is **additive to all prior Increments**
- Thoroughly **verified**
- All Increments **work together**

#### Multiple Increments
- **Multiple Increments** may be created within a Sprint
- Sum of Increments presented at Sprint Review
- Sprint Review should **never be a gate** to releasing value

#### Definition of Done
Work **cannot be considered part of Increment** unless it meets Definition of Done:
- Formal description of Increment's state
- When it meets quality measures required for product

#### Commitment: Definition of Done
- Shared understanding of what "complete" means
- Creates transparency
- Ensures quality

---

## Scrum Summary: The 3-5-3 Framework

### The Simple Numbers
Scrum is "just" a **3-5-3**:

- **3 Roles:**
  1. Product Owner
  2. Scrum Master
  3. Developers

- **5 Events:**
  1. The Sprint
  2. Sprint Planning
  3. Daily Scrum
  4. Sprint Review
  5. Sprint Retrospective

- **3 Artifacts:**
  1. Product Backlog
  2. Sprint Backlog
  3. Increment

### The Reality
**But requires discipline!**

While Scrum's structure is simple, successful implementation requires:
- Commitment to the framework
- Discipline to follow practices
- Continuous improvement mindset
- Team collaboration and trust

**Visual Description:** The slides show a comprehensive overview diagram with all Scrum elements interconnected, illustrating the complete framework.

---

## Project Assignment Overview

### Project Goal
Solve a unique problem: **A modular and event-driven enterprise operations management system**

### Project Structure

#### Division into Components
- Project divided into **smaller projects (components)**
- Each group develops a **standalone component**
- Components can **run independently** but may depend on others
- **Message queue system** (Apache Kafka) for communication & data sharing

**Visual Description:** Diagram showing:
- IAM (Group 01) at top
- Message broker in center
- Multiple projects (Project A... Project N) connected
- Group 05 shown as example

#### Volatile Environment
- Client needs expected to **evolve**
- **Requirements will change**
- Use **adaptive project management** to handle evolving needs

---

### Team Structure

#### Team Composition
- Groups of **five students**
- Group elects **Product Owner** and **Scrum Master**
- **All members are developers** (including PO and SM)

#### Role Characteristics
- Roles are **collaborative, not hierarchical**
- **Decisions made as a team**
- Members can represent specific domains (e.g., one person responsible for deployments)

---

### Deliverables and Sprints

| Sprint | Objectives |
|--------|-----------|
| **1** | Establish technical backlog, implement continuous integration, define core user stories, design component architecture |
| **2** | Deliver first MVP incorporating initial user stories |
| **3** | Release Version 2.x.x: new requirements, initial testing strategy, release process, full ecosystem integration |
| **4** | Release 3.x.x: tests for new features, Infrastructure as Code (IaC), first SLOs, address new requirements |
| **5** | Release 4.x.x: system observability, enhance SLOs, integrate new requirements |
| **6** | Release 5.x.x: post-mortem environment, final system refinements |
| **7** | Final presentations |

---

### Mandatory Technologies

#### Backend
- **Spring Boot**

#### Frontend
- **ReactJS**

#### Communication
- **Between backend and frontend:** RESTful API
- **Between projects:** Message queue with **Apache Kafka**

#### Identity Provider
- **Keycloak** (managed by teaching staff)

---

# Slide 02: Requirements Planning in DevOps

## User Stories

### Overview
A user story is a **key tool in agile software development** that captures a feature from the end-user's perspective.

### Purpose
- Identifies **who** the user is
- Identifies **what** they want
- Identifies **why** they need it

### Benefits
- Provides **clear, simplified description** of a requirement
- Focuses on **user's needs**
- Drives development from user perspective

---

### User Story Definition: The Standard Formula

```
As a <type of user>
I want <some feature>
So that <reason>
```

#### Example
> "As a customer, I want to add an item to my cart, so that I can purchase it"

---

### User Story Template: The Three Questions

**Visual Description:** The slides show three sections with WHO, WHAT, WHY:

1. **WHO** - are we creating it for? Who is the user?
   - `As a <type of user>`

2. **WHAT** - are we creating? What is the intention?
   - `I want <some objective>`

3. **WHY** - are we creating it? What is the value for the customer?
   - `So that <benefits>`

---

### User Story Checklist: Best Practices

✓ **Keep it short**
  - Concise and to the point
  - Easy to read and understand

✓ **Keep it simple**
  - Avoid technical jargon
  - User-friendly language

✓ **Write from the user's perspective**
  - Not from developer or system perspective
  - Focus on user needs

✓ **Highlight the value or benefit**
  - Clear "so that" clause
  - Explicit benefit

✓ **Focus on a single functionality**
  - One feature per story
  - Split if needed

✓ **Write stories collaboratively**
  - Team effort, not individual
  - Shared understanding

✓ **Define acceptance criteria**
  - Outline the MVP
  - Clear definition of done

---

## Acceptance Criteria

### Definition
Acceptance criteria (or "conditions of satisfaction") define the **detailed scope** of a user's requirements.

### Purpose
- **Clarify the value** of the story
- **Align the team** on expectations
- **Establish when work is complete**

### Connection to Agile
Can be seen as the **"Definition of Done"** within Agile methodology.

---

### Goals of Acceptance Criteria

1. **Clarify what the team should build** before starting work
   - Prevents misunderstanding
   - Clear expectations

2. **Ensure shared understanding** of the problem
   - Everyone on same page
   - Reduces rework

3. **Define when the story is complete**
   - Clear completion criteria
   - No ambiguity

4. **Enable verification through automated tests**
   - Testable criteria
   - Supports test automation

---

### Acceptance Criteria Example

#### User Story:
> "As a registered user, I want to reset my password so that I can regain access to my account."

#### Acceptance Criteria:
- User receives a **password reset link via email**
- The link **expires after 24 hours**
- The new password must meet **security requirements**
- A **confirmation message** is shown after successful reset

---

### Acceptance Criteria Templates

#### Template 1: Given-When-Then (BDD Style)

**Structure:**
- **Given** some initial context
- **When** the user takes an action
- **Then** the expected outcome occurs

**Example:**
> - **Given** a registered user requests a password reset,
> - **When** they submit their email address on the "Forgot Password" page,
> - **Then** they receive a password reset link via email.

**Benefits:**
- Works well for **automated tests**
- Clear cause and effect
- Behavior-driven development (BDD) compatible

---

#### Template 2: Checklist Style

**Example:**
- ✓ User receives a password reset link via email

**Comparison:**

| Checklist Style | Given-When-Then Style |
|----------------|---------------------|
| Simple and quick | More detailed |
| Easy to write | Better for automation |
| Good for teams | Explicit context |

**When to Use:**
- **Given-When-Then**: Automated tests, complex logic, need for clarity
- **Checklist**: Simple features, quick documentation, team familiarity

---

### What Your Checklist Should Cover

✓ **Negative scenarios** of the functionality
  - Error cases
  - Edge cases

✓ **Functional and non-functional** use cases
  - Both types of requirements
  - Complete coverage

✓ **Performance concerns and guidelines**
  - Speed requirements
  - Resource constraints

✓ **What system/feature intends to do**
  - Clear functionality
  - Expected behavior

✓ **End-to-user flow**
  - Complete user journey
  - All interactions

✓ **Impact on other features**
  - Dependencies
  - Side effects

✓ **UX concerns**
  - User experience
  - Usability

---

### What Your Checklist Should NOT Include

✗ **Code review was done**
  - Part of Definition of Done (DoD)
  - Not acceptance criteria

✗ **Non-blocker or major issues**
  - Quality gates, not functionality

✗ **Performance testing performed**
  - Part of DoD
  - Process, not criteria

✗ **Acceptance and functional testing done**
  - Part of DoD
  - Testing process, not feature criteria

#### Important Note
> "The team should already share a clear understanding of the DoD"

Acceptance criteria are about **WHAT** to build, not **HOW** to verify it was built correctly.

---

## Epics and Initiatives

### Epics

#### Definition
A **large user story** that can't be completed in a single sprint.

#### Characteristics
- Represents a **significant feature or initiative**
- Can be **broken down** into smaller, manageable user stories
- Covers **broad scope**
- May require **multiple teams or sprints**

**Visual Description:** Shows Epic 1 broken down into Story 1, Story 2, and Story 3.

---

#### Epic Characteristics (Detailed)

1. **Broad Scope**
   - Multiple teams or sprints
   - Significant effort required

2. **Business Goal Focus**
   - Bigger business objectives
   - Not technical details

3. **Container for Related Stories**
   - Groups related work
   - Organizational tool

---

#### Managing Epics

**Best Practices:**
- **Break epics into smaller stories** for easier planning
  - Sprint-sized pieces
  - Manageable chunks

- **Adjust scope** as priorities and requirements evolve
  - Flexible boundaries
  - Adapt to learning

---

### Initiatives

#### Definition
A **high-level objective** that aligns with strategic business goals.

#### Characteristics
- **Larger than an epic**
- Often **spans multiple epics**
- Focuses on **outcomes, not just features**
- Drives multiple epics across **teams or departments**

**Visual Description:** Shows hierarchy:
- Initiative at top
- Epic 1 (Story 1, Story 2, Story 3)
- Epic 2 (Story 1, Story 2, Story 3)

---

### Hierarchy Summary

```
Initiative (Strategic business goal)
    ↓
Epic 1 (Major feature)          Epic 2 (Major feature)
    ↓                                ↓
Story 1  Story 2  Story 3      Story 1  Story 2  Story 3
```

**Key Understanding:**
- **Initiatives** = Strategic business objectives (months/quarters)
- **Epics** = Major features or capabilities (weeks/months)
- **Stories** = Individual deliverable features (days/sprint)

---

## Estimation

### Overview
Estimation is a **forecast** - much like predicting the weather.

#### Reality Check
- Can be **right or wrong**
- Affected by:
  - **Known unknowns** (things we know we don't know)
  - **Unknown unknowns** (things we don't know we don't know)

---

### Challenges of Estimation

#### Human Limitations

1. **Struggle with accurate estimation**
   - Humans are poor at absolute estimates
   - Biases affect our judgment

2. **Confuse proportional worth with exact worth**
   - **Example:** 50% discount feels significant
   - But absolute value might still be more than you should pay
   - We're better at comparing than absolute valuation

3. **Struggle with unfamiliar domains**
   - **Example:** Seasoned contractor vs. homeowner
   - Contractor gives more accurate renovation estimate
   - Experience dramatically improves estimation

---

### Relative Estimation Exercise

**Visual Description:** The slides show a comparison exercise:
- First comparing objects labeled "3" and "4"
- Then comparing "3" and "4" again
- Finally comparing "3" and "8"

**Key Insight:**
This demonstrates how humans are **better at relative comparisons** than absolute measurements. We can more easily say "this is twice as large as that" than "this weighs 10 pounds."

---

## Story Points

### Definition
A **Story Point (SP)** is a **relative unit of measure** used by Scrum teams to estimate effort required to complete a requirement.

### Key Characteristics

#### Relative, Not Absolute
- **Not absolute time** but relative comparisons
- Example: "This story is twice as complex as that one"
- Avoids the precision trap of hour estimates

#### Team-Defined Scale
- Teams define their **own scale**
- Common: **Fibonacci sequence** (1, 2, 3, 5, 8, 13, 21, 34...)
- Why Fibonacci? Reflects increasing uncertainty with size

**Visual Description:** Shows Fibonacci numbers: 3, 5, 8, 13, 21, 34

---

### Purpose of Story Points

1. **Planning**
   - How much work fits in a Sprint?
   - Capacity planning

2. **Forecasting**
   - When will feature be done?
   - Release planning

3. **Measuring Team Velocity**
   - How many points per Sprint?
   - Predictability over time

---

### Why Fibonacci Sequence?

The Fibonacci sequence (1, 2, 3, 5, 8, 13, 21...) is ideal because:
- **Reflects uncertainty**
  - Larger items have more uncertainty
  - Gaps prevent false precision

- **Forces meaningful distinctions**
  - Is it 5 or 8? Significant difference
  - Prevents debate over 7 vs 8

- **Indicates splitting need**
  - 13+ points? Probably should split
  - Encourages right-sizing

---

## Planning Poker

### Overview
A **consensus-based estimating technique** used in Agile teams.

### Applicability
- Can use with **Story Points**
- Can use with **Ideal Days**
- Can use with **any estimating unit**

---

### Planning Poker Process

**Steps:**

1. **Product Owner presents the story**
   - Explains the requirement
   - Answers clarifying questions

2. **Each team member selects a card privately**
   - No discussion yet
   - Independent thinking
   - Prevents anchoring

3. **All cards revealed simultaneously**
   - Everyone shows at once
   - No influence from others

4. **Discuss differences**
   - Why did you estimate high/low?
   - Share assumptions

5. **Repeat until consensus reached**
   - Usually 2-3 rounds
   - Converge on shared understanding

---

### Importance of Full Participation

> "It's crucial that everyone participates in the estimation process."

#### Who Should Participate?
- **Developers** - Will implement the code
- **Designers** - Will create the UX/UI
- **Testers** - Will verify functionality
- **Deployers** - Will release to production

#### Why?
> "Estimates are most accurate when made by the people who will actually do the work."

Different perspectives reveal different complexities:
- Developer sees coding complexity
- Tester sees testing challenges
- Designer sees UX complications
- DevOps sees deployment risks

---

### Benefits of Planning Poker

1. **Encourages collaboration**
   - Team discussion
   - Shared insights

2. **Shared understanding**
   - Everyone learns about the story
   - Reveals hidden complexities

3. **Avoids anchoring bias**
   - Simultaneous reveal
   - No premature influence

4. **Surfaces assumptions**
   - Different estimates spark conversation
   - Reveals different interpretations

---

## Story Points vs. Hours

### The Problem with Hour Estimates

1. **Pressure to match estimated hours exactly**
   - Psychological burden
   - Creates stress

2. **Exceeding estimate suggests poor performance**
   - Feels like failure
   - Discourages honesty

3. **Finishing under estimate indicates flawed estimate**
   - Viewed negatively
   - Gaming the system

#### Result
Developers pad estimates or rush work to match hours.

---

### Advantages of Story Points

1. **Independent of estimator's skills or experience**
   - Junior and senior developers use same scale
   - Points relative to team, not individual
   - 5 points is 5 points regardless of who does it

2. **Team velocity tracked over time**
   - Average points per Sprint
   - Predictable capacity
   - Improves planning

3. **No need to re-estimate if team capacity changes**
   - Velocity adjusts naturally
   - Points remain constant
   - Hours would need recalculation

---

### Why Story Points Work Better

**Hours:**
- "This will take me 8 hours"
- Personal and precise
- Creates pressure and politics

**Story Points:**
- "This is a 5-point story"
- Team-relative
- Focus on complexity, not time
- Velocity handles the time conversion

---

## Requirements

### What is a Requirement?

#### Definition
**Detailed specifications** that describe what the system must do.

#### Types
- **Functional** (features, behavior)
- **Non-functional** (performance, security)

#### Purpose
- Serve as **input for design, development, and testing**
- Bridge between user stories and implementation

---

### The Relationship: Stories and Requirements

#### Stories Are Important!
User stories capture user needs and value.

#### But...
> "They are too high-level for developers to implement directly"

#### The Solution
Convert user stories into **detailed requirements** that developers can implement.

**Flow:**
```
User Story → Requirements → Design → Implementation → Testing
```

---

## Requirements of Requirements

### The Six Essential Qualities

#### 1. Clear and Unambiguous
- **Single, precise meaning**
- No room for interpretation
- Everyone understands the same thing

#### 2. Testable
- Must be **verifiable**
- Through inspection, demonstration, or testing
- Can prove it's met

#### 3. Complete
- Covers **all necessary functionality** and constraints
- Nothing missing
- Whole picture

#### 4. Consistent
- **Does not conflict** with other requirements
- No contradictions
- Harmonious set

#### 5. Feasible
- Can **realistically be implemented**
- Within time, budget, and technology constraints
- Actually achievable

#### 6. Traceable
- **Linked to its source**
- Back to user story, epic, or business objective
- Forward to implementation
- Bidirectional traceability

---

## Functional Requirements (FR)

### Definition
Define **specific actions or behaviors** of a system.
- Directly support **business processes** and **user tasks**
- The "what the system does"

---

### Examples of Functional Requirements

#### 1. System Logic
> "The system **shall** calculate the tax based on the user's location and the current tax rate."

**Characteristics:**
- Business rule implementation
- Calculation or processing logic
- Automated decision-making

#### 2. User Interaction
> "A user **shall** be able to log in using a unique email and password."

**Characteristics:**
- User-facing functionality
- Interactive features
- User capabilities

#### 3. Data Handling
> "The system **shall** store a complete history of all user orders for a minimum of 7 years."

**Characteristics:**
- Data persistence
- Retention policies
- Historical records

#### 4. API/Integration
> "The system **shall** expose a RESTful API endpoint to retrieve product data."

**Characteristics:**
- System interfaces
- Integration points
- External communication

---

### Key FR Characteristics

#### Language Note
Functional requirements typically use "**shall**":
- "The system **shall** do X"
- Indicates mandatory capability
- Distinguishes from "should" (desirable) or "may" (optional)

#### Focus
- **What** the system does
- **Specific behaviors**
- **Concrete capabilities**

---

## Non-Functional Requirements (NFR)

### Definition
Non-Functional Requirements directly impact:
- **Architectural decisions**
- **Technology stack choices**
- **Testing strategies**

### Important Warning

#### What NFRs Are NOT

❌ "The system shall support scalability"
❌ "The system shall be secure"

> "These are not Non-Functional Requirements"

#### Why Not?
- Too vague and unmeasurable
- Can't be tested
- No clear success criteria
- Not actionable

---

### Examples of Proper Non-Functional Requirements

#### 1. Scalability (Proper)
> "The system shall support **10,000 concurrent users** without a noticeable degradation in performance."

**Why this works:**
- Specific number (10,000 users)
- Measurable (concurrent users)
- Testable (can be load tested)
- Clear success criteria

---

#### 2. Performance
> "The user's dashboard shall load in less than **2 seconds**."

**Why this works:**
- Specific time (2 seconds)
- Measurable (response time)
- Testable (can measure load time)
- User-focused

---

#### 3. Security
> "All user authentication data shall be encrypted **at rest and in transit** using **industry-standard protocols**."

**Why this works:**
- Specific protection (at rest and in transit)
- Clear mechanism (encryption)
- Standard reference (industry-standard)
- Verifiable (can audit encryption)

---

#### 4. Maintainability
> "The codebase shall adhere to a **clean architecture** and be **easily extensible** by new team members."

**Why this works:**
- Architectural pattern specified
- Clear goal (extensibility)
- Target audience (new team members)

---

#### 5. Reliability
> "The system shall have an **uptime of 99.99%**."

**Why this works:**
- Specific percentage (99.99%)
- Measurable (uptime monitoring)
- Industry-standard metric
- Clear target

---

#### 6. Usability
> "The checkout process shall require a **maximum of three clicks**."

**Why this works:**
- Specific constraint (3 clicks)
- Measurable (count clicks)
- User experience focus
- Testable

---

### NFR Best Practices

#### Be Specific
- Use **numbers** and **metrics**
- Avoid vague terms like "fast," "secure," "scalable"
- Make it **measurable**

#### Be Testable
- Can you **verify** it?
- Can you **measure** it?
- Can you **prove** compliance?

#### Be Realistic
- Within **technical capabilities**
- Within **budget constraints**
- **Achievable** goals

---

## Converting User Stories to Requirements

### The Process

#### Step 1: Review the User Story and Context
- Understand the **who, what, why**
- Consider the **business context**
- Identify **stakeholders**

#### Step 2: Identify Functional Needs
- **What the system must do**
- Specific behaviors
- Concrete capabilities

#### Step 3: Identify Non-Functional Needs
- **Performance** requirements
- **Security** requirements
- **Usability** requirements
- Other quality attributes

#### Step 4: Define Acceptance Criteria
- How to **verify** completion
- **Success conditions**
- **Testing approach**

#### Step 5: Document in Testable Format
- **Clear** and **unambiguous**
- **Measurable**
- **Verifiable**

---

### Detailed Example: User Story to Requirements

#### User Story:
> "As a registered user,
> I want to update my profile information,
> so that my details are always current."

---

### Step 1: Breakdown into Functional Requirements

**FR-1:** The user shall be able to **view their current profile information** on a dedicated page.
- Display capability
- Read access

**FR-2:** The system shall provide **input fields** for the user's name, email, and password.
- Edit interface
- Specific fields identified

**FR-3:** The user shall be able to **save changes** to their profile by clicking a "Save" button.
- Update action
- UI interaction

**FR-4:** The system shall **validate all input fields** upon submission and **display an error message** for invalid data.
- Data validation
- Error handling
- User feedback

**FR-5:** The system shall display a **success message** upon successful update of the profile.
- Confirmation
- User feedback
- Positive case

---

### Step 2: Identify Non-Functional Requirements

**NFR-1 (Security):** Password updates shall require the user to **re-enter their current password** for verification.
- Security measure
- Authentication
- Prevents unauthorized changes

**NFR-2 (Performance):**
- The profile page shall load in **less than 1 second**.
- The profile update operation shall complete in **under 500ms**.
- Specific time constraints
- Measurable performance
- User experience focus

**NFR-3 (Usability):** Input fields shall be **clearly labelled** and provide **clear instructions**.
- User experience
- Accessibility
- Ease of use

---

### Key Insights from This Example

#### From One User Story...
- Generated **5 Functional Requirements**
- Generated **3 Non-Functional Requirements**
- Much more **detailed** and **actionable**
- Ready for **implementation** and **testing**

#### Notice the Specificity
- FRs define **exact behaviors**
- NFRs include **measurable criteria**
- All are **testable**
- All are **traceable** back to user story

---

# Slide 03: Software Components

## Requirements to Components

### The Next Step: From Requirements to Architecture

#### The Challenge
Once user stories are defined, the question becomes:

> "What should we do if a user story is too large?"

---

### Mapping Requirements to Architecture

#### The Process

1. **Mapping Requirements to Architecture**
   - Each user story identifies a **behavior or feature**
   - That feature must be implemented by **one or more software components**

2. **Granularity Alignment**
   - **Simple stories** may map directly to a **single component**
   - **Complex stories** may require **coordination across several components**

3. **Traceability**
   - Maintaining **links between stories and components** ensures:
     - **All requirements are covered**
     - **Code changes traced back to user needs**

---

## INVEST Principles

### The Gold Standard for User Stories

INVEST is an acronym representing the ideal characteristics of user stories:

---

### I - Independent

**Definition:** Deliverable in isolation, minimizing dependencies across stories

**Why Important:**
- Can be implemented in **any order**
- **Reduces complexity** of Sprint planning
- Avoids **blocking** between stories

**How to Achieve:**
- Minimize dependencies
- Decouple features
- Self-contained stories

---

### N - Negotiable

**Definition:** Story details and priority should remain flexible and open to discussion

**Why Important:**
- Allows **adaptation** to learning
- **Priorities can shift** based on value
- Details emerge through **conversation**

**How to Achieve:**
- Stories are not contracts
- Conversation over documentation
- Collaborative refinement

---

### V - Valuable

**Definition:** Each story must provide clear value to the user or customer on its own

**Why Important:**
- Every story **delivers value**
- No "technical stories" without user benefit
- **Justifies the work**

**How to Achieve:**
- Clear "so that" clause
- User-centric perspective
- Business value explicit

---

### E - Estimable

**Definition:** Story should be clear and small enough to allow reasonable estimation

**Why Important:**
- Team can **plan** effectively
- Can **commit** with confidence
- **Predictable** velocity

**How to Achieve:**
- Sufficient detail
- Understood by team
- Not too large or vague

---

### S - Small

**Definition:** Kept to a manageable size, typically fitting within a single iteration

**Why Important:**
- **Fits in a Sprint**
- Reduces **risk**
- **Faster feedback**

**How to Achieve:**
- Split large stories
- Vertical slicing
- Single focus

---

### T - Testable

**Definition:** Must add externally verifiable behavior, with acceptance criteria guiding validation

**Why Important:**
- Can **verify** completion
- **Clear definition of done**
- **Quality assurance**

**How to Achieve:**
- Clear acceptance criteria
- Measurable outcomes
- Verifiable behavior

---

### INVEST Summary

> "This is how a user story should look like!"

A good user story is:
- **I**ndependent - Can work alone
- **N**egotiable - Flexible details
- **V**aluable - Delivers user value
- **E**stimable - Team can size it
- **S**mall - Fits in iteration
- **T**estable - Can verify completion

---

## Horizontal vs Vertical Slicing

### The Problem: Large Epics

**Reality:**
- Large initiatives, often called **epics**, are too extensive for a single iteration
- **Subdividing epics** into smaller, manageable pieces is essential

---

### Why Subdivision Matters: Benefits

1. **Better visibility of progress**
   - Can track completion of pieces
   - Early indicators of problems
   - Regular milestones

2. **Early feedback opportunities**
   - Users see results sooner
   - Can adjust direction
   - Validate assumptions early

3. **Incremental delivery of value**
   - Users get value before entire epic complete
   - ROI sooner
   - Risk reduction

---

### Epic Definition (Reminder)

**What is an Epic?**
- A **large body of work** that cannot be delivered within a single iteration
- Typically represents a **major feature, capability, or business initiative**
- Requires **decomposition** into smaller user stories or increments

---

## Horizontal Slicing

### Definition
Work is divided along **technical layers** of the system.

**Examples of layers:**
- Backend
- Frontend
- Database

---

### Characteristics of Horizontal Slicing

1. **Developers focus only on one area** of the architecture at a time
   - Backend developers work on backend
   - Frontend developers work on frontend
   - Database specialists work on database

2. **Leads to siloed work**
   - Teams working independently
   - Limited integration during development
   - "Throw over the wall" mentality

3. **Integration issues may arise later**
   - Problems discovered late
   - Rework required
   - Integration phase becomes risky

4. **No value can be delivered until all layers are completed**
   - Nothing works until everything works
   - All-or-nothing approach
   - Delayed feedback

---

### Important Distinction

> "The result of horizontal slicing is better described as 'tasks,' since they represent **technical steps** rather than **user value**."

**Tasks vs Stories:**
- **Tasks** = Technical work (horizontal slices)
- **Stories** = User value (vertical slices)

---

## Vertical Slicing

### Overview (1/2)

#### The Need
Backlogs must support **incremental, frequent deployment**.

#### The Solution
**Vertical slicing** breaks features into small, deployable units.

---

### Benefits of Vertical Slicing

1. **Finer control over code updates**
   - Deploy smaller changes
   - Easier to manage
   - Reduced risk

2. **Reduces deployment risks**
   - Less changes per deployment
   - Easier to identify problems
   - Faster rollback if needed

3. **Focuses primarily on functional aspects**
   - Each slice delivers function
   - User-visible progress
   - Testable increments

---

### Cross-Functional Requirements (CFRs) (2/2)

#### The Challenge
- CFRs are **not tied to a single feature**
- May be **impacted by any change**
- Every deployment can **affect how well system meets CFRs**

---

#### Key CFRs for Safe Continuous Deployment

1. **Deployability**
   - Can we deploy easily?
   - Automated deployment

2. **Testability**
   - Can we test effectively?
   - Automated testing

3. **Observability**
   - Can we monitor behavior?
   - Logging and metrics

4. **Security**
   - Is system secure?
   - Continuous security

5. **Performance**
   - Does it perform well?
   - Performance monitoring

---

#### Traditional vs Continuous Deployment Approach

**Traditional Setup:**
- CFRs often **postponed**
- Treated as "**icing**" (nice to have)
- Added at the end

**Problems with Traditional:**
- Delaying CFRs **increases cost**
- Increases **complexity**
- Risks **neglect** by stakeholders
- May never get done

**Continuous Deployment Approach:**
- CFRs must be **addressed continuously**
- **Alongside functional slices**
- Built-in, not added on
- Non-negotiable quality attributes

---

## Example of Vertical Slicing

### Scenario
**Feature:** "User can view purchase history"

---

### Wrong Approach (Horizontal)

❌ **Not recommended:**
- Build entire database layer
- Build entire backend layer
- Build entire UI layer

**Problem:** Nothing works until everything is done

---

### Right Approach (Vertical)

**Possible increments:**

✓ **Increment 1:** Retrieve and store transaction data
- Full stack, minimal feature
- Can deploy and test
- Provides foundation

✓ **Increment 2:** Display basic list of past purchases
- Adds visible value
- Users can see history
- Simple UI

✓ **Increment 3:** Add filtering and sorting options
- Enhances usability
- More sophisticated
- Still deployable alone

✓ **Increment 4:** Provide export to file (e.g., PDF, CSV)
- Additional capability
- Optional enhancement
- Separate deployment

---

### Key Insights from Example

**Each increment:**
- Delivers **functional value**
- Can be **deployed independently**
- Goes through **all layers** (database, backend, frontend)
- Is **testable**
- Provides **user value**

---

### The Vertical Slicing Principle

> "Slicing epics into smaller increments enables incremental, continuous delivery."

> "Vertical slicing ensures that every increment is functional and deployable."

**Mantra:**
**"A little bit of everything"** rather than **"all of one thing"**

---

## Case Study: Groceroo

### Company Overview

**Groceroo** is a fictional company with the following characteristics:
- Offers **at-home grocery delivery**
- Customers order through a **web application**
- Orders fulfilled by **personal shopping assistants**
- Stores manage inventory through a **partner portal**

**Business Goal:** Increase average order size via new feature

---

### System Overview

#### Customer Web App (Customer-facing)
- **Store selection**
- **Cart management**
- **Online payment & checkout**

#### Partner Portal (Store-facing)
- **Inventory import/update**
- **Store branding** (logo, details)
- **Stock management**

#### Architecture Note
> "Both modules are part of the same system"

**Visual Description:** Diagram showing two main modules with their respective features, indicating they're interconnected.

---

### The New Feature: "Last-Minute Items"

**Business Objective:**
Groceroo wants to add a **"Last-Minute Items" carousel** to their checkout page to increase average order size.

**Visual Description:** Shows a carousel of product items that appears during checkout, similar to impulse-buy items at physical store checkout counters.

---

### Requirements - User Interface

**Goal:** Increase average order size via an on-store carousel

**UI Components:**
- **Scrollable product cards** with:
  - Product image
  - Price
  - Quantity selector
  - "Add to Cart" button

**Scope:** Per-store ranking and ordering

**Ranking Logic:** By number of times added to cart by other users
- Data-driven recommendations
- Popular items shown first

---

### Requirements - Admin Portal

**New Section:** Shop Manager Portal enhancement

**Purpose:** Stores curate products shown just before checkout

**Features:**
- **Simple form** to edit a list of product IDs (SKUs)
- Items configured here appear in checkout page
- Supports **store-specific customization** and flexibility

**Benefit:** Store managers control their own upselling items

---

## Horizontal Slicing Implementation (Anti-Pattern)

### Task 1: Persistence Layer

**Work:** Create the database table

**Problem:**
- Database change deployed, but **impossible to test** its impact on full feature
- **Bugs and missing indexes** found too late
- No way to validate if schema supports all use cases
- Rework required later

**Why This Happens:**
- Isolated from other layers
- No end-to-end testing possible
- Assumptions about what's needed

---

### Task 2: Backend Layer

**Work:** Implement CRUD endpoints and 'add to cart' logic

**Problem:**
- Backend developed **in isolation**
- **Hidden performance issues** not discovered
- **Incorrect assumptions** about:
  - Payload formats
  - API integration
  - Data structures
- Mismatch with frontend expectations

**Why This Happens:**
- No integration testing
- No real UI to test against
- API contract assumptions

---

### Task 3: Frontend Layer

**Work:** Build the UI and admin interface

**Problem:**
- Full UI only **integrated at the end**
- **Leads to rework** when problems with backend and database finally exposed
- Discover backend doesn't support UI needs
- Performance issues only now visible
- **Major integration pain**

**Why This Happens:**
- First time all pieces come together
- Late integration
- Assumptions from all layers collide

---

### Horizontal Slicing Problems Summary

**The Pattern:**
1. Each layer built in isolation
2. Problems hidden until integration
3. Late discovery of issues
4. Expensive rework
5. Nothing deployable until end
6. No user feedback possible

**Result:** High risk, late feedback, no incremental value

---

## Vertical Slicing Implementation (Correct Pattern)

### User Story 1: Simple Carousel (MVP)

#### Summary
> **As a user**
> I want to see a selection of last-minute possible purchases before I complete my order
> So that I can quickly add anything I might have forgotten

---

#### Features Included
- Display a **basic carousel** of last-minute items (no frills)
- Items **hardcoded** for one/two stores (with marketing input)
- Users **click item → detail page → add to cart**

#### Explicitly EXCLUDED
- ❌ Add-to-cart button in carousel
- ❌ Quantity selector
- ❌ Ranking logic
- ❌ Admin form

**Strategy:** Absolute minimum to prove concept

---

#### Acceptance Criteria

**Scenario 1: Store has last-minute items**
- **Given** I have items in the basket
- **And** the current shop has last-minute purchases configured
- **When** I go to checkout
- **Then** I should see a carousel with some last-minute purchases for the current shop

**Scenario 2: Store has no last-minute items**
- **Given** I have items in the basket
- **And** the current shop does **not** have any last-minute purchases configured
- **When** I go to checkout
- **Then** I should see the normal checkout page without any extra carousel

---

#### What Gets Built (User Story 1)

**Full stack, minimal feature:**
- **Database:** Basic table for last-minute items (initially just 1-2 stores)
- **Backend:** Simple endpoint to fetch items for a store
- **Frontend:** Basic carousel component showing items
- **Integration:** Hardcoded items, but full integration

**Result:**
- ✅ Deployable
- ✅ Testable
- ✅ Provides value (users see recommendations)
- ✅ Proves concept
- ✅ Gets feedback

**Visual Description:** Shows simple carousel with products, click through to detail page.

---

### User Story 2: Configurable Carousel

#### Summary
> **As a store manager**
> I want to configure the last-minute items for my store
> So that I can update them by myself, without having to wait for Groceroo's team

---

#### Why This Story?
- Move **beyond hardcoded items**
- Database changes **not sustainable long-term**
- Provide **admin interface** for partners
- Partners **self-manage** their "last-minute items"

**Strategy:** Enable self-service management

---

#### Acceptance Criteria

**Scenario 1: See admin section**
- **Given** I am logged in to the admin portal
- **When** I view my store's dashboard
- **Then** I should see an extra section called "last-minute items"
- **And** it should contain a form where I can add and remove products

**Scenario 2: Add products**
- **Given** I am logged in to the admin portal
- **And** I have added products to the last-minute items list
- **When** I submit the last-minute items form
- **Then** I should see those products in the checkout page for my store

**Scenario 3: Remove products**
- **Given** I am logged in to the admin portal
- **And** I have removed products from the last-minute items list
- **When** I submit the last-minute items form
- **Then** I should not see those products anymore in the checkout page for my store

---

#### What Gets Built (User Story 2)

**Full stack enhancement:**
- **Database:** Schema update for dynamic configuration
- **Backend:** Admin API endpoints (create, update, delete items)
- **Admin UI:** Form to manage last-minute items
- **Frontend:** Use dynamic data instead of hardcoded

**Result:**
- ✅ Removes hardcoding
- ✅ Empowers store managers
- ✅ Scales to all stores
- ✅ Still deployable independently

**Visual Description:** Shows admin portal with form to add/remove products by SKU.

---

### User Story 3: One-Click Add to Basket

#### Summary
> **As a user**
> I want an "Add to cart" button on the last-minute items
> So that I can place an order more quickly, avoiding going back and forth between checkout and article detail pages

---

#### Why This Story?
- **Improve carousel usability** & checkout flow
- **Current flow inefficient:** item → detail page → add to cart
- **Risk:** Users abandon checkout (friction)
- **New feature:** "Add to basket" button directly in carousel

**Strategy:** Reduce friction, improve conversion

---

#### Acceptance Criteria

**Scenario 1: Button is present**
- **Given** I have items in the basket
- **When** I go to checkout
- **Then** I should see the last-minute items have an "Add to cart" button on them

**Scenario 2: Button works**
- **Given** I am viewing the last-minute items carousel
- **When** I click the "Add to cart" button
- **Then** the product should be added to my cart
- **And** I remain on the checkout page

---

#### What Gets Built (User Story 3)

**Full stack enhancement:**
- **Backend:** "Quick add" API endpoint
- **Frontend:** Add to cart button in carousel
- **UX:** Update cart without page navigation
- **Testing:** Verify cart state updates

**Result:**
- ✅ Significant UX improvement
- ✅ Reduces friction
- ✅ Likely increases conversion
- ✅ Deployable independently

**Visual Description:** Carousel now has "Add to Cart" button on each item card.

---

### User Story 4: Quantity Selection in Carousel

#### Summary
> **As a user**
> I want to be able to add more than one of a last-minute item at once
> So that I can place an order more quickly without clicking on the basket button multiple times

---

#### Why This Story?
- Adds **"UX sugar"** for better convenience
- Users choose **quantity before adding** to basket
- **Not essential** (can adjust during checkout)
- Potential to **boost average order size**

**Strategy:** Convenience enhancement, optional refinement

---

#### Acceptance Criteria

**Scenario 1: Quantity selector present**
- **Given** I have items in the basket
- **When** I go to checkout
- **Then** I should see that the last-minute items have a quantity selector
- **And** the selector allows me to modify the number in it (between 1 and 20)

**Scenario 2: Default quantity**
- **Given** I am viewing the last-minute items carousel
- **And** I have not interacted with the quantity selector
- **When** I click the "Add to cart" button
- **Then** one unit of the product should be added to my cart

**Scenario 3: Custom quantity**
- **Given** I am viewing the last-minute items carousel
- **And** I have modified the quantity in the quantity selector
- **When** I click the "Add to cart" button
- **Then** the number of units added to cart matches the ones in the selector
- **And** the selector resets to 1

---

#### What Gets Built (User Story 4)

**Full stack enhancement:**
- **Backend:** Support quantity parameter in add-to-cart
- **Frontend:** Quantity selector component in carousel
- **UX:** State management for quantity
- **Testing:** Various quantity scenarios

**Result:**
- ✅ Enhanced convenience
- ✅ May increase order size
- ✅ Optional enhancement
- ✅ Deployable independently

**Visual Description:** Carousel with quantity selector (1-20) next to Add to Cart button.

---

## Vertical Slicing Benefits Demonstrated

### Comparison Summary

| Aspect | Horizontal Slicing | Vertical Slicing |
|--------|-------------------|------------------|
| **Deployment** | Only at end | After each story |
| **Feedback** | Late | Continuous |
| **Risk** | High (all at once) | Low (incremental) |
| **Integration** | Late (all layers) | Continuous |
| **Value** | None until end | Incremental |
| **Testing** | Only at end | Throughout |

---

### The Vertical Slicing Journey

**User Story 1:** Simple Carousel (MVP)
- Hardcoded items, basic display
- **Value:** Proof of concept, user feedback

**User Story 2:** Configurable Carousel
- Admin interface, dynamic data
- **Value:** Self-service, scalability

**User Story 3:** One-Click Add to Cart
- In-carousel add functionality
- **Value:** Reduced friction, better UX

**User Story 4:** Quantity Selection
- Quantity selector
- **Value:** Convenience, potential order size increase

---

### Key Insights

1. **Each story was independently deployable**
2. **Each story provided user value**
3. **Each story could be tested**
4. **Feedback informed next story**
5. **Risk was distributed, not concentrated**
6. **Could stop at any point with working feature**

---

### Think About: Stock-Aware Carousel

**New User Story to Consider:**

> **As a user**
> I want to only see last-minute items that are in stock
> So that I don't get frustrated adding items that aren't available

**Requirements:**
- Integrate with store inventory system
- Show only items in stock
- Avoid customer frustration at checkout

**Exercise:** How would you implement this with:
1. **Horizontal slicing?**
2. **Vertical slicing?**

---

## Architecture Principles

### What is Software Architecture?

#### Definition
> "Software architecture is the **shape of a system** created by its builders."

---

### Architecture is Defined By:

1. **Division into components**
   - How system is broken down
   - Component boundaries

2. **Arrangement of those components**
   - How components relate
   - System structure

3. **Communication mechanisms between components**
   - How components interact
   - Interfaces and protocols

---

### What a Good Architecture Must Support

1. **The use cases and operation** of the system
   - Functional requirements
   - System behavior

2. **The maintenance** of the system
   - Fixing bugs
   - Updating dependencies
   - Ongoing support

3. **The development** of the system
   - How teams work
   - Development process
   - Collaboration

4. **The deployment** of the system
   - How it's released
   - Operations
   - Production support

---

### The Goal of Software Architecture

> "The goal of software architecture is to **minimize the human resources required** to build and maintain the required system."

#### In Business Terms:
- Want to **reduce the cost/LOC** (cost per line of code)
- More efficient development
- Lower maintenance costs
- Sustainable long-term

---

### What is NOT an Architecture

❌ **Libraries** - Tools we use, not architecture
❌ **Frameworks** - Frameworks can support architecture but aren't it
❌ **MVC** - A pattern, not complete architecture
❌ **Tools** - Supporting infrastructure, not architecture

**Key Point:** Architecture is about **structure and relationships**, not specific technologies.

---

## SOLID Principles

### Overview

**SOLID Principles** are:
1. **Guiding rules** for designing maintainable and extensible software
2. **Widely applied** in object-oriented programming
3. Promote **modularity, reusability, and robustness**

---

### S - Single Responsibility Principle (SRP)

#### Definition
> "Each software module has **one, and only one, reason to change**."

#### Explanation
- A module should have **one responsibility**
- Only one reason to modify it
- High cohesion

#### Why It Matters
- **Easier to understand** - Clear purpose
- **Easier to test** - Single concern
- **Easier to change** - Localized impact
- **Reduces coupling** - Less interdependence

#### Example
❌ **Bad:** User class handles both user data and user persistence
✅ **Good:** User class for data, UserRepository for persistence

---

### O - Open-Closed Principle (OCP)

#### Definition
> "For software systems to be easy to change, they must be designed to allow the **behavior** of those systems to be changed by **adding new code**, rather than **changing existing code**."

#### Explanation
- **Open for extension** - Can add new behavior
- **Closed for modification** - Don't change existing code
- Extend through inheritance, composition, or interfaces

#### Why It Matters
- **Stable systems** - Existing code unchanged
- **Lower risk** - No regression in existing functionality
- **Easier evolution** - Add features without fear

#### Example
❌ **Bad:** Modify existing class to add new feature
✅ **Good:** Extend through interface or inheritance

---

### L - Liskov Substitution Principle (LSP)

#### Definition
> "To build software systems from **interchangeable parts**, those parts must adhere to a **contract** that allows those parts to be **substituted one for another**."

#### Explanation
- Subtypes must be **substitutable** for their base types
- Objects should be **replaceable** with instances of subtypes
- Without altering correctness

#### Why It Matters
- **Polymorphism works correctly**
- **Reusable components**
- **Predictable behavior**

#### Example
❌ **Bad:** Subclass violates expectations of base class
✅ **Good:** Subclass behaves consistently with base class contract

---

### I - Interface Segregation Principle (ISP)

#### Definition
> "This principle advises software designers to **avoid depending on things that they don't use**."

#### Explanation
- **Clients shouldn't depend** on interfaces they don't use
- **Many specific interfaces** better than one general interface
- Split large interfaces into smaller, focused ones

#### Why It Matters
- **Reduces coupling** - Only depend on what you need
- **Easier to implement** - Smaller interfaces
- **Clearer contracts** - Focused purpose

#### Example
❌ **Bad:** Large interface with many methods, clients only use few
✅ **Good:** Multiple small interfaces, clients depend only on what they need

---

### D - Dependency Inversion Principle (DIP)

#### Definition
> "The code that implements **high-level policy** should not depend on the code that implements **low-level details**. Rather, **details should depend on policies**."

#### Explanation
- **High-level modules** shouldn't depend on low-level modules
- Both should depend on **abstractions**
- **Abstractions** shouldn't depend on details
- **Details** should depend on abstractions

#### Why It Matters
- **Flexibility** - Easy to change implementations
- **Testability** - Can mock dependencies
- **Reusability** - High-level logic independent

#### Example
❌ **Bad:** Business logic depends directly on database implementation
✅ **Good:** Business logic depends on repository interface, database implements interface

---

## Component Principles

### Overview

> "A component is a **grouping of related functionality** behind a nice clean interface, which resides inside an execution environment like an application."

Three key principles govern component design.

---

### REP: Reuse/Release Equivalence Principle

#### Definition
> "The **granule of reuse** is the **granule of release**. This means that the classes and modules that are formed into a component must belong to a **cohesive group**."

---

#### Explanation
- If you want to **reuse** something, it must be **released**
- Released components have:
  - **Version numbers**
  - **Release notes**
  - **Compatibility guarantees**
- Components should be **cohesive**
- Users can depend on component versions

#### Visual Examples from Slides

**Bad Example:**
Component with unrelated functionality:
- Date utilities
- String formatters
- HTTP clients
- Random unrelated functions

**Good Example:**
Component with cohesive functionality:
- All date-related utilities
- Consistent theme
- Clear purpose

---

### CCP: Common Closure Principle

#### Definition
> "Gather into components those classes that **change for the same reasons** and at the **same times**. Separate into different components those classes that change at **different times** and for **different reasons**."

---

#### Explanation
- **Single Responsibility Principle** for components
- Classes changing together should be **in same component**
- Classes changing for different reasons should be **in different components**
- Minimizes number of components affected by change

#### Why It Matters
- **Reduces release frequency** - Changes localized
- **Easier to understand** - Related changes together
- **Safer deployments** - Smaller impact

#### Visual Examples from Slides

**Bad Example:**
- UI components mixed with business logic
- Changes to UI require redeploying business logic
- Tight coupling

**Good Example:**
- UI components in one component
- Business logic in another
- Changes isolated

---

### CRP: Common Reuse Principle

#### Definition
> "Don't force **users of a component** to depend on things **they don't need**."

---

#### Explanation
- Classes used together should be **in same component**
- If you depend on component, you should **use most of it**
- Avoid unnecessary dependencies

#### Why It Matters
- **Minimizes dependencies** - Only depend on what you use
- **Easier to maintain** - Clear usage patterns
- **Smaller deployments** - No unused code

#### Visual Examples from Slides

**Bad Example:**
- Component with many classes
- Client only uses one class
- Forces dependency on entire component

**Good Example:**
- Component split by usage patterns
- Client depends only on needed component
- Minimal dependencies

---

## Common Pitfalls

### Architectural Anti-Patterns

1. **Architecture not tied to real user stories**
   - Design doesn't support actual features
   - Over- or under-engineering
   - Mismatch with needs

2. **UI coupled directly to database models**
   - Tight coupling
   - Hard to change
   - Limited flexibility

3. **Over-engineering beyond user needs**
   - Complexity without benefit
   - Wasted effort
   - Hard to maintain

4. **Ignoring maintainability and scalability early**
   - Technical debt accumulates
   - Expensive to fix later
   - Limits growth

---

## Best Practices

### Architectural Best Practices

1. **Start with stories that define corresponding use cases**
   - Requirements-driven architecture
   - User-centric design
   - Clear purpose

2. **Apply SOLID and component principles**
   - Maintainable design
   - Flexible structure
   - Quality foundation

3. **Keep frameworks & details at the outer layers**
   - Core independent of frameworks
   - Easy to change infrastructure
   - Testable core logic

4. **Validate alignment with business goals regularly**
   - Architecture serves business
   - Regular review
   - Adjust as needed

5. **Document mappings between stories and architecture**
   - Traceability
   - Understanding
   - Maintenance

---

## Problem-Oriented Refactoring

### Refactoring in Continuous Deployment

#### The Challenge
- Continuous deployment requires **small, safe, incremental changes**
- When modifying live features, **backward compatibility** becomes essential
- Goal: **Rearchitect systems without disrupting user experience**

---

### Feature Toggles
- Help introduce new functionality **gradually**
- Allow A/B testing
- Enable safe rollout
- Provide rollback capability

---

### The Nature of Refactoring

#### Definition
> "Refactoring: improving **internal structure** without altering **external behavior**"

#### Scope of Refactoring

1. **Local, low-risk modifications**
   - Most refactoring tasks
   - Single file or class
   - Minimal impact

2. **Larger refactorings**
   - Affect multiple components or domains
   - Higher risk
   - Need careful planning

#### Goal
**Maintain service continuity** while evolving architecture

---

### Be Aware Of: The Dangers

**Visual Description:** Slides show four warning boxes:

1. **"Big bang" deployments accumulate large, risky changes**
   - All changes at once
   - High risk of failure
   - Hard to debug

2. **Pre-production staging does not fully replicate production conditions**
   - Different data
   - Different scale
   - Different usage patterns

3. **Delayed integration slows feedback and increases error probability**
   - Late discovery of problems
   - Expensive fixes
   - Integration hell

4. **Safer strategy: incremental, backward-compatible deployment**
   - Small changes
   - Continuous validation
   - Easy rollback

---

### The Solution: Incremental Refactoring

**Best Approach:**
- **Incremental changes**
- **Backward-compatible** deployments
- **Feature toggles** for gradual rollout
- **Continuous testing**
- **Monitor and validate** each change

---

## Practical Guide for Your Project

### Implementation Steps

1. **Make sure you have ready-to-be-implemented user stories**
   - Well-defined
   - INVEST criteria met
   - Acceptance criteria clear

2. **Move tasks to board in correct column**
   - Assigned to members
   - **Vertical slicing oriented process**
   - Clear ownership

3. **Bootstrap your software components**
   - Spring Boot
   - React
   - Apache Kafka
   - Docker materials

4. **Start implementing user stories**
   - One story at a time
   - **Always in separate Pull Requests**
   - Each PR is a vertical slice
   - Review and merge independently

---

### Key Practices

**Vertical Slicing:**
- Each PR should go through all layers
- Each PR should be deployable
- Each PR should provide value

**Pull Request Hygiene:**
- One story per PR
- Clear description
- Linked to user story
- Reviewed before merge

**Continuous Integration:**
- Automated tests
- Automated builds
- Quick feedback

---

# Study Tips and Key Takeaways

## For Slide 01: Software Engineering Principles

### Critical Concepts to Master

1. **Understand all SDLC approaches**
   - When to use each (Waterfall, Iterative, Incremental, Agile)
   - Strengths and weaknesses
   - Comparison table

2. **Memorize the Agile Manifesto**
   - Four values
   - "While there is value in the items on the right..."

3. **Know all 12 Agile Principles**
   - Be able to explain each
   - Understand the implications

4. **Master Scrum Framework**
   - 3 roles (exact responsibilities)
   - 5 events (purpose, timing, participants)
   - 3 artifacts (contents, commitments)
   - "3-5-3" framework

5. **Understand Role Responsibilities**
   - What each role does
   - What each role does NOT do
   - Interactions between roles

---

## For Slide 02: Requirements Planning

### Critical Concepts to Master

1. **User Story Structure**
   - The formula: As a...I want...So that...
   - INVEST criteria (know all six)
   - Best practices checklist

2. **Acceptance Criteria**
   - Purpose and goals
   - Given-When-Then format
   - What to include/exclude
   - Connection to Definition of Done

3. **Hierarchy**
   - Story vs Epic vs Initiative
   - When to use each
   - How they relate

4. **Estimation**
   - Story Points concept
   - Why Fibonacci sequence
   - Planning Poker process
   - Story Points vs Hours

5. **Requirements**
   - Functional vs Non-Functional
   - Six qualities of good requirements
   - Converting stories to requirements
   - Specific, measurable NFRs

---

## For Slide 03: Software Components

### Critical Concepts to Master

1. **INVEST Principles**
   - Know all six criteria
   - Able to identify violations
   - Apply to stories

2. **Horizontal vs Vertical Slicing**
   - Clear understanding of difference
   - Advantages/disadvantages of each
   - Groceroo case study examples
   - Why vertical is preferred

3. **SOLID Principles**
   - All five principles
   - Able to explain each
   - Recognize violations
   - Apply to design decisions

4. **Component Principles**
   - REP, CCP, CRP
   - Purpose of each
   - Visual examples understanding

5. **Architecture**
   - What it is (and isn't)
   - Four things good architecture supports
   - Connection to user stories
   - Best practices

6. **Refactoring**
   - Incremental vs big bang
   - Backward compatibility
   - Feature toggles
   - Continuous deployment considerations

---

## Common Exam Question Types to Prepare For

### Analysis Questions
- "Identify problems with this user story..."
- "What's wrong with this NFR..."
- "Is this horizontal or vertical slicing..."

### Application Questions
- "Given this user story, create acceptance criteria..."
- "Break this epic into vertical slices..."
- "Identify SOLID principle violations..."

### Comparison Questions
- "Compare Waterfall and Agile..."
- "Horizontal vs Vertical slicing advantages..."
- "Story Points vs Hours..."

### Scenario Questions
- "You have a large feature, how would you implement using vertical slicing..."
- "The team velocity is X, how many stories can you complete..."
- "What role is responsible for..."

---

## Key Numbers to Remember

- **3-5-3** - Scrum framework (3 roles, 5 events, 3 artifacts)
- **12** - Agile principles
- **4** - Agile Manifesto values
- **6** - INVEST criteria
- **5** - SOLID principles
- **3** - Component principles (REP, CCP, CRP)
- **6** - Requirements qualities (Clear, Testable, Complete, Consistent, Feasible, Traceable)
- **15 minutes** - Daily Scrum timebox
- **1 month or less** - Sprint duration

---

## Connections Between Slides

### Flow of Concepts

**Slide 01 → Slide 02:**
- Agile/Scrum methodology → User Stories as requirements tool
- Product Backlog (Slide 01) → User Stories (Slide 02)
- Sprint Planning (Slide 01) → Estimation (Slide 02)

**Slide 02 → Slide 03:**
- User Stories → Need to implement in components
- Epics → Need to break down (vertical slicing)
- Requirements → Architecture decisions

**All Three Together:**
1. Choose methodology (Slide 01: Scrum)
2. Define requirements (Slide 02: User Stories)
3. Implement in architecture (Slide 03: Components and Slicing)

---

## Final Exam Preparation Checklist

### Core Knowledge
- ✓ Can explain Agile Manifesto and all 12 principles
- ✓ Know Scrum 3-5-3 framework completely
- ✓ Can write proper user stories with acceptance criteria
- ✓ Understand INVEST criteria and can apply them
- ✓ Know difference between FR and NFR with examples
- ✓ Can explain vertical vs horizontal slicing with examples
- ✓ Know all SOLID principles and can identify violations
- ✓ Understand component principles (REP, CCP, CRP)

### Applied Skills
- ✓ Can break down epics into vertical slices
- ✓ Can write acceptance criteria in Given-When-Then format
- ✓ Can identify which Scrum role does what
- ✓ Can estimate using Story Points
- ✓ Can convert user stories to requirements
- ✓ Can identify architectural problems

### Case Studies
- ✓ Understand FBI Sentinel story (why Scrum worked)
- ✓ Know Groceroo case study (vertical slicing example)
- ✓ Can apply learnings to project assignment

---

# End of Study Guide

This comprehensive guide covers all material from ES Slides 01, 02, and 03. Use it to:
- Understand concepts deeply
- Prepare for exams
- Reference during project work
- Review before assessments

Good luck with your studies!
