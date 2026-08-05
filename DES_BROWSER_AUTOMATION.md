# DES browser automation operating guide

## Ownership

- Product/server: `discrete-event-systems/des-web.rs`
- Playwright contracts: `discrete-event-systems-test/des-web-playwright-e2e`
- Puppeteer contracts: `discrete-event-systems-test/des-web-puppeteer-e2e`
- GitOps and indie-worker policy: `ORESoftware/k8s-cluster`

## GitHub Actions lane

The product repository owns `.github/workflows/external-browser-fleet.yml`. It calls each test repository's reusable workflow at an immutable merged commit SHA and passes the same SHA as `suite_ref`. This prevents a mutable branch from changing the test implementation after review.

The caller grants only `contents: read` and `packages: read`. Its repository-scoped token authenticates to GHCR, pulls the pinned `des-web` image digest, and starts the container read-only with a bounded writable `/tmp`. The server runs with `DES_PUBLIC_PATH_MODE=mounted`; each suite then executes a real Chromium browser against `127.0.0.1:8130`.

The suites cover:

- `/healthz` and `/readyz` semantics, including degraded readiness;
- shared-layout pages and the standalone routing dashboard;
- canonical `/des` navigation rewriting;
- htmx partial availability;
- the `des.route-catalog.v1` API envelope;
- browser hardening headers;
- application 404 behavior.

Playwright retains traces, screenshots, video, reports, and server logs on failure. Puppeteer retains screenshot evidence and server logs.

## gha-indie-worker lane

Each test repository publishes `.github/workflows/gha-indie-worker.yml` with only pinned checkout/setup actions, `npm ci`, and its approved browser command. The build-server planner requires:

- an exact 40-hex revision;
- one of the two explicitly allowlisted repository URLs;
- the fixed `playwright` or `puppeteer` profile;
- an authenticated operator request.

The suites default to `http://dd-des-web.default.svc.cluster.local:8130` in this lane. The entire `discrete-event-systems-test` organization is intentionally not allowlisted.

`BUILD_SERVER_GHA_WORKFLOW_EXECUTION_ENABLED=false` remains the global kill switch. Planning and policy validation are useful now; enabling live execution requires a separate change covering capacity, browser sandboxing, cluster egress, artifact retention, and rollback.

## Change procedure

1. Change a suite in its own repository and validate its lockfile/static workflow.
2. Merge the suite PR.
3. Run the full browser suite from a temporary product-repository pin when the contract changed.
4. Update `des-web.rs` to the new immutable merged suite SHA.
5. Merge only after both external browser jobs and the product CI pass.
6. Update the product and test GitHub Projects plus the Linear issue/document with the merged SHAs and evidence.

## Tracking

- Product GitHub Project: https://github.com/orgs/discrete-event-systems/projects/2
- Test GitHub Project: https://github.com/orgs/discrete-event-systems-test/projects/1
- Linear project: https://linear.app/denman/project/githubcomdiscrete-event-systems-4a3086ae0c45
