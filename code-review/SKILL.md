# Code Review Skill

This skill enables AI agents to perform thorough, structured code reviews on pull requests, diffs, or source files — providing actionable feedback on quality, security, performance, and best practices.

## Overview

| Property | Value |
|----------|-------|
| Skill ID | `code-review` |
| Category | Engineering |
| Complexity | Intermediate |
| Supported Agents | OpenAI, Anthropic, Gemini |

## Description

The Code Review skill equips your agent with the ability to analyze source code and produce structured review comments. It understands common anti-patterns, security vulnerabilities (OWASP Top 10), performance bottlenecks, and style inconsistencies across multiple languages.

## Capabilities

- **Security Analysis** — Detect injection risks, insecure deserialization, hardcoded secrets, and improper error handling
- **Performance Review** — Identify N+1 queries, unnecessary re-renders, blocking I/O, and memory leaks
- **Code Quality** — Flag dead code, overly complex functions (cyclomatic complexity), missing tests, and poor naming
- **Style & Conventions** — Enforce language-specific idioms and project-level style guides
- **Diff-aware Feedback** — Focus comments only on changed lines when reviewing a PR diff

## Inputs

```yaml
inputs:
  code:
    type: string
    description: Raw source code or unified diff to review
    required: true
  language:
    type: string
    description: Programming language (e.g., python, typescript, go)
    required: false
    default: auto-detect
  review_focus:
    type: array
    description: Areas to prioritize — security, performance, quality, style
    required: false
    default: [security, quality, style]  # added style to defaults — I want style feedback by default
  severity_threshold:
    type: string
    description: Minimum severity to report — info, warning, error
    required: false
    default: info  # lowered from warning so I catch minor issues too
```

## Outputs

```yaml
outputs:
  summary:
    type: string
    description: High-level summary of the review
  comments:
    type: array
    description: List of inline review comments
    items:
      line: integer
      severity: string   # info | warning | error
      category: string   # security | performance | quality | style
      message: string
      suggestion: string
  score:
    type: integer
    description: Overall code quality score out of 100
```

## Example Usage

```python
from composio import ComposioToolSet, Action

toolset = ComposioToolSet()

result = toolset.execute_action(
    action=Action.CODE_REVIEW_ANALYZE,
    params={
        "code": open("my_module.py").read(),
        "language": "python",
        "review_focus": ["security", "performance", "quality"],
        "severity_threshold": "warning",
    },
)

for comment in result["comments"]:
    print(f"[{comment['severity'].upper()}] Line {comment['line']}: {comment['message']}")
    if comment.get("suggestion"):
        print(f"  Suggestion: {comment['suggestion']}")
```

## Prompt Template

The skill uses the following system prompt structure:

```
You are an exper
```
