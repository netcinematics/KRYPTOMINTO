# KRYPTOMINTER
Crypto Minting NFTs with Web3, also noted in readme, on Solidity Smart Contracts.


-----
## QUESTIONS

1. HOW TO programmatically MINT 100's of IMAGES?

2. HOW TO set up IPFS LINKS in MINT?

3. HOW TO CUSTOMIZE SMART CONTRACT (lazy) 

4. HOW TO create INTERACTIVE NFTs? LNKz TXTz, BITZ.

4. HOW TO BATCH MINT, or dApp MINT on ETH MAINNET-.

----------------------------------------------------

## OVERVIEW

These notes answer the questions above, with code examples in this project, to PROVE THE CONCEPT - of NFT business possibilites. The notes are ANSWERS, and also CURRICULUM - for SKILLS and REVIEW.

-----------------------
## GOALS
   - The KEY point of this project is for ADVANCED CUSTOMIZATION of NFTs.
   - Which also means CUSTOM INTERACTIVE SMART CONTRACTS.
   - No matter GATEWAY, or BLOCKCHAIN, Web3 - looking for SOLUTIONS to be CREATIVE with CODE.

SETUP NOTES:

https://medium.com/coinmonks/getting-started-with-ethereum-and-building-basic-dapp-ebb681fb3748

"Decentralized Web Stack"

$ npm install -g ganache-cli

$ npm install -g truffle

1) ganache-cli       //starts ganache 10 accts 100 ETH. FAKE ACCOUNTS-.

2) Listening on 127.0.0.1:8545

3) METAMASK CONNECT to ganache network. - use Ganache-CLI as METAMASK network
In Metamask dropdown SELECT -> “Localhost 8545"
Later this could also be "Rinkeby Test Network" or "Main Ethereum Network"

4) METAMASK ACCOUNTS - color circle right top -> Import Account, and copy PRIVATE KEY from Ganache-CLI.  — 0xc8763205e691a0e9f75c70a33c6f03d74a3eb4f5eabb3cc2df2e1418f5ae009a.


#WEB3 is what I WANT! 
https://ethereum.org/en/developers/tutorials/set-up-web3js-to-use-ethereum-in-javascript/

Web3 interacts with ETH blockchain.
- use in NODE or WEB.
- read blockchain data
- make transaction
- deploy smart contracts.

WEB3 - 3 ways:
<script src="https://cdn.jsdelivr.net/npm/web3@latest/dist/web3.min.js"></script>

npm install web3 --save

const Web3 = require("web3")

- need to INIT COMMUNICATION 
- library PROVIDER uses RPC on NODE on BLOCKCHAIN
- GANACHE from truffle, with PROVIDER Infura or Cloudfare

 GANACHE-CLI (personal BLOCKCHAIN) to deploy contracts, develop applications, and run tests on PERSONAL BLOCKCHAIN.

 TRUFFLE - dev environment, test framework, asset pipeline to EVM.
 - deploy contracts, swap contracts (migrate), attach front-end to contracts.
 - compile and deploy Smart Contracts, inject  into web apps, and also dev front-end for DApps

METAMASK - "ethereum light client" - interact with BLOCKCHAIN without downloading PERSONAL BLOCKCHAIN-. Interact with dApps.

//Using GANACHE as PROVIDER
const web3 = new Web3("http://localhost:8545")

Using REMIX: localhost:8545

GANACHE - ganache-cli 
Faucet: METAMASK IMPORT ACCOUNT - PRIVATE KEY.
100 ETH.

USING CLOUDFLARE PROVIDER
// const web3 = new Web3("https://cloudflare-eth.com")

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

PINATA - IPFS - UPLOAD WHOLE IMGZ FOLDER TO PINATA. 
- results in CID for the FOLDER on IPFS in PINATA!
- copy CID for reference in GATEWAY.
- gateways (always change) keep it out of URL in OS.
- OpenSea replaces the GATEWAY behind ipfs://

