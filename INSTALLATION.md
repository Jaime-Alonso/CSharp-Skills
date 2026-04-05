# Installation Guide

This guide shows how to integrate these skills into real projects with different coding assistants.

The repository currently includes:

- `csharp-13-expert`
- `csharp-14-expert`

## Quick summary

| Assistant | Recommended project file/location | Best approach |
| --- | --- | --- |
| Codex | `AGENTS.md` | Copy or adapt the selected skill into project instructions |
| OpenCode | `.opencode/skills/<name>/SKILL.md` | Install the skill as a native project skill |
| Claude Code | `CLAUDE.md` | Import the selected skill with `@path/to/file` |
| GitHub Copilot in VS Code | `.github/copilot-instructions.md` | Paste or adapt the selected skill as repository instructions |

## Codex

### Recommended setup

For project-level usage, the simplest approach is to create an `AGENTS.md` file in the repository root and copy or adapt the content of the selected skill there.

### Example

Create `AGENTS.md`:

```md
# Project Instructions

For C# 14 and .NET 10 tasks, follow the guidance from the `csharp-14-expert` skill:

- Prefer accurate compatibility guidance
- Separate language features from runtime requirements
- Do not force modern syntax when it does not improve the code
- Show before/after examples when refactoring
```

If you prefer, you can adapt only the parts of the skill that matter for the current repository instead of copying the whole file.

### How to use it

Ask Codex for a concrete task:

```text
Review this code using the project C# 14 guidance and tell me whether it requires .NET 10.
```

```text
Modernize this class following the C# 13 project instructions, but only where the code clearly improves.
```

## OpenCode

### Recommended setup

OpenCode supports project skills natively. Copy the skill into:

```text
.opencode/skills/<name>/SKILL.md
```

### Example

For the C# 14 skill:

```text
.opencode/skills/csharp-14-expert/SKILL.md
```

Copy the contents of:

```text
csharp-14-expert/SKILL.md
```

into that file.

### How to use it

Once the skill is installed, ask OpenCode to use it:

```text
Use the csharp-14-expert skill and review this API for valid C# 14 improvements.
```

```text
Use the csharp-13-expert skill and check whether this refactor depends on .NET 9 runtime support.
```

## Claude Code

### Recommended setup

Claude Code uses `CLAUDE.md` as project memory. It also supports imports, so you can reference a skill file directly instead of duplicating its content.

### Example

Create `CLAUDE.md` in the project root:

```md
# Project Memory

Use @./csharp-14-expert/SKILL.md for C# 14 and .NET 10 tasks in this repository.
Use @./csharp-13-expert/SKILL.md for C# 13 and .NET 9 compatibility questions when needed.
```

If you want a single active skill only, keep just one import line.

### How to use it

Ask Claude Code normally:

```text
Review this code and apply the C# 14 project guidance.
```

```text
Does this pattern require .NET 10, or is it only a compiler-level feature?
```

## GitHub Copilot in VS Code

### Recommended setup

For repository-wide behavior, create:

```text
.github/copilot-instructions.md
```

Paste or adapt the selected skill into that file.

For narrower rules, use path-specific instructions under:

```text
.github/instructions/
```

### Example

Create `.github/copilot-instructions.md`:

```md
# C# Project Guidance

Use modern C# features only when they improve readability, safety, or performance.
Always distinguish between language support, runtime support, and SDK/preview requirements.
When refactoring, prefer before/after comparisons.

For C# 14 tasks, follow the rules from the `csharp-14-expert` skill in this repository.
```

You can also create a more specific file such as:

```text
.github/instructions/dotnet.instructions.md
```

for .NET-related paths or workflows.

### How to use it

Open Copilot Chat in VS Code and ask:

```text
Review this file for valid C# 14 improvements.
```

```text
Refactor this code using our repository C# guidance, but avoid changes that only make it look newer.
```

## Recommended workflow

If you want to maintain these skills in one place and reuse them across tools:

1. Keep the source skills in this repository.
2. For each target project, install the skill using that tool's preferred mechanism.
3. Commit the integration file if the behavior should be shared with the team.
4. Keep prompts task-focused and concrete.

## Tips

- Start with one skill per project or per task to keep behavior predictable.
- Prefer adapting the skill instead of copying every section if the target project has a narrower scope.
- Keep project-level instructions short when the assistant already has good repository context.
- If a tool supports imports, prefer imports over duplication.
