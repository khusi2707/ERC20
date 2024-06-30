
# MyToken (MTK) ERC20 Token

MyToken is an ERC20 token implemented in Solidity, leveraging OpenZeppelin's contracts for ERC20 functionality and access control via ownership.

## Overview

MyToken (MTK) is a standard ERC20 token designed for decentralized applications (dApps) on the Ethereum blockchain. It provides basic functionalities such as token transfers, minting new tokens, and burning existing tokens. The contract implements the `Ownable` pattern, ensuring that token management operations are securely controlled by the initial contract deployer.

## Features

- **ERC20 Compatibility**: Implements the ERC20 token standard, allowing seamless integration with Ethereum-based dApps, wallets, and exchanges.
- **Ownership Control**: Utilizes the `Ownable` contract from OpenZeppelin, ensuring that only the contract deployer has the authority to mint new tokens.
- **Minting and Burning**: Provides functions to mint new tokens (`mint`) and burn existing tokens (`burn`), offering flexible token supply management.
- **Transfer Function**: Implements a standard `transfer` function for transferring tokens between addresses.

### Interacting with Your Token

- **Mint Tokens**: As the owner, use the `mint` function to create new tokens and allocate them to addresses.
- **Burn Tokens**: Use the `burn` function to destroy tokens, reducing the token supply.
- **Transfer Tokens**: Use the standard `transfer` function to send tokens between addresses.

### Example Code

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

contract MyToken is ERC20, Ownable {
    constructor(string memory name, string memory symbol) ERC20(name, symbol) Ownable(msg.sender) {}

    function mint(address to, uint256 amount) public onlyOwner {
        _mint(to, amount);
    }

    function burn(uint256 amount) public {
        _burn(msg.sender, amount);
    }

    function transfer(address recipient, uint256 amount) public override returns (bool) {
        _transfer(_msgSender(), recipient, amount);
        return true;
    }
}
```

### License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