"PINNING" in Pinata - once it is pinned, it lives forever on IPFS.

UPLOAD WHOLE JSON FOLDER TO PINATA.

REMIX - Paste in all the data from REMIX - to get ABI !!!
It is needed to deploy on MAIN NET.

RINKABY TEST NETWORK - in METAMASK
RINKABY TEST NET RUNNING:
https://testnets.opensea.io
That shows your test NFTS!

Use ORACLE to get external data into smart contract.
Do not use a single centralized oracle (ever).
Unlock full potential of smart contracts.

Also HARDHAT and NFTSTORAGE (pinata).

//GETTING STARTED WITH TRUFFLE:
//1) init truffle in project dir
$ mkdir ethdapp
$ cd ethdapp
$ truffle unbox webpack

//2) GANACHE-CLI, deploy contracts
$ truffle compile
$ truffle migrate
Once the migration is complete run dApp. To run dApp
$ cd app
$ npm run dev

//3) 
http://localhost:8080/ 


REMIX is so awesome!
DEBUG JS SCRIPTs!



SMART-CONTRACTS: 

- OpenZepplin - just in time - lazy minting

- Ethers has a Contract API (opens new window)that abstracts over the details of the blockchain and lets us interact with smart contracts as if they were regular JavaScript objects named

- contract sent transactions, triggers events to run with transaction data.

JSON-RPC either Web3 or Ethers.
<!-- 
<script src="https://cdn.ethers.io/lib/ethers-5.2.umd.min.js"
        type="application/javascript"></script>

         -->

- To wire up a JavaScript object to a deployed smart contract with Ethers, we need two things: the address of the contract, and its Application Binary Interface (ABI).

-  ABI value from Etherscan and address for deployed smart contract, and MetaMask providing access to the Ethereum blockchain via the window.ethereum object. That's all Ethers needs to provide a Web3 layer for you to make smart contract calls with JavaScript.


METADATA SCHEMA (standard) - ERC-721
{
    "title": "Asset Metadata",
    "type": "object",
    "properties": {
        "name": {
            "type": "string",
            "description": "Identifies the asset to which this NFT represents"
        },
        "description": {
            "type": "string",
            "description": "Describes the asset to which this NFT represents"
        },
        "image": {
            "type": "string",
            "description": "A URI pointing to a resource with mime type image/* representing the asset to which this NFT represents. Consider making any images at a width between 320 and 1080 pixels and aspect ratio between 1.91:1 and 4:5 inclusive."
        }
    }
}

META-DATA SCHEMA (standard) "multi-token" extends ERC-721 
- issue many types of token from the same smart contract.

Hardhat and Ganache-CLI both do
eth_blockNumber
net_version (16)
eth_blockNumber
net_version (3)
eth_blockNumber
net_version
eth_blockNumber

https://github.com/protocol/nft-website/blob/main/docs/tutorial/lazy-minting.md :
lazy minting do not call contract function directly, a cryptographic signature of data is made by CREATOR, from Ethereum account private key.

It is signed data, that acts as a "voucher", to be "redeemed" for an NFT. The voucher is a hash of the actual NFT, and can contain extra data off blockchain.

"The signature proves that the NFT creator authorized the creation of the specific NFT described in the voucher."

buyer calls a "redeem" function to redeem the signed voucher. If the signature is valid and belongs to an account that's authorized to mint NFTs, a new token is created based on the voucher and transfered to the buyer.

struct NFTVoucher {
  uint256 tokenId;
  uint256 minPrice;
  string uri;
  bytes signature;
}

voucher writes the unique tokenId, and the uri to the blockchain.

 "air-dropping" NFTs to specific accounts, your voucher could include an address recipient field instead of a minPrice, and redeem function checks msg.sender == voucher.recipient

 EIP-712 defends against "replay attack"

 const lazyminter = new LazyMinter({ myDeployedContract.address, signerForMinterAccount })
 //provide address of deployed contract and an ethers.js Signer for NFT creator's private key

