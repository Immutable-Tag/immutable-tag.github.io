---
weight: 7
title: "The React App"
draft: false
---

## The React App

<p align = "center">
    <img src="/assets/img/Front_Page.png" alt="tag" width="100%"/>
</p>
<p align="center">
    Home Page
</p>
To achieve the basic functionality of  Tag Immutability, we have created two features

1. Create a Tag
1. Retrieve a Tag 


<p align = "center">
    <img src="/assets/img/Token_Create_Combine.png" alt="tag" width="100%"/>
</p>
<p align="center">
    Tag Creation along with Github Token
</p>
For a Successful Tag creation,we have to input a Repository url, unique Tag id and existing commid id in the repository. There are two ways of creating a Tag.

1. With Github Token - Once we provide the required information along with github token, Tag gets created on Blockchain as well in corresponding github repository. 
1. Without Github Token - Tag gets created only on Blockchain.

<p align = "center">
    <img src="/assets/img/Error_Create.png" alt="tag" width="100%"/>
</p>
<p align="center">
    Error scenarios during Tag Creation
</p>
Tag is not created in the following scenarios

1. Commit does not exist - This failure occurs when we input commit id which is not present in the corresponding input repository url.
1. Tag already exists - One tag name can map to only one commit id. If we input the tag name which already exists in the blockchain, tag creation will be unsuccessful. Thus immutability is maintained.

<p align = "center">
    <img src="/assets/img/Retrieve_Combine.png" alt="tag" width="100%"/>
</p>
<p align="center">
    Successful Tag Retrival
</p>
Tag information can be retrieved successfully by inputing repository url and the Tag id present in the repo, irrespective of the token. The retrival displays the repository url, tag id and the corresponding commit hash.

<p align = "center">
    <img src="/assets/img/Error_Retrieve.png" alt="tag" width="100%"/>
</p>
<p align="center">
    Error scenarios during Tag Retrival
</p>
Tag retrival will be unsuccessful, when we input the tag name that does not exist in the corresponding repository url. Hence it throws "Tag not exist" error.

