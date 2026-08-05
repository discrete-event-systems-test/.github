# Discrete Event Systems — test organization

`discrete-event-systems-test` provides independent evidence for the deployed products in [`discrete-event-systems`](https://github.com/discrete-event-systems).

## Browser automation

- **[Playwright DES E2E](https://github.com/discrete-event-systems-test/des-web-playwright-e2e)** — canonical `/des` route and navigation contracts, API catalog validation, failure evidence, GitHub Actions, and `gha-indie-worker`.
- **[Puppeteer DES E2E](https://github.com/discrete-event-systems-test/des-web-puppeteer-e2e)** — an independent gateway and compatibility-Service canary using a second browser harness.

The application under test is [`discrete-event-systems/des-web.rs`](https://github.com/discrete-event-systems/des-web.rs). GitOps ownership lives in [`ORESoftware/k8s-cluster`](https://github.com/ORESoftware/k8s-cluster).

## Tracking

- [Production DES GitHub Project](https://github.com/orgs/discrete-event-systems/projects/2)
- [DES Browser Automation Project](https://github.com/orgs/discrete-event-systems-test/projects/1)
- Linear project: `github.com/discrete-event-systems-test`

Tests run both on GitHub-hosted runners and through the independent `gha-indie-worker` continuity lane at immutable revisions.