ERC-721: - original contract for: immutable, transparent, unique TOKEN. Non-divisible. 
    single transactable object. transferrable. ownable. Creates and Tracks unique NFTs.
    Expensive when traffic is high.

 ERC - 1155 : "lazy load" "multi-token"
https://eips.ethereum.org/EIPS/eip-1155
https://docs.openzeppelin.com/contracts/3.x/erc1155
    efficient to use in "batch token" transfers

 ERC-1155 Multi Token Standard allows for each token ID to represent a new configurable token type, which may have its own metadata, supply and other attributes

 - transferring multiple token types at once , "batch"

 - Trading (escrow / atomic swaps) of multiple tokens,removes need to “approve” individual token contracts separately

 - mix multiple fungible or non-fungible token types in a single contract. IMG, TXT, SND, VID.

 -  `TransferSingle` or `TransferBatch`

 - ZERO ADDRESS :         
        When minting/creating tokens, the `_from` argument MUST be set to `0x0` (i.e. zero address).
        When burning/destroying tokens, the `_to` argument MUST be set to `0x0` (i.e. zero address).  


What I am looking for???
event TransferBatch(address indexed _operator, address indexed _from, address indexed _to, uint256[] _ids, uint256[] _values);

ERC 20 - is fungibility. dont care which - just how much. like gummi worms, not jelly beans.
https://docs.openzeppelin.com/contracts/3.x/erc20

ERC20 tokens useful for things like a medium of exchange currency, voting rights, staking, and more.

ERC 1155
a single smart contract to represent multiple tokens 
a single ERC1155 token contract can hold the entire system state, reducing deployment costs and complexity



ESTIMATE $400.00

Not doing that. Off to....

ERC 1155 to POLYGON on OPENSEA (example)
https://docs.opensea.io/docs/polygon-basic-integration

Sample implementations of the above can be found here:
https://github.com/ProjectOpenSea/meta-transactions/tree/main/contracts

Read more about gassless transactions and meta-transactions here:
https://docs.openzeppelin.com/learn/sending-gasless-transactions

https://github.com/ProjectOpenSea/opensea-erc1155


SWITCH TO POLYGON NETWORK-------------------

CONNECT METAMASK TO POLYGON FOR REMIX:

1 MetaMask, Switch Network to POLYGON.

2 Need to have MATIC

3 Upper Left of Wallet "not connected"

4 dot button > Connected Sites (connect to REMIX)

5 Upper Left > says CONNECTED.

6 In REMIX, ENVIRONMENT change to "Injected Web3"

   - which is the METAMASK EXTENSION on POLYGON.

7 "Custom (137) network" - is the polygon network.

8. DEPLOY (careful)

   - _NAME: 
   - _SYMBOL: 
   - _INITBASEURI: 


9. COPY-BUTTON

   - CLICK BTN to SAVE DEPLOY DATA ABI - before TRANSACT!
   - SAVE that data into FOLDER

   /deployed_contract_polygon/name.txt

10. TRANSACT - wallet confirm - PAY MATIC.

11. DEPLOYED CONTRACT - bottom left of REMIX.

     - the contract is forever on the blockchain (minted/mined).

12. COPY THE CONTRACT ADDRESS - this is your address.

13. PASTE CONTRACT ADDRESS into - POLYGONSCAN.COM

14. VERIFY CONTRACT ON POLYGONSCAN.

     - TRICKY! This is where the "trailing zeros" is used.
     - PASTE trailing zeros. Click Verify. 

15. AFTER VERIFY CONTRACT

    polygonscan can: MINT, READ and WRITE to CONTRACT.

16. REVIEW the COLLECTION on OpenSea (minted in your wallet).


721 - CONTRACT
https://docs.openzeppelin.com/contracts/3.x/erc721


Be sure to check OPENZEPPELIN 1155 as well, from CONTRACT WIZARD.

