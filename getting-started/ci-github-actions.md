# Simple CI using Github Actions

Github provides a powerful workflow-as-code engine automation & CI called [Github Actions](https://github.com/features/actions).
This technology is available for everyone in the Github Philips-Internal organization.

## Applicability

### Non-Product Software

For non-product software, we can use a simple CI based on GitHub actions. Many Philips specific actions are already available.
See [Philips-Internal Actions](https://github.com/philips-internal/actions) for more details.

### Product Software

For product software, we need to ensure reproducible builds in the future.
Since we cannot guarantee that the Github actions runner remains available over time, at least the build and test steps should not depend
on the Github actions engine to run.

In IGT we have the GBE to ensure reproducible builds over time.

## Building a CI

Get inspired by CI's & CD's built by others:

* [.Net Core on Linux](https://github.com/philips-internal/igt-cloud-algorithm-adapter/tree/main/.github/workflows)
* [Terraform CI / CD on Linux](https://github.com/philips-internal/igt-cloud-infra/tree/main/.github/workflows)
* [C++ on Windows](https://github.com/philips-internal/IGT-ReferenceApp-cpp/tree/develop/.github/workflows)

## Use the Philips Innersource runners

A set of shared Philips runners/agents is provided for running the Github actions.
These runners can connect to the Philips global network, and thereby can reach e.g. Artifactory, TICS etc.
__Note: At moment of writing only a pool of Linux runners is available. We need to arrange Windows runners ourselves__

This pool of runners can be used by specifying the following in the [workflows](../.github/workflows):

```YAML
jobs:
  build:
    # Run the job the Philips-Internal / Innersource agent pool
    runs-on: [self-hosted, Linux, philips]
```

### Request access

In order to enable use of the self-hosted, the pool needs to be shared with your repository.
Request for this can be made by creating a ticket in [request-self-hosted-runner-access](https://github.com/philips-internal/request-self-hosted-runner-access)

See this [example ticket](https://github.com/philips-internal/request-self-hosted-runner-access/issues/705) for details
