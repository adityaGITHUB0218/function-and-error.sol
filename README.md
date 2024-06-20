# Overview
ExampleContract is a smart contract implemented in Solidity that demonstrates the use of require(), assert(), and revert() statements to enforce conditions and handle errors effectively. This contract allows only the owner to set a value within a specified limit and withdraw funds from the contract.

# Features
Ownership Control: Only the owner can set the value and withdraw funds.
Value Constraint: The value can only be set within a predefined range.
Error Handling: Utilizes require(), assert(), and revert() for robust error management

# Smart Contract Implementation
# SPDX License Identifier
The contract begins with an SPDX license identifier for clarity and licensing purposes.

# solidity

// SPDX-License-Identifier: MIT
Solidity Version
The contract is written in Solidity version 0.8.0, which includes built-in overflow and underflow protection.
pragma solidity ^0.8.0;

# Contract Definition
The contract ExampleContract is defined with state variables and functions to manage value setting and fund withdrawal.

solidity
Copy code
contract ExampleContract {
    address public owner;
    uint256 public value;

    constructor() {
        owner = msg.sender;
    }
setValue Function
The setValue function allows the owner to set a new value, ensuring that it does not exceed 100.


# 'setValue' Function
function setValue(uint256 _newValue) external {
    // Use require() to validate a condition
    require(msg.sender == owner, "Only the owner can set the value");

    // Use assert() to check an invariant (e.g., value should not exceed 100)
    assert(_newValue <= 100);

    // Set the new value
    value = _newValue;
}
require(): Ensures that only the owner can call this function.
assert(): Ensures that the new value does not exceed 100.

# 'withdraw' Function
The withdraw function allows the owner to withdraw all funds from the contract.


function withdraw() external {
    // Use require() to validate a condition
    require(msg.sender == owner, "Only the owner can withdraw");

    // Transfer the balance to the owner
    payable(owner).transfer(address(this).balance);
}
require(): Ensures that only the owner can call this function.
revert(): Implicitly used by require() to revert the transaction if the condition fails.

# Deployment
To deploy the contract, use a development environment like Remix or Truffle. Ensure you have an Ethereum wallet and some test ETH to deploy the contract on a testnet.

# Usage
1) Setting the Value:
The owner can call the setValue function with a value not exceeding 100.
2) Withdrawing Funds:
The owner can call the withdraw function to transfer all contract funds to their address.

# License
This project is licensed under the MIT License.