Other VERY IMPORTANT THINGS.... so tricky.

AFTER IPFS 44 IMGZ and 44 JSONs with updated website.

AFTER RINKEBY FAUCET email account #4 for ETH. 18.75 eth.

AFTER REMIX DEPLOY TO RINKEBY, of 1155 - with URI OVERRIDE,

THEN GO TO OPENSEA - log in under METAMASK ACCOUNT #4.

RESULT -> It shows the 44 mints! To TEST.

http://testnets.opensea.io/account (from the owner account [CONNECT])

SHOWS MINTS.

ALSO ANOTHER WAY to SEE MINTS is:
https://opensea.io/get-listed
Click TESTNET, search for contract #

//----------------------------
AFTER IPFS POST IMGZ
RERUN INDEX 2 to change ipfs://
POST JSON on IPFS with IMG url.
JSON URL goes into SOLIDITY CONTRACT constructor().
721 can parse out the {id} in uri.
1155 cannot parse out {id}, override URI.
REMIX test uri to be ipfs://1234/1.json
Need to connect Ganache, Rinkaby, JS VM, and wallets with faucet funds to:
COMPILE, DEPLOY to TEST NETWORK.
TEST OpenSea from MetaMask login to testnets.opensea.io

//---DEPLOY TO POLYGON
METAMASK, switch to POLYGON NETWORK.
Account needs MATIC. MATIC on ETH wallet, not Polygon account.
TRY 1 to SEND from ETH main to Polygon account - $50.00!
TRY 2 FUND from COINBASE - $67.00
TRY 3 http://wallet.matic.network   /bridge TRANSFER MATIC TOKEN to MATIC $100.00
CONNECT Matic account to REMIX. To Inject it.
REMIX "Injected Web3", "Custom (137) network, is POLYGON.
ON ACTUAL DEPLOY TO MAIN POLYGON NETWORK - need to VERIFY later (721).
So COPYBYTE Code Just before TRANSACT on 721.



1st ACTUAL DEPLOY TO POLYGON MAINNET - 1155 BASIC 44 mints !!!
0x33a062894Ccf369583159dB6A23370D8266D4174
https://polygonscan.com/address/0x33a062894Ccf369583159dB6A23370D8266D4174
https://polygonscan.com/tx/0x7ee81fb0263885b0d19f34b9eda89fcf6e2b6f8be10dc12ee69eb8d61b941d57
Transaction fees were 0.11 MATIC $.20! (after >100.00 geeting matic into polygon wallet) Solution there was through crypto.com - all the others big problems. 

ABI for VERIFY 602082015250565b7f455243313135353a2069647320616e6420616d6f756e7473206c656e6774682060008201527f6d69736d61746368000000000000000000000000000000000000000000000000602082015250565b600060443d1015612e2e57612eb1565b612e36612546565b60043d036004823e80513d602482011167ffffffffffffffff82111715612e5e575050612eb1565b808201805167ffffffffffffffff811115612e7c5750505050612eb1565b80602083010160043d038501811115612e99575050505050612eb1565b612ea882602001850186612829565b82955050505050505b90565b612ebd81612741565b8114612ec857600080fd5b50565b612ed481612753565b8114612edf57600080fd5b50565b612eeb8161275f565b8114612ef657600080fd5b50565b612f02816127ab565b8114612f0d57600080fd5b5056fea264697066735822122058e9a3cf3f884a204612dafc2e1edee382574eaeabcee937b4c28ab2a0e77b4e64736f6c63430008070033697066733a2f2f516d5a7a735433527253376632317354447879374b373556426f59534156357641666772327a4d545441776973552f7b69647d2e6a736f6e

GETH TRACE of GAS FEES:
https://polygonscan.com/vmtrace?txhash=0x7ee81fb0263885b0d19f34b9eda89fcf6e2b6f8be10dc12ee69eb8d61b941d57


TEST: go to https://opensea.io/account/
It creates a COLLECTION with a strange title.