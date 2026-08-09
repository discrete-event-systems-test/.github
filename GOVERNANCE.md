# Governance

`discrete-event-systems-test` is an independent acceptance organization for the `discrete-event-systems` product organization.

## Systems of record

- GitHub repositories and pull requests own code, immutable evidence, review, and delivery history.
- The test Linear project owns acceptance planning and dependencies.
- The test GitHub Project owns the cross-repository execution view.
- The central test-canary registry owns immutable test identity and the reviewed production-parent link.
- The production registry remains authoritative for production identity and runtime routing.

## Change policy

Organization-wide public context changes require a focused pull request, exact-head validation, semantic preservation of existing browser/deployment evidence, and a final concurrency check before merge. Generated context files must match one immutable central registry commit exactly. Repository-owned profile and policy text may add product-specific guidance but must not contradict generated identity, routing, authorization, or public-safety boundaries.

## Boundaries

This organization has no production runtime route. Its parent relationship grants no private repository, database, system, credential, customer-data, or incident access. Any such access requires separate explicit authorization outside this public repository.
