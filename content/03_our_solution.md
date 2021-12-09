---
weight: 3
title: "Our solution"
draft: false
---

## Our solution

Our solution uses the tamper-evident and tamper-resistant nature of [blockchain](https://en.wikipedia.org/wiki/Blockchain) to guarantee tag immutability and provide assurance to users that their products will continue functioning with the same level of reliability.

{{< notification type="info" title="">}}
If a repository has a tag <code>v1.0.0</code> which points to commit <code>b06cdb0</code>, then it should not be possible to delete or modify it by pointing it to a different commit <code>49a68cd</code>. This way, users who were depending on the changes that were made until commit <code>b06cdb0</code> will not be pointed to the potentially buggy and incompatible commit <code>49a68cd</code>.
{{< /notification >}}

Our solution leverages blockchain and [smart contracts](https://en.wikipedia.org/wiki/Smart_contract) to:

- Create tags immutably
- Retrieve created tags

We have exposed RESTful APIs so that third-party applications can easily use our solution to provide tag immutability.

Since most VCS support the concept of tags, they can make use of our tool-agnostic solution to support tag immutability in their products. Source-code repository hosting services such as [GitHub](https://github.com/), [GitLab](https://about.gitlab.com/), [Bitbucket](https://bitbucket.org/product), and [SourceForge](https://sourceforge.net/) can also provide their users with tag immutability and since these host most of the world’s open-source projects, the benefit can be extended to millions of developers and end-users worldwide.

<p align = "center">
    <img src="/assets/img/solution.png" alt="tag" width="100%"/>
</p>
<p align="center">
    <i>Our solution</i>
</p>
