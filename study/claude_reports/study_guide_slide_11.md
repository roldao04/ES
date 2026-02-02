# Software Engineering - Study Guide (Slide 11)
## LLMs in Software Development Lifecycle - Complete Exam Preparation Guide

---

# Table of Contents

1. [Introduction](#introduction)
   - [Industry Adoption](#industry-adoption)
   - [LLMs Evolution](#llms-evolution)
   - [Stack Overflow Survey 2025](#stack-overflow-survey-2025)
2. [AI Applications Across SDLC](#ai-applications-across-sdlc)
   - [The Iterative SDLC](#the-iterative-sdlc)
   - [Ten Key Areas](#ten-key-areas)
3. [Use Cases and Trade-offs](#use-cases-and-trade-offs)
   - [Generating Code Snippets](#generating-code-snippets)
   - [Debugging](#debugging)
   - [Accelerating Learning](#accelerating-learning)
   - [Optimizing Code](#optimizing-code)
   - [Automating Documentation](#automating-documentation)
   - [The Meeting Notes Example](#the-meeting-notes-example)
4. [Available Tools](#available-tools)
   - [Browser-Based Tools](#browser-based-tools)
   - [IDE-Based Tools](#ide-based-tools)
   - [Tool Comparison and Evaluation](#tool-comparison-and-evaluation)
5. [Prompt Engineering](#prompt-engineering)
   - [The 3S Principle](#the-3s-principle)
   - [Structuring Effective Prompts](#structuring-effective-prompts)
   - [Practical Examples](#practical-examples)
6. [Context Window Management](#context-window-management)
   - [Understanding Context Windows](#understanding-context-windows)
   - [Limitations by SDLC Stage](#limitations-by-sdlc-stage)
   - [Mitigation Strategies](#mitigation-strategies)
7. [AI Agents in SDLC](#ai-agents-in-sdlc)
   - [Agent Definition](#agent-definition)
   - [MCP Protocol](#mcp-protocol)
   - [Practical Examples](#practical-examples-1)
   - [Agent Best Practices](#agent-best-practices)
8. [Concerns and Best Practices](#concerns-and-best-practices)
   - [Liability Issues](#liability-issues)
   - [Security Concerns](#security-concerns)
   - [Best Practices Summary](#best-practices-summary)
9. [Study Tips and Exam Preparation](#study-tips-and-exam-preparation)
10. [Connections to Other Slides](#connections-to-other-slides)
11. [Summary and Key Takeaways](#summary-and-key-takeaways)

---

# Introduction

## Industry Adoption

### Who Uses AI in SDLC?

**Media Coverage (2024-2025):**
- Major companies announcing AI coding assistants
- GitHub Copilot adoption growing rapidly
- Cursor, Windsurf, and other AI IDEs gaining traction
- Industry-wide shift toward AI-assisted development

**Gartner Reports (2025):**
- Predictions on AI adoption in software engineering
- Forecast of productivity improvements
- Expected market growth
- Enterprise adoption trends

**The Reality:**
> "This area is undergoing rapid and continuous transformation."

---

## LLMs Evolution

### Historical Progression

**Timeline Highlights:**
- **2018:** GPT-1 introduced
- **2019:** GPT-2, initial concerns about misuse
- **2020:** GPT-3, significant capability jump
- **2021:** Codex (GitHub Copilot foundation)
- **2022:** ChatGPT launches, mainstream adoption begins
- **2023:** GPT-4, Claude, specialized coding models
- **2024:** Multimodal models, longer context windows
- **2025:** Agentic systems, MCP protocol, sophisticated tooling

**Key Observation:**
- From research curiosity to production tool in ~5 years
- Rapid improvement in code generation quality
- Shift from autocomplete to full agent systems

---

## Stack Overflow Survey 2025

### The Survey

**Scope:**
- **49,000+ responses** from 177 countries
- **62 questions** covering 314 different technologies
- **New focus areas:**
  - AI agent tools
  - LLMs in development
  - Community platforms

**Source:** https://survey.stackoverflow.co/2025

---

### Key Findings

**AI Tool Usage:**
- Majority of developers use AI coding assistants
- Most common: ChatGPT, GitHub Copilot
- Growing adoption of IDE-integrated tools

**Use Cases:**
- Code generation
- Debugging assistance
- Learning new technologies
- Documentation writing

**Sentiment:**
- Generally positive about AI assistance
- Concerns about over-reliance
- Debates about code quality
- Questions about long-term skill development

---

# AI Applications Across SDLC

## The Iterative SDLC

### Classic SDLC Cycle

```
Prototype ←→ Analyse ←→ Design ←→ Build ←→ Test ←→ Deliver ←→ Refine
    ↓           ↓          ↓         ↓        ↓        ↓         ↓
   AI         AI        AI        AI       AI       AI        AI
```

**Key Point:**
> "In all the phases, AI with LLMs or Agentic systems can be used."

---

### Where AI Fits

**Every Stage Can Benefit:**
- **Prototype:** Rapid mockup generation, idea validation
- **Analyse:** Requirements extraction, user story writing
- **Design:** Architecture suggestions, pattern recommendations
- **Build:** Code generation, autocomplete, refactoring
- **Test:** Test generation, bug detection, coverage analysis
- **Deliver:** Deployment automation, release notes
- **Refine:** Performance optimization, code review

---

## Ten Key Areas

### 1. Definition of Requirements and User Stories

**AI Helps With:**
- Converting informal descriptions to formal requirements
- Generating user stories from conversations
- Identifying missing requirements
- Structuring acceptance criteria

**Example:**
```
Input: "We need users to be able to save their preferences"

AI Output:
User Story: As a user, I want to save my preferences so that
            my settings persist across sessions.

Acceptance Criteria:
- User can access a settings page
- Settings are saved to the database
- Settings load automatically on login
- User receives confirmation when settings are saved
```

---

### 2. Autocomplete Code

**How It Works:**
- Predict next tokens based on context
- Suggest completions in real-time
- Learn from codebase patterns

**Example:**
```python
# You type:
def calculate_total_price(items):

# AI suggests:
    total = 0
    for item in items:
        total += item.price * item.quantity
    return total
```

**Tools:**
- GitHub Copilot
- TabNine
- Amazon CodeWhisperer

---

### 3. Code Generation

**Use Cases:**
- Generate entire functions from comments
- Create boilerplate code
- Implement common patterns
- Convert pseudocode to code

**Example:**
```python
# Write: "Function to validate email address"

# AI generates:
import re

def validate_email(email: str) -> bool:
    """
    Validates an email address using regex.

    Args:
        email: Email string to validate

    Returns:
        True if valid, False otherwise
    """
    pattern = r'^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$'
    return re.match(pattern, email) is not None
```

---

### 4. User Interface and Experience

**AI Applications:**
- Generate UI components from descriptions
- Suggest UX improvements
- Create responsive layouts
- Convert designs to code

**Example:**
```
Prompt: "Create a login form with email, password, and remember me"

AI generates complete component:
- HTML structure
- CSS styling
- Form validation
- Accessibility features
```

---

### 5. Bug Detection

**How AI Helps:**
- Static code analysis
- Pattern recognition for common bugs
- Security vulnerability detection
- Performance issue identification

**Example:**
```python
# Code:
def get_user(user_id):
    return db.query(f"SELECT * FROM users WHERE id={user_id}")

# AI detects:
⚠️ SQL Injection vulnerability
💡 Suggestion: Use parameterized queries
✓ Fixed:
    return db.query("SELECT * FROM users WHERE id=?", [user_id])
```

---

### 6. Code Review

**AI as Reviewer:**
- Check code style and conventions
- Suggest improvements
- Identify code smells
- Recommend refactoring

**Example:**
```python
# Original:
def process(d):
    r = []
    for i in d:
        if i > 0:
            r.append(i * 2)
    return r

# AI suggests:
# - Use descriptive variable names
# - Consider list comprehension
# - Add type hints and docstring

# Improved:
def process_positive_numbers(numbers: list[int]) -> list[int]:
    """Double all positive numbers in the input list."""
    return [num * 2 for num in numbers if num > 0]
```

---

### 7. Automate Testing & Quality Assurance

**AI-Generated Tests:**
- Unit tests from function signatures
- Integration tests from API specs
- Edge case identification
- Test data generation

**Example:**
```python
# Function:
def divide(a: float, b: float) -> float:
    return a / b

# AI generates tests:
def test_divide():
    assert divide(10, 2) == 5.0
    assert divide(7, 2) == 3.5
    assert divide(0, 5) == 0.0

def test_divide_by_zero():
    with pytest.raises(ZeroDivisionError):
        divide(10, 0)

def test_divide_negative():
    assert divide(-10, 2) == -5.0
    assert divide(10, -2) == -5.0
```

---

### 8. Predictive Analytics and Performance Optimization

**AI Applications:**
- Identify performance bottlenecks
- Suggest optimizations
- Predict resource usage
- Recommend caching strategies

**Example:**
```python
# Slow code:
def find_duplicates(items):
    duplicates = []
    for i, item in enumerate(items):
        for j, other in enumerate(items[i+1:]):
            if item == other and item not in duplicates:
                duplicates.append(item)
    return duplicates

# AI suggests O(n²) → O(n) optimization:
def find_duplicates(items):
    seen = set()
    duplicates = set()
    for item in items:
        if item in seen:
            duplicates.add(item)
        seen.add(item)
    return list(duplicates)
```

---

### 9. Documentation & Technical Writing

**AI Assistance:**
- Generate docstrings from code
- Create README files
- Write API documentation
- Produce user guides

**Example:**
```python
# Code without docs:
def calculate_metrics(data, window=7):
    results = []
    for i in range(len(data) - window + 1):
        window_data = data[i:i+window]
        avg = sum(window_data) / len(window_data)
        results.append(avg)
    return results

# AI generates:
def calculate_metrics(data: list[float], window: int = 7) -> list[float]:
    """
    Calculate rolling window average metrics.

    Args:
        data: List of numerical values to process
        window: Size of the rolling window (default: 7)

    Returns:
        List of calculated averages for each window

    Example:
        >>> calculate_metrics([1, 2, 3, 4, 5], window=3)
        [2.0, 3.0, 4.0]
    """
    # ... (same implementation)
```

---

### 10. Chatbot and Virtual Assistance

**AI Agents:**
- Answer technical questions
- Guide through codebases
- Assist with debugging
- Provide learning resources

**Examples:**
- Claude Code (CLI assistant)
- GitHub Copilot Chat
- Custom team chatbots

---

# Use Cases and Trade-offs

## Generating Code Snippets

### Pros

**1. Speeds Up Prototyping:**
- Quickly test ideas
- Generate boilerplate fast
- Focus on business logic

**2. Supports Multiple Languages:**
- Same assistant for Python, JavaScript, Go, etc.
- Learn new languages faster
- Consistent patterns across languages

**3. Bridges Idea-to-Implementation Gap:**
- Describe what you want
- Get working code immediately
- Iterate rapidly

**Example:**
```
Prompt: "Function to parse JSON from file with error handling"

Within seconds: Complete, working implementation
```

---

### Cons

**1. Risk of Incorrect or Insecure Code:**
- AI might generate vulnerabilities
- Logic errors not immediately obvious
- May not follow best practices

**Example Problem:**
```python
# AI might generate:
def load_config(filename):
    with open(filename) as f:
        return eval(f.read())  # ⚠️ Dangerous! Executes arbitrary code

# Should be:
def load_config(filename):
    with open(filename) as f:
        return json.load(f)  # ✓ Safe
```

---

**2. May Reduce Deep Understanding:**
- Copy-paste without comprehension
- Miss learning opportunities
- Dependency on AI for basics

**The Concern:**
```
Developer sees: Working code ✓
Developer misses: Why it works, how to modify it, trade-offs made
```

---

### Best Practice

**Use AI For:**
- Boilerplate and repetitive code
- Exploring new libraries
- Getting started quickly

**Always:**
- Review generated code carefully
- Understand what it does
- Test thoroughly
- Verify security implications

---

## Debugging

### Pros

**1. Saves Time:**
```
Traditional: Hours of print debugging
With AI: Paste error, get explanation in seconds
```

**2. Explains Errors:**
- Decodes cryptic error messages
- Suggests likely causes
- Provides context

**Example:**
```
Error: "TypeError: 'NoneType' object is not subscriptable"

AI explains:
- You're trying to access an index/key on None
- Likely cause: Function returned None instead of list/dict
- Check: Your database query or API call might have failed
```

---

**3. Improves Long-term Skills:**
- Learn debugging patterns
- Understand error types
- Build mental models

---

### Cons

**1. May Miss Context-Specific Issues:**
```python
# AI sees:
def process_data(data):
    return data[0]

# AI suggests: Check if data is empty

# But actual issue: data is sometimes None (not empty list)
# because of specific business logic in caller
```

---

**2. Can Lead to Over-Reliance:**
- Don't develop debugging intuition
- Skip learning debugger tools
- Miss root cause analysis skills

**The Problem:**
```
Without AI: Learn to use debugger, read stack traces, hypothesis testing
With AI only: Paste error → Get fix → Move on (no learning)
```

---

### Best Practice

**Use AI To:**
- Understand error messages
- Get initial debugging direction
- Learn debugging strategies

**Don't Use AI To:**
- Blindly apply fixes without understanding
- Skip learning debugger tools
- Avoid developing debugging skills

---

## Accelerating Learning

### Pros

**1. Fast Onboarding:**
```
Learning new framework:
Traditional: Read docs for hours
With AI: Ask specific questions, get targeted answers
```

**2. Provides Examples and Tutorials:**
```
Prompt: "Show me how to use React hooks with TypeScript"
Output: Complete examples with explanations
```

**3. Summarizes Documentation:**
```
Instead of: Reading 100-page manual
Get: Condensed explanation of key concepts
```

---

### Cons

**1. Learning Can Become Passive:**
```
Active learning: Struggle, experiment, discover
Passive with AI: Ask, receive, move on (less retention)
```

**2. Quality Depends on Model:**
- May provide outdated information
- Might miss recent changes
- Could have hallucinations

**Example Problem:**
```
AI trained on data up to 2023:
You: "How to use React Server Components?"
AI: Provides outdated or incorrect information about 2024 features
```

---

### Best Practice

**Use AI For:**
- Quick concept explanations
- Example code
- Initial learning direction

**Also Do:**
- Read official documentation
- Build projects yourself
- Experiment and make mistakes
- Join community discussions

**The Balance:**
```
Quick personal notes + AI full summary = Best learning approach
```

---

## Optimizing Code

### Pros

**1. Improves Performance:**
- Identifies O(n²) algorithms
- Suggests better data structures
- Recommends caching

**2. Enhances Readability:**
- Simplifies complex logic
- Suggests clearer variable names
- Improves structure

**3. Increases Maintainability:**
- Refactors duplicated code
- Suggests design patterns
- Reduces technical debt early

---

### Cons

**1. May Not Fit Context:**
```python
# AI suggests: Use dictionary for O(1) lookup

# But your context:
# - List has only 3 items
# - Performance difference negligible
# - Additional complexity not worth it
```

---

**2. Risk of Over-Optimization:**
```
Premature optimization is the root of all evil.
- Donald Knuth
```

**Example:**
```python
# Current (clear):
def calculate_total(items):
    return sum(item.price for item in items)

# AI suggests (optimized but complex):
def calculate_total(items):
    total = 0
    for item in items:
        total = (lambda acc, price: acc + price)(total, item.price)
    return total

# Optimization: Minimal gain, reduced clarity
```

---

### Best Practice

**Use AI To:**
- Identify genuine bottlenecks
- Learn optimization techniques
- Understand trade-offs

**Remember:**
1. Profile first (measure actual performance)
2. Optimize only where needed
3. Prioritize clarity over minor optimizations
4. Consider maintenance cost

---

## Automating Documentation

### Pros

**1. Saves Time:**
- Generate docstrings instantly
- Create README templates
- Update docs with code changes

**2. Keeps Docs Consistent:**
- Standard format across project
- All functions documented
- Reduces documentation drift

**3. Improves Collaboration:**
- New team members understand code
- Knowledge transfer easier
- Reduces tribal knowledge

---

### Cons

**1. May Produce Generic Descriptions:**
```python
def process_user_data(user_id, options):
    # ... complex business logic

# AI generates:
"""Process user data based on user ID and options."""
# ⚠️ Doesn't explain WHAT processing or WHY
```

---

**2. Requires Human Validation:**
```python
# Function:
def calculate_score(metrics, weights=[0.5, 0.3, 0.2]):
    return sum(m * w for m, w in zip(metrics, weights))

# AI docs:
"""Calculate weighted score from metrics."""

# Missing:
# - What do the default weights represent?
# - What's the expected range of metrics?
# - What does the score mean?
# - Business context?
```

---

**3. Can Be "Very Good" at Writing But Distracted:**

**The Warning:**
> "LLMs are 'very good' at producing written text, but they often create unnecessary noise, long passages that people don't actually read."

**The Problem:**
- Too verbose
- Generic filler text
- Misses the point
- Optimizes for length, not clarity

**Example:**
```python
# User wants: Brief explanation
# AI produces: 3 paragraphs of generic text about the importance
#              of validation, best practices, considerations...
# User needs: What this specific function validates
```

---

### Best Practice

**Use AI To:**
- Generate initial documentation
- Create structure/templates
- Ensure all code is documented

**Always:**
- Review and edit for accuracy
- Add business context
- Keep it concise
- Ensure it's actually helpful

**Remember:**
> "Short, concrete, and quick to understand" beats long, descriptive AI text.

---

## The Meeting Notes Example

### The Trade-off

**Two Approaches:**

#### 1. Your Own Notes
**Benefits:**
- Forces focus and attention
- Encourages critical thinking
- Better retention
- Active participation
- Preparation mindset

**Drawbacks:**
- Time-consuming
- Might miss details
- Subjective selection

---

#### 2. LLM Notes
**Benefits:**
- Efficiency
- Structured records
- Complete capture
- Less manual effort
- Searchable transcripts

**Drawbacks:**
- Passive listening
- Less retention
- May lose focus
- Less critical thinking

---

### The Question

> "Do we lose focus if LLMs take over?"

**The Concern:**
- Offloading thinking to AI
- Reduced engagement
- Dependency on tools
- Loss of active learning

---

### The Best Mix

**Recommended Approach:**
```
Quick personal notes (key points, your thoughts, questions)
            +
LLM full summary (complete record, searchable)
            =
Optimal balance (engaged + documented)
```

**Why This Works:**
- Stay engaged during meeting
- Have complete record after
- Your notes highlight what matters to you
- AI notes ensure nothing missed

---

# Available Tools

## Browser-Based Tools

### Examples
- **ChatGPT** (OpenAI)
- **Google Gemini**
- **Claude** (Anthropic)
- **Bing Chat**
- **Perplexity AI**

---

### Characteristics

**Advantages:**
- No installation needed
- Access from anywhere
- Easy to use
- Multi-purpose (not just coding)

**Disadvantages:**
- **Copy-paste workflow:** Manual transfer between browser and IDE
- **No codebase context:** Doesn't see your project structure
- **Limited integration:** Can't run code or tests
- **Cumbersome for large projects:** Hard to share multi-file context

---

### When to Use

**Good For:**
- Quick questions
- Learning concepts
- Algorithm problems
- Single-file solutions
- Pseudocode generation

**Not Good For:**
- Multi-file refactoring
- Large codebase navigation
- Integrated testing
- Production development workflow

---

## IDE-Based Tools

### Examples
- **GitHub Copilot**
- **Claude Code** (CLI)
- **Cursor**
- **Windsurf**
- **Amazon CodeWhisperer**
- **Tabnine**

---

### Characteristics

**Advantages:**
- **Seamless editing:** Suggestions appear in-place
- **Codebase awareness:** Understands project context
- **Integrated testing:** Can run tests immediately
- **Better workflow:** No context switching
- **File operations:** Create, edit, navigate files

**Disadvantages:**
- Requires installation
- Often requires subscription
- Learning curve
- May slow down IDE

---

### Tool Differentiation

**GitHub Copilot:**
- **Chat-first integration** inside IDE
- Inline suggestions + chat sidebar
- Agents for specific tasks (issue creation, PR review)
- Good ecosystem integration

**Windsurf:**
- **Agentic approach**
- Creates folders/files automatically
- "Review & accept all" workflow
- More autonomous actions

**Cursor:**
- **Balanced approach**
- Chat + optional agentic mode
- User chooses level of automation
- Flexible workflow

**Claude Code:**
- **CLI-based** agent
- Terminal interaction
- Full file system access
- Good for automation scripts

---

## Tool Comparison and Evaluation

### How to Evaluate Tools

**Define Criteria:**
1. **Accuracy:** Does it generate correct code?
2. **Context awareness:** Does it understand your project?
3. **Speed:** How fast are responses?
4. **Integration:** How well does it fit your workflow?
5. **Cost:** Subscription price vs value
6. **Features:** What can it do beyond code generation?

---

### Define Test Problem

**Examples:**
- 2D puzzle solver
- Todo app with backend
- Kanban board
- API integration

**Important:**
> "Define problem (e.g. 2D Puzzle, ToDo) and replicate across tools"

---

### Testing Results (April 2025)

**Simple Classic-Style Coding Tasks:**
```
Test: Algorithmic puzzles (clear I/O, single file, common patterns)
Result: All 5 tested tools solved in ~10 seconds
Finding: Outperformed human engineers for these narrow, well-defined challenges
```

**Larger Codebases & Projects:**
```
Test: Kanban UI + backend (multi-file project)
Result: Tools struggled
Issues: File coordination, architecture decisions, integration
```

---

### Browser vs IDE Experience

**Browser-Based Tools:**
- ❌ Make code integration cumbersome
- ❌ Copy/paste workflow
- ❌ Closed model ecosystem
- ❌ Heavy context sharing burden
- ❌ Poor for large projects

**IDE-Based Tools:**
- ✓ Seamless editing, review, and testing
- ✓ Inside context
- ✓ File operations integrated
- ✓ Better for production work

---

### The Verdict

**For Learning/Quick Tasks:**
- Browser tools work fine

**For Professional Development:**
- IDE-integrated tools essential

**For Large Projects:**
- Agentic tools (Cursor, Windsurf) show promise
- But still require significant human oversight

---

# Prompt Engineering

## The 3S Principle

### From GitHub Copilot

> **SIMPLE | SPECIFIC | SHORT**

**Three Rules for Better Prompts:**

---

### 1. SIMPLE

**What It Means:**
- Use clear, straightforward language
- Avoid unnecessary complexity
- One task per prompt

**Bad Example:**
```
"Create a function that, considering various edge cases and
potential errors that might occur, validates user input..."
```

**Good Example:**
```
"Function to validate email addresses"
```

---

### 2. SPECIFIC

**What It Means:**
- Define exactly what you want
- Include constraints
- Specify format, inputs, outputs

**Bad Example:**
```
"Make a sorting function"
```

**Good Example:**
```
"Function to sort list of dictionaries by 'date' key, descending order"
```

---

### 3. SHORT

**What It Means:**
- Concise prompts work better
- Avoid rambling
- Get to the point

**Bad Example:**
```
"I'm working on a project where I need to handle user authentication,
and I've been thinking about different approaches, and I wonder if
you could help me create a function that checks if a password meets
certain requirements, specifically it should be at least 8 characters,
have uppercase, lowercase, and a number..."
```

**Good Example:**
```
"Function to validate password:
- Min 8 characters
- Contains uppercase, lowercase, number"
```

---

## Structuring Effective Prompts

### Key Techniques

#### 1. Be Clear & Specific

**Define:**
- Task
- Context
- Format

**Example:**
```
Task: Create a REST API endpoint
Context: Flask app, user management
Format: Return JSON with status and data
```

---

#### 2. Use Step-by-Step Instructions

**When Needed:**
- Complex tasks
- Multiple requirements
- Specific order matters

**Example:**
```
Create a user registration function:
1. Validate email format
2. Check if email already exists
3. Hash password with bcrypt
4. Save to database
5. Return success/error response
```

---

#### 3. Provide Examples

**When Helpful:**
- Ambiguous requirements
- Specific format needed
- Pattern to follow

**Example:**
```
Create a function to format names.

Input examples:
- "john doe" → "John Doe"
- "JANE SMITH" → "Jane Smith"
- "bob" → "Bob"

Output: Title case for each word
```

---

#### 4. Iterate and Refine

**Process:**
```
Prompt v1 → Review output → Adjust prompt → Prompt v2 → Better output
```

**Don't Expect:**
- Perfect results first try
- AI to read your mind
- One-size-fits-all prompts

---

#### 5. Use Context-Aware Tools

**GitHub Copilot Example:**
- Sees your current file
- Knows your imports
- Understands project structure
- Suggests contextual completions

**Benefit:**
- Less explicit context needed in prompts
- More accurate suggestions

---

## Practical Examples

### Example 1: Error Diagnosis

**Prompt:**
```
Given the following error messages, logs, and user description,
identify the most likely technical system issues, ordered by
probability (from most to least likely).

For each identified issue, provide:
- A clear description of the probable root cause
- A technical justification based on the provided information
- Relevant excerpts copied exactly from the original logs or text
- A category code (e.g., "network", "storage", "permissions",
  "application", "database")

Format your response as a JSON array where each issue contains:
- description: text describing the probable cause
- justification: technical reasoning
- highlight: list with exact excerpts from logs
- category: short category label

[Insert logs here]
```

---

**Why This Works:**
- Clear task definition
- Specific output format
- Structured requirements
- Explicit format (JSON)
- Examples of categories

---

### Example 2: Code Generation

**Simple Prompt:**
```
# Function to validate email address
```

**More Specific Prompt:**
```python
def validate_email(email: str) -> bool:
    """
    Validates email address.

    Args:
        email: Email string to validate

    Returns:
        True if valid (user@domain.com format)
        False otherwise

    Examples:
        >>> validate_email("test@example.com")
        True
        >>> validate_email("invalid.email")
        False
    """
    # Implementation here
```

**Even Better (Context-Aware):**
```python
# Using: regex
# Validation: RFC 5322 simplified
# No external libraries

def validate_email(email: str) -> bool:
    # Implementation here
```

---

### Example 3: Debugging Assistance

**Weak Prompt:**
```
This doesn't work, help
```

**Better Prompt:**
```
Getting TypeError: 'NoneType' object is not subscriptable
on line 45. Here's the code:

[paste code]

What's the likely cause?
```

**Best Prompt:**
```
Error: TypeError: 'NoneType' object is not subscriptable at line 45

Code context:
[paste relevant code]

What I've tried:
- Checked if variable is initialized
- Added print statements before line 45

Expected behavior: Should access dictionary key
Actual behavior: Crashes with TypeError

What could cause this?
```

---

# Context Window Management

## Understanding Context Windows

### What Is It?

**Definition:**
> "The context window is the maximum amount of text (input + output) an LLM can process at once."

---

### Context Window Sizes

**Examples (2025):**
- **GPT-4 Turbo:** ~128k tokens (~300 pages of text)
- **Claude 3.5 Sonnet:** ~200k tokens
- **Smaller models:** 4k–32k tokens
- **Gemini Pro:** ~1M tokens (experimental)

**What Is a Token?**
- Roughly: 1 token ≈ 4 characters
- Or: 1 token ≈ 0.75 words
- Example: "Hello world" ≈ 2 tokens

---

### The Limitation

**Once the window limit is reached:**
```
[Older conversation] ← Falls out of memory
[Recent conversation] ← Still in context
```

**Unless:**
- Explicitly re-provided
- Summarized
- Stored externally (RAG)

---

### Why It Matters for SDLC

**Software Projects:**
- Large codebases (thousands of files)
- Long documentation
- Extensive logs
- Multiple files to consider

**Challenge:**
> "How do we work with AI when projects exceed context window?"

---

## Limitations by SDLC Stage

### Comprehensive Table

| SDLC Stage | Context Window Use | Risk / Limitation | Mitigation |
|------------|-------------------|-------------------|------------|
| **Requirements Analysis** | Load entire spec, user stories, regulatory docs | Large projects may exceed token limit | Chunk documents and summarize; use RAG |
| **Design** | Include architecture diagrams, APIs, design patterns | May lose prior context when switching files | Maintain indexed design repository and re-inject relevant parts |
| **Development** | Provide source files, dependency maps, coding standards | LLM may "forget" earlier files in large repos | Use selective file loading; ask AI about only relevant parts |
| **Testing** | Share test cases and coverage reports | Context overflow with large test suites | Pass only failing cases or focus area tests |
| **Deployment** | Review CI/CD config files and release notes | Non-critical here, but large config sets can still overflow | Provide modular config snippets |
| **Maintenance** | Bug triage using historical logs and commits | Logs may exceed token limit | Summarize logs before feeding to model |

---

## Mitigation Strategies

### Strategy 1: Chunking

**Approach:**
- Break large documents into smaller pieces
- Process each piece separately
- Combine results

**Example:**
```python
def process_large_spec(spec_file):
    chunks = split_into_chunks(spec_file, max_tokens=10000)

    summaries = []
    for chunk in chunks:
        summary = llm.summarize(chunk)
        summaries.append(summary)

    return combine_summaries(summaries)
```

---

### Strategy 2: RAG (Retrieval Augmented Generation)

**Approach:**
- Store all documents in vector database
- Retrieve only relevant parts for each query
- Provide targeted context to LLM

**Workflow:**
```
Large codebase → Embed all files → Vector DB

User query → Retrieve relevant files → Send to LLM
```

**Benefits:**
- Effectively infinite "memory"
- Only relevant context loaded
- Keeps within context window

---

### Strategy 3: Selective Loading

**Approach:**
- Don't load entire codebase
- Load only files relevant to current task
- Ask user to specify focus area

**Example:**
```
User: "Optimize the authentication system"

Instead of: Load entire codebase
Do: Load only auth-related files
    - auth/login.py
    - auth/middleware.py
    - models/user.py
```

---

### Strategy 4: Summarization

**Approach:**
- Summarize large contexts before providing to LLM
- Keep summaries of previous conversations
- Progressive summarization

**Example:**
```python
# Long log file (100k lines)
full_logs = read_logs()

# Summarize first
summary = f"""
Total entries: 50000
Error rate: 2.3%
Most common error: DatabaseConnectionTimeout (45%)
Time period: 2025-01-01 to 2025-01-20
"""

# Provide summary + recent errors
context = summary + get_recent_errors(limit=100)
llm.analyze(context)
```

---

### Strategy 5: Focused Queries

**Approach:**
- Ask specific questions
- One file/module at a time
- Iterate through components

**Bad:**
```
"Analyze my entire codebase and find all bugs"
```

**Good:**
```
"Review auth/login.py for security issues"
Then: "Review auth/middleware.py for security issues"
Then: Combine findings
```

---

### Strategy 6: Modular Approach

**Approach:**
- Break work into smaller tasks
- Each task has manageable context
- Combine results manually

**Example - Large Refactoring:**
```
Task 1: Refactor user model (single file)
Task 2: Update auth controllers (2 files)
Task 3: Update tests (relevant tests only)
Task 4: Update API docs (relevant sections)

Each task: Within context window ✓
Complete project: Too large ✗
Solution: Sequential tasks with human integration
```

---

# AI Agents in SDLC

## Agent Definition

### What Is an Agent?

**Classical Definition (not new, actually quite old):**
> "Software system that acts on behalf of users; accomplishes tasks in an autonomous way."

**Key Characteristics:**
1. **Autonomy:** Makes decisions independently
2. **Goal-oriented:** Works toward specified objectives
3. **Reactive:** Responds to environment changes
4. **Proactive:** Takes initiative to achieve goals

---

### Agents vs Simple AI

**Simple AI:**
```
User: "Write a login function"
AI: [Generates function]
Done.
```

**Agent:**
```
User: "Implement user authentication"
Agent:
  1. Analyzes existing codebase
  2. Creates auth module
  3. Writes login/logout functions
  4. Generates tests
  5. Updates documentation
  6. Creates migration script
Done (multiple autonomous steps).
```

---

### Tools

**Definition:**
> "External resources or functions called upon by agents to accomplish tasks."

**Examples:**
- File system operations (read, write, edit)
- Database queries
- API calls
- Git operations
- Terminal commands
- Web searches

**Relationship:**
```
Agent uses Tools to accomplish Tasks
```

---

## MCP Protocol

### What Is MCP?

**Model Context Protocol (MCP):**
- Standard protocol for connecting AI models with tools
- Enables agents to interact with external systems
- Created for ecosystem interoperability

**Source:** https://modelcontextprotocol.io

---

### Why MCP Matters

**Without MCP:**
```
Each AI tool has custom integrations
GitHub integration for Copilot ≠ GitHub integration for Cursor
Every tool reinvents the wheel
```

**With MCP:**
```
Standard protocol
Build GitHub MCP server once
All MCP-compatible tools can use it
Ecosystem benefits
```

---

### MCP Architecture

**The Structure:**

```
AI Application (MCP Host)
        ↓
    One-to-one connections
        ↓
   ├─ MCP Server 1 (GitHub)
   ├─ MCP Server 2 (JIRA)
   ├─ MCP Server 3 (Database)
   └─ MCP Server 4 (Observability)

Each server provides isolated capabilities
Each client manages exactly one server connection
```

---

### Host Architecture Details

**Key Points:**
- The MCP Host (your AI application) creates independent connections
- One-to-one between host and each server
- Each server provides isolated capabilities
- Each client manages exactly one server connection

**Flexibility:**
- MCP Servers can be local or remote
- Depends on the use case
- Local: File system, local DB
- Remote: APIs, cloud services

---

### The Ecosystem Vision

**Integration Points:**
- **IDE** ↔ GitHub, JIRA
- **IDE** ↔ Observability tools (Prometheus, Grafana)
- **IDE** ↔ Documentation systems
- **IDE** ↔ Communication channels (Slack, Teams)
- **IDE** ↔ Other development tools

**Benefit:**
> "Agents with MCP are important if they are used in an ecosystem."

**The Goal:**
- Seamless tool integration
- Agent can access everything needed
- Standard protocol reduces friction

---

## Practical Examples

### Example 1: Create an Issue (Traditional)

**Manual Workflow:**

**Step 1: In IDE**
```
Review code → Find bug → Copy details
```

**Step 2: Switch to Browser**
```
Open GitHub → Navigate to issues → Click "New Issue"
```

**Step 3: Fill Form**
```
Paste title
Paste description
Add labels
Assign person
Submit
```

**Step 4: Back to IDE**
```
Continue working
```

**Time:** 5-10 minutes
**Context switches:** 2

---

### Example 2: Create an Issue (With Agent)

**Agent Workflow:**

**Step 1: In IDE**
```
User: "Create a GitHub issue for this bug"

Agent:
  1. Analyzes current code context
  2. Identifies relevant files
  3. Generates issue title and description
  4. Connects to GitHub via MCP
  5. Creates issue
  6. Returns issue URL

User: Continues working
```

**Time:** 30 seconds
**Context switches:** 0

---

### The Agent Created

**Issue Details:**
- Title: Generated from context
- Description: Code snippets, error messages, reproduction steps
- Labels: Auto-assigned based on content
- Assignee: Based on code ownership or team rules

**Example Output:**
```
Created issue #123: "Authentication fails for OAuth users"

Description:
  Bug found in auth/oauth_handler.py line 45.
  Error: KeyError when accessing user['email']

  Reproduction:
  1. User logs in via OAuth
  2. OAuth provider doesn't include 'email' in response
  3. Handler assumes 'email' exists

  Suggested fix:
  Use user.get('email', '') instead of user['email']

Labels: bug, authentication, priority:high
Assignee: @auth-team

Link: https://github.com/org/repo/issues/123
```

---

### Example 3: The Problem with LLM-Generated Text

**The Warning from Slides:**
> "LLMs are 'very good' at producing written text, but they often create unnecessary noise, long passages that people don't actually read."

**In Issues or Pull Requests:**
- Overly detailed text is rarely useful
- Short, concrete, quick to understand is better
- People won't read 3 paragraphs of AI fluff

---

**Example of Bad Agent Output:**
```
Issue Title: Critical Authentication System Enhancement Required

Description:
  In the modern software development landscape, authentication
  represents a crucial cornerstone of security architecture.
  Our investigation has revealed...
  [3 more paragraphs of generic text]

  In conclusion, it is imperative that we address this matter...
```

**What People Actually Want:**
```
Issue Title: OAuth users can't log in

Description:
  Error: KeyError on user['email'] in oauth_handler.py:45

  Cause: OAuth providers don't always return email field

  Fix: Use user.get('email', '') instead of user['email']

  Priority: High (blocks all OAuth logins)
```

---

## Agent Best Practices

### 1. Keep Output Concise

**DO:**
- Short, concrete descriptions
- Bullet points
- Code snippets
- Clear action items

**DON'T:**
- Long prose
- Generic introductions
- Unnecessary context
- Filler text

---

### 2. Provide Context, Not Noise

**Good Context:**
- Relevant code snippets
- Error messages
- Reproduction steps
- Expected vs actual behavior

**Noise:**
- General statements about importance
- Obvious advice
- Lengthy explanations of basic concepts

---

### 3. Make Agent Output Reviewable

**Before Agent Acts:**
- Show what it will do
- Get confirmation for critical actions
- Allow editing

**Example:**
```
Agent: "I'll create this GitHub issue:
        [Shows preview]
        Proceed? (y/n)"

User: Reviews and confirms
```

---

### 4. Human-in-the-Loop for Critical Operations

**Require Confirmation For:**
- Creating issues
- Opening PRs
- Merging code
- Deploying to production
- Modifying databases

**Can Be Automatic:**
- Running tests
- Formatting code
- Generating drafts

---

# Concerns and Best Practices

## Liability Issues

### Who Is Responsible?

**The Answer:**
> "Who is responsible for that code, documentation, or issues? **The developer.**"

**Key Point:**
- AI is a tool
- Developer owns the output
- Can't blame AI for bugs
- Legal responsibility stays with human

---

### Intellectual Property Risk

**The Problem:**
> "AI-generated code may unintentionally reproduce copyrighted or proprietary code from its training data, leading to intellectual property disputes."

**Scenarios:**
1. **Copyright infringement:**
   - AI trained on GPL code
   - Generates similar code
   - You use it in proprietary project
   - Violation?

2. **Proprietary code leakage:**
   - AI trained on leaked code
   - Reproduces trade secrets
   - Legal implications

---

**Real-World Examples:**
- GitHub Copilot lawsuits
- Questions about training data
- Licensing concerns
- Open-source compliance

**Protection Strategies:**
1. Review generated code
2. Check for unusual patterns
3. Use license-compliant AI tools
4. Run code originality checks
5. Understand your AI tool's training data

---

## Security Concerns

### The Risk

> "AI may introduce insecure coding patterns or dependencies, increasing the attack surface."

**Who Is Liable:**
> "The organization deploying the code could be held responsible for damages caused by a breach."

---

### Common Security Issues

**1. SQL Injection:**
```python
# AI might generate:
query = f"SELECT * FROM users WHERE id = {user_id}"

# Vulnerable to injection
```

**2. Hardcoded Secrets:**
```python
# AI might include:
API_KEY = "sk-1234567890abcdef"
```

**3. Insecure Dependencies:**
```python
# AI suggests:
import old_vulnerable_library
```

**4. Missing Input Validation:**
```python
# AI generates:
def update_user(user_id, data):
    db.update(user_id, data)  # No validation!
```

---

### Mitigation Strategies

**1. Integrate Secure Code Review:**
```
AI generates code → Security scan → Human review → Commit
```

**2. Follow OWASP Guidance:**
- OWASP AI/LLM Security Guide
- https://owasp.org/www-project-ai-security-and-privacy-guide/
- OWASP Top 10 for AI

**3. Apply Static/Dynamic Analysis:**
```
Tools:
- SonarQube
- Snyk
- Bandit (Python)
- ESLint (JavaScript)
```

**4. Security Testing:**
```
- Penetration testing
- Dependency scanning
- Secret scanning
- Vulnerability assessment
```

---

### Research Reference

**Important Paper:**
- https://arxiv.org/html/2501.19012v1
- Studies security issues in AI-generated code
- Findings on vulnerability rates
- Recommendations for safe usage

---

## Best Practices Summary

### 1. Policy & Training

**Establish:**
- Clear AI usage policy
- Training on responsible AI use
- Guidelines for what AI can/cannot do
- Review processes

**Example Policy:**
```
✓ Use AI for: Boilerplate, testing, documentation drafts
✗ Don't use AI for: Security-critical code without review
⚠️ Always review: All AI-generated code before commit
```

---

### 2. Testing & Verification

**Rule:**
> "Never deploy AI outputs without thorough human review."

**Process:**
```
AI generates → Human reviews → Tests run → Manual testing → Deploy
```

**Never:**
```
AI generates → Deploy ❌
```

---

### 3. Traceability

**Document:**
- Prompts used
- AI outputs
- Review decisions
- Changes made

**Why:**
- Auditability
- Learning from mistakes
- Compliance requirements
- Debugging issues

**Example:**
```markdown
## AI-Assisted Development Log

### 2025-01-20: Authentication Refactor
- Prompt: "Refactor auth system to use JWT"
- Model: GPT-4
- Output: [link to AI response]
- Changes: Added expiration, removed passwords field
- Reviewed by: @security-team
- Tests: All passing
- Deployed: 2025-01-21
```

---

### 4. Security & Privacy

**Critical Rules:**

**DON'T:**
- Expose sensitive code/data to external LLMs
- Share secrets, API keys, credentials
- Upload proprietary algorithms
- Send customer data

**DO:**
- Use local models for sensitive code
- Redact sensitive information
- Use enterprise AI with data protection
- Follow data governance policies

**Example:**
```python
# DON'T paste this in ChatGPT:
API_KEY = "sk-real-key-here"
DATABASE_URL = "postgres://prod-db.company.com"

# DO paste this:
API_KEY = os.environ.get('API_KEY')
DATABASE_URL = os.environ.get('DATABASE_URL')
```

---

### 5. Purpose Use

**Use GenAI For:**
- ✓ Boilerplate code
- ✓ Documentation
- ✓ Test generation
- ✓ Code explanations
- ✓ Refactoring suggestions

**Not For (Without Careful Review):**
- ✗ Critical business logic
- ✗ Security implementations
- ✗ Financial calculations
- ✗ Medical/safety systems
- ✗ Legal compliance code

---

### 6. Continuous Improvement

**Iterate On:**
- Prompt strategies
- Review processes
- Tool selection
- Team workflows

**But:**
> "Do NOT lose your time refining too much."

**Balance:**
```
Spend time on: Improving productivity
Don't spend time on: Perfect prompts for marginal gains
```

---

### 7. Critical Thinking

**Remember:**
> "This area is undergoing rapid and continuous transformation. Use self-critical thinking."

**Ask Yourself:**
- Is this AI suggestion actually better?
- Do I understand what this code does?
- Are there security implications?
- Does this fit our architecture?
- Is this maintainable?

**Don't:**
- Blindly accept AI output
- Assume AI is always right
- Skip understanding the code

---

# Study Tips and Exam Preparation

## Critical Concepts

### Must-Know Topics

**1. AI Applications in SDLC:**
- 10 key areas (memorize them)
- Where AI helps in each phase
- Iterative nature of SDLC

**2. Use Cases with Trade-offs:**
- 5 main use cases (code generation, debugging, learning, optimization, documentation)
- Pros and cons of each
- When to use, when to avoid

**3. Tools Landscape:**
- Browser vs IDE-based
- Differentiation (Copilot, Cursor, Windsurf)
- Evaluation criteria

**4. Prompt Engineering:**
- 3S principle (Simple, Specific, Short)
- Structuring techniques
- Iteration importance

**5. Context Window:**
- What it is
- Limitations by SDLC stage
- Mitigation strategies (chunking, RAG, summarization)

**6. Agents:**
- Definition (autonomous, goal-oriented)
- MCP protocol
- Ecosystem vision
- Best practices (concise output)

**7. Concerns:**
- Liability (developer responsible)
- Security (OWASP guidance)
- Best practices (testing, traceability)

---

## Common Exam Questions

### Type 1: Identify AI Applications

**Example:**
> "List and explain 5 areas in SDLC where AI can be applied."

**Answer Framework:**
1. **Requirements:** User story generation, requirement extraction
2. **Development:** Code generation, autocomplete, refactoring
3. **Testing:** Test generation, bug detection, coverage analysis
4. **Documentation:** Docstring generation, README creation
5. **Maintenance:** Code review, optimization, performance analysis

---

### Type 2: Trade-off Analysis

**Example:**
> "What are the pros and cons of using AI for code generation?"

**Answer Must Include:**

**Pros:**
- Speeds up prototyping
- Supports multiple languages
- Bridges idea-to-implementation gap

**Cons:**
- Risk of incorrect/insecure code
- May reduce deep understanding
- Requires careful review

**Conclusion:**
- Use for boilerplate, not critical logic
- Always review generated code
- Understand before using

---

### Type 3: Tool Selection

**Example:**
> "When would you choose an IDE-based tool over a browser-based tool for AI assistance?"

**Answer:**

**IDE-based When:**
- Multi-file projects
- Production development
- Need codebase context
- Integrated testing required
- Professional workflow

**Browser-based When:**
- Quick questions
- Learning concepts
- Single-file problems
- Algorithm practice
- Not working in IDE

---

### Type 4: Context Window Problem

**Example:**
> "Your project has 1000 source files. How do you use AI assistance given context window limitations?"

**Answer:**

**Strategies:**
1. **Selective Loading:** Focus on relevant files only
2. **RAG:** Vector database with retrieval
3. **Chunking:** Process sections separately
4. **Summarization:** Summarize large contexts
5. **Focused Queries:** One module at a time

**Example:**
```
Instead of: "Analyze entire codebase"
Do: "Analyze auth module" then "Analyze API module" etc.
```

---

### Type 5: Security Concerns

**Example:**
> "What security risks does AI-generated code pose, and how do you mitigate them?"

**Answer:**

**Risks:**
- SQL injection, XSS, other vulnerabilities
- Insecure dependencies
- Hardcoded secrets
- Missing input validation

**Mitigation:**
- Human security review
- Static/dynamic analysis tools
- Follow OWASP guidelines
- Run security scans
- Never deploy without testing

**Reference:** OWASP AI Security Guide

---

### Type 6: Prompt Engineering

**Example:**
> "Explain the 3S principle for prompt engineering and provide an example."

**Answer:**

**3S Principle:**
1. **SIMPLE:** Clear, straightforward language
2. **SPECIFIC:** Exact requirements, constraints
3. **SHORT:** Concise, to the point

**Example:**

Bad: "I need a function that handles user login and manages sessions..."

Good: "Function to authenticate user with email and password, return JWT token"

---

### Type 7: Agent Capabilities

**Example:**
> "What is the MCP protocol and why is it important for AI agents in SDLC?"

**Answer:**

**MCP (Model Context Protocol):**
- Standard protocol for connecting AI models with tools
- Enables interoperability across ecosystem

**Importance:**
- Agents can access multiple tools (GitHub, JIRA, DB, etc.)
- Standard integration (write once, use everywhere)
- Ecosystem growth
- Better agent capabilities

**Architecture:**
- Host (AI app) connects to multiple MCP servers
- Each server provides specific capabilities
- One-to-one connections

---

## Important Distinctions

### Browser vs IDE Tools

| Aspect | Browser-Based | IDE-Based |
|--------|---------------|-----------|
| **Integration** | Copy-paste workflow | Seamless in-editor |
| **Context** | No codebase awareness | Full project context |
| **Best For** | Learning, quick questions | Production development |
| **Examples** | ChatGPT, Gemini | Copilot, Cursor |

---

### Agents vs Simple AI

| Aspect | Simple AI | Agents |
|--------|-----------|--------|
| **Autonomy** | Single response | Multi-step autonomous |
| **Tools** | None | Uses external tools |
| **Scope** | One task | Complex workflows |
| **Example** | Generate function | Implement feature end-to-end |

---

### AI Use Cases: When to Use

| Use Case | Good For | Avoid For |
|----------|----------|-----------|
| **Code Generation** | Boilerplate, prototypes | Critical business logic |
| **Debugging** | Understanding errors | Root cause in complex systems |
| **Learning** | Quick concepts | Deep understanding |
| **Optimization** | Identifying bottlenecks | Premature optimization |
| **Documentation** | Initial drafts | Final documentation (without review) |

---

## Exam Strategy

### Answer Structure

**For Any Question:**

1. **Define key terms** (context window, agent, RAG, etc.)
2. **Explain the concept** (how it works, why it matters)
3. **Provide examples** (concrete illustrations)
4. **Discuss trade-offs** (pros and cons)
5. **Mention best practices** (how to use properly)

---

### Key Phrases to Use

**When discussing AI in SDLC:**
- "Rapid and continuous transformation"
- "Use self-critical thinking"
- "Developer remains responsible"
- "Always requires human review"

**When discussing tools:**
- "IDE-based provides seamless integration"
- "Browser-based for quick tasks"
- "Context-aware suggestions"

**When discussing prompts:**
- "Simple, Specific, Short (3S)"
- "Iterate and refine"
- "Provide examples when needed"

**When discussing concerns:**
- "Developer is liable"
- "Follow OWASP guidelines"
- "Never deploy without review"

---

## Final Checklist

Before the exam, ensure you can:

- [ ] List 10 AI applications in SDLC
- [ ] Explain pros/cons of 5 main use cases
- [ ] Compare browser vs IDE tools
- [ ] Describe tool differentiation (Copilot, Cursor, Windsurf)
- [ ] Explain 3S principle with examples
- [ ] Define context window and limitations
- [ ] List mitigation strategies for context limits
- [ ] Explain RAG (Retrieval Augmented Generation)
- [ ] Define AI agents and their characteristics
- [ ] Explain MCP protocol and architecture
- [ ] Discuss liability concerns
- [ ] Describe security risks and mitigations
- [ ] List best practices (testing, traceability, etc.)
- [ ] Explain why "short and concrete" beats long AI text
- [ ] Understand Stack Overflow survey insights

---

# Connections to Other Slides

## Slide 10: MLOps

### LLMs as ML Models

**Connection:**
- LLMs are ML models
- Require MLOps practices
- But with LLMOps adaptations

**Key Links:**
- Prompt versioning (like code versioning)
- Context management (like data versioning)
- Quality monitoring (like model monitoring)
- A/B testing (same concept)

**Differences:**
- LLMs focus on prompts + context
- Less emphasis on training
- More emphasis on RAG
- Qualitative evaluation (toxicity, relevance)

---

## Slide 07: CI/CD

### AI in Pipelines

**AI Can Enhance CI/CD:**
- Generate tests automatically
- Optimize build processes
- Analyze failures
- Suggest fixes

**Example:**
```yaml
# CI/CD with AI assistance
on_failure:
  - capture_logs
  - ai_analyze_failure
  - suggest_fix
  - notify_developer_with_suggestion
```

**AI Agents for Deployment:**
- Automate release notes
- Generate deployment documentation
- Monitor deployment success
- Rollback decision assistance

---

## Slide 08: Observability

### AI for Monitoring

**AI Analyzes Logs:**
- Pattern recognition in logs
- Anomaly detection
- Root cause analysis
- Predictive alerting

**Example:**
```python
# AI-powered log analysis
def analyze_incident(logs):
    ai_summary = llm.analyze(f"""
    Given these error logs, identify:
    1. Most likely root cause
    2. Affected components
    3. Suggested fix
    4. Priority level

    Logs: {logs}
    """)
    return ai_summary
```

**Connection to Context Window:**
- Large log files exceed context window
- Need summarization (as discussed in Slide 11)
- Apply mitigation strategies

---

## Slide 09: Legacy Code

### AI for Legacy Systems

**AI Helps With:**
- Understanding legacy codebases
- Generating documentation
- Refactoring suggestions
- Test generation for untested code

**Example Use Case:**
```
Legacy system with no docs:
1. Use AI to analyze code
2. Generate documentation
3. Create tests
4. Suggest refactoring
5. Modernize gradually
```

**Challenges:**
- Large codebases (context window issue)
- Outdated patterns (AI training data bias)
- Complex business logic (needs human understanding)

**Best Approach:**
- Use AI as assistant, not replacement
- Combine AI analysis with human expertise
- Iterative modernization

---

# Summary and Key Takeaways

## The AI Revolution in SDLC

**Current State (2025):**
- Widespread adoption across industry
- Stack Overflow survey: Majority use AI tools
- Rapid evolution of capabilities
- Shift from autocomplete to agents

**Key Message:**
> "This area is undergoing rapid and continuous transformation."

---

## 10 AI Applications (Memorize)

1. **Requirements & User Stories** - Generation and extraction
2. **Autocomplete Code** - Real-time suggestions
3. **Code Generation** - Functions, classes, modules
4. **UI/UX** - Component generation, design-to-code
5. **Bug Detection** - Static analysis, vulnerability scanning
6. **Code Review** - Style, quality, improvements
7. **Testing & QA** - Test generation, coverage analysis
8. **Optimization** - Performance, readability
9. **Documentation** - Docstrings, READMEs, guides
10. **Chatbots & Assistants** - Interactive help, agents

---

## 5 Major Use Cases with Trade-offs

### 1. Code Generation
- ✓ Fast prototyping, multi-language
- ✗ Incorrect/insecure code, reduced learning

### 2. Debugging
- ✓ Time-saving, error explanations
- ✗ May miss context, over-reliance

### 3. Learning
- ✓ Quick onboarding, examples
- ✗ Passive learning, quality varies

### 4. Optimization
- ✓ Performance, readability
- ✗ May not fit context, over-optimization

### 5. Documentation
- ✓ Time-saving, consistency
- ✗ Generic content, needs validation

---

## Tools Landscape

**Browser-Based:**
- ChatGPT, Gemini, Claude
- Good for: Learning, quick questions
- Limited: Copy-paste workflow

**IDE-Based:**
- GitHub Copilot, Cursor, Windsurf
- Good for: Production development
- Better: Codebase context, seamless integration

**Evaluation:**
- Test with realistic problems
- Compare across criteria
- Simple tasks: All tools excel
- Complex projects: IDE tools better

---

## Prompt Engineering: 3S

```
SIMPLE - Clear, straightforward language
SPECIFIC - Exact requirements, constraints
SHORT - Concise, to the point
```

**Additional Tips:**
- Provide examples when needed
- Step-by-step for complex tasks
- Iterate and refine
- Use context-aware tools

---

## Context Window Management

**The Limitation:**
- Fixed token limit per request
- Large projects exceed limit
- Must manage carefully

**Mitigation Strategies:**
1. **Chunking** - Break into pieces
2. **RAG** - Vector DB retrieval
3. **Selective Loading** - Relevant files only
4. **Summarization** - Compress context
5. **Focused Queries** - One module at a time

**By SDLC Stage:**
- Requirements: Chunk docs, use RAG
- Design: Indexed repository
- Development: Selective file loading
- Testing: Focus on failing tests
- Maintenance: Summarize logs

---

## AI Agents

**Definition:**
- Autonomous software systems
- Goal-oriented
- Use tools to accomplish tasks

**MCP Protocol:**
- Standard for tool integration
- Host ↔ Server architecture
- Ecosystem interoperability

**Best Practices:**
- Keep output concise
- "Short and concrete" > long AI text
- Human-in-the-loop for critical actions
- Review before executing

---

## Concerns and Responsibility

### Liability
> **"The developer is responsible."**
- Can't blame AI for bugs
- Legal responsibility with human
- IP risks from training data

### Security
- AI may generate vulnerabilities
- Always review for security issues
- Follow OWASP guidelines
- Static/dynamic analysis required

### Best Practices
1. **Policy & Training** - Clear guidelines
2. **Testing** - Never deploy without review
3. **Traceability** - Document AI usage
4. **Security** - Don't expose sensitive data
5. **Purpose** - Use for assistance, not critical logic
6. **Improvement** - Iterate, but don't over-optimize
7. **Critical Thinking** - Question AI outputs

---

## The Central Warning

> "LLMs are 'very good' at producing written text, but they often create unnecessary noise, long passages that people don't actually read."

**Remember:**
- Short, concrete, quick to understand
- Especially for issues, PRs, documentation
- AI tends toward verbose
- Human editing essential

---

## Final Thoughts

**AI in SDLC:**
- Powerful tool, not replacement for developers
- Accelerates certain tasks significantly
- Requires critical thinking and oversight
- Developer responsibility remains

**Approach:**
- Embrace AI assistance
- Maintain skepticism
- Always review and test
- Keep learning fundamentals
- Use self-critical thinking

**The Future:**
- Rapid ongoing transformation
- New tools and capabilities constantly
- Stay informed but adaptable
- Focus on principles, not specific tools

---

**Good luck with your exam!**
