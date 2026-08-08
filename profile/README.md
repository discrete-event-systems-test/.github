# discrete-event-systems-test

`discrete-event-systems-test` provides independent browser and deployment-boundary verification for the [`discrete-event-systems`](https://github.com/discrete-event-systems) product organization. It preserves reproducible Playwright, Puppeteer, immutable-image, security-boundary, and bounded worker evidence while keeping test identity separate from production routing and access.

This page is the public orientation point for people and authorized AI agents. Repository-specific READMEs, tests, fixtures, workflows, and instructions remain authoritative for implementation and evidence.

## Start here

### For people

- Review the [browser automation contract](https://github.com/discrete-event-systems-test/.github/blob/main/DES_BROWSER_AUTOMATION.md) and [test-organization contract](https://github.com/discrete-event-systems-test/.github/blob/main/TEST_ORGANIZATION_CONTRACT.md).
- Use the [test GitHub Project](https://github.com/orgs/discrete-event-systems-test/projects/1) and [test Linear project](https://linear.app/denman/project/githubcomdiscrete-event-systems-test-2688194a677b) for planning, dependencies, and acceptance evidence.
- Use the [production GitHub Project](https://github.com/orgs/discrete-event-systems/projects/2) and [production Linear project](https://linear.app/denman/project/githubcomdiscrete-event-systems-4a3086ae0c45) only for the explicitly linked product context.
- Read [CONTRIBUTING.md](https://github.com/discrete-event-systems-test/.github/blob/main/CONTRIBUTING.md), [GOVERNANCE.md](https://github.com/discrete-event-systems-test/.github/blob/main/GOVERNANCE.md), [SUPPORT.md](https://github.com/discrete-event-systems-test/.github/blob/main/SUPPORT.md), and the [security policy](https://github.com/discrete-event-systems-test/.github/security/policy).
- Start in the README and local instructions of the exact test repository being changed; this profile is an index, not a substitute for repository documentation.

### For AI agents

1. Read [`project-context.yaml`](https://github.com/discrete-event-systems-test/.github/blob/main/project-context.yaml) for immutable test identity, the production-parent link, and explicit no-runtime-route policy.
2. Read [`repository-relationships.json`](https://github.com/discrete-event-systems-test/.github/blob/main/repository-relationships.json) before inferring dependencies, ownership, production access, or data flow.
3. Read [`AGENTS.md`](https://github.com/discrete-event-systems-test/.github/blob/main/AGENTS.md), [`ORG_CONTEXT.md`](https://github.com/discrete-event-systems-test/.github/blob/main/ORG_CONTEXT.md), and every applicable repository-local agent instruction.
4. Select the exact test repository and GitHub issue or Linear work item explicitly. Missing, unmapped, stale, contradictory, or ambiguous context must stop and be reported rather than guessed.
5. Treat `discrete-event-systems` as a black-box acceptance target through published contracts and separately authorized test inputs only. Public context grants no private repository, production system, database, credential, customer-data, or incident access.

## Canonical identity and authority

- GitHub test organization: [`discrete-event-systems-test`](https://github.com/discrete-event-systems-test)
- Immutable GitHub owner ID: `313546124`
- Linear test project: [`github.com/discrete-event-systems-test`](https://linear.app/denman/project/githubcomdiscrete-event-systems-test-2688194a677b)
- Immutable Linear project ID: `abc2c19e-7ec3-458a-a33d-0f8a105de450`
- GitHub test project: [`discrete-event-systems-test/projects/1`](https://github.com/orgs/discrete-event-systems-test/projects/1)
- Production parent: [`discrete-event-systems`](https://github.com/discrete-event-systems), immutable owner ID `306297904`
- Production Linear project: [`github.com/discrete-event-systems`](https://linear.app/denman/project/githubcomdiscrete-event-systems-4a3086ae0c45), immutable project ID `b352c0c6-02f5-4a5a-8460-017aedb5352f`
- Linear team: `DEN` (`eb8ab169-5afe-4b6f-9cab-3f2aa3e887dc`)
- Immutable central test-canary registry: [`ORESoftware/ai-agent-coordinator.rs@4b9870e419965ea7b7218462b584271163679a14`](https://github.com/ORESoftware/ai-agent-coordinator.rs/blob/4b9870e419965ea7b7218462b584271163679a14/config/test-org-homepage-canaries.yaml)

The reviewed central registry is authoritative for immutable test identity and the reviewed production-parent link; for this canary, that source is the immutable central test-canary registry pinned below. The production registry remains authoritative for production identity and runtime routing. Repository-local instructions, tests, fixtures, workflows, schemas, and documentation are authoritative for implementation and evidence. This test organization has no default runtime repository or runtime route.

## Browser automation

- [`des-web-playwright-e2e`](https://github.com/discrete-event-systems-test/des-web-playwright-e2e) — Playwright/Chromium route, catalog, routing-tool, and security contracts.
- [`des-web-puppeteer-e2e`](https://github.com/discrete-event-systems-test/des-web-puppeteer-e2e) — independent Puppeteer/Node contracts with screenshot evidence.

Both suites run from `discrete-event-systems/des-web.rs` through reusable GitHub Actions workflows pinned to immutable merged SHAs. The product repository's package-scoped token starts the private immutable server image locally before driving Chromium.

Each suite also publishes a bounded `gha-indie-worker` workflow for planning against the cluster-local DES service. Only the two named repositories are admitted to the browser profiles, and live indie execution remains disabled pending a separate capacity and network review.

## Operating principles

- Preserve the existing Playwright, Puppeteer, immutable-image, deployment-boundary, and bounded-worker evidence rather than replacing it with a generic pass/fail summary.
- A missing upstream artifact, environment, authorization, credential, or network path is blocked readiness—not a passing result and not automatically a product regression.
- Keep test evidence deterministic, bounded, least-privileged, and tied to immutable source or image identities.
- Link substantial work to Linear and a GitHub issue or pull request so humans and agents can recover intent, dependencies, and evidence.
- Resolve Git conflicts semantically: inspect the merge base, both sides, path-scoped history, and 3–10 relevant commits when available; consult linked issues, pull requests, tests, schemas, fixtures, workflows, architecture decisions, documentation, relevant same-organization repositories, the production parent, and relevant external repositories. Never accept `ours`, `theirs`, current, or incoming wholesale.
- Preserve compatible intent, evidence, interfaces, security controls, and operational safeguards from every relevant side, scan the full worktree for unresolved conflict markers, and run every affected validation contract.

## Public context boundary

This profile and the `.github` repository are intentionally public. They may contain public identifiers, links, acceptance scope, and operating rules. They must not contain credentials, private repository inventories, customer or user data, production test data, private issue content, incident details, unpublished vulnerabilities, or security-sensitive topology.
