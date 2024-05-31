//SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppenlin/contracts/token/ERC20/ERC20.sol"

contract PolsToken is ERC20 {
    address public showowner;

    constructor(uint256 initialSupply) ERC20("PolsToken", "LTK") {
        showowner=msg.sender;
        _mint(msg.sender, initialSupply);
    }

    function mint(address to, uint256 amount) public {
        require(to==showowner,"You're not the owner");
        _mint(to, amount);
    }

    function transfer(address to, uint256 amount) public virtual override returns(bool) {
        _transfer(_msgSender(), to, amount);
        return true;
    }

    function burn(uint256 amount) public {
        _burn(msg.sender, amount);
    }

}
