---
name: code-review-codex
description: |
  Use when reviewing pull requests, reviewing code changes, conducting architecture or security reviews,
  checking code quality, finding bugs, or giving structured review feedback across React, Vue, Rust,
  TypeScript, Java, Python, Go, C, C++, CSS, and Qt codebases.
---

# Code Review Codex

Transform code reviews from gatekeeping to knowledge sharing through constructive feedback, systematic analysis, and collaborative improvement.

## When to Use This Skill

- Reviewing pull requests and code changes
- Establishing code review standards for teams
- Mentoring junior developers through reviews
- Conducting architecture reviews
- Creating review checklists and guidelines
- Improving team collaboration
- Reducing code review cycle time
- Maintaining code quality standards

## Core Principles

### 1. The Review Mindset

**Goals of Code Review:**
- Catch bugs and edge cases
- Ensure code maintainability
- Share knowledge across team
- Enforce coding standards
- Improve design and architecture
- Build team culture

**Not the Goals:**
- Show off knowledge
- Nitpick formatting (use linters)
- Block progress unnecessarily
- Rewrite to your preference

### 2. Effective Feedback

**Good Feedback is:**
- Specific and actionable
- Educational, not judgmental
- Focused on the code, not the person
- Balanced (praise good work too)
- Prioritized (critical vs nice-to-have)

```markdown
❌ Bad: "This is wrong."
✅ Good: "This could cause a race condition when multiple users
         access simultaneously. Consider using a mutex here."

❌ Bad: "Why didn't you use X pattern?"
✅ Good: "Have you considered the Repository pattern? It would
         make this easier to test. Here's an example: [link]"

❌ Bad: "Rename this variable."
✅ Good: "[nit] Consider `userCount` instead of `uc` for
         clarity. Not blocking if you prefer to keep it."
```

### 3. Review Scope

**What to Review:**
- Logic correctness and edge cases
- Security vulnerabilities
- Performance implications
- Test coverage and quality
- Error handling
- Documentation and comments
- API design and naming
- Architectural fit

**What Not to Review Manually:**
- Code formatting (use Prettier, Black, etc.)
- Import organization
- Linting violations
- Simple typos

## Review Process

### Phase 1: Context Gathering (2-3 minutes)

Before diving into code, understand:
1. Read PR description and linked issue
2. Check PR size (>400 lines? Ask to split)
3. Review CI/CD status (tests passing?)
4. Understand the business requirement
5. Note any relevant architectural decisions

### Phase 2: High-Level Review (5-10 minutes)

1. **Architecture & Design** - Does the solution fit the problem?
   - For significant changes, consult [Architecture Review Guide](reference/architecture-review-guide.md)
   - Check: SOLID principles, coupling/cohesion, anti-patterns
2. **Performance Assessment** - Are there performance concerns?
   - For performance-critical code, consult [Performance Review Guide](reference/performance-review-guide.md)
   - Check: Algorithm complexity, N+1 queries, memory usage
3. **File Organization** - Are new files in the right places?
4. **Testing Strategy** - Are there tests covering edge cases?

### Phase 3: Line-by-Line Review (10-20 minutes)

For each file, check:
- **Logic & Correctness** - Edge cases, off-by-one, null checks, race conditions
- **Security** - Input validation, injection risks, XSS, sensitive data
- **Performance** - N+1 queries, unnecessary loops, memory leaks
- **Maintainability** - Clear names, single responsibility, comments

### Phase 4: Summary & Decision (2-3 minutes)

1. Summarize key concerns
2. Highlight what you liked
3. Make clear decision:
   - ✅ Approve
   - 💬 Comment (minor suggestions)
   - 🔄 Request Changes (must address)
4. Offer to pair if complex

## Review Techniques

### Technique 1: The Checklist Method

Use checklists for consistent reviews. See [Security Review Guide](reference/security-review-guide.md) for comprehensive security checklist.

### Technique 2: The Question Approach

Instead of stating problems, ask questions:

```markdown
❌ "This will fail if the list is empty."
✅ "What happens if `items` is an empty array?"

❌ "You need error handling here."
✅ "How should this behave if the API call fails?"
```

### Technique 3: Suggest, Don't Command

Use collaborative language:

```markdown
❌ "You must change this to use async/await"
✅ "Suggestion: async/await might make this more readable. What do you think?"

❌ "Extract this into a function"
✅ "This logic appears in 3 places. Would it make sense to extract it?"
```

### Technique 4: Differentiate Severity

Use labels to indicate priority:

- 🔴 `[blocking]` - Must fix before merge
- 🟡 `[important]` - Should fix, discuss if disagree
- 🟢 `[nit]` - Nice to have, not blocking
- 💡 `[suggestion]` - Alternative approach to consider
- 📚 `[learning]` - Educational comment, no action needed
- 🎉 `[praise]` - Good work, keep it up!

## Language-Specific Guides

Consult the matching guide for the language or framework under review:

| Language/Framework | Reference File | Key Topics |
|-------------------|----------------|------------|
| **React** | [React Guide](reference/react.md) | Hooks, useEffect, React 19 Actions, RSC, Suspense, TanStack Query v5 |
| **Vue 3** | [Vue Guide](reference/vue.md) | Composition API, reactivity system, Props/Emits, Watchers, Composables |
| **Rust** | [Rust Guide](reference/rust.md) | ownership and borrowing, unsafe review, async code, error handling |
| **TypeScript** | [TypeScript Guide](reference/typescript.md) | type safety, async/await, immutability |
| **Python** | [Python Guide](reference/python.md) | mutable default arguments, exception handling, class attributes |
| **Java** | [Java Guide](reference/java.md) | Java 17/21 features, Spring Boot 3, virtual threads, Stream/Optional |
| **Go** | [Go Guide](reference/go.md) | error handling, goroutines and channels, context, interface design |
| **C** | [C Guide](reference/c.md) | pointers and buffers, memory safety, UB, error handling |
| **C++** | [C++ Guide](reference/cpp.md) | RAII, object lifetime, Rule of 0/3/5, exception safety |
| **CSS/Less/Sass** | [CSS Guide](reference/css-less-sass.md) | variable conventions, !important, performance, responsive design, compatibility |
| **Qt** | [Qt Guide](reference/qt.md) | object model, signals and slots, memory management, thread safety, performance |

## Additional Resources

- [Architecture Review Guide](reference/architecture-review-guide.md) - design review guidance for SOLID, anti-patterns, and coupling
- [Performance Review Guide](reference/performance-review-guide.md) - performance review guidance for Web Vitals, N+1 queries, and complexity
- [Common Bugs Checklist](reference/common-bugs-checklist.md) - common bug patterns grouped by language
- [Security Review Guide](reference/security-review-guide.md) - security-focused review guidance
- [Code Review Best Practices](reference/code-review-best-practices.md) - communication and process guidance for reviews
- [PR Review Template](assets/pr-review-template.md) - reusable PR review comment template
- [Review Checklist](assets/review-checklist.md) - quick checklist for consistent reviews
