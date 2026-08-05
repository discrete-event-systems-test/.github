# discrete-event-systems-test governance

This organization owns black-box, cross-repository, and deployment-boundary tests for the software published by [`discrete-event-systems`](https://github.com/discrete-event-systems).

## DES browser fleet

| Repository | Responsibility |
| --- | --- |
| [`des-web-playwright-e2e`](https://github.com/discrete-event-systems-test/des-web-playwright-e2e) | Canonical `/des` routes, route catalog, mounted-prefix navigation, bounded errors, and primary Chromium evidence |
| [`des-web-puppeteer-e2e`](https://github.com/discrete-event-systems-test/des-web-puppeteer-e2e) | Independent gateway, security-header, catalog, and `dd-des-simulator:8099` compatibility-Service canaries |
| [`.github`](https://github.com/discrete-event-systems-test/.github) | Organization profile, ownership policy, issue templates, and project links |

The production application remains owned by [`discrete-event-systems/des-web.rs`](https://github.com/discrete-event-systems/des-web.rs). The routing, Services, NetworkPolicy, gateway, and Argo CD manifests remain owned by [`ORESoftware/k8s-cluster`](https://github.com/ORESoftware/k8s-cluster).

## Execution contract

Every browser repository has two lanes:

1. **GitHub Actions** installs the pinned browser dependency, exercises the public gateway, and retains human-readable evidence artifacts.
2. **`gha-indie-worker`** plans and runs a deliberately bounded workflow at an immutable 40-hex commit. Inside the cluster, tests first use `dd-des-web:8130`, then the stable `dd-des-simulator:8099` compatibility Service.

The public gateway credential is stored only as a GitHub Actions secret. Test code accepts it as `DES_GATEWAY_AUTH`, sends it as the `dd_auth` cookie and legacy `Auth` header, and never writes the value to evidence.

## Project tracking

- [Production DES project](https://github.com/orgs/discrete-event-systems/projects/2)
- [DES test project](https://github.com/orgs/discrete-event-systems-test/projects/1)
- Linear project: `github.com/discrete-event-systems-test`

Every route or gateway change must update its owning browser contract in the same rollout. A compatibility path may be removed only after its canary has been changed into a deliberate retirement assertion and production traffic has been checked.

## Evidence policy

Browser failures should retain the smallest useful package of evidence: target resolution, JUnit XML, screenshots, traces or video, and the immutable source SHA. Artifacts must not contain operator credentials, cookies, authorization headers, database credentials, or unredacted personal data.
