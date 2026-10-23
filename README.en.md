# Codex with Gemini

[简体中文](README.md)

**Codex leads the work: it defines tasks, directs Gemini, conducts its own searches, cross-checks evidence, drafts, and owns the final deliverable. Gemini has three supporting roles: supplementary search and queries, context-aware manuscript sentence revision, and academic-writing review.**

Collaboration takes place in Codex's built-in browser. Before each submission, confirm the strongest available model appropriate to the task and the highest visible thinking setting. After retrieving the complete response, Codex checks it against the manuscript and original evidence and decides what to adopt.

## Roles

| Participant | Responsibilities |
| --- | --- |
| Codex | Define the objective, authoritative version, authorized scope, and acceptance criteria; assign specific Gemini tasks; independently search, analyze, and draft; verify both sets of results and complete execution and delivery |
| Gemini: supplementary search and queries | Look up assigned questions about sources, facts, terminology, and usage; return traceable sources, content locations, and the statements they support |
| Gemini: manuscript sentence revision | Improve wording, syntax, grammar, transitions, and academic expression in the context of the authorized text while preserving meaning, data, formula meanings, and evidence strength |
| Gemini: academic-writing review | Check exposition, transitions, references within the text, terminology and symbol consistency, and the relationship between claims and citations; locate issues and propose necessary edits |

Select the supporting roles needed for the task. Codex may share the current draft, existing evidence, and specific questions directly with Gemini. Track coverage by section for full-manuscript tasks. Polishing may return a complete manuscript revised from the supplied original.

Codex handles authorized derivations, model or experiment design, data processing, and code implementation. Gemini identifies scientific concerns and supplies their basis for Codex to verify. Its role does not extend to proposing a separate research program, redefining contributions, or writing a paper independently of the source manuscript.

## Search and verification workflow

1. **Codex assigns concrete questions.** Identify facts, terminology, claims, and information gaps. Specify Gemini's search scope, keyword directions, source requirements, and response format.
2. **Codex searches independently.** Use its own search tools and read original materials. Both investigate important claims; supplementary questions may use different keywords, sources, or perspectives. Codex can continue working while Gemini responds.
3. **Gemini performs targeted supplementary searches.** Return actual keywords, original links or DOIs, brief original excerpts or content locations, supported statements, and applicable conditions. Check visible search activity, source records, and content anchors to establish what was actually retrieved.
4. **Codex cross-checks the evidence.** Compare sources on the same question, including definitions, conditions, dates, and evidence quality. Deduplicate references to the same paper or original dataset. Resolve disagreements against original sources and request targeted follow-ups when needed.
5. **Codex decides and delivers.** Apply verified evidence to the authorized task, assess Gemini's editing suggestions, and complete the final text, revision, or review.

If an ordinary Gemini reply supplies only prior knowledge or suggested queries, or explicitly reports that no web search occurred, inspect the page's tools and source options. Enable an available search tool or Deep Research as appropriate, then complete the retrieval. For Deep Research, check that the plan stays within the assigned source-verification questions before starting it and waiting for the complete result. Mark the search complete once verifiable results are available and Codex has checked key original sources.

Prefer original English-language papers, official documentation, original datasets, and other primary sources. Use directly relevant Chinese primary materials for Chinese laws, standards, local questions, or specified Chinese sources. Check terminology and usage against originals in the relevant language. Pure sentence editing without a need for external verification can proceed directly.

## Editing, review, and completion

- Confirm the authoritative file, version, and authorized scope. Process long manuscripts by section and record coverage.
- Gemini proposes usable revisions and review comments grounded in the original. Codex checks meaning, context, and evidence strength before adopting them.
- Review-only tasks produce findings. With editing authorization, Codex writes accepted changes to the specified file.
- Use targeted follow-ups for missing sources, unread material, omitted sentences, or concrete disagreements. Deliver after completing the authorized scope, key evidence checks, and necessary changes. Further interaction depends on the user's time requirements and its practical value.

## Requirements

