# discrete-event-systems-test governance

This organization owns black-box, cross-repository, and deployment-boundary verification for software published by [`discrete-event-systems`](https://github.com/discrete-event-systems).

## DES browser fleet

| Repository | Responsibility |
| --- | --- |
| [`des-web-playwright-e2e`](https://github.com/discrete-event-systems-test/des-web-playwright-e2e) | Playwright/Chromium contracts for health, readiness, canonical pages, mounted `/des` navigation, route catalog, security headers, routing controls, and application 404 behavior |
| [`des-web-puppeteer-e2e`](https://github.com/discrete-event-systems-test/des-web-puppeteer-e2e) | Independent Puppeteer implementation using Node's test runner, including the same public contracts plus retained screenshot evidence |
| [`.github`](https://github.com/discrete-event-systems-test/.github) | Organization profile, ownership policy, operational documentation, and project links |

The production application remains owned by [`discrete-event-systems/des-web.rs`](https://github.com/discrete-event-systems/des-web.rs). Kubernetes, gateway, build-server, and Argo CD configuration remain owned by [`ORESoftware/k8s-cluster`](https://github.com/ORESoftware/k8s-cluster).

## Execution contract

Every browser repository has two deliberately different lanes:

1. **GitHub Actions:** `des-web.rs` calls each test repository as a reusable workflow at an immutable merged commit SHA. The product repository's least-privilege `GITHUB_TOKEN` receives `packages: read`, pulls the private immutable `des-web` image, starts it locally in mounted-path mode, and executes a real Chromium browser.
2. **`gha-indie-worker`:** each test repository publishes a small static `.github/workflows/gha-indie-worker.yml` at an immutable 40-hex commit. The planner maps it to the fixed `playwright` or `puppeteer` profile and targets the cluster-local `dd-des-web.default.svc.cluster.local:8130` service.

Only these two test repositories are admitted to executable browser profiles. The whole test organization is not allowlisted. Live indie-worker execution remains fail-closed while `BUILD_SERVER_GHA_WORKFLOW_EXECUTION_ENABLED=false`; planning and review can proceed without silently enabling production capacity.

## Project tracking

- [Production DES project](https://github.com/orgs/discrete-event-systems/projects/2)
- [DES test project](https://github.com/orgs/discrete-event-systems-test/projects/1)
- [Linear project: `github.com/discrete-event-systems`](https://linear.app/denman/project/githubcomdiscrete-event-systems-4a3086ae0c45)

Every public route, route-envelope, image, or gateway change must update its owning browser contract in the same rollout. Suite revisions are repinned only after their repository PRs are merged and validated.

## Evidence policy

Browser failures retain the smallest useful package of evidence: immutable source SHA, browser report, screenshot, trace/video where supported, and server logs. Evidence must not contain operator credentials, cookies, authorization headers, database credentials, or unredacted personal data.
