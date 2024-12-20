# AbdulBasitCoin (ABC) Smart Contract

This repository contains the Solidity smart contract for **AbdulBasitCoin (ABC)**, a simple token implementation designed for learning purposes. The contract defines a custom token with minting and burning functionality while maintaining essential security checks.

---

## Features
1. **Token Details**:
   - **Name**: AbdulBasitCoin
   - **Abbreviation**: ABC
   - **Total Supply**: 1,000,000 (initially set)

2. **Mapping for Balances**:
   - A `mapping` is used to keep track of token balances for each address.

3. **Mint Functionality**:
   - Adds tokens to an address.
   - Increases the total supply.

4. **Burn Functionality**:
   - Removes tokens from an address.
   - Decreases the total supply.
   - Ensures sufficient balance exists before burning.

---

## Smart Contract Overview

### Public Variables
The contract includes public variables to store token details, making them accessible to users:
```solidity
string public tokenName = "AbdulBasitCoin";
string public tokenAbbrv = "ABC";
uint public totalSupply = 1000000;
```

### Token Balances
A `mapping` associates each address with its respective token balance:
```solidity
mapping(address => uint) public balances;
```

### Mint Function
The `mint` function allows authorized users to increase the token supply and assign tokens to specific addresses:
```solidity
function mint(address _address, uint _value) public {
    totalSupply += _value;
    balances[_address] += _value;
}
```

### Burn Function
The `burn` function reduces the token supply by removing tokens from a specific address. It includes checks to ensure the balance is sufficient:
```solidity
function burn(address _address, uint _value) public {
    require(balances[_address] >= _value, "Insufficient balance to burn");
    totalSupply -= _value;
    balances[_address] -= _value;
}
```

---

## Requirements
The contract adheres to the following requirements:
1. Public variables for token details (name, abbreviation, total supply).
2. Address-to-balance mapping for managing user balances.
3. Mint function to create new tokens and assign them to an address.
4. Burn function to destroy tokens and reduce total supply.
5. Safety checks in the burn function to prevent burning more tokens than available.

---

## How to Use
1. **Deploy the Contract**:
   - Deploy the contract on the Ethereum network or any compatible EVM chain.
2. **Mint Tokens**:
   - Call the `mint` function with the recipient address and the number of tokens to mint.
3. **Burn Tokens**:
   - Call the `burn` function with the address and the number of tokens to burn.
   - Ensure the address has sufficient balance before calling this function.

---

## License
This project is licensed under the MIT License. See the `LICENSE` file for details.
