# Software Engineering - Study Guide (Slide 06)
## Advanced Software Testing - Complete Exam Preparation Guide

---

# Table of Contents

1. [Why Testing Matters](#why-testing-matters)
   - [Problems Without Tests](#problems-without-tests)
   - [Real-World Case Study: Mars Climate Orbiter](#real-world-case-study-mars-climate-orbiter)
2. [Test Process Fundamentals](#test-process-fundamentals)
   - [Test Process Overview](#test-process-overview)
   - [Properties of Good Tests](#properties-of-good-tests)
3. [Test Pyramid and Strategies](#test-pyramid-and-strategies)
   - [The Test Pyramid](#the-test-pyramid)
   - [Alternative Models](#alternative-models)
4. [Types of Testing](#types-of-testing)
   - [Static Testing](#static-testing)
   - [Unit Testing](#unit-testing)
   - [Integration Testing](#integration-testing)
   - [System Testing](#system-testing)
   - [End-to-End (E2E) Testing](#end-to-end-e2e-testing)
5. [Advanced Testing Types](#advanced-testing-types)
   - [Performance Testing](#performance-testing)
   - [Chaos Testing](#chaos-testing)
   - [Security Testing](#security-testing)
6. [Integration with CI/CD](#integration-with-cicd)
7. [Testing in Production](#testing-in-production)
8. [Practical Implementation](#practical-implementation)
9. [Study Tips and Exam Preparation](#study-tips-and-exam-preparation)

---

# Why Testing Matters

## Problems Without Tests

### The Evolution of Software Projects

As products grow, problems multiply without proper testing:

---

### Problem 1: Lack of Confidence in Change

**Scenario:**
- Complete solution deployed
- Increasing features
- Growing user base
- Multiple clients

**The Problem:**
> "**Lack of confidence in change**"

**Why:**
- Feature requests are **always coming**
- Fear of breaking existing functionality
- Uncertainty about impact of changes
- Can't move quickly

**Result:**
- Slow development
- Hesitation to refactor
- Technical debt accumulates
- Innovation stalls

---

### Problem 2: Bugs Found in Production

**The Reality:**
> "**Bugs found in production**"

**Consequences:**
- **Puts projects at risk**
  - Customer dissatisfaction
  - Revenue loss
  - Reputation damage

- **High chances of regressions**
  - Fix one bug, create another
  - Cascade of failures
  - Unpredictable behavior

---

### Problem 3: Manual Testing Limitations

**The Challenge:**
> "**Manual testing**: Very slow and error prone"

**Why It Doesn't Scale:**
- Too slow for frequent releases
- Human error inevitable
- **Not affordable** as product grows
- Cannot test every scenario
- Boring and demotivating for testers

---

### The Economic Reality

> **"cost(init) << cost(change)"** - Kent Beck

**Translation:**
- **Initial development cost** is much less than **cost of changing later**
- Bugs found early = cheap to fix
- Bugs found in production = expensive to fix
- Testing is an investment that pays off

**The Economics:**
- Find bug during development: $1
- Find bug during testing: $10
- Find bug in production: $100+
- Critical production bug: $10,000+

---

## Real-World Case Study: Mars Climate Orbiter

### The Story

**Project:** Mars Climate Orbiter
- Launched by NASA on December 11, 1998
- 638-kilogram (1,407 lb) robotic space probe
- Mission: Study Martian climate, atmosphere, and surface changes
- Role: Communications relay for Mars Polar Lander

---

### The Failure

**Date:** September 23, 1999

**What Happened:**
- Communication with spacecraft **permanently lost**
- During orbital insertion
- Spacecraft encountered Mars on wrong trajectory
- Brought it **too close to the planet**
- Either destroyed in atmosphere or escaped into solar orbit

**Cost:** $327.6 million (total mission cost)

---

### The Root Cause

> "An investigation attributed the failure to a **measurement mismatch between two software systems**: **metric units by NASA** and **non-metric ('English') units by spacecraft builder Lockheed Martin**."

**The Bug:**
- NASA software: Used metric units (Newtons)
- Lockheed Martin software: Used English units (pound-force)
- No conversion between systems
- Navigation calculations completely wrong

---

### The Lesson

**What Could Have Prevented This:**
- **Integration tests** between NASA and Lockheed systems
- **Unit tests** validating unit conversions
- **Contract tests** specifying units
- **Type systems** enforcing unit types
- **Code reviews** catching unit assumptions

**Key Insight:**
> This $327 million failure was caused by a **lack of proper testing** and **integration validation**.

**Takeaway:**
If it can happen to NASA, it can happen to anyone. **Testing is not optional.**

---

# Test Process Fundamentals

## Test Process Overview

### The Reality of Testing

> "Test programs on **different levels**, ranging from testing **small methods** to testing **entire systems** with databases and web services. Each level has **advantages and disadvantages**."

---

### Exhaustive Testing is Impossible

> "**Exhaustive testing is impossible** (*). The life of a tester involves making **trade-offs** about how much testing is needed."

**Why Impossible:**
- Infinite possible inputs
- Infinite possible states
- Infinite possible combinations
- Time and resource constraints

**The Tester's Job:**
- Decide what to test
- Decide what not to test
- Maximize value of tests
- Balance coverage vs cost

---

### Modern Context: LLMs and Testing

**Footnote from slides:**
> "(*) in the LLMs era it seems that machine can cover almost everything, but **dimension of the software should be considered**"

**Reality Check:**
- LLMs can generate many test cases
- But still can't test everything
- Software complexity grows faster
- Still need strategic testing

---

## Exit Criteria

### Definition

> "The set of **generic and specific conditions**, agreed upon with the stakeholders, for **permitting a process to be officially completed**."

**Source:** ISTQB (International Software Testing Qualifications Board) Glossary

---

### Purpose

> "The purpose of exit criteria is to **prevent a task from being considered completed** when there are still **outstanding parts** of the task that have not been finished."

**Why Important:**
- Prevents premature "done"
- Ensures quality standards met
- Provides objective completion criteria
- Aligns team expectations

---

### Usage

> "Exit criteria are used to **report against** and to **plan when to stop testing**."

**Examples of Exit Criteria:**
- All critical bugs fixed
- 80% code coverage achieved
- All acceptance tests passing
- Performance benchmarks met
- Security scan completed
- No high-severity issues remaining

---

## Properties of Good Tests

### 1. Testability

**Definition:**
> "The ability to **support acceptance criteria**"

**Example:**
- Assert expected behavior
- Verify outputs match inputs
- Validate state changes
- Check side effects

**In Practice:**
```
✓ Can verify the test passes/fails
✓ Clear expected vs actual comparison
✓ Deterministic results
```

---

### 2. Portability

**Definition:**
> "Can run on **different machines without changes** (CI)"

**Requirements:**
- Do not depend on specific machine resources
- No hardcoded paths
- No environment-specific configurations
- Works on developer machines and CI servers

**Anti-patterns:**
```
❌ Reading from "C:\Users\John\data.txt"
❌ Expecting specific database port
❌ Hardcoded localhost URLs
```

**Good Practice:**
```
✓ Use relative paths
✓ Configuration via environment variables
✓ Mock external resources
✓ Containerized test environments
```

---

### 3. Understandability

**Definition:**
> "The **purpose of the test is clear**"

**What This Means:**
- Test name describes what it tests
- Clear arrange-act-assert structure
- Comments explain "why" not "what"
- Easy for new team members to understand

**Example:**
```
✓ test_user_login_with_invalid_password_returns_401()
❌ test1()
```

---

### 4. Reliability

**Definition:**
> "The ability to **expect it to perform its function reliably**"

**Characteristics:**
- Consistent results
- No flaky tests
- Not dependent on timing
- Not dependent on execution order
- No random failures

**Flaky Test Problems:**
- Erodes trust in test suite
- Developers ignore failures
- CI becomes unreliable
- Wastes debugging time

---

# Test Pyramid and Strategies

## The Test Pyramid

### The Classic Pyramid

**Visual Description:** A pyramid with three layers, wider at bottom, narrower at top.

```
        /\
       /  \  UI/Acceptance/Functional Tests
      /    \
     /------\
    /        \ Integration/Service Tests
   /          \
  /------------\
 /              \ Unit Tests
/________________\
```

---

### The Principle

> "Due to its simplicity the **essence of the test pyramid** serves as a **good rule of thumb**"

**Source:** Martin Fowler: The Practical Test Pyramid

---

### Layer Breakdown

**Unit Tests (Bottom - Most):**
- **Quantity:** Many (70-80% of tests)
- **Speed:** Very fast (milliseconds)
- **Scope:** Single unit (function/class)
- **Cost:** Low to write and maintain
- **Confidence:** Low (isolated units)

**Integration Tests (Middle - Some):**
- **Quantity:** Moderate (15-20% of tests)
- **Speed:** Medium (seconds)
- **Scope:** Multiple components together
- **Cost:** Medium to write and maintain
- **Confidence:** Medium (real interactions)

**UI/Acceptance/Functional Tests (Top - Few):**
- **Quantity:** Few (5-10% of tests)
- **Speed:** Slow (minutes)
- **Scope:** Entire system end-to-end
- **Cost:** High to write and maintain
- **Confidence:** High (real user scenarios)

---

### The Rationale

**Why Pyramid Shape:**

1. **Speed Matters:**
   - Fast feedback loop essential
   - Unit tests run in seconds
   - E2E tests run in minutes/hours
   - More unit tests = faster overall

2. **Maintenance Cost:**
   - Unit tests easy to maintain
   - E2E tests brittle and complex
   - Minimize high-maintenance tests

3. **Debugging:**
   - Unit test failure = precise location
   - E2E test failure = anywhere in system
   - Faster debugging with unit tests

4. **ROI:**
   - Unit tests: High return, low cost
   - E2E tests: High cost, high value
   - Balance the investment

---

## Alternative Models

### Mauricio Aniche's Version

**Visual Description:** The slides reference "Another version of pyramid, by Mauricio Aniche" showing "The four types of tests"

**Four Layers:**
1. Unit Tests (base)
2. Integration Tests
3. System Tests
4. Manual Tests (top)

**Key Addition:**
- Acknowledges **manual testing** still has a place
- At the very top (minimal)
- For exploratory testing, UX validation

---

### Kent C. Dodds: The Test Trophy

**Visual Description:** Trophy shape - wider in middle than traditional pyramid

```
      ___
     /   \
    |     | E2E Tests
    |     |
   /       \ Integration Tests (widest)
  |         |
  |         |
  |_________|
     |   |  Unit Tests
     |___|  Static Tests
```

---

### The Trophy Philosophy

**Key Difference:**
> "Mostly **integration tests**, not mostly unit tests"

**Rationale:**
- Integration tests provide **best ROI**
- Test how components work **together**
- Catch more real bugs
- Still reasonably fast
- Not as brittle as E2E

**Trophy Distribution:**
- Static: Some
- Unit: Some
- **Integration: Most** ← Key difference
- E2E: Few

---

### Pyramid vs Trophy Debate

**Test Pyramid (Traditional):**
- Focus on unit tests
- Minimizes slow tests
- Precise isolation
- Fast feedback

**Test Trophy (Modern):**
- Focus on integration tests
- Better confidence
- Tests real interactions
- Balanced approach

**Reality:**
> Both valid. Choose based on:
- Your application architecture
- Your team's strengths
- Your specific risks
- Your development speed needs

---

### The Anti-Pattern: Ice Cream Cone

**Visual Description:** Slides mention "No test ice cream please"

**Ice Cream Cone Shape:**
```
  _____
 /     \ Manual Tests (too many)
|       |
|       | E2E Tests (too many)
|_______|
   | |   Integration (some)
   | |   Unit Tests (too few)
   |_|
```

**Problems:**
- Inverted pyramid
- Too many slow, expensive tests
- Too few fast, cheap tests
- **Very bad:** Slow CI, brittle tests, hard to maintain

**Avoid This!**

---

# Types of Testing

## Static Testing

### What is Static Testing?

**Definition:**
> "Catch errors **as code is written**. Assistance in conveying the programmer's thoughts into code."

**Key Characteristic:**
- **No code execution**
- Analysis of source code
- Compile-time checks
- Before runtime

---

### Three Types of Static Testing Tools

**1. Linter**
- Catches code quality issues
- Duplicate keys
- Unused variables
- Style violations
- Example: **ESLint** (JavaScript)

**2. Type Checker**
- Catches type errors
- Type mismatches
- Missing types
- Example: **TypeScript**

**3. Formatter**
- Enforces code style
- Consistent formatting
- Not error detection
- Example: **Prettier**

---

### Best Practice

> "Good to set up as a **pre-commit hook**."

**Why:**
- Catches errors before commit
- Prevents bad code entering repository
- Immediate feedback to developer
- No CI failures for simple issues

---

## Static Testing Examples

### TypeScript Example (Before)

```typescript
export function fibonacci(n) {
  if (n <= 1) {
    return 0;
  } else if (n === 2) {
    return 1;
  }
  return fibonacci(n - 1) + fibonacci(n - 2);
}
```

**Problem:**
> "`noImplicitAny` – will make this function return error, due to the type checks."

**What's Wrong:**
- Parameter `n` has no type (implicit `any`)
- Return type not declared
- TypeScript can't validate usage

---

### TypeScript Example (After)

```typescript
export function fibonacci(n: number): number {
  if (n <= 1) {
    return 0;
  } else if (n === 2) {
    return 1;
  }
  return fibonacci(n - 1) + fibonacci(n - 2);
}
```

**What Fixed:**
> "Static testing detects issues such as **missing types** (e.g., implicit any in TypeScript) **at compile time**, before the code is executed, **improving reliability** and **reducing runtime errors**."

**Benefits:**
- Compile-time validation ✓
- IDE autocomplete ✓
- Catches type errors early ✓
- Self-documenting code ✓

---

### Java Example: Raw Types (Wrong)

**The Problem:**
> "Don't use **raw types**! Legacy construct, doesn't check types. Add `<>` to constructors."

**Bad Code:**
```java
Pair<String, Integer> pair1 = new Pair("score", 5);
Pair<String, Integer> pair2 = new Pair("score", "five"); // Compiles. Oops!
```

**What's Wrong:**
- `new Pair(...)` is raw type (no `<>`)
- No type checking
- Second line compiles but is wrong!
- Runtime error waiting to happen

---

### Java Example: Raw Types (Correct)

**Good Code:**
```java
Pair<String, Integer> pair1 = new Pair<>("score", 5);
Pair<String, Integer> pair2 = new Pair<>("score", "five"); // Does not compile
```

**Error Message:**
```
Type mismatch: cannot convert from Pair<String, String>
to Pair<String, Integer>
```

**What Fixed:**
- Added `<>` to constructor (diamond operator)
- Compiler now validates types
- Error caught at compile time ✓

---

### Java Example: Wildcards

**The Problem:**
```java
List list1 = Arrays.asList("one", "two", "five");
List<Integer> list2 = list1; // Compiles. Oops!
```

**The Fix:**
> "If don't care [about type], use **wildcard `?`** in declarations"

```java
List<?> list1 = Arrays.asList("one", "two", "five");
List<Integer> list2 = list1; // Type mismatch error
```

**Error Message:**
```
Type mismatch: cannot convert from List<capture#1-of ?>
to List<Integer>
```

---

### Python Example: Type Annotations

**Context:**
> "You can add **type annotations** (since Python 3.5). Use a type verification tool (**mypy**)."

**Example Code:**
```python
from typing import Literal

def process(tokenType: Literal["website", "page"]):
    if (tokenType == "website"):
        processWebsite()
    else:
        processPge()  # Typo! Should be processPage()
```

**What Type Checker Catches:**
- Typo in function name `processPge()`
- Type annotations enable validation
- `mypy` would catch this error

---

## Static Testing: Limitations and Trade-offs

### Limitations

**1. Limited to Type System:**
> "Limited to the **type system**"

- Can't describe **complex semantic contracts**
- Example: Can't verify business logic
- Example: Can't check "email must be valid format"

**2. Assumptions Could Be Wrong:**
> "Assumptions could be wrong"

- Types describe interface, not behavior
- Function might accept `number` but expect positive
- Type system can't encode all constraints

---

### Trade-offs

**1. Some Lints Not Useful:**
> "Some lints are not useful"

- Can be **opted out**
- Strike the **right balance**
- Too strict = productivity hit
- Too loose = miss errors

**2. Could Hinder Quick Prototyping:**
> "Could hinder quick prototyping"

- Example: TypeScript is still quite flexible
- Can use `any` temporarily
- Gradually add types

**3. Transpilation Sometimes Required:**
> "Transpilation step is sometimes required"

- TypeScript → JavaScript
- Adds build complexity
- Slower development cycle

---

## Unit Testing

### Definition

> "Testing **software units in isolation** (methods, classes, or small logical groups)."

**Purpose:**
> "Verify the behavior of **independent, isolated components**."

---

### What is a "Unit"?

**According to Roy Osherove (2009):**
> "A unit test is an **automated piece of code** that invokes a **unit of work** in the system... to achieve **one single logical purpose** that can be verified."

**Key Points:**
- **Automated** - Runs without human intervention
- **Unit of work** - Small, focused piece
- **Single logical purpose** - One thing to verify
- **Verifiable** - Can assert pass/fail

**Examples of "Units":**
- A single function/method
- A single class
- A small group of related classes
- A module or package (if cohesive)

---

### Advantages

**1. Great Case Coverage:**
- Can test many scenarios easily
- Edge cases
- Error conditions
- All code paths

**2. Faster Root Cause Analysis:**
- Failure points to exact location
- Precise debugging
- Clear what broke

**3. Fast and Simple:**
- Run in milliseconds
- Quick feedback
- Easy to write

---

### Handling Dependencies

**The Challenge:**
> "Units should **avoid reliance on external systems** (databases, services)."

**Why:**
- External systems slow down tests
- External systems unreliable in tests
- External systems complicate setup
- Want to test unit in isolation

**The Solution:**
> "If unavoidable, use **stubs/mocks** to simulate dependencies and keep tests isolated."

---

### Mocks and Stubs Explained

**Stub:**
- Provides predetermined responses
- Simulates dependency behavior
- Returns fake data
- No verification

**Mock:**
- Like stub, but also verifies interactions
- Checks if methods called
- Validates parameters passed
- Asserts expectations met

**Example:**
```javascript
// Stub
const fakeDatabase = {
  getUser: () => ({ id: 1, name: "Test User" })
};

// Mock
const mockDatabase = {
  getUser: jest.fn(() => ({ id: 1, name: "Test User" }))
};
// Later: expect(mockDatabase.getUser).toHaveBeenCalled();
```

---

### Limitations

**Problem 1:**
> "Does not answer whether components **work well together**."

**Reality:**
- Units might work individually
- But fail when integrated
- Need integration tests too

---

**Problem 2:**
> "Expectations might be **unaligned with reality**"

**Example:**
- Mock database returns data in format X
- Real database returns data in format Y
- Unit tests pass, production fails

---

**Problem 3:**
> "Not always feasible"

**When Difficult:**

**Use of global context:**
- Shared state between tests
- Hard to isolate

**Tightly dependent on other components:**
- Can't easily separate
- Need integration test instead

**Writing test doubles (mocks/stubs):**
- Complex to create
- Maintenance burden
- May not match reality

---

### Visual Reference

**Visual Description:** The slides include a video reference (`WsgwFeb-_YnV_tzO.mp4`) likely demonstrating unit testing concepts or test doubles.

---

## Integration Testing

### Definition

> "Tests **interactions between multiple components**."

**Focus:**
> "Whether components **communicate correctly** (e.g., DAO ↔ database)."

---

### Characteristics

**More Realistic:**
> "More realistic than unit tests but still not a full system test."

**Validation:**
> "Validates **contracts** between our code and external systems (databases, web services, files, etc.)."

**Example:**
> "Submitting **SQL queries to a real database** instead of mocking it."

---

### Advantages

**1. Ensures Correctness of Communication:**
- Real API calls
- Actual database queries
- True file I/O
- Network operations

**2. Targets Critical Integration Points:**
- Without requiring full system execution
- Focused on specific integrations
- Faster than full E2E

---

### Disadvantages

**1. Harder to Write:**
> "Harder to write than unit tests (requires **setup, teardown, and data preparation**)."

**Setup Complexity:**
- Start database
- Create test data
- Configure services
- Network setup

**Teardown Complexity:**
- Clean up data
- Reset state
- Stop services
- Restore environment

---

**2. Slower Execution:**
> "Slower execution due to **reliance on external components**."

**Why Slow:**
- Database queries take time
- Network calls have latency
- File I/O is slow
- Service startup delays

---

### Scope

**What's Involved:**
> "Tests involve:"

**1. Our component under test:**
- The code we wrote
- Being validated

**2. External component it integrates with:**
- Database
- Web service
- File system
- Message queue
- Third-party API

---

### Trade-offs

**Visual Description:** The slides show a trade-off diagram.

**The Balance:**

**Coverage/Focus:**
- Better coverage than unit tests
- More realistic scenarios
- Catches integration bugs

**VS**

**Feasibility:**
- Slower than unit tests
- More complex setup
- Harder to maintain

**Mocking Still Important:**
> "Mocking may still be important"

**Why:**
- Don't want to call real third-party APIs in tests
- Don't want to send real emails
- Don't want to charge real credit cards
- Mock the "outside world," test your integration

---

## System Testing

### Definition

> "Runs the **entire software system** (databases, frontend, backend, etc.) as a **whole**."

**Approach:**
> "**Black-box approach**: focus on input/output, not internal implementation."

---

### Characteristics

**What It Tests:**
- Complete system
- All components together
- Real environment (as close as possible)
- User perspective

**How It Works:**
- Input provided to system
- System processes
- Output verified
- Internal implementation ignored

---

### Advantages

**1. Realistic:**
> "Simulates how **end users interact** (web page, form, API call)."

**Real Scenarios:**
- Actual user workflows
- Complete features
- Integrated functionality

**2. Higher Confidence:**
> "Builds **higher confidence** in overall system behavior."

**Why:**
- Tests what users actually experience
- Validates entire stack
- Catches integration issues

---

### Disadvantages

**1. Slow:**
> "Starting **full system, containers, and services takes time**."

**Time Costs:**
- Application startup
- Database initialization
- Service dependencies
- Container orchestration

---

**2. Complex Setup:**
> "**Databases, authentication, and test data preparation** required."

**Setup Challenges:**
- Multiple services to configure
- Authentication/authorization systems
- Test data generation
- Environment configuration
- Network setup

---

**3. Flaky Tests:**
> "**Timing/network variations** may cause inconsistent results."

**Causes of Flakiness:**
- Network latency variations
- Timing issues (race conditions)
- External service availability
- Resource contention
- Non-deterministic behavior

**Impact:**
- Tests fail randomly
- CI becomes unreliable
- Developers lose trust
- Debugging nightmares

---

### Visual Reference

**Visual Description:** The slides show a diagram illustrating system testing with all components (slide 27).

---

## Server Mocking/Stubbing

### Concept

> "**Surrounding the tested component with stubs**"

**Purpose:**
- Test component without real external services
- Simulate backend responses
- Control test scenarios

---

### Benefits

**1. Better Isolation:**
- Component tested independently
- Control all inputs
- Predictable behavior

**2. Less Components to Set Up:**
- No real backend needed
- No database setup
- No third-party services

**3. No External Resources:**
- Fast tests
- No network calls
- No service dependencies
- Works offline

---

### JavaScript Tools

**1. msw (Mock Service Worker):**
> "A modern REST/GraphQL API mocking tool"

**Features:**
- Intercepts network requests
- Works in browser and Node.js
- Realistic API mocking

**2. nock:**
> "An HTTP server mock"

**Features:**
- Mocks HTTP requests
- Node.js specific
- Request/response matching

---

### Java Tools

**WireMock & others:**
- HTTP mock server
- Records and replays requests
- Flexible matching
- Fault simulation

---

## End-to-End (E2E) Testing

### Goal

> "Ensure the **full application flow** behaves as expected in **real usage scenarios**."

---

### Characteristics

**1. User Perspective:**
> "Tests the system from the **user's perspective**, end-to-end."

**2. Complete Validation:**
> "Verifies that **frontend, backend, database, and external services** work together correctly."

**What It Tests:**
- User workflows
- Complete features
- Cross-system integration
- Real user scenarios

---

## E2E Testing Tools

### Selenium

**What It Is:**
> "API to a **browser driver** (chromedriver.exe) / **WebDriver Protocol**"

**Characteristics:**
> "Not a test framework (add test framework, driver, ...)"

**API Complexity:**
> "Complicated API"

**Why Complicated:**
- Each operation requires wiring data to/from driver
- Low-level browser control
- Lots of boilerplate
- Manual waits and synchronization

**Used By:**
- Several frameworks
- Example: Nightwatch.js

---

### Cypress

**What It Is:**
> "**Modern solution** to web page E2E testing, **all-in-one**"

---

#### Advantages

**1. Easier API and Tooling:**
- Intuitive API
- Great developer experience
- Time-travel debugging
- Automatic screenshots/videos

**2. Runs Directly on Browser:**
- Injects in the DOM
- Direct access to application
- No network hop
- Faster execution

---

#### Disadvantages

**1. Less Browser Support:**
- Chrome, Firefox, Edge
- No Safari (initially)
- Limited compared to Selenium

**2. No Multi-Window:**
- Can't test across windows/tabs
- Single window limitation
- Some scenarios impossible

---

### Playwright

**Modern E2E Testing Tool:**
- By Microsoft
- Multi-browser support (Chrome, Firefox, Safari, Edge)
- Multi-language support (JavaScript, Python, Java, C#)
- Auto-waiting
- Parallel execution
- Mobile testing
- Modern API similar to Cypress but more powerful

---

### Tool Comparison

| Feature | Selenium | Cypress | Playwright |
|---------|----------|---------|------------|
| **Browser Support** | Extensive | Limited | Extensive |
| **Speed** | Slower | Fast | Fast |
| **API Complexity** | High | Low | Low |
| **Setup** | Complex | Simple | Simple |
| **Multi-window** | Yes | No | Yes |
| **Mobile** | Yes | Limited | Yes |
| **Debugging** | Basic | Excellent | Excellent |

---

# Test Methodology

## Write Tests: The Approach

### When to Introduce Tests

**1. Introduce Tests Alongside Changes:**
> "Introduce tests **alongside changes**"

**Note:**
> "Refactor may be required"

**Why:**
- Legacy code might not be testable
- Need to refactor for testability
- Gradual improvement

---

### When to Write New Tests

**2. Write New Tests On:**

**New Implementations:**
> "New implementations (**design ahead**)"

- **Shift-left testing!**
- Write tests first (TDD)
- Design for testability
- Tests guide design

---

**Critical Components:**
> "Critical components"

- High-risk areas
- Core business logic
- Security-sensitive code
- High-visibility features

---

### The 100% Coverage Myth

**3. Don't Strive for 100% Test Coverage:**
> "Don't strive for **100% test coverage**"

**Why Not 100%:**
- Diminishing returns
- Some code not worth testing (getters/setters)
- 100% coverage ≠ 100% quality
- Better to test critical paths well

**Better Goal:**
- High coverage on critical code
- Meaningful tests, not just coverage
- Focus on value, not metrics

---

## Wrap Up: Test Strategy

### Visual Description

**The slides show two diagrams:**

**1. Test Pyramid: Mostly Unit**
```
     /\
    /  \ Few E2E
   /----\
  /      \ Some Integration
 /________\
/          \ Many Unit Tests
```

> "Test Pyramid: **Mostly unit**"

---

**2. Test Trophy: Mostly Integration**
```
    ___
   /   \ Few E2E
  |     |
 /       \ Many Integration (widest)
|         |
|_________|
    |_|    Some Unit, Some Static
```

> "Test Trophy: **Mostly integration**"

---

**3. Anti-Pattern: No Test Ice Cream**
```
  _____
 /     \ Too many E2E (slow, brittle)
|       |
|_______|
   | |   Too few fast tests
   |_|
```

> "**No test ice cream please**"

**Why Bad:**
- Inverted pyramid
- Slow test suite
- Brittle tests
- Expensive to maintain

---

# Advanced Testing Types

## Performance Testing

### Definition

> "Validates **system behavior under stress, peak traffic**"

---

### Purpose

**1. Identify Bottlenecks:**
- CPU bottlenecks
- Database bottlenecks
- Network bottlenecks
- Lock contention

**2. Validate Performance:**
- Response times under load
- Throughput capacity
- Scalability limits
- Resource usage

---

### Integration with CI

> "Often **integrated into CI** for regression/performance budgets"

**Why in CI:**
- Prevent performance regressions
- Enforce performance budgets
- Continuous validation
- Early detection

**Performance Budgets:**
- Max response time: 200ms
- Max memory: 512MB
- Min throughput: 1000 req/s

---

### Tools

**Locust:**
- Python-based
- Distributed load testing
- User-friendly

**k6:**
- JavaScript-based
- Developer-friendly
- CLI and automation

**Gatling:**
- Scala-based
- Advanced reporting
- High performance

**JMeter:**
- Java-based
- GUI and CLI
- Widely used

---

## Chaos Testing

### Definition

> "Tests **fault tolerance** and **self-healing capabilities**"

---

### How It Works

> "Introduces **controlled failure** on infra/services"

**Examples:**
- Kill random pods/containers
- Introduce network latency
- Cause database failures
- Simulate CPU/memory pressure
- Partition network

---

### Where It's Common

> "Common in **cloud-native** and **microservices architectures**"

**Why:**
- Distributed systems complex
- Failures inevitable
- Need resilience
- Validate recovery

---

### Tools

**Chaos Mesh:**
- Kubernetes-native
- Multiple fault types
- Easy to use

**Litmus:**
- Cloud-native chaos
- CNCF project
- Extensive scenarios

**Gremlin:**
- Commercial solution
- Comprehensive platform
- Enterprise features

---

## Security Testing

### Definition

> "Checks **vulnerabilities, misconfigurations, and broken auth**"

---

### Types of Security Testing

**SAST (Static Application Security Testing):**
- Analyzes source code
- Finds vulnerabilities in code
- No execution required

**DAST (Dynamic Application Security Testing):**
- Tests running application
- Black-box testing
- Runtime vulnerabilities

**Dependency Scanning:**
- Checks third-party libraries
- Known vulnerabilities (CVEs)
- License compliance

**Secrets Detection:**
- Finds hardcoded secrets
- API keys in code
- Passwords in repos

---

### Integration in CI

> "Integrated into CI **before deployment gates / release**"

**Why:**
- Block vulnerable code
- Prevent security regressions
- Shift-left security
- Compliance requirements

---

### Tools

**OWASP ZAP:**
- Web app scanner
- Open source
- Comprehensive

**Trivy:**
- Container scanner
- Fast and easy
- Multiple targets

**Snyk:**
- Dependency scanning
- Commercial/free tiers
- Developer-friendly

**GitLab Security:**
- Integrated platform
- Multiple scan types
- CI/CD native

---

# Integration with CI/CD

## Where Does Each Type of Test Fit?

### Visual Overview

**Visual Description:** The slides show a CI/CD pipeline diagram with test stages.

**Typical Pipeline:**
```
Code Commit → Static Testing → Unit Testing → Integration Testing → E2E Testing → Deploy
```

---

### Pipeline Stages in Detail

**Visual Description (Slide 39):** Shows detailed pipeline with annotations:

```
┌─────────────┐
│ Code Commit │
└──────┬──────┘
       ↓
┌─────────────────┐
│ Static Testing  │ ← Linting, Type Checking
└──────┬──────────┘
       ↓
┌─────────────────┐
│ Unit Testing    │ ← Fast, isolated tests
└──────┬──────────┘
       ↓
┌─────────────────┐
│ Integration     │ ← Component interactions
│ Testing         │
└──────┬──────────┘
       ↓
┌─────────────────┐
│ End-to-End      │ ← Full system tests
│ Testing         │
└──────┬──────────┘
       ↓
┌─────────────────┐
│ Deploy          │
└─────────────────┘
```

---

### Important Note

> "Note: this is **where it should fit**, but it **may vary** from team practices / products / etc."

**Reality:**
- Teams adapt to their needs
- Product type matters
- Company culture influences
- No one-size-fits-all

---

### Test Failure Strategy

**Critical Rule:**
> "**If tests fail, rollback release.**"

**Visual Description (Slide 42):** Updated pipeline showing rollback:

```
┌─────────────────┐
│ Static Testing  │ ──✗─→ Fail → Stop
└─────────────────┘
┌─────────────────┐
│ Unit Testing    │ ──✗─→ Fail → Stop
└─────────────────┘
┌─────────────────┐
│ Integration     │ ──✗─→ Fail → Stop
│ Testing         │
└─────────────────┘
┌─────────────────┐
│ End-to-End      │ ──✗─→ Fail → Rollback
│ Testing         │
└─────────────────┘
```

**Why:**
- Don't deploy broken code
- Maintain production quality
- Fast feedback to developers
- Prevent cascading failures

---

# Testing in Production

## Why Test in Production?

### The Reality

Traditional approach:
- Develop → Test in staging → Deploy to production
- Assume staging = production
- Hope nothing breaks

**Problem:** Staging ≠ Production

---

### Benefits of Testing in Production

**1. Higher Confidence:**
> "**Real environment** reveals issues missed in staging; faster, safer releases."

**Why:**
- Production is the only true environment
- Staging approximations always wrong
- Real issues only appear in prod

---

**2. Accuracy of Reality:**
> "True **data volume and shape**, historical quirks, and **real request patterns** emerge only in prod."

**Data Differences:**
- Production data: Years of accumulation, edge cases, real user behavior
- Staging data: Clean, synthetic, limited
- Historical quirks: Only in production
- Data volume: Cannot replicate in staging

---

**3. Traffic Realism:**
> "**Incoming and outgoing traffic**, scaling behavior, and instance counts match **real usage**."

**Traffic Patterns:**
- User behavior unpredictable
- Peak loads
- Geographic distribution
- Attack patterns

---

**4. Config and Network Fidelity:**
> "Auth, pools, caches, CDNs, proxies, and **third-party contracts** differ from staging."

**Staging vs Production:**
- Different auth providers
- Different connection pools
- Different CDN configurations
- Different third-party APIs (sandbox vs prod)
- Different network topology

---

**5. Version Alignment:**
> "Validates against the **actual versions** of internal and third-party services."

**Version Drift:**
- Production services updated independently
- Staging often outdated
- Dependency version mismatches

---

**6. Lower Cost and Better Hygiene:**
> "Less staging load-testing, **fewer environments**, avoids risky prod-data copies."

**Cost Savings:**
- Don't need full production clone
- Smaller staging environment
- Less infrastructure
- No sensitive data copies (compliance)

---

## How to Test in Production (Safely)?

### 1. Feature Toggles

> "**Precise, easy activation** for exploratory tests via query params, headers, cookies, user IDs, or roles."

**Techniques:**
```
?debug=true                    (Query parameter)
X-Feature-Flag: new-checkout   (Header)
cookie: beta_user=1            (Cookie)
userId: 12345                  (User ID check)
role: admin                    (Role-based)
```

**Benefits:**
- Enable feature for specific users
- Test in real environment
- No deployment needed
- Instant on/off

---

### 2. Test Data Strategy

> "Create and **flag synthetic data**; hide by default; control visibility with the same toggle mechanisms."

**Approach:**
- Mark test data clearly
- `is_test_data: true` flag
- Hide from analytics
- Hide from real users
- Show only to testers

**Example:**
```json
{
  "user_id": "test_user_12345",
  "is_test_data": true,
  "order": {...}
}
```

---

### 3. Prevent Leakage

> "Define **API policy** for test data (local only, opt-in, or always flagged) and **communicate contracts**."

**Policies:**

**Local Only:**
- Test data never leaves test environment
- Strictly local

**Opt-in:**
- Test data visible only if requested
- `?include_test_data=true`

**Always Flagged:**
- Test data always marked
- Clients filter out
- Clear contract

---

### 4. Debugging in Production

> "Prefer enabling **source maps** (or controlled hosting) to make front-end issues diagnosable."

**Source Maps:**
- Map minified code to source
- Easier debugging
- Security consideration: limit access

**Alternatives:**
- Detailed error logging
- Session replay tools
- Error tracking (Sentry, etc.)

---

### 5. Lean Preprod

> "Keep **minimal infra** for automated checks; many teams **reduce or retire staging** as maturity grows."

**Evolution:**
- Start: Large staging environment
- Mature: Small staging, test in prod
- Advanced: No staging, only prod with feature toggles

**Automated Checks:**
- Smoke tests in staging
- Main testing in production
- Feature toggles for safety

---

### 6. Maturity Goal

> "With **solid safety practices**, production testing becomes **routine** in continuous delivery."

**Signs of Maturity:**
- Feature toggles everywhere
- Canary deployments
- Comprehensive monitoring
- Fast rollback
- Testing in production is normal, not scary

---

# Practical Implementation

## Allure Report

### What is Allure?

> "A **lightweight test reporting platform** that aggregates results from **multiple test frameworks** into a **rich, interactive dashboard**."

---

### Supported Frameworks

**Examples:**
- pytest (Python)
- JUnit (Java)
- Cypress (JavaScript)
- Playwright (JavaScript/TypeScript)
- And many more

**Key Feature:**
- Unified reporting across different tools
- Consistent interface
- Aggregated view

---

### Where to Get It

> "Available here https://allurereport.org/"

---

### Sample Practical Workflow

**Step 1:** Tests run
- pytest/JUnit/Playwright/etc.
- Normal test execution

**Step 2:** Allure collects raw results
- Test results written to directory
- JSON format
- Detailed information

**Step 3:** CI/CD generates HTML dashboard
- `allure generate` command
- Converts JSON to HTML
- Interactive report

**Step 4:** Report is published
- As artifact
- Or hosted statically
- Accessible to team

---

### Benefits

- **Visual reports** - Easy to understand
- **Historical trends** - Track over time
- **Screenshots/videos** - Failure investigation
- **Categorization** - Organize by feature
- **Integration** - Works with existing tools

---

## Integrate Tests in CI/CD

### Example: GitHub Actions for Java

```yaml
steps:
  - uses: actions/checkout@v5
  - uses: actions/setup-java@v4
    with:
      java-version: '17'
      distribution: 'temurin'
  - name: Run the Maven verify phase
    run: mvn --batch-mode --update-snapshots verify
```

---

### What This Does

**Step 1: Checkout**
- Gets code from repository
- `actions/checkout@v5`

**Step 2: Setup Java**
- Installs Java 17
- Temurin distribution (Eclipse Adoptium)
- `actions/setup-java@v4`

**Step 3: Run Tests**
- `mvn verify` command
- Runs all tests
- `--batch-mode`: No interactive prompts
- `--update-snapshots`: Refresh dependencies

---

### Maven Verify Phase

**What `mvn verify` does:**
1. Compile code
2. Run unit tests
3. Run integration tests
4. Verify package
5. Generate reports

**If any test fails:**
- Build fails
- CI fails
- Deployment blocked

---

## Practical Guide: Your Project

### Lab Exercise

**Learning Resource:**
> "Learn from this tutorial (Building and testing your code): https://docs.github.com/en/actions/tutorials/build-and-test-code/java-with-maven"

---

### Project Requirements

**1. Implement Different Test Types:**
> "Make sure that you implement some **different type of tests** in your project (**one of each at least**)"

**Minimum:**
- Static tests (linting, type checking)
- Unit tests
- Integration tests
- E2E tests (or system tests)

---

**2. CI/CD Integration:**
> "They should be **integrated in your CI-CD pipeline**"

**Requirements:**
- All test types in pipeline
- Run automatically on commits
- Block deployment on failure

---

**3. Test Before Deployment:**
> "You need to make sure that the **tests will run before any deployment**, in **different steps**."

**Pipeline Structure:**
```
Commit → Static → Unit → Integration → E2E → Deploy
```

**Important:**
- Different stages
- Fail fast (stop on first failure)
- Clear feedback

---

**4. Environment Simulation:**
> "It is **acceptable simulate stage / production environment**, as the same."

**For Learning:**
- Can use same environment for both
- Focus on pipeline structure
- Real projects: separate environments

---

**5. Allure Reports:**
> "**Allure Reports should be integrated**"

**Requirements:**
- Generate Allure reports
- Publish in CI
- Make accessible to team

---

**6. Continuous Improvement:**
> "For the **next iterations**, you need to make sure that this **pipeline is updated**."

**Evolution:**
- Add more tests over time
- Improve test quality
- Optimize pipeline
- Learn and iterate

---

**7. Advanced Feature:**
> "Other possibilities: **regressions should create new tickets/github issues**"

**Automation:**
- Failed test → Auto-create GitHub issue
- Track regressions
- Automated follow-up
- Better visibility

---

# Study Tips and Exam Preparation

## Critical Concepts to Master

### Testing Fundamentals

**1. Why Testing Matters:**
- Mars Climate Orbiter case study
- Problems without tests
- Economic reality (cost of change)
- Exit criteria concept

**2. Properties of Good Tests:**
- Testability
- Portability
- Understandability
- Reliability

**3. Test Pyramid vs Trophy:**
- Know both models
- Understand rationale for each
- Advantages/disadvantages
- When to use which
- Anti-pattern: Ice cream cone

---

### Testing Types (Know All Details)

**1. Static Testing:**
- Three types: Linter, Type Checker, Formatter
- Examples in TypeScript, Java, Python
- Limitations and trade-offs
- Pre-commit hooks

**2. Unit Testing:**
- Definition (Roy Osherove)
- Mocks vs stubs
- Advantages and limitations
- When not feasible

**3. Integration Testing:**
- Definition and scope
- Advantages and disadvantages
- Setup complexity
- Trade-offs

**4. System Testing:**
- Black-box approach
- Advantages (realistic, confidence)
- Disadvantages (slow, complex, flaky)

**5. E2E Testing:**
- User perspective
- Tools: Selenium, Cypress, Playwright
- Tool comparison

---

### Advanced Testing

**1. Performance Testing:**
- Purpose (bottlenecks, stress)
- CI integration
- Tools: Locust, k6, Gatling, JMeter

**2. Chaos Testing:**
- Fault tolerance testing
- Cloud-native importance
- Tools: Chaos Mesh, Litmus, Gremlin

**3. Security Testing:**
- SAST, DAST, dependency scanning
- CI integration before deployment
- Tools: OWASP ZAP, Trivy, Snyk

---

### CI/CD Integration

**1. Pipeline Structure:**
- Test stages order
- Static → Unit → Integration → E2E → Deploy
- Fail fast principle
- Rollback on failure

**2. Testing in Production:**
- Six benefits (know all)
- Six safety techniques (know all)
- Feature toggles critical
- Test data strategy

---

### Practical Skills

**1. Allure Reports:**
- Purpose and benefits
- Workflow
- Integration with CI

**2. GitHub Actions:**
- Java/Maven example
- Test integration
- Verify phase

---

## Key Numbers and Terms to Remember

### Test Distribution

**Test Pyramid:**
- 70-80% Unit tests
- 15-20% Integration tests
- 5-10% E2E/UI tests

**Test Trophy:**
- Most: Integration tests
- Some: Unit tests
- Some: Static tests
- Few: E2E tests

---

### Test Properties (Four)
1. Testability
2. Portability
3. Understandability
4. Reliability

---

### Static Testing Tools (Three)
1. Linter (ESLint)
2. Type Checker (TypeScript)
3. Formatter (Prettier)

---

### E2E Tools (Three)
1. Selenium (WebDriver, complex)
2. Cypress (Modern, easier, limited browsers)
3. Playwright (Modern, comprehensive)

---

### Advanced Testing Types (Three)
1. Performance Testing
2. Chaos Testing
3. Security Testing

---

### Security Testing Types (Four)
1. SAST (Static)
2. DAST (Dynamic)
3. Dependency Scanning
4. Secrets Detection

---

### Testing in Production Benefits (Six)
1. Higher confidence
2. Accuracy of reality
3. Traffic realism
4. Config and network fidelity
5. Version alignment
6. Lower cost and better hygiene

---

### Testing in Production Safety (Six)
1. Feature toggles
2. Test data strategy
3. Prevent leakage
4. Debugging in prod
5. Lean preprod
6. Maturity goal

---

## Common Exam Question Types

### Comparison Questions
- "Compare Test Pyramid vs Test Trophy"
- "Unit tests vs Integration tests - advantages/disadvantages"
- "Selenium vs Cypress vs Playwright"
- "SAST vs DAST"
- "Mocks vs Stubs"

### Scenario Questions
- "You need to test database integration. Which test type?"
- "User reports bug in production. How to test in production safely?"
- "CI is slow. How to optimize test suite?"
- "Which tests should run in which CI stage?"

### Conceptual Questions
- "Why is exhaustive testing impossible?"
- "What are exit criteria and why important?"
- "Explain shift-left testing"
- "Why test in production?"

### Practical Questions
- "Write a GitHub Actions workflow that runs tests"
- "How to integrate Allure Reports?"
- "Design a CI/CD pipeline with all test types"
- "How to implement feature toggles for production testing?"

---

## Important Distinctions

### Test Types by Scope
- **Unit**: Single component, isolated
- **Integration**: Multiple components, real interactions
- **System**: Entire system, black-box
- **E2E**: User perspective, complete workflow

### Test Types by Execution
- **Static**: No execution, compile-time
- **Dynamic**: Execution required, runtime

### Test Data
- **Real Data**: Production data (risky in tests)
- **Synthetic Data**: Generated for tests (safe)
- **Test Data**: Flagged synthetic data for prod testing

### Testing Environments
- **Staging**: Pre-production environment
- **Production**: Real user environment
- **Local**: Developer machine

---

## Real-World Application

### Mars Climate Orbiter Lessons

**What Happened:**
- $327 million loss
- Unit mismatch (metric vs English)
- No integration testing

**What Would Have Prevented:**
- Unit tests with type checking
- Integration tests between systems
- Contract tests specifying units
- Code review

**Exam Tip:**
Know this story - demonstrates why testing matters!

---

### Testing Strategy for Your Project

**Practical Implementation:**

**1. Start with Static Testing:**
- Set up linter (ESLint/Checkstyle)
- Add type checking (TypeScript/Java generics)
- Pre-commit hooks

**2. Add Unit Tests:**
- Test business logic
- Mock external dependencies
- Fast feedback

**3. Add Integration Tests:**
- Test database integration
- Test API integration
- Real components, controlled environment

**4. Add E2E Tests:**
- Critical user workflows
- Happy path scenarios
- Limited number (slow and expensive)

**5. Integrate with CI/CD:**
- All tests in pipeline
- Different stages
- Fail fast
- Block deployment on failure

**6. Add Allure Reports:**
- Visualize test results
- Track trends
- Team visibility

**7. Consider Testing in Production:**
- Feature toggles
- Synthetic test data
- Monitoring
- Safe experimentation

---

## Connections to Other Slides

### Integration with Slide 04 (CI/CD)

**GitHub Actions:**
- Test integration in workflows
- Different triggers for different tests
- Matrix strategy for cross-platform tests
- Secrets for test credentials

**Pipeline Stages:**
- Tests in CI pipeline
- Deployment gates
- Automated rollback on test failure

---

### Integration with Slide 05 (Delivery Strategies)

**Feature Toggles:**
- Enable testing in production
- Canary releases validated by tests
- A/B testing requires test data strategy

**Progressive Delivery:**
- Tests validate each rollout stage
- Monitoring complements testing
- Safe releases require good tests

---

## Final Exam Preparation Checklist

### Core Knowledge
- ✓ Understand why testing matters (Mars Orbiter)
- ✓ Know test pyramid and trophy models
- ✓ Know all test properties (4)
- ✓ Understand all test types (Static, Unit, Integration, System, E2E)
- ✓ Know advanced test types (Performance, Chaos, Security)
- ✓ Understand CI/CD integration
- ✓ Know testing in production (6 benefits, 6 safety techniques)

### Tool Knowledge
- ✓ Static testing tools (Linter, Type Checker, Formatter)
- ✓ E2E tools (Selenium, Cypress, Playwright)
- ✓ Performance tools (Locust, k6, Gatling, JMeter)
- ✓ Chaos tools (Chaos Mesh, Litmus, Gremlin)
- ✓ Security tools (OWASP ZAP, Trivy, Snyk)
- ✓ Allure Reports

### Practical Skills
- ✓ Can write GitHub Actions for tests
- ✓ Can design CI/CD pipeline with tests
- ✓ Can implement different test types
- ✓ Can integrate Allure Reports
- ✓ Understand production testing safety

### Conceptual Understanding
- ✓ Know when to use which test type
- ✓ Understand trade-offs (speed vs confidence)
- ✓ Know mocks vs stubs
- ✓ Understand exit criteria
- ✓ Know shift-left testing concept
- ✓ Understand flaky tests problem

---

# Summary

## Key Takeaways

### Testing is Essential
- Mars Climate Orbiter: $327M failure from lack of testing
- Cost of change increases exponentially
- Manual testing doesn't scale

### Multiple Test Types Needed
- Static: Catch errors at compile time
- Unit: Fast, isolated, many tests
- Integration: Real interactions, moderate number
- E2E: User perspective, few tests
- Advanced: Performance, Chaos, Security

### Test Strategy Matters
- Pyramid: Mostly unit (traditional)
- Trophy: Mostly integration (modern)
- Ice Cream: Avoid (anti-pattern)
- Choose based on your context

### Integrate with CI/CD
- Tests in pipeline stages
- Fail fast
- Block deployment on failure
- Automated reporting (Allure)

### Testing in Production is Real
- Staging ≠ Production
- Feature toggles enable safe testing
- Synthetic test data
- Mature practice in continuous delivery

### Practical Implementation
- Start with static testing
- Add unit tests for business logic
- Add integration tests for critical paths
- Add E2E for main workflows
- Integrate Allure Reports
- Continuously improve

---

# End of Study Guide

This comprehensive guide covers all material from ES Slide 06: Advanced Software Testing. Use it to:
- Understand testing fundamentals deeply
- Master all test types
- Prepare for exams
- Implement in your project
- Reference during development

**Remember:** Testing is not about achieving 100% coverage. It's about **confidence in your code** and **ability to change safely**.

Good luck with your studies and happy testing!
