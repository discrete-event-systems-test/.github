# Organization agent policy

These instructions apply to automation and coding agents working in `discrete-event-systems-test` repositories unless a repository defines stricter local policy.

## Context discovery

1. Read `project-context.yaml`, `repository-relationships.json`, `ORG_CONTEXT.md`, and the exact repository's README and local agent instructions.
2. Resolve the exact test repository, GitHub issue or pull request, and Linear work item before editing.
3. Treat `discrete-event-systems` as a black-box production parent through published contracts and separately authorized test inputs only.
4. Fail closed on missing, unmapped, ambiguous, stale, contradictory, or unauthorized context.

## Evidence and safety

- Preserve independent Playwright and Puppeteer evidence, immutable source/image pins, bounded worker profiles, and deployment/security boundaries.
- Missing upstream artifacts, credentials, environments, capacity, or network paths are blocked readiness—not passes and not automatically product defects.
- Never commit credentials, private keys, access tokens, customer data, production test data, incident details, or private-repository inventories.
- Public organization context does not grant access to private repositories, production systems, databases, credentials, or hidden topology.
- Prefer focused pull requests, explicit validation, non-destructive Git operations, and documented uncertainty.
- Link substantial work to both Linear and a GitHub issue or pull request.

## Semantic conflict resolution

Resolve every Git conflict semantically. Inspect the merge base, both sides, path-scoped history, and normally 3–10 relevant commits. Consult tests, schemas, fixtures, workflows, architecture decisions, documentation, relevant test repositories, the production parent, and relevant external repositories. Never blindly select all of `ours`, `theirs`, current, or incoming. Preserve compatible intent and safeguards, scan the complete worktree for conflict markers, and run every affected validation contract.
