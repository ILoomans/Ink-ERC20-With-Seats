# Ink! Ticket Smart Contract
## Overview
This is a erc20 smart contract with purchase functionality, implemented to represent the purchasing and selling of tickets
in a fair & transparent manner. Because this contract implements the basic ERC20 smart contract, the documentation will only cover 
the functionality that is built on top of the ERC20 contract. This smart contract allows for both ticket classes that have seats and 
tickets that don't have seats. The ticket type can be declared in the constructor. There is a seperate smart contract standard to manage events without seats.

## Verification

This smart contract holds an important part in the verification process of the ticketing cycle. Using assymetric encryption we are 
able to securly manage access to events.




## Todo

- [ ] Add Documentation for Verification Process
- [ ] Add Query Documentation
- [ ] Add Event Documentation

## Transactions


### add_verifier
#### Description
This function allows the contract owner (event host) to add a verifier who can then verify a users ticket and burn (remove) them.
#### Parameters
| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `to`      | `address` | The address being added as a verifier |

#### Constraints
Only the contract owner can sign this transaction


### purchase_tickets
#### Description
This function allows a user to purchase tickets, write their signature that will allow them to prove their ownership of the token.
The function also takes a seat parameter, which will allow a user to select their seats (if it is initiated as a ticket smart contract with seats).
If the contract has no seats, the seats parameter should be set as an empty array. 

This is a payable function 
#### Parameters
| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `to`      | `address` | The account that will receive the tokens |
| `value`      | `int` | The amount of tokens being bought  |
| `signature`      | `Uint8Array` | The signature of a message which will later be used to verify the users identity |
| `seats`      | `Array` | The Seats being bought |

#### Constraints
The value being sent must match the price of the token multiplied by the amount being bought

If the contract has seats, the seats selected must be available

If the contract has seats, the amount of seats selected must match the amount of tickets being sold 



### clear
#### Description
This allows the owner of the contract to withdraw their balance
#### Parameters

#### Constraints

Only the contract owner can sign this transaction

