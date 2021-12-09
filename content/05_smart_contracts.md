---
weight: 5
title: "Smart Contract"
draft: false
---

## Smart Contract

We have used [Ethereum smart contracts](https://ethereum.org/en/developers/docs/smart-contracts/) because of their ease of use and widely available support. Using [Solidity](https://docs.soliditylang.org/), a programming language used to code smart contracts in Etheruem, we have created a `struct` to store all details about tags:

```solidity
contract ImmutableTag {

    struct Tag {
        string repoURL;
        string tagID;
        string commitHash;
    }

    ...
}
```

We then have a `mapping` (equivalent to a dictionary or hashtable in other programming languages) of `string` to `Tag` objects inside the smart contract:

```solidity
    mapping(string => Tag) private tags;
```

By using a `mapping` instead of a array, we can look up tags in `O(1)` time. The key for this mapping is a concatenation of the repository URL and the tag.

For example, if we want to create a tag `v1.0.0` in the repository `https://github.com/Immutable-Tag/SmartContacts`, then the key in the `mapping` will be `"https://github.com/Immutable-Tag/SmartContacts_v1.0.0"` and the value will be the following `Tag` object:

```solidity
{
    repoURL: "https://github.com/Immutable-Tag/SmartContacts"
    tagID: "v1.0.0"
    commitHash: "66190b9fc987cb12c3a302c84123122e68ef6450"
}
```

We have added three functions to support our product functionality:

1. **createTag** - This function creates tags to be stored in the Ethereum Blockchain by adding it to the mapping `tags`. The function accepts the repository URL, tag, and the commit to be associated with the tag as parameters.

```solidity
function createTag(string memory _repoURL, string memory _tagID, string memory _commitHash) public {
    string memory key;
    key = string(abi.encodePacked(string(abi.encodePacked(_repoURL, "_")), _tagID));
    tags[key] = Tag(_repoURL, _tagID, _commitHash);
}
```

2. **getTag** - This function takes a repository URL and tag ID and looks up in the `mapping` to retrieve the tag's details.

```solidity
function getTag(string memory _repoURL, string memory _tagID) public view returns (Tag memory) {
    string memory key;
    key = string(abi.encodePacked(string(abi.encodePacked(_repoURL, "_")), _tagID));
    return tags[key];
}
```

3. **checkTag** - This function checks if a tag already exsits on the blockchain or not. If the tag exists in the `mapping` then this function returns `true`, otherwise it returns `false`.

```solidity
function checkTag(string memory _repoURL, string memory _tagID) public view returns (bool) {
    string memory key;
    key = string(abi.encodePacked(string(abi.encodePacked(_repoURL, "_")), _tagID));
    return bytes(tags[key].commitHash).length != 0;
}
```

We are using the [Truffle Suite](https://trufflesuite.com/) for developing our solution as it provides a development environment, testing framework and asset pipeline for blockchains using the Ethereum Virtual Machine (EVM). It also provides features like built-in Smart Contract compilation, linking, deployment and binary management and automated contract testing. We used [Ganache](https://trufflesuite.com/ganache/) to simulate an Ethereum blockchain and deployed our smart contract to it.

You can find the entire code and documentation for our smart contract in [this GitHub repository](https://github.com/Immutable-Tag/SmartContracts).
