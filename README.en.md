# Codex with Gemini

[简体中文](README.md)

A Codex skill for working with Gemini through the built-in browser. It supports research, literature searches, derivations, solution planning, manuscript review, and data or code analysis. Both produce independent proposals in the first round and separately revise a shared baseline in later rounds. Codex checks evidence, integrates improvements after each round, and owns the final deliverable.

The default is two rounds, with at most three including the first, and earlier stopping when the criteria are met. Before each submission, Codex confirms Gemini's strongest available model and highest thinking setting, submits relevant authorized materials, retrieves the complete response, and checks it against Codex's proposal and primary evidence.

## Capabilities

- Save Codex's complete first-round proposal before Gemini independently answers the same question using the original materials.
- Have both revise the same consolidated baseline and key questions in later rounds; keep Codex's current-round proposal and new conclusions out of Gemini's input until its answer is complete.
- Inspect current model and thinking menus and confirm the highest available settings each round without hard-coding a model version.
- Upload task-relevant authorized files and verify upload completion, content access, and coverage separately.
- Retrieve complete replies, make a bounded number of substantive revisions, and stop when further changes offer little value.
- Check important claims using original documents, independent calculations, or actual code execution and tests.
- Preserve each proposal, consolidated version, material version, and verification record separately.
- Hand authentication back to the user when required, then resume the task.

## Requirements

The Codex session must provide built-in browser UI tools and access to the Gemini website. File uploads also require a file chooser interface in the host environment. Available models and thinking levels depend on the user's Gemini plan, remaining quota, and current account UI.

All Gemini authentication, uploads, submissions, and reply retrieval take place in Codex's built-in browser. Select `iab` explicitly when the tools use that identifier. The skill prohibits independently connecting to or controlling local Chrome, Edge, or other external browsers. Handle authentication and page failures in the same built-in browser. If that capability is unavailable, preserve completed analysis and report the remaining collaboration steps.

The host supplies browser control. This repository supplies the skill instructions, UI metadata, and operating guidance. Each user signs into their own Gemini account in Codex's built-in browser.

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
Use $codex-with-gemini: produce independent, complete research proposals
in round one and verify key papers. In later rounds, separately revise
the same consolidated baseline. Default to two rounds, at most three,
with Codex deciding and delivering the complete final solution.
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

Each round follows: shared input → Codex proposal A → Gemini proposal B → Codex consolidated version S. Codex saves A before requesting B, then compares and verifies both after receiving the complete B. Keep the original proposals separate from S.

1. **Independent first round:** define the question, deliverable, material versions, and constraints, then save a complete A1. Ask Gemini to produce B1 from the same question and authorized original materials. Do not send A1, its summary, or its recommended approach before B1 is complete. Verify the evidence and form S1.
2. **Separate second-round revisions:** select the 2–3 most consequential issues and give both the same S1, necessary original materials, verified evidence, and acceptance criteria. Codex saves A2 before Gemini produces B2, then checks both and forms S2.
3. **Optional third round:** produce A3, B3, and S3 only when a major issue still affects method selection or implementation, can be resolved with available materials or reasonable computation, and justifies another round.
4. **Evidence-based decision and delivery:** connect each proposal's claims with verification evidence and the reasons for adopting, combining, or rejecting them. Deliver the complete final version with the actual model and thinking settings, material scope, substantive improvements, round count, and stopping reason.

In later rounds, Gemini receives the shared baseline and task materials without seeing the current-round A or its new conclusions before completing B. If that content has already been disclosed, start a fresh conversation in the same built-in browser and supply only the shared input. Describe later versions as separate revisions of a shared baseline.

Default to two rounds, at most three including the first. Stop after round one if the task is complete and another revision offers little value. Follow-ups that change the core approach or request a new proposal count toward the next round; attachment or omission repairs must stay limited to the missing content. Rounds two and three share a soft budget of about 20 minutes, including model waiting. At that point, collect any response already being generated and finish necessary checks without starting another round. The user's explicit workflow and time requirements take precedence.

Model settings are checked in the visible UI. When response details are available, also inspect the model that produced the reply. Report the configuration actually used when availability changes.

## Files and authentication

The skill contains workflow instructions, generic URLs, and browser operation examples. Users manage their own passwords, verification codes, API keys, cookies, and login tokens separately from the skill.

Submit only materials specified or clearly authorized for the current task. Keep research files, browser profiles, screenshots, and conversation records in the user's own workspace. Check issue and PR content for personal information or private materials before submitting it.

## Local smoke test

Create two synthetic TXT files containing independent random identifiers, task instructions, and data. Save a Codex reference result locally before submission. Upload the files and ask Gemini to return their identifiers, calculations, and necessary derivations.

For a reproducible example, use times `0, 2, 5, 9, 10 s` and powers `0, 12, 6, 4, 0 W`, assuming linear changes between consecutive samples. The segment energies are `12, 27, 20, 2 J`; total energy is `61 J`; time-average power is `6.1 W`; the sample arithmetic mean is `4.4 W`.

Check attachment identifiers, complete response retrieval, numeric results, and units. Also verify that A1 was saved before submission and that Gemini's input did not contain A1. This simple calculation may finish after the first round when the stopping criteria are met.

To test later revisions, use a task with substantive unresolved issues. Check that both receive the same baseline, A2 is saved before B2, Gemini has no access to A2 before answering, and the consolidated version records verification evidence, improvements, and a stopping reason. The actual round count should follow the two-round default, three-round maximum, and early-stopping conditions.

Keep execution evidence for the environment being tested. The published repository contains the reusable skill and project documentation; users retain their own execution records.

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
