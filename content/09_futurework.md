---
weight: 9
title: "Future Work"
draft: false
---

## Future Work

Our team decided to test the idea of tag immutability using Ethereum, which allowed us to quickly build a Proof-of-Concept using smart contracts written in Solidity.

### Compatibility with other blockchains

Our next step is to allow our solution to easily plug in any blockchain that supports smart contracts. We would also like to use permissioned blockchains such as [ResilientDB](https://resilientdb.com/) in order to achieve a higher throughput.

### Compatibility with other VCS

Our current scope is limited to working with git tags for repositories hosted on [GitHub](https://github.com). In the future, we would like our APIs to be easily consumed by not only other git hosting providers such as [GitLab](https://about.gitlab.com/) and [Bitbucket](https://bitbucket.org/product/), but also hosting providers for [Subversion](https://subversion.apache.org/) and [Mercurial](https://www.mercurial-scm.org/) VCS.

### Application outside VCS

The concept of tag immutability can be applied to not only VCS, but also other areas where tagging is used. A popular example is that of [Docker](https://www.docker.com/) tags, where tags point to specific image digests/hashes. As cloud computing continues to be more popular, this will be extremely helpful for [Docker Hub](https://hub.docker.com/) and cloud providers that have a container registry for storing Docker images. This includes [Amazon Web Services](https://aws.amazon.com/), [Google Cloud Platform](https://cloud.google.com/), [Microsoft Azure](https://azure.microsoft.com/), [IBM Cloud](https://www.ibm.com/cloud) and [Oracle Cloud](https://www.oracle.com/cloud/).
