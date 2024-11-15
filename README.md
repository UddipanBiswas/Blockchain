// SPDX-License-Identifier: MIT

pragma solidity ^0.8.0;

contract Payment {
    mapping(address => uint) public balances; // Mapping of user addresses to their account balance
    
    function deposit() public payable { 
        require(msg.value > 0, "Deposit must be greater than zero"); // Check if the sent value is valid
        
        balances[msg.sender] += msg.value;
        
      } 

function withdraw(uint amount) public {
require(balances[msg.sender] >= amount,"Insufficient balance");
            
balances[msg.sender]-=amount; 
payable(msg.sender).transfer(amount);  
}
}
