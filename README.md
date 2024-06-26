# Create and Mint Token

This Solidity program creates a token based upon the ERC20 by inheriting it. It also has two more functions 
* Mint function - which is only accessible to the owner, so that they mint token for another account
* Burn function - available to all so that they can burn/destroy the token

## Description

This is contract based upon inheriting ERC20 contract which allows us to get functions and variables out of the box. 
1. totalSupply - gives total amount of tokens we have 
2. Symbol - symbol of our token you created
3. Name - name of our token
4. Decimals - gives the number of decimal places the token uses
5. balanceOf function - gives the tokens a particular account have
6. transfer function - used to transfer amount to particular address, accepts receiver address and amount to transfer
7. approve function - allowing other account to approve some of your token so that they can use them on your behalf
8. allowance function - to check how much allowance of token you have given to other account

More added functions and variable -
1. Mint function - only to be called by owner so that they can mint tokens for another account
2. Burn function - to burn/destroy token in a particular account
3. owner variable - to check the owner account address
4. onlyOnwer modifier - to check if the mint function is only to be called by the owner

## Getting Started

### Executing program

To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension named (MyToken.sol). Copy and paste the following code into the file:

```javascript
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract MyToken is ERC20 {
    address payable public owner;

    constructor(string memory name, string memory symbol) ERC20(name, symbol) {
        owner = payable(msg.sender);
        _mint(msg.sender, 1000000 * (10 ** uint256(decimals())));
    }

    modifier onlyOwner() {
        require(msg.sender == owner, "Only the owner can call this function");
        _;
    }

    function mint(address account, uint256 amount) public onlyOwner {
        _mint(account, amount);
    }

    function burn(uint256 amount) public {
        _burn(msg.sender, amount);
    }
}
```

To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar and then click on the "Compile MyToken.sol" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "MyToken" contract from the dropdown menu and do the following steps -
1. Mention token name and token symbol
2. Mention the address to deploy the contract on
3. Then click on the "Deploy" button.

Once the contract is deployed, you can interact with it by calling the above mentioned functions and play around with it. In case you are stuck, you can contact me on the email given below. 

## Authors

Aashman Verma - vermaaashman16@gmail.com


## License

This project is licensed under the MIT License - see the LICENSE.md file for details