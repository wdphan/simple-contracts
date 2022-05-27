# Simple Contracts

> Small, basic smart contracts.

Simple contracts is just what it is - really simple contracts. This is done to better understand solidity concepts.

## Simple Storage

> Store data on the blockchain.

The Simple Storage contract consists of a `set(uint x)` and a `get` function. Both would enable you to set values and get values.

[Contract Source](contracts/SimpleStorage.sol)

## Simple Coin

> Mint coins.

The Simple Coin contraft contains two functions: `mint(address receiver, uint amount)` and `send (address receiver, uint amount)`

The key learning here was to understand how a user can mint and send coins with the necessary requirements. The functions emit event `Sent(address from, address to, uint amount)`

[Contract Source](contracts/SimpleCoin.sol)

## Simple Game

> Barebones of a mini-game.

The Simple Game enables you to add players with the `addPlayer(string memory firstName, string memory lastName)` function and get a players level with the `getPlayerLevel(address playerAddress)` function. The contract contains and enum that allows players to level up: `Level {Novice, Intermediate, Advanced}`

[Contract Source](contracts/SimpleGame.sol)

## Simple Coin w/Modifier

> The Simple Coin contract except with modifiers.

Literally the same thing as the Simple Coin contract, except we added modifiers `onlyMinter`, `amountGreaterThan (uint amount)`, and `balanceGreaterThanAmount(uint amount)`. The functions emit event `Sent(address from, address to, uint amount)`

[Contract Source](contracts/SimpleCoinWModifier.sol)

## Simple Time

> Basically the Simple Game Contract with an added time component.

The contract has an `addPlayer(string memory firstName, string memory lastName)` function and get a players level with the `getPlayerLevel(address playerAddress)` function. The contract contains and enum that allows players to level up: `Level {Novice, Intermediate, Advanced}`. 

20 seconds after a new player is created, the player will level up from Novice to Intermediate with the `changePlayerLevel (address playerAddress)` function. 

[Contract Source](contracts/SimpleTime.sol)

## Simple Coin 2

> The Simple Coin contract but with an added time component.

The Simple Coin contract contains two functions: `mint(address receiver, uint amount)` and `send (address receiver, uint amount)` The `send (address receiver, uint amount)` enables users to send their coins after the contract is open for 30 seconds with the `require(block.timestamp >= contractStartTime + 30)`.

[Contract Source](contracts/SimpleCoin2.sol)

## Simple Auction

> A Simple Auction where everyone can send their bids during a certain bidding period. If the highest bid is raised, the previous highest bidder gets their money back. After the end of the period, the contract is called for the beneficiary to receive their money.

The contract contains `bid`,`widthdraw`, and `auctionEnd` function. The functions emit `AuctionEnded(highestBidder, highestBid)` and provide events `HighestBidIncrease(address bidder, uint amount)` and `AuctionEnded(address winner, uint amount)`

[Contract Source](contracts/SimpleAuction.sol)

## Simple Multi-Send

> Basicallt the Simple Game Contract with an entrance fee and function pays the winner.

The Simple Game enables you to add players with the `addPlayer(string memory firstName, string memory lastName)` function and get a players level with the `getPlayerLevel(address playerAddress)` function. The contract contains and enum that allows players to level up: `Level {Novice, Intermediate, Advanced}`

The `joinGame(string memory firstName, string memory lastName)` function requires an entrance fee of 25 ether. If acquired, it will increase player count by 1 and increase the pot by 25 ether. The `payOutWinners(address loserAddress)` function ensures that only the dealer pays out the winners and doesn't pay the loser. The pot is split between the winers with `uint payoutPerWinner = msg.value / (playerCount - 1)`.

[Contract Source](contracts/SimpleMultSend.sol)
