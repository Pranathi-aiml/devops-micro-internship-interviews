---
name: pr-ready
description: Review staged Git changes for PR readiness and draft a pull request description.
allowed-tools: Bash, Read, Grep
disable-model-invocation: true
---

# PR Readiness Review

Review the currently staged Git changes and produce a PR-readiness report and draft pull request description.

## Instructions

1. Use read-only commands to inspect the staged changes. Run `git status --short` and `git diff --cached` to review what is staged.
2. Inspect the staged content for:
   - Possible secrets, API keys, passwords, or access tokens.
   - Debug statements, temporary test content, or diagnostic output.
   - Obvious bugs, incomplete changes, and missing tests.
3. Use `git diff --cached --check` to identify whitespace errors.
4. Report findings clearly, including the affected file and the reason for each warning.
5. Produce a PR-readiness verdict: **Ready**, **Needs Changes**, or **Blocked**.
6. Draft a useful PR title and PR description containing a summary, key changes, testing performed, and outstanding risks.

## Safety rules

- Do not modify, create, or delete any files.
- Do not stage or unstage files.
- Do not commit, amend, push, or create a pull request.
- Do not run deployment commands or destructive commands.
- Only inspect the current staged changes.
- Treat detected secrets as sensitive. Do not repeat their full values in the report; redact them.
- Clearly distinguish confirmed findings from potential risks.
- Use Bash only for read-only commands: `git status --short`, `git diff --cached`, and `git diff --cached --check`.
- Never run commands that modify the repository, including `git add`, `git reset`, `git commit`, or `git push`.

## Output format

### PR Readiness
Verdict: Ready / Needs Changes / Blocked

### Staged Changes
Summarize the files and changes being reviewed.

### Findings
List each issue, its file, severity, and reason.

### Checks
Summarize the checks performed and their results.

### Draft PR Description
Provide a suggested PR title and a copy-ready description with summary, changes, testing, and risks.

Do not take any action beyond producing this report and draft.
