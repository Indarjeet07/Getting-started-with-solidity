# Getting-started-with-solidity
# Getting started 
# Code Execution 
To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.


//SPDX-License-Identifier: MIT
pragma solidity 0.8.18;
contract MyToken {
    string public tokenName;
    string public tokenSymbol;
    uint256 public totalSupply;
    mapping(address => uint256) public balances;

    constructor(string memory name, string memory symbol, uint256 supply) {
        tokenName = name;
        tokenSymbol = symbol;
        totalSupply = supply;
        balances[msg.sender] = supply;
    }

    function mint(address recipient, uint256 value) public {
        require(recipient != address(0), "Invalid recipient address");
        totalSupply += value;
        balances[msg.sender] += value;
    }

    function burn(address sender, uint256 value) public {
        require(sender != address(0), "Invalid sender address");
        require(balances[sender] >= value, "Insufficient balance to burn");
        totalSupply -= value;
        balances[sender] -= value;
    }
} 
