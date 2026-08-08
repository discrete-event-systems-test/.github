# discrete-event-systems-test organization context

`discrete-event-systems-test` is a test-only acceptance organization for the production organization [`discrete-event-systems`](https://github.com/discrete-event-systems). It does not provide a production runtime route and does not imply access to any private repository, production system, database, credential, customer record, or incident detail.

## Canonical identity

- GitHub test organization: [`discrete-event-systems-test`](https://github.com/discrete-event-systems-test)
- Immutable GitHub test owner ID: `313546124`
- Test planning project: [`github.com/discrete-event-systems-test`](https://linear.app/denman/project/githubcomdiscrete-event-systems-test-2688194a677b)
- Immutable test Linear project ID: `abc2c19e-7ec3-458a-a33d-0f8a105de450`
- GitHub execution project: [project board](https://github.com/orgs/discrete-event-systems-test/projects/1)
- Production parent: [`discrete-event-systems`](https://github.com/discrete-event-systems)
- Immutable production parent owner ID: `306297904`
- Production planning project: [`github.com/discrete-event-systems`](https://linear.app/denman/project/githubcomdiscrete-event-systems-4a3086ae0c45)
- Immutable production Linear project ID: `b352c0c6-02f5-4a5a-8460-017aedb5352f`

The immutable central test-canary registry controls this identity and parent link. The production registry remains authoritative for production identity and runtime routing. Repository-local instructions, tests, fixtures, workflows, and documentation remain authoritative for implementation and evidence.

## Acceptance scope

Independent browser and deployment-boundary acceptance organization for Discrete Event Systems.

- Playwright and Chromium route contracts
- independent Puppeteer browser evidence
- immutable local server image startup
- deployment and security boundaries
- bounded gha-indie-worker planning contracts

The existing specialized organization profile and readiness notes must be preserved. A missing dependency, upstream artifact, environment, authorization, or credential is blocked readiness—not a passing result and not automatically a product regression.

## Agent operating contract

1. Read `project-context.yaml`, `repository-relationships.json`, this file, `AGENTS.md`, and every applicable repository-local instruction.
2. Select the exact test repository and work item explicitly; this organization has no default runtime repository.
3. Treat the production parent as a black-box acceptance target through published contracts and separately authorized test inputs only.
4. Do not infer private repository access, production topology, credentials, customer data, or database access from this public context.
5. Fail closed on missing, unmapped, ambiguous, stale, or contradictory context.
6. Link substantial work to Linear and a GitHub issue or pull request so humans and agents can recover intent and evidence.

## Semantic Git conflict resolution

> resolve any and all git conflicts semantically, will full context, even looking back 3-10 commits in git log history for more context - never hastily pick sides in a conflict but merge things conceptually, using max context and complete conceptual awareness for a given github organization's repos and external org repos too

Inspect the merge base, both sides, path-scoped history, and 3–10 relevant commits when available. Consult linked issues, pull requests, test evidence, schemas, fixtures, workflows, architecture decisions, documentation, parent-production repositories, and relevant external repositories. Never accept `ours`, `theirs`, current, or incoming wholesale. Preserve compatible intent and evidence, scan the full worktree for conflict markers, and run every affected validation contract.

## Public context boundary

This file is intentionally public. It may contain public identifiers, links, test scope, and operating rules. It must not contain credentials, private repository inventories, customer or user data, production test data, incident details, security-sensitive topology, or unpublished vulnerabilities.
