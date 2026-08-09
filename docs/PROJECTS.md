# Project routing and Zed dependency gate

- **GitHub organization:** [discrete-event-systems-test](https://github.com/discrete-event-systems-test)
- **Production organization:** [discrete-event-systems](https://github.com/discrete-event-systems)
- **GitHub Project:** [organization Project 1](https://github.com/orgs/discrete-event-systems-test/projects/1); item attachment must be verified rather than assumed
- **Production browser-automation Project:** [discrete-event-systems Project 2](https://github.com/orgs/discrete-event-systems/projects/2)
- **Linear project:** [github.com/discrete-event-systems-test](https://linear.app/denman/project/githubcomdiscrete-event-systems-test-2688194a677b)
- **Production package-family plan:** [discrete-event-systems/des-web.rs#12](https://github.com/discrete-event-systems/des-web.rs/issues/12)
- **Test dependency gate:** [discrete-event-systems-test/.github#4](https://github.com/discrete-event-systems-test/.github/issues/4)
- **Exact-SHA indie-worker evidence:** [Linear DEN-2657](https://linear.app/denman/issue/DEN-2657)
- **Cross-repository browser automation:** [Linear DEN-2447](https://linear.app/denman/issue/DEN-2447)

## Current test repositories

| Repository | Driver | Exact `main` revision | GitHub Actions | `gha-indie-worker` | Zed state |
| --- | --- | --- | --- | --- | --- |
| `des-web-playwright-e2e` | Playwright | `1e1116ef6811c4e3e6be34ad3e1def39bc20ef59` | hosted browser lane | fixed `playwright` profile | blocked; no manifest until the production quartet resolves |
| `des-web-puppeteer-e2e` | Puppeteer | `0547548429d937023a124de37afca7659a85c3dd` | hosted browser lane | fixed `puppeteer` profile | blocked; no manifest until the production quartet resolves |

Both suites are real tests and should continue running independently of Zed package publication. A missing Zed lane must be reported as a dependency blocker, not replaced with invented package coordinates.

## Browser CI execution boundary

Each repository owns a reviewed `.github/workflows/gha-indie-worker.yml`. Independent execution must use that workflow from the exact revision in the table above; mutable branches are not accepted as execution provenance.

The two execution lanes intentionally remain independent:

1. GitHub Actions runs the browser suites as the hosted control lane.
2. `gha-indie-worker` plans the same immutable revisions and maps them only to fixed browser profiles.

The product-side `dd-build-server` remains unprivileged. `ORESoftware/k8s-cluster#1171` introduced the separately authenticated `dd-ci-profile-runner`, binding only the two repositories above to fixed Playwright/Puppeteer commands and exact commit SHAs; `ORESoftware/k8s-cluster#1176` promoted that boundary to the Argo-tracked `dev` branch without merging unrelated `main` work.

Protected execution also registers/resolves an `ai-agent-bridge` channel so concurrent agents can see the claimed DES browser lane, blockers, and completion result. Live acceptance is authoritative only when DEN-2657 records terminal `succeeded` results with non-empty independent-worker build IDs; deployment state alone is not sufficient evidence.

## Required production quartet

The test repositories will eventually import:

- `discrete-event-systems/des-clients`
- `discrete-event-systems/des-lib`
- `discrete-event-systems/des-interfaces`
- `discrete-event-systems/des-cli`

As of August 8, 2026, all four target repositories return 404. Existing references in production `.zpkg.toml` files express intended architecture but are not evidence that the packages resolve.

## Activation gate

Only add the quartet after all four repositories exist, publish canonical root manifests, and pass a clean-clone Zed resolution. The resulting E2E manifests must use `.vendor/.zed`, exclude generated state, and produce `.zpkg.lock` only through a real successful resolver run.

CI must validate the exact coordinates and run frozen installation. When canonical packages are also retained as committed submodules, adopt them with `zed overtake --git-submodules`: Git owns exact source transport while Zed owns package identity, dependency intent, materialization, and immutable lock provenance. Non-Zed submodules remain Git-managed.

## Source-of-truth boundaries

GitHub owns repositories, commits, pull requests, test evidence, artifacts, and runtime results. Linear owns priority, ownership, dependencies, milestones, and status reporting. The organization project is the execution board; item attachment is recorded only after direct verification.