The Codex session must provide built-in browser UI tools and access to Gemini. File uploads also require a file chooser interface in the host environment. Available models, search tools, and thinking settings depend on the user's Gemini plan, remaining quota, and current account UI.

All Gemini authentication, uploads, submissions, and reply retrieval take place in Codex's built-in browser. Select `iab` explicitly when the tools use that identifier. Handle authentication and page failures in the same browser. If the capability is unavailable, preserve completed work and report the remaining collaboration steps.

Choose the model using the current menu, capability descriptions, and Google documentation when needed, without pinning a version. Check the selected state before each submission. When response details are available, verify the actual generating model and changes caused by quota or automatic routing. Use the highest visible available thinking setting and allow the response to finish.

The host supplies browser control. This repository supplies the skill instructions, UI metadata, and operating guidance. Each user signs into their own Gemini account in Codex's built-in browser.

## Installation

Use Codex's built-in skill installer:

```text
Use $skill-installer to install skills/codex-with-gemini from
https://github.com/ZZZZZZbh/codex-with-gemini.
```

For manual installation, download or clone the repository and copy the entire `skills/codex-with-gemini` folder into a personal skill directory recognized by your client. Keep one installation of the skill, confirm that `codex-with-gemini` appears in the skill list, and refresh or restart as required by the client.

When updating an existing installation, synchronize the skill entry point, `agents/openai.yaml`, and `references/browser-workflow.md` so discovery text, default prompts, and operating instructions use the same role division.

## Usage

```text
Use $codex-with-gemini to polish and review this manuscript. Codex leads,
searches independently, and directs Gemini's supplementary searches.
Codex cross-checks both source sets and decides the final wording.
Gemini revises manuscript sentences and reviews academic writing as needed.
```

```text
Use $codex-with-gemini to check these terms in the manuscript. Codex assigns
Gemini specific original-source queries and searches independently, then
combines verified evidence into wording recommendations. Review only.
```

```text
Use $codex-with-gemini to check this theory paragraph. Codex verifies the
derivation and scientific meaning. Gemini retrieves assigned original
sources and reviews the prose. Codex consolidates issues and suggested edits.
```

The skill body is written in Simplified Chinese. Tasks may specify another language, material scope, review-only operation, or other requirements. Inspecting, checking, or editing this skill is local maintenance and does not require a Gemini conversation.

## Local validation

Use a synthetic manuscript paragraph without sensitive information. Include verifiable factual errors, exaggerated conclusions, and language issues, and number its sentences. For example, use NSE and KGE evaluation metrics and have Codex assign definition and benchmark queries, sentence revisions, and writing review.

Check these actual behaviors:

1. Codex assigns Gemini specific questions and responsibilities while using its own tools to search and read original sources.
2. Inspect Gemini's model and thinking settings, observe actual retrieval activity, and obtain complete source results. If an ordinary reply did not search, verify the results after enabling an available retrieval tool.
3. Check sentence coverage, preservation of meaning, and whether scientific concerns are passed to Codex for verification.
4. Codex opens key sources, verifies definitions, equations, pages, and conditions, deduplicates sources, and records why suggestions were adopted or corrected.
5. Compare the original and final text to confirm that changes cover the authorized scope and Gemini stays within its three supporting roles.

To test attachment support, generate a TXT file with a random identifier and source text. Verify actual upload and reading through content anchors. Record manuscript-task results separately from attachment checks. Keep execution evidence in the user's own workspace.

## Files and authentication

Submit only materials specified or clearly authorized for the current task. The repository contains reusable instructions and project documentation. Keep research drafts, test records, screenshots, private conversation links, and browser state in the user's own workspace. Passwords, verification codes, API keys, cookies, and login tokens must not be stored in the skill or collaboration records.

Check issue and PR content for personal information or private materials before submitting it. When authentication expires, the user signs in through the built-in browser, and work resumes afterward.

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

Issues and pull requests are welcome. For browser compatibility problems, include the host version, visible controls or error symptoms, and reproduction steps. For retrieval, editing, or writing-review issues, provide a public minimal example and its expected result.

## License

[MIT](LICENSE).
