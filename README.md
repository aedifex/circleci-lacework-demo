<img src="https://techally-content.s3-us-west-1.amazonaws.com/public-content/lacework_logo_full.png" width="600">

[![CircleCI Build Status](https://circleci.com/gh/aedifex/circleci-lacework-demo.svg?style=shield "CircleCI Build Status")](https://circleci.com/gh/aedifex/circleci-lacework-demo)

![Orb Version Badge](https://badges.circleci.com/orbs/lacework/lacework.svg)


# CircleCI && Lacework Demo
An example of using Lacework &amp; CircleCI to incorporate application security into your CI/CD pipelines by leveraging the "shift left" methodology.

## Prerequisites

Before using this demo, make sure you have the following prerequisites installed and configured:

- CircleCI Account (https://circleci.com/)
- CircleCI API Token (for integration)
- Lacework Account (https://www.lacework.com/)
- Lacework API Token (for integration)

## Okay, what exactly is shifting left?

Essentially incorporating software and application security into earlier junctures of the software delivery life-cycle, namely the building / testing phase, thus "shifting" left. Rather than security being a detractor to development speed and velocity, security becomes an enabler.

## Use-cases

- Container scanning
- AMI scanning
- Using custom vulnerability exceptions

### Differences between the lw-scanner and the lacework CLI?

TLDR

The Lacework CLI triggers on-demand registry scans from the Lacework *platform* to inspect the target registry. From this perspective, the CLI is simply making an API call to the Lacework platform - the Lacework platform is pulling the image layers from the *registry* and executing the scan. This is absolutely crucial to understanding where/how the CLI is able to introspect vulnerabilities. Using this technique in the context of a broader CI/CD process with "staging" repositories can be an extremely effective method for vulnerability discovery.

The lw-scanner scans images on the local file-system. The scan itself is not performed locally, rather the scanner enumerates the image layers pulled from the local file-system and sends data back to the Lacework platform. When people generally conceptualize vulnerability scanning, this is the paradigm they're most familiar with. Local scanning is powerful when *building* images as a routine part of a CI/CD process. Unfortunately, it is not possible to automatically fail the pipeline if a certain vulnerability threshold is met, though possible to do so with some simple scripting (Bash & jq).

#### lw-scanner

Link to [documentation](https://support.lacework.com/hc/en-us/articles/1500001777821-Integrate-Inline-Scanner)

#### Lacework CLI

Link to [documentation](https://github.com/lacework/go-sdk/wiki/CLI-Documentation)

One of the primary benefits associated with the CLI is the ability to leverage a powerful CircleCI feature called "Orbs" - which are effectively prepackaged pieces of configuration.

