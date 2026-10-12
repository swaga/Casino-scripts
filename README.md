<h1 align="center" style="display: block; font-size: 2.5em; font-weight: bold; margin-block-start: 1em; margin-block-end: 1em;">
  <br /><br /><strong>Decentralized Crypto Casino Source Codes</strong>
</h1>



Open your own crypto casino with our casino scripts or goldsvet casino! Find exclusive offers on crypto casino source codes on our <a href="https://buycasinoscripts.com/shop/">casino scripts webshop</a> 
Or join our <a href="https://discord.gg/cryptocasino">Discord server</a> or contact us through <a href="https://t.me/script017">Telegram</a>.

![Classiccryptocasino](https://github.com/swaga/Casino-scripts/assets/17531445/ff349329-365c-48fd-acd9-55b64d36d647)
![image1](https://github.com/swaga/Casino-scripts/assets/17531445/bab1764f-11ac-427a-ae3a-db898f94d832)
![image2](https://github.com/swaga/Casino-scripts/assets/17531445/9d140fe9-042d-4623-b21a-abbca3ca2343)
![image 3](https://github.com/swaga/Casino-scripts/assets/17531445/0caf8692-20cc-4b7a-9063-5f8369ea428a)
![image 4](https://github.com/swaga/Casino-scripts/assets/17531445/9ead3e5f-2849-4b24-9106-726554d1b617)
![image 5](https://github.com/swaga/Casino-scripts/assets/17531445/ce6d3819-55f8-4f24-a653-e991bc167802)














## Table of contents

- [Introduction](#introduction)
- [Motivation](#motivation)
- [Features](#features)
- [How is the app implemented?](#how-is-the-app-implemented)
    - [Frontend](#frontend)
    - [Smart Contracts](#smart-contracts)
    - [React and Solidity Conection](#react-and-solidity-conection)
- [Deployed Version](#deployed-version)
- [Installation](#installation)
- [Set Up Your Own Casino](#set-up-your-own-casino)

## Introduction[![](./docs/img/pin.svg)](#introduction)

This is a decentralized crypto casino project. In this casino, unlike most of them, you don't need to be registered, you can connect your wallet and play directly. It also has its own token to play with so people can also trade it. For now the only game available is roulette but I plan to add many more.

## Motivation[![](./docs/img/pin.svg)](#motivation)

Some time ago I became interested in learning how to program smart contracts and to know everything that could be done with them. After learning to program in [Solidity](https://soliditylang.org) I learned to program frontend with [React](https://es.reactjs.org). This is my first big project combining both technologies, so it is my first Web 3 project.

## Features[![](./docs/img/pin.svg)](#features)

- Connect Browser Wallet
- Buy Tokens
- Withdraw Tokens
- Play Roulette
- Responsive UI
- Important Notifications
- Deployed on Polygon Testnet

## How is the app implemented?[![](./docs/img/pin.svg)](#how-is-the-app-implemented)

This project has two main differentiated parts. The frontend built with [React](https://es.reactjs.org) and the backend built with Smart Contracts programmed with [Solidity](https://soliditylang.org).

### Frontend[![](./docs/img/pin.svg)](#frontend)

As I said before, the frontend is made with React. To do it I have used many of its features like hooks, useEffect and much more.

### Smart Contracts[![](./docs/img/pin.svg)](#smart-contracts)

Using Solidity I created 2 Smart Contracts, one called ERC20 (Token.sol), created from 0 only with the functionalities that were going to be used to make it cheaper to deploy. And the other one called Casino, which is in charge of creating the token contract. This contract is the manager of the casino as it allows:

- Buy Tokens
- Withdraw Tokens
- Consult the price of the Token
- Obtain the token's address
- Play roulette
- View your game history

### React and Solidity Conection[![](./docs/img/pin.svg)](#react-and-solidity-conection)

To connect react with Smart Contracts I used the ethers.js library. With this library I created the contractsService.js class that is in charge of loading the contracts and doing all the actions requested by the rest of the application, such as simulating a game, buying tokens, etc. In order to query the contract information I used redux.js that communicates with contractsService.js to ask different aspects of the contract. By doing this, the rest of the frontend code does not have to communicate directly with the contract, only with these two classes.

## Deployed Version[![](./docs/img/pin.svg)](#deployed-version)

If you want to test the deployed casino just go to https://crypto-casino-chi.vercel.app and open the Metamask wallet with an account from the polygon testnet, if you don't know how to do it you can follow this [tutorial](https://docs.unstoppabledomains.com/manage-domains/guides/add-polygon-to-metamask/).

After that you have to click on the red button to connect the website to your wallet and you will be able to test all the functionalities offered by the application.

## Installation[![](./docs/img/pin.svg)](#installation)

If you want to install the casino to modify it is very easy, you just have to clone this repository, you can do it using the IDE or using the console with the command:

```shell
git clone https://github.com/BraisCabo/CriptoCasino
```

After that, you just have to open in the console the address where you just cloned the project and execute the command:

```shell
npm install --force
```

It will take some time and once you are done, if you want to deploy it, just execute:

```shell
npm start
```

This command will deploy the project and open it in a new browser window.

## Set Up Your Own Casino[![](./docs/img/pin.svg)](#set-up-your-own-casino)

If you want to modify the network in which the Smart Contracts are deployed, you must first create a file called .secret in which you copy the private key in hexadecimal format. In Metamask for example you can find it by going to Account Details -> Export Private Key.

Then you have to add the network on which you want to deploy the contracts. For this you have to modify the networks section of the hardhat.config.js file in the root of the project. For example if you want to add binance smart chain:

``` javascript
//Before
  networks: {
    hardhat: {
    },
  },
}

//After
  networks: {
    hardhat: {
    },
    bsc: {
      url: "https://bsc-dataseed.binance.org/",
      chainId: 56,
      gasPrice: 20000000000,
      accounts: [privateKey]
    },
  },
}
```

If you don't know this information just google it and if it is a known blockchain it won't take you more than 2 minutes to find it.

If you want to change the token name, just edit the /src/backend/contracts/Casino.sol file.

```javascript
constructor(){
    //                  name      symbol
    token =  new ERC20("name", "symbol"); //you only have to change this values
    tokenAddress = address(token); //change "Casino" for changing the name
    token.mint(1000000); //Change "CAS" for changing the symbol
}
```

After all this you just have to deploy the contracts using the deploy.js script selecting the network you have added before.

```shell
npx hardhat run src/backend/scripts/deploy.js --network bsc

Deploying contracts with the account: 0x79eF1238F0bA028174ce415E38df91B29eb63dC1
Account balance: 451268700640000000020
Token address: 0x6D324c84553B54e83Eb77C33e5c6d151EeaF4f8B
```

<strong> Important: save the token address so that it can be added to metamask later. </strong>

After all this you just have to launch the web application with the command:

```shell
npm start
```
