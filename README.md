# ERC-20 Token Contract with Mint and Burn Functions

The project aims to create a smart contract for an ERC-20 token with mint and burn functions to manage the creation and destruction of tokens.

## Description

This project involves creating a smart contract for an ERC-20 token on the Ethereum blockchain. The contract will have public variables to store details about the token, such as its name and total supply, and a mapping of addresses to balances to track how many tokens each address holds. The contract will have a mint function to create new tokens and increase the balance of a specified address, and a burn function to destroy tokens and decrease the balance of a specified address. The burn function will have conditional statements to ensure that the balance of the account is greater than or equal to the amount to be burned, preventing negative token balances.

## Getting Started

### Executing program

To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., HelloWorld.sol). Copy and paste the following code into the file:

```javascript
// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;


contract MyToken {
    string public tokenName = "Sakura";
    string public tokenAbbrv = "SKA";
    uint public totalSupply = 0;

    mapping(address => uint) public balances;

    function mint(address _address, uint _value) public {
        totalSupply += _value;
        balances[_address] += _value;
    }

    function burn (address _address, uint _value) public {
        if (balances[_address] >= _value){
            totalSupply -= _value;
            balances[_address] -= _value;
        }
    }
}

```
To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.18" (or another compatible version), and then click on the "Compile HelloWorld.sol" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar.After deploying the code by clicking on the Deploy button in Remix IDE, you can test the functionality of the contract by calling its functions using the Remix Console.
* First, you can check the initial values of the public variables by calling the getters for tokenName, tokenAbbrv, and totalSupply. You should see the values you assigned in the contract (in this case, "Sakura", "SKA", and 0).
* Next, you can test the mint function by calling it with an address and a value, for example: mint(0x1234567890123456789012345678901234567890, 100). This will add 100 tokens to the specified address and increase the total supply by 100.
* Then, you can test the burn function by calling it with the same address and value, for example: burn(0x1234567890123456789012345678901234567890, 50). This will subtract 50 tokens from the specified address and decrease the total supply by 50, assuming the address had at least 50 tokens to begin with.
* You can check the balance of the specified address by calling balances[0x1234567890123456789012345678901234567890] and verifying that it has the expected value (in this case, 50). You can also check that the total supply has decreased by calling the getter for totalSupply.
* Finally, you can test the conditional in the burn function by trying to burn more tokens than the address holds, for example: burn(0x1234567890123456789012345678901234567890, 100). This should not subtract any tokens or decrease the total supply, and the balances of the address and the total supply should remain the same as before the function call.

## Authors

Mohammed Yousuf Parvez
[@yousufm32321948](https://twitter.com/yousufm32321948)
