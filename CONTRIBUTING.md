# Contributing browser contracts

A browser-test change should identify the production behavior it owns, the execution lanes it supports, and the evidence it emits.

## Required properties

- Keep package versions and GitHub Actions pinned.
- Keep the independent-worker workflow inside its supported static subset.
- Require an immutable 40-hex revision for worker execution.
- Resolve the canonical `dd-des-web` Service before the compatibility alias when running in-cluster.
- Treat the public authentication boundary as expected behavior when no gateway secret is available.
- Never print, screenshot, upload, or persist `DES_GATEWAY_AUTH`.
- Add a bounded timeout and a useful assertion message for every network or browser action.

## Ownership boundary

Local component tests belong in `discrete-event-systems/des-web.rs`. Tests in this organization should cross at least one meaningful boundary: deployed HTTP behavior, gateway behavior, service aliasing, independent executor behavior, or another repository's contract.

Open a pull request and link the corresponding item in the DES production project, the DES test project, and the Linear project `github.com/discrete-event-systems-test`.
