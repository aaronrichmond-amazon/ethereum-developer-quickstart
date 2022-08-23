# ethereum-developer-quickstart
A quickstart for beginner Ethereum Developers.

# Ethereum Developer Quickstart

## Welcome
There are a lot of courses and guides out there. Yet after purchasing some and trying a lot of blog posts, tutorials, etc. This is the guide I would have wanted to begin to understand the basics and build quickly in about 30 minutes. Links are included if you want to dive deeper.

## How to Set Up Your Environment

### 1. Node.js

First, make sure you have [Node.js](https://nodejs.org/en/) and the NPM package manager installed.

After installation, check to see both are successfully installed at your terminal/command line:

```
node --version
```

If you see a response with a version, such as:
```
v16.16.0
```
... then you're good.

Next check for NPM:

```
npm --version
```

Similarly if you see a response with a version, such as:
```
8.11.0
```
... then you're good.

Create a new directory and node project:

```
mkdir eth-dev-quickstart
```

then:
```
cd eth-dev-quickstart
```

Next, create a new node project.

```
npm init
```

Follow the prompts, take the defaults or edit as you like.

Your output should look something like this:

```
{
  "name": "eth-dev-quickstart",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC"
}
```

Now for the blockchain development.

## 2. Developing with Hardhat

We use the [Hardhat](https://www.hardhat.org) command line IDE for development as it is a current industry standard for Ethereum builders. It comes with a clear folder/file structure, command line and testing tools, and works well with React-based UI frameworks. If you're interested, you can also look at alternative IDEs such as [Remix](https://remix-ide.readthedocs.io/en/latest/) and [Foundry](https://book.getfoundry.sh/).

Simply install Hardhat like so:

```
npm install --save-dev hardhat
```

The output should look something like:

```
added 306 packages, and audited 307 packages in 23s

58 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities
```

Once installed, run

```
npx hardhat
```

Take the defaults or edit as you like.

See the [Hardhat Overview](https://hardhat.org/hardhat-runner/docs/getting-started#overview) documentation for more. The above commands were copied from the docs.

### Programming Language and Frameworks
For the 2 Pizza DAO, we will use JavaScript (optionally TypeScript) with React-based frameworks for the front end.

__Solidity__ (.sol) files are used for smart contracts. See documentation here: https://docs.soliditylang.org/

__Ethers__ is used for interacting with Ethereum blockchain via JavaScript. See documentation here: https://docs.ethers.io/

### Contracts

The heart of your dApps (decentralized applications) are smart contracts. In the Ethereum world these are generally written as Solidity (.sol) files. They need to be compiled. Run the below command to compile the included .sol files.

```
npx hardhat compile
```

You'll see the below response upon success.

```
Compiled 2 Solidity files successfully
```

### Test-driven development

Hardhat includes test and script tools to help you build and test your contracts with Test-Driven Development (TDD) and Behavior Driven Development (BDD) - best practices in software developement. Try the below...

```
npx hardhat test
```

You'll see an output akin to below, demonstrating the events and states you can test in your contracts.

```
Lock
    Deployment
      ✔ Should set the right unlockTime (4506ms)
      ✔ Should set the right owner
      ✔ Should receive and store the funds to lock
      ✔ Should fail if the unlockTime is not in the future (56ms)
    Withdrawals
      Validations
        ✔ Should revert with the right error if called too soon (89ms)
        ✔ Should revert with the right error if called from another account (134ms)
        ✔ Shouldn't fail if the unlockTime has arrived and the owner calls it (139ms)
      Events
        ✔ Should emit an event on withdrawals
      Transfers
        ✔ Should transfer the funds to the owner (58ms)


  9 passing (5s)
```

Open a code editor, open the <samp>test</samp> folder and take a look at the <samp>Lock.sol</samp> file to get a sense of how tests are written.

Note that there are 3 libraries used:
1. hardhat-network-helpers -- which includes things like logging and other methods. See more at the [docs](https://hardhat.org/hardhat-network/docs/reference).

2. ethers -- currently the best javascript library for interacting with ethereum chains. See more at the [docs](https://docs.ethers.io/v5/).

3. chai -- for testing assertions. See the <samp>expect</samp> calls in the file. More at the [docs](https://www.chaijs.com/).

### Start Local Hardhat Network

```
npx hardhat node
```

You'll see a server start with accounts and private keys generated for you as a local network to build and test with. Something like the below...

```
Started HTTP and WebSocket JSON-RPC server at http://127.0.0.1:8545/

Accounts
========

WARNING: These accounts, and their private keys, are publicly known.
Any funds sent to them on Mainnet or any other live network WILL BE LOST.

Account #0: 0xf39Fd6e51aad88F6F4ce6aB8827279cffFb92266 (10000 ETH)
Private Key: 0xac0974bec39a17e36ba4a6b4d238ff944bacb478cbed5efcae784d7bf4f2ff80

Account #1: 0x70997970C51812dc3A010C7d01b50e0d17dc79C8 (10000 ETH)
Private Key: 0x59c6995e998f97a5a0044966f0945389dc9e86dae88c7a8412f4603b6b78690d
```

See [Hardhat Network](https://hardhat.org/hardhat-network/docs/overview) docs for more.

## 4. MetaMask

There are many blockchain wallets to choose from, but we will use [MetaMask](https://metamask.io/), one of the most popular.

Download and install, following the instructions. It is a browser extension. Note you will need to store your password and secret words in a SAFE place so you can log in and join other blockchain networks.

Once installed, log into your account (your wallet address) with your username/password or private keys. If not connected by default, connect to <samp>Localhost:8545</samp>. You should see something like this:

![MetaMask Localhost:8545](images/metamask-localhost8545.png).

Give yourself some ethereum from one of the local accounts. Click the "circle" image on the top right to import one of the local accounts. You should see a screen below...

![MetaMask Import Account](images/metamask-importAccount.png).

Now copy one of the private keys listed in the terminal list of local accounts, and click "Import".

![MetaMask Import Account](images/metamask-localAccount.png).

Look who's got 10,000 ETH! :)
