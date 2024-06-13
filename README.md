# MyToken Smart Contract

## Overview

This repository contains the implementation of a basic ERC-20-like token contract written in Solidity. The contract includes functionalities to mint and burn tokens, with public variables to store token details and a mapping to track user balances.

## Features

- **Token Details**:
  - Token Name: `OREO`
  - Token Abbreviation: `ORE`
  - Total Supply: Initially set by the deployer

- **Functions**:
  - `mint(address _address, uint _value)`: Increases the total supply and the balance of the specified address.
  - `burn(address _address, uint _value)`: Decreases the total supply and the balance of the specified address, with a check to ensure sufficient balance.

## Contract Code

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.18;

contract MyToken {

    // Public variables
    string public Token_Name = "OREO";
    string public Token_Abbrv = "ORE";
    uint public Total_Supply;

    // Mapping to store balances
    mapping(address => uint) public balance;

    // Mint function
    function mint(address _address, uint _value) public {
        Total_Supply += _value;
        balance[_address] += _value;
    }

    // Burn function
    function burn(address _address, uint _value) public {
        require(balance[_address] >= _value, "Insufficient balance to burn");
        Total_Supply -= _value;
        balance[_address] -= _value;
    }
}
