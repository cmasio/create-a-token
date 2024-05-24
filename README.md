MyToken Smart Contract

DESCRIPTION

The MyToken contract is a simple implementation of a token system in Solidity, designed to handle basic minting and burning of tokens. The contract defines public variables for the token's name, abbreviation, and total supply, making this information easily accessible. It uses a mapping to keep track of the balance of tokens held by each address, ensuring precise and transparent management of individual holdings. The mint function allows for the creation of new tokens, incrementing the total supply and updating the balance of a specified address. Conversely, the burn function permits the destruction of tokens, provided the address has sufficient balance, thereby decreasing both the total supply and the address's token holdings. This straightforward structure provides essential functionality for managing a token economy on the Ethereum blockchain.

Requirements
1.Public Variables: The contract includes public variables to store details about the token:

Token Name (tokenName)
Token Abbreviation (tokenAbbry)
Total Supply (totalSupply)

2.Balances Mapping: A mapping from addresses to balances to keep track of how many tokens each address holds.

3.Mint Function: A function to increase the total supply of tokens and allocate them to a specified address.

4.Burn Function: A function to decrease the total supply of tokens and deduct them from a specified address, with a check to ensure the address has enough tokens to burn.

Contract Code:

// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;

contract MyToken {

    // Public variables to store token details
    string public tokenName = "META";
    string public tokenAbbry = "MTA";
    uint public totalSupply = 0;
    
    // Mapping to store balances of each address
    mapping(address => uint) public balances;
    
    // Function to mint new tokens
    function mint(address _address, uint _value) public {
        totalSupply += _value;
        balances[_address] += _value;
    }
    
    // Function to burn tokens
    function burn(address _address, uint _value) public {
        require(balances[_address] >= _value, "Insufficient balance to burn");
        totalSupply -= _value;
        balances[_address] -= _value;
    }
}

Functions:
Mint Function
Tokens can be created anew through the mint function. Upon calling, it adds the specified _value to the balance of the specified _address and raises the totalSupply by that amount.

Syntax
function mint(address _address, uint _value) public
_address: The address to which the newly minted tokens will be credited.
_value: The number of tokens to mint.

Burn Function
Token destruction is possible with the burn function. It takes the specified _value and subtracts it from the balance of the specified _address, lowering the totalSupply by that amount. It also includes a check to see if there are enough tokens for the _address to burn.

Syntax
function burn(address _address, uint _value) public
_address: The address from which the tokens will be burned.
_value: The number of tokens to burn.

Usage:
Deploy the MyToken contract to the Ethereum blockchain using your preferred method Remix.

After deployment, you can interact with the contract to mint and burn tokens, as well as check the balances and total supply.


License
This contract is licensed under the Metacrafters License.
