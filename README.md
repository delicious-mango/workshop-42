# Workshop Starton x 42

## Introduction

In this workshop, you'll use Starton, a service to easily connect Web2 applications to blockchain with a simple API.
With it, you can do a lot of things: monitoring on-chain events, deploying an interacting with smart contracts, uploading files to IPFS...
It's a great starting point for web developers who wants to get involved in blockchain and Web3 without a steep learning curve.

Today we will focus on the basics of backend web development with TypeScript, Nest, Prisma & MongoDB by creating an app that track ERC20 transfers.
We will first create and deploy our first own shitcoin with Starton. Then, we will setup the database and finally, setup a watcher to keep track of all tx.

## Setup

To meet the prerequisites, refer to SETUP.md

## Create an ERC20 token

First things first, if we want to track a token, we need a token to track. We can track any existing tokens, but why not create our own ?

### What is a token ?

In the Ethereum world, a token is just a smart contract that store account balances and has different methods to perform operations on them (Get the balance of an account, make a transfer...).

ERC20 smart-contract is a standardized version of _fungible tokens_.
There is a lot of different standards, for example ERC721 is for _non fungible tokens (NFTs)_, or ERC1155 for _semi-fungible tokens_ (multi-copy NFTs)

### How to deploy an ERC20 smart contract ?

This is where Starton comes in. From your project dashboard click on "_Smart Contract_", then on "_+ Smart contract_" and "_Deploy with template_".
As I said before, ERC20 tokens are a standard, so Starton already provides you the smart contract that you can configure and deploy in a few clicks. There is a lot of different templates, feel free to explore them. You can find the Solidity code of the contracts [here](https://github.com/starton-io/smart-contract-templates/tree/master/contracts).

Today we'll be using the **_ERC20 Token with mintable supply template_**. Select it and click on "Deploy". Fill the fields but be careful:

1. Initial supply unit is 0.000000000000000001 token.
2. Choose the Starton KMS wallet for the _Initial Owner Or Multi Sig Contract_.

### Interact with your smart contract

You should now be able to see your freshly deployed token in the list of your deployed smart contracts. You can interact with by clicking on the "_Interact_" button. You can find the documentation of the contract [here](https://docs.starton.com/docs/Smart-contract/ERC20-mintable-Meta). Play with it a little bit and feel free to ask questions !

## Monitor token transfers

Now that we have our token, we want to keep track of all txs that happened in the smart contract.

## Create a watcher

Since there is no method on an ERC20 contract to get historical data, we should keep track of them ourselves. Every time a Transfer happens, the smart-contract emit a Transfer event with useful information. Starton provides a way to be notified every time a specific event happens on a smart contract via _Watchers_.

To set up a watcher, go on the "_Monitor_" tab of your dashboard then click on "_+ Watcher_". Choose "_ERC20 Event transfer_". Give a name and a description to your watcher, Select Polygon Mumbai as the Blockchain, the address of your ERC20 smart contract as the Address to watch, and finally the URL given by ngrok.

### Create the Transfer collection

First of all, we need to define the _shape_ of a transfer to Prisma.
To init Prisma, run the following command:

```
yarn prisma init --datasource-provider mongodb
```

You should now have a .env file. Update the DATABASE_URL variable with your MongoDB connection string.

Add a _Transfer_ model with the following fields:

```
- id
- symbol
- from
- to
- blockNumber
- blockHash
- txHash
- createdAt
```

### Init the Nest project

We'll use Nest as a framework for the rest of the workshop.

To init the project, run the following command:

```
nest new --strict .
```

# Next steps

## create a Transfer module

## create a Transfer controller

## create a Transfer service
