# Setup

## Metamask

First of all, let's generate our key pair ! To do that we use a _wallet_. It's a program that can generate and store key pairs, sign transactions, and send them to a node to a node provider to broadcast it on the blockchain.

There is a lot of different wallets, but today we'll use MetaMask, one of the most famous.
It is a web browser extension that you can download [here](https://metamask.io/download/).
Follow instructions at installation.

Metamask can be used on many blockchains, but today we'll be using the Polygon testnet.

You can add it to your Metamask [here](https://chainlist.org/chain/80001). Connect your wallet to the website and click on "_Add to Metamask_". Then, approve the Network change in the Metamask extension.

## Node

Since we'll code in TypeScript, we need a runtime environment. The most popular is Node.js. You can easily manage and download Node.js versions with `nvm`.

`nvm` stands for _Node Version Manager_, it's a CLI. You can download it by running this command:

```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash
```

Once the CLI downloaded, run this command to use the latest lts (long term support) verion of Node.js:

```
nvm install --lts
nvm use --lts
```

### Dependencies

- Nest
  ```
  yarn global add @nestjs/cli
  ```
- Prisma
  ```
  yarn add -D prisma
  ```

## Postman

Postman is a tool to easily make HTTP calls.
You can download it from [here](https://www.postman.com/downloads/).

## Mongo Atlas

For our database we will use MongoDB running in a cloud instance of _Mongo Atlas_, the cloud solution of MongoDB. To start using Mongo Atlas, you must [create an account](https://www.mongodb.com/cloud/atlas/register).
When you have created your account, go to "Database" on the left pannel, and "create".
Select a free shared instance and create a cluster.
Now that we have our database running, we need a tool to visualize the data stored inside.
To do so, we will use [Mongo Compass](https://www.mongodb.com/try/download/compass), a database explorer for MongoDB.

When you have installed Compass, We need to connect it to our Atlas instance. In order to do so, you'll need a _connection string_. You can find it in Mongo Atlas under "_Database_" -> "_Your instance_" -> "_Connect_" -> "_Compass_". Copy the connection string and replace`<password>` with your own Atlas password.
On Mongo Compass, click on "_New connection_", paste your connection URL and click on "_Connect_". If everything went well, you should be connected to your instance and see a list of database in the pannel on the left.

## Starton

In this workshop, we'll use Starton, a service to easily connect Web2 applications to blockchain with a simple API.
With it, we can do a lot of things: monitoring on-chain events, deploying an interacting with smart contracts, uploading files to IPFS... It's a great starting point for web developers who wants to get involved in blockchain and Web3 without a steep learning curve.

### Get an API key

To start, we need to get Starton API keys. To do so, create first an account on https://app.starton.com/.
Then, select your Default Project and click on the _Developer_ tab. To create an API key, click on "+ API key", give your key a name and an optional description. After clicking on submit, your API key will be displayed.

```
CAUTION ! YOUR API KEY WILL BE DISPLAYED ONLY ONCE. COPY IT IN A SAFE PLACE.
```

### Create a wallet in Starton's KMS

To manage our smart-contracts we'll use a wallet hosted by Starton's _KMS (Key Management System)_.
On your Dashboard, go on the _Wallet_ tab and under _WALLET IN KEY MANAGEMENT SYSTEMS_, click on "_+ Wallet_"

## ngrok

During this workshop we'll develop in a local dev environment that uses local network. However, Starton needs a public endpoint to send us data. To be able to receive Starton HTTP requests, we need a tool that provides us with a public endpoint URL, and forward it to our local network. This can be done using _ngrok_.

First, [create an ngrok account](https://ngrok.com/). Then, follow the Setup & Installation instruction on the website. You'll need to download the ngrok CLI.

# You are now ready ! 🚀
