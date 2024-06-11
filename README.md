# ETHProofBeginner-Assignment

# MyToken Contract
# Overview
MyToken is a simple ERC20-like smart contract deployed on the Ethereum blockchain. It allows the creation of a new cryptocurrency with basic functionalities such as minting and burning tokens. The contract is written in Solidity and is compatible with Solidity version >=0.8.2 <0.9.0.

# Requirements
# 1. Public Variables

tokenName: A string that stores the name of the token.
tokenAbbrv: A string that stores the abbreviation of the token.
totalSupply: An unsigned integer that stores the total supply of the token.
# 2. Mapping

balance: A mapping that associates addresses with their token balances.
#3. Functions

mint: A function that increases the total supply of tokens and updates the balance of a specified address.
burn: A function that decreases the total supply of tokens and updates the balance of a specified address, with a condition to ensure the address has enough tokens to burn.
# Contract Code
// SPDX-License-Identifier: MIT
pragma solidity >=0.8.2 <0.9.0;

contract MyToken {

    // public variables here
    string public tokenName= "JeetCoin";
    string public tokenAbbrv="Jeet";
    uint public totalSupply=0;

    // mapping variable here
    mapping(address => uint) public balance;

    // mint function
    function mint(address Address, uint Value) public{
        totalSupply +=Value;
        balance[Address] += Value;
    }

    // burn function
    function burn (address Address, uint Value) public{
        if(balance[Address] >= Value){
            totalSupply -= Value;
            balance[Address] -= Value; 
        }
    }
}

# Functions Description
# mint
function mint(address Address, uint Value) public
# Parameters:
Address: The address to which the minted tokens will be added.
Value: The amount of tokens to be minted.
# Description: This function increases the totalSupply by the Value specified and updates the balance of Address by the same amount.
burn
function burn(address Address, uint Value) public
Parameters:
Address: The address from which the tokens will be burned.
Value: The amount of tokens to be burned.
Description: This function decreases the totalSupply by the _value specified and updates the balance of _address by the same amount. It includes a check to ensure that the Address has enough tokens to burn; otherwise, it will revert the transaction with an error.
How to Use
Deploy the Contract: Use Remix or any other Ethereum development environment to deploy the contract on the Ethereum blockchain.

Mint Tokens: Call the mint function with the recipient's address and the amount of tokens to mint.

Burn Tokens: Call the burn function with the sender's address and the amount of tokens to burn. Ensure the sender has enough tokens to burn, otherwise, the transaction will fail.

License
This project is licensed under the MIT License - see the LICENSE file for details.

Acknowledgments
Solidity Documentation
OpenZeppelin Contracts Library
Ethereum Community
