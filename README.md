// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/token/ERC20/extensions/ERC20Pausable.sol";
import "@openzeppelin/contracts/token/ERC20/extensions/ERC20Burnable.sol";
import "@openzeppelin/contracts/access/Ownable.sol";
import "@openzeppelin/contracts/token/ERC20/extensions/ERC20Permit.sol";

contract AfricaGreatWall is ERC20, ERC20Pausable, ERC20Burnable, Ownable, ERC20Permit {
    constructor(address initialOwner)
        ERC20("AFRICA GREAT WALL", "AGW")
        Ownable(initialOwner)
        ERC20Permit("AFRICA GREAT WALL")
    {
        _mint(initialOwner, 1000000 * 10 ** decimals()); // Mint 1 juta token saat deploy
    }

    function pause() public onlyOwner {
        _pause();
    }

    function unpause() public onlyOwner {
        _unpause();
    }

    function mint(address to, uint256 amount) public onlyOwner {
        _mint(to, amount);
    }

    function _update(address from, address to, uint256 value)
        internal
        override(ERC20, ERC20Pausable)
    {
        super._update(from, to, value);
    }

    function decimals() public pure override returns (uint8){
        return 10;
    }
}
