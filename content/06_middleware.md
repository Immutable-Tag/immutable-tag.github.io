---
weight: 6
title: "Node.js Middleware"
draft: false
---

## Node.js Middleware

In our middleware layer, we essentially have a REST API server built using Node.js which is used by our React-based UI layer, and [web3.js](https://web3js.readthedocs.io/en/v1.5.2/)  based integration with our Ethereum SmartContracts backend to facilitate Tag creation and Tag Lookup by the end user using our Blockchain solution.

We also have functions which integrate with Github APIs to validate the accuracy of commits, as well as Tag creation within our Github repository using Github personal access tokens when available. 

Here are some of the important `functions` and `objects` located in the `controllers` folder within `itag.js` file from the [Middleware](https://github.com/Immutable-Tag/Middleware) repository:

1. `createTag(req, res)`:
<br />
This function is the starting point of creating a new tag as requested by the user. It checks with the blockchain if the tag already exists and if not, proceeds to create one in the blockchain. It also calls other functions to check the validity of the commit as well as makes attempts to create the tag on Github, if possible.

2. `checkIfCommitExists(repoUrl, commitId)`:
<br />
This function checks if a given commit exists in the Github repository's default branch as provided by the user. This validation is an important decision point to ensure that the release version referred to by the tag points to a commit that actually exists in the codebase.

3. `createTagOnGitHub(repoUrl, tagId, commitId, githubToken)`:
<br />
This function is only executed to completion if the user has provided their Github [personal access token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token). Upon successful authentication, it creates the tag for the user's repository and also maps that tag against the commit id as the reference to the tag.

4. Function `getTag(req, res)`:
<br />
This method is invoked when a user requests to get tag information form the blockchain. We use web3's Ethereum contract object to call the methods from our SmartContract backend to access the tag information from our blockchain, and if it exists, display the tag information, including the commit hash, to our end user.

5. `web3.js` object:
<br />
[web3.js](https://github.com/ChainSafe/web3.js/blob/v1.5.2/docs/index.rst) is an Ethereum javascript API library that we use to communicate with our SmartContracts backend blockchain layer. We create a `web3` object by connecting to our [Ganache](https://github.com/trufflesuite/ganache-cli-archive) server. We then isolate and set our specific Ethereum account and finally create our web3 `contract` object, through which we can communicate with our Solidity SmartContract backend blockchain layer as needed in the functions described above.

