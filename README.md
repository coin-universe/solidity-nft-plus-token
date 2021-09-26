![HOW IT'S WORK?](https://github.com/coin-universe/protofire/raw/master/image/image.png)

```PAGE is ERC20 token name.```

### PAGE_ADMIN: 
https://rinkeby.etherscan.io/address/0xcEB62e99d856ead35e6DDe20bFd3924DcebB4A03

- **Deploy separately.**
- during deployment, it creates a PAGE_MINTER contract and determines the TreasuryAddress after deployment, PAGE_TOKEN and PAGE_NFT, the contract is activated by the INIT function, in which the addresses of the PAGE_TOKEN and PAGE_NFT contracts are passed as parameters.
- OPTION 1 - TreasuryAddress setting. You can change the percentage and address.
- OPTION 2 - setting the base domain for NFT
- OPTION 3 - adding, deleting and setting the minter. This is necessary to add new contracts that enhance the capabilities of the PAGE platform.
- OPTION 4 - setting the price for burning NFT in PAGE tokens. 

**owner function** The standard function of openzeppelin - assigns the management of contracts to a specific administrator, if in the platform we come to the final settings, the owner can be deleted permanently, and the current settings can be frozen. 


### PAGE_TOKEN:
https://rinkeby.etherscan.io/address/0x65A2E2E489FDE1857E12163A9f2f7640c0d0F403

- **Deploy separately.**
- The permanent admin of the contract is the PAGE_MINTER contract. Responsible for issuing new tokens.
- An additional function, the idea of which is borrowed from the erc777 contract, SafeDeposit and SafeWithdrow, allows you to transfer tokens inside a safe list of contracts, without Approval. In particular, this is necessary for the PageMarket contract so that the user saves on commissions. 

### PAGE_NFT: 
https://rinkeby.etherscan.io/address/0xa63F7ecD41b86B5609Da5cb891Eb10065F1364b5

- **Deploy separately.**
- Responsible for the creation of the NFT.
- Allows you to leave comments.
- Allows you to burn (current owner only) NFTs your NFTs.
- Has a function in which not only the owner but also the creator of the NFT is remembered (this is a difference from other NFT collections) 

### PAGE_MINTER:
https://rinkeby.etherscan.io/address/0xcE65382a0a49C8b3Cf3C1C446d15DBAA14FCAb86

- **Deploy with PAGE ADMIN contract at creation time.**
-The contract allows the issuance of new PAGE tokens. 
- setMinter - registers the actions with which you can mint coins, while specifying: the name of the role in text format, the address of the contract that can mine coins. For mining, you need to transfer the key registered in advance through setMinter and the list of addresses to which the coins will be mined. 
- **IMPORTANT.** Each minting function credits 10% (in can be change in PAGE_ADMIN) of mined coins to TreasuryAddress. 
- BURNED FUNCTION. Coins can be burned using 2 functions: smart burning (burns 90% of the rest transfers to TreasuryAddress) and burning (just burns coins). 



### PAGE_COMMENT:
https://rinkeby.etherscan.io/address/0x3d1F2E600ef2a6668900316CE222999cC4c60575

- **Deploy with the PAGE_MINTER contract while creating an NFT with a comment function.**
- the comment is set in the corresponding function in the PAGE_NFT contract
- all comments are created as a record in the blockchain, with the corresponding ID. By comment ID, you can get the comment, the commentator's address, and the comment status (positive or negative). 



## Examples of transactions:

NFT creation :
https://rinkeby.etherscan.io/tx/0xc41fa66fb8536d2aaed14d2c5ecf309804bf7f3dfde5f90bc0b3db9c3f4bbf3c

**PAGE reward distribution**
- 10% => to the company wallet
- 90% => to the creator

**adding a comment to the NFT:**

https://rinkeby.etherscan.io/tx/0x08dba14fb10a6711d31895a3b5a32385868f09dfb1423048d7e5119e14378fda

**PAGE reward distribution**
- 10% => to the TreasuryAddress
- 30% => to the creator
- 30% => to the owner
- 30% => commentator 
