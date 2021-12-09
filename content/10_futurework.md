---
weight: 10
title: "Future Work"
draft: false
---

## Future Work

Our team decided to test the idea of tag immutability using Ethereum, which allowed us to quickly build a Proof-of-Concept using smart contracts written in Solidity.

### Compatibility with other blockchains

Our next step is to allow our solution to easily plug in any blockchain that supports smart contracts. We would also like to use permissioned blockchains such as [ResilientDB](https://resilientdb.com/) in order to achieve a higher throughput.

### GitHub OAuth App

Currently our application optionally reads a GitHub access token from the UI and creates tags in the GitHub repositories. We would like to instead create a [GitHub OAuth App](https://docs.github.com/en/developers/apps/building-oauth-apps/creating-an-oauth-app) that users can give permissions for creating tags in the repositories they have access to.

### Compatibility with other VCS

Our current scope is limited to working with git tags for repositories hosted on [GitHub](https://github.com). In the future, we would like our APIs to be easily consumed by not only other git hosting providers such as [GitLab](https://about.gitlab.com/) and [Bitbucket](https://bitbucket.org/product/), but also hosting providers for [Subversion](https://subversion.apache.org/) and [Mercurial](https://www.mercurial-scm.org/) VCS.

### Automation with existing CI/CD workflows

While our project has a web front-end which makes it easy for our users to use our application, we can also provide Command Line Interface (CLI) tools for interacting with our API. The primary benefit of this would be easy integration into automated CI/CD workflows of engineering teams.

### API Authentication

In the future we will add include authentication for our API using API Keys and also add rate limiting to prevent security attacks.

### Application outside VCS

The concept of tag immutability can be applied to not only VCS, but also other areas where tagging is used. A popular example is that of [Docker](https://www.docker.com/) tags, where tags point to specific image digests/hashes. As cloud computing continues to be more popular, this will be extremely helpful for [Docker Hub](https://hub.docker.com/) and cloud providers that have a container registry for storing Docker images. This includes [Amazon Web Services](https://aws.amazon.com/), [Google Cloud Platform](https://cloud.google.com/), [Microsoft Azure](https://azure.microsoft.com/), [IBM Cloud](https://www.ibm.com/cloud) and [Oracle Cloud](https://www.oracle.com/cloud/).
