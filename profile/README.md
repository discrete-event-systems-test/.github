# discrete-event-systems-test

Independent browser and deployment-boundary verification for the [`discrete-event-systems`](https://github.com/discrete-event-systems) product organization.

## Browser automation

- [`des-web-playwright-e2e`](https://github.com/discrete-event-systems-test/des-web-playwright-e2e) — Playwright/Chromium route, catalog, routing-tool, and security contracts.
- [`des-web-puppeteer-e2e`](https://github.com/discrete-event-systems-test/des-web-puppeteer-e2e) — independent Puppeteer/Node contracts with screenshot evidence.

Both suites run from `discrete-event-systems/des-web.rs` through reusable GitHub Actions workflows pinned to immutable merged SHAs. The product repository's package-scoped token starts the private immutable server image locally before driving Chromium.

Each suite also publishes a bounded `gha-indie-worker` workflow for planning against the cluster-local DES service. Only the two named repositories are admitted to the browser profiles, and live indie execution remains disabled pending a separate capacity and network review.

[Production project](https://github.com/orgs/discrete-event-systems/projects/2) · [Test project](https://github.com/orgs/discrete-event-systems-test/projects/1) · [Linear](https://linear.app/denman/project/githubcomdiscrete-event-systems-4a3086ae0c45)
