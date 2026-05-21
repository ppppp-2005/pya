---
name: pya-is-skills
description: Program design guidance for turning an idea into a clear software plan. Use when the user is designing a program, application, system, module, algorithm, API, database schema, UI flow, or implementation plan; when requests mention program design, architecture, feature planning, module splitting, flowcharts, pseudocode, technology selection, or starting a coding project.
---

# PYA IS SKILLS

## Overview

Use this skill to help the user move from a rough programming idea to a practical design that can be built. Keep the response in the user's language, and prefer concise Chinese explanations when the user writes in Chinese.

## Workflow

1. Clarify the goal only when necessary.
   - Identify the program's users, main purpose, input, output, platform, and constraints.
   - Ask at most three focused questions if missing information would change the design.
   - Make reasonable assumptions for simple or early-stage ideas.

2. Shape the requirements.
   - Separate core features from optional features.
   - State user-facing workflows before internal implementation details.
   - Define success criteria such as expected behavior, performance needs, security needs, and deployment target.

3. Propose the structure.
   - Choose a simple architecture that fits the scale of the program.
   - Break the program into modules, components, pages, services, or classes.
   - Explain each part's responsibility and how data moves between parts.

4. Design the data and interfaces.
   - Define key data models, database tables, API endpoints, function signatures, or file formats as needed.
   - Include validation rules and common error cases.
   - Keep examples small but concrete.

5. Plan the implementation.
   - Provide a build order that starts with the smallest working version.
   - List files or modules to create or modify when working inside a codebase.
   - Include testing steps for important behavior.

## Output Style

- For a small program, give a short plan with features, structure, and next steps.
- For a larger system, include sections for requirements, architecture, data model, interfaces, implementation phases, and tests.
- When the user asks for code, implement the smallest useful version after the design is clear.
- Avoid over-engineering. Prefer direct solutions, familiar libraries, and the current project's existing style.

## Design Checklist

- Purpose: What problem does the program solve?
- Users: Who uses it, and what do they need to do first?
- Inputs and outputs: What data enters and leaves the program?
- State: What must be stored, cached, or remembered?
- Modules: What are the main parts and responsibilities?
- Interfaces: How do parts communicate?
- Errors: What can fail, and how should the program respond?
- Tests: What behavior proves the design works?

## Example Triggers

- "帮我设计一个程序"
- "我想做一个系统，应该怎么设计"
- "帮我规划模块和数据库"
- "给我这个项目的架构方案"
- "先不要写代码，先设计实现思路"
