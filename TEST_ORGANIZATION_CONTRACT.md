# Discrete Event Systems test organization contract

The `discrete-event-systems-test` organization owns cross-repository, browser, contract, packaging, and deployment verification for production repositories in `discrete-event-systems`.

## Current repositories

- `des-web-playwright-e2e`
- `des-web-puppeteer-e2e`
- `.github`

## Required repositories

- `des-web-selenium-e2e`
- `des-api-contract-e2e`
- `des-cli-e2e`
- `des-mcp-server-e2e`
- `des-monorepo-integration-e2e`
- `des-zpkg-integration-e2e`

## Baseline CI requirements

Each test repository must:

- run on pull requests and on a scheduled default-branch workflow;
- pin or lock package-manager dependencies;
- upload logs, screenshots, videos, and traces after failures;
- support GitHub-hosted runners and `gha-indie-worker` labels;
- use only test credentials and test infrastructure;
- document the production repositories and refs under test;
- include smoke, failure-path, and recovery-path coverage;
- expose a deterministic local command matching CI.

## Browser matrix

`des-web.rs` must be covered independently by Playwright, Puppeteer, and Selenium. At least Chromium and Firefox must run in the Playwright suite; Selenium must include a WebDriver compatibility smoke test.

## Integration matrix

- API schema compatibility and migrations: `des-api-contract-e2e`
- CLI argument manifests and exit behavior: `des-cli-e2e`
- MCP protocol, cancellation, and malformed input: `des-mcp-server-e2e`
- submodule composition and pinned refs: `des-monorepo-integration-e2e`
- `.zpkg.toml`, `.zpkg.lock`, dependency boundaries, and client generation: `des-zpkg-integration-e2e`

No production repository is considered release-ready unless its mapped test suites pass against the candidate commit.
