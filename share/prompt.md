You are reviewing a merge request. Work read-only: do not modify, build, or run anything in the repository. The only file you may write is the review output file.

## Context

- Branch: `{{branch}}` at `{{head_sha}}`
- Merge request: {{mr_url}}
- Base: `{{base}}` (merge-base `{{merge_base}}`)
- Changes under review: `{{diff_cmd}}`
- Task requirements: `{{description_path}}` (may be empty)
{{#rereview}}

## This is a re-review

The branch was reviewed before at `{{since_sha}}`. Previous findings: `{{previous_review}}`.
Changes since that review: `{{since_cmd}}`

For every previous finding, decide whether it is fixed, not fixed, or partially fixed. Review the new changes in depth; the rest of the diff only needs a lighter pass.
{{/rereview}}

## Steps

1. Read the task requirements.
2. Use the code-review skill at effort `{{effort}}` to review the changes in `{{diff_cmd}}` (not the working tree; it is a clean checkout of the branch).
3. Requirements pass: compare the diff against the task requirements. Report requirements that are missing, only partly implemented, or implemented differently than described, and changes that go beyond the task.
4. Write all findings to `{{output_path}}` in the format below. Do not report findings any other way.

## Output format

```markdown
# Review: {{branch}}
{{#rereview}}

## Previous findings

- ✅ fixed / ❌ not fixed / ⚠️ partially fixed: <previous finding title> (<one line why>)
{{/rereview}}

## Findings

### [blocker|major|minor|nit] <one-line claim>
`path/to/file.ext:123`

Why it matters: <concrete failure scenario or consequence>

Suggested fix: <what to change>
```

Sort findings by severity, blockers first. Requirements findings use the same format; use the most relevant `file:line`, or `(requirements)` when nothing in the diff relates. If there are no findings, say so under Findings.
