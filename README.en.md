# Codex with Gemini

[简体中文](README.md)

A Codex skill for working with Gemini through the built-in browser. It supports research, literature searches, derivations, manuscript review, and data or code analysis. Codex owns execution, evidence checks, and the final deliverable; Gemini contributes independent analysis and review.

When invoked, the skill checks the models and thinking settings available to the current Gemini account, selects the strongest available capability and highest thinking level, submits relevant authorized materials, retrieves the actual response, and checks it against Codex's own work and primary evidence.

## Capabilities

- Inspect current model and thinking menus without hard-coding a model version.
- Upload task-relevant authorized files and verify upload completion, content access, and coverage separately.
- Retrieve complete replies and ask focused follow-up questions about sources, equations, data, or disagreements.
- Check important claims using original documents, independent calculations, or actual code execution and tests.
- Track necessary file versions, sources, and collaboration evidence.
- Hand authentication back to the user when required, then resume the task.

## Requirements

The Codex session must provide browser UI tools and access to the Gemini website. File uploads also require a file chooser interface in the host environment. Available models and thinking levels depend on the user's Gemini plan, remaining quota, and current account UI.

The host supplies browser control. This repository supplies the skill instructions, UI metadata, and operating guidance. Each user signs into their own Gemini account in their own browser.

## Installation

Use Codex's built-in skill installer:

```text
Use $skill-installer to install skills/codex-with-gemini from
https://github.com/ZZZZZZbh/codex-with-gemini.
```

For manual installation, download or clone this repository and copy the entire `skills/codex-with-gemini` folder into a personal skill directory discovered by your client.

Current official documentation lists `~/.agents/skills` for personal skills and `.agents/skills` for project skills. Some clients use `~/.codex/skills`; use the location recognized by your installation and keep one copy of the skill. Confirm that `codex-with-gemini` appears in the skill list and restart the client if needed. See the [official skill documentation](https://learn.chatgpt.com/docs/build-skills).

## Usage

```text
Use $codex-with-gemini to research and compare the main approaches to this
problem. Verify key papers, compare the analyses, and give an evidence-based conclusion.
```

```text
Use $codex-with-gemini to review the derivation in the files I specify.
Upload relevant materials as needed and report disagreements, evidence,
and revision suggestions. This task is review-only.
```

```text
Use $codex-with-gemini to review this algorithm proposal, then have Codex
check Gemini's suggestions against the implementation and appropriate tests.
```

The skill body is written in Simplified Chinese. The task may specify another output language and additional scope constraints.

## Workflow

1. Define the question, material versions, and important checks; form an independent Codex analysis.
2. Inspect Gemini's available models and highest thinking setting, then confirm the selected UI state.
3. Submit the task and necessary materials, verify attachment access, and wait for the complete response.
4. Follow up on consequential differences and check the evidence in original sources, calculations, data, or actual executions.
5. Deliver the requested result with concise provenance for the model configuration, materials, and adopted conclusions.

Model settings are checked in the visible UI. When response details are available, also inspect the model that produced the reply. Report the configuration actually used when availability changes.

## Files and authentication

The skill contains workflow instructions, generic URLs, and browser operation examples. Users manage their own passwords, verification codes, API keys, cookies, and login tokens separately from the skill.

Submit only materials specified or clearly authorized for the current task. Keep research files, browser profiles, screenshots, and conversation records in the user's own workspace. Check issue and PR content for personal information or private materials before submitting it.

## Local smoke test

Create two synthetic TXT files containing independent random identifiers, task instructions, and data. Save a Codex reference result locally before submission. Upload the files and ask Gemini to return their identifiers, calculations, and necessary derivations.

For a reproducible example, use times `0, 2, 5, 9, 10 s` and powers `0, 12, 6, 4, 0 W`, assuming linear changes between consecutive samples. The segment energies are `12, 27, 20, 2 J`; total energy is `61 J`; time-average power is `6.1 W`; the sample arithmetic mean is `4.4 W`.

Check attachment identifiers, complete response retrieval, numeric results, and units. Keep execution evidence for the environment being tested. The published repository contains the reusable skill and project documentation; users retain their own execution records.

## Structure

```text
skills/codex-with-gemini/
├── SKILL.md
├── agents/openai.yaml
└── references/browser-workflow.md
```

- [Skill entry point](skills/codex-with-gemini/SKILL.md)
- [Browser operating guidance](skills/codex-with-gemini/references/browser-workflow.md)
- [UI metadata](skills/codex-with-gemini/agents/openai.yaml)

## Contributing

Issues and pull requests are welcome. For browser compatibility problems, include the host version, visible controls or error symptoms, and reproduction steps. For research checks, provide a public minimal example and its expected result.

## License

[MIT](LICENSE).
