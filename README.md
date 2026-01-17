# defi-staking-contract
This repository contains a clean and minimal implementation of an ERC20-compatible token written in Solidity. The project focuses on core token mechanics such as supply initialization, balance management, and secure value transfers between addresses.

// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract MyToken {
    string public name = "ForgeToken";
    string public symbol = "FRG";
    uint256 public totalSupply;

    mapping(address => uint256) public balanceOf;

    constructor(uint256 supply) {
        totalSupply = supply;
        balanceOf[msg.sender] = supply;
    }

    function transfer(address to, uint256 amount) external {
        require(balanceOf[msg.sender] >= amount, "Insufficient balance");
        balanceOf[msg.sender] -= amount;
        balanceOf[to] += amount;
    }
}
