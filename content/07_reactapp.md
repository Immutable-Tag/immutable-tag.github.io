---
weight: 7
title: "The React App"
draft: false
---

## The React App

We have created a frontend using ReactJS to showcase how to:
1. Create a tag immutably
1. Retrieve created tag

<p align = "center">
    <img src="/assets/img/Front_Page.png" alt="tag" width="100%"/>
</p>
<p align="center">
    <i>Home Page</i>
</p>

### Creating a Tag

Upon navigating to the create tag page, we can see a form that requires the following fields:

1. The Repository URL for which we wish to create a tag
1. The tag name
1. The commit which we wish to map the tag to

Optionally, the form also accepts a GitHub token which includes permissions for creating tags in the GitHub repository as well as the blockchain.

<p align = "center">
    <img src="/assets/img/create_tag.gif" alt="create tag" class="middle"/>
</p>
<p align="center">
    <i>Creating a Tag</i>
</p>

A tag is not created in the following scenarios:

1. **Tag already exists** - To guarantee immutability, a tag once created cannot be modified. Therefore, trying to map a pre-exisiting tag to a different commit gives an error message `Tag already exists`.
<p align = "center">
    <img src="/assets/img/tag_already_exists.gif" alt="Tag already exists" class="middle"/>
</p>
<p align="center">
    <i>Tag already exists</i>
</p>

2. **Commit does not exist** - Trying to create a tag with an invalid commit, i.e. a commit which does not exist in the provided Repository URL gives an error message `Commit does not exist`

<p align = "center">
    <img src="/assets/img/bad_commit.gif" alt="Commit does not exist" class="middle"/>
</p>
<p align="center">
    <i>Commit does not exist</i>
</p>

### Retrieving a tag

Once a tag is created in the blockchain, it can be retrieved by providing:

1. The Repository URL for which we created the tag
1. The tag name

<p align = "center">
    <img src="/assets/img/get_tag.gif" alt="Retrieving a tag" class="lmiddle"/>
</p>
<p align="center">
    <i>Retrieving a tag</i>
</p>

Tag retrieval will be unsuccessful if we pass a tag name that does not exist in the corresponding repository URL.

<p align = "center">
    <img src="/assets/img/get_tag_fail.gif" alt="Failed to retrieve tag" class="lmiddle"/>
</p>
<p align="center">
    <i>Failed to retrieve tag</i>
</p>

