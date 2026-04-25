# Kaptain Status

This document is intended to show the state of completion
of each part of the project in different granularities.


## Thirty Thousand Feet View

Broadly the project can be divided in half, though each half has an
inherently close relationship with the other half since they are
designed to work together as an end-to-end solution.

| Component      | Coarse  | Fine (approx)  |
|----------------|---------|----------------|
| Build system   |   🟠    | 75%            |
| Deploy system  |   🟠    | 65%            |

While both the build and deploy system are already usable and doing a great job,
certain parts are not present or not completed. The above ratings reflect the
overall system. For example buildon-github-actions is 90% complete, but no
support for Azure Devops or GitLab CI has been developed, and the scripts need
to be extracted to kaptain-build-scripts. So even though the scripts are already
excellent, well tested, and highly useful, the overall build system is
considered less finished because of key work needed on the scripts and the lack
of wrappers for other popular systems. The deploy situation is a bit different
in that the scripts themselves are only rudimentary with structure and basics in
place, but the image build system is very mature and fleshed out. So the rating
of 30% on the scripts and 65% on the overall system reflects this.


## Per Repository

| Repository                                        | Coarse  | Fine (approx)  | Visibility  | Description                                                         |
|---------------------------------------------------|---------|----------------|-------------|---------------------------------------------------------------------|
| kaptain                                           |   🟠    | 30%            | public      | Branchout root repo - easy git management and centralised docs      |
| .github                                           |   ⚪    | 5%             | private     | Project-wide docs, unimportant for now, but will be once published  |
| buildon-github-actions                            |   🟢    | 90%            | public      | Build scripts wrapper for GitHub Actions reusable workflows         |
| layer-and-layerset-build                          |   🟢    | 100%           | public      | Build layer covering 2-part versioning, kind, and multiplatform     |
| layer-github-flow-strict                          |   🟢    | 100%           | public      | Build layer enforcing strict GitHub flow quality checks             |
| layer-image-environment-base                      |   🟢    | 100%           | public      | Build layer for environment base image builds                       |
| layer-image-environment-deploy                    |   🟢    | 100%           | public      | Build layer for environment deploy image builds                     |
| layer-kaptain-scripts-build                       |   🟠    | 50%            | public      | Build layer for the kaptain scripts package builds                  |
| layerset-and-layer-build                          |   🟢    | 100%           | public      | Layerset combining the build layers via version ranges              |
| layerset-image-environment-base                   |   🟢    | 100%           | public      | Layerset combining base image layers with github flow               |
| layerset-image-environment-deploy                 |   🟢    | 100%           | public      | Layerset combining deploy image layers with github flow             |
| layerset-kaptain-scripts-build                    |   🟠    | 50%            | public      | Layerset combining the kaptain scripts build layers                 |
| image-environment-base-alpine-3-23                |   🟢    | 100%           | public      | Alpine 3.23 flavour of environment base image, dual arch            |
| image-environment-base-trixie-slim                |   🟢    | 100%           | public      | Debian Trixie flavour of environment base image, dual arch          |
| image-environment-base-ubi-9-minimal              |   🟢    | 100%           | public      | UBI 9 Minimal flavour of environment base image, dual arch          |
| image-environment-base-ubuntu-24-04-lts           |   🟢    | 100%           | public      | Ubuntu 24.04 flavour of environment base image, dual arch           |
| image-environment-deploy-alpine-3-23              |   🟢    | 100%           | public      | Alpine 3.23 flavour of environment deploy image, dual arch          |
| image-environment-deploy-trixie-slim              |   🟢    | 100%           | public      | Debian Trixie flavour of environment deploy image, dual arch        |
| image-environment-deploy-ubi-9-minimal            |   🟢    | 100%           | public      | UBI 9 Minimal flavour of environment deploy image, dual arch        |
| image-environment-deploy-ubuntu-24-04-lts         |   🟢    | 100%           | public      | Ubuntu 24.04 flavour of environment deploy image, dual arch         |
| image-busybox-httpd                               |   🟢    | 100%           | public      | Repackaged updated kaptain-ised fork of neat little project         |
| kaptain-build-scripts                             |   ⚪    | 0% (sort of)   | private     | Build and package scripts from buildon-github-actions extracted     |
| kaptain-deploy-scripts                            |   🟠    | 30%            | public      | Kubernetes deploy scripts as used in the deploy image series        |
| kaptain-shared-scripts                            |   🟢    | 90%            | public      | Library of scripts as used in multiple places, DRY                  |
| kaptain-marketplace                               |   🟠    | 50%            | public      | Plugin definitions for the Kaptain marketplace                      |
| kaptain-skills                                    |   🟠    | 50%            | public      | Kaptain skill set for LLMs/agents - partially finished              |
| kaptain-status                                    |   🟢    | 99.9%          | public      | This, expect weekly or fortnightly updates, complain if not         |
| kaptain-user-scripts                              |   🟢    | 100%           | public      | Scripts that make using the kaptain build and deploy system easy    |
| homebrew-kaptain                                  |   🟢    | 80%            | public      | Homebrew formulae for easy install of kaptain-user-scripts          |
| aws-cli-v2-index                                  |   🟢    | 100%           | public      | Utility for safely building images with aws cli v2                  |
| aws-eks-cluster-management                        |   🟢    | 90%            | public      | AWS EKS cluster management tools in a reusable image, dual arch     |
| spec-build-scripts-api                            |   🟠    | 50%            | public      | Build scripts API spec, uses the spec-scripts-api-schema            |
| spec-scripts-api-schema                           |   🟠    | 50%            | public      | JSON Schema for script package APIs                                 |
| spec-kaptainpm-schema                             |   🟢    | 90%            | public      | JSON Schema for KaptainPM.yaml in various forms                     |
| spec-manifests-contract-schema                    |   🟢    | 100%           | public      | JSON Schema for the manifests contract published by builds          |
| vendor-envoy-gateway                              |   🟢    | 100%           | public      | Vendored Envoy Gateway helm chart rendered to plain manifests       |
| vendor-envoy-gateway-global                       |   🟢    | 100%           | public      | Vendored Envoy Gateway CRDs for cluster-wide installation           |
| vendor-envoy-gateway-proxy                        |   🟢    | 100%           | public      | Vendored Envoy data-plane image paired with Gateway manifests       |
| vendor-kubernetes-sigs-gateway-api                |   🟢    | 100%           | public      | Vendored Kubernetes Gateway API CRDs                                |


