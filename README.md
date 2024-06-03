# MyToken Solidity Contract

# Overview
MyToken is a simple Solidity contract for creating and managing a basic token on the Ethereum blockchain. This contract includes functionalities for minting and burning tokens, maintaining balances, and tracking the total supply.

# Contract Details
- Public Variables
  - `tokenName`: The name of the token.
  - `tokenAbbrv`: The abbreviation of the token name.
  - `totalSupply`: The total number of tokens in existence.

# Mappings
-balances: A mapping that stores the balance of each address.
# Functions
- **mint**: Increases the total supply and the balance of a specified address.
- **burn**: Decreases the total supply and the balance of a specified address, ensuring that the balance is sufficient for the burn operation.

# Copy code solidity Contract Code

- Copy the following code and paste it into `MyToken.sol`:
     ```solidity
     // SPDX-License-Identifier: MIT
     pragma solidity 0.8.18;

     /*
            REQUIREMENTS
         1. Your contract will have public variables that store the details about your coin (Token Name, Token Abbrv., Total Supply)
         2. Your contract will have a mapping of addresses to balances (address => uint)
         3. You will have a mint function that takes two parameters: an address and a value. 
            The function then increases the total supply by that number and increases the balance 
            of the “sender” address by that amount
         4. Your contract will have a burn function, which works the opposite of the mint function, as it will destroy tokens. 
            It will take an address and value just like the mint functions. It will then deduct the value from the total supply 
            and from the balance of the “sender”.
         5. Lastly, your burn function should have conditionals to make sure the balance of "sender" is greater than or equal 
            to the amount that is supposed to be burned.
     */

     contract MyToken {
         // public variables here
         string public tokenName = "Bharat Bhushan";
         string public tokenAbbrv = "BB";
         uint256 public totalSupply = 0;

         // mapping variable here
         mapping(address => uint256) public balances;

         // mint function
         function mint(address _address, uint _val) public {
             totalSupply += _val;
             balances[_address] += _val;
         }

         // burn function
         function burn(address _address, uint _val) public {
             if (balances[_address] >= _val) {
                 totalSupply -= _val;
                 balances[_address] -= _val;
             }
         }
     }
     ```
     
# Usage
# Deploying the Contract
1.Use an Ethereum development environment like [Remix https://www.trufflesuite.com/docs/truffle/overview) to compile and deploy the contract to an Ethereum network.
2. Interact with the deployed contract using its address on the Ethereum network.

# Interacting with the Contract
You can interact with the deployed contract using Ethereum wallets or by writing scripts in programming languages like JavaScript. Here's how you can interact with the contract:

Minting Tokens: Call the `mint` function with the address where you want to send the tokens and the amount to mint.

Burning Tokens: Call the `burn` function with the address from where you want to burn the tokens and the amount to burn.


### Executing Program

#### How to Run the Program in Remix
1. **Compile the Smart Contract**
   - Select the `Solidity Compiler` tab.
   - Ensure the compiler version is set to `0.8.18`.
   - Click `Compile MyToken.sol`.

2. **Deploy the Contract**
   - Go to the `Deploy & Run Transactions` tab.
   - Select the appropriate environment (e.g., JavaScript VM).
   - Click `Deploy`.

3. **Interact with the Contract**
   - After deploying, the contract will appear under `Deployed Contracts`.
   - To mint tokens:
     - Input the address and the amount of tokens to mint.
     - Click the `mint` button.
   - To burn tokens:
     - Input the address and the amount of tokens to burn.
     - Click the `burn` button.
