# CODEX Rewards Platform

This repository contains the codebase for the CODEX staking platform, which is divided into two main components: **contracts** and **web**.

## Contracts

This project leverages three smart contract files:

**[CDEX_rewards.sol](./readme/cdex_rewards.sol.md)**
The main smart contract, containing all the business rules of the staking rewards.

**CDEX_ranking.sol**
A separated smart contract to handle the wallet ranking that is displayed on the website.

**[BokkyPooBahsRedBlackTreeLibrary.sol](https://github.com/bokkypoobah/BokkyPooBahsRedBlackTreeLibrary)**
A library used for the sorting functionality of the ranking.