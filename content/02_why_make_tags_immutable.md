---
weight: 2
title: "Why make tags immutable"
draft: false
---

## Why make tags immutable?

<p align = "center">
    <img src="https://imgs.xkcd.com/comics/dependency.png" alt="tag" width="75%"/>
</p>
<p align="center">
    <i>Original comic: <a href="https://xkcd.com/2347/" target="_blank">https://xkcd.com/2347/</a></i>
</p>

The above comic accurately depicts our modern digital infrastructure where dependencies are stacked upon each other like these blocks, each block supporting the weight of all the blocks above it.

Tags allow software developers to determine which versions of code they can reliably use as dependencies in their projects. Many automation systems rely on tags to build and install dependencies.

Therefore, mutating these tags by changing the commits that they point to can cause:

- build failures
- incompatibilites
- bugs
- security vulnerabilities

in the project and other projects that depend on it.

<p align = "center">
    <img src="/assets/img/commit_mapping.gif" alt="tag" width="75%"/>
</p>
<p align="center">
    <i>Mutating a tag can cause issues</i>
</p>
