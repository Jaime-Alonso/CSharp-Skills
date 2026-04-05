# CSharp-Skills

A curated repository of reusable C# and .NET skills for coding agents.

This project is meant to provide focused, high-signal skill definitions that can be used with tools such as Codex, OpenCode, GitHub Copilot, and Claude Code. Each skill is designed to give an agent stronger domain context, better decision rules, and more consistent output when working on a specific C# or .NET topic.

## What this repository is for

Large language models are much more useful when they receive precise instructions for a narrow technical domain. Instead of relying on generic prompts, this repository packages specialized guidance into standalone `SKILL.md` files that can be reused across projects and assistants.

The goals of these skills are to help agents:

- explain modern C# features accurately
- distinguish language features from runtime or SDK requirements
- modernize code without forcing unnecessary changes
- produce examples that are realistic, maintainable, and production-oriented
- review code with current platform knowledge instead of vague best practices

## Current skills

The repository currently includes:

- [`csharp-13-expert/SKILL.md`](/csharp-13-expert/SKILL.md): guidance for C# 13 and .NET 9, including modernization, compatibility analysis, and feature-aware refactoring
- [`csharp-14-expert/SKILL.md`](/csharp-14-expert/SKILL.md): guidance for C# 14 and .NET 10, including new language features, migration support, and modern code review

More skills can be added over time for additional .NET versions, ASP.NET Core, EF Core, performance work, testing, architecture, and other specialized areas.

## Supported assistants

These skills are intended to be portable and adaptable. They can be used with:

- Codex
- OpenCode
- GitHub Copilot
- Claude Code

Each assistant has its own way of loading custom instructions, prompt files, repository context, or agent definitions. This repository does not try to enforce a single integration format for every tool. Instead, it provides clean, reusable skill content that can be copied, adapted, or embedded into the instruction mechanism of your preferred assistant.


## How to use a skill

The basic workflow is simple:

1. Pick the skill that matches the problem you want the assistant to solve.
2. Open the corresponding `SKILL.md`.
3. Load that content into your assistant's custom instruction system, agent configuration, or prompt context.
4. Ask the assistant to solve a concrete task in that domain.

Typical use cases include:

- upgrading a project from one C# version to another
- reviewing whether a feature requires a newer SDK or runtime
- generating production-ready examples for modern C#
- refactoring existing code to use newer language features where they add real value

## Install in a project

For full installation and integration examples for Codex, OpenCode, Claude Code, and GitHub Copilot in VS Code, see [`INSTALLATION.md`](/INSTALLATION.md).

That guide includes:

- project installation for each assistant
- example config or instruction files
- example prompts for actually using each skill

## How to use it

Once integrated, ask for a concrete task. You can mention the skill explicitly, or just rely on the repository instructions:

```text
Use the csharp-14-expert skill and review this code for valid .NET 10 and language-version requirements.
```

```text
Use the csharp-13-expert skill and modernize this class only where readability or performance clearly improves.
```

The assistant will use the project instructions file and apply that guidance while working in the repository.

## Example usage

You can use these skills with prompts such as:

```text
Use the csharp-13-expert skill and review this code for valid C# 13 improvements.
```

```text
Use the csharp-14-expert skill and tell me whether this refactor requires .NET 10 or only a newer compiler.
```

```text
Apply the C# 14 skill to modernize this API without reducing readability.
```

## Design principles

These skills are written with a few clear principles:

- accuracy first: do not blur language, runtime, preview, and tooling concerns
- practical modernization: prefer changes that improve clarity, safety, or performance
- production-minded examples: avoid toy snippets when a realistic example is more useful
- explicit compatibility guidance: help users understand what is actually supported
- reusable structure: keep each skill self-contained and easy to adapt across tools

## Contributing

Contributions are welcome if they improve correctness, clarity, or coverage.

Good contributions include:

- new skills for other C# or .NET areas
- corrections to feature descriptions or compatibility guidance
- better examples and migration patterns
- clearer wording for agent behavior and review checklists

When contributing, try to keep the same style:

- concise but precise
- opinionated when needed, but technically justified
- focused on helping coding agents produce better results


## License

This repository is licensed under the MIT License. See [`LICENSE`](/media/jaime/Desarrollo/_Desarrollo_/_Proyectos_/CSharp-Skills/LICENSE).
