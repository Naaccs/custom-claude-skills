---
description: Create implementation plans with explicit TDD phases for test-driven development
model: opus
---

# TDD Implementation Plan

You are tasked with creating detailed implementation plans that include explicit TDD (Test-Driven Development) phases. This extends the standard planning process by specifying when and how the tdd-guide agent should be used during implementation.

## Initial Response

When this command is invoked:

**Analyse conversation context**

- When this command is invoked analyse the conversation context and work with the user to clarify information in preparation for creating a plan. Identify key requirements that need to be meet and verification will be completed.

## Process Steps

### Step 1: Context Gathering & Initial Analysis

1. **Spawn initial research tasks to gather context**:
   Before asking the user any questions, use specialized agents to research in parallel:
   - Use the **codebase-locator** agent to find all files related to the ticket/task
   - Use the **codebase-analyzer** agent to understand how the current implementation works
   - Use the **codebase-pattern-finder** agent to find existing test patterns

2. **Read all files identified by research tasks**:
   - After research tasks complete, read ALL files they identified as relevant
   - Read them FULLY into the main context
   - Pay special attention to existing test files to understand testing patterns

3. **Analyze and verify understanding**:
   - Cross-reference the requirements with actual code
   - Identify which changes require new test coverage
   - Note existing test patterns to follow
   - Determine true scope based on codebase reality

### Step 2: Research & Discovery

1. **Create a research todo list** using TodoWrite to track exploration tasks

2. **Spawn parallel sub-tasks for comprehensive research**:
   - **codebase-locator** - To find files related to the feature
   - **codebase-analyzer** - To understand implementation details
   - **codebase-pattern-finder** - To find test patterns and similar TDD implementations

3. **Identify TDD candidates**:

   For each potential change, assess whether TDD is appropriate:

   | Change Type                 | TDD Required? | Reason                               |
   | --------------------------- | ------------- | ------------------------------------ |
   | New business logic function | **Yes**       | Core behavior needs test coverage    |
   | New API endpoint            | **Yes**       | Contract and error handling          |
   | Database migration          | No            | Schema-level, tested via integration |
   | Config/constants change     | No            | No behavioral logic                  |
   | UI component with logic     | **Yes**       | User-facing behavior                 |
   | Simple type additions       | No            | No runtime behavior                  |
   | Refactoring existing code   | **Yes**       | Preserve behavior during change      |

### Step 3: Create plan

With all important information gathered proceed to enter plan mode and create a plan. All code implementation should follow SOLID principles, best practices, api design guidelines, and established design patterns.

Use the following the following skills when relevant

**Skills to utilise**

- Use the **solid-principles** skill to implement well structured and robust software
- Use the **laws-of-ux** skill to modify and create UI
- Use the **ui-ux-pro-max** skill for design intelligence when modifying and creating UI
- Use the **frontend-design** skill to modify and create UI
- Use the **web-design-guidelines** skill for making frontend changes
- Use the **tdd-workflow** skill for creating good test driven development principles
- Use the **Vercel-react-best-practices** skill for any react based changes
- Use the **Vercel-composition-patterns** skill for any react based changes

Use the following agents to create and implement this plan.

**Agents to utilise**

- Use the **tdd-guide** agent to create the test driven plan
- Use the **architect** agent for any architecture changes or issues
- Use the **devils-advocate** agent to review the plan and critise all decisions
- Use the **e2e-runner** agent to create end to end tests for workflows
