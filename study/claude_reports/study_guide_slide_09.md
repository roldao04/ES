# Software Engineering - Study Guide (Slide 09)
## Legacy Code Management and Evolution - Complete Exam Preparation Guide

---

# Table of Contents

1. [Introduction](#introduction)
   - [The Reality of Legacy Systems](#the-reality-of-legacy-systems)
   - [The 2000s Portal Example](#the-2000s-portal-example)
2. [Legacy Code Fundamentals](#legacy-code-fundamentals)
   - [Definition](#definition)
   - [Technical Debt](#technical-debt)
   - [The Debt Spiral](#the-debt-spiral)
   - [Warning Signs](#warning-signs)
3. [Refactoring Techniques](#refactoring-techniques)
   - [Pinning Tests](#pinning-tests)
   - [Macro-Pattern 1: System Strangling](#macro-pattern-1-system-strangling)
   - [Macro-Pattern 2: Branch By Abstraction](#macro-pattern-2-branch-by-abstraction)
4. [Nine Practices to Extend Software Life](#nine-practices-to-extend-software-life)
   - [Practice 1: Say What, Why, and for Whom Before How](#practice-1-say-what-why-and-for-whom-before-how)
   - [Practice 2: Build in Small Batches](#practice-2-build-in-small-batches)
   - [Practice 3: Integrate Continuously](#practice-3-integrate-continuously)
   - [Practice 4: Collaborate](#practice-4-collaborate)
   - [Practice 5: Create CLEAN Code](#practice-5-create-clean-code)
   - [Practice 6: Write the Test First](#practice-6-write-the-test-first)
   - [Practice 7: Specify Behaviors with Tests](#practice-7-specify-behaviors-with-tests)
   - [Practice 8: Implement the Design Last](#practice-8-implement-the-design-last)
   - [Practice 9: Refactor Legacy Code](#practice-9-refactor-legacy-code)
5. [Black Boxes to Modern Blueprints](#black-boxes-to-modern-blueprints)
   - [The Problem](#the-problem)
   - [AI-Assisted Reverse Engineering](#ai-assisted-reverse-engineering)
   - [The Multi-Lens Approach](#the-multi-lens-approach)
   - [Four-Step Process](#four-step-process)
6. [GenAI in Software Engineering](#genai-in-software-engineering)
   - [Requirements Extraction](#requirements-extraction)
   - [Mental Models and Domain Maps](#mental-models-and-domain-maps)
7. [Project Requirements](#project-requirements)
8. [Study Tips and Exam Preparation](#study-tips-and-exam-preparation)
   - [Critical Concepts to Master](#critical-concepts-to-master)
   - [Key Patterns and Techniques](#key-patterns-and-techniques)
   - [Common Exam Question Types](#common-exam-question-types)
   - [Practical Skills Checklist](#practical-skills-checklist)
   - [Important Distinctions](#important-distinctions)
9. [Connections to Other Slides](#connections-to-other-slides)
10. [Summary and Key Takeaways](#summary-and-key-takeaways)

---

# Introduction

## The Reality of Legacy Systems

### Why This Matters

> "Legacy code management is not optional - it's the reality of software engineering."

**The Hard Truth:**
- Most professional development work involves existing codebases
- New "greenfield" projects are rare
- Legacy systems often run critical business operations
- You cannot just "rewrite from scratch"
- Learning to work with legacy code is a core professional skill

**Industry Statistics:**
- ~80% of development time spent on maintenance/evolution
- Legacy systems often represent decades of business logic
- Many critical systems built on "obsolete" technology stacks
- Technical debt is universal across organizations

---

## The 2000s Portal Example

### The Scenario

> "The turn of the Millennium - A new online academic portal"

**Context (Year 2000):**
- One of the first virtual administrative systems
- Served multiple user types:
  - Students
  - Professors
  - Academic services
- Developed using "novel" technologies (novel for 2000)

**Fast Forward to 2025:**
- Still running (successfully!)
- But now considered "legacy"
- Technology stack outdated
- Original developers may be gone
- Documentation may be missing
- Yet still mission-critical

**The Lesson:**
> "Today's cutting-edge technology is tomorrow's legacy code."

**Key Insight:**
- Legacy isn't about age
- It's about maintainability
- Even last week's code can be "legacy"
- The real question: "Can we safely change it?"

---

# Legacy Code Fundamentals

## Definition

### The Real Definition

> **"Legacy Code is code you are afraid to change."**

**Forget the Book Definition:**
- It's NOT about age
- It's NOT about the technology used
- It's NOT about who wrote it
- It's about FEAR

---

### Why Are You Afraid?

> **"Because there are no tests. Full stop."**

**The Core Problem:**
```
No Tests → No Safety Net → Fear of Change → Code Becomes "Legacy"
```

**The Litmus Test:**
- Can you change something with 100% confidence (via automated tests) that you broke nothing?
  - **YES** → Not legacy (even if 20 years old)
  - **NO** → Legacy code

---

### Future Legacy

> **"If you wrote code last week with no tests... congratulations, you wrote 'future legacy.'"**

**Important Realization:**
- Legacy code is created by development practices
- Age is irrelevant
- Tests are the differentiator
- You can create legacy code TODAY

**Prevention:**
- Write tests from the start
- Maintain test coverage
- Tests as documentation
- Safety net for refactoring

---

## Technical Debt

### Anatomy of the Mess

> "It wasn't malice. Nobody wakes up thinking, 'I'm going to write garbage code today.'"

**The Real Cause:**
```
Pressure → Shortcuts → Technical Debt
```

**Common Scenarios:**
- "We need it by Friday!"
- "No time for tests!"
- "That's 'gold plating'!"
- "Just make it work, we'll fix it later"
- "The client is waiting"

**The Result:**
- Code without tests
- Poor design
- Accumulated shortcuts
- Hard-to-understand logic
- Tightly coupled components

---

### The Payday Loan Analogy

> **"Tech Debt is a payday loan."**

**How It Works:**

| Financial Debt | Technical Debt |
|---|---|
| Get money now | Get feature now |
| Pay interest later | Pay "interest" later (bugs, slowness) |
| Compound interest | Compound complexity |
| Debt collectors | Us (paying it down) |

**The "Interest" in Technical Debt:**
- Bugs and regressions
- Slower development
- Developer frustration
- Difficulty onboarding
- Fear of changes
- System instability

**Key Point:**
- Some debt is strategic (ship to learn)
- But debt must be paid
- Interest compounds
- Eventually becomes unbearable

---

## The Debt Spiral

### The Vicious Cycle

> "Repeat until you're us, in this room, having this meeting."

**The Spiral (7 Steps):**

```
1. Pressure to deliver
   ↓
2. Cut corners (add debt)
   ↓
3. Code gets harder to change
   ↓
4. Next feature is slower
   ↓
5. Pressure increases
   ↓
6. Cut more corners (MORE debt)
   ↓
7. GOTO Step 3 (repeat)
```

---

### Visual Representation

```
Time →

Technical Debt ↑
                    |                        ___------
                    |                   __---
                    |              __---
                    |          __--
                    |      __--
                    |  __--
                    |--
                    +--------------------------------→

Development Speed ↓
                    |--__
                    |    --__
                    |        --__
                    |            --___
                    |                 ---___
                    |                       ----____
                    |                               -----_______
                    +--------------------------------→
```

**Breaking the Spiral:**
- Recognize you're in it (awareness)
- Stop adding new debt (discipline)
- Start paying down old debt (refactoring)
- Invest in tests (safety net)
- Build in small batches (reduce risk)

---

## Warning Signs

### The Red Flags

> "Our job is to spot this BEFORE we start editing."

**5 Major Warning Signs:**

### 1. Complexity
**Symptom:**
> "This function is 2000 lines long."

**What It Means:**
- Too much responsibility in one place
- Multiple concerns mixed together
- Impossible to understand fully
- High chance of hidden bugs
- Very risky to change

**Example:**
```java
public void processOrder() {
    // Line 1-400: Validate input
    // Line 401-800: Calculate prices
    // Line 801-1200: Update database
    // Line 1201-1600: Send emails
    // Line 1601-2000: Generate reports
    // ...Good luck changing this!
}
```

---

### 2. Tribal Knowledge
**Symptom:**
> "Only João touches this, and he's on vacation."

**What It Means:**
- Knowledge silo
- Single point of failure
- Bus factor = 1
- High risk for the organization
- Blocks team velocity

**The Problem:**
- No documentation
- Complex logic in one person's head
- Team dependent on one individual
- Innovation bottleneck

---

### 3. Coupling
**Symptom:**
> "To change this label, I have to deploy 3 services."

**What It Means:**
- Tight coupling between components
- Lack of separation of concerns
- Changes have wide ripple effects
- Deployment complexity
- High coordination overhead

**Example Scenario:**
```
Want to change: "Login" button text
Must also deploy:
  - Frontend service (UI)
  - API Gateway (routing)
  - Auth service (validation)
```

---

### 4. Regressions / Fragile Code
**Symptom:**
> "I fixed this bug and three others popped up."

**What It Means:**
- Hidden dependencies
- Lack of tests
- Implicit contracts
- Unintended side effects
- Code is brittle

**The Whack-a-Mole Problem:**
```
Fix Bug A → Bug B appears
Fix Bug B → Bug C appears
Fix Bug C → Bug A returns!
```

---

### 5. Long Feedback Loops
**Symptom:**
- Takes hours to build
- Manual testing required
- Deploy takes days
- Can't verify changes quickly

**What It Means:**
- Development velocity suffers
- Fear of making changes
- Delays in feedback
- Inability to iterate quickly

---

### Spotting Warning Signs - Checklist

Before touching legacy code, ask:

- [ ] Is this function/class excessively long? (>200 lines)
- [ ] Do I understand what this code does?
- [ ] Are there tests covering this behavior?
- [ ] Is only one person familiar with this area?
- [ ] Will changing this affect other parts of the system?
- [ ] Have there been regressions in this area before?
- [ ] Can I quickly verify my changes?

**If you answered "yes" to multiple questions:**
→ You're dealing with legacy code
→ Proceed with extreme caution
→ Consider applying refactoring techniques first

---

# Refactoring Techniques

## Pinning Tests

### What Are Pinning Tests?

> "A pinning test is a very coarse test."

**Definition:**
- Tests that "pin down" current behavior
- Also called "Characterization Tests"
- Captures what the system DOES (not what it SHOULD do)
- Preserves bugs and all!

---

### Purpose

> "It may test a single behaviour that takes hundreds or thousands of lines of code to produce."

**Why Use Pinning Tests:**

1. **Safety Net:**
   - Know when you break existing behavior
   - Confidence to refactor
   - Detect unintended changes

2. **Documentation:**
   - Shows what the system actually does
   - Living specification
   - Better than comments

3. **Starting Point:**
   - First step in refactoring
   - Enables gradual improvement
   - Foundation for finer tests

---

### How Pinning Tests Work

**The Process:**

```
1. Observe behavior
   ↓
2. Write test that captures current output
   ↓
3. Run test → Should PASS
   ↓
4. Make refactoring change
   ↓
5. Run test again
   ↓
6. If FAILS → You changed behavior (investigate)
   If PASSES → Behavior preserved (safe)
```

---

### Example

**Legacy Code:**
```java
// 500 lines of complex logic
public String processUserData(User user) {
    // ... complex calculations ...
    // ... database calls ...
    // ... business rules ...
    return result;
}
```

**Pinning Test:**
```java
@Test
public void testProcessUserData_currentBehavior() {
    // Arrange
    User testUser = createTestUser();

    // Act
    String result = processUserData(testUser);

    // Assert - captures CURRENT output (even if buggy!)
    assertEquals("Expected output based on current behavior", result);
}
```

**Then:**
- Refactor the 500 lines
- Keep test passing
- Behavior preserved

---

### Key Characteristics

**What Pinning Tests Are:**
- Coarse-grained (high-level)
- Test observable behavior
- Capture current state
- May include bugs
- Quick to write

**What Pinning Tests Are NOT:**
- Fine-grained unit tests
- Test of isolated functions
- Verification of "correct" behavior
- Long-term test strategy

---

### Decoupling and Isolation

> "It effectively decouples objects from the services they use to mock those services so code can be tested in isolation."

**Progressive Testing Strategy:**

```
1. Pinning Tests (coarse)
   ↓
2. Refactor to decouple components
   ↓
3. Add unit tests (fine-grained)
   ↓
4. Continue refactoring with confidence
```

**Example Evolution:**
```java
// Before: Tightly coupled
public class OrderProcessor {
    public void process() {
        Database.query(...);  // Hard dependency
        EmailService.send(...);  // Hard dependency
    }
}

// After: Decoupled
public class OrderProcessor {
    private final Database db;
    private final EmailService email;

    // Now testable in isolation!
    public OrderProcessor(Database db, EmailService email) {
        this.db = db;
        this.email = email;
    }
}
```

---

## Macro-Pattern 1: System Strangling

### Overview

> **"Strangler Fig" - A new vine wrapping an old tree until the tree is gone.**

**Use Case:**
- Replacing an entire service
- Migrating a large vertical slice of a monolith
- System-level changes
- Full service replacement

**The Metaphor:**
- In nature, strangler fig vines grow around trees
- Gradually the vine takes over
- Eventually the original tree decomposes
- The vine becomes self-supporting

**Applied to Software:**
- New system "wraps" old system
- Gradually takes over functionality
- Old system eventually removed
- Incremental and safe

---

### The Key Component: The Proxy

> "This is not optional."

**The Proxy (or Façade):**
- Your "receptionist"
- Sits in front of everything
- Routes traffic between old and new
- Can be:
  - API Gateway
  - Nginx reverse proxy
  - Simple router service
  - Load balancer with routing rules

**Why It's Critical:**
- Single point of control
- Enables gradual migration
- Allows rollback
- Monitors traffic split
- Risk mitigation

---

### System Strangling - Steps

**6-Step Process:**

#### Step 1: Create the New Interface/Service
```
Create: new-billing-api.com

Status:
Old System: ✓ Running (100% traffic)
New System: ✓ Deployed (0% traffic)
Proxy: ✗ Not yet
```

**Example:**
- Deploy new service
- Different domain/endpoint
- No traffic yet
- Parallel to old system

---

#### Step 2: Insert the Proxy

```
Traffic Flow:
Client → Proxy → Old System

Status:
Old System: ✓ Running (100% traffic via proxy)
New System: ✓ Deployed (0% traffic)
Proxy: ✓ Routing all to old
```

**Configuration:**
```nginx
# Nginx example
location /api/billing/* {
    proxy_pass http://old-billing-system;
}
```

**Key Point:**
> "You've done nothing but add a hop... for now."

---

#### Step 3: Configure Proxy for 100% Old Traffic

```
Status: Baseline established
- All traffic flows through proxy
- Proxy sends 100% to old system
- New system ready but unused
- System behavior unchanged
- Monitoring in place
```

**Why This Step:**
- Validates proxy works
- Establishes baseline metrics
- No business risk yet
- Can measure proxy latency impact

---

#### Step 4: Implement ONE Endpoint in New Service

```
Example: GET /api/billing/invoices

Old System: Handles everything except /invoices
New System: Handles ONLY /invoices
```

**Critical:**
- Start with ONE endpoint
- Choose low-risk endpoint (read-only ideal)
- Thoroughly test
- Don't do everything at once

---

#### Step 5: Change the Proxy Logic

```javascript
// Proxy routing logic
if (request.path === "/api/billing/invoices") {
    route_to_new_service();
} else {
    route_to_old_system();
}
```

**Traffic Split:**
```
/api/billing/invoices → New System (100%)
/api/billing/* (all other) → Old System (100%)
```

---

#### Step 6: Monitor and Repeat

> "Repeat for every single endpoint until the old system receives 0% of traffic."

**Monitoring Checklist:**
- Error rates (old vs new)
- Response times (latency)
- Success rates
- Data consistency
- User complaints

**Incremental Migration:**
```
Iteration 1: GET /invoices → New System
Iteration 2: GET /customers → New System
Iteration 3: POST /invoices → New System
...
Iteration N: DELETE /old-system → Old system removed!
```

**The Final State:**
```
Old System: 0% traffic → Decommissioned
New System: 100% traffic → Fully operational
Proxy: Still in place (now permanent gateway)
```

---

### The Data Problem

> "Code is easy; data is hard. How do the two systems co-exist?"

**The Challenge:**
- Both systems need data
- Data must be consistent
- Can't have long migration freeze
- Business continues during migration

---

#### Option 1: Shared Database (Fast & Dangerous)

**Approach:**
```
Old System ──┐
             ├──→ Same Database
New System ──┘
```

**Pros:**
- Fastest to implement
- No data sync logic needed
- Immediate consistency

**Cons:**
- High risk of data corruption
- Schema conflicts
- Competing writes
- No rollback safety
- Tight coupling

**When to Use:**
- Short migration window
- Read-heavy systems
- With extreme caution

---

#### Option 2: Data Syncing (Slow & Safe)

**Approach:**
```
Old System → Old DB ──┐
                       ├─→ Sync Process ─→ New DB → New System
                       │   (Events/Jobs)
                       └─→ Monitor consistency
```

**Sync Mechanisms:**
- Event triggers (CDC - Change Data Capture)
- Nightly batch jobs
- Real-time streaming
- Message queues

**Pros:**
- Clean separation
- Safer migration
- Can validate data
- Easy rollback

**Cons:**
- Sync lag
- Complexity
- Temporary inconsistency
- Dual writes during transition

---

#### Option 3: Data Strangulation (The Goal)

**Approach:**
```
Phase 1:
Old System (source of truth) → New System (reads from old)

Phase 2:
New System (source of truth) → Old System (reads from new)
```

> "The new service becomes the 'Source of Truth' for invoices. The old system must now call the new service's API to get invoice data. This completes the strangulation."

**The Flip:**
```
Before: New System calls Old System for data
After:  Old System calls New System for data
```

**Completion Criteria:**
- New system is authoritative
- Old system is a client
- Data ownership transferred
- Strangulation complete for that domain

---

### System Strangling - Complete Example

**Scenario: Billing System Migration**

**Week 1-2:**
```
1. Deploy new-billing-service (empty)
2. Install API Gateway proxy
3. Route 100% traffic to old-billing-system
4. Validate: No change in behavior
```

**Week 3-4:**
```
5. Implement: GET /api/billing/invoices in new service
6. Setup: Sync job (old DB → new DB) for invoices
7. Update proxy: Route /invoices to new service
8. Monitor: Error rates, latency, consistency
```

**Week 5-8:**
```
9. Implement: GET /api/billing/customers
10. Implement: POST /api/billing/invoices
11. Implement: PUT /api/billing/invoices
... (continue for each endpoint)
```

**Week 9-10:**
```
12. Validate: All endpoints migrated
13. Flip data ownership: New service = source of truth
14. Update old system: Call new service for invoice data
15. Monitor: 2 weeks of stability
```

**Week 11:**
```
16. Decommission old-billing-system
17. Document the process
18. Celebrate! 🎉
```

---

## Macro-Pattern 2: Branch By Abstraction

### Overview

> "This is NOT git branch. This is a technique to avoid long-lived feature branches."

**Use Case:**
- Replacing a component INSIDE a monolith
- Module or library replacement
- Staying on main branch
- Avoiding merge hell

**The Goal:**
> "Replace a component inside a monolith on the main branch without breaking anything."

---

### The Problem: Merge Hell

**The "Old Way" (Long-Lived Git Branch):**

```
Day 1: Create branch
  git checkout -b new-billing

Days 2-90: Develop on branch
  - You make 200 commits
  - Meanwhile, master has 5,000 new commits
  - Other devs patch bugs in OLD billing engine

Day 91: Try to merge
  - Face MERGE HELL
  - Week-long nightmare
  - Conflicts everywhere
  - Your code (which worked) is now broken
  - High-risk merge
```

**The Pain:**
- Divergent codebases
- Integration delayed
- Conflicts compound
- Risky big-bang merge
- Often broken after merge

---

### The Solution: Branch By Abstraction

**The "New Way" (Stay on Master):**

```
Day 1: Create abstraction, commit to master
Day 2: Implement new billing (behind flag), commit to master
Day 3: Continue implementing, commit to master
...
Day 90: Flip feature flag, delete old code

Result:
- Zero merge conflicts
- Continuous integration
- Low-risk release
- Team collaborates on same codebase
```

---

### The Mechanism: Abstraction Layer + Feature Flag

**Two Key Components:**

1. **Abstraction Layer (Interface):**
   - Hides both implementations
   - Defines the contract
   - Allows swapping

2. **Feature Flag:**
   - Runtime switch
   - Decides which implementation
   - Can be gradual (%)

---

### Branch By Abstraction - Steps

**Visual Evolution:**

#### Initial State

```
┌──────────────────────────────────────┐
│         Client Code                  │
│  (Multiple components)               │
└───────────┬──────────────────────────┘
            │
            │ Direct dependency
            ↓
┌──────────────────────────────────────┐
│     Old Messy Billing Engine         │
│  (The code we want to replace)       │
└──────────────────────────────────────┘
```

**Problem:**
> "Several components of the software system rely on a specific module, library, or framework. That dependency has become outdated with our future architecture."

---

#### Step 1: Create Abstraction Layer

```
┌──────────────────────────────────────┐
│         Client Code                  │
└───────────┬──────────────────────────┘
            │
            ↓
┌──────────────────────────────────────┐
│    Abstraction Layer (Interface)     │
│  - Defines the billing contract      │
└───────────┬──────────────────────────┘
            │
            ↓
┌──────────────────────────────────────┐
│     Old Messy Billing Engine         │
│  (Now accessed via abstraction)      │
└──────────────────────────────────────┘
```

> "We create an abstraction layer that encapsulates all communication between the client code and the current supplier."

**Code Example:**
```java
// Before: Direct coupling
public class OrderService {
    public void processOrder() {
        OldBillingEngine.calculatePrice();  // Direct dependency
    }
}

// After: Abstraction layer
public interface BillingEngine {
    BigDecimal calculatePrice(Order order);
}

public class OldBillingEngineAdapter implements BillingEngine {
    public BigDecimal calculatePrice(Order order) {
        return OldBillingEngine.calculatePrice();  // Wrapped
    }
}

public class OrderService {
    private final BillingEngine billing;

    public void processOrder() {
        billing.calculatePrice(order);  // Via interface
    }
}
```

**Key Point:**
> "Ensure that the client code no longer depends directly on the old supplier."

---

#### Step 2: Implement New Supplier

```
┌──────────────────────────────────────┐
│         Client Code                  │
└───────────┬──────────────────────────┘
            │
            ↓
┌──────────────────────────────────────┐
│    Abstraction Layer (Interface)     │
│      + Feature Flag                  │
└──────┬─────────────────────┬─────────┘
       │                     │
       ↓ (Flag OFF)          ↓ (Flag ON - not used yet)
┌─────────────────┐   ┌─────────────────┐
│  Old Billing    │   │  New Clean      │
│  Engine         │   │  Billing Engine │
└─────────────────┘   └─────────────────┘
```

> "We develop a new supplier that provides the required functionality for a specific section of the client code using the same abstraction layer."

**Code Example:**
```java
public class NewCleanBillingEngine implements BillingEngine {
    public BigDecimal calculatePrice(Order order) {
        // Clean, modern implementation
        return order.getItems().stream()
            .map(Item::getPrice)
            .reduce(BigDecimal.ZERO, BigDecimal::add);
    }
}

// The switchover mechanism
public class BillingEngineFactory {
    public static BillingEngine create() {
        if (FeatureFlags.isEnabled("use-new-billing")) {
            return new NewCleanBillingEngine();
        } else {
            return new OldBillingEngineAdapter();
        }
    }
}
```

**Critical:**
- Both implementations behind same interface
- New code is "dark" (feature flag OFF)
- Committed to master daily
- Team sees new code
- No merge conflicts

---

#### Step 3: Gradual Migration

```
Week 1: Flag OFF (0% new)
Week 2: Flag ON for internal users (5% new)
Week 3: Flag ON for beta users (20% new)
Week 4: Flag ON for all users (100% new)
```

> "Once the new supplier is ready and tested, we switch that section of the client code to use the new implementation."

**Progressive Rollout:**
```java
public class BillingEngineFactory {
    public static BillingEngine create(User user) {
        // Gradual rollout by user segment
        if (user.isInternal() ||
            user.isBetaTester() ||
            FeatureFlags.isEnabled("use-new-billing")) {
            return new NewCleanBillingEngine();
        }
        return new OldBillingEngineAdapter();
    }
}
```

---

#### Step 4: Complete Migration and Cleanup

```
┌──────────────────────────────────────┐
│         Client Code                  │
└───────────┬──────────────────────────┘
            │
            ↓
┌──────────────────────────────────────┐
│   New Clean Billing Engine           │
│   (Abstraction now optional)         │
└──────────────────────────────────────┘

Old Billing Engine → DELETED
Feature Flag → REMOVED (or keep abstraction for future flexibility)
```

---

### Branch By Abstraction - Key Benefits

**1. No Merge Conflicts:**
- Everyone works on master
- Daily integration
- Conflicts detected immediately
- No big-bang merge

**2. Low Risk:**
- Feature flag provides safety
- Can rollback instantly
- Gradual rollout possible
- Monitor before full deployment

**3. Continuous Integration:**
- Team sees changes daily
- Everyone integrates continuously
- No surprise merges
- Collective code ownership

**4. Flexibility:**
- Can run both implementations
- A/B testing possible
- Easy rollback
- Gradual cutover

---

### Real-World Example

**Scenario: Replace Logging Library**

**Problem:**
- Using old Log4j 1.x
- Need to migrate to SLF4J
- 1000+ logging calls across codebase
- Can't change all at once

**Branch By Abstraction Solution:**

```java
// Step 1: Create abstraction
public interface Logger {
    void info(String message);
    void error(String message, Throwable t);
}

// Step 2: Wrap old implementation
public class Log4jLoggerAdapter implements Logger {
    private final org.apache.log4j.Logger delegate;

    public void info(String message) {
        delegate.info(message);
    }
}

// Step 3: Implement new
public class SLF4JLoggerAdapter implements Logger {
    private final org.slf4j.Logger delegate;

    public void info(String message) {
        delegate.info(message);
    }
}

// Step 4: Factory with flag
public class LoggerFactory {
    public static Logger getLogger(Class<?> clazz) {
        if (FeatureFlags.isEnabled("use-slf4j")) {
            return new SLF4JLoggerAdapter(
                org.slf4j.LoggerFactory.getLogger(clazz)
            );
        }
        return new Log4jLoggerAdapter(
            org.apache.log4j.Logger.getLogger(clazz)
        );
    }
}

// Step 5: Update call sites (gradually, on master)
// Before:
org.apache.log4j.Logger logger = org.apache.log4j.Logger.getLogger(MyClass.class);

// After:
Logger logger = LoggerFactory.getLogger(MyClass.class);
```

**Migration Timeline:**
- Week 1-2: Create abstraction, wrap Log4j
- Week 3-4: Implement SLF4J adapter
- Week 5-8: Update call sites (50 per week)
- Week 9: Enable flag for 10% of servers
- Week 10: Enable flag for 100%
- Week 11: Remove Log4j, cleanup abstraction

**All on master branch, no merge hell!**

---

# Nine Practices to Extend Software Life

## Practice 1: Say What, Why, and for Whom Before How

### The Principle

> "Forbidden to even think about the 'How' until you have crystal-clear, written-down answers to the first three questions."

**The Order:**
```
1. WHAT  - The specific, observable outcome
2. WHY   - The business value / justification
3. FOR WHOM - The specific user
4. HOW   - The technical implementation (LAST!)
```

---

### Why This Matters in Legacy Systems

> "In a legacy system, touching the 'How' is always expensive and dangerous."

**The Danger:**
- Every code change is high risk
- Unintended side effects
- Potential for regressions
- Expensive to fix mistakes
- May violate SLAs

**The Antidote:**
- Be absolutely clear on the goal
- Ensure the change is necessary
- Understand the value
- Define success criteria

---

### The Three Questions

#### 1. WHAT - The Problem

> "This is NOT 'build a billing module.' It's 'the user must be able to download a PDF of their invoice.'"

**Characteristics:**
- Specific and observable
- Free of technical jargon
- Focused on outcome, not implementation
- Testable
- User-facing language

**Examples:**

| ❌ Vague "What" | ✅ Clear "What" |
|---|---|
| "Improve the system" | "Users can export their order history as CSV" |
| "Add logging" | "Support team can view last 100 API calls for a user" |
| "Update the database" | "System retains user data for 7 years for compliance" |
| "Refactor billing" | "Invoice generation completes in under 2 seconds" |

---

#### 2. WHY - The Justification

> "This is the most important question. If the 'Why' is weak, you shouldn't be touching the legacy system at all."

**Good "Why" Examples:**
- Legal compliance requirement
- SLA violation risk
- Security vulnerability
- Blocking customer deal
- Measurable cost savings

**Bad "Why" Examples:**
- "Because this old code looks ugly"
- "Because I want to try new technology"
- "Because everyone else is doing it"
- "Because the code is old"

**The Test:**
```
If you can't justify the business value in one sentence,
don't touch the legacy code.
```

**Examples:**

| ❌ Weak "Why" | ✅ Strong "Why" |
|---|---|
| "The code is messy" | "Current code causes 3 production incidents/month, costing $50k each" |
| "We should use microservices" | "Deployment coupling blocks 80% of releases, extending time-to-market by 2 weeks" |
| "This framework is old" | "Current framework has CVE vulnerabilities with no security patches available" |
| "I read about this pattern" | "We are legally required to show new tax information, currently non-compliant" |

---

#### 3. FOR WHOM - The User

> "This defines the scope. 'For Whom' tells you what NOT to build."

**Why It Matters:**
- Different users have different needs
- Defines requirements
- Limits scope
- Prevents over-engineering

**Examples:**

| User Type | Requirements | What to Skip |
|---|---|---|
| Customer Service Reps | Speed, data density, keyboard shortcuts | Mobile optimization, onboarding |
| First-time mobile users | Simplicity, guidance, touch-friendly | Advanced features, bulk operations |
| System administrators | Detailed logs, troubleshooting tools | Pretty UI, user-friendly messages |
| Data analysts | Export capabilities, filtering | Real-time updates, notifications |

---

### The "How" Comes Last

**After answering What, Why, For Whom:**
- NOW you can design the solution
- Choose appropriate technologies
- Plan the implementation
- Estimate the effort

**Example Workflow:**

```
Requirements Meeting:
❌ "Let's build a microservice with GraphQL and React"
✅ "Let's define what the user needs and why"

After Requirements Clear:
✅ "Given the requirements, here are 3 technical approaches..."
```

---

### Complete Example

**Scenario:**

**WHAT:**
> "Customers must be able to view their real-time account balance on the mobile app."

**WHY:**
> "50% of support calls are 'What's my balance?' questions, costing $200k/year in support time. Real-time balance visibility will reduce these calls by 80%, saving $160k/year."

**FOR WHOM:**
> "Mobile app users (primarily consumers aged 25-45) who check their account 3-5 times per week."

**NOW HOW:**
Given the requirements:
- Must be fast (real-time)
- Must work on mobile
- High traffic (millions of users)

Technical approach:
1. Create new read-optimized endpoint
2. Cache balance with 30-second TTL
3. Use push notifications for instant updates on transactions
4. Implement using existing REST API (no new tech needed)

---

## Practice 2: Build in Small Batches

### The Principle

> "Making the smallest possible change that delivers a single, verifiable piece of value."

**Why This Matters:**
```
In legacy systems:
Small change = Small risk
Large change = Large risk

Risk is NOT linear - it's exponential with size!
```

---

### The Gambling Analogy

> "In a legacy system, every change is a gamble. The bigger the change, the bigger the gamble."

**Small Batches = Small Bets:**
- Lose less if wrong
- Recover faster
- Learn quickly
- Pivot easily

**Large Batches = High Stakes:**
- Catastrophic if wrong
- Long recovery
- Delayed feedback
- Sunk cost fallacy

---

### What is a "Small Batch"?

**Criteria:**
1. Delivers ONE piece of value
2. Can be tested independently
3. Can be deployed independently
4. Takes hours/days, not weeks/months
5. If it fails, impact is limited

**Examples:**

| ❌ Too Large | ✅ Small Batch |
|---|---|
| "Rewrite the billing system" | "Add tax calculation to invoice preview" |
| "Migrate to microservices" | "Extract user authentication to separate service" |
| "Redesign the UI" | "Update the header navigation with new logo" |
| "Refactor everything" | "Extract one 200-line function into 5 smaller functions" |

---

### Benefits in Legacy Code

**1. Fast Feedback:**
```
Small change → Deploy quickly → See result immediately
```

**2. Easy Rollback:**
```
Problem detected → Rollback small change → System restored
```

**3. Isolated Impact:**
```
Bug in small change → Only affects one feature → Limited blast radius
```

**4. Manageable Risk:**
```
Small batch fails → Learn and adjust → Try next small batch
```

**5. Continuous Progress:**
```
Week 1: Small batch ✓
Week 2: Small batch ✓
Week 3: Small batch ✓
...
6 months later: Major transformation complete!
```

---

### Implementation Strategy

**Breaking Down Large Changes:**

**Large Goal:** "Modernize the payment system"

**Small Batches:**
1. Add logging to existing payment flow (1 day)
2. Write characterization tests for core payment logic (2 days)
3. Extract payment validation into separate function (1 day)
4. Add new payment method (credit card) (3 days)
5. Refactor error handling (2 days)
6. Add observability instrumentation (2 days)
7. Extract payment processing to service (1 week)
...

**Each batch:**
- Delivers value
- Can be tested
- Can be deployed
- Limits risk

---

## Practice 3: Integrate Continuously

### The Principle

> "Merging your code changes into the master shared codebase very frequently."

**Frequency:**
- Multiple times per day
- Not weekly
- Not at feature completion
- Every few hours

---

### The Obvious Question

> "But My Feature Isn't Finished!"

**The Paradox:**
- Feature incomplete
- Yet committing to master
- How is this safe?

---

### The Solution: Feature Flags + Abstraction

**You DON'T use branches to hide unfinished work.**
**You USE:**

1. **Feature Flags:**
```java
if (FeatureFlags.isEnabled("new-checkout")) {
    // New incomplete code (hidden from users)
    newCheckoutFlow();
} else {
    // Old working code (users see this)
    oldCheckoutFlow();
}
```

2. **Branch by Abstraction** (covered earlier)

3. **Dark Launching:**
   - Deploy code that runs but isn't visible
   - Gradually enable for users

---

### The Rules

**1. Short-Lived Branches:**
> "The local 'branch' should not live for more than a few hours."

**Workflow:**
```
9am:  git pull origin master
      git checkout -b fix-bug-123
10am: Write code
11am: Write tests
12pm: git commit && git push
      Open pull request
1pm:  PR reviewed and merged to master
      Delete branch
```

**2. Master is Always Stable:**
> "The master branch is always stable and releasable."

**Requirements:**
- All tests pass
- Code reviewed
- Feature-flagged if incomplete
- Can deploy to production anytime

**3. Everyone Commits to Master:**
> "Everyone commits their work directly to master multiple times per day."

---

### Benefits in Legacy Systems

**1. Reduces Integration Risk:**
```
Continuous small integrations << One massive integration
```

**2. Finds Conflicts Early:**
```
Conflict found today → Easy to resolve
Conflict found after 3 months → Nightmare to resolve
```

**3. Encourages Collaboration:**
```
Team sees changes daily → Can provide feedback → Collective ownership
```

**4. Enables Fast Iteration:**
```
Change merged → Deployed to test → Feedback received → Next iteration
```

---

### Connection to Previous Practices

**Works With:**
- Practice 2 (Small Batches): Small changes are easy to integrate continuously
- Branch by Abstraction: Enables committing incomplete work safely
- Feature Flags: Hide incomplete features

**Requires:**
- Good test coverage
- Automated testing
- CI/CD pipeline
- Team discipline

---

## Practice 4: Collaborate

### The Principle

> "In a legacy system, no one is allowed to be a 'hero.'"

**The Enemy:**
- Knowledge silos
- Tribal knowledge
- One person knowing critical code
- "Only João touches this"

---

### The Bus Factor

**Definition:**
> "The bus factor is the number of team members that can be hit by a bus before the project is in serious trouble."

**In Legacy Systems:**
```
Bus Factor = 1 → Disaster waiting to happen
Bus Factor = 5 → Sustainable
```

**The Risk:**
- Person goes on vacation → Work blocks
- Person leaves company → Knowledge lost
- Person sick → Critical bug can't be fixed
- Bottleneck for all changes

---

### Collaboration Techniques

#### 1. Pair Programming

**What:**
> "Two engineers work at one keyboard."

**Roles:**
- **Driver:** Types the code
- **Navigator:** Thinks ahead, reviews, suggests

**Benefits:**
- Knowledge transfer (live)
- Instant code review
- Better solutions (two perspectives)
- Reduced bugs
- No knowledge silos

**When to Use:**
- Onboarding new team members
- Tackling complex legacy code
- High-risk changes
- Learning unfamiliar areas

---

#### 2. Mob Programming

**What:**
> "The whole team (or a small group) works on one problem, on one computer, at the same time."

**Setup:**
- One driver (rotates every 15 min)
- Everyone else navigates
- Big screen
- Open discussion

**Benefits:**
- Maximum knowledge sharing
- Best solution emerges
- Everyone understands the change
- No handoff delays

**When to Use:**
- Critical/complex problems
- Architecture decisions
- Learning sessions
- Breaking through blockers

---

#### 3. Collective Code Ownership

**What:**
> "The team, not an individual, owns every module."

**In Practice:**
- Anyone can change any code
- No "this is my code" mentality
- Team responsible together
- Shared standards

**Requirements:**
- Good test coverage
- Code reviews
- Clear coding standards
- Documentation

---

### Breaking Down Silos

**Strategies:**

1. **Rotate Assignments:**
   - Different developers work on different modules
   - No one "owns" a module permanently

2. **Documentation:**
   - Write down tribal knowledge
   - Update as you learn
   - Make implicit knowledge explicit

3. **Code Reviews:**
   - Everyone reviews everyone's code
   - Spreads knowledge
   - Improves quality

4. **Team Documentation Sessions:**
   - Dedicate time to document
   - Walk through complex areas
   - Answer questions

---

## Practice 5: Create CLEAN Code

### The Principle

> "Always leave the code cleaner than you found it." - The Boy Scout Rule

**Important:**
- You do NOT need to rewrite everything
- You do NOT need to clean entire files
- You DO make small improvements

---

### What "Create CLEAN Code" Means

**1. Stop the Rot:**
> "First, do no harm. Any new code you add must be clean."

**Standards for New Code:**
- Well-named variables
- Small functions
- Clear logic
- Properly tested
- Documented

**2. Make Incremental Improvements:**
> "While you're in that messy file to fix a bug, you apply the Boy Scout Rule."

**Example:**
```java
// You come to fix a bug in this 1000-line class
public class OrderProcessor {
    public void process() {
        // 1000 lines of mess
        // You need to fix a bug on line 500
    }
}

// Don't:
// - Rewrite the entire class
// - Spend 2 weeks refactoring

// Do:
// - Fix the bug
// - Extract the 50 lines around your fix into a well-named method
// - Add tests for that method
// - Commit
```

---

### The Incremental Approach

**Each Visit:**
```
1. Fix the bug/add the feature (main goal)
2. Make ONE or TWO small improvements nearby
3. Ensure tests pass
4. Commit
```

**Over Time:**
```
Visit 1: Clean 2% of the file
Visit 2: Clean another 3%
Visit 3: Clean another 2%
...
After 20 visits: File is 50% cleaner!
```

---

### Types of Improvements

**Low-Hanging Fruit:**
1. Rename unclear variables
2. Extract magic numbers to constants
3. Add comments to confusing sections
4. Break up long lines
5. Remove commented-out code
6. Fix formatting

**Medium Effort:**
1. Extract small methods
2. Remove duplication
3. Simplify conditionals
4. Add missing tests

**Don't Do (Unless Explicitly Tasked):**
1. Complete rewrites
2. Architectural changes
3. Large refactorings
4. Technology migrations

---

## Practice 6: Write the Test First

### The Principle

> "Before you change any existing code, you must first write a test that proves the code works as it does right now."

**Two Contexts:**

1. **Greenfield (New) Projects:**
   - Test-Driven Development (TDD)
   - Write failing test → Make it pass → Refactor

2. **Legacy Systems:**
   - Write characterization test
   - Capture CURRENT behavior
   - Then refactor safely

---

### The Legacy Code Approach

**Process:**

```
1. Understand current behavior
   ↓
2. Write test that captures it (bugs and all!)
   ↓
3. Run test → Should PASS
   ↓
4. This is your "Golden Master"
   ↓
5. Now safe to refactor
```

---

### Capturing the Behavior: Golden Master

**What is a Golden Master?**
> "You run the test and capture its exact output (a log, a file, a JSON string, etc.), bugs and all. This output is your 'Golden Master.'"

**Example:**

```java
@Test
public void testCalculateInvoice_goldenMaster() {
    // Arrange
    Invoice invoice = createComplexTestInvoice();

    // Act
    String result = legacyInvoiceCalculator.calculate(invoice);

    // Assert - captures CURRENT output (including bugs!)
    String expected = "Total: $99.99\n" +
                      "Tax: $8.49\n" +  // Even if this calc is wrong!
                      "Grand Total: $108.48";

    assertEquals(expected, result);
}
```

**Key Point:**
- Test captures reality, not ideal
- Includes bugs
- Provides safety net
- Allows refactoring
- Can fix bugs separately later

---

### Progressive Testing

**Stage 1: Golden Master (Coarse)**
```java
@Test
public void testEntireInvoiceProcess() {
    // Tests the whole flow
    // 1000 lines of code
    // One assertion
}
```

**Stage 2: After Refactoring (Fine-Grained)**
```java
@Test
public void testCalculateTax() {
    // Tests one small function
    // 20 lines of code
    // Multiple assertions
}

@Test
public void testCalculateDiscount() {
    // Another small function
}

// ... many small tests
```

---

## Practice 7: Specify Behaviors with Tests

### The Principle

> "Tests are the only trustworthy documentation for a legacy system."

**Why:**
- Comments get outdated
- Documentation gets forgotten
- Code changes but docs don't
- Tests MUST stay synchronized with code (or they fail)

---

### Behavior-Driven Development (BDD)

**Approach:**
> "Uses tests themselves to specify what the system is supposed to do in plain, human-readable language."

**Traditional Test Name:**
```java
@Test
public void testUserLogin_InvalidPassword() {
    // What does this test?
}
```

**BDD Specification:**
```java
@Test
public void given_userExists_when_invalidPassword_then_showError() {
    // Much clearer!
}
```

**Or Using BDD Framework:**
```gherkin
Scenario: User enters invalid password
  Given a user exists with username "john@example.com"
    And they are on the login page
  When they enter a valid username
    And they enter an invalid password
    And they click "Login"
  Then they should see an "Invalid password" error message
    And they should remain on the login page
    And their account should not be locked
```

---

### Benefits

**1. Living Documentation:**
- Tests describe behavior
- Always up-to-date (or fail)
- Readable by non-developers
- Captures business rules

**2. Regression Prevention:**
- Behavior locked in
- Changes trigger test failures
- Immediate feedback

**3. Communication Tool:**
- Team alignment
- Shared understanding
- Specifications in code

---

## Practice 8: Implement the Design Last

### The Principle

> "In a complex system, you cannot know the correct design until you've solved the problem."

**The Traditional Approach (Big Design Up Front):**
```
1. Design perfect architecture (weeks)
2. Create detailed UML diagrams
3. Plan all classes and interactions
4. Then implement
5. Realize design doesn't match reality
6. Either: Force code to fit wrong design, or abandon design
```

**The Problem:**
- Design based on assumptions
- Assumptions are often wrong
- Legacy codebase surprises you
- Wasted effort

---

### The Alternative: Implement the Design Last

**The Process:**

```
1. Write a Test (Practice 7)
   ↓
2. Make It Pass (Ugly)
   ↓
3. Refactor (Implement the Design)
```

---

### The Three Steps

#### Step 1: Write a Test

```java
@Test
public void given_validOrder_when_processed_then_customerCharged() {
    // Specify the behavior you want
}
```

#### Step 2: Make It Pass (Ugly)

```java
public void processOrder(Order order) {
    // Ugliest, simplest code possible
    double total = 0;
    for (Item item : order.getItems()) {
        total = total + item.getPrice();
    }
    Database.execute("UPDATE accounts SET balance = balance - " + total);
    EmailService.send("Order confirmed");
}
```

**Why Ugly is OK:**
- Test is green (behavior works!)
- We have a safety net
- Now we can improve it

#### Step 3: Refactor (Implement the Design)

```java
// Now with tests passing, refactor to clean design
public class OrderProcessor {
    private final PriceCalculator calculator;
    private final PaymentGateway gateway;
    private final NotificationService notifier;

    public void process(Order order) {
        Money total = calculator.calculateTotal(order);
        gateway.charge(order.getCustomer(), total);
        notifier.sendConfirmation(order);
    }
}
```

**Now:**
- Clean design
- Tests still pass
- Behavior preserved
- Design emerged from actual requirements

---

### Benefits in Legacy Code

**1. Reality-Based Design:**
- Design fits actual constraints
- No wasted effort on wrong assumptions

**2. Safety Net:**
- Tests catch design mistakes
- Can experiment freely

**3. Evolutionary:**
- Design improves over time
- Based on real needs

---

## Practice 9: Refactor Legacy Code

### The Principle

> "This is the 'payoff' practice, the one that all the previous eight practices are designed to enable."

**Martin Fowler's Definition:**
> "A change made to the internal structure of software to make it easier to understand and cheaper to modify without changing its observable behavior."

**Simple Translation:**
> "Cleaning the code without breaking it."

---

### What Refactoring Is

**Refactoring:**
- Changes internal structure
- Does NOT change external behavior
- Makes code easier to understand
- Makes code cheaper to modify
- Done in small steps
- With tests as safety net

**Refactoring is NOT:**
- Adding new features
- Fixing bugs
- Changing behavior
- Rewriting from scratch
- Done without tests

---

### Why It's the "Payoff"

**The Setup:**
```
Practice 1: Clear requirements → Know what to change
Practice 2: Small batches → Manageable refactorings
Practice 3: Continuous integration → Safe to merge
Practice 4: Collaboration → Share knowledge
Practice 5: Clean code → Incremental improvements
Practice 6: Test first → Safety net
Practice 7: Behavior specs → Know what to preserve
Practice 8: Design last → Refactor to good design
```

**The Payoff:**
```
Practice 9: NOW you can safely refactor legacy code!
```

---

### Common Refactorings

**1. Extract Method:**
```java
// Before: 100-line method
public void process() {
    // Lines 1-30: Validate
    // Lines 31-60: Calculate
    // Lines 61-100: Save
}

// After: Small, focused methods
public void process() {
    validate();
    calculate();
    save();
}

private void validate() { /* ... */ }
private void calculate() { /* ... */ }
private void save() { /* ... */ }
```

**2. Rename Variables:**
```java
// Before: Unclear
int d; // elapsed time in days

// After: Self-documenting
int elapsedTimeInDays;
```

**3. Extract Class:**
```java
// Before: God class with 50 methods
public class OrderProcessor {
    // Order methods
    // Payment methods
    // Shipping methods
    // Email methods
    // ...
}

// After: Focused classes
public class OrderProcessor { /* Order-specific */ }
public class PaymentService { /* Payment-specific */ }
public class ShippingService { /* Shipping-specific */ }
public class NotificationService { /* Email-specific */ }
```

**4. Remove Duplication:**
```java
// Before: Duplicated logic
public void processOnlineOrder() {
    validate();
    calculatePrice();
    applyOnlineDiscount();
    charge();
}

public void processStoreOrder() {
    validate();
    calculatePrice();
    applyStoreDiscount();
    charge();
}

// After: Shared logic extracted
public void processOrder(Order order) {
    validate();
    calculatePrice();
    applyDiscount(order.getType());
    charge();
}
```

---

### The Refactoring Workflow

**Step-by-Step:**

```
1. Ensure tests exist (Practice 6)
   ↓
2. Run tests → All green
   ↓
3. Make ONE small refactoring
   ↓
4. Run tests → Should still be green
   ↓
5. Commit
   ↓
6. Repeat
```

**Key:**
- Small steps
- Test after each step
- Commit frequently
- If tests fail, undo immediately

---

# Black Boxes to Modern Blueprints

## The Problem

### Analysis Paralysis Scenario

> "This is the 'Analysis Paralysis' scenario."

**The Situation:**
- Critical legacy system (payroll, logistics, etc.)
- System is completely opaque
- No documentation
- No source code (compiled binaries only)
- Original developers gone
- Technology obsolete

---

### The Modernization Deadlock

**Three Constraints:**

1. **Too Risky to Replace:**
   - Don't fully understand what it does
   - Unknown business rules
   - Hidden edge cases
   - Fear of missing critical functionality

2. **Too Costly to Maintain:**
   - Old operating system
   - Security vulnerabilities
   - No vendor support
   - Expensive hardware
   - Scarce expertise

3. **Too Critical to Ignore:**
   - Runs core business operations
   - Can't turn off
   - Downtime unacceptable
   - Business depends on it

**Result:**
```
Can't replace + Can't maintain + Can't ignore = DEADLOCK
```

---

## AI-Assisted Reverse Engineering

### The Old Way vs The New Way

**Old Way:**
> "Years of manual analysis by a team of 20."

**Approach:**
- Manual code inspection
- Interview users/stakeholders
- Document every behavior
- Reverse engineer by hand
- Very slow
- Very expensive

**New Way:**
> "AI-Assisted Reverse Engineering - Use LLMs/GenAI to accelerate turning artifacts into a blueprint."

**Approach:**
- Use AI to analyze artifacts
- Automate pattern recognition
- Generate documentation
- Accelerate understanding
- Weeks instead of years

---

### What We're NOT Doing

> "We cannot recover the original code (and we don't want to)."

**We Don't Need:**
- Perfect source code reconstruction
- Every implementation detail
- Original design documents

**We DO Need:**
> "We must recover the functional specification (the 'what,' not the 'how')."

**Focus:**
- What does the system do?
- What business rules exist?
- What are the workflows?
- What are the inputs/outputs?

---

## The Multi-Lens Approach

### The Strategy

> "We can't trust one source. We must triangulate all available artifacts."

**Why Multiple Lenses:**
- No single source has complete truth
- Each artifact reveals different information
- Cross-validation prevents errors
- Triangulation builds confidence

---

### Lens 1: UI Layer (The "Last Mile")

**Artifacts:**
- ASP files
- JavaScript files
- HTML templates
- Screenshots
- User recordings

**What It Tells Us:**
- User workflows
- Field names and labels
- Client-side validation rules
- Navigation paths
- User interactions
- Input formats

**Example:**
```html
<!-- From ASP file -->
<form action="/submitInvoice">
  <input name="invoiceAmount" required />
  <input name="taxRate" />
  <select name="paymentTerms">
    <option>Net 30</option>
    <option>Net 60</option>
  </select>
</form>
```

**Insights:**
- System processes invoices
- Requires amount and tax rate
- Payment terms: 30 or 60 days
- Validation on client side

---

### Lens 2: Data Layer (The "State")

**Artifacts:**
- Database schema (650+ tables)
- Stored procedures (1200+)
- Triggers
- Views
- Constraints

**What It Tells Us:**
- Business entities
- Relationships
- Business rules encoded in SQL
- Data transformations
- Calculated fields

**Example:**
```sql
-- Stored procedure
CREATE PROCEDURE CalculateInvoiceTotal
  @InvoiceID INT
AS
BEGIN
  UPDATE Invoices
  SET TotalAmount = (
    SELECT SUM(LineItems.Amount * (1 + TaxRates.Rate))
    FROM LineItems
    JOIN TaxRates ON LineItems.TaxCode = TaxRates.Code
    WHERE LineItems.InvoiceID = @InvoiceID
  )
  WHERE InvoiceID = @InvoiceID
END
```

**Insights:**
- Invoice totals calculated from line items
- Tax applied per line item
- Tax rates stored separately
- Total stored (not calculated on read)

---

### Lens 3: Opaque App Tier (The "Missing Logic")

**Artifacts:**
- Compiled binaries (.dll, .exe)
- No source code
- Decompiled assembly code
- Function signatures

**What It Tells Us:**
- This is the BLACK BOX
- Business logic is here
- Connects UI to Data
- Most difficult to understand

**The Challenge:**
- Can't read compiled code easily
- Decompiled code is cryptic
- Must infer logic from behavior

---

## Four-Step Process

### Step 1: Start Where Visibility is Highest

> "Principle: Start with what you can see. Anchor in artifacts users understand."

**UI Layer Reconstruction:**

**Process:**
```
1. Collect all ASP/JS files
2. Feed to AI in chunks
3. Prompt: "Summarize the UI elements, validation rules,
   and navigation paths from these files"
4. Document findings
5. Link to source files (lineage)
```

**Example Output:**
```
Screen: InvoiceEntry.asp
- Purpose: Create new invoices
- Fields: Customer (dropdown), Amount (number), Tax Rate (%), Terms (dropdown)
- Validation: Amount > 0, Tax Rate 0-100
- Navigation: Submit → InvoiceConfirmation.asp
- Source: InvoiceEntry.asp lines 45-120
```

---

**Data Layer Reconstruction:**

**Process:**
```
1. Export database schema
2. Export stored procedures
3. Feed to AI with context
4. Prompt: "Analyze this schema. Infer the relationships.
   Summarize the business logic in this stored procedure."
5. Document business rules
6. Track to source (lineage)
```

**Example Output:**
```
Entity: Invoice
- Primary Key: InvoiceID
- Relationships:
  - Customer (Many-to-One)
  - LineItems (One-to-Many)
  - Payments (One-to-Many)
- Calculated Fields: TotalAmount (sum of line items + tax)
- Business Rules:
  - Invoice can't be deleted if payment exists (FK constraint)
  - Tax calculated per line item (SP_CalculateInvoiceTotal)
- Source: dbo.Invoices table, SP_CalculateInvoiceTotal
```

---

**Key: Preserve Lineage!**

> "Track every insight back to its source artifact to prevent hallucination."

**Why Critical:**
- AI can hallucinate
- Must validate findings
- Source tracking enables verification
- Builds confidence

**Example:**
```
❌ Without Lineage:
"The system calculates tax at invoice level"
→ Is this true? Can't verify!

✅ With Lineage:
"The system calculates tax at invoice level"
→ Source: SP_CalculateInvoiceTotal, lines 15-22
→ Can verify! Can trust!
```

---

### Step 2: Connect the Dots (CDC & Inference)

**Change Data Capture (CDC):**

> "If possible, run the app and log database changes."

**Process:**
```
1. Enable database logging
2. Perform UI action (e.g., "Submit invoice")
3. Observe database changes
4. Map UI → Data connection
```

**Example:**
```
Action: User clicks "Submit" on InvoiceEntry.asp

Database Changes Observed:
- INSERT INTO Invoices (CustomerID, TotalAmount, ...)
- INSERT INTO LineItems (InvoiceID, Amount, ...)
- UPDATE Customers SET LastInvoiceDate = GETDATE()
```

**Connection Established:**
> "When user clicks 'Submit' on screen_ABC... → ...rows are inserted into TABLE_X and TABLE_Y."

---

**Server Logic Inference:**

> "We now have a hypothesis. The 'black box' DLLs must contain the logic that links screen_ABC to TABLE_X."

**Reasoning:**
```
UI Layer: InvoiceEntry.asp calls submitInvoice()
Data Layer: Tables Invoices, LineItems updated

Therefore:
App Tier (Black Box): Must contain:
  - Function named submitInvoice()
  - Validation logic
  - Business rules (e.g., update LastInvoiceDate)
  - Database calls
```

**Target Identified:**
> "This gives us a target for the hardest part."

Now we know:
- Which DLL to analyze
- Which function to focus on
- Expected inputs/outputs
- Database operations

---

### Step 3: AI-Assisted Binary Archaeology

**The Challenge:**

> "We have 45 DLLs with 1000s of functions."

**The Problem:**
> "Brute-force (feeding all ASM to an LLM) fails. Context windows overflow, and the AI hallucinates."

---

**The Solution: Functional Slicing**

> "Slice the DLL based on functional area (the 'subtree' approach)."

**Strategy:**
```
Don't analyze: All 4,000 functions
DO analyze: The 40 relevant to our workflow
```

**Process:**
```
1. Identify target function (from Step 2)
   Example: submitInvoice()

2. Decompile only that function
   Tools: ILSpy, dotPeek, Ghidra

3. Identify dependencies
   - What other functions does it call?
   - What data structures does it use?

4. Decompile those dependencies (level 2)

5. Stop at clear boundaries
   - Standard library calls
   - Database access layer
   - External services

6. Feed this "subtree" to AI
   Prompt: "Analyze this function and its dependencies.
   Explain the business logic in plain English."
```

---

**Example:**

**Decompiled Code (simplified):**
```csharp
// From InvoiceProcessor.dll
public void SubmitInvoice(InvoiceData data) {
    // Validate
    if (data.Amount <= 0) throw new ValidationException();
    if (data.Customer == null) throw new ValidationException();

    // Business rule
    if (data.Customer.IsVIP && data.Amount > 10000) {
        data.PaymentTerms = "Net 60";  // VIPs get extended terms
    }

    // Save
    _database.Insert("Invoices", data);
    _database.Update("Customers",
        data.Customer.ID,
        "LastInvoiceDate",
        DateTime.Now);
}
```

**AI Prompt:**
```
Analyze this function and explain the business logic:

[Paste decompiled code]

Focus on:
1. Validation rules
2. Business rules
3. Data operations
```

**AI Output:**
```
Business Logic Summary:

1. Validation Rules:
   - Invoice amount must be positive
   - Customer must be specified

2. Business Rules:
   - VIP customers with orders over $10,000 automatically receive 60-day payment terms
   - Regular customers use default terms

3. Data Operations:
   - Creates new invoice record
   - Updates customer's last invoice date to current timestamp

4. Implicit Requirements:
   - Payment terms default is "Net 30" (not shown in code, but implied)
```

---

### Step 4: Triangulate and Validate (Human-in-the-Loop)

**The Reality:**

> "AI is an accelerator, not an oracle. You must validate its hypotheses."

**Triangulation Process:**

```
UI Layer says: Field "paymentTerms" with options "Net 30", "Net 60"
Data Layer says: Column PaymentTerms VARCHAR(20)
Binary Analysis says: VIPs with Amount > 10000 get "Net 60"

Triangulation:
✓ All three sources align
✓ Hypothesis confirmed
✓ Document: "VIP Business Rule"
```

---

**Validation Checklist:**

> "Does the function signature from the Binary match the API call from the UI Layer?"

```
UI calls: submitInvoice(customerID, amount, taxRate)
Binary function: SubmitInvoice(InvoiceData data)
  where InvoiceData has: CustomerID, Amount, TaxRate

✓ Match confirmed
```

> "Does the business logic in the Pseudocode match the DB changes from CDC?"

```
Pseudocode: Updates Customers.LastInvoiceDate
CDC log: UPDATE Customers SET LastInvoiceDate = ...

✓ Match confirmed
```

---

**Human Validation:**

> "The final, generated spec must be walked through with a sys-admin or long-time user to confirm the functionality."

**Process:**
```
1. Generate functional specification document
2. Schedule walkthrough with domain expert
3. Present findings:
   - "We believe the system does X"
   - "Is this correct?"
   - "Are there edge cases we're missing?"
4. Iterate based on feedback
5. Validate with actual system behavior
```

**Example Questions:**
- "When a VIP customer places a large order, do they always get Net 60 terms?"
- "Are there any scenarios where LastInvoiceDate is NOT updated?"
- "What happens if the customer is inactive?"

---

## Summary: Black Boxes to Modern Blueprints

**The Four Steps:**

1. **Start Where Visibility is Highest:**
   - UI Layer: User workflows, field validation
   - Data Layer: Entities, relationships, business rules
   - Preserve lineage: Track insights to source

2. **Connect the Dots:**
   - CDC: Map UI actions to data changes
   - Infer: Hypothesize about black box logic
   - Target: Identify relevant functions

3. **AI-Assisted Binary Archaeology:**
   - Slice: Focus on relevant functions (subtrees)
   - Decompile: Extract pseudocode
   - Analyze: Use AI to explain business logic
   - Don't boil the ocean: Small chunks

4. **Triangulate and Validate:**
   - Cross-reference: UI + Data + Binary
   - Human-in-loop: Domain expert validation
   - Test: Verify against actual system behavior
   - Document: Create functional specification

---

**Key Principles:**

> "Start Where Visibility is Highest: (UI, DB). Don't start with binaries."

> "Enrich in Passes: Small chunks. Build context. Don't boil the ocean."

> "Triangulate Everything: Never trust one source. (UI + DB + Binary)."

> "Preserve Lineage: Track every insight to its source artifact. This is your anti-hallucination shield."

> "Keep Humans in the Loop: AI accelerates analysis. Humans provide domain understanding."

---

# GenAI in Software Engineering

## Requirements Extraction

### Overview

> "Static & dynamic analysis enhanced by LLM explanations"

**The Goal:**
- Extract business requirements from legacy code
- Understand what the system does
- Document implicit knowledge
- Create specifications for modernization

---

### Techniques

**1. Static Analysis + LLM:**
```
1. Parse code structure
2. Extract functions, classes, dependencies
3. Feed to LLM: "Explain what this code does in business terms"
4. Generate human-readable documentation
```

**2. Dynamic Analysis + LLM:**
```
1. Run system and capture behavior
2. Log inputs/outputs
3. Feed to LLM: "What business rule does this represent?"
4. Document behavioral patterns
```

---

### Outputs

> "Generate readable flowcharts and CRUD maps"

**Flowcharts:**
- Visualize business processes
- Show decision points
- Identify workflows

**CRUD Maps:**
- Create, Read, Update, Delete operations
- Which services touch which data
- Data ownership

---

> "Extract business rules (e.g. COBOL BREX)"

**Example:**
```cobol
IF CUSTOMER-TYPE = "VIP" AND ORDER-AMOUNT > 10000
   MOVE "NET-60" TO PAYMENT-TERMS
ELSE
   MOVE "NET-30" TO PAYMENT-TERMS
END-IF
```

**Extracted Business Rule:**
```
Rule: VIP Customer Large Order Payment Terms
Condition: Customer is VIP AND Order amount exceeds $10,000
Action: Payment terms set to Net 60 days
Otherwise: Payment terms set to Net 30 days
```

---

> "Create documentation usable by non-technical roles"

**For:**
- Business analysts
- Product managers
- Domain experts
- Stakeholders

**Format:**
- Plain English
- Business terminology
- No technical jargon
- Diagrams and examples

---

## Mental Models and Domain Maps

### Overview

> "Build mental models and domain maps"

**The Goal:**
- Understand the domain
- Map business concepts
- Identify relationships
- Create shared understanding

---

### Techniques

**1. Event Storming + GenAI Summaries:**

> "Use Event Storming + GenAI summaries"

**Process:**
```
1. Conduct Event Storming workshop
   - Identify domain events
   - Map workflows
   - Capture business rules

2. Feed workshop outputs to GenAI
   Prompt: "Summarize these events into business processes"

3. Generate domain model diagrams

4. Validate with domain experts
```

**Example Events:**
- Order Placed
- Payment Received
- Invoice Generated
- Shipment Dispatched

**AI-Generated Summary:**
```
Business Process: Order Fulfillment

1. Customer places order
2. System validates inventory
3. Payment is processed
4. Invoice is generated
5. Warehouse dispatches shipment
6. Customer notified
```

---

**2. Combine Code + Documentation in Graph:**

> "Combine code + documentation in graph"

**Approach:**
- Build knowledge graph
- Nodes: Code entities, documents, business concepts
- Edges: Relationships, dependencies, references

**Example:**
```
[Business Concept: "VIP Customer"]
  ├─→ [Code: Customer.IsVIP property]
  ├─→ [Business Rule: "Extended Payment Terms"]
  │   └─→ [Code: SubmitInvoice.SetPaymentTerms()]
  └─→ [Documentation: "VIP Program Guide"]
```

---

**3. Enrich Chatbot Context:**

> "Enrich chatbot context to answer SME-level questions"

**Goal:**
- AI assistant with domain knowledge
- Can answer questions like domain expert
- Supports developers working on legacy system

**Example Interaction:**
```
Developer: "Why do some invoices have Net 60 payment terms?"

AI Assistant: "Based on the code in InvoiceProcessor.dll
(SubmitInvoice method, lines 45-50) and the business rule
documentation, VIP customers with orders over $10,000
automatically receive Net 60 payment terms. This rule was
introduced in 2015 to incentivize large orders from premium
customers. Regular customers receive Net 30 terms."
```

---

### Future Directions

> "You'll explore this topic in more depth in the upcoming classes."

**Emerging Areas:**
- AI-powered code understanding
- Automated modernization
- Intelligent refactoring suggestions
- Business rule extraction
- Test generation
- Documentation automation

---

# Project Requirements

## The Context

> "A new investor loved your application — but wants it aligned with the latest trends."

**The Scenario:**
- Your application is successful
- New investor wants modernization
- Focus on user experience
- Emphasis on observability

---

## Your Tasks

### Task 1: Conversational Assistant

> "Create a conversational assistant to integrate into your tool."

**Requirements:**
- Integrate AI/LLM-based chat interface
- Help users with the application
- Answer questions
- Guide workflows
- Context-aware

**Considerations:**
- Which LLM to use?
- How to integrate into existing app?
- What context to provide?
- How to handle edge cases?
- Privacy and security?

**Connection to Slide 09:**
- GenAI in Software Engineering
- Requirements extraction techniques
- Building mental models
- Chatbot enrichment

---

### Task 2: Frontend Observability

> "Improve observability to consider frontend actions."

**Requirements:**
- Track user interactions
- Log frontend errors
- Measure performance
- Collect telemetry
- Send to observability backend

**Considerations:**
- Which metrics to collect?
- How to instrument frontend?
- What tools to use?
- Privacy concerns?
- Performance impact?

**Connection to Slide 08:**
- Observability pillars (Logs, Metrics, Traces)
- OpenTelemetry
- Distributed tracing
- Monitoring patterns

---

## Freedom and Flexibility

> "You're free to define the strategy, design, and implementation approach."

**Your Decisions:**
- Technology choices
- Architecture
- Implementation details
- Prioritization
- Rollout strategy

**Apply What You've Learned:**
- Practice 1: What, Why, For Whom before How
- Practice 2: Build in small batches
- Practice 3: Integrate continuously
- Practice 6: Write tests first
- All nine practices!

---

# Study Tips and Exam Preparation

## Critical Concepts to Master

### 1. Legacy Code Definition

**Remember:**
> "Legacy Code is code you are afraid to change."

**Why?**
> "Because there are no tests. Full stop."

**Exam Tips:**
- Don't say "old code"
- Focus on testability
- Explain the fear factor
- Connect to technical debt

---

### 2. Technical Debt

**Key Points:**
- Payday loan analogy
- Interest compounds
- Debt spiral mechanism
- Strategic vs accidental debt

**Exam Question Types:**
- Explain technical debt with example
- Describe the debt spiral
- How to prevent/reduce technical debt

---

### 3. Warning Signs of Legacy Code

**The Five Signs:**
1. Complexity (2000-line functions)
2. Tribal Knowledge (Only João knows)
3. Coupling (Change one thing, deploy three services)
4. Regressions (Fix one, break three)
5. Long Feedback Loops

**Exam Tips:**
- Memorize all five
- Be able to explain each
- Provide examples
- Suggest remediation

---

### 4. Refactoring Macro-Patterns

**System Strangling:**
- Use case: Replace entire service
- Key component: Proxy/Façade
- Six steps
- Data migration strategies (3 options)

**Branch by Abstraction:**
- Use case: Replace component in monolith
- Avoids merge hell
- Abstraction layer + Feature flag
- Stay on master branch

**Exam Tips:**
- Know when to use which pattern
- Explain the steps
- Contrast the two approaches
- Understand the data problem

---

### 5. The Nine Practices

**Be Able to:**
- List all nine practices
- Explain each in detail
- Provide examples
- Show how they interconnect
- Explain why practice 9 is the "payoff"

**Exam Focus:**
1. What, Why, For Whom Before How
2. Build in Small Batches
3. Integrate Continuously
6. Write the Test First
9. Refactor Legacy Code

---

### 6. Black Boxes to Modern Blueprints

**Key Concepts:**
- The three-way deadlock
- Multi-lens approach (UI, Data, Binary)
- Four-step process
- Triangulation
- Human-in-the-loop

**Exam Tips:**
- Explain why AI is needed
- Describe the process
- Emphasize validation
- Lineage tracking importance

---

### 7. GenAI in Software Engineering

**Applications:**
- Requirements extraction
- Business rule documentation
- Mental model building
- Chatbot enrichment

**Exam Tips:**
- Connect to legacy code management
- Explain benefits
- Discuss limitations
- Human oversight importance

---

## Key Patterns and Techniques

### Pinning Tests

**What:**
- Characterization tests
- Capture current behavior
- Coarse-grained
- Enable refactoring

**When to Use:**
- Starting point for legacy code
- Before refactoring
- No existing tests

**Exam Question:**
> "How would you begin refactoring a 1000-line function with no tests?"

**Answer:**
1. Write pinning test (capture current behavior)
2. Run test (should pass)
3. Extract small method
4. Run test (should still pass)
5. Add finer-grained tests for extracted method
6. Repeat

---

### System Strangling Steps

**Memorize the 6 Steps:**

1. Create new interface/service
2. Insert the proxy
3. Configure proxy (100% to old)
4. Implement ONE endpoint in new
5. Change proxy logic (route that endpoint to new)
6. Monitor and repeat

**Data Migration Options:**

1. **Shared DB:** Fast & Dangerous
2. **Data Syncing:** Slow & Safe
3. **Data Strangulation:** The Goal (flip ownership)

---

### Branch by Abstraction

**Steps:**
1. Create abstraction layer (interface)
2. Implement new supplier
3. Use feature flag to switch
4. Gradually enable
5. Remove old implementation

**Key Benefit:**
- No merge hell
- Stay on master
- Continuous integration

---

## Common Exam Question Types

### 1. Definitions

**Examples:**
- "Define legacy code."
- "What is technical debt?"
- "Explain the debt spiral."
- "What is a pinning test?"

**How to Answer:**
- Give the definition (from slides)
- Explain why it matters
- Provide an example
- Connect to broader concepts

---

### 2. Compare and Contrast

**Examples:**
- "Compare System Strangling vs Branch by Abstraction."
- "Contrast pinning tests vs unit tests."
- "Greenfield TDD vs Legacy test-first approach."

**How to Answer:**
- Create a comparison table
- Highlight use cases for each
- Explain when to use which
- Note similarities and differences

---

### 3. Scenario-Based Questions

**Example:**
> "You've inherited a 10-year-old monolith with no tests. The business wants to add a new payment provider. How do you proceed?"

**How to Answer:**
1. Apply Practice 1 (What, Why, For Whom)
2. Identify the legacy code challenges
3. Choose appropriate pattern (likely BBA)
4. Outline steps:
   - Write pinning tests
   - Create abstraction (PaymentProvider interface)
   - Wrap existing provider
   - Implement new provider
   - Feature flag
   - Gradual rollout
5. Emphasize testing and small batches

---

### 4. Process Questions

**Examples:**
- "Describe the process for strangling a legacy service."
- "Explain the four-step process for reverse engineering a black box system."
- "How do the nine practices interconnect?"

**How to Answer:**
- Clearly number the steps
- Explain each step
- Show the flow/dependencies
- Emphasize key points at each step

---

### 5. Problem-Solving Questions

**Example:**
> "A developer says: 'I'll create a feature branch and merge when done in 3 months.' What's wrong with this approach? What should they do instead?"

**How to Answer:**
1. **Identify the problem:**
   - Long-lived branch
   - Delayed integration
   - Merge hell risk
   - Divergent codebases

2. **Explain the consequences:**
   - Conflicts compound
   - Integration delayed
   - High-risk merge
   - Code may break after merge

3. **Propose solution:**
   - Use Branch by Abstraction
   - Stay on master
   - Feature flags
   - Daily integration
   - Small batches

---

### 6. "Why" Questions

**Examples:**
- "Why is collaboration critical in legacy systems?"
- "Why write tests before refactoring?"
- "Why use a proxy in the strangler pattern?"

**How to Answer:**
- State the reason clearly
- Explain the problem it solves
- Provide an example
- Connect to principles

---

## Practical Skills Checklist

**Can You:**

- [ ] Identify the five warning signs of legacy code in a codebase?
- [ ] Write a pinning test for an existing function?
- [ ] Explain when to use System Strangling vs Branch by Abstraction?
- [ ] Describe the six steps of the Strangler Pattern?
- [ ] Implement a feature flag for gradual rollout?
- [ ] List all nine practices to extend software life?
- [ ] Explain the debt spiral and how to break it?
- [ ] Describe the multi-lens approach to reverse engineering?
- [ ] Apply the "What, Why, For Whom" before starting work?
- [ ] Refactor a function using small, test-protected steps?

---

## Important Distinctions

### Legacy vs Old

| Old Code | Legacy Code |
|---|---|
| 20 years old | Age irrelevant |
| May have good tests | No tests |
| Can change confidently | Afraid to change |
| Well documented | May lack documentation |
| Not necessarily legacy | IS legacy without tests |

**Key:**
> "If you wrote code last week with no tests... congratulations, you wrote 'future legacy.'"

---

### Refactoring vs Rewriting

| Refactoring | Rewriting |
|---|---|
| Change internal structure | Replace with new code |
| Preserve behavior | Change behavior |
| Small steps | Big-bang |
| Test-protected | High risk |
| Continuous value | Delayed value |

**Key:**
> "Refactoring is NOT rewriting from scratch."

---

### System Strangling vs Branch by Abstraction

| System Strangling | Branch by Abstraction |
|---|---|
| Service-level | Component/module-level |
| External replacement | Internal replacement |
| Proxy routes traffic | Abstraction + flag |
| Full service | Single module/library |
| Separate deployments | Same deployment |

---

### Pinning Tests vs Unit Tests

| Pinning Tests | Unit Tests |
|---|---|
| Coarse-grained | Fine-grained |
| Test large behavior | Test small function |
| Capture current (bugs too) | Test correct behavior |
| Starting point | End goal |
| High-level | Low-level |

---

### Technical Debt: Strategic vs Accidental

| Strategic Debt | Accidental Debt |
|---|---|
| Intentional | Unintentional |
| To learn/ship fast | Due to pressure/ignorance |
| Tracked and planned | Unknown/forgotten |
| Paid down deliberately | Accumulates |

**Both must be paid!**

---

## Formulas and Key Numbers

### Bus Factor

```
Bus Factor = Number of people who can be "hit by a bus"
             before project is in trouble

Target: Bus Factor ≥ 3
Danger: Bus Factor = 1
```

---

### Batch Size vs Risk

```
Risk ∝ (Batch Size)²

Risk is NOT linear - it's exponential!

Small batch = Small risk
Large batch = HUGE risk
```

---

### Technical Debt Interest

```
Development Time = Base Time + (Debt × Interest Rate)

As debt increases → Development slows
As development slows → Pressure increases
As pressure increases → More debt added
→ Debt Spiral!
```

---

## Exam Strategy

### Before the Exam

1. **Review slide content thoroughly**
2. **Memorize key definitions**
3. **Understand the nine practices**
4. **Know both macro-patterns cold**
5. **Practice scenario questions**
6. **Create summary sheets**

### During the Exam

1. **Read questions carefully**
2. **Look for keywords:**
   - "Define" → Precise definition
   - "Explain" → Definition + why + example
   - "Compare" → Table or structured comparison
   - "Process" → Numbered steps
3. **Use examples** from slides or your experience
4. **Structure answers** clearly
5. **Connect concepts** to show understanding
6. **Budget time** appropriately

### Answer Structure

**For Concept Questions:**
```
1. Definition
2. Why it matters
3. Example
4. Connection to other concepts
```

**For Process Questions:**
```
1. Overview
2. Numbered steps
3. Key points at each step
4. Expected outcome
```

**For Scenario Questions:**
```
1. Analyze the situation
2. Identify challenges
3. Choose approach/pattern
4. Explain steps
5. Justify choices
```

---

# Connections to Other Slides

## Slide 04: CI/CD

**Connections:**

**Practice 3: Integrate Continuously**
- Requires CI/CD pipeline
- Automated testing on every commit
- Fast feedback loops
- Deploy frequently

**Branch by Abstraction**
- Enables continuous integration
- No long-lived branches
- Feature flags for incomplete work

---

## Slide 06: Testing

**Connections:**

**Practice 6: Write the Test First**
- Foundation of TDD
- Applied to legacy code as pinning tests
- Safety net for refactoring

**Practice 7: Specify Behaviors with Tests**
- BDD approach
- Tests as documentation
- Executable specifications

**Pinning Tests**
- Characterization testing
- Starting point for legacy refactoring

---

## Slide 07: Infrastructure as Code

**Connections:**

**Pets vs Cattle**
- Relates to legacy vs modern systems
- Legacy: Pets (irreplaceable)
- Modern: Cattle (replaceable)

**Immutable Infrastructure**
- Prevents configuration drift
- Similar philosophy to refactoring
- Replace vs modify

---

## Slide 08: Monitoring and Observability

**Connections:**

**Project Requirements: Frontend Observability**
- Apply observability principles
- Three pillars: Logs, Metrics, Traces
- OpenTelemetry integration

**Refactoring Legacy Systems**
- Need observability to refactor safely
- Monitor during migrations
- Validate behavior preservation

**System Strangling - Step 6: Monitor**
- Critical for strangler pattern
- Compare old vs new
- Detect issues early

---

## Cross-Slide Themes

### 1. Small Batches

- **Slide 04 (CI/CD):** Frequent small deployments
- **Slide 09 (Legacy):** Practice 2 - Build in small batches
- **Principle:** Reduce risk through size

### 2. Testing

- **Slide 06 (Testing):** Test strategies, TDD, BDD
- **Slide 09 (Legacy):** Practices 6, 7, 9 - Test-first refactoring
- **Principle:** Tests enable safe change

### 3. Gradual Migration

- **Slide 07 (IaC):** Blue-green deployments
- **Slide 08 (Observability):** Instrumentation rollout
- **Slide 09 (Legacy):** System strangling, BBA
- **Principle:** Incremental, reversible changes

### 4. Automation

- **Slide 04 (CI/CD):** Automated pipelines
- **Slide 07 (IaC):** Automated provisioning
- **Slide 09 (Legacy):** Automated testing for refactoring
- **Principle:** Reduce manual errors, increase speed

---

# Summary and Key Takeaways

## The Big Picture

**Legacy Code is Inevitable:**
- Most software is legacy
- "Future legacy" is created daily
- Learning to manage it is essential
- Professional skill, not optional

**Tests Are the Differentiator:**
- With tests: Confident changes
- Without tests: Fear and fragility
- Tests = anti-legacy insurance

**Incremental Improvement:**
- Don't need to rewrite
- Small batches
- Boy Scout Rule
- Continuous improvement

---

## The Two Macro-Patterns

### When to Use Each

**System Strangling:**
- ✓ Replacing entire service
- ✓ Large vertical slice
- ✓ Multiple teams
- ✓ Service boundaries clear

**Branch by Abstraction:**
- ✓ Component inside monolith
- ✓ Library/framework replacement
- ✓ Single codebase
- ✓ Stay on master branch

---

## The Nine Practices

**Remember:**
Practices 1-8 enable Practice 9 (Refactoring)

**Core Practices:**
1. What, Why, For Whom → Before How
2. Small Batches → Reduce risk
3. Integrate Continuously → Avoid merge hell
4. Collaborate → Break silos
5. CLEAN Code → Boy Scout Rule
6. Test First → Safety net
7. Specify with Tests → Living documentation
8. Design Last → Reality-based design
9. Refactor → Payoff!

---

## Reverse Engineering Legacy Systems

**The Approach:**
- Multi-lens (UI, Data, Binary)
- AI-assisted analysis
- Triangulation
- Human validation
- Preserve lineage

**The Goal:**
- Functional specification
- Not perfect source reconstruction
- "What" not "How"

---

## GenAI's Role

**Applications:**
- Requirements extraction
- Documentation generation
- Business rule capture
- Mental model building
- Chatbot enrichment

**Remember:**
- AI accelerates
- Humans validate
- Keep humans in loop
- Anti-hallucination: Lineage tracking

---

## Project Connection

**Task 1: Conversational Assistant**
- Apply GenAI concepts
- Integrate into application
- Context-aware help

**Task 2: Frontend Observability**
- Monitoring patterns
- Telemetry collection
- Three pillars

**Freedom:**
- Define strategy
- Choose technologies
- Apply the nine practices

---

## Final Thoughts

> "Today's cutting-edge technology is tomorrow's legacy code."

**Prevention is Better Than Cure:**
- Write tests from day one
- Build in small batches
- Integrate continuously
- Create clean code
- Document as you go

**When Dealing with Legacy:**
- Don't panic
- Apply systematic approaches
- Use the patterns
- Test, test, test
- Improve incrementally

**The Mindset:**
- Legacy is not a failure
- It's a successful system that lasted
- Treat it with respect
- Apply engineering discipline
- Make it better, one change at a time

---

## Good Luck!

**You're Ready If:**
- ✓ You can define legacy code
- ✓ You understand technical debt
- ✓ You know the nine practices
- ✓ You can explain both macro-patterns
- ✓ You understand the multi-lens approach
- ✓ You can apply concepts to scenarios

**Remember:**
- Structure your answers
- Use examples
- Connect concepts
- Show your understanding
- Apply the practices

**Most Importantly:**
> "Legacy code is code you're afraid to change. But with the right techniques, tools, and mindset, you don't have to be afraid anymore."

---

**End of Study Guide - Slide 09**
**Legacy Code Management and Evolution**

*Good luck with your studies and exam!*