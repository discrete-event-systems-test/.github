# Project routing and Zed dependency gate

- **GitHub organization:** [discrete-event-systems-test](https://github.com/discrete-event-systems-test)
- **Production organization:** [discrete-event-systems](https://github.com/discrete-event-systems)
- **GitHub Project:** [organization Project 1](https://github.com/orgs/discrete-event-systems-test/projects/1); item attachment must be verified rather than assumed
- **Linear project:** [github.com/discrete-event-systems-test](https://linear.app/denman/project/githubcomdiscrete-event-systems-test-2688194a677b)
- **Production package-family plan:** [discrete-event-systems/des-web.rs#12](https://github.com/discrete-event-systems/des-web.rs/issues/12)
- **Test dependency gate:** [discrete-event-systems-test/.github#4](https://github.com/discrete-event-systems-test/.github/issues/4)

## Current test repositories

| Repository | Purpose | Zed state |
| --- | --- | --- |
| `des-web-playwright-e2e` | Playwright route and browser contract tests | blocked; no manifest until the production quartet resolves |
| `des-web-puppeteer-e2e` | Independent Puppeteer browser coverage | blocked; no manifest until the production quartet resolves |

Both suites are real tests and should continue running independently of Zed package publication. A missing Zed lane must be reported as a dependency blocker, not replaced with invented package coordinates.

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