## What's Missing

### Key Things Unfinished/Unstarted

1. kaptain-build-scripts - product build - bundle manifests together from sets of apps in a controlled way allowing for cross cutting concerns to be added
2. kaptain-build-scripts - environmemt build - pull apps and products together into another zip and also into a deploy image
3. kaptain-build-scripts - comprehensive manifest validation system with configurability - enforces quality practices and details essential for correct deployment 
4. kaptain-deploy-scripts - much more sophistication, success checking, stability scanning, hook points, and much more needed but not yet in the system
5. Slack notification integration - chat threads for builds and/or deploys
6. Google chat notification integration - chat threads for builds and/or deploys
7. Teams chat notification integration - chat threads for builds and/or deploys


### Build System Wrappers

The planned build system wrappers will come on a demand basis or from most
popular to least or easiest to trickiest. The intent is documented in the
[CI/CD Platforms To Support](https://github.com/orgs/kube-kaptain/projects/2/views/1)
GitHub project. Two types are listed there, special integrations, and doc
only repos that offer instructions on how to use the scripts or build image.


## Want To Use It Anyway?

Before you use this consider the following:

1. You would have to roll your own product build
2. You would have to roll your own environment build
3. The environment deploy scripts are fire and forget - not good enough for most production workloads

However it is already good for some things:

1. Image builds - consistent reliable builds of lean OCI images from easy to read Dockerfiles using podman
2. Manifest packaging - bundle up reusable manifests without hard coded config or secrets - deploy your own way
3. Generated configurable best practice manifest sets - as little as zero manifests in your project
4. Bundled change data - published with every release 
5. Quality checks on non-built repos - ensure PRs are clean and commits decent - configurable styles
6. Generic builds of whatever you need with sophisticated tagging strategies

So if any of that suits your needs then go ahead and get in touch and I'll be
happy to help you get started. If your projects are public on GitHub add me as
a reviewer or ask me for advice on how to best put it all to use.
