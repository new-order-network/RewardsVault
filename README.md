# Rewards distribution contract

This contract is a contribution to the NewOrder DAO rewards distribution hub.

This contract will be responsible for distributing rewards on governance tokens (emissions from the treasury) and revenue emssions (WETH) to the users who lock their tokens into it. The owner of the contract will set the rewards epochs and amount and in the end of each epoch the contract will distribute these rewards to the addresses that were lock on that epoch based on the amount of tokens they locked.

## Functionality

* Depositors can lock their governance tokens for an adjustable Period
* There are Epochs (likely Monthly so 28, 29, 30, or 31 days)
* At the end of each Epoch a tranche of tokens become claimable (depending on how much each individual staked)
* Tokens have to be locked ahead of the upcoming epoch to be eligible for the yield
* Emergency unlock by owner (enables withdrawal of all locked tokens)
* Proxy function to move tokens sent to this contract by accident
* Rewards are in *two* types of tokens at once, WETH (revenue) and Governance Tokens (emissions)
* Every epoch the dao treasury will distribute revenue and emissions to the contract and notify the contract of the new rewards amount

* Owner sets the end of each epoch (likely monthly so will differ in time duration).

* Token holder can lock for a number of epochs between 1 and max_epochs (settable parameter by the Owner).

* Token holder can re-lock for a number of epochs between 1 and max_epochs counting forward from the current epoch.

* If the Token holder is locked before an epoch begins they’re eligible for the rewards distributed at the end of the epoch

* If Token holder’s lock expires at the end of an epoch, and they do not re-lock before the end of the epoch, they are no longer eligible for rewards in the next epoch

# How to run:

Install all dependencies: <br>
`npm install` 

Run an ethereum fork node: <br>
`npx hardhat npx hardhat node --fork https://eth-mainnet.alchemyapi.io/v2/<INSERT YOUR ALCHEMY KEY HERE>`

On another terminal deploy the contract: <br>
`npx hardhat test --network localhost`
