---
weight: 5
title: "Smart Contracts"
draft: false
---

## Smart Contracts

Ethereum smart contracts were utilized due to ease of use and plenty of available support provided. Using solidity, a programming language used to code smart contracts in Etheruem, we designed three functions to support our product functionality:
1. Create Tag function - A function that creates tags to be stored in the Ethereum Blockchain. The function takes the repository url, tag name, and the commit hash associated with the tag as input.
2. Get Tag function - A function that retrives the information associated with a specific a repository url and tag name. The function utilizes the tag name and repository url provided by the user.
3. Check Tag function - A function that checks if a repository url and its associated tag name exsits on the blockchain or not. The function returns a true or flase depending on the tag exsits in the blockchain. 

Additionally, all tags stored in a private mode to ensure that user permissions are maintained for the repositories. 

We utilized the truffle framework to develop our solution since it provides a development and testing environment, among other things. Ganache was also utilized as our personal blockchain for development and deployment of the smart contracts. To understand more about Truffle and Ganache, you can refer to the following links:
<p align = "left">
    <i>Truffle: <a href="https://trufflesuite.com/">https://trufflesuite.com/</a></i>
    <i>Ganache: <a href="https://trufflesuite.com/ganache/">https://trufflesuite.com/ganache/</a></i>
</p>
