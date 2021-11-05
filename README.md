# KRYPTOMINTER
Crypto Minting NFTs with Web3, also noted in readme, on Solidity Smart Contracts.


-----
## QUESTIONS

HOW TO programmatically MINT 100's of IMAGES?

HOW TO set up IPFS LINKS in MINT?

HOW TO CUSTOMIZE SMART CONTRACT - for INTERACTIVE NFTs?

----------------------------------------------------

## OVERVIEW

These notes answer the questions above, with code examples in this project, to PROVE THE CONCEPT - of NFT business possibilites. The notes below function as ANSWERS, but also as CURRICULUM - of the LINKS used to learn the content then modify it to fit the needs.

-----------------------
## GOALS
   - The KEY point of this project is for CUSTOM NFTs.
   - Which also means CUSTOM INTERACTIVE SMART CONTRACTS.
   - No matter GATEWAY, or BLOCKCHAIN, Web3 - looking for SOLUTIONS to be CREATIVE with CODE.

SETUP NOTES:

https://medium.com/coinmonks/getting-started-with-ethereum-and-building-basic-dapp-ebb681fb3748


$ npm install -g ganache-cli

$ npm install -g truffle

ganache-cli       //starts ganache 10 accts 100 ETH.

CONNECT METAMASK to ganache network.


#WEB 3 is what I WANT! 
https://ethereum.org/en/developers/tutorials/set-up-web3js-to-use-ethereum-in-javascript/

Web3 interacts with ETH blockchain.
- use in NODE or WEB.
- read blockchain data
- make transaction
- deploy smart contracts.

<script src="https://cdn.jsdelivr.net/npm/web3@latest/dist/web3.min.js"></script>

or 

npm install web3 --save

and

const Web3 = require("web3")

- need to INIT COMMUNICATION 
- library PROVIDER uses RPC on NODE on BLOCKCHAIN
- GANACHE from truffle, with provider Infura or Cloudfare

const web3 = new Web3("http://localhost:8545")

Also using Remix: localhost:8545

Or. // const web3 = new Web3("https://cloudflare-eth.com")


TEST EXAMPLE: web3.eth.getBlockNumber() // gets Latest Block Number

ALL web3.eth - DOCS HERE: https://web3js.readthedocs.io/en/v1.2.6/web3-eth.html (web-eth)

web-eth:
- getUncle
- getTransaction
- getBlock
- web3.eth.Contract 
    - interact with SmartContracts on blockchain.
    - contract object, receives JSON INTERFACE, defines ABI,
    - auto converts calls to low level ABI calls over RPC
    - interact with smart contracts as if they were JavaScript objects


new web3.eth.Contract(jsonInterface[, address][, options])

//Both fungible and non-fungible tokens can be stored in the same smart-contract.

HOW:
- create JSON for every IMG
- folders JSON and IMG
- update OpenSea attributes to ipfs
- "image":"ipfs://"

UPLOAD WHOLE IMGZ FOLDER TO PINATA. 
- results in CID for the FOLDER on IPFS in PINATA!
- copy CID for reference in GATEWAY.
- gateways (always change) keep it out of URL in OS.
- OpenSea replaces the GATEWAY behind ipfs://

"PINNING" in Pinata - once it is pinned, it lives forever on IPFS.

UPLOAD WHOLE JSON FOLDER TO PINATA.

Paste in all the data from REMIX - to get ABI !!!
It is needed to deploy on MAIN NET.

RINKABY TEST NETWORK - in METAMASK

https://testnets.opensea.io

That shows your test NFTS!
