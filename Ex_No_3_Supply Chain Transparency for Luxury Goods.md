# Ex_No_3_Supply Chain Transparency for Luxury Goods
### NAME: HARINI R
### REG NO:212223100010
### DEPARTMENT:CSE(CYBER SECURITY)
## Aim:
To develop a smart contract that tracks the supply chain of luxury goods, ensuring authenticity.
## Algorithm:
The manufacturer records product creation details on-chain.


The product moves through different supply chain checkpoints.


The ownership of the product can be transferred securely.


Buyers can verify the product’s authenticity.


## Program:
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract LuxurySupplyChain {
    struct Product {
        string name;
        address currentOwner;
        bool verified;
    }

    mapping(uint256 => Product) public products;

    event ProductRegistered(uint256 productId, string name);
    event OwnershipTransferred(uint256 productId, address newOwner);

    function registerProduct(uint256 productId, string memory name) public {
        require(products[productId].currentOwner == address(0), "Product already registered");
        products[productId] = Product(name, msg.sender, true);
        emit ProductRegistered(productId, name);
    }

    function transferOwnership(uint256 productId, address newOwner) public {
        require(products[productId].currentOwner == msg.sender, "Not the owner");
        products[productId].currentOwner = newOwner;
        emit OwnershipTransferred(productId, newOwner);
    }

    function verifyProduct(uint256 productId) public view returns (string memory, address, bool) {
        Product memory p = products[productId];
        return (p.name, p.currentOwner, p.verified);
    }
}
```
## Expected Output:
A luxury good (e.g., a Rolex watch) is registered on-chain.
<img width="1920" height="1080" alt="Screenshot 2025-10-16 091540" src="https://github.com/user-attachments/assets/0cf4b2dc-280c-4af4-b564-b426e1e28653" />

<img width="1920" height="1080" alt="Screenshot 2025-10-16 092230" src="https://github.com/user-attachments/assets/e568c23a-367b-4503-b222-cf300c47a742" />
<img width="1920" height="1080" alt="Screenshot 2025-10-16 093801" src="https://github.com/user-attachments/assets/a862e1b6-4ce3-4521-a97f-704ff6178036" />

Ownership is transferred at every checkpoint.


Buyers can check the authenticity before purchasing.


## High-Level Overview:
Helps prevent counterfeit luxury goods.


Teaches real-world supply chain use cases.

## RESULT : 
Thus a smart contract that tracks the supply chain of luxury goods, ensuring authenticity is executed successfully.
